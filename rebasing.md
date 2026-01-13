# Git Rebase – Step by Step

This guide explains **Git rebasing** in depth:

* How history diverges  
* How rebase rewrites commits  
* How conflicts occur and are resolved  
* When rebasing is safe vs dangerous

<img width="2742" height="1257" alt="image" src="https://github.com/user-attachments/assets/aa34bcaa-7335-49ae-9f55-12523682d97b" />
<img width="633" height="656" alt="image" src="https://github.com/user-attachments/assets/4968c8b9-cf0c-45e8-86d2-6bba3fedcd48" />

---

## 📌 Index

1. [What Is Git Rebase](#1-what-is-git-rebase)  
2. [Rebase vs Merge (Conceptual Difference)](#2-rebase-vs-merge-conceptual-difference)  
3. [When Rebasing Is Used](#3-when-rebasing-is-used)  
4. [Creating a Feature Branch](#4-creating-a-feature-branch)  
5. [Making Commits on Feature Branch](#5-making-commits-on-feature-branch)  
6. [Advancing `main` Independently](#6-advancing-main-independently)  
7. [Triggering a Rebase](#7-triggering-a-rebase)  
8. [What Happens During Rebase (Internals)](#8-what-happens-during-rebase-internals)  
9. [Visual Diagram – Before Rebase](#9-visual-diagram--before-rebase)  
10. [Visual Diagram – After Rebase](#10-visual-diagram--after-rebase-history-rewritten)  
11. [Real Rebase Conflict Scenario](#11-real-rebase-conflict-scenario)  
12. [Resolving a Rebase Conflict](#12-resolving-a-rebase-conflict)  
13. [Aborting a Rebase](#13-aborting-a-rebase)  
14. [Common Mistakes](#14-common-mistakes)  
15. [Best Practices & Final Mental Model](#15-best-practices--final-mental-model)  
16. [Rebase Failure Mode](#16-rebase-failure-mode--rebase-hell-why-merge-sometimes-wins)  
17. [Final Mental Model](#17-final-mental-model)  
18. [One-Line Summary](#18-one-line-summary)  

---

## 1. What Is Git Rebase

**Rebase** moves your commits and **replays them on top of another branch**.

Instead of merging histories, Git:

* Temporarily removes your commits  
* Updates your branch to latest base  
* Re-applies your commits one by one

---

## 2. Rebase vs Merge (Conceptual Difference)

<img width="259" height="194" alt="image" src="https://github.com/user-attachments/assets/4f980b32-281b-4b54-9287-2231a7828551" />

| Merge | Rebase |
|-----|-------|
| Preserves history | Rewrites history |
| Adds merge commit | No merge commit |
| Safe for shared branches | Dangerous if misused |
| Non-linear graph | Linear history |

> **Merge records what happened. Rebase pretends it happened later.**

---

## 3. When Rebasing Is Used

✔ Clean feature branch before PR  
✔ Keep linear commit history  
✔ Update feature branch with latest `main`  
❌ Never rebase shared / pushed branches  

---

## 4. Creating a Feature Branch

```bash
git checkout -b feature-branch
```

**Explanation:**

* Creates `feature-branch`  
* Switches to it immediately  
* Base is current `main`

---

## 5. Making Commits on Feature Branch

```bash
echo "Feature commit 1" >> feature.txt
git add feature.txt
git commit -m "Feature commit 1"
```

```bash
echo "Feature commit 2" >> feature.txt
git add feature.txt
git commit -m "Feature commit 2"
```

**Explanation:**

* Two commits exist only on `feature-branch`  
* `main` remains unchanged

---

## 6. Advancing `main` Independently

```bash
git checkout main
```

```bash
echo "Main commit 1" >> main.txt
git add main.txt
git commit -m "Main commit 1"
```

**Explanation:**

* `main` now has new commits  
* Branch histories diverge

---

## 7. Triggering a Rebase

```bash
git checkout feature-branch
git rebase main
```

**Explanation:**

* Git finds the common ancestor  
* Temporarily removes feature commits  
* Replays them on top of latest `main`  
* **Commit hashes change**

---

## 8. What Happens During Rebase (Internals)

Internally Git does:

```
1. Save feature commits
2. Move branch pointer to main
3. Re-apply commits one by one
4. Create NEW commits
```

Old commits become **orphaned**.

---

## 9. Visual Diagram – Before Rebase

```
main (HEAD)
*
| Main commit 1
*
| Initial commit
 \
  feature-branch
  *
  | Feature commit 2
  *
  | Feature commit 1
```

---

## 10. Visual Diagram – After Rebase (History Rewritten)

```
main
*
| Main commit 1
*
| Initial commit
 \
  feature-branch (HEAD)
  *
  | Feature commit 2'
  *
  | Feature commit 1'
```

⚠️ Apostrophe (`'`) means **new commit hash**

---

## 11. Real Rebase Conflict Scenario

Conflict occurs when:

* Same file  
* Same lines  
* Modified in both branches

Example:

```bash
git rebase main
```

❌ Conflict in `feature.txt`

---

## 12. Resolving a Rebase Conflict

Open the conflicted file:

```text
<<<<<<< HEAD
Main branch change
=======
Feature branch change
>>>>>>> Feature commit
```

### Resolve manually:

```text
Main branch change
Feature branch change
```

Then continue:

```bash
git add feature.txt
git rebase --continue
```

Repeat until all commits are replayed.

---

## 13. Aborting a Rebase

```bash
git rebase --abort
```

**Explanation:**

* Cancels the entire rebase  
* Restores branch to original state  
* No history damage

---

## 14. Common Mistakes

❌ Rebasing pushed branches  
❌ Rebasing `main` or `develop`  
❌ Force-pushing without team agreement  
❌ Using rebase to “fix” broken commits  

---

## 15. Best Practices & Final Mental Model

### Best Practices

✔ Rebase only local feature branches  
✔ Rebase before PR, not after  
✔ Use merge for shared branches  
✔ Use interactive rebase for cleanup

---

## 16. Rebase Failure Mode — “Rebase Hell” (Why Merge Sometimes Wins)

Rebase can turn a **single logical conflict** into **many sequential conflicts** because Git replays commits **one-by-one**, not end-state-to-end-state.

**Why this happens:**

* Merge compares **final branch states**  
* Rebase compares **every intermediate commit**  
* Fixes in later commits are **unknown during earlier conflict resolution**

**Result:**

* Repeated manual conflict resolution  
* Higher risk of human error  
* Massive time waste  
* Increased chance of broken code

> **Mental Model:**  
> Merge resolves *what matters*.  
> Rebase replays *everything*, even mistakes that were already fixed.

**Rule of Thumb:**

* ✔ Use **merge** when branches diverged significantly  
* ✔ Use **rebase** only for short-lived, local, clean feature branches  
* ❌ Never rebase to “fix” collaboration problems

<img width="500" height="750" alt="image" src="https://github.com/user-attachments/assets/2c8913ea-9a93-4fe1-b127-050dcd872d07" />

---

## 17. Final Mental Model

> **Rebase rewrites time. Merge records reality.  
> Use rebase for clarity, merge for collaboration.**

---

## 18. One-Line Summary

<img width="300" height="168" alt="image" src="https://github.com/user-attachments/assets/d03c5356-8b88-43e2-a5bc-66d9b3beb9e6" />

> **Rebase makes history cleaner, but mistakes permanent — respect it.**
