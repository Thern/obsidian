# How This Vault Works

This vault uses the **PARA method** by Tiago Forte — a simple, universal system for organizing information by *actionability* rather than topic.

---

## The Four Categories

### P — Projects `10 - Projects/`
A project is **a series of tasks with a clear goal and a deadline** (explicit or implied).

- Has a defined outcome: "Website redesign is live", "Half-marathon completed"
- Is either active or finished — never ongoing
- Lives in `10 - Projects/Work/` or `10 - Projects/Personal/`
- When done → move to `40 - Archive/`

**Examples:** Launch new feature, Plan holiday trip, Read *Atomic Habits*, Set up home office

### A — Areas `20 - Areas/`
An area is a **sphere of ongoing responsibility with no end date**.

- Has a *standard* to maintain, not a finish line
- Requires regular attention and review
- Lives in `20 - Areas/Work/` or `20 - Areas/Personal/`

**Examples:** Health, Finances, Engineering, Direct Reports, Home

> The key distinction: Projects have an end. Areas don't. "Get fit" is an Area; "Run a 5k in May" is a Project.

### R — Resources `30 - Resources/`
Reference material on topics you're interested in or learning about.

- No action required — just useful to have
- Organized by topic (one note or subfolder per topic)
- **Examples:** notes on a book, programming concepts, recipe ideas, travel research

### A — Archive `40 - Archive/`
Completed or inactive items from any of the above three categories.

- Move items here instead of deleting — you might need them later
- Mirror the original structure: `40 - Archive/Projects/`, `40 - Archive/Areas/`

---

## The Inbox `00 - Inbox/`

Everything new goes here first. **Never file something directly into PARA during capture — it breaks your flow.**

Process the inbox during your weekly review:
1. Move → Projects, Areas, Resources, or Archive
2. Delete anything you don't need
3. Goal: **empty inbox every week**

---

## Weekly Notes `Weekly Notes/`

A weekly note replaces a daily journal for lower overhead. Create one each Monday.

**Naming convention:** `YYYY-Www` — e.g., `2026-W08`

Use the template: `_Templates/Weekly Note`

The weekly note is your place to:
- Set your top 3 priorities for the week
- Log what's happening at work and personally
- Do your inbox review
- Run a brief retrospective (what worked, what didn't)
- Set focus for the following week

---

## Templates `_Templates/`

| Template | Use for |
|----------|---------|
| `Project` | Every new project note |
| `Weekly Note` | Monday of each week |
| `Meeting` | Any meeting with action items |
| `Area` | Creating a new area note |

**To use in Obsidian:** Install the **Templater** plugin (recommended over core Templates) and set `_Templates/` as your template folder.

---

## Naming Conventions

| Item | Format | Example |
|------|--------|---------|
| Weekly Note | `YYYY-Www` | `2026-W08` |
| Project Note | `YYYY-MM - Name` | `2026-02 - Website Redesign` |
| Meeting Note | `YYYY-MM-DD - Topic` | `2026-02-18 - Q1 Planning` |
| Area Note | Plain name | `Health`, `Finances` |
| Resource Note | Plain descriptive name | `Atomic Habits - Notes` |

---

## Tagging System

Use tags sparingly — the folder structure does most of the work.

| Tag | Meaning |
|-----|---------|
| `#status/active` | Currently being worked on |
| `#status/waiting` | Blocked, waiting on someone/something |
| `#status/done` | Completed (before archiving) |
| `#area/work` | Work-related |
| `#area/personal` | Personal life |
| `#meeting` | Meeting note |
| `#weekly-review` | Weekly note |

---

## Linking Philosophy

- Use `[[wikilinks]]` freely to connect related notes
- Every project note should link back to its parent area
- Weekly notes can link to project notes for context
- Resources can be linked from projects and areas that use them
- **Don't over-engineer links** — link when it's genuinely useful

---

## Recommended Obsidian Plugins

| Plugin | Why |
|--------|-----|
| **Templater** | Better templating than the core plugin (supports date math) |
| **Dataview** | Query notes like a database — powers the dashboard in `Home.md` |
| **Calendar** | Sidebar calendar for navigating weekly notes |
| **Periodic Notes** | Auto-creates weekly notes from template on schedule |

---

## Weekly Review Checklist

Run this every Monday (or Sunday evening):

1. **Inbox** — process everything in `00 - Inbox/`
2. **Projects** — review each active project; update next actions
3. **Areas** — check each area note; anything needing a new project?
4. **Calendar** — review past week and upcoming week
5. **Create weekly note** — use `_Templates/Weekly Note`

---

## The Golden Rule

> **Organize by where you'll look for it, not where it came from.**

When in doubt: put it in the Inbox and sort it during the weekly review.
