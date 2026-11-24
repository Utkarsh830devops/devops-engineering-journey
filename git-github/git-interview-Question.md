# Git & GitHub Interview Questions for DevOps Engineers

## Basic Git Questions

### 1. What is Git?

Git is a distributed version control system used to track and manage changes in source code and files.

---

### 2. What is Version Control?

Version Control is a system that tracks changes in files and allows teams to collaborate efficiently.

---

### 3. What is the difference between Git and GitHub?

| Git | GitHub |
|------|---------|
| Version Control Tool | Cloud Platform |
| Works Locally | Works Online |
| Tracks Changes | Hosts Repositories |

---

### 4. What is a Git Repository?

A Git repository is a directory that contains project files and Git history.

---

### 5. What is the difference between Local Repository and Remote Repository?

| Local | Remote |
|---------|---------|
| Stored on Laptop | Stored on GitHub |
| Personal Changes | Shared Changes |

---

## Git Commands

### 6. How do you initialize a repository?

```bash
git init
```

---

### 7. How do you clone a repository?

```bash
git clone <repository-url>
```

---

### 8. How do you check repository status?

```bash
git status
```

---

### 9. How do you see commit history?

```bash
git log
```

Short version:

```bash
git log --oneline
```

---

## add, commit, push, pull

### 10. What does git add do?

Moves changes from the Working Directory to the Staging Area.

```bash
git add .
```

---

### 11. What does git commit do?

Creates a snapshot of staged changes.

```bash
git commit -m "message"
```

---

### 12. What does git push do?

Uploads local commits to a remote repository.

```bash
git push origin main
```

---

### 13. What does git pull do?

Downloads and merges changes from the remote repository.

```bash
git pull origin main
```

---

### 14. Difference between git fetch and git pull?

| git fetch | git pull |
|------------|-----------|
| Downloads changes | Downloads + Merges changes |
| Does not modify working directory | Updates working directory |

---

## Branching

```bash
git branch dev
```

or

```bash
git checkout -b dev
```

---

### 18. How do you switch branches?

```bash
git checkout dev
```

or

```bash
git switch dev
```

---

### 19. How do you list branches?

```bash
git branch
```

All branches:

```bash
git branch -a
```

---

### 20. How do you delete a branch?

Local:

```bash
git branch -d dev
```

Force delete:

```bash
git branch -D dev
```

Remote:

```bash
git push origin --delete dev
```

---

## Merge


A merge conflict occurs when Git cannot automatically merge changes from two branches.

---

### 26. Why do Merge Conflicts occur?

- Same file modified
- Same line modified
- Git cannot decide which version to keep

---

### 27. How do you resolve a Merge Conflict?

1. Open file
2. Remove conflict markers
3. Keep required code
4. Save file
5. Add file

```bash
git add .
git commit -m "Resolved conflict"
```

---

### 28. How do you abort a merge?

```bash
git merge --abort
```

---

### 29. What does --ours mean?

```bash
git checkout --ours file.txt
```

Keeps current branch version.

---

### 30. What does --theirs mean?

```bash
git checkout --theirs file.txt
```

Keeps incoming branch version.

---

## Pull Requests

### 31. What is a Pull Request?

A Pull Request (PR) is a request to merge changes from one branch into another after review.

---

### 32. Why do we use Pull Requests?

- Code Review
- Collaboration
- Approval Process
- Quality Control

---

### 33. What happens after a Pull Request is approved?

The changes can be merged into the target branch.

---

### 34. Can a Pull Request be rejected?

Yes.

Reviewers can:

- Request Changes
- Reject Changes
- Ask Questions

---

## GitHub

### 35. What is GitHub?

GitHub is a cloud-based platform used to host Git repositories.

---

### 36. Why is GitHub used?

- Source Code Hosting
- Collaboration
- Pull Requests
- CI/CD Integration

---

### 37. What is Forking?

Forking creates a personal copy of another repository in your GitHub account.

---

### 38. What is the difference between Fork and Clone?

| Fork | Clone |
|--------|--------|
| GitHub Copy | Local Copy |
| Cloud | Laptop |

---

### 39. What is an Upstream Repository?

The original repository from which a fork was created.

---

### 40. What does this command do?

```bash
git push -u origin dev
```

### 44. How do teams generally work in Git?

```text
Feature Branch
     ↓
Commit
     ↓
Push
     ↓
Pull Request
     ↓
Code Review
     ↓
Merge
```

---

### 45. Explain a Git workflow used in your project.

```text
Create Feature Branch
        ↓
Implement Changes
        ↓
Commit
        ↓
Push to GitHub
        ↓
Raise Pull Request
        ↓
Code Review
        ↓
Merge into Main
        ↓
Deployment Pipeline Triggered
```

---

## Must Remember Commands

```bash
git status

git add .

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

git log --oneline

git log --oneline --graph --all

git branch -a

git branch -r

git push -u origin branch-name

git push origin --delete branch-name
```

---

# DevOps Interview Focus Areas

✅ Git Workflow

✅ Branching Strategy

✅ Pull Requests

✅ Merge Conflicts

✅ GitHub Collaboration

✅ fetch vs pull

✅ ours vs theirs

✅ Feature Branch Workflow

✅ Git Flow

✅ Real Project Git Workflow
