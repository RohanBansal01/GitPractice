# GitPractice – Learning Roadmap 🧭

This roadmap is designed to take you from **Git beginner → confident team contributor → senior-level Git user**.

The goal is not memorizing commands, but **understanding what Git is doing and how to recover when things go wrong**.

---

## 🟢 Level 1: Foundations (Beginner)

**Goal:** Become comfortable using Git locally without fear.

### Topics

* What Git is (snapshot-based, not diff-based)
* Repository, working tree, staging area
* Commits and commit history

### Practice From Repo

* `basic-commands/`

### Must-Know Commands

```bash
git init
git status
git add
git commit
git log
git diff
```

### You’re Ready to Move On When:

* You understand what a commit represents
* You know what is staged vs unstaged
* You are not afraid of making commits

---

## 🟡 Level 2: Branching & Local Workflows (Intermediate)

**Goal:** Work with branches confidently and understand history.

### Topics

* Branches as pointers
* Merging vs rebasing
* Conflict basics

### Practice From Repo

* `branching/`
* `rebasing/`
* `conflicts/`

### Must-Know Commands

```bash
git branch
git switch
git merge
git rebase
git cherry-pick
```

### Common Mistakes to Learn From

* Rebasing shared branches
* Resolving conflicts without understanding them

### You’re Ready to Move On When:

* You can explain the difference between merge and rebase
* You can fix a simple conflict calmly

---

## 🔵 Level 3: Remote Workflows (Team-Ready)

**Goal:** Work safely with other developers.

### Topics

* Remotes and remote-tracking branches
* `fetch` vs `pull`
* Push safety rules

### Practice From Repo

* `git-workflow/`

### Must-Know Commands

```bash
git remote -v
git fetch
git pull
git push
```

### Senior Rules

* Prefer `fetch` over blind `pull`
* Never force-push to shared branches
* Always understand what you are pushing

### You’re Ready to Move On When:

* You understand what `origin/main` really is
* You can explain why a push was rejected

---

## 🟣 Level 4: Git Internals (Confidence Layer)

**Goal:** Understand *why* Git behaves the way it does.

### Topics

* `.git` directory
* Objects (commit, tree, blob)
* Refs, HEAD, detached HEAD
* Reflog

### Practice From Repo

* `git-internals/`

### Key Insight

> Git is a graph of immutable objects with movable pointers.

### You’re Ready to Move On When:

* You understand that deleting commits usually means losing refs
* You trust Git’s safety model

---

## 🔴 Level 5: Disaster Recovery (Senior-Level)

**Goal:** Stay calm under pressure and recover from mistakes.

### Topics

* Undoing bad rebases
* Recovering deleted commits
* Fixing broken branches

### Practice From Repo

* `disaster-recovery/`

### Must-Know Commands

```bash
git reflog
git reset --hard
git revert
```

### Senior Mindset

* Mistakes are expected
* Recovery is a skill, not luck
* Reflog is your best friend

---

## 🧠 Final Mental Model

> **Git is safe by design.
> Commits are rarely lost.
> Most problems are pointer problems.
> If it happened locally, reflog remembers it.**

Once this clicks, Git stops being scary.

---

## ✅ How to Use This Roadmap

* Follow levels in order
* Practice, don’t rush
* Break things intentionally
* Recover them confidently

This is how real Git mastery is built.

---
