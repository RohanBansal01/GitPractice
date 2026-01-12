# Git Branching & Merging – Step by Step

This document explains:
- How to create and switch branches
- How merges work in a typical workflow
- How branching and merging affect repository history

---

## 1️⃣ View Current Branch

```bash
git branch
````

**Explanation:**

* Lists all local branches
* `*` marks the currently active branch
* Default branch is usually `main`

---

## 2️⃣ Create a New Branch

```bash
git branch feature-branch
```

**Explanation:**

* Creates a new branch named `feature-branch`
* Does NOT switch to it
* Both branches initially point to the same commit

---

## 3️⃣ Switch to the New Branch

```bash
git checkout feature-branch
```

**Explanation:**

* Switches the working directory to `feature-branch`
* All new commits will belong to this branch

### Alternative (Git 2.23+)

```bash
git switch feature-branch
```

---

## 4️⃣ Make Changes in the Feature Branch

```bash
echo "Feature work" >> feature.txt
git add feature.txt
git commit -m "Added feature.txt in feature-branch"
```

**Explanation:**

* Creates a new commit on `feature-branch`
* `main` remains unchanged

---

## 5️⃣ Switch Back to Main

```bash
git checkout main
```

**Explanation:**

* Returns to `main`
* `feature.txt` is not present yet

---

## 6️⃣ Merge Feature Branch into Main

```bash
git merge feature-branch
```

**Explanation:**

* Integrates changes from `feature-branch` into `main`
* Creates a merge commit if branches diverged
* Preserves branch history

---

## 7️⃣ Delete Feature Branch

```bash
git branch -d feature-branch
```

**Explanation:**

* Deletes the local feature branch
* Safe after a successful merge

---

## 8️⃣ View All Branches

```bash
git branch      # Local branches
git branch -a   # Local + remote branches
```

**Explanation:**

* Useful for tracking active and stale branches

---

# 📊 Visual Diagram – Branching & Merging

## Step 0: Initial Commit

```
main (HEAD)
*
| Initial commit
```

---

## Step 1: Create Feature Branch

```
main
*
| Initial commit
 \
  feature-branch (HEAD)
```

---

## Step 2: Commit on Feature Branch

```
main
*
| Initial commit
 \
  feature-branch (HEAD)
  *
  | Added feature.txt
```

---

## Step 3: Merge Feature Branch into Main

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

## Step 4: Feature Branch Deleted

```
main (HEAD)
*
| Merge commit
*
| Initial commit
```

---

## 🧠 Explanation of Repository Changes

* Feature work is isolated in `feature-branch`
* `main` stays stable until merge
* Merge integrates changes while preserving history
* Deleting a branch does NOT delete merged commits

```

---
