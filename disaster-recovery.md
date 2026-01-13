# Git Disaster Recovery

This guide explains **how to recover from catastrophic Git mistakes**, so you:

* Don’t panic when history is broken
* Recover lost commits safely
* Fix messed-up branches without hurting teammates

<img width="318" height="159" alt="image" src="https://github.com/user-attachments/assets/d6100ea1-c813-4256-95db-43e24bd62575" />

> ⚠️ Practical, hands-on, real-world advice — no fluff.

---

## 📚 Index

1. [Why Disaster Recovery Matters](#1-why-disaster-recovery-matters)  
2. [Understand the Graph First](#2-understand-the-graph-first)  
3. [Check `HEAD` and Current Branch](#3-check-head-and-current-branch)  
4. [Viewing `reflog` for Recovery Points](#4-viewing-reflog-for-recovery-points)  
5. [Recovering a Lost Commit](#5-recovering-a-lost-commit)  
6. [Undoing a Bad Rebase](#6-undoing-a-bad-rebase)  
7. [Undoing a Bad Merge](#7-undoing-a-bad-merge)  
8. [Fixing a Broken Branch](#8-fixing-a-broken-branch)  
9. [Reset vs Revert](#9-reset-vs-revert)  
10. [Recovering Deleted Branches](#10-recovering-deleted-branches)  
11. [Recovering Forced-Pushed History](#11-recovering-forced-pushed-history)  
12. [When to Use `git fsck`](#12-when-to-use-git-fsck)  
13. [Recovering Orphaned Commits](#13-recovering-orphaned-commits)  
14. [Common Recovery Mistakes](#14-common-recovery-mistakes)  
15. [Final Recovery Mental Model](#15-final-recovery-mental-model)  

---

## 1. Why Disaster Recovery Matters

Git rarely deletes commits instantly.  
Most “lost” work is **just dangling pointers**.

> Knowledge of internals + reflog = confidence under pressure.

---

## 2. Understand the Graph First

Always visualize history:

```bash
git log --graph --oneline --all
```

Questions to ask:

* Where is `HEAD`?  
* Which branch is broken?  
* What commit(s) are missing?

---

## 3. Check `HEAD` and Current Branch

```bash
git status
git branch -vv
```

* Are you on the branch you think you are?  
* Are you detached?

Detachment often explains “lost commits.”

---

## 4. Viewing `reflog` for Recovery Points

```bash
git reflog
```

Example:

```
d4e5f6 HEAD@{0}: reset: moving to d4e5f6
a1b2c3 HEAD@{1}: commit: Add login feature
```

Reflog is **your undo history**.

---

## 5. Recovering a Lost Commit

```bash
git checkout d4e5f6
git switch -c recovered-branch
```

Or restore branch:

```bash
git branch recovered d4e5f6
```

> Dangling commits aren’t lost until garbage collection.

---

## 6. Undoing a Bad Rebase

```bash
git reflog
git reset --hard HEAD@{3}
```

* HEAD@{3} = state before rebase  
* Never panic, reflog keeps all previous refs

---

## 7. Undoing a Bad Merge

### 7.1 Abort Merge

If merge went wrong:

```bash
git merge --abort
```

### 7.2 Reset After Merge

If already committed:

```bash
git reset --hard HEAD@{1}
```

> Always check reflog first.

---

## 8. Fixing a Broken Branch

Scenario: branch points to wrong commit

```bash
git reset --hard <correct-commit-hash>
git push --force-with-lease origin broken-branch
```

> Ensures teammates are not overwritten blindly.

---

## 9. Reset vs Revert

| Reset                | Revert                     |
| -------------------- | -------------------------- |
| Moves branch pointer | Creates new commit to undo |
| Dangerous on shared  | Safe on shared branches    |
| Local only           | Public safe                |

> Senior rule: **never reset shared branches without `--force-with-lease`.**

---

## 10. Recovering Deleted Branches

```bash
git reflog
git branch recovered <commit-hash>
```

Even a branch deleted days ago can often be restored.

---

## 11. Recovering Forced-Pushed History

```bash
git fetch origin
git reflog show origin/main
git reset --hard <good-commit>
```

> `--force-with-lease` prevents accidental overwrite next time.

---

## 12. When to Use `git fsck`

```bash
git fsck --lost-found
```

* Finds dangling commits  
* Useful if commits are “lost” after weird operations

> Only needed in extreme cases.

---

## 13. Recovering Orphaned Commits

```bash
git show <commit-hash>
git branch recovered <commit-hash>
```

* Orphaned commits = commits with no branch pointing to them  
* Reflog + fsck = rescue toolset

---

## 14. Common Recovery Mistakes

❌ Panic and delete `.git/`  
❌ Force push without checking teammates  
❌ Reset shared branches blindly  
❌ Forgetting reflog exists  
❌ Ignoring backup forks

> Git almost always lets you recover if you stay calm.

---

## 15. Final Recovery Mental Model

> **Git stores everything as objects + refs + logs.  
> Commits are immutable; pointers move.  
> Reflog and fetch are your lifelines.  
> Reset/recover/rebase carefully, never blindly.**

With this, even catastrophic mistakes are recoverable.
