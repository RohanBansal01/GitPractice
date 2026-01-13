# Git Remote Workflow

This guide explains **how to work with remotes safely in a team**, so you:

* Don’t break shared branches  
* Understand what Git is protecting you from  
* Know exactly when history changes

<img width="1160" height="1082" alt="image" src="https://github.com/user-attachments/assets/ec8caab6-b656-4e00-826e-6dae83d8dbe9" />

> This is **mandatory knowledge** for real-world Git usage.

---

## 📚 Index

1. [What a Remote Workflow Is](#1-what-a-remote-workflow-is)  
2. [What `origin` Actually Represents](#2-what-origin-actually-represents)  
3. [Local vs Remote Branches](#3-local-vs-remote-branches)  
4. [Remote-Tracking Branches](#4-remote-tracking-branches)  
5. [What `git fetch` Really Does](#5-what-git-fetch-really-does)  
6. [Why `fetch` Is Always Safe](#6-why-fetch-is-always-safe)  
7. [What `git pull` Really Does](#7-what-git-pull-really-does)  
8. [`pull` with Merge vs Rebase](#8-pull-with-merge-vs-rebase)  
9. [Tracking Branches Explained](#9-tracking-branches-explained)  
10. [Setting and Verifying Upstream](#10-setting-and-verifying-upstream)  
11. [What `git push` Really Does](#11-what-git-push-really-does)  
12. [Fast-Forward vs Rejected Push](#12-fast-forward-vs-rejected-push)  
13. [Safe Force Push (`--force-with-lease`)](#13-safe-force-push---force-with-lease)  
14. [Common Remote Workflow Mistakes](#14-common-remote-workflow-mistakes)  
15. [Final Team-Safe Mental Model](#15-final-team-safe-mental-model)  

---

## 1. What a Remote Workflow Is

A **remote workflow** is how local Git histories are:

* Observed  
* Integrated  
* Published  

Remote workflows exist because **multiple people move refs independently**.

---

## 2. What `origin` Actually Represents

`origin` is:

* A **name** pointing to a remote repository URL  

It is **not**:

* Special  
* Central authority  
* Automatically trusted  

```
origin → https://github.com/org/repo.git
```

---

## 3. Local vs Remote Branches

Local branches:

```
main
feature-auth
```

Remote-tracking branches:

```
origin/main
origin/feature-auth
```

Key rule:

> You commit to local branches only.

---

## 4. Remote-Tracking Branches

`origin/main` means:

> “The last known state of `main` on the remote.”

Facts:

* Read-only  
* Updated only by `git fetch`  
* Never commit to them

---

## 5. What `git fetch` Really Does

```bash
git fetch origin
```

Internally:

1. Downloads new commit objects  
2. Updates `refs/remotes/origin/*`  
3. Does **not** touch your branches  

Fetch is **pure observation**.

---

## 6. Why `fetch` Is Always Safe

`git fetch`:

* Never rewrites history  
* Never causes conflicts  
* Never changes working files  

**Senior rule:**

> Fetch before you think.

---

## 7. What `git pull` Really Does

```bash
git pull
```

Internally:

```bash
git fetch
git merge   # or rebase
```

Meaning:

* Pull **moves refs**  
* Pull can cause conflicts  
* Pull can change history

---

## 8. `pull` with Merge vs Rebase

### 8.1 Merge pull

* Preserves history  
* Adds merge commits  
* Safe for shared branches

### 8.2 Rebase pull

* Rewrites commits  
* Cleaner history  
* Safe only for private branches  

Never rebase pulled shared work.

---

## 9. Tracking Branches Explained

A tracking branch tells Git:

* Where to pull from  
* Where to push to  

Check:

```bash
git branch -vv
```

Without tracking, Git can’t automate.

---

## 10. Setting and Verifying Upstream

Set upstream explicitly:

```bash
git branch --set-upstream-to=origin/main
```

Why this matters:

* `git pull` knows what to merge  
* `git push` knows where to publish

---

## 11. What `git push` Really Does

```bash
git push origin main
```

Git checks:

1. Is this a fast-forward?  
2. Will commits be lost?  
3. Has the remote advanced?  

Push fails to **protect others**.

---

## 12. Fast-Forward vs Rejected Push

Fast-forward:

```
remote: A → B
local:  A → B → C
```

Rejected:

```
remote: A → B → D
local:  A → B → C
```

Git refuses to overwrite `D`.

---

## 13. Safe Force Push (`--force-with-lease`)

```bash
git push --force-with-lease
```

This checks:

> “Has the remote changed since I last fetched?”

If yes → abort  
If no → push  

This protects teammates’ work.

---

## 14. Common Remote Workflow Mistakes

❌ Pulling without fetching  
❌ Force pushing shared branches  
❌ Rebasing after pulling team commits  
❌ Committing to outdated branches  
❌ Ignoring rejected push warnings  

All of these break **shared refs**.

---

## 15. Final Team-Safe Mental Model

> **Local branches are private workspaces.  
> Remote branches are shared truth.  
> Fetch to observe.  
> Merge or rebase consciously.  
> Push only when history is safe.**
