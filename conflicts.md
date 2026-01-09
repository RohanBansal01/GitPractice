# Git Merge Conflicts – Step by Step

This guide explains how **merge conflicts occur**, how to **resolve them**, and
how Git records the resolution.

---

## 1️⃣ Create a Feature Branch

```bash
git checkout -b feature-branch
````

**Explanation:**

* Creates a new branch from `main`
* Switches to `feature-branch`

---

## 2️⃣ Make Changes in Feature Branch

```bash
echo "Feature branch change" >> conflict.txt
git add conflict.txt
git commit -m "Feature branch change"
```

**Explanation:**

* Modifies `conflict.txt` on the feature branch
* Creates a commit that diverges from `main`

---

## 3️⃣ Switch Back to Main Branch

```bash
git checkout main
```

**Explanation:**

* Moves back to `main`
* Feature branch changes are not present here

---

## 4️⃣ Make Conflicting Changes in Main

```bash
echo "Main branch change" >> conflict.txt
git add conflict.txt
git commit -m "Main branch change"
```

**Explanation:**

* Modifies the **same file and same line**
* This sets up a merge conflict

---

## 5️⃣ Merge Feature Branch into Main

```bash
git merge feature-branch
```

**Explanation:**

* Git tries to merge histories
* Conflict occurs because both branches modified the same lines
* Merge pauses and requires manual resolution

---

## 6️⃣ Resolve the Conflict

Open `conflict.txt`. You will see:

```text
<<<<<<< HEAD
Main branch change
=======
Feature branch change
>>>>>>> feature-branch
```

**Explanation:**

* `HEAD` → current branch (`main`)
* Section below `=======` → incoming branch (`feature-branch`)
* You must choose or combine changes

### Example Resolution

```text
Main branch change
Feature branch change
```

Save the file after editing.

---

## 7️⃣ Stage the Resolved File

```bash
git add conflict.txt
```

**Explanation:**

* Marks the conflict as resolved
* Git will allow the merge to continue

---

## 8️⃣ Complete the Merge

```bash
git commit -m "Resolved merge conflict"
```

**Explanation:**

* Finalizes the merge
* Records a merge commit with both histories

---

## 9️⃣ Abort the Merge (Optional)

```bash
git merge --abort
```

**Explanation:**

* Cancels the merge process
* Restores branch to pre-merge state

---

# 📊 Visual Diagram – Merge Conflicts

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

## Step 2: Diverging Commits

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
  *
  | Initial commit
```

---

## Step 3: Merge Attempt (Conflict)

```
git merge feature-branch

❌ Conflict in conflict.txt
```

---

## Step 4: Conflict Resolution

```
Edit conflict.txt
git add conflict.txt
git commit -m "Resolved merge conflict"
```

---

## Step 5: Merge Complete

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

## 🧠 Key Takeaways

* Conflicts occur when **same lines are modified**
* Git never guesses — humans resolve conflicts
* Conflict markers guide manual resolution
* Resolution is recorded as a merge commit

```
