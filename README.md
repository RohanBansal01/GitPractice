# GitPractice 📚

[![License: MIT](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![GitHub Repo](https://img.shields.io/badge/GitHub-Repo-black?logo=github)](https://github.com/YourUsername/GitPractice)

**GitPractice** is a hands-on repository for learning, practicing, and mastering **Git and GitHub**, from fundamentals to advanced real-world workflows.

This repository focuses on **how Git actually works**, not just memorizing commands.

<img width="731" height="500" alt="image" src="https://github.com/user-attachments/assets/4ef88315-a424-4b72-afd8-a03ea133ffda" />

---

## 📖 Table of Contents

- [1. Project Overview](#1-project-overview)
- [2. Repository Structure](#2-repository-structure)
- [3. Engineering Review and Delivery Standards](#3-engineering-review-and-delivery-standards)
  - [3.1 Engineering Docs and Guides](#31-engineering-docs-and-guides)
- [4. Common Confusion: Git vs GitHub vs GitLab](#4-common-confusion-git-vs-github-vs-gitlab)
- [5. Installation and Setup](#5-installation-and-setup)
- [6. How to Use This Repository](#6-how-to-use-this-repository)
- [7. Features](#7-features)
- [8. Contributing](#8-contributing)
- [9. License](#9-license)
- [10. Maintainer](#10-maintainer)

---

## 1. Project Overview

This repository helps you:

- Understand Git fundamentals (commits, branches, merges)
- Practice common Git commands and workflows
- Learn advanced concepts like rebasing, stashing, and cherry-picking
- Build confidence with Git internals and disaster recovery
- Follow best practices for collaborative, team-based Git usage

---

## 2. Repository Structure

```bash
GitPractice/
│
├── docs/
│   ├── pull-request-guidelines.md
│   ├── engineering-vocabulary.md
│   ├── engineering-foundations.md
│   ├── git-github-shortcuts.md
│   ├── git-tools-industry-guide.md
│   └── github-markdown.md
│
├── gitpractice-roadmap/
├── basic-commands/
├── git-workflow/
├── git-internals/
├── branching/
├── rebasing/
├── stashing/
├── conflicts/
├── disaster-recovery/
│
├── resources/
│   ├── README.md
│   ├── interactive-platforms.md
│   ├── official-documentation.md
│   ├── youtube-playlists.md
│   ├── git-tools.md
│   └── cheat-sheets.md
│
├── README.md
└── LICENSE
````

> Folder names are intentionally **lowercase and hyphenated** for consistency and cross-platform compatibility.

---

## 3. Engineering Review and Delivery Standards

This section explains how pull requests, code reviews, and engineering workflows are handled in professional teams.

---

### 3.1 Engineering Docs and Guides

These documents reflect how Git, GitHub, and engineering practices are handled in real-world professional teams.

#### 📄 Pull Request Guidelines

→ [docs/pull-request-guidelines.md](docs/pull-request-guidelines.md)

How to create high-quality pull requests, conduct code reviews, handle approvals, and follow professional do’s and don’ts.

#### 🧠 Engineering Vocabulary

→ [docs/engineering-vocabulary.md](docs/engineering-vocabulary.md)

Common industry terms every software engineer should know when working with Git, GitHub, code reviews, and production systems.

#### 🏗 Engineering Foundations

→ [docs/engineering-foundations.md](docs/engineering-foundations.md)

Core engineering principles including ownership, production mindset, incident handling, rollback strategies, and trade-off analysis.

#### ⚡ Git and GitHub Shortcuts

→ [docs/git-github-shortcuts.md](docs/git-github-shortcuts.md)

Common Git and GitHub shortcuts used in real-world projects, terminals, and daily developer workflows.

#### 🛠 Git Tools – Industry Guide

→ [docs/git-tools-industry-guide.md](docs/git-tools-industry-guide.md)

A practical comparison of Git Bash, GitHub CLI, terminal tools, and what professionals use in day-to-day development.

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

> Understanding PR reviews and engineering foundations is mandatory for real-world Git usage.

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/d4ffabc6-9b5f-499d-9e86-853baa9e9b7e" />

---

## 4. Common Confusion: Git vs GitHub vs GitLab

Many people confuse **Git**, **GitHub**, and **GitLab**.
This repository focuses primarily on **Git**, while demonstrating how it is used with platforms like GitHub and GitLab.

| Tool       | What it is                                          |
| ---------- | --------------------------------------------------- |
| **Git**    | A distributed version control system (runs locally) |
| **GitHub** | A hosting and collaboration platform for Git        |
| **GitLab** | A DevOps platform built around Git                  |

> Git manages history.
> GitHub manages collaboration.
> GitLab manages the software lifecycle.

If you understand Git deeply, switching between GitHub, GitLab, or any future tool becomes easy.

---

## 5. Installation and Setup

1. Clone the repository:

```bash
git clone https://github.com/YourUsername/GitPractice.git
cd GitPractice
```

2. Navigate into any folder and follow the examples or README files inside.

---

## 6. How to Use This Repository

This repository is structured to help you learn Git step by step:

1. Each folder focuses on a single Git concept (example: `branching/`, `rebasing/`, `disaster-recovery/`)
2. Start by following the GitPractice roadmap:

   * [GitPractice Roadmap](gitpractice-roadmap.md)
3. Run Git commands locally to experiment with the examples and exercises
4. Modify files, commit changes, and break things on purpose, then recover them

> Tip: Don’t just memorize commands — understand what Git is doing behind the scenes.

You can also explore additional learning material here:

* [resources/README.md](resources/README.md)

---

## 7. Features

* Beginner to intermediate Git coverage
* Practical real-world workflows (not academic theory)
* Git internals explained in a developer-friendly way
* Disaster recovery scenarios to build confidence
* Suitable for solo learning and team preparation

---

## 8. Contributing

Contributions are welcome.

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

## 10. Maintainer

**Maintained by [Rohan Bansal](https://github.com/RohanBansal01)**

---

Git is safest when you understand how to recover, not just how to commit.
