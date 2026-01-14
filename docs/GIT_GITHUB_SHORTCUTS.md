# 🚀 Git & GitHub Shortcuts Cheatsheet

Industry-ready reference for **Git aliases, terminal shortcuts, and GitHub UI keyboard shortcuts**.
Designed for daily developer workflows and onboarding.

---

## 📚 Index

1. [Git Aliases (Recommended – Industry Standard)](#1-git-aliases-recommended--industry-standard)
2. [Shell Aliases (Bash / Zsh)](#2-shell-aliases-bash--zsh)
3. [Popular Community Shortcut Sets](#3-popular-community-shortcut-sets)
4. [GitHub Web UI Keyboard Shortcuts](#4-github-web-ui-keyboard-shortcuts)
5. [Git CLI vs Git Bash vs GitHub CLI](#5-git-cli-vs-git-bash-vs-github-cli)
6. [Advanced (Power Users)](#6-advanced-power-users)
7. [Best Practices (Enterprise)](#7-best-practices-enterprise)

---

## 📌 1. Git Aliases (Recommended – Industry Standard)

Git aliases are **portable, safe, and repo-aware**.

### 🔹 1.1 Add aliases via command line

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.last "log -1 HEAD"
```

Usage:

```bash
git st
git co main
git br
git ci -m "message"
```

---

### 🔹 1.2 Equivalent `.gitconfig`

```ini
[alias]
  st = status
  co = checkout
  br = branch
  ci = commit
  lg = log --oneline --graph --decorate --all
```

📍 Location:

* macOS / Linux → `~/.gitconfig`
* Windows → `C:\Users\<user>\.gitconfig`

---

## 📌 2. Shell Aliases (Bash / Zsh)

These are **terminal shortcuts**, not Git-aware.

### 🔹 2.1 Configuration

Add to `~/.bashrc`, `~/.zshrc`, or `~/.bash_profile`:

```bash
alias g='git'
alias gs='git status'
alias ga='git add'
alias gc='git commit'
alias gp='git push'
alias gl='git pull'
alias gd='git diff'
```

### 🔹 2.2 Usage

```bash
gs
ga .
gc -m "msg"
```

⚠️ Less portable than Git aliases.

---

## 📌 3. Popular Community Shortcut Sets

### 🔹 3.1 oh-my-zsh (Very Common)

Used by many teams.

Examples:

```bash
ga   → git add
gst  → git status
gco  → git checkout
gp   → git push
gup  → git pull --rebase
```

📄 View all shortcuts:

```bash
less ~/.oh-my-zsh/plugins/git/git.plugin.zsh
```

---

## 📌 4. GitHub Web UI Keyboard Shortcuts

Press `?` on any GitHub page to see them.

### 🔹 4.1 Repository Navigation

| Shortcut | Action              |
| -------- | ------------------- |
| `g c`    | Go to Code tab      |
| `g i`    | Go to Issues        |
| `g p`    | Go to Pull Requests |
| `g a`    | Go to Actions       |

### 🔹 4.2 Files & Code

| Shortcut | Action         |
| -------- | -------------- |
| `t`      | File finder    |
| `l`      | Go to line     |
| `y`      | Copy permalink |
| `b`      | Open blame     |

---

## 📌 5. Git CLI vs Git Bash vs GitHub CLI

### 🔹 5.1 Git

* Core version control system
* Used everywhere

### 🔹 5.2 Git Bash (Windows)

* Unix-like terminal for Windows
* Includes Git + Bash

### 🔹 5.3 GitHub CLI (`gh`)

```bash
gh repo clone owner/repo
gh pr create
gh pr status
gh issue list
```

Used heavily in **CI/CD & automation**.

---

## 📌 6. Advanced (Power Users)

### 🔹 6.1 Git Aliases with Logic

```ini
[alias]
  cob = checkout -b
  undo = reset --soft HEAD~1
  amend = commit --amend --no-edit
```

### 🔹 6.2 Example

```bash
git cob feature/login
git undo
git amend
```

---

## 📌 7. Best Practices (Enterprise)

✅ Prefer **Git aliases** over shell aliases
✅ Keep aliases **documented** in repo
✅ Avoid redefining standard commands
✅ Share via onboarding docs

---
