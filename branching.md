
##  `branching/branching.md`**

````markdown
# Git Branching & Merging – Step by Step

This document is a **team-ready guide** covering:
- Branching and merging fundamentals
- Real-world workflows
- PR, code review, and CI/CD integration
- Conflict and rebase scenarios
- Best practices used in production teams

---

## 📚 Index

1. View & Create Branches  
2. Working with Feature Branches  
3. Merging into Main  
4. Visual Diagrams – Branching & Merging  
5. Fast-Forward vs Merge Commit  
6. Merge vs Rebase (Comparison)  
7. Real-World Developer Workflow  
8. PR / Code Review Flow  
9. CI/CD Interaction with Branches  
10. Real Merge Conflict Scenario  
11. Real Rebase Conflict Scenario  
12. Common Mistakes  
13. Best Practices  
14. Team Branching Strategies  
15. Final Mental Model  

---

## 1️⃣ View Current Branch

```bash
git branch
````

**Explanation:**

* Lists all local branches
* `*` marks the active branch
* Default branch is usually `main`

---

## 2️⃣ Create a New Branch

```bash
git branch feature-branch
```

**Explanation:**

* Creates a new branch
* Does NOT switch to it
* Both branches point to the same commit

---

## 3️⃣ Switch to the New Branch

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

## 4️⃣ Make Changes in Feature Branch

```bash
echo "Feature work" >> feature.txt
git add feature.txt
git commit -m "Added feature.txt in feature-branch"
```

**Explanation:**

* Commit exists only on feature branch
* `main` remains stable

---

## 5️⃣ Switch Back to Main

```bash
git checkout main
```

**Explanation:**

* Feature changes are not yet in `main`

---

## 6️⃣ Merge Feature Branch into Main

```bash
git merge feature-branch
```

**Explanation:**

* Integrates feature work
* Creates merge commit if histories diverged

---

## 7️⃣ Delete Feature Branch

```bash
git branch -d feature-branch
```

**Explanation:**

* Safe cleanup after merge

---

## 8️⃣ View All Branches

```bash
git branch      # Local
git branch -a   # Local + Remote
```

---

# 📊 Visual Diagram – Basic Branching

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

# 🔀 Fast-Forward vs Merge Commit

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

# 🔁 Merge vs Rebase

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

# 🧪 Real-World Developer Workflow

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

# 🔍 PR / Code Review Flow

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

# ⚙️ CI/CD Interaction with Branches

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

# 🔥 Real Rebase Conflict Scenario

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

# ⚠️ Common Mistakes

❌ Working directly on `main`
❌ Rebasing shared branches
❌ Huge long-running branches
❌ Skipping PR reviews

---

# ✅ Best Practices

✔ One feature per branch
✔ Small, frequent merges
✔ PRs with CI checks
✔ Delete merged branches
✔ Merge > Rebase for teams

---

# 🏗 Team Branching Strategies

## Git Flow

* `main` → production
* `develop` → integration
* Best for release-heavy orgs

## Trunk-Based Development

* Single `main`
* Short-lived branches
* Best for CI/CD teams

---

## 🧠 Final Mental Model

> **Branches are pointers, commits are immutable, merges reconcile truth, and CI enforces discipline.**
