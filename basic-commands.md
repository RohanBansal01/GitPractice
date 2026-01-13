# Basic Git Commands – Complete Guide (Mental Model First)

This document explains **basic Git commands line by line**, how they affect the **working directory, staging area, and commit history**, and how everything fits together in a **real developer workflow**.

<img width="481" height="455" alt="image" src="https://github.com/user-attachments/assets/3e9c416e-cd0c-4bdb-90dc-4dc148e6dd54" />

---

## 📚 Index

1. [What Git Is Tracking (Core Areas)](#1-what-git-is-tracking-core-areas)  
2. [Initial Git Configuration](#2-initial-git-configuration)  
3. [Creating a Repository](#3-creating-a-repository)  
4. [Repository Status Explained](#4-repository-status-explained)  
5. [Adding Files to Staging](#5-adding-files-to-staging)  
6. [Committing Changes](#6-committing-changes)  
7. [Viewing Commit History](#7-viewing-commit-history)  
8. [Understanding `git diff`](#8-understanding-git-diff)  
9. [Undoing Staging (`git reset`)](#9-undoing-staging-git-reset)  
10. [Removing & Renaming Files](#10-removing--renaming-files)  
11. [Inspecting a Commit](#11-inspecting-a-commit)  
12. [Undoing Commits (Soft vs Hard)](#12-undoing-commits-soft-vs-hard)  
13. [End‑to‑End Local Workflow](#13-end-to-end-local-workflow)  
14. [Common Beginner Mistakes](#14-common-beginner-mistakes)  
15. [Final Mental Model](#15-final-mental-model)  

---

## 1. What Git Is Tracking (Core Areas)

Git always works with **three areas**:

```
Working Directory → Staging Area → Commit History
```

• **Working Directory**: Actual files on your disk  
• **Staging Area (Index)**: Files prepared for commit  
• **Commit History**: Snapshots stored permanently  

Every Git command moves changes **between these areas**.

---

## 2. Initial Git Configuration

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

**What happens?**  
• Sets identity for all future commits  
• Required before creating commits  

*No repo changes yet.*

---

## 3. Creating a Repository

```bash
git init
```

**What happens?**  
• Creates a hidden `.git/` folder  
• Git starts tracking this directory  

```
Working Directory: files
Staging Area: empty
Commit History: empty
```

---

## 4. Repository Status Explained

```bash
git status
```

**What happens?**  
• Shows file state transitions  
• Answers: What changed? What is staged? What is untracked?  

Key states:  
• Untracked  
• Modified  
• Staged

---

## 5. Adding Files to Staging

```bash
git add <file>
git add .
```

**What happens?**  
• Copies file snapshot into staging area  
• Does NOT create a commit  

```
Working Directory → Staging Area
```

---

## 6. Committing Changes

```bash
git commit -m "message"
```

**What happens?**  
• Takes staged snapshot  
• Stores it permanently in history  

```
Staging Area → Commit History
```

After commit, staging becomes empty.

---

## 7. Viewing Commit History

```bash
git log
git log --oneline
```

**What happens?**  
• Displays commit DAG (history graph)  
• Each commit = full snapshot

---

## 8. Understanding `git diff`

```bash
git diff
```

**What happens?**  
• Shows differences between:

```
Working Directory ↔ Staging Area
```

Use it to **review changes before staging**.

---

## 9. Undoing Staging (`git reset`)

```bash
git reset <file>
```

**What happens?**  
• Removes file from staging  
• Keeps file unchanged locally  

```
Staging Area → Working Directory
```

---

## 10. Removing & Renaming Files

```bash
git rm <file>
git mv old new
```

**What happens?**  
• File deletion/rename is staged automatically  
• Requires commit to finalize  

Git tracks **content changes**, not filenames.

---

## 11. Inspecting a Commit

```bash
git show <commit>
```

**What happens?**  
• Displays exact changes introduced  
• Useful for debugging history

---

## 12. Undoing Commits (Soft vs Hard)

### 12.1 Soft Reset

```bash
git reset --soft HEAD~1
```

• Removes commit  
• Keeps changes staged

### 12.2 Hard Reset

```bash
git reset --hard HEAD~1
```

• Removes commit  
• Deletes changes permanently ⚠️

---

## 13. End‑to‑End Local Workflow

```
Edit file
↓
git diff
↓
git add
↓
git commit
↓
git log
```

Repeat continuously.

---

## 14. Common Beginner Mistakes

• Forgetting `git add` before commit  
• Using `--hard` without understanding  
• Editing files during conflicts blindly  
• Thinking Git stores diffs (it stores snapshots)

---

## 15. Final Mental Model

<img width="275" height="183" alt="image" src="https://github.com/user-attachments/assets/c989894e-95f9-4edf-a8a2-edb200b6fa59" />

Think of Git as:

```
A timeline of snapshots
```

• You edit files freely  
• You stage intentionally  
• You commit deliberately  

If you understand **where your change is**, you understand Git.

---
