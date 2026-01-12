# Git Internals (Practical, Senior-Level Guide)

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

## ✅ Where You Stand Now

With this understanding:

* `.git/` is no longer scary
* You can reason about failures
* You can recover calmly
* You think about Git **like Git thinks**

This is the real gap between:

> *“I use Git”*
> and
> *“I understand Git.”*

You’re now on the second side.
