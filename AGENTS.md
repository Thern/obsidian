# AGENTS.md — Obsidian Vault Guidelines

This file guides AI coding agents (Claude Code, OpenCode, Cursor, etc.) operating inside this Obsidian vault.

---

## What This Repo Is

This is a **personal knowledge management vault** using the [PARA method](https://fortelabs.com/blog/para/). It is not a software project — there are no build steps, tests, or linters. The "code" here is Markdown.

The vault tracks both work and personal projects, areas of ongoing responsibility, reference resources, and archived items.

---

## Folder Structure

```
Home.md                   # Dashboard — entry point
00 - Inbox/               # Unprocessed captures (sort during weekly review)
10 - Projects/            # Active projects with a clear outcome + deadline
  Work/
  Personal/
20 - Areas/               # Ongoing responsibilities with no end date
  Work/
  Personal/
30 - Resources/           # Reference material organized by topic
40 - Archive/             # Completed or inactive items from any category
Weekly Notes/             # One note per week, named YYYY-Www (e.g. 2026-W08)
_Templates/               # Note templates — do not use these directly as notes
_Meta/                    # Vault documentation and conventions
```

See `_Meta/How This Vault Works.md` for the full PARA guide.

---

## Core PARA Rules

- **Projects** have a defined outcome and are either active or done. When done, move to `40 - Archive/`.
- **Areas** have no end date — they represent ongoing standards to maintain.
- **Resources** are reference-only; no action required.
- **Inbox first** — all new captures go to `00 - Inbox/`, never filed directly.
- Never delete notes — move to `40 - Archive/` instead.

---

## File & Naming Conventions

| Note type     | Location                        | Naming format              | Example                          |
|---------------|---------------------------------|----------------------------|----------------------------------|
| Project       | `10 - Projects/Work/` or `Personal/` | `YYYY-MM - Name`      | `2026-02 - Website Redesign.md`  |
| Area          | `20 - Areas/Work/` or `Personal/`    | Plain name                | `Health.md`, `Engineering.md`    |
| Resource      | `30 - Resources/`               | Plain descriptive name     | `Atomic Habits - Notes.md`       |
| Weekly Note   | `Weekly Notes/`                 | `YYYY-Www`                 | `2026-W08.md`                    |
| Meeting Note  | Inside relevant project or area | `YYYY-MM-DD - Topic`       | `2026-02-18 - Q1 Planning.md`    |
| Archive       | `40 - Archive/`                 | Original name, unchanged   | —                                |

- Use **kebab-case or Title Case** for file names — be consistent within a folder.
- Folder names are prefixed with numbers (`00`, `10`, `20`, `30`, `40`) so they sort correctly in Obsidian's file explorer. Do not change these prefixes.
- Folders starting with `_` (`_Templates`, `_Meta`) are system folders — they appear at the top of the explorer and should not hold regular notes.

---

## Markdown Style

- **Headings:** Use `#` for the note title, `##` for major sections, `###` for subsections. Don't skip levels.
- **Frontmatter:** All notes should have YAML frontmatter at the top. See templates for the expected fields.
- **Links:** Use Obsidian wikilinks `[[Note Name]]` for internal links. Use standard `[text](url)` for external links.
- **Tags:** Use `#tag/subtag` format. See the tagging system below.
- **Checkboxes:** Use `- [ ]` for tasks, `- [x]` for completed tasks.
- **Tables:** Use Markdown tables for structured data (e.g. recurring tasks, action items).
- **Callouts:** Use Obsidian callout syntax `> [!note]`, `> [!warning]`, `> [!tip]` for highlighted content.
- **Blank lines:** Add a blank line between sections for readability.
- **No trailing spaces.**

### Frontmatter Fields

```yaml
---
created: YYYY-MM-DD
updated: YYYY-MM-DD      # update this when you edit the note
status: active           # active | waiting | done (for projects)
tags:
  - status/active
  - area/work
---
```

---

## Tagging System

Use tags sparingly — the folder structure carries most of the organizational weight.

| Tag | Meaning |
|-----|---------|
| `#status/active` | Currently being worked on |
| `#status/waiting` | Blocked or waiting on someone/something |
| `#status/done` | Completed (before archiving) |
| `#area/work` | Work-related note |
| `#area/personal` | Personal life note |
| `#meeting` | Meeting note |
| `#weekly-review` | Weekly note |

---

## Templates

Always use templates when creating new notes. Templates live in `_Templates/`.

| Template | Use for |
|----------|---------|
| `_Templates/Project.md` | Every new project |
| `_Templates/Weekly Note.md` | Monday of each week |
| `_Templates/Meeting.md` | Any meeting with action items |
| `_Templates/Area.md` | Creating a new area note |

When creating a note as an agent, copy the relevant template's structure manually (Obsidian's Templater plugin handles `{{date}}` substitution automatically when using the UI; when creating via CLI/agent, substitute dates yourself using `YYYY-MM-DD` format).

---

## Agent Instructions

### Creating a new project

1. Create a file in `10 - Projects/Work/` or `10 - Projects/Personal/`
2. Name it `YYYY-MM - Project Name.md`
3. Use the structure from `_Templates/Project.md`
4. Set frontmatter: `status: active`, appropriate tags
5. Link it from `Home.md` if it's a top priority

### Creating a new area

1. Create a file in `20 - Areas/Work/` or `20 - Areas/Personal/`
2. Use a plain descriptive name (e.g. `Engineering.md`)
3. Use the structure from `_Templates/Area.md`

### Creating a weekly note

1. Create a file in `Weekly Notes/` named `YYYY-Www.md` (e.g. `2026-W08.md`)
2. Use the structure from `_Templates/Weekly Note.md`
3. Fill in the week date range at the top

### Archiving a completed project

1. Move the file from `10 - Projects/` to `40 - Archive/`
2. Update frontmatter: `status: done`, `updated: YYYY-MM-DD`
3. Add a brief retrospective note at the bottom of the file

### Adding a resource

1. Create a file in `30 - Resources/`
2. Use a plain descriptive name
3. No required frontmatter beyond `created` date

### Capturing a quick note

1. Drop it in `00 - Inbox/` with any filename
2. Do not attempt to file it further — leave triage to the weekly review

---

## What Agents Should NOT Do

- Do not modify files in `_Templates/` unless explicitly asked to update a template
- Do not modify `_Meta/How This Vault Works.md` unless explicitly asked
- Do not rename or renumber the top-level folders (`00 - Inbox`, `10 - Projects`, etc.)
- Do not delete notes — move to `40 - Archive/` instead
- Do not create deeply nested subfolder hierarchies — PARA intentionally stays shallow (max 2 levels deep inside each top-level folder)
- Do not add tags that aren't in the tagging system above without asking first

---

## OpenCode Commands

Custom commands live in `.opencode/commands/` and are invoked with `/` in the TUI.

| Command | Description |
|---------|-------------|
| `/sync` | Stage all changes, commit with a timestamp message, and push to GitHub |

### `/sync`

Runs `git add -A && git commit -m "vault: update notes YYYY-MM-DD HH:MM" && git push`.

Use this whenever you want to save the current state of the vault to GitHub. The LLM will report back whether the push succeeded or if there were any errors.

---

## Obsidian-Specific Notes

This vault is designed for [Obsidian](https://obsidian.md). Recommended plugins:

| Plugin | Purpose |
|--------|---------|
| **Templater** | Date-aware templates; set template folder to `_Templates/` |
| **Dataview** | Powers the query blocks in `Home.md` and area notes |
| **Calendar** | Sidebar calendar for navigating weekly notes |
| **Periodic Notes** | Auto-creates weekly notes from template |

The `Home.md` dashboard uses Dataview query blocks. These render in Obsidian but will appear as fenced code blocks in plain Markdown editors — this is expected.
