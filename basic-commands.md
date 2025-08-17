
# `basic-commands/` – Line-by-Line Git Commands with Explanation

````markdown
# Basic Git Commands – Step by Step

## 1. Configure Git
```bash
git config --global user.name "Your Name"  
# Sets your Git username globally; commits will show this name

git config --global user.email "you@example.com"  
# Sets your Git email globally; commits will show this email
````

## 2. Initialize a Repository

```bash
git init  
# Creates a new Git repository in the current folder
# Starts tracking changes in this project
```

## 3. Check Repository Status

```bash
git status  
# Shows which files are staged, unstaged, or untracked
```

## 4. Add Changes to Staging

```bash
git add <filename>  
# Stages a specific file to include in the next commit

git add .  
# Stages all changed and new files in the repository
```

## 5. Commit Changes

```bash
git commit -m "Initial commit"  
# Records the staged changes in the repository with a descriptive message
```

## 6. View Commit History

```bash
git log  
# Shows detailed history of commits including SHA, author, date, and message

git log --oneline  
# Shows a concise one-line summary of commits for easier viewing
```

## 7. Clone a Repository

```bash
git clone https://github.com/username/repo.git  
# Copies an existing Git repository from GitHub to your local machine
```

## 8. View Differences

```bash
git diff  
# Shows changes made in files that are not yet staged for commit
```

## 9. Remove a File from Staging

```bash
git reset <filename>  
# Unstages a file that was added with git add
```

## 10. Remove a File from Working Directory

```bash
git rm <filename>  
# Deletes a file from the repository and stages the deletion
```

## 11. Rename a File

```bash
git mv oldname.txt newname.txt  
# Renames a file and stages the change for commit
```

## 12. Show Changes for a Specific Commit

```bash
git show <commit-hash>  
# Displays what changed in a particular commit
```

## 13. Undo Last Commit (Keep Changes)

```bash
git reset --soft HEAD~1  
# Moves HEAD back by one commit, but keeps the changes staged
```

## 14. Undo Last Commit (Discard Changes)

```bash
git reset --hard HEAD~1  
# Moves HEAD back by one commit and discards all changes
```






#!/bin/bash

# ===============================
# Basic Git Commands Script
# ===============================

echo "1️⃣ Configure Git Username and Email"
echo "Setting global username and email..."
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
echo "✅ Username and email configured"
echo

echo "2️⃣ Initialize a new Git repository"
git init
echo "✅ Repository initialized"
echo

echo "3️⃣ Check repository status"
git status
echo

echo "4️⃣ Add a file to staging area"
echo "Creating a sample file..."
echo "Hello Git" > sample.txt
git add sample.txt
echo "✅ sample.txt added to staging"
git status
echo

echo "5️⃣ Commit changes"
git commit -m "Initial commit"
echo "✅ Changes committed"
git log --oneline
echo

echo "6️⃣ Make changes and view differences"
echo "Appending a new line..."
echo "Another line" >> sample.txt
git diff
echo

echo "7️⃣ Add all changes and commit again"
git add .
git commit -m "Added another line to sample.txt"
echo "✅ Changes committed"
git log --oneline
echo

echo "8️⃣ Rename the file"
git mv sample.txt renamed_sample.txt
git commit -m "Renamed sample.txt to renamed_sample.txt"
echo "✅ File renamed and committed"
git log --oneline
echo

echo "9️⃣ Remove the file"
git rm renamed_sample.txt
git commit -m "Removed renamed_sample.txt"
echo "✅ File removed"
git log --oneline
echo

echo "🔹 Script completed! You have practiced basic Git commands step by step."










## **Git Repo Visual Flow – `basic-commands.sh`**

### **Step 0: Before `git init`**

```
Working Directory:
├── (empty)

Staging Area: empty
Commit History: empty
```

---

### **Step 1: `git init`**

```
Working Directory:
├── (empty)
└── .git/   # Hidden Git directory created

Staging Area: empty
Commit History: empty
```

---

### **Step 2: Create `sample.txt` and `git add sample.txt`**

```
Working Directory:
├── sample.txt

Staging Area:
├── sample.txt

Commit History: empty
```

---

### **Step 3: `git commit -m "Initial commit"`**

```
Working Directory:
├── sample.txt

Staging Area: empty

Commit History:
* Initial commit
  └ sample.txt content: "Hello Git"
```

---

### **Step 4: Append line + `git diff`**

```
Working Directory:
├── sample.txt (modified)
      "Hello Git"
      "Another line"

Staging Area: empty

Commit History:
* Initial commit
```

`git diff` shows the added line `"Another line"`.

---

### **Step 5: `git add .` + `git commit -m "Added another line"`**

```
Working Directory:
├── sample.txt

Staging Area: empty

Commit History:
* Added another line
  └ sample.txt content: "Hello Git" + "Another line"
* Initial commit
```

---

### **Step 6: `git mv sample.txt renamed_sample.txt` + commit**

```
Working Directory:
├── renamed_sample.txt

Staging Area: empty

Commit History:
* Renamed sample.txt to renamed_sample.txt
  └ File renamed
* Added another line
  └ sample.txt content: "Hello Git" + "Another line"
* Initial commit
```

---

### **Step 7: `git rm renamed_sample.txt` + commit**

```
Working Directory:
├── (empty)

Staging Area: empty

Commit History:
* Removed renamed_sample.txt
* Renamed sample.txt to renamed_sample.txt
* Added another line
* Initial commit
```

---

### ✅ **Summary of Repo Changes**

| Step | Action                        | Working Dir         | Staging Area | Commit History                                 |
| ---- | ----------------------------- | ------------------- | ------------ | ---------------------------------------------- |
| 0    | Before `git init`             | empty               | empty        | empty                                          |
| 1    | `git init`                    | empty               | empty        | empty                                          |
| 2    | `git add sample.txt`          | sample.txt          | sample.txt   | empty                                          |
| 3    | `git commit "Initial commit"` | sample.txt          | empty        | Initial commit                                 |
| 4    | Modify file + `git diff`      | sample.txt(mod)     | empty        | Initial commit                                 |
| 5    | `git add .` + `git commit`    | sample.txt          | empty        | Initial + Added another line                   |
| 6    | `git mv` + commit             | renamed\_sample.txt | empty        | Initial + Added another line + Rename          |
| 7    | `git rm` + commit             | empty               | empty        | Initial + Added another line + Rename + Remove |

---

This diagram **clearly shows how each command changes the repo state**:

* **Working Directory:** Your actual files on disk.
* **Staging Area (Index):** Files staged for commit.
* **Commit History:** Snapshots of the repository.

---

If you want, I can **make a colored visual diagram image** (like a flowchart) that you can include in your GitPractice README to make it beginner-friendly.

Do you want me to create that image?


