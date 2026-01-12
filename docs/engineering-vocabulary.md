# Engineering Vocabulary 

This document defines the **minimum vocabulary** a beginner must understand to operate **professionally** in real engineering teams.

This is **not theory**.
This is the **language used daily** in code reviews, standups, PRs, and incidents.

---

## 📚 Index 

1. Purpose of This Document
2. File Naming (Industry-Standard)
3. Repository
4. Commit
5. Branch
6. Main / Trunk
7. Feature Branch
8. Merge
9. Rebase
10. Conflict
11. Pull Request (PR)
12. Review & Approval Terms
13. CI / Build / Checks
14. Architecture Vocabulary
15. Professional Review Language (Do / Don’t)

---

## 1️⃣ Purpose of This Document

This file exists to:

> **Align beginners with industry language used by senior engineers.**

If you understand these terms, you:

* Communicate clearly
* Avoid confusion
* Gain trust faster

---

## 2️⃣ File Naming (Industry-Standard)

Correct file name:

```
engineering-vocabulary.md
```

Recommended location:

```
docs/engineering-vocabulary.md
```

### Why this is correct

* `docs/` → industry-standard documentation folder
* Descriptive, searchable, professional
* Signals **team knowledge**, not personal notes

🚫 Avoid:

* `terms.md`
* `notes.md`
* `random-doc.md`

---

## 3️⃣ Repository (Repo)

**What it means:**

> A project **plus its entire version history**

A repo is not just code — it’s:

* Commits
* Branches
* Tags
* Configuration
* Collaboration history

---

## 4️⃣ Commit

**What it means:**

> A snapshot of the project at a point in time

Key ideas:

* Commits are immutable
* They form a graph
* Everything in Git builds on commits

---

## 5️⃣ Branch

**What it means:**

> A movable pointer to a commit

Important:

* Branches are cheap
* Branches are not copies of code
* They only move forward as you commit

---

## 6️⃣ Main / Trunk

**What it means:**

> The primary shared branch of the repository

Rules:

* Must stay stable
* Must pass CI
* Represents deployable state

---

## 7️⃣ Feature Branch

**What it means:**

> A short-lived branch for isolated work

Used for:

* Features
* Fixes
* Refactors

Deleted after merge.

---

## 8️⃣ Merge

**What it means:**

> Combining histories of two branches

Key types:

* Fast-forward merge
* Merge commit

Merges preserve history.

---

## 9️⃣ Rebase

**What it means:**

> Replaying commits on a new base commit

Used to:

* Keep history linear
* Clean up commits

⚠️ Rewrites history — use carefully.

---

## 🔟 Conflict

**What it means:**

> Git cannot automatically combine changes

Conflicts are:

* Normal
* Not errors
* A signal of overlapping work

Solved by humans.

---

## 1️⃣1️⃣ Pull Request (PR)

**What it means:**

> A request to merge changes into shared history

PRs exist for:

* Review
* Discussion
* Accountability
* Quality control

---

## 1️⃣2️⃣ Review & Approval Terms

Common industry language:

* **LGTM** → Looks Good To Me
* **Approve** → Acceptable to merge
* **Request Changes** → Blocking issues exist
* **Draft PR** → Work in progress
* **Code Owner** → Responsible person/team

Approval means **safe to ship**, not perfect.

---

## 1️⃣3️⃣ CI / Build / Checks

Core terms:

* **CI** → Continuous Integration
* **Pipeline** → Automated workflow
* **Build** → Compile/package step
* **Check** → Individual CI job
* **Green Build** → All checks passed
* **Red Build** → Something failed

Never merge a red build.

---

## 1️⃣4️⃣ Architecture Vocabulary

These appear in reviews constantly:

* **Refactor** → Improve code without changing behavior
* **Tech Debt** → Intentional compromise
* **Breaking Change** → Breaks existing users
* **Backward Compatibility** → Old behavior still works
* **Coupling** → Dependency between components
* **Cohesion** → Focus of a component
* **Abstraction** → Hiding complexity

---

## 1️⃣5️⃣ Professional Review Language (Critical)

### ✅ Use These Phrases

* “Nit: minor suggestion”
* “Blocking: must fix”
* “Non-blocking feedback”
* “What’s the rationale here?”
* “Trade-off accepted”

### 🚫 Avoid These

* “This is wrong”
* “Bad code”
* “Why did you do this?”

Tone = professionalism.

---

## 🧠 Final Senior Mental Model

> **Knowing tools is junior.
> Knowing vocabulary is professional.
> Using the right words builds trust instantly.**

If you speak this language, you belong in the room.

---

