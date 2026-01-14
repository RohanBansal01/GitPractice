# GitPractice 📚

[![License: MIT](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![GitHub Repo](https://img.shields.io/badge/GitHub-Repo-black?logo=github)](https://github.com/YourUsername/GitPractice)

**GitPractice** is a hands-on repository for learning, practicing, and mastering **Git and GitHub**, from fundamentals to advanced, real-world workflows.

This repo focuses on **how Git actually works**, not just commands. <img width="731" height="500" alt="image" src="https://github.com/user-attachments/assets/4ef88315-a424-4b72-afd8-a03ea133ffda" />

---

## 📖 Table of Contents

* [1. Project Overview](#1-project-overview)
* [2. Repository Structure](#2-repository-structure)
* [3. Engineering Review & Delivery Standards](#3-engineering-review--delivery-standards)

  * [3.1 Engineering Docs & Guides](#31-engineering-docs--guides)
* [4. Common Confusion: Git vs GitHub vs GitLab](#4-common-confusion-git-vs-github-vs-gitlab)
* [5. Installation & Setup](#5-installation--setup)
* [6. How to Use This Repository](#6-how-to-use-this-repository)
* [7. Features](#7-features)
* [8. Contributing](#8-contributing)
* [9. License](#9-license)

---

## 1. Project Overview

This repository helps you:

* Understand Git fundamentals (commits, branches, merges)
* Practice common Git commands and workflows
* Learn advanced concepts like rebasing, stashing, and cherry-picking
* Build confidence with Git internals and disaster recovery
* Follow best practices for collaborative, team-based Git usage

---

## 2. Repository Structure

```
GitPractice/
│
├── docs/
│   ├── pull-request-guidelines.md       # PR rules &  workflow
│   ├── engineering-vocabulary.md        # Industry terms / Git vocabulary
│   ├── engineering-foundations.md       # Ownership, production mindset, incident handling, etc.
│   ├── git-github-shortcuts.md          # Git & GitHub shortcuts
│   ├── git-tools-industry-guide.md      # Git tools comparison (CLI, Bash, etc.)
│   └── github-markdown.md               # GitHub Markdown standards
├── gitpractice-roadmap/  # Roadmap for how to follow this repo
├── basic-commands/       # Core Git commands and fundamentals
├── git-workflow/         # How Git workflows operate in real projects
├── git-internals/        # How Git works internally (objects, refs, HEAD)
├── branching/            # Branch creation, merging strategies, workflows
├── rebasing/             # Rebase examples and exercises
├── stashing/             # Git stash use cases and examples
├── conflicts/            # Merge conflict handling
├── disaster-recovery/    # Recovering from Git mistakes and failures
├── README.md             # Project documentation
└── LICENSE               # MIT License
```

> Folder names are intentionally **lowercase and hyphenated** for consistency and cross-platform compatibility.

---

## 3. Engineering Review & Delivery Standards

This section explains how pull requests, code reviews, and engineering workflows are handled in professional teams.

---

### 3.1 Engineering Docs & Guides

These documents reflect **how Git, GitHub, and engineering practices are actually handled in real-world professional teams**.

#### 📄 Pull Request Guidelines
→ [docs/pull-request-guidelines.md](docs/pull-request-guidelines.md)

How to create high-quality pull requests, conduct code reviews, handle approvals, and follow professional do’s & don’ts.

#### 🧠 Engineering Vocabulary
→ [docs/engineering-vocabulary.md](docs/engineering-vocabulary.md)

Common industry terms every software engineer should know when working with Git, GitHub, code reviews, and production systems.

#### 🏗 Engineering Foundations
→ [docs/engineering-foundations.md](docs/engineering-foundations.md)

Core engineering principles including ownership, production mindset, incident handling, rollback strategies, and trade-off analysis.

#### ⚡ Git & GitHub Shortcuts
→ [docs/git-github-shortcuts.md](docs/git-github-shortcuts.md)

Common Git and GitHub shortcuts used in real-world projects, terminals, and daily developer workflows.

#### 🛠 Git Tools – Industry Guide
→ [docs/git-tools-industry-guide.md](docs/git-tools-industry-guide.md)

A practical comparison of Git Bash, GitHub CLI, terminal tools, and what professionals actually use in day-to-day development.

#### 📝 GitHub Markdown Guide
→ [docs/github-markdown.md](docs/github-markdown.md)

Industry-grade GitHub Markdown standards for READMEs, documentation, pull requests, and issues.

---

These documents explain:

* How PR reviews work in teams
* What reviewers expect
* How to give and receive feedback professionally
* How to think like a senior engineer in real-world projects
* How to handle incidents, rollbacks, and production issues

> Understanding PR reviews and engineering foundations is **mandatory** for real-world Git usage.

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/d4ffabc6-9b5f-499d-9e86-853baa9e9b7e" />

---

## 4. Common Confusion: Git vs GitHub vs GitLab

Many people confuse **Git**, **GitHub**, and **GitLab**.
This repository focuses primarily on **Git**, while demonstrating how it is used with platforms like GitHub and GitLab.

| Tool       | What it is                                          |
| ---------- | --------------------------------------------------- |
| **Git**    | A distributed version control system (runs locally) |
| **GitHub** | A hosting & collaboration platform for Git          |
| **GitLab** | A DevOps platform built around Git                  |

> **Git manages history.
> GitHub manages collaboration.
> GitLab manages the software lifecycle.**

If you understand **Git deeply**, switching between GitHub, GitLab, or any future tool becomes trivial.

---

## 5. Installation & Setup

1. Clone the repository:

```bash
git clone https://github.com/YourUsername/GitPractice.git
cd GitPractice
```

2. Navigate into any folder and follow the examples or README files inside.

---

## 6. How to Use This Repository

This repository is structured to help you **learn Git step by step**:

1. Each folder focuses on a **single Git concept** (e.g., `branching/`, `rebasing/`, `disaster-recovery/`)
2. Start by following the **GitPractice roadmap** ([GitPractice Roadmap](gitpractice-roadmap.md)) to know **what to practice at each level**
3. Run Git commands locally to experiment with the examples and exercises
4. Modify files, commit changes, and **break things on purpose — then recover them** 💪

> **Tip:** Don’t just memorize commands — understand **what Git is doing behind the scenes**.

---

## 7. Features

* Beginner to intermediate Git coverage
* Practical, real-world workflows (not academic theory)
* Git internals explained in a developer-friendly way
* Disaster recovery scenarios to build confidence
* Suitable for solo learning and team preparation

---

## 8. Contributing

Contributions are welcome!

1. Fork the repository
2. Create a new branch:

   ```bash
   git checkout -b feature-name
   ```
3. Make your changes and commit:

   ```bash
   git commit -m "Add feature"
   ```
4. Push your branch:

   ```bash
   git push origin feature-name
   ```
5. Open a Pull Request

---

## 9. License

This project is licensed under the **MIT License**.
See the [LICENSE](LICENSE) file for details.

---

Git is safest when you understand **how to recover**, not just how to commit.

---

