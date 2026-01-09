# Git Stash – Step by Step

This guide explains how **Git stash** temporarily saves uncommitted work,
allowing you to switch context without committing unfinished changes.

---

## 1️⃣ Make Changes in Working Directory

```bash
echo "Temporary work" >> temp.txt
git status
````

**Explanation:**

* Modifies `temp.txt`
* `git status` shows uncommitted changes in the working directory

---

## 2️⃣ Save Changes to Stash

```bash
git stash
```

**Explanation:**

* Saves all uncommitted changes (staged + unstaged)
* Resets working directory to match the last commit (`HEAD`)
* Changes are stored safely in a stash stack

---

## 3️⃣ List Stashes

```bash
git stash list
```

**Explanation:**

* Displays all saved stashes
* Each stash has an identifier like `stash@{0}`, `stash@{1}`

---

## 4️⃣ Apply Last Stash

```bash
git stash apply
```

**Explanation:**

* Restores the most recent stash
* Stash remains in the list (not deleted)

---

## 5️⃣ Apply a Specific Stash

```bash
git stash apply stash@{0}
```

**Explanation:**

* Applies a specific stash by index
* Useful when multiple stashes exist

---

## 6️⃣ Pop Stash (Apply + Remove)

```bash
git stash pop
```

**Explanation:**

* Applies the latest stash
* Removes it from the stash list

---

## 7️⃣ Drop a Stash

```bash
git stash drop stash@{0}
```

**Explanation:**

* Deletes a specific stash
* Does NOT apply its changes

---

## 8️⃣ Clear All Stashes

```bash
git stash clear
```

**Explanation:**

* Removes all stashes permanently
* Use with caution

---

# 📊 Visual Diagram – Git Stash

## Step 0: Working Directory Modified

```
Working Directory:
├── temp.txt (modified)

Staging Area: empty

Commit History:
* Initial commit
```

---

## Step 1: After `git stash`

```
Working Directory: clean
Staging Area: empty

Stash:
* stash@{0} → temp.txt changes

Commit History:
* Initial commit
```

---

## Step 2: After `git stash apply`

```
Working Directory:
├── temp.txt (changes restored)

Staging Area: empty

Stash:
* stash@{0} still exists

Commit History:
* Initial commit
```

---

## Step 3: After `git stash pop`

```
Working Directory:
├── temp.txt (changes restored)

Staging Area: empty

Stash: empty

Commit History:
* Initial commit
```

---

## 🧠 Key Takeaways

* `git stash` temporarily saves work without committing
* Ideal for quick context switching
* `apply` restores changes but keeps stash
* `pop` restores changes and removes stash
* Stashes do NOT affect commit history

```

