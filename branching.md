# Git Branching & Merging – Step by Step

This document is a **team-ready guide** covering:
- Branching and merging fundamentals
- Real-world workflows
- PR, code review, and CI/CD integration
- Conflict and rebase scenarios
- Best practices used in production teams

---

## 📚 Index

1. [View Current Branch](#1-view-current-branch)
2. [Create a New Branch](#2-create-a-new-branch)
3. [Switch to the New Branch](#3-switch-to-the-new-branch)
4. [Make Changes in Feature Branch](#4-make-changes-in-feature-branch)
5. [Switch Back to Main](#5-switch-back-to-main)
6. [Merge Feature Branch into Main](#6-merge-feature-branch-into-main)
7. [Delete Feature Branch](#7-delete-feature-branch)
8. [View All Branches](#8-view-all-branches)
9. [Visual Diagram – Basic Branching](#9-visual-diagram--basic-branching)
10. [Fast-Forward vs Merge Commit](#10-fast-forward-vs-merge-commit)
11. [Merge vs Rebase](#11-merge-vs-rebase)
12. [Real-World Developer Workflow](#12-real-world-developer-workflow)
13. [PR / Code Review Flow](#13-pr--code-review-flow)
14. [CI/CD Interaction with Branches](#14-cicd-interaction-with-branches)
15. [Real Merge Conflict Scenario](#15-real-merge-conflict-scenario)
16. [Real Rebase Conflict Scenario](#16-real-rebase-conflict-scenario)
17. [Common Mistakes](#17-common-mistakes)
18. [Best Practices](#18-best-practices)
19. [Team Branching Strategies](#19-team-branching-strategies)
20. [Final Mental Model](#20-final-mental-model)

---

## 1. View Current Branch

```bash
git branch
```

**Explanation:**

* Lists all local branches
* `*` marks the active branch
* Default branch is usually `main`

<img width="275" height="184" alt="image" src="https://github.com/user-attachments/assets/3000020f-c43f-4b12-ad38-7b79fb2d97d5" />

---

## 2. Create a New Branch

```bash
git branch feature-branch
```

**Explanation:**

* Creates a new branch
* Does NOT switch to it
* Both branches point to the same commit

---

## 3. Switch to the New Branch

```bash
git checkout feature-branch
```

### 3.1 Alternative (Git 2.23+)

```bash
git switch feature-branch
```

**Explanation:**

* Working directory switches to feature branch
* New commits go here

---

## 4. Make Changes in Feature Branch

```bash
echo "Feature work" >> feature.txt
git add feature.txt
git commit -m "Added feature.txt in feature-branch"
```

**Explanation:**

* Commit exists only on feature branch
* `main` remains stable

---

## 5. Switch Back to Main

```bash
git checkout main
```

**Explanation:**

* Feature changes are not yet in `main`

---

## 6. Merge Feature Branch into Main

```bash
git merge feature-branch
```

**Explanation:**

* Integrates feature work
* Creates merge commit if histories diverged

---

## 7. Delete Feature Branch

```bash
git branch -d feature-branch
```

**Explanation:**

* Safe cleanup after merge

---

## 8. View All Branches

```bash
git branch      # Local
git branch -a   # Local + Remote
```

---

## 9. Visual Diagram – Basic Branching

### 9.1 Initial State

```
main (HEAD)
*
| Initial commit
```

### 9.2 Feature Branch Created

```
main
*
| Initial commit
 \
  feature-branch (HEAD)
```

### 9.3 Commit on Feature Branch

```
main
*
| Initial commit
 \
  feature-branch (HEAD)
  *
  | Added feature.txt
```

### 9.4 Merge into Main

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

## 10. Fast-Forward vs Merge Commit

### 10.1 Fast-Forward

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

### 10.2 Merge Commit

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

## 11. Merge vs Rebase

### 11.1 Merge (Safe for Teams)

```bash
git merge feature-branch
```

* Preserves history
* Preferred for shared branches

### 11.2 Rebase (Clean History)

```bash
git checkout feature-branch
git rebase main
```

* Rewrites commits
* Never rebase shared branches

---

## 12. Real-World Developer Workflow

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

## 13. PR / Code Review Flow

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

## 14. CI/CD Interaction with Branches

### 14.1 Common Setup

| Branch    | CI/CD Action          |
| --------- | --------------------- |
| feature/* | Run tests only        |
| main      | Test + build + deploy |
| release/* | Test + staging deploy |

### 14.2 Example CI Rule

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

## 15. Real Merge Conflict Scenario

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

### 15.1 Resolution

```text
timeout: 60
```

```bash
git add config.yml
git commit -m "Resolve merge conflict"
```

---

## 16. Real Rebase Conflict Scenario

```bash
git checkout feature-branch
git rebase main
```

Conflict appears.

### 16.1 Fix → Continue

```bash
git add config.yml
git rebase --continue
```

### 16.2 Abort if needed

```bash
git rebase --abort
```

---

## 17. Common Mistakes

❌ Working directly on `main`  
❌ Rebasing shared branches  
❌ Huge long-running branches  
❌ Skipping PR reviews

---

## 18. Best Practices

✔ One feature per branch  
✔ Small, frequent merges  
✔ PRs with CI checks  
✔ Delete merged branches  
✔ Merge > Rebase for teams

---

## 19. Team Branching Strategies

### 19.1 Git Flow

* `main` → production
* `develop` → integration
* Best for release-heavy orgs

### 19.2 Trunk-Based Development

* Single `main`
* Short-lived branches
* Best for CI/CD teams

---

## 20. Final Mental Model

<img width="218" height="231" alt="image" src="https://github.com/user-attachments/assets/d1dd88c9-89ca-400d-afa9-53d91155c6ad" />

> **Branches are pointers, commits are immutable, merges reconcile truth, and CI enforces discipline.**
