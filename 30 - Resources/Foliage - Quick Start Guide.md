---
created: 2026-02-19
updated: 2026-02-19
tags:
  - area/work
---

# Foliage — Quick Start Guide

> **What is Foliage?** A distributed graph platform for building "digital twins" of your IT infrastructure. You model your systems (servers, VMs, Kubernetes clusters, microservices) as a live object graph, then query and propagate signals across that graph — e.g., "if this AZ goes down, what services are affected?"

- GitHub SDK: [foliagecp/sdk](https://github.com/foliagecp/sdk)
- Demo repo (CfgMgmtCamp/FOSDEM 2026): [foliagecp/fosdem-2026-demo](https://github.com/foliagecp/fosdem-2026-demo)
- Talk recording (live demo): [YouTube](https://www.youtube.com/live/nweHLZNs_jQ?t=24860s)

---

## Core Concepts

| Term | What it means |
|------|--------------|
| **Domain / Model** | An isolated namespace of objects (e.g. `m1` = infra, `m2` = K8s) |
| **Connector** | Ingests raw data (command output, K8s API, JSON file) into the graph |
| **Adapter** | Builds/updates a *derived* object graph (the digital twin) from connector data |
| **Signal** | An async event over NATS that triggers functions on graph objects |
| **Shadow object** | A local placeholder pointing to a real object in a *different* domain — how cross-domain linking works |
| **Weak cluster domains** | Configured neighbor domains that can be queried/linked via shadow objects |

The tech stack is: **Go** + **NATS JetStream** (event bus + KV store) + **Docker Compose**.

---

## Step 1 — Watch the demo first

Before writing any code, watch the recorded live demo from CfgMgmtCamp 2026:

[https://www.youtube.com/live/nweHLZNs_jQ?t=24860s](https://www.youtube.com/live/nweHLZNs_jQ?t=24860s)

This shows all four models running together and what the graph UI looks like.

---

## Step 2 — Run the FOSDEM demo locally

The fastest way to understand Foliage is to run the demo that was presented at the conference.

### Prerequisites

- Docker + Docker Compose
- Go 1.21+ (only needed if you want to modify code)
- (Optional) `nats` CLI for manual signal publishing

### Clone and run a single model

```bash
git clone https://github.com/foliagecp/fosdem-2026-demo.git
cd fosdem-2026-demo

# Start the infrastructure (KVM) twin
cd m1
docker compose up --build
```

Each model (`m1`–`m4`) is self-contained with its own NATS instance and `docker-compose.yaml`.

### What each model does

| Model | What it twins |
|-------|--------------|
| `m1` | Servers → hypervisors → VMs (from `lshw`, `lsmod`, `vagrant` snapshots) |
| `m2` | Kubernetes cluster → nodes → pods/deployments (live or from a dump) |
| `m3` | Microservice architecture from a JSON file (e.g. Google's Online Boutique) |
| `m4` | Meta-model: aggregates m1+m2+m3 under one root via shadow objects |

### Run all models together (cross-domain linking)

Running all four models requires sharing a single NATS instance:

1. Start one model's NATS (e.g. start `m1` fully)
2. For m2, m3, m4: disable their own `nats` service in their `docker-compose.yaml`
3. Set `NATS_URL` in each model's `.env` file to point at the shared NATS
4. Bring up m2, m3, m4

Once all four are running, m4 will create shadow links across all domains — giving you the "single pane of glass" view.

---

## Step 3 — Run the SDK simple test

The SDK itself has a simpler standalone test that's good for understanding the fundamentals before dealing with the full demo.

```bash
git clone https://github.com/foliagecp/sdk.git
cd sdk/tests/simple

# Build
docker compose build

# Run
docker compose up -d

# Verify everything is up
docker ps

# Check NATS is healthy
docker logs simple-nats-1 | tail -5

# Check the Foliage runtime has no errors
docker logs simple-runtime-1 | grep -i error

# Tear down
docker compose down -v
```

Grafana (metrics) is available at `http://localhost:3000` once running.

---

## Step 4 — Read the SDK docs (in order)

Work through these in sequence:

1. [Graph CRUD](https://github.com/foliagecp/sdk/blob/main/docs/graph_crud.md) — how to create/read/update/delete graph vertices and edges
2. [Object CRUD](https://github.com/foliagecp/sdk/blob/main/docs/object_crud.md) — the higher-level object model on top of the graph
3. [JPGQL](https://github.com/foliagecp/sdk/blob/main/docs/jpgql.md) — the XPath-like graph query language for traversal and signal routing
4. [Graph debug UI](https://github.com/foliagecp/sdk/blob/main/docs/graph_debug.md) — how to visualise your graph
5. [How to write an application](https://github.com/foliagecp/sdk/blob/main/docs/how_to_write_an_application.md) — putting it all together

---

## Step 5 — Write your first Go application

Add the SDK as a Go dependency:

```bash
go get github.com/foliagecp/sdk
```

The pattern for any Foliage application is:

```
1. Define connector(s) — ingest raw data into CMDB objects
2. Define adapter(s)   — build a derived object graph from connector data
3. Wire signals        — connect connector output → adapter input via NATS subjects
4. Define post-process — handle cross-domain linking or error propagation
```

Look at `m3` in the demo repo as the simplest example — it's just a JSON file being turned into a graph. Good starting template.

---

## Relevance to our work

- **Blast radius analysis**: model our services as a graph, simulate an AZ going down, see which services are affected — directly addresses the kind of observability gaps we discussed
- **CMDB as living graph**: connector pattern fits well over Terraform state or Ansible inventory
- **Loose coupling**: each domain (infra, K8s, apps) is independently deployed — aligns with our multi-team ownership model

> [!note] Next steps
> - [ ] Watch the CfgMgmtCamp recording in full
> - [ ] Run the FOSDEM demo locally (start with m1 only)
> - [ ] Evaluate whether Foliage's graph model fits on top of our existing Terraform/Ansible inventory data
> - [ ] Check if NATS JetStream is already approved/used internally

---

---

## Using Foliage on AWS (VMs + Kubernetes)

### Short answer

No application instrumentation required for infrastructure and K8s topology. There is a meaningful ceiling to what Foliage can know without it, but for the most valuable use case (blast radius: "what breaks if this AZ goes down?") you get a long way without touching Java/Go/Python code.

### What Foliage can learn without touching application code

**From Kubernetes (zero instrumentation)**

The `m2` K8s connector queries the Kubernetes API and builds a full graph of clusters → nodes → pods → deployments → replicasets. Just mount a `kubeconfig` into the `cn_ad_k8s` container per cluster. One model instance per cluster.

**From EC2 VMs (lightweight agent, no app changes)**

The `m1` agent runs a shell script on the host that pushes OS-level snapshots to NATS. For AWS EC2 the `lshw` approach still works, but you'd also want a connector against the **AWS EC2 API** (`describe-instances`, `describe-availability-zones`, etc.) to get cloud-level topology (VPC, subnet, AZ, region) that `lshw` can't see. That's a new Go connector (~100–200 lines) — no application changes.

### The gap: service-to-service dependencies (m3)

Foliage does not auto-discover which service calls which. It can tell you "pod X is on node Y on VM Z in AZ A" — but not "service A calls service B over gRPC" unless you provide that separately.

| Option | What it means | App changes? |
|--------|--------------|-------------|
| Hand-write architecture JSON | Document the call graph yourself (m3 approach) | None |
| Extract from **cdic-wire architecture diagram** | Parse existing architecture source into m3 JSON format | None |
| Connector to **Istio** (Kiali API / Prometheus) | Actual live traffic topology from the mesh | None |
| Connector to **OTEL / Jaeger / Tempo** | Real call graphs from distributed traces | None (already instrumented) |
| Add OTEL instrumentation | Most accurate, real dependency graph | Yes |

> [!note] Our situation
> We have both **Istio** and **OTEL** already in place — neither requires additional app changes.
> The **cdic-wire architecture diagram** may also be parseable into m3's JSON format as a starting point.
> These are worth exploring when time allows — see action items below.

### Practical mapping to our AWS setup

```
Our AWS setup        →  Foliage model
──────────────────────────────────────────────────────
EC2 instances        →  m1 (new AWS EC2 API connector)
EKS / K8s clusters   →  m2 (kubeconfig mount, one per cluster)
Service call graph   →  m3 (cdic-wire diagram export, or Istio/OTEL connector)
Blast radius queries →  m4 (meta-model: EC2 → K8s node → pod → service)
```

The key insight: `m2` already links K8s nodes back to their underlying VMs via shadow objects. So once `m1` (EC2 topology) and `m2` (K8s) are running, Foliage knows which pod runs on which EC2 instance in which AZ — blast radius analysis works at that level without any app instrumentation.

> [!note] Action items (when time allows)
> - [ ] Investigate whether cdic-wire architecture diagram can be exported/parsed into Foliage m3 JSON format
> - [ ] Evaluate Istio connector approach — poll Kiali API or Prometheus to feed m3 automatically
> - [ ] Evaluate OTEL/Jaeger connector as alternative m3 source (we already have traces)
> - [ ] Prototype m1 AWS EC2 API connector (replaces lshw agent for cloud VMs)

---

*See also: [[CfgMgmtCamp 2026 - Conference Notes]]*
