# Git Internals 

This guide explains **how Git actually works under the hood**, using the **real internal components** Git uses every day.

You’ll understand:

* Why Git feels safe
* Why mistakes are recoverable
* What changes when you run each command

> Lightweight, practical, non-academic.
> This is the **confidence layer** most developers never build.
<img width="1782" height="1606" alt="image" src="https://github.com/user-attachments/assets/b915968d-9d79-4b17-8904-b005de76ae1a" />


---

## 📚 Index

1. What Git Internals Really Are
2. The `.git` Directory (Big Picture)
3. Git Objects (Blue)
4. Commit Objects
5. Tree Objects
6. Blob Objects
7. Git Refs (Red)
8. Branches Are Just Refs
9. Tags vs Branch Refs
10. `HEAD` and Detached `HEAD`
11. Logs / Reflog (Green)
12. Why Reflog Is Your Safety Net
13. Remotes as Refs
14. Config & Temp Files
15. Final Unified Mental Model
16. Do and Don'ts

---

## 1️⃣ What Git Internals Really Are

**Git internals are the files inside `.git/` that store your history, pointers, and recovery data.**

Git doesn’t hide magic — it hides *files*.

---

## 2️⃣ The `.git` Directory (Big Picture)

At a high level, `.git/` contains:

* **Objects** → actual data (blue)
* **Refs** → pointers to data (red)
* **Logs** → history of pointer movement (green)
* **Config** → behavior settings (light gray)
* **Temp** → short-lived operational files (gray)

Everything Git does touches one of these.

---

## 3️⃣ Git Objects (Blue)

**Objects store all real data in Git.**

Located in:

```
.git/objects/
```

They are:

* Immutable
* Content-addressed (by hash)
* Never edited, only added

Three types exist:

* commit
* tree
* blob

---

## 4️⃣ Commit Objects

A **commit object** contains:

* Pointer to a tree
* Pointer(s) to parent commit(s)
* Metadata (author, message, timestamp)

Conceptually:

```
commit
 ├── tree
 ├── parent
 └── metadata
```

Commits do **not** store files directly.

---

## 5️⃣ Tree Objects

A **tree object** represents a directory.

It maps:

```
filename → blob
subdir   → tree
```

Trees give Git its directory structure.
Without trees, commits would be flat.

---

## 6️⃣ Blob Objects

A **blob** stores raw file content.

Important:

* No filename
* No permissions
* Just bytes

If two files have the same content → same blob.

This is why Git is space-efficient.

---

## 7️⃣ Git Refs (Red)

**Refs are human-readable pointers to commit hashes.**

Located in:

```
.git/refs/
```

Examples:

* `refs/heads/main`
* `refs/heads/feature-login`
* `refs/remotes/origin/main`
* `refs/tags/v1.0`

Refs are how humans interact with commits.

---

## 8️⃣ Branches Are Just Refs

A branch is nothing more than:

```
branch-name → commit-hash
```

When you commit:

* Git creates a new commit object
* Git moves the branch ref forward

Old commits remain untouched.

Branches are cheap because refs are cheap.

---

## 9️⃣ Tags vs Branch Refs

| Branch Ref        | Tag Ref        |
| ----------------- | -------------- |
| Moves             | Never moves    |
| Development       | Release marker |
| Updated on commit | Fixed forever  |

Tags are **anchors**.
Branches are **moving pointers**.

---

## 🔟 `HEAD` and Detached `HEAD`

`HEAD` is a special ref:

```
HEAD → current branch → commit
```

Detached `HEAD`:

```
HEAD → commit (no branch)
```

This happens when you checkout a commit directly.

Fix immediately:

```bash
git switch -c new-branch
```

Otherwise, commits become unreachable.

---

## 1️⃣1️⃣ Logs / Reflog (Green)

**Logs record ref movement over time.**

Located in:

```
.git/logs/
```

`reflog` answers:

> “Where did this ref point before?”

Commands recorded:

* commit
* reset
* rebase
* checkout
* amend

---

## 1️⃣2️⃣ Why Reflog Is Your Safety Net

Commits aren’t lost immediately.

Even after:

```bash
git reset --hard
```

You can recover:

```bash
git reflog
git reset --hard HEAD@{n}
```

If it happened locally, **reflog knows**.

---

## 1️⃣3️⃣ Remotes as Refs

Remote branches are just refs too:

```
refs/remotes/origin/main
```

Rules:

* You never commit to them
* They update only on `git fetch`

`git fetch` = update remote refs
`git pull` = fetch + merge/rebase

---

## 1️⃣4️⃣ Config & Temp Files

### Config (Light Gray)

Located in:

```
.git/config
```

Controls:

* remotes
* merge behavior
* rebase defaults
* hooks

### Temp (Gray)

Examples:

* `MERGE_HEAD`
* `REBASE_HEAD`
* `CHERRY_PICK_HEAD`

These exist **only during operations**.
If Git crashes, these explain what was happening.

---

## 1️⃣5️⃣ Final Unified Mental Model

> **Git is a content-addressed object store
>
> * refs that move
> * logs that remember movement
> * config that controls behavior.**

You don’t “delete commits”.
You only lose pointers — and reflog remembers them.

---

## 1️⃣6️⃣ Git Internals — Do’s and Don’ts (Senior Rules)

These rules exist **because of how Git internals work**, not because of “best practice folklore”.

---

### ✅ DO: Think in Pointers, Not Files

**Why (internals):**

* Files live in **blob objects**
* History is tracked by **refs pointing to commits**

**Rule:**

> You are always moving pointers, never editing history directly.

This mindset prevents panic.

---

### ❌ DON’T: Panic After `reset --hard`

**Why (internals):**

* Commits still exist as objects
* Only refs moved
* Reflog recorded the movement

**Correct response:**

```bash
git reflog
git reset --hard HEAD@{n}
```

Reset is reversible because **objects are immutable**.

---

### ✅ DO: Create a Branch Immediately in Detached `HEAD`

**Why (internals):**

* Detached `HEAD` = no ref pointing to new commits
* Unreferenced commits can be garbage-collected

**Rule:**

```bash
git switch -c safe-branch
```

This creates a **ref**, which protects the commit.

---

### ❌ DON’T: Commit Directly to `origin/*`

**Why (internals):**

* `origin/*` lives under `refs/remotes/`
* These are **read-only tracking refs**

They exist to **observe**, not modify.

---

### ✅ DO: Fetch Before Any Risky Operation

**Why (internals):**

* `git fetch` only updates remote refs
* No objects or refs are destroyed
* No working tree changes

**Senior rule:**

> Fetch gives you information without consequences.

---

### ❌ DON’T: Use `git pull` Blindly

**Why (internals):**

* `pull` = `fetch` + `merge/rebase`
* That means **ref movement + possible conflict**

Always know *which refs will move* before pulling.

---

### ✅ DO: Use `--force-with-lease`, Never Plain `--force`

**Why (internals):**

* Plain force overwrites remote refs unconditionally
* Lease checks the remote ref state first

```bash
git push --force-with-lease
```

This respects **other people’s refs**.

---

### ❌ DON’T: Delete `.git` Files Manually (Unless You Know Why)

**Why (internals):**

* `.git` is not cache
* Objects, refs, logs are interdependent

Deleting files here can orphan commits permanently.

If you don’t know what it is — don’t delete it.

---

### ✅ DO: Use Reflog as Your Undo History

**Why (internals):**

* Reflog logs **ref movement**, not commits
* It survives rebases, resets, amends

Mental model:

> Reflog = “timeline of my mistakes”

---

### ❌ DON’T: Assume Commits Are Deleted Immediately

**Why (internals):**

* Objects are garbage-collected lazily
* Only unreachable objects are eligible
* GC runs much later

This is why recovery usually works.

---

### ✅ DO: Understand Temp Files During Operations

**Why (internals):**

* Files like `MERGE_HEAD`, `REBASE_HEAD`
* Indicate Git is mid-operation

If something breaks:

* These files explain *what Git was doing*

Never ignore them.

---

### ❌ DON’T: Rebase Shared Branches

**Why (internals):**

* Rebase rewrites commit objects
* Remote refs now point to different histories
* Teammates’ refs diverge

Rebase is safe **only where refs are private**.

---

### ✅ DO: Use Tags for Releases, Not Branches

**Why (internals):**

* Tags never move
* Branch refs move constantly

Releases need **immutability**, not convenience.

---

### ❌ DON’T: Fear Git — Fear Ignorance

**Why (internals):**

* Git is conservative
* Objects persist
* Logs remember
* Refs are recoverable

Most damage comes from *not knowing where pointers moved*.

---

## 🧠 Final Operational Mental Model (With Rules)

> **Objects store truth
> Refs decide visibility
> Logs remember mistakes
> Config controls behavior
> Temp files show intent**

If you respect those five layers:

* You won’t lose work
* You won’t break teammates
* You won’t fear Git internals

You’ll **reason about Git instead of memorizing commands*

---



