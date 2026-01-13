
##  `branching/branching.md`

<img width="1921" height="1057" alt="image" src="https://github.com/user-attachments/assets/54d9b2aa-bced-432c-991b-336938af203d" />

````markdown
````
# Git Branching & Merging – Step by Step

This document is a **team-ready guide** covering:
- Branching and merging fundamentals
- Real-world workflows
- PR, code review, and CI/CD integration
- Conflict and rebase scenarios
- Best practices used in production teams

---

## 📚 Index

1. [View Current Branch](#1.-view-current-branch)
2. [Create a New Branch](#create-a-new-branch)
3. [Switch to the New Branch](#switch-to-the-new-branch)
4. [Make Changes in Feature Branch](#make-changes-in-feature-branch)
5. [Switch Back to Main](#switch-back-to-main)
6. [Merge Feature Branch into Main](#merge-feature-branch-into-main)
7. [Delete Feature Branch](#delete-feature-branch)
8. [View All Branches](#view-all-branches)
9. [Visual Diagram – Basic Branching](#visual-diagram--basic-branching)
10. [Fast-Forward vs Merge Commit](#fast-forward-vs-merge-commit)
11. [Merge vs Rebase](#merge-vs-rebase)
12. [Real-World Developer Workflow](#real-world-developer-workflow)
13. [PR / Code Review Flow](#pr--code-review-flow)
14. [CI/CD Interaction with Branches](#cicd-interaction-with-branches)
15. [Real Merge Conflict Scenario](#real-merge-conflict-scenario)
16. [Real Rebase Conflict Scenario](#real-rebase-conflict-scenario)
17. [Common Mistakes](#common-mistakes)
18. [Best Practices](#best-practices)
19. [Team Branching Strategies](#team-branching-strategies)
20. [Final Mental Model](#final-mental-model)


---

## 1. View Current Branch 


```bash
git branch
````

**Explanation:**

* Lists all local branches
* `*` marks the active branch
* Default branch is usually `main`

<img width="275" height="184" alt="image" src="https://github.com/user-attachments/assets/3000020f-c43f-4b12-ad38-7b79fb2d97d5" />


---

##  Create a New Branch

```bash
git branch feature-branch
```

**Explanation:**

* Creates a new branch
* Does NOT switch to it
* Both branches point to the same commit

---

##  Switch to the New Branch

```bash
git checkout feature-branch
```

### Alternative (Git 2.23+)

```bash
git switch feature-branch
```

**Explanation:**

* Working directory switches to feature branch
* New commits go here

---

##  Make Changes in Feature Branch

```bash
echo "Feature work" >> feature.txt
git add feature.txt
git commit -m "Added feature.txt in feature-branch"
```

**Explanation:**

* Commit exists only on feature branch
* `main` remains stable

---

##  Switch Back to Main

```bash
git checkout main
```

**Explanation:**

* Feature changes are not yet in `main`

---

##  Merge Feature Branch into Main

```bash
git merge feature-branch
```

**Explanation:**

* Integrates feature work
* Creates merge commit if histories diverged

---

##  Delete Feature Branch

```bash
git branch -d feature-branch
```

**Explanation:**

* Safe cleanup after merge

---

##  View All Branches

```bash
git branch      # Local
git branch -a   # Local + Remote
```

---

#  Visual Diagram – Basic Branching

## Initial State

```
main (HEAD)
*
| Initial commit
```

## Feature Branch Created

```
main
*
| Initial commit
 \
  feature-branch (HEAD)
```

## Commit on Feature Branch

```
main
*
| Initial commit
 \
  feature-branch (HEAD)
  *
  | Added feature.txt
```

## Merge into Main

```
main (HEAD)
*
| Merge commit
|\
| * Added feature.txt
|/
* Initial commit
```

---

#  Fast-Forward vs Merge Commit

## Fast-Forward

```bash
git merge feature-branch
```

```
main (HEAD)
*
| Feature commit
*
| Initial commit
```

**Explanation:**

* No divergence
* Pointer just moves forward

---

## Merge Commit

```
main (HEAD)
*
| Merge commit
|\
| * Feature commit
* | Main commit
|/
* Initial commit
```

---

#  Merge vs Rebase

## Merge (Safe for Teams)

```bash
git merge feature-branch
```

* Preserves history
* Preferred for shared branches

## Rebase (Clean History)

```bash
git checkout feature-branch
git rebase main
```

* Rewrites commits
* Never rebase shared branches

---

#  Real-World Developer Workflow

```bash
git checkout -b login-feature
git add .
git commit -m "Add login validation"

git checkout main
git pull origin main

git merge login-feature
git push origin main

git branch -d login-feature
```

---

#  PR / Code Review Flow

```bash
git checkout -b feature/api-timeout
git push origin feature/api-timeout
```

**Typical PR Flow:**

1. Developer opens Pull Request
2. CI runs (tests, lint, security)
3. Reviewers comment / approve
4. PR merged into `main`
5. Branch deleted

**Key Rule:**

> ❌ Never push directly to `main`

---

#  CI/CD Interaction with Branches

### Common Setup

| Branch    | CI/CD Action          |
| --------- | --------------------- |
| feature/* | Run tests only        |
| main      | Test + build + deploy |
| release/* | Test + staging deploy |

### Example CI Rule

```yaml
on:
  push:
    branches:
      - main
```

**Explanation:**

* CI ensures broken code never reaches production
* Branches control deployment flow

---

# 🔥 Real Merge Conflict Scenario

```bash
git merge feature-branch
```

Conflict in `config.yml`

```text
<<<<<<< HEAD
timeout: 30
=======
timeout: 60
>>>>>>> feature-branch
```

### Resolution

```text
timeout: 60
```

```bash
git add config.yml
git commit -m "Resolve merge conflict"
```

---

#  Real Rebase Conflict Scenario

```bash
git checkout feature-branch
git rebase main
```

Conflict appears.

### Fix → Continue

```bash
git add config.yml
git rebase --continue
```

### Abort if needed

```bash
git rebase --abort
```

---

#  Common Mistakes

❌ Working directly on `main`
❌ Rebasing shared branches
❌ Huge long-running branches
❌ Skipping PR reviews


---

#  Best Practices

✔ One feature per branch
✔ Small, frequent merges
✔ PRs with CI checks
✔ Delete merged branches
✔ Merge > Rebase for teams


---

#  Team Branching Strategies

## Git Flow

* `main` → production
* `develop` → integration
* Best for release-heavy orgs

## Trunk-Based Development

* Single `main`
* Short-lived branches
* Best for CI/CD teams

---

##  Final Mental Model

<img width="218" height="231" alt="image" src="https://github.com/user-attachments/assets/d1dd88c9-89ca-400d-afa9-53d91155c6ad" />


> **Branches are pointers, commits are immutable, merges reconcile truth, and CI enforces discipline.**
