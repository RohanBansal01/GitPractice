# GitHub Pull Request (PR) Guide: Templates + Reviews

This guide explains **how to create, review, and approve Pull Requests** the way **experienced engineers do in real teams**. It combines **PR templates** with **review practices**.

> **PR reviews are not about control.**  
> They are about **code quality, shared ownership, and long-term safety**.

<img width="725" height="800" alt="image" src="https://github.com/user-attachments/assets/994fa061-275c-478d-a73d-f08ea783826e" />

---

## 📚 Index

1. [What a Pull Request Really Is](#1-what-a-pull-request-really-is)  
2. [Why PR Reviews Matter](#2-why-pr-reviews-matter)  
3. [When to Open a PR](#3-when-to-open-a-pr)  
4. [Size of a Good PR](#4-size-of-a-good-pr)  
5. [Writing a Good PR Description](#5-writing-a-good-pr-description)  
6. [GitHub PR Templates](#6-github-pr-templates)  
7. [What Reviewers Actually Look For](#7-what-reviewers-actually-look-for)  
8. [Code Review vs Design Review](#8-code-review-vs-design-review)  
9. [How to Review Code (Step-by-Step)](#9-how-to-review-code-step-by-step)  
10. [Commenting Style (How Seniors Comment)](#10-commenting-style-how-seniors-comment)  
11. [Approving a PR](#11-approving-a-pr)  
12. [When to Request Changes](#12-when-to-request-changes)  
13. [Handling Disagreements](#13-handling-disagreements)  
14. [Common PR Mistakes](#14-common-pr-mistakes)  
15. [Do’s and Don’ts (Golden Rules)](#15-dos-and-donts-golden-rules)  
16. [Final PR Review Mental Model](#16-final-pr-review-mental-model)  

<img width="640" height="366" alt="image" src="https://github.com/user-attachments/assets/aa199013-adc5-42b4-8979-e8941ee2b9f5" />

---

## 1. What a Pull Request Really Is

A Pull Request is:

> **A request to merge a set of changes into shared history, after human verification.**

It is **not**:

* Just a formality  
* Just CI passing  
* Just “LGTM”

It’s a **checkpoint before shared truth changes**.

<img width="227" height="222" alt="image" src="https://github.com/user-attachments/assets/9857610f-114c-478a-8421-8c4a0d7d7d0e" />

It’s called a Pull Request because you push to your branch, but request the upstream to pull.

---

## 2. Why PR Reviews Matter
<img width="284" height="177" alt="image" src="https://github.com/user-attachments/assets/2ad398a0-7de8-4958-9455-ba43939e1557" />

PR reviews exist to:

* Catch bugs early  
* Share knowledge across the team  
* Maintain consistency  
* Protect production  
* Reduce “bus factor”

> Code without review is **private code**.  
> Reviewed code becomes **team code**.

---

## 3. When to Open a PR

Open a PR when:

* A logical unit of work is complete  
* Code compiles and tests pass  
* You can explain *why* the change exists

Do **not** wait for perfection.  
Do **not** open half-broken PRs unless marked as **Draft**.

---

## 4. Size of a Good PR

Senior rule:

> **If a PR cannot be reviewed in ~15–30 minutes, it’s too big.**

Good PR size:

* 1 feature  
* 1 fix  
* 1 refactor

Large PRs hide bugs.

---

## 5. Writing a Good PR Description

A good PR description answers:

* **What changed?**  
* **Why was it needed?**  
* **How was it tested?**  
* **Any risks or follow-ups?**

Example template:

```md
### What
Brief summary

### Why
Reason for change

### How
Implementation approach

### Testing
Tests / manual steps
```

> If reviewers need to read code to understand intent — the PR failed.

---

## 6. GitHub PR Templates

Pull Request Templates make PRs **consistent, clear, and easy to review**.

### 6.1 Benefits

* **Consistency:** All PRs follow the same format  
* **Clarity:** Guidance on what info to include  
* **Efficiency:** Checklists reduce back-and-forth  
* **Onboarding:** New developers quickly learn your process

### 6.2 How to Create a Template

1. Add a file `PULL_REQUEST_TEMPLATE.md` under `.github/`  
2. Push to your default branch  
3. GitHub auto-applies it for new PRs

### 6.3 Suggested Template

```md
## Summary
<!-- Short summary "Why are the changes needed"? Include links (Jira, Slack, design docs) -->

## Changes Made
<!-- Describe the specific changes and approach -->

## Checklist
- [ ] Added comments to complex code
- [ ] Updated documentation
- [ ] No new warnings generated
- [ ] Added tests for fixes/features
- [ ] Dependent changes merged downstream

<details>
<summary>Optional Sections</summary>

## Screenshots
<!-- Visual changes if applicable -->

## Related Issues
<!-- Link issues or bugs addressed -->

## Testing Instructions
<!-- How to test changes -->

## Special Notes for Reviewer
<!-- Any specific instructions or considerations -->

</details>
```

---

## 7. What Reviewers Actually Look For

Senior reviewers check:

* Correctness  
* Edge cases  
* Readability & naming  
* Architecture fit  
* Tests  
* Impact on existing code

They **do not** nitpick style endlessly.

---

## 8. Code Review vs Design Review

**Code Review**:

* Is this code correct?  
* Is it readable?  
* Is it safe?

**Design Review**:

* Does this belong here?  
* Is this the right abstraction?  
* Will this scale?

> Mix them carefully—call out design concerns explicitly.

---

## 9. How to Review Code (Step-by-Step)

1. Read PR description  
2. Understand intent  
3. Review structure first  
4. Review logic next  
5. Review edge cases  
6. Review tests last

> Never start line-by-line without context.

---

## 10. Commenting Style (How Seniors Comment)

Good comments are:

* Clear  
* Calm  
* Specific  
* Actionable

✅ “This may fail when X is null — can we guard it?”  
❌ “This is wrong.”

---

## 11. Approving a PR

Approve when:

* Code does what it claims  
* Risks are understood  
* Trade-offs are acceptable

> Approval does **not** mean perfect.  
> It means **safe enough to ship**.

---

## 12. When to Request Changes

Request changes if:

* Correctness bug exists  
* Security issue exists  
* Design violation  
* Missing tests

> Be explicit about **blocking vs non-blocking** feedback.

---

## 13. Handling Disagreements

Senior behavior:

* Ask *why*  
* Provide reasoning  
* Prefer data over opinion  
* Escalate design decisions early

> Never argue style endlessly.

---

## 14. Common PR Mistakes

❌ Huge PRs  
❌ No description  
❌ Mixing refactor + feature  
❌ Ignoring reviewer feedback  
❌ Ego-driven discussions  
❌ Approving without understanding

---

## 15. Do’s and Don’ts (Golden Rules)

### 15.1 ✅ DO

* Keep PRs small  
* Explain intent clearly  
* Review others’ PRs seriously  
* Be kind but firm  
* Treat reviews as collaboration

### 15.2 ❌ DON’T

* Take feedback personally  
* Rubber-stamp approvals  
* Rewrite someone’s code without explanation  
* Block PRs over personal preference  
* Ignore CI failures

---

## 16. Final PR Review Mental Model

<img width="275" height="183" alt="image" src="https://github.com/user-attachments/assets/08de94ff-42b9-44f1-9024-45df60f27628" />

> **PRs are conversations, not gatekeeping.**  
> Reviews protect the codebase, not egos.  
> Shared code means shared responsibility.

> A strong PR culture creates **strong teams**.
