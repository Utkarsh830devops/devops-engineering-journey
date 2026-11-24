# Day 19 - Git Merge

## What is Merge?

Merge combines changes from one branch into another branch.

## Commands Practiced

### Create Branch

```bash
git checkout -b feature-merge
```

### Commit Changes

```bash
git add .
git commit -m "message"
```

### Switch to Main

```bash
git checkout main
```

### Merge Branch

```bash
git merge feature-merge
```

### Push Changes

```bash
git push origin main
```

### Delete Local Branch

```bash
git branch -d feature-merge
```

### Delete Remote Branch

```bash
git push origin --delete feature-merge
```

## Key Learnings

- Merge combines branch changes.
- Main branch receives feature code.
- Git supports fast-forward merges.
- Cleanup branches after successful merge.

## Status

✅ Completed
