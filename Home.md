# Home

> Your personal command center. Start here every day.

---

## Quick Capture

- [[00 - Inbox/README|Go to Inbox]] — drop anything here first, sort later

---

## Active Projects

### Work
```dataview
LIST
FROM "10 - Projects/Work"
WHERE status = "active"
SORT file.mtime DESC
```
> *No dataview plugin? Browse [[10 - Projects/Work]] directly.*

### Personal
```dataview
LIST
FROM "10 - Projects/Personal"
WHERE status = "active"
SORT file.mtime DESC
```
> *No dataview plugin? Browse [[10 - Projects/Personal]] directly.*

---

## Weekly Notes

- [[Weekly Notes/{{date:YYYY-[W]WW}}|This Week]]

Recent weeks:
```dataview
LIST
FROM "Weekly Notes"
SORT file.name DESC
LIMIT 5
```

---

## Areas

### Work
- [[20 - Areas/Work|Work Areas]]

### Personal
- [[20 - Areas/Personal/Health|Health]]
- [[20 - Areas/Personal/Finances|Finances]]
- [[20 - Areas/Personal/Learning|Learning]]
- [[20 - Areas/Personal/Home|Home]]

---

## Resources & Reference

- [[30 - Resources|Browse Resources]]

---

## Meta
- [[_Meta/How This Vault Works|How This Vault Works]]
- [[40 - Archive|Archive]]
