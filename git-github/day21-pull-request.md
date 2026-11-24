# Day 21 - Pull Requests

## What is a Pull Request?

A Pull Request (PR) is a request to merge changes from one branch into another branch after review.

## Commands Practiced

### Create Branch

```bash
git checkout -b feature-practice
```

### Commit Changes

```bash
git add .
git commit -m "message"
```

### Push Branch

```bash
git push -u origin feature-practice
```

### Delete Branch After Merge

```bash
git branch -d feature-practice

git push origin --delete feature-practice
```

## Pull Request Workflow

```text
Branch
  ↓
Commit
  ↓
Push
  ↓
Pull Request
  ↓
Review
  ↓
Approval
  ↓
Merge
```

## Key Learnings

- Pull Requests enable code review.
- PRs help maintain code quality.
- PRs support team collaboration.
- Approved PRs can be merged into main.

## Status

✅ Completed
