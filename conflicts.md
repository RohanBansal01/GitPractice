##  `conflicts/conflicts.md`

<img width="219" height="230" alt="image" src="https://github.com/user-attachments/assets/3c0e837f-3650-4b56-aca9-b24850c2486c" />


````markdown
````
# Git Merge & Rebase Conflicts – Step by Step

<img width="1502" height="994" alt="image" src="https://github.com/user-attachments/assets/fb6bfc50-51d8-4d36-8b42-3683262facc3" />


This guide explains:
- Why conflicts happen
- How to resolve merge and rebase conflicts
- How Git records conflict resolutions
- Best practices teams follow to avoid them

---

## 📚 Index

1. What Is a Git Conflict  
2. When Conflicts Occur  
3. Creating a Feature Branch  
4. Making Conflicting Changes  
5. Triggering a Merge Conflict  
6. Understanding Conflict Markers  
7. Resolving a Merge Conflict  
8. Completing or Aborting a Merge  
9. Visual Diagram – Merge Conflict  
10. Real Merge Conflict Scenario  
11. Triggering a Rebase Conflict  
12. Resolving a Rebase Conflict  
13. Visual Diagram – Rebase Conflict  
14. Common Mistakes  
15. Best Practices & Mental Model  

---

## 1️⃣ What Is a Git Conflict

A **Git conflict** occurs when Git cannot automatically decide
which changes to keep.

**Typical causes:**
- Same file edited in two branches
- Same lines modified differently
- File deleted in one branch and edited in another

---

## 2️⃣ When Conflicts Occur

Conflicts commonly occur during:

```bash
git merge
git rebase
git cherry-pick
````

Git pauses the operation and asks **you** to resolve it.

---

## 3️⃣ Create a Feature Branch

```bash
git checkout -b feature-branch
```

**Explanation:**

* Creates a new branch from `main`
* Switches to `feature-branch`

---

## 4️⃣ Make Changes in Feature Branch

```bash
echo "Feature branch change" >> conflict.txt
git add conflict.txt
git commit -m "Feature branch change"
```

**Explanation:**

* Modifies `conflict.txt`
* Creates a commit unique to feature branch

---

## 5️⃣ Make Conflicting Changes in Main

```bash
git checkout main
echo "Main branch change" >> conflict.txt
git add conflict.txt
git commit -m "Main branch change"
```

**Explanation:**

* Modifies the **same file and same line**
* This guarantees a conflict

---

## 6️⃣ Trigger a Merge Conflict

```bash
git merge feature-branch
```

**Explanation:**

* Git cannot auto-merge
* Merge stops and reports a conflict

---

## 7️⃣ Understanding Conflict Markers

Open `conflict.txt`:

```text
<<<<<<< HEAD
Main branch change
=======
Feature branch change
>>>>>>> feature-branch
```

**Meaning:**

* `HEAD` → current branch (`main`)
* Bottom section → incoming branch
* You must decide final content

---

## 8️⃣ Resolve the Merge Conflict

### Example Resolution

```text
Main branch change
Feature branch change
```

```bash
git add conflict.txt
```

**Explanation:**

* Removes conflict markers
* Marks file as resolved

---

## 9️⃣ Complete or Abort the Merge

### Complete Merge

```bash
git commit -m "Resolved merge conflict"
```

### Abort Merge

```bash
git merge --abort
```

**Explanation:**

* `commit` finalizes merge
* `abort` restores pre-merge state

---

# 📊 Visual Diagram – Merge Conflict

## Before Merge

```
main (HEAD)
*
| Main branch change
*
| Initial commit
 \
  feature-branch
  *
  | Feature branch change
```

---

## During Merge

```
git merge feature-branch

❌ Conflict in conflict.txt
```

---

## After Resolution

```
main (HEAD)
*
| Resolved merge conflict
|\
| * Feature branch change
* | Main branch change
|/
* Initial commit
```

---

## 🔥 Real Merge Conflict Scenario

**Scenario:**
Two developers update `timeout` value.

```text
<<<<<<< HEAD
timeout: 30
=======
timeout: 60
>>>>>>> feature-branch
```

**Resolution:**

```text
timeout: 60
```

```bash
git add config.yml
git commit -m "Resolve timeout conflict"
```

---

## 🔁 Triggering a Rebase Conflict

```bash
git checkout feature-branch
git rebase main
```

**Explanation:**

* Git replays feature commits on top of `main`
* Conflict may occur mid-rebase

---

## 🔧 Resolving a Rebase Conflict

```bash
# Fix the file
git add conflict.txt
git rebase --continue
```

### Abort Rebase

```bash
git rebase --abort
```

**Explanation:**

* `continue` resumes rebase
* `abort` restores original branch

---

# 📊 Visual Diagram – Rebase Conflict

## Before Rebase

```
main
*
| Main commit
*
| Initial commit
 \
  feature-branch
  *
  | Feature commit
```

---

## After Rebase (Resolved)

```
feature-branch (HEAD)
*
| Feature commit'
*
| Main commit
*
| Initial commit
```

---

## ⚠️ Common Mistakes

❌ Panic-editing conflict markers
❌ Forgetting `git add` after resolving
❌ Rebasing shared branches
❌ Auto-resolving without understanding


<img width="481" height="494" alt="image" src="https://github.com/user-attachments/assets/1283ccee-0f9d-442d-b5d8-4753f3419b21" />


---

## ✅ Best Practices

✔ Keep commits small
✔ Pull latest `main` before merging
✔ Resolve conflicts locally
✔ Use merge for shared branches
✔ Rebase only personal branches

---

## 🧠 Final Mental Model

<img width="277" height="182" alt="image" src="https://github.com/user-attachments/assets/b1062db7-f24b-46e7-b8b1-448687268baa" />

> **A conflict is Git asking you to choose the source of truth.
> Git never guesses — humans decide.**

