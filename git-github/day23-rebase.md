# Day 23 - Git Rebase

## What is Git Rebase?

Git Rebase is used to move or reapply commits from one branch on top of another branch.

Its main purpose is to create a clean and linear commit history.

---

## Why Use Rebase?

Suppose the main branch receives new commits while you are working on a feature branch.

### Before Rebase

```text
main

A --- B --- E --- F
       \
        C --- D (feature)
```

Your feature branch is behind the main branch.

---

## Rebase

```bash
git checkout feature

git rebase main
```

### After Rebase

```text
A --- B --- E --- F --- C' --- D'
```

Git moves your commits on top of the latest main branch.

---

## Rebase Workflow

### Switch to Feature Branch

```bash
git checkout feature-login
```

### Rebase with Main

```bash
git rebase main
```

Now feature-login contains the latest commits from main.

---

## Merge vs Rebase

### Merge

```bash
git merge main
```

Result:

```text
A --- B --- E
      \      \
       C --- D --- M
```

Produces a Merge Commit.

---

### Rebase

```bash
git rebase main
```

Result:

```text
A --- B --- E --- C' --- D'
```

Produces a clean linear history.

---

## Advantages of Rebase

- Cleaner Git history
- Easier troubleshooting
- Better commit visualization
- Cleaner Pull Requests

---

## Rebase Conflict

Sometimes both branches modify the same file.

Example:

```text
main modifies line 10
feature modifies line 10
```

Running:

```bash
git rebase main
```

may result in:

```text
CONFLICT
```

---

## Resolve Rebase Conflict

### Check Status

```bash
git status
```

### Fix Conflict

Edit the file manually.

### Stage Resolved File

```bash
git add .
```

### Continue Rebase

```bash
git rebase --continue
```

---

## Abort Rebase

If you want to cancel:

```bash
git rebase --abort
```

Git returns to the state before the rebase started.

---

## Interactive Rebase

Interactive rebase allows you to modify commit history.

```bash
git rebase -i HEAD~3
```

You can:

```text
pick
reword
squash
drop
edit
```

---

## Squash Commits

Before:

```text
Added file
Fixed typo
Updated file
```

After squash:

```text
Added file with updates
```

Single clean commit.

### Example

```bash
git rebase -i HEAD~3
```

Change:

```text
pick
squash
squash
```

---

## Common Commands

### Rebase Branch

```bash
git rebase main
```

### Continue Rebase

```bash
git rebase --continue
```

### Abort Rebase

```bash
git rebase --abort
```

### Interactive Rebase

```bash
git rebase -i HEAD~3
```

---

## Real DevOps Workflow

Keep feature branch updated with main:

```bash
git checkout feature-terraform

git fetch origin

git rebase main
```

Then push:

```bash
git push --force-with-lease
```

---

## Difference Between Merge and Rebase

| Merge | Rebase |
|---------|---------|
| Creates merge commit | No merge commit |
| Non-linear history | Linear history |
| Easier for beginners | Cleaner history |
| Preserves branch history | Rewrites branch history |

---

## Difference Between Rebase and Reset

| Rebase | Reset |
|---------|---------|
| Rearranges commits | Removes commits |
| Keeps work | May remove work |
| Clean history | Undo history |

---

## Difference Between Rebase and Revert

| Rebase | Revert |
|---------|---------|
| Rewrites commit history | Preserves history |
| Used for clean branches | Used for safe rollback |
| May require force push | Creates reverse commit |

---

## Interview Questions

### What is Git Rebase?

Git Rebase reapplies commits from one branch onto another branch to create a linear history.

---

### Why use Rebase?

- Clean history
- Easier debugging
- Smaller and cleaner Pull Requests

---

### Difference Between Merge and Rebase?

Merge combines histories and creates a merge commit.

Rebase rewrites history and creates a linear commit structure.

---

### How do you resolve a Rebase Conflict?

```bash
# Fix conflict manually

git add .

git rebase --continue
```

---

### How do you abort a Rebase?

```bash
git rebase --abort
```

---

### What is Interactive Rebase?

Interactive rebase allows modifying commit history such as:

- Squashing commits
- Renaming commits
- Removing commits

---

## Important Commands Cheat Sheet

```bash
git rebase main

git rebase --continue

git rebase --abort

git rebase -i HEAD~3

git fetch origin

git push --force-with-lease
```

---

## Key Learnings

✅ Rebase creates a clean linear history

✅ Rebase replays commits on top of another branch

✅ Rebase can create conflicts

✅ Interactive rebase is used for commit cleanup

✅ Rebase is commonly used before creating Pull Requests

---

## Status

✅ Completed
