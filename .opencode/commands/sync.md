---
description: Commit all vault changes and push to GitHub
---

Run these git commands and report the result concisely:

!`git add -A && git commit -m "vault: update notes $(date '+%Y-%m-%d %H:%M')" && git push 2>&1 || echo "Git command failed with exit code: $?"`

If there was nothing to commit, say so. If there was an error, explain it clearly.
