```text
test1.txt
test2.txt
```

They are untracked.

How do you remove them?

### Preview

```bash
git clean -n
```

### Delete

```bash
git clean -f
```

---

## Scenario 4: Last Commit Message is Wrong

### Question

You committed:

```bash
git commit -m "updted terraform"
```

Need to fix the message.

### Answer

```bash
git commit --amend -m "Updated Terraform Configuration"
```

---

## Scenario 5: Remove Last Commit But Keep Changes

### Question

Last commit is wrong but code is correct.

Need to remove commit only.

### Answer

```bash
git reset --soft HEAD~1
```

Result:

```text
Commit removed
Changes staged
```

---

## Scenario 6: Remove Last Commit And Unstage Changes

### Question

Need to remove commit and move files back to working directory.

### Answer


### Question

Terraform code deployed to production caused issues.

Need to rollback safely.

### Answer

Preferred:

```bash
git revert <commit-id>
```

Reason:

```text
Preserves history
Creates rollback commit
Safe for production
```

---

## Scenario 9: Hotfix Required in Production

### Question

A critical bug is found in production.

How would you fix it?

### Answer

```bash
git checkout main

git checkout -b hotfix/risk-fix
```

Make changes.

```bash
git add .
git commit -m "Fixed risk calculation bug"
```

Merge back:

```bash
hotfix/risk-fix
      ↓
main
```

---

## Scenario 10: Need Only One Commit

### Question

You need one bug-fix commit from another branch.

Do not want the whole branch.

### Answer

```bash
git cherry-pick <commit-id>
```

---

```bash
git status
```

Open file.

Resolve:

```bash
<<<<<<< HEAD
=======
>>>>>>> feature-branch
```

Remove markers.

```bash
git add .

git commit -m "Resolved merge conflict"
```

---

## Scenario 13: Keep Current Version During Conflict

### Question

Merge conflict occurred.

Need to keep current branch version.

### Answer

```bash
git checkout --ours file.txt
```

---

## Scenario 14: Keep Incoming Version During Conflict

### Question

Need to accept incoming branch version.

### Answer

```bash
git checkout --theirs file.txt
```

---

## Scenario 15: Cancel Merge

### Question

Merge started but want to stop it.

### Answer

```bash
git merge --abort
```

---

## Scenario 16: Cancel Rebase

### Question

```

Use:

```text
squash
```

to combine commits.

---

## Scenario 18: View Production Release

### Question

Need to inspect version:

```text
v1.0
```

### Answer

```bash
git checkout v1.0
```

---

## Scenario 19: Create Production Release

### Question

Application is ready for release.

### Answer

Create tag:

```bash
git tag -a v1.0 -m "Production Release"
```

Push:

```bash
git push origin v1.0
```

---

## Scenario 20: Accidentally Pushed Secret

### Question

AWS Access Key committed to repository.

### Answer

Immediate actions:

```text
1. Revoke/Rotate credentials
2. Remove secret from code
3. Commit fix
4. Rewrite history if required
5. Push cleaned version
```

---

## Scenario 21: Main Branch Protection

### Question

How do DevOps teams generally work with Terraform code?

### Answer

```text
Create Feature Branch
       ↓
Develop Terraform Changes
       ↓
Commit
       ↓
Push
       ↓
Pull Request
       ↓
Code Review
       ↓
Merge To Main
       ↓
Pipeline Deployment
```

---

## Scenario 23: Difference Between Fetch and Pull

### Question

Before starting work, why would you use fetch instead of pull?

### Answer

```bash
git fetch
```

Allows reviewing changes first:

```bash
git diff main origin/main
```

without modifying local code.

---

## Scenario 24: Interview Favorite

### Question

What Git strategy does your current team use?

### Sample Answer

```text
We follow a Feature Branch workflow.

Developers create feature branches from dev, commit changes, push to GitHub, create Pull Requests, get code reviewed, merge into dev, promote to UAT, create release branches, merge into main, and tag production releases.
```

---

# 🚀 Top 10 Commands Every DevOps Engineer Should Remember

```bash
git status

git add .

git commit -m "message"

git push

git pull

git fetch

git merge

git rebase

git revert

git log --oneline --graph --all
```
