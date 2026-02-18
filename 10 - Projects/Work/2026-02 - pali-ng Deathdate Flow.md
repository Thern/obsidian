---
created: 2026-02-18
updated: 2026-02-18
status: active
area: work
tags:
  - status/active
  - area/work
---

# pali-ng — Deathdate Flow

## Goal

> Implement the deathdate flow in pali-ng so it executes a `terraform plan` and surfaces the result interactively. Currently the flow is a no-op.

## Key Info

| Field    | Value   |
|----------|---------|
| Status   | active  |
| Area     | work    |
| Priority | medium  |

## Next Action

- [ ] Wait for Arnoud's research on terraform interaction options
- [ ] Decide on approach (tfexec / terratest / current fork)
- [ ] Begin implementation once approach is chosen

## Notes & Progress

### 2026-02-18

First discussion with Arnoud. Three options on the table for how pali-ng interacts with Terraform/Terragrunt:

| Option | Notes |
|--------|-------|
| **tfexec** | HashiCorp Go library for direct Terraform interaction. Unknown Terragrunt compatibility — Arnoud to investigate |
| **terratest** | Primarily a testing library, but may work for programmatic invocation. Needs experimentation |
| **Current (fork process)** | Works today but has no interactivity. Feels like a workaround |

Arnoud is leading the research since he has capacity as a newcomer.

## Related

- [[2026-02-18 - pali-ng Terraform Plan Discussion]]

## Archive Notes

> When this project is complete, add a short retrospective here before moving to `40 - Archive/`.
