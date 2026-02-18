---
date: 2026-02-18
created: 2026-02-18
tags:
  - meeting
  - area/work
---

# Meeting: pali-ng Terraform Plan Discussion

**Date:** 2026-02-18 Wednesday
**Location / Link:** Office

## Attendees

- Willem
- Arnoud

## Agenda

1. pali-ng deathdate flow — currently does nothing, needs implementation
2. Terraform plan interaction — evaluate current approach and alternatives

---

## Notes

### Deathdate Flow

The "deathdate" flow in pali-ng is currently a no-op. Arnoud wants to start implementing it. The first step is deciding how pali-ng interacts with Terraform/Terragrunt to run a `terraform plan`.

### Terraform Interaction Options

Three options discussed:

| Option | Description | Status |
|--------|-------------|--------|
| **tfexec** | HashiCorp Go package for direct Terraform interaction. Clean API, well-maintained. | Not sure if compatible with Terragrunt — needs investigation |
| **terratest** | HashiCorp testing library, primarily for testing Terraform modules. Could potentially be repurposed. | More experimentation needed |
| **Current approach** | Fork the Terragrunt process, capture stdout, parse output. | Works, but limited interactivity — feels like a hack |

The current forked-process approach lacks interactive control (e.g. approving/rejecting a plan). All three options need more investigation before a decision.

---

## Action Items

| Action | Owner | Due |
|--------|-------|-----|
| Research tfexec compatibility with Terragrunt | Arnoud | — |
| Evaluate terratest as a programmatic interface | Arnoud | — |
| Follow up with Arnoud on findings | Willem | Next sync |

## Decisions Made

- Arnoud will lead the research (he's new and has bandwidth for investigation)

## Follow-Up

- Check in with Arnoud on what he finds
- Decision pending before deathdate flow implementation can begin

---

*Filed under: [[10 - Projects/Work/]]*
