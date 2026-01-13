# GitPractice – Learning Roadmap 🧭

This roadmap is designed to take you from **Git beginner → confident team contributor → senior-level Git user**.

The goal is not memorizing commands, but **understanding what Git is doing and how to recover when things go wrong**.

<img width="600" height="428" alt="image" src="https://github.com/user-attachments/assets/6d0ce931-1661-4da4-b523-0d3c95c02656" />

---

## 📚 Index

1. [Level 1: Foundations (Beginner)](#1-level-1-foundations-beginner)  
2. [Level 2: Branching & Local Workflows (Intermediate)](#2-level-2-branching--local-workflows-intermediate)  
3. [Level 3: Remote Workflows (Team-Ready)](#3-level-3-remote-workflows-team-ready)  
4. [Level 4: Git Internals (Confidence Layer)](#4-level-4-git-internals-confidence-layer)  
5. [Level 5: Disaster Recovery (Senior-Level)](#5-level-5-disaster-recovery-senior-level)  
6. [Additional Documentation / Reference Docs](#6-additional-documentation--reference-docs)  
7. [Final Mental Model](#7-final-mental-model)  
8. [How to Use This Roadmap](#8-how-to-use-this-roadmap)  

---

## 1. Level 1: Foundations (Beginner)

**Goal:** Become comfortable using Git locally without fear.

### 1.1 Topics

* What Git is (snapshot-based, not diff-based)  
* Repository, working tree, staging area  
* Commits and commit history

### 1.2 Practice From Repo

* `basic-commands/`

### 1.3 Must-Know Commands

```bash
git init
git status
git add
git commit
git log
git diff
```

### 1.4 You’re Ready to Move On When

* You understand what a commit represents  
* You know what is staged vs unstaged  
* You are not afraid of making commits

---

## 2. Level 2: Branching & Local Workflows (Intermediate)

**Goal:** Work with branches confidently and understand history.

### 2.1 Topics

* Branches as pointers  
* Merging vs rebasing  
* Conflict basics

### 2.2 Practice From Repo

* `branching/`  
* `rebasing/`  
* `conflicts/`

### 2.3 Must-Know Commands

```bash
git branch
git switch
git merge
git rebase
git cherry-pick
```

### 2.4 Common Mistakes to Learn From

* Rebasing shared branches  
* Resolving conflicts without understanding them

### 2.5 You’re Ready to Move On When

* You can explain the difference between merge and rebase  
* You can fix a simple conflict calmly

---

## 3. Level 3: Remote Workflows (Team-Ready)

**Goal:** Work safely with other developers.

### 3.1 Topics

* Remotes and remote-tracking branches  
* `fetch` vs `pull`  
* Push safety rules

### 3.2 Practice From Repo

* `git-workflow/`

### 3.3 Must-Know Commands

```bash
git remote -v
git fetch
git pull
git push
```

### 3.4 Senior Rules

* Prefer `fetch` over blind `pull`  
* Never force-push to shared branches  
* Always understand what you are pushing

### 3.5 You’re Ready to Move On When

* You understand what `origin/main` really is  
* You can explain why a push was rejected

---

## 4. Level 4: Git Internals (Confidence Layer)

**Goal:** Understand *why* Git behaves the way it does.

### 4.1 Topics

* `.git` directory  
* Objects (commit, tree, blob)  
* Refs, HEAD, detached HEAD  
* Reflog

### 4.2 Practice From Repo

* `git-internals/`

### 4.3 Key Insight

> Git is a graph of immutable objects with movable pointers.

### 4.4 You’re Ready to Move On When

* You understand that deleting commits usually means losing refs  
* You trust Git’s safety model

---

## 5. Level 5: Disaster Recovery (Senior-Level)

**Goal:** Stay calm under pressure and recover from mistakes.

### 5.1 Topics

* Undoing bad rebases  
* Recovering deleted commits  
* Fixing broken branches

### 5.2 Practice From Repo

* `disaster-recovery/`

### 5.3 Must-Know Commands

```bash
git reflog
git reset --hard
git revert
```

### 5.4 Senior Mindset

* Mistakes are expected  
* Recovery is a skill, not luck  
* Reflog is your best friend

---

## 6. Additional Documentation / Reference Docs

To truly master Git in a professional environment, consult these **team reference documents**:

```
docs/
├── pull-request-guidelines.md       # PR rules & workflow
├── engineering-vocabulary.md        # Industry terms / Git vocabulary
└── engineering-foundations.md       # Ownership, production mindset, incident handling, etc.
```

> These documents complement practical Git skills with **PR culture, vocabulary, and senior engineering mindset**.

---

## 7. Final Mental Model

> **Git is safe by design.  
> Commits are rarely lost.  
> Most problems are pointer problems.  
> If it happened locally, reflog remembers it.**

Once this clicks, Git stops being scary.

---

## 8. How to Use This Roadmap

* Follow levels in order  
* Practice, don’t rush  
* Break things intentionally  
* Recover them confidently

This is how real Git mastery is built.
