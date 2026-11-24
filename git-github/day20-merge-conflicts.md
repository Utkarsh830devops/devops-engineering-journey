# Day 20 - Merge Conflicts

## What is a Merge Conflict?

A merge conflict occurs when Git cannot automatically merge changes from two branches.

## Commands Practiced

### Merge Branch

```bash
git merge feature-branch
```

### Check Status

```bash
git status
```

### View Difference

```bash
git diff
```

### Abort Merge

```bash
git merge --abort
```

### Resolve Conflict

```bash
git add file-name

git commit -m "Resolved merge conflict"
```

## Conflict Markers

```text
<<<<<<< HEAD
Current Branch Changes
=======
Incoming Branch Changes
>>>>>>> feature-branch
```
## ⭐ Super Important: Ours vs Theirs

During a merge conflict, Git provides special options to keep either your current branch version or the incoming branch version.

---

### Keep Current Branch Version

```bash
git checkout --ours file.txt
```

Meaning:

```text
Keep the version from the branch you are currently on.
Discard the incoming branch changes.
```

Example:

Current Branch:

```text
replicas: 2
```

Incoming Branch:

```text
replicas: 3
```

Command:

```bash
git checkout --ours deployment.yaml
```

Result:

```text
replicas: 2
```

✅ Current branch version retained.

---

### Keep Incoming Branch Version

```bash
git checkout --theirs file.txt
```

Meaning:

```text
Keep the version from the branch being merged.
Discard the current branch changes.
```

Example:

Current Branch:

```text
replicas: 2
```

Incoming Branch:

```text
replicas: 3
```

Command:

```bash
git checkout --theirs deployment.yaml
```

Result:

```text
replicas: 3
```

✅ Incoming branch version retained.

---

## Complete Workflow

### Keep Current Branch Version

```bash
git checkout --ours file.txt
git add file.txt
git commit -m "Resolved conflict using current branch version"
```

---

### Keep Incoming Branch Version

```bash
git checkout --theirs file.txt
git add file.txt
git commit -m "Resolved conflict using incoming branch version"
```

---

## Real DevOps Example

Suppose a conflict occurs in:

```text
Jenkinsfile
```

Current Branch:

```groovy
docker build -t app:v1 .
```

Incoming Branch:

```groovy
docker build -t app:v2 .
```

To keep current branch:

```bash
git checkout --ours Jenkinsfile
```

To keep incoming branch:

```bash
git checkout --theirs Jenkinsfile
```

---

## Interview Question

### What is the difference between `--ours` and `--theirs`?

| Command | Meaning |
|----------|----------|
| `git checkout --ours file.txt` | Keep current branch version |
| `git checkout --theirs file.txt` | Keep incoming branch version |

### When would you use them?

When resolving merge conflicts and you want to accept one side's changes without manually editing the file.

---


## Key Learnings

- Conflicts happen when the same lines are modified.
- Git cannot automatically decide which version to keep.
- Manual resolution is required.
- Remove conflict markers before committing.

## Status

✅ Completed


