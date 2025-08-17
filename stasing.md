1. **Line-by-line Git stash commands**,
2. **Explanations for each command**,
3. **Visual diagram showing how stashes temporarily save changes**.

---

# **`stashing/stashing.md` – Git Stash Examples**

````markdown
# Git Stash – Step by Step

## 1️⃣ Make Changes in Working Directory
```bash
echo "Temporary work" >> temp.txt
git status
# Shows temp.txt is modified/untracked
````

## 2️⃣ Save Changes to Stash

```bash
git stash
# Saves all uncommitted changes (staged or unstaged) and cleans working directory
# Now working directory matches HEAD commit
```

## 3️⃣ List Stashes

```bash
git stash list
# Shows all stashes saved with unique identifiers like stash@{0}, stash@{1}, etc.
```

## 4️⃣ Apply Last Stash

```bash
git stash apply
# Applies the latest stash changes back to working directory
# Stash is not deleted
```

## 5️⃣ Apply a Specific Stash

```bash
git stash apply stash@{0}
# Applies a specific stash from the list
```

## 6️⃣ Pop Stash (Apply + Remove)

```bash
git stash pop
# Applies the last stash and removes it from the stash list
```

## 7️⃣ Drop a Stash

```bash
git stash drop stash@{0}
# Deletes a specific stash without applying it
```

## 8️⃣ Clear All Stashes

```bash
git stash clear
# Removes all saved stashes
```

```

---

## **Visual Diagram – Git Stash**

### **Step 0: Working Directory Modified**
```

Working Directory:
├── temp.txt (modified)

Staging Area: empty
Commit History:

* Initial commit

```

### **Step 1: git stash**
```

Working Directory: clean (no changes)
Staging Area: empty
Stash:

* stash@{0} – contains temp.txt changes
  Commit History:
* Initial commit

```

### **Step 2: git stash apply**
```

Working Directory:
├── temp.txt (changes restored)
Staging Area: empty
Stash:

* stash@{0} remains
  Commit History:
* Initial commit

```

### **Step 3: git stash pop**
```

Working Directory:
├── temp.txt (changes restored)
Staging Area: empty
Stash: empty
Commit History:

* Initial commit

```

**Explanation:**  
- `git stash` is useful to **temporarily save changes** without committing.  
- You can switch branches or perform other tasks safely.  
- `apply` restores changes without removing the stash; `pop` restores and removes it.

---


