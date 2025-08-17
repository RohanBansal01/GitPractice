1. **Line-by-line Git commands** for branching, merging, and workflow examples.
2. **Explanation of each command**.
3. A **visual diagram** showing how branches and merges affect the repository.

---

# **`branching/branching.md` – Git Branching & Merging**

````markdown
# Git Branching & Merging – Step by Step

## 1️⃣ View Current Branch
```bash
git branch  
# Shows the current branch (default is 'main') and all local branches
````

## 2️⃣ Create a New Branch

```bash
git branch feature-branch  
# Creates a new branch called 'feature-branch'
# No switch yet; main branch is still active
```

## 3️⃣ Switch to the New Branch

```bash
git checkout feature-branch  
# Switches your working directory to the new branch
# All new commits will go to 'feature-branch'

# OR (Git 2.23+)
git switch feature-branch
```

## 4️⃣ Make Changes in the Branch

```bash
echo "Feature work" >> feature.txt
git add feature.txt
git commit -m "Added feature.txt in feature-branch"
```

## 5️⃣ Switch Back to Main

```bash
git checkout main  
# Returns to main branch
# feature.txt will not be in main yet
```

## 6️⃣ Merge Feature Branch into Main

```bash
git merge feature-branch  
# Combines commits from 'feature-branch' into 'main'
# If no conflicts, a merge commit is created
```

## 7️⃣ Delete Feature Branch

```bash
git branch -d feature-branch  
# Deletes the branch locally after merging
```

## 8️⃣ View All Branches

```bash
git branch      # Local branches
git branch -a   # Local + remote branches
```

```






---

## **Visual Diagram – Branching & Merging**

### **Step 0: Initial Commit**
```

main

* Initial commit

```

### **Step 1: Create & Switch to Feature Branch**
```

main

* Initial commit

feature-branch (HEAD)

```

### **Step 2: Add Commit in Feature Branch**
```

main

* Initial commit

feature-branch (HEAD)

* Added feature.txt

```

### **Step 3: Merge Feature Branch into Main**
```

main (HEAD)

* Merge commit: feature-branch
  |
  \| \* Added feature.txt (feature-branch)
* Initial commit

```

### **Step 4: Delete Feature Branch**
```

main (HEAD)

* Merge commit: feature-branch
* Initial commit

```

**Explanation of Repo Changes:**
- `feature-branch` is used for isolated work.  
- `main` remains stable until merge.  
- Merge combines commits, and branch can then be deleted.

---
