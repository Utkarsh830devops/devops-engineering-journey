
## Repository Basics

### Initialize Repository

```bash
git init
```

### Clone Repository

```bash
git clone <repo-url>
```

### Check Status

```bash
git status
```

### View Commit History

```bash
git log

git log --oneline

git log --oneline --graph --all
```

---

# Daily Workflow

```bash
git status

git add .

git commit -m "message"

git push
```

---

# Difference Between Git and GitHub

| Git | GitHub |
|--------|---------|
| Version Control Tool | Repository Hosting Platform |
| Local | Cloud |
| Tracks Changes | Stores Repositories |

---

# Git Areas

```text
Working Directory
      ↓
Staging Area
      ↓
Local Repository
      ↓
Remote Repository
```

---


### Fetch

```bash
git fetch
```

✅ Downloads changes

❌ Doesn't merge changes

---

### Pull

```bash
git pull
```

✅ Downloads changes

✅ Merges changes

Internally:

```bash
git fetch
git merge
```

---

# Merge

### Merge Branch

```bash
git checkout main

git merge dev
```

### Abort Merge

```bash
git merge --abort
```

---

# Merge Conflict

Occurs when:

```text
Same file
Same line
Different changes
```

### Check Conflict

```bash
git status
```

### Resolve

```bash
git add .

git commit -m "Resolved conflict"
```

---

# Ours vs Theirs

### Keep Current Branch

```bash
git checkout --ours file.txt
```

### Keep Incoming Branch

```bash
git checkout --theirs file.txt
```

---

# Pull Requests (PR)

Workflow:

```text
Feature Branch
      ↓
Push
      ↓
Pull Request
      ↓
Review
      ↓
Merge
```

### Push Branch

```bash
git push -u origin feature-branch
```

---

# Fork vs Clone

| Fork | Clone |
|--------|--------|
| GitHub Copy | Local Copy |
| Cloud | Local Machine |
| For Open Source | For Development |

---

# Private Repository

Visible only to authorized users.

Used for:

- Company Projects
- Terraform Code
- Internal Documents
- Jenkins Pipelines

---

# Collaborator

Admin
```

---

# Protected Branch

Usually:

```text
main
master
production
```

Rules:

✅ PR Required

✅ Approval Required

✅ CI/CD Checks Required

❌ Direct Push Restricted

---

# Tags

Used for releases.

Examples:

```text
v1.0
v1.1
v2.0
```

### Create Tag

```bash
git tag v1.0
```

### Annotated Tag

```bash
git tag -a v1.0 -m "Release v1.0"
```

### View Tags

```bash
git tag
```

### Push Tag

```bash
git push origin v1.0
```

### Push All Tags

```bash
git push origin --tags
```

---

# Restore

## Discard Working Directory Changes

```bash
git restore file.txt
```

### Works On

✅ Tracked Files

❌ Untracked Files

---

## Unstage File

```bash
git restore --staged file.txt
```

---

# Reset

## Unstage File

```bash
git reset file.txt
```

---

## Soft Reset

```bash
git reset --soft HEAD~1
```

Result:

```text
Commit removed
Changes staged
```

---

## Mixed Reset

```bash
git reset --mixed HEAD~1
```

Result:

```text
Commit removed
Changes unstaged
```

---

## Hard Reset

```bash
git reset --hard HEAD~1
```

Result:

```text
Commit removed
Changes removed
```

⚠️ Dangerous

---

# Revert

Safe production rollback.

```bash
git revert <commit-id>
```

### Latest Commit

```bash
git revert HEAD
```

### Result

```text
Original commit remains
New reverse commit created
```

---

# Reset vs Revert

| Reset | Revert |
|--------|--------|
| Rewrites History | Preserves History |
| Dangerous | Safe |
| Removes Commit | Creates Reverse Commit |

---

# Rebase

### Rebase Branch

```bash
git rebase main
```

Purpose:

```text
Creates Linear History
```

---

### Continue Rebase

```bash
git rebase --continue
```


```bash
git rebase -i HEAD~3
```

---

# Merge vs Rebase

| Merge | Rebase |
|--------|--------|
| Merge Commit | No Merge Commit |
| Keeps Branch History | Linear History |
| Simple | Clean |

---

# Cherry Pick

Copy one commit from another branch.

```bash
git cherry-pick <commit-id>
```

Use Case:

```text
Need only one bug fix
Don't want full merge
```

---

# Enterprise Workflow

```text
feature/*
      ↓
dev
      ↓
uat
      ↓
release/v1.0
      ↓
main
      ↓
v1.0 Tag
```

---

# Hotfix Workflow

```text
main
  ↓
hotfix/risk-fix
  ↓
main
  ↓
v1.0.1 Tag
```

### Create Hotfix

```bash
git checkout main

git checkout -b hotfix/risk-fix
```

---

# Production Rollback

### Preferred

```bash
git revert <commit-id>
```

### Alternative

```bash
git checkout v1.0
```

---

# Most Asked Interview Questions

### Difference Between Fetch and Pull?

Fetch downloads.

Pull downloads + merges.

---

### Difference Between Merge and Rebase?

Merge preserves history.

Rebase creates linear history.

---

### Difference Between Reset and Revert?

Reset rewrites history.

Revert preserves history.

---

### Why Protected Branches?

To prevent direct production changes.

---

### Why Tags?

git commit -m "message"

git push

git pull

git fetch

git clone

git branch

git checkout

git switch

git merge

git merge --abort

git restore

git restore --staged

git reset

git reset --soft HEAD~1

git reset --hard HEAD~1

git revert

git rebase

git rebase --continue

git rebase --abort

git cherry-pick

git tag

git push --tags

git branch -vv

git log --oneline --graph --all
```

---

# Interview One-Liners

✅ Fetch = Download only

✅ Pull = Fetch + Merge

✅ Merge = Join histories

✅ Rebase = Rewrite history

✅ Reset = Remove commits

✅ Revert = Safe rollback

✅ Tag = Release marker

✅ PR = Code review process

✅ Protected Branch = No direct production changes

✅ Cherry Pick = Copy one commit

✅ Hotfix = Emergency production fix
