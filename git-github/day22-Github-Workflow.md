# Day 22 - GitHub Workflows

## What is a Workflow?

A workflow is the process followed by teams to develop, review, and deploy code.

## Common Workflows

### Personal Workflow

main → Commit → Push

### Feature Branch Workflow

feature branch → PR → Merge

### Git Flow

main
develop
feature/*
release/*
hotfix/*

### Trunk-Based Development

Small feature branches merged frequently into main.

## Important Commands

### Show Tracking Branch

```bash
git branch -vv
```

### Fetch Changes

```bash
git fetch
```

### Pull Changes

```bash
git pull
```

### View Branch Graph

```bash
git log --oneline --graph --all
```

## Key Learnings

- Feature Branch Workflow is the most common workflow.
- Pull Requests enable reviews.
- Git Flow adds release and hotfix branches.
- fetch and pull are different.

## Status

✅ Completed
