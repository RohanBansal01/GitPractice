# Engineering Vocabulary

This document defines the **minimum vocabulary** a beginner must understand to operate **professionally** in real engineering teams.

This is **not theory**.  
This is the **language used daily** in code reviews, standups, PRs, and incidents.

---

## 📚 Index

1. [Purpose of This Document](#1-purpose-of-this-document)  
2. [File Naming (Industry-Standard)](#2-file-naming-industry-standard)  
3. [Repository](#3-repository)  
4. [Commit](#4-commit)  
5. [Branch](#5-branch)  
6. [Main / Trunk](#6-main--trunk)  
7. [Feature Branch](#7-feature-branch)  
8. [Merge](#8-merge)  
9. [Rebase](#9-rebase)  
10. [Conflict](#10-conflict)  
11. [Pull Request (PR)](#11-pull-request-pr)  
12. [Review & Approval Terms](#12-review--approval-terms)  
13. [CI / Build / Checks](#13-ci--build--checks)  
14. [Architecture Vocabulary](#14-architecture-vocabulary)  
15. [Professional Review Language (Do / Don’t)](#15-professional-review-language-do--dont)  
16. [Final Mental Model](#16-final-mental-model)  

---

## 1. Purpose of This Document

This file exists to:

> **Align beginners with industry language used by senior engineers.**

If you understand these terms, you:

* Communicate clearly  
* Avoid confusion  
* Gain trust faster

---

## 2. File Naming (Industry-Standard)

Correct file name:

```
engineering-vocabulary.md
```

Recommended location:

```
docs/engineering-vocabulary.md
```

### 2.1 Why this is correct

* `docs/` → industry-standard documentation folder  
* Descriptive, searchable, professional  
* Signals **team knowledge**, not personal notes

🚫 Avoid:

* `terms.md`  
* `notes.md`  
* `random-doc.md`

---

## 3. Repository

**What it means:**

> A project **plus its entire version history**

A repo is not just code — it’s:

* Commits  
* Branches  
* Tags  
* Configuration  
* Collaboration history

---

## 4. Commit

**What it means:**

> A snapshot of the project at a point in time

Key ideas:

* Commits are immutable  
* They form a graph  
* Everything in Git builds on commits

---

## 5. Branch

**What it means:**

> A movable pointer to a commit

Important:

* Branches are cheap  
* Branches are not copies of code  
* They only move forward as you commit

---

## 6. Main / Trunk

**What it means:**

> The primary shared branch of the repository

Rules:

* Must stay stable  
* Must pass CI  
* Represents deployable state

---

## 7. Feature Branch

**What it means:**

> A short-lived branch for isolated work

Used for:

* Features  
* Fixes  
* Refactors

Deleted after merge.

---

## 8. Merge

**What it means:**

> Combining histories of two branches

Key types:

* Fast-forward merge  
* Merge commit

Merges preserve history.

---

## 9. Rebase

**What it means:**

> Replaying commits on a new base commit

Used to:

* Keep history linear  
* Clean up commits

⚠️ Rewrites history — use carefully.

---

## 10. Conflict

**What it means:**

> Git cannot automatically combine changes

Conflicts are:

* Normal  
* Not errors  
* A signal of overlapping work

Solved by humans.

---

## 11. Pull Request (PR)

**What it means:**

> A request to merge changes into shared history

PRs exist for:

* Review  
* Discussion  
* Accountability  
* Quality control

---

## 12. Review & Approval Terms

Common industry language:

* **LGTM** → Looks Good To Me  
* **Approve** → Acceptable to merge  
* **Request Changes** → Blocking issues exist  
* **Draft PR** → Work in progress  
* **Code Owner** → Responsible person/team

Approval means **safe to ship**, not perfect.

---

## 13. CI / Build / Checks

Core terms:

* **CI** → Continuous Integration  
* **Pipeline** → Automated workflow  
* **Build** → Compile/package step  
* **Check** → Individual CI job  
* **Green Build** → All checks passed  
* **Red Build** → Something failed

Never merge a red build.

---

## 14. Architecture Vocabulary

These appear in reviews constantly:

* **Refactor** → Improve code without changing behavior  
* **Tech Debt** → Intentional compromise  
* **Breaking Change** → Breaks existing users  
* **Backward Compatibility** → Old behavior still works  
* **Coupling** → Dependency between components  
* **Cohesion** → Focus of a component  
* **Abstraction** → Hiding complexity

---

## 15. Professional Review Language (Do / Don’t)

### 15.1 ✅ Use These Phrases

* “Nit: minor suggestion”  
* “Blocking: must fix”  
* “Non-blocking feedback”  
* “What’s the rationale here?”  
* “Trade-off accepted”

### 15.2 🚫 Avoid These

* “This is wrong”  
* “Bad code”  
* “Why did you do this?”

Tone = professionalism.

---

## 16. Final Mental Model

> **Knowing tools is junior.  
> Knowing vocabulary is professional.  
> Using the right words builds trust instantly.**

If you speak this language, you belong in the room.
