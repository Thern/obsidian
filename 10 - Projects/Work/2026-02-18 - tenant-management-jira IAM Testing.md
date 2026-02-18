---
date: 2026-02-18
created: 2026-02-18
tags:
  - meeting
  - area/work
---

# Meeting: tenant-management-jira IAM Testing

**Date:** 2026-02-18 Wednesday
**Location / Link:** Office

## Attendees

- Willem
- Ruchika

## Agenda

1. Test tenant-management-jira with IAM software statements

---

## Notes

Testing was limited — blocked by IAM software statements not yet being deployed. Pinged Sebastian twice, no response.

**Positive update:** Switched to SCRATCH containers for the project. Image size is now ~21 MB with minimal attack surface (close to zero vulnerabilities expected).

### Fallback plan

If IAM software statements aren't deployed before/during holidays: fall back to API key auth.

---

## Action Items

| Action | Owner | Due |
|--------|-------|-----|
| Deploy IAM software statements | Sebastian | ASAP |
| Check if IAM deployed after holidays | Willem | Monday 2026-02-23 |
| Implement API key fallback if IAM not ready | Willem | Monday 2026-02-23 |

## Decisions Made

- Switched to SCRATCH containers — image now 21 MB, minimal vulnerabilities

## Follow-Up

- If Sebastian deploys IAM during holidays: work on Monday from a clean state
- If not: fall back to API key auth

---

*Filed under: [[10 - Projects/Work/]]*
