# Pull Request (PR) Reviews 

This guide explains **how to create, review, and approve Pull Requests** the way **experienced engineers do in real teams**.

PR reviews are **not about control**.
They are about **code quality, shared ownership, and long-term safety**.

<img width="725" height="800" alt="image" src="https://github.com/user-attachments/assets/6d4e0998-26f0-4c7c-b758-42c72b3443b8" />

---

## 📚 Index

1. What a Pull Request Really Is
2. Why PR Reviews Matter
3. When to Open a PR
4. Size of a Good PR
5. Writing a Good PR Description
6. What Reviewers Actually Look For
7. Code Review vs Design Review
8. How to Review Code (Step-by-Step)
9. Commenting Style (How Seniors Comment)
10. Approving a PR
11. When to Request Changes
12. Handling Disagreements
13. Common PR Mistakes
14. Do’s and Don’ts (Golden Rules)
15. Final PR Review Mental Model

---

## 1️⃣ What a Pull Request Really Is

A Pull Request is:

> **A request to merge a set of changes into shared history, after human verification.**

It is **not**:

* Just a formality
* Just CI passing
* Just “LGTM”

It’s a **checkpoint before shared truth changes**.

---

## 2️⃣ Why PR Reviews Matter

PR reviews exist to:

* Catch bugs early
* Share knowledge across the team
* Maintain consistency
* Protect production
* Reduce “bus factor”

> Code without review is **private code**.
> Reviewed code becomes **team code**.

---

## 3️⃣ When to Open a PR

Open a PR when:

* A logical unit of work is complete
* Code compiles and tests pass
* You can explain *why* the change exists

Do **not** wait for perfection.
Do **not** open half-broken PRs unless marked as **Draft**.

---

## 4️⃣ Size of a Good PR

Senior rule:

> **If a PR cannot be reviewed in ~15–30 minutes, it’s too big.**

Good PR size:

* 1 feature
* 1 fix
* 1 refactor

Large PRs hide bugs.

---

## 5️⃣ Writing a Good PR Description

A good PR description answers:

* **What changed?**
* **Why was it needed?**
* **How was it tested?**
* **Any risks or follow-ups?**

Template:

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

If reviewers need to read code to understand intent — the PR failed.

---

## 6️⃣ What Reviewers Actually Look For

Senior reviewers check:

* Correctness
* Edge cases
* Readability
* Naming
* Architecture fit
* Tests
* Impact on existing code

They do **not** nitpick style endlessly.

---

## 7️⃣ Code Review vs Design Review

**Code Review**:

* Is this code correct?
* Is it readable?
* Is it safe?

**Design Review**:

* Does this belong here?
* Is this the right abstraction?
* Will this scale?

Mixing them causes frustration.
Call out design concerns explicitly.

---

## 8️⃣ How to Review Code (Step-by-Step)

Senior workflow:

1. Read PR description
2. Understand intent
3. Review structure first
4. Review logic next
5. Review edge cases
6. Review tests last

Never start line-by-line without context.

---

## 9️⃣ Commenting Style (How Seniors Comment)

Good comments are:

* Clear
* Calm
* Specific
* Actionable

Examples:

✅ “This may fail when X is null — can we guard it?”
❌ “This is wrong.”

Tone matters. Written words carry weight.

---

## 🔟 Approving a PR

Approve when:

* Code does what it claims
* Risks are understood
* Trade-offs are acceptable

Approval does **not** mean:

* “Perfect”
* “I would write it this way”

It means:

> **Safe enough to ship.**

---

## 1️⃣1️⃣ When to Request Changes

Request changes if:

* There is a correctness bug
* There is a security issue
* There is a design violation
* Tests are missing where required

Be explicit about **blocking vs non-blocking** feedback.

---

## 1️⃣2️⃣ Handling Disagreements

Disagreements are normal.

Senior behavior:

* Ask *why*
* Provide reasoning
* Prefer data over opinion
* Escalate design decisions early

Never argue style endlessly.

---

## 1️⃣3️⃣ Common PR Mistakes

❌ Huge PRs
❌ No description
❌ Mixing refactor + feature
❌ Ignoring reviewer feedback
❌ Ego-driven discussions
❌ Approving without understanding

---

## 1️⃣4️⃣ Do’s and Don’ts (Golden Rules)

### ✅ DO

* Keep PRs small
* Explain intent clearly
* Review others’ PRs seriously
* Be kind but firm
* Treat reviews as collaboration

### ❌ DON’T

* Take feedback personally
* Rubber-stamp approvals
* Rewrite someone’s code without explanation
* Block PRs over personal preference
* Ignore CI failures

---

## 1️⃣5️⃣ Final PR Review Mental Model

> **PRs are conversations, not gatekeeping.
> Reviews protect the codebase, not egos.
> Shared code means shared responsibility.**

A strong PR culture creates **strong teams**.

---

