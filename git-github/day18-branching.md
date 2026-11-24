# Day 18 - Git Branching

## What is a Branch?

A branch is an independent line of development in Git.

## Commands Practiced

### Check Branch

```bash
git branch
```

### Create Branch

```bash
git branch feature-branch
```

### Switch Branch

```bash
git checkout feature-branch
```

### Create and Switch

```bash
git checkout -b feature-branch
```

### Push Branch

```bash
git push origin feature-branch
```

## Bonus Branch Commands

### Show Local Branches

```bash
git branch
```

Example:

```text
dev
* main
```

---

### Show Remote Branches

```bash
git branch -r
```

Example:

```text
origin/main
origin/dev
```

---

### Show All Branches

```bash
git branch -a
```

Example:

```text
* main
  dev
  remotes/origin/main
  remotes/origin/dev
```

---

### Delete Local Branch

```bash
git branch -d dev
```

Use when branch is already merged.

---

### Force Delete Local Branch

```bash
git branch -D dev
```

Use when branch is not merged but you still want to delete it.

---

### Delete Remote Branch

```bash
git push origin --delete dev
```

Example Output:

```text
To github.com:user/repo.git
 - [deleted] dev
```

---

### Rename Current Branch

```bash
git branch -m new-branch-name
```

Example:

```bash
git branch -m feature-login
```

---

### Rename Another Branch

```bash
git branch -m old-name new-name
```

Example:

```bash
git branch -m dev development
```

---

### View Current Branch

```bash
git branch --show-current
```

Example Output:

```text
main
```

---

### Switch Branch

```bash
git switch dev
```

or

```bash
git checkout dev
```

---

### Create and Switch Branch

```bash
git switch -c feature-terraform
```

or

```bash
git checkout -b feature-terraform
```

---

## Key Learnings

- `git branch` shows local branches.
- `git branch -r` shows remote branches.
- `git branch -a` shows all branches.
- `git branch -d` deletes a local branch.
- `git branch -D` force deletes a local branch.
- `git push origin --delete` deletes a remote branch.
- `git switch` is the modern way to change branches.

## Real DevOps Workflow

```bash
git checkout -b feature-jenkins

# Work on code

git add .
git commit -m "Added Jenkins pipeline"

git push -u origin feature-jenkins

# After merge

git checkout main

git pull origin main

git branch -d feature-jenkins

git push origin --delete feature-jenkins
```

## Key Learnings

- Branches isolate changes.
- Main branch should remain stable.
- Features are developed in separate branches.
- Branches can be merged later.

## Status

✅ Completed
