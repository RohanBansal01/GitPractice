
````markdown
# Git Rebase – Step by Step

This guide explains **Git rebasing** with:
- Exact commands
- What each command does
- How commit history is rewritten

---

## 1️⃣ Create a Feature Branch

```bash
git checkout -b feature-branch
````

**Explanation:**

* Creates a new branch named `feature-branch`
* Switches to it immediately

---

## 2️⃣ Make Commits in Feature Branch

```bash
echo "Feature commit 1" >> feature.txt
git add feature.txt
git commit -m "Feature commit 1"
```

```bash
echo "Feature commit 2" >> feature.txt
git add feature.txt
git commit -m "Feature commit 2"
```

**Explanation:**

* Two commits are created on `feature-branch`
* These commits exist only on the feature branch

---

## 3️⃣ Switch to Main and Make a Commit

```bash
git checkout main
```

```bash
echo "Main commit 1" >> main.txt
git add main.txt
git commit -m "Main commit 1"
```

**Explanation:**

* `main` advances independently
* Now `main` and `feature-branch` have diverged

---

## 4️⃣ Rebase Feature Branch onto Main

```bash
git checkout feature-branch
git rebase main
```

**Explanation:**

* Git takes feature commits
* Replays them **on top of the latest `main`**
* Commit hashes are rewritten

---

## 5️⃣ Resolve Conflicts (If Any)

```bash
# Fix conflicts manually, then:
git add <file>
git rebase --continue
```

**Explanation:**

* Resolve conflicts file by file
* Continue rebasing until finished

---

## 6️⃣ Abort a Rebase

```bash
git rebase --abort
```

**Explanation:**

* Cancels the rebase
* Restores branch to its original state

---

## 7️⃣ Interactive Rebase

```bash
git rebase -i HEAD~2
```

**Explanation:**

* Opens an editor
* Lets you `pick`, `squash`, `reword`, or `drop` commits
* Used for cleaning history before merge

---

# 📊 Visual Diagram – Git Rebase

## Step 0: Initial State

```
main (HEAD)
*
| Initial commit
```

---

## Step 1: Feature Branch Created

```
main
*
| Initial commit
 \
  feature-branch (HEAD)
```

---

## Step 2: Commits on Feature Branch

```
main
*
| Initial commit
 \
  feature-branch (HEAD)
  *
  | Feature commit 2
  *
  | Feature commit 1
```

---

## Step 3: Commit on Main

```
main (HEAD)
*
| Main commit 1
*
| Initial commit
 \
  feature-branch
  *
  | Feature commit 2
  *
  | Feature commit 1
```

---

## Step 4: After Rebase (History Rewritten)

```
main
*
| Main commit 1
*
| Initial commit
 \
  feature-branch (HEAD)
  *
  | Feature commit 2'
  *
  | Feature commit 1'
```

---


---

## 🧠 Rebase vs Merge (One Line)

> **Rebase rewrites history for clarity; merge preserves history for safety.**

```

