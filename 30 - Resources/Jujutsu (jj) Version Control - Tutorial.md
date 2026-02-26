---
created: 2026-02-26
updated: 2026-02-26
tags:
  - resource/tutorial
  - tech/version-control
---

# Jujutsu (jj) Version Control - Tutorial

Jujutsu (jj) is a modern version control system that serves as a powerful alternative to Git. It offers a more intuitive mental model, better handling of conflicts, and a cleaner command structure.

## What Makes Jujutsu Different?

### Key Concepts

1. **Every change is automatically committed** - No staging area to worry about
2. **Working copy is a commit** - Your current changes are always tracked
3. **Conflicts are first-class citizens** - You can commit and work with conflicted states
4. **Immutable history with pointers** - Operations create new commits rather than modifying existing ones
5. **Git-compatible** - Can work with Git repositories and remotes

### Advantages Over Git

- **Simpler mental model** - No staging area confusion
- **Built-in co-located repos** - Can use jj in Git repos without conflict
- **Better conflict resolution** - Conflicts are materialized as files you can edit
- **Undo anything** - True operation log with easy rollback
- **Automatic commit messages** - Generates descriptions based on changes
- **No detached HEAD states** - Everything is a proper branch

---

## Installation

### macOS
```bash
brew install jj
```

### Linux
```bash
cargo install --git https://github.com/martinvonz/jj.git jj-cli
```

### Windows
```bash
cargo install --git https://github.com/martinvonz/jj.git jj-cli
```

Or download binaries from: https://github.com/martinvonz/jj/releases

---

## Tutorial: Learning Jujutsu

### 1. Initialize a Repository

Create a new jj repository:
```bash
jj init my-project
cd my-project
```

Or use jj with an existing Git repository:
```bash
cd existing-git-repo
jj git init --colocate
```

The `--colocate` flag means jj and git share the same working directory.

### 2. Understanding the Working Copy

Check status:
```bash
jj status
```

Unlike Git, your working directory changes are automatically part of a commit. Create a file and check status:

```bash
echo "Hello Jujutsu" > README.md
jj status
```

You'll see the working copy commit has changed.

### 3. Creating Commits (Describing Changes)

In jj, you "describe" changes rather than "commit" them:

```bash
jj describe -m "Add README file"
```

This updates the description of your current working copy commit. Now create a new change:

```bash
jj new
```

This creates a new working copy commit on top of the current one. The previous change is now immutable.

**Alternative workflow** - describe and create new change in one step:
```bash
echo "More content" >> README.md
jj commit -m "Add more content to README"
```

The `jj commit` command describes the current change and creates a new working copy.

### 4. Viewing History

See the log of changes:
```bash
jj log
```

The output shows a graph with:
- `@` - Your current working copy
- `◉` - Other commits
- Change IDs (unique identifiers)
- Commit IDs (Git-compatible hashes)

For more detail:
```bash
jj log -r 'all()'
jj show  # Show current change
```

### 5. Making Changes and Amending

Edit files as normal:
```bash
echo "Line 2" >> README.md
jj status
jj diff
```

Your changes are automatically in the working copy. To describe them:
```bash
jj describe -m "Updated description"
```

### 6. Branching

Create a branch at the current commit:
```bash
jj branch create feature-x
```

List branches:
```bash
jj branch list
```

Switch to a different commit/branch:
```bash
jj new main  # Create new change based on main
```

### 7. Rebasing and Moving Changes

Move the current change to a different parent:
```bash
jj rebase -d main
```

Move a specific change:
```bash
jj rebase -s <change-id> -d <destination>
```

### 8. Conflict Resolution

jj lets you commit conflicted states. When conflicts occur:

```bash
jj status  # Shows conflicts
jj diff     # Shows conflict markers in files
```

Edit the files to resolve conflicts, then:
```bash
jj describe -m "Resolve conflicts"
```

### 9. Undoing Operations

View operation log:
```bash
jj op log
```

Undo the last operation:
```bash
jj undo
```

Restore to a specific operation:
```bash
jj op restore <operation-id>
```

This is like time travel - you can undo commits, rebases, merges, anything!

### 10. Working with Git Remotes

Add a remote:
```bash
jj git remote add origin https://github.com/user/repo.git
```

Fetch changes:
```bash
jj git fetch
```

Push changes:
```bash
jj git push
```

Pull changes (fetch + rebase):
```bash
jj git fetch
jj rebase -d main@origin
```

### 11. Squashing Changes

Squash current change into parent:
```bash
jj squash
```

Squash specific changes:
```bash
jj squash -r <change-id>
```

### 12. Splitting Changes

Split the current change interactively:
```bash
jj split
```

This opens an editor where you can select which changes go into which commit.

---

## Cheatsheet

### Repository Setup
| Command | Description |
|---------|-------------|
| `jj init` | Create new jj repository |
| `jj git init --colocate` | Use jj in existing Git repo |
| `jj git clone <url>` | Clone a Git repository |

### Basic Workflow
| Command | Description |
|---------|-------------|
| `jj status` | Show working copy status |
| `jj diff` | Show changes in working copy |
| `jj describe -m "msg"` | Describe current change |
| `jj commit -m "msg"` | Describe change and create new working copy |
| `jj new` | Create new empty working copy |
| `jj new <change-id>` | Create change on top of specific commit |

### Viewing History
| Command | Description |
|---------|-------------|
| `jj log` | Show commit history graph |
| `jj log -r 'all()'` | Show full history |
| `jj show` | Show current change details |
| `jj show <change-id>` | Show specific change |

### Branching
| Command | Description |
|---------|-------------|
| `jj branch create <name>` | Create branch at current commit |
| `jj branch list` | List all branches |
| `jj branch set <name> -r <change>` | Move branch to different commit |
| `jj branch delete <name>` | Delete a branch |

### Navigation
| Command | Description |
|---------|-------------|
| `jj new main` | Create change based on main branch |
| `jj edit <change-id>` | Edit a specific commit (make it working copy) |

### Rebasing & Moving
| Command | Description |
|---------|-------------|
| `jj rebase -d <dest>` | Rebase current change onto destination |
| `jj rebase -s <src> -d <dest>` | Rebase source commit to destination |
| `jj rebase -b <branch> -d <dest>` | Rebase entire branch |

### Squashing & Splitting
| Command | Description |
|---------|-------------|
| `jj squash` | Squash current change into parent |
| `jj squash -r <change-id>` | Squash specific change into parent |
| `jj split` | Interactively split current change |

### Conflict Resolution
| Command | Description |
|---------|-------------|
| `jj status` | Check for conflicts |
| `jj diff` | View conflict markers |
| (edit files manually, then describe) | Resolve conflicts |

### Undo & History
| Command | Description |
|---------|-------------|
| `jj op log` | View operation history |
| `jj undo` | Undo last operation |
| `jj op restore <op-id>` | Restore to specific operation |

### Git Integration
| Command | Description |
|---------|-------------|
| `jj git remote add <name> <url>` | Add Git remote |
| `jj git fetch` | Fetch from Git remote |
| `jj git push` | Push to Git remote |
| `jj git push --branch <branch>` | Push specific branch |

### Advanced
| Command | Description |
|---------|-------------|
| `jj abandon` | Abandon current change (remove from history) |
| `jj duplicate` | Create copy of current change |
| `jj resolve` | Resolve conflicts with a tool |
| `jj absorb` | Automatically squash changes into relevant commits |

---

## Common Workflows

### Feature Development
```bash
# Start a new feature
jj new main
jj branch create feature-login

# Make changes
echo "code" > login.js
jj commit -m "Add login functionality"

# More changes
echo "more code" >> login.js
jj commit -m "Improve login validation"

# Push to remote
jj git push --branch feature-login
```

### Fixing a Mistake
```bash
# Made a mistake in last change
jj undo

# Or edit a specific past commit
jj edit <change-id>
# Make fixes
jj describe -m "Fixed version"
jj new  # Return to tip
```

### Updating Feature Branch
```bash
# Fetch latest main
jj git fetch

# Rebase your branch
jj rebase -d main@origin
```

### Cleaning Up Before Push
```bash
# Squash last two changes
jj squash -r @  # Squash current into parent

# Or interactively split a change
jj split
```

---

## Key Differences from Git

| Concept | Git | Jujutsu |
|---------|-----|---------|
| Working directory | Not tracked until staged | Always a commit |
| Staging area | Required for commits | Doesn't exist |
| Amending | `git commit --amend` | Automatic (just describe) |
| Branching | `git checkout -b` | `jj new` + `jj branch create` |
| Rewriting history | Dangerous | Safe with operation log |
| Conflicts | Must resolve before commit | Can commit conflicted state |
| Undo | Complex reflog | Simple `jj undo` |

---

## Tips & Best Practices

1. **Use `jj log` frequently** - The visual graph helps understand the repository state
2. **Don't fear conflicts** - jj makes them easy to handle; you can even commit them
3. **Leverage the operation log** - `jj op log` and `jj undo` are your safety net
4. **Use change IDs** - They're more stable than commit hashes
5. **Describe changes meaningfully** - While jj auto-generates descriptions, manual ones are clearer
6. **Explore with `jj new`** - Cheap to create new working copies for experimentation
7. **Squash before pushing** - Clean up local history with `jj squash`
8. **Co-locate with Git** - Use `--colocate` to keep Git compatibility for teams

---

## Resources

- **Official Documentation**: https://martinvonz.github.io/jj/
- **GitHub Repository**: https://github.com/martinvonz/jj
- **Tutorial Videos**: Search for "Jujutsu version control" on YouTube
- **Community**: Join discussions on GitHub Issues and Discord

---

## Next Steps

1. Install jj and initialize a test repository
2. Practice the basic workflow: `new` → edit → `commit`
3. Experiment with `jj undo` to see how safe operations are
4. Try using jj in a colocated Git repository
5. Explore advanced features like `jj absorb` and `jj split`

Happy version controlling! 🎯
