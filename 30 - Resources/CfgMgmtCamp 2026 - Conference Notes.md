---
created: 2026-02-06
updated: 2026-02-19
tags:
  - area/personal
  - area/work
---

# CfgMgmtCamp 2026 — Conference Notes

**Dates:** 4–6 February 2026
**Location:** Ghent, Belgium
**Website:** [cfgmgmtcamp.org](https://cfp.cfgmgmtcamp.org/ghent2026/)

---

## Talks

### AI Native Infrastructure Automation: how I learned to stop worrying and love Claude

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/UGTUYH/) · Adam Jacob (CEO, System Initiative)

- Don't care about "best practices" of applications, because they were created for "human developers" (DRY, KISS). These things don't matter if an LLM can update anything faster anyway.

> **Personal take:** I understand where he is coming from, but I think he's a bit too crazy about it.

---

### OpenTofu Builds It, Ansible Configures It: Using the Right Tool for the Right Job

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/RTUESF/) · James Freeman (AWS)

- Same thing that we are doing. Feels validating. Expected more from the talk.

---

### On the Path to Digital Twins: Loosely Coupled Infrastructure Models

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/RZ8FQZ/) · Pavel Lavrenko (Foliage)

- **Foliage** — tool to create "digital twins" of infra/apps. Can show downstream effects of interruptions:
  - AZ / Region / Cloud going down
  - Service taking down dependent services
- Seems very early, but interesting concept.
- [foliage.dev](https://www.foliage.dev/#how-it-works)

---

### Cloud Native at the Far(m) Edge: Running Kubernetes and AI on Tractors

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/UYXXAQ/) · Mauro Morales & Jordan Karapanagiotis

- Immutable infra for edge Kubernetes (Kairos project).
- Not applicable to us, but reinforces the need for contained DGC.

---

### Using antsibull-nox to test your Ansible collection

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/CSS3XT/) · Felix Fontein

- Two different packages to validate/lint/generate docs for Ansible.
- **Ansible roles `argument_spec.yaml`:**
  - Extra info about Ansible roles.
  - Helps with documenting roles specifically.
  - [argument_spec docs](https://docs.ansible.com/projects/ansible/latest/dev_guide/developing_program_flow_modules.html#argument-spec)
  - [validateargumentspec article](https://www.ansiblepilot.com/articles/ansible-role-input-validation-with-validateargumentspec)

---

### Beyond Static Files: Dynamic Configurations for a Future-Proof World

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/S93BW8/) · Marcel van Lohuizen & Roger Peppe (CUE Labs)

- **CUE:** [cuelang.org](https://cuelang.org/docs/concept/how-cue-enables-configuration/)
- Could be interesting to externalise config validation.
  - Currently we need to start the application to check if the validation is successful; CUE could be ran on the side.

---

### Dopamine, Dunning-Kruger, and a Life in Technology

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/MGVWWM/) · James Freeman

- Did not attend — check back for recording.

---

### How to Use an AI Assistant with Your Monitoring System

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/CE9YF8/) · Dmytro Kozlov (VictoriaMetrics)

- Tried to attend, but the room was overfull.
- Check back for recording.

---

### Ansible - State of the Community

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/PES9FE/) · John "gundalow" Barker & Don Naro

- Nice round-up of the latest Ansible changes, but hard to follow since we are ~5 years behind our current Ansible version.
- Looking forward to the update — looks nice.

---

### Asking a local LLM about my Ansible playbooks because why not

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/Y833ZQ/) · David Moreau-Simard (OVHcloud)
[Recording](https://www.youtube.com/watch?v=WvMmCr8Ho4c)

- Integrate **ARA** (and MCP) with a LLM for querying Ansible playbook results.
- Looks interesting — should really find the time to dig deeper into MCP.

> [!note] Action items
> - [ ] Check if MCP is allowed in Collibra, and if so what is needed.
> - [ ] Would only allow read-only MCP — not willing to trust LLM without human intervention.

---

### Watch paint dry - Monitoring what doesn't change

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/78VKZV/) · Ole Herman Schumacher Elgesem (Northern.tech)

- Could not attend — check back for recording.

---

### From Code to Context: Infrastructure as Code and the Model Context Protocol

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/VM78AU/) · Mar (System Vertrieb Alexander GmbH)

- More MCP. OK-ish talk.

---

### Next-Level Infrastructure as Code with AWS CDK and LocalStack

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/AXBWWR/) · Matheus das Merces (PostNL)

- Just a talk about AWS CDK — not useful for us since we are multi-cloud.
- If we want this capability, Pulumi is the better choice imho.

---

### Building AI-Assisted Operations: Agentic AI Workshop

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/DCRWVC/) · Engin Diri & Zaid Ajaj (Pulumi)

- Mainly a Pulumi workshop.
- **Kagent** was interesting — might be nice to investigate further.
  - Agent framework to allow for debugging of resources.
  - Requires MCP to be allowed.
- Workshop repo: `/Users/willem.jans/Documents/git/github.com/workshop/cfgmgmtcamp-2026-agentic-ai-workshop`

---

### Prowler - Maximize your Cloud Security Compliance Assessments with Open Source and a pinch of AI

[Talk page](https://cfp.cfgmgmtcamp.org/ghent2026/talk/VK3NKE/) · Andoni Alonso & Pedro Martin (Prowler)

- [prowler.com](https://prowler.com/overview)
- Nice tool, but very security-focused.
- Maybe integrate into something, but this should be covered by the Security team's tools imho.

---

## Themes & Takeaways

- **MCP (Model Context Protocol)** was a recurring theme across multiple talks — worth investigating whether it's allowed internally and what the requirements are.
- **Ansible** remains very active in the community; arg spec validation and antsibull-nox are worth a closer look.
- **CUE** looks promising for externalising config validation without needing to run the full application.
- **Digital twins** (Foliage) is an early but interesting direction for infra observability.
- General AI hype is present, but there are real, practical tools emerging.
