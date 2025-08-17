1. **Line-by-line Git commands for rebasing**,
2. **Explanations for each command**,
3. **Visual diagram showing how commits are rewritten during rebase**.

---

# **`rebasing/rebasing.md` – Git Rebase Examples**

````markdown
# Git Rebase – Step by Step

## 1️⃣ Create a Feature Branch
```bash
git checkout -b feature-branch
# Creates and switches to 'feature-branch' in one step
````

## 2️⃣ Make Commits in Feature Branch

```bash
echo "Feature commit 1" >> feature.txt
git add feature.txt
git commit -m "Feature commit 1"

echo "Feature commit 2" >> feature.txt
git add feature.txt
git commit -m "Feature commit 2"
```

## 3️⃣ Switch to Main and Make Commit

```bash
git checkout main
echo "Main commit 1" >> main.txt
git add main.txt
git commit -m "Main commit 1"
```

## 4️⃣ Rebase Feature Branch onto Main

```bash
git checkout feature-branch
git rebase main
# Reapplies feature commits on top of latest main commit
```

## 5️⃣ Resolve Conflicts (if any)

```bash
# Edit conflicting files, then:
git add <file>
git rebase --continue
# Repeat until rebase finishes
```

## 6️⃣ Abort Rebase

```bash
git rebase --abort
# Cancels rebase and restores branch to original state
```

## 7️⃣ Interactive Rebase

```bash
git rebase -i HEAD~2
# Opens editor to squash, reorder, or edit last 2 commits
```

```

---

## **Visual Diagram – Git Rebase**

### **Step 0: Initial Commit**
```

main (HEAD)

* Initial commit

```

### **Step 1: Feature Branch Created**
```

main

* Initial commit

feature-branch (HEAD)

```

### **Step 2: Commits in Feature Branch**
```

main

* Initial commit

feature-branch (HEAD)

* Feature commit 2
* Feature commit 1

```

### **Step 3: Commit in Main**
```

main (HEAD)

* Main commit 1
* Initial commit

feature-branch

* Feature commit 2
* Feature commit 1

```

### **Step 4: Rebase Feature onto Main**
```

main

* Main commit 1
* Initial commit

feature-branch (HEAD)

* Feature commit 1'
* Feature commit 2'

```

**Explanation:**  
- Commits from `feature-branch` are **rebased on top of main**.  
- Original feature commits are replaced with new commits (`1'` and `2'`) for linear history.  
- Keeps history cleaner compared to a merge commit.  

---
