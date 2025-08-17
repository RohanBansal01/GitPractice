1. **Line-by-line Git commands to create and resolve merge conflicts**,
2. **Explanations for each command**,
3. **Visual diagram showing how conflicts occur and are resolved**.

---

# **`conflicts/conflicts.md` – Git Merge Conflicts**

````markdown
# Git Merge Conflicts – Step by Step

## 1️⃣ Create a Feature Branch
```bash
git checkout -b feature-branch
# Creates and switches to a new branch
````

## 2️⃣ Make Changes in Feature Branch

```bash
echo "Feature work" >> conflict.txt
git add conflict.txt
git commit -m "Feature branch change"
```

## 3️⃣ Switch Back to Main Branch

```bash
git checkout main
```

## 4️⃣ Make Conflicting Changes in Main

```bash
echo "Main branch change" >> conflict.txt
git add conflict.txt
git commit -m "Main branch change"
```

## 5️⃣ Merge Feature Branch into Main

```bash
git merge feature-branch
# Merge conflict occurs because both branches modified the same lines in conflict.txt
```

## 6️⃣ Resolve Conflicts

* Open `conflict.txt` in a text editor.
* Look for conflict markers:

```
<<<<<<< HEAD
Main branch change
=======
Feature branch change
>>>>>>> feature-branch
```

* Edit the file to combine changes or choose one version.
* Save the file.

## 7️⃣ Stage Resolved File

```bash
git add conflict.txt
```

## 8️⃣ Complete Merge

```bash
git commit -m "Resolved merge conflict"
# Commit now records the merged changes
```

## 9️⃣ Abort Merge (Optional)

```bash
git merge --abort
# Cancels merge and restores main branch to pre-merge state
```

```

---

## **Visual Diagram – Merge Conflicts**

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

### **Step 2: Commits on Both Branches**
```

main

* Main branch change (HEAD)
* Initial commit

feature-branch

* Feature branch change
* Initial commit

```

### **Step 3: Merge Attempt**
```

git merge feature-branch

# Conflict occurs on conflict.txt

```

### **Step 4: Resolve Conflict**
```

Edit conflict.txt, choose or combine changes
git add conflict.txt
git commit -m "Resolved merge conflict"

```

### **Step 5: Merge Complete**
```

main (HEAD)

* Resolved merge conflict
* Main branch change
* Initial commit

```

**Explanation:**  
- Conflicts happen when **two branches modify the same lines** in a file.  
- Git marks the conflict for you with `<<<<<<<`, `=======`, `>>>>>>>`.  
- You manually resolve the conflict, stage it, and commit.  
- Merge history is then complete with a clear resolution.

---


