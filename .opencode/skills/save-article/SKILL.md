---
name: save-article
description: Fetch a web article by URL, extract its main points as a summary, and save it as a resource note in the vault so it can be read even if the original is taken down.
argument-hint: <url>
disable-model-invocation: true
allowed-tools: WebFetch, Read, Write, Glob
---

# Save Article

Fetch and archive a web article into the vault as a resource note.

## Steps

1. **Fetch the article** at `$ARGUMENTS` using WebFetch.
2. **Extract metadata** from the page: title, author, publication date, source domain.
3. **Write a summary** section with:
   - A brief intro sentence explaining what the article argues.
   - A bullet-point list of the main points (aim for 5–10 bullets).
   - A pull-quote or conclusive recommendation if the article has one.
4. **Copy the full article text** (body only — no navigation, share buttons, sidebars, or footers) into a `## Full Text` section, preserving headings and structure as Markdown.
5. **Determine the filename**: `<Title> - <Author Last Name>.md` using Title Case. Strip any characters that are invalid in file names.
6. **Create the note** at `30 - Resources/<filename>` using the template below.
7. **Report back** with the file path and a short recap of what was saved.

## Note template

```markdown
---
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags:
  - area/work
---

# <Title> — <Author>

**Author:** <Author>
**Published:** <Date>
**Source:** [<domain>](<url>)
**Reading time:** ~N minutes

---

## Summary

<intro sentence>

### Main points

- ...

---

## Full Text

<full article body>
```

## Rules

- Use today's date (`YYYY-MM-DD`) for both `created` and `updated`.
- Keep the `## Full Text` section faithful to the original — do not paraphrase it.
- Do not create the file in `00 - Inbox/` or anywhere other than `30 - Resources/`.
- Do not delete or overwrite existing notes; if a file with the same name exists, append ` (2)` to the filename.
- Only use the tags listed in AGENTS.md. Default to `area/work` unless the content is clearly personal.
