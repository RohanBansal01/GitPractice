# Git Stash 

This guide explains **Git stash** in depth:
- What stash really is
- How it works internally
- When it’s safe and unsafe
- How conflicts occur with stash
- How senior developers use it correctly

<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/d3d579c8-e3b6-4a8b-b049-ca32597ebabc" />


---

## 📌 Index

1. What Is Git Stash  
2. When Git Stash Is Used  
3. What Git Stash Is NOT  
4. Working Directory vs Staging vs Commit  
5. Creating Uncommitted Changes  
6. Saving Changes to Stash  
7. What Happens Internally (Internals)  
8. Listing & Inspecting Stashes  
9. Applying vs Popping a Stash  
10. Visual Diagram – Stash Lifecycle  
11. Real Stash Conflict Scenario  
12. Resolving a Stash Conflict  
13. Dropping & Clearing Stashes  
14. Common Mistakes  
15. Best Practices & Final Mental Model  

---

## 1️⃣ What Is Git Stash

`git stash` temporarily **shelves uncommitted changes** so you can:
- Switch branches
- Pull updates
- Fix urgent issues

Without committing unfinished work.

> **Stash is a clipboard, not a backup.**

---

## 2️⃣ When Git Stash Is Used

✔ Quick context switch  
✔ Pull latest changes safely  
✔ Fix urgent production issue  
✔ Save experimental work briefly  

❌ Long-term storage  
❌ Collaboration  
❌ Replacing commits  

---

## 3️⃣ What Git Stash Is NOT

❌ Not part of commit history  
❌ Not pushed to remote  
❌ Not safe forever  
❌ Not visible to teammates  

Stashes are **local and fragile**.

---

## 4️⃣ Working Directory vs Staging vs Commit

Before stash:

```
Working Directory → modified files
Staging Area     → may have files
Commit History   → unchanged
```

Stash affects:
- Working Directory
- Staging Area

Never commit history.

---

## 5️⃣ Creating Uncommitted Changes

```bash
echo "Temporary work" >> temp.txt
git status
```

**Explanation:**
- File is modified
- Changes exist only locally
- Not yet safe to commit

---

## 6️⃣ Saving Changes to Stash

```bash
git stash
```

**Explanation:**
- Saves staged + unstaged changes
- Clears working directory
- Creates a stash entry

Working directory becomes **clean**.

---

## 7️⃣ What Happens Internally (Internals)

Internally Git:
```
1. Creates two commits (index + working tree)
2. Stores them in refs/stash
3. Resets working directory to HEAD
```

Stash is **a hidden commit stack**, not magic.

---

## 8️⃣ Listing & Inspecting Stashes

```bash
git stash list
```

```bash
git stash show stash@{0}
```

```bash
git stash show -p stash@{0}
```

**Explanation:**
- `list` → shows stash stack
- `show` → summary
- `-p` → full diff

---

## 9️⃣ Applying vs Popping a Stash

### Apply
```bash
git stash apply
```
✔ Restores changes  
✔ Keeps stash  

### Pop
```bash
git stash pop
```
✔ Restores changes  
✔ Deletes stash  

> Use **apply** if you’re unsure.

---

## 🔟 Visual Diagram – Stash Lifecycle

### Before Stash
```
Working Directory:
├── temp.txt (modified)

Staging Area: maybe files
Commit History:
* Initial commit
```

### After `git stash`
```
Working Directory: clean
Staging Area: empty

Stash Stack:
* stash@{0} → temp.txt changes

Commit History:
* Initial commit
```

### After `git stash pop`
```
Working Directory:
├── temp.txt (restored)

Stash Stack: empty
Commit History unchanged
```

---

## 1️⃣1️⃣ Real Stash Conflict Scenario

Conflict occurs when:
- You stash changes
- Switch branch
- That branch changed the same lines

```bash
git stash apply
```

❌ Conflict in `temp.txt`

---

## 1️⃣2️⃣ Resolving a Stash Conflict

Conflict markers appear:

```text
<<<<<<< Updated upstream
Main branch change
=======
Stashed change
>>>>>>> Stashed changes
```

### Resolve manually, then:

```bash
git add temp.txt
```

If using `pop`, Git removes stash **only if successful**.

---

## 1️⃣3️⃣ Dropping & Clearing Stashes

### Drop one stash
```bash
git stash drop stash@{0}
```

### Clear all stashes
```bash
git stash clear
```

⚠️ **Irreversible operation**

---

## 1️⃣4️⃣ Common Mistakes

❌ Using stash as long-term storage  
❌ Forgetting stashes exist  
❌ Clearing stash accidentally  
❌ Stashing work instead of committing  
❌ Assuming stash is shared  

---

## 1️⃣5️⃣ Best Practices & Final Mental Model

### Best Practices
✔ Stash only short-lived work  
✔ Use stash messages  
✔ Prefer commits over stash  
✔ Clear stash regularly  
✔ Use apply before pop  

### Final Mental Model

> **Stash is a temporary drawer —  
> commits are permanent shelves.**

<img width="500" height="659" alt="image" src="https://github.com/user-attachments/assets/b5d947be-649f-4655-b44a-03b2d5bb2f6b" />


---

## 🧠 One-Line Summary

> **Git stash saves time, not history — use it briefly and deliberately.**
