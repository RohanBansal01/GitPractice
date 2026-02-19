# Ticketing Systems  (Industry Workflow Guide)

## 1. What is a Ticket?

A **ticket** is a tracked work item used in software teams to manage development and support work in a structured way.

A ticket is the official record of:

1.1 What needs to be done  
1.2 Why it is needed  
1.3 Who is responsible  
1.4 Current progress/status  
1.5 Priority and deadlines  
1.6 Discussions, approvals, and audit history  
1.7 Related code changes, PRs, and deployments  

In professional teams, tickets act as the **single source of truth** for work.




<img width="224" height="225" alt="image" src="https://github.com/user-attachments/assets/c27c1e91-9729-4eae-aaa1-75e2319f0294" />



---

## 2. Why Companies Use Ticketing Systems

Ticketing systems exist because modern projects involve multiple developers, QA engineers, business stakeholders, and production environments.

Ticketing ensures:

2.1 Clear tracking of responsibilities  
2.2 Work prioritization (what is important vs what can wait)  
2.3 Progress visibility for managers and teams  
2.4 Proper QA and testing validation  
2.5 Controlled releases and deployments  
2.6 Audit trail (who changed what, when, and why)  
2.7 Reduced confusion in team communication  

Without tickets, software development becomes unstructured and difficult to scale.

---

## 3. Common Types of Tickets (Industry Standard)

Different companies use different naming conventions, but these are the most common ticket types.

### 3.1 Bug

A **bug** ticket represents an issue where the system is not working as expected.

Examples:

3.1.1 Login failing for valid credentials  
3.1.2 Incorrect invoice total calculation  
3.1.3 API returning 500 error  

Bug tickets usually include:

3.1.4 Steps to reproduce  
3.1.5 Expected behavior  
3.1.6 Actual behavior  
3.1.7 Logs/screenshots  
3.1.8 Environment details (Dev/QA/Prod)

---

### 3.2 Task

A **task** is a small unit of technical work.

Examples:

3.2.1 Add a database column  
3.2.2 Add validation in service layer  
3.2.3 Update configuration file  

Tasks are usually smaller than features.

---

### 3.3 Story (User Story)

A **story** describes a feature requirement from the user/business perspective.

Example:

3.3.1 "As a user, I want to reset my password so I can regain access."

Stories normally include:

3.3.2 Acceptance criteria  
3.3.3 Business rules  
3.3.4 UI/API requirements  
3.3.5 Testing expectations  

---

### 3.4 Epic

An **epic** is a large requirement that contains multiple stories/tasks.

Example:

3.4.1 "Student Management Module"  

This epic may contain:

3.4.2 Add student feature  
3.4.3 Update student feature  
3.4.4 Student search feature  
3.4.5 Student reports feature  

Epic = group of related deliverables.

---

### 3.5 Sub-task

A **sub-task** is a breakdown of a story/task into smaller parts.

Example:

3.5.1 Story: Create Student Registration Feature  

Subtasks:

3.5.2 Create UI screen  
3.5.3 Create backend service  
3.5.4 Add entity model changes  
3.5.5 Add unit test cases  

---

### 3.6 Improvement / Enhancement

Used when something works but needs improvement.

Examples:

3.6.1 Improve query performance  
3.6.2 Refactor legacy code  
3.6.3 Improve error handling and logs  

---

### 3.7 Incident / Support Ticket

Used for production issues or urgent support work.

Examples:

3.7.1 Production system down  
3.7.2 Customer cannot place order  
3.7.3 Data mismatch in reports  

Incident tickets are usually treated as highest priority.

---

## 4. Ticket Priority vs Severity

### 4.1 Priority

Priority defines how urgent the ticket is.

Common levels:

4.1.1 Critical / P0  
4.1.2 High / P1  
4.1.3 Medium / P2  
4.1.4 Low / P3  

---

### 4.2 Severity (Mostly for Bugs)

Severity defines the impact level of the issue.

Common severity types:

4.2.1 Blocker  
4.2.2 Critical  
4.2.3 Major  
4.2.4 Minor  
4.2.5 Trivial  

---

## 5. Ticket Lifecycle (Typical Workflow)

Most professional teams follow a workflow like:

5.1 Open / Created  
5.2 Assigned  
5.3 In Progress  
5.4 In Review  
5.5 QA / Testing  
5.6 Ready for Release  
5.7 Done / Closed  

Additional common statuses:

5.8 Blocked  
5.9 Reopened  
5.10 On Hold  

---

## 6. What is a Ticketing System?

A **ticketing system** is the platform used to manage, track, and organize tickets.

It provides features such as:

6.1 Ticket creation and assignment  
6.2 Status tracking and workflow management  
6.3 Sprint planning and backlog management  
6.4 Commenting and collaboration  
6.5 Reporting dashboards  
6.6 Release planning  
6.7 Linking tickets to code and deployments  

---

## 7. Common Ticketing Platforms Used in Industry

### 7.1 JIRA

JIRA is the most widely used ticketing tool in software companies.

It supports:

7.1.1 Agile workflows (Scrum, Kanban)  
7.1.2 Stories, epics, tasks, bugs  
7.1.3 Sprint and release management  
7.1.4 GitHub/GitLab integration  


<img width="599" height="587" alt="image" src="https://github.com/user-attachments/assets/b45845a1-0b0c-425e-ad6c-d1905d3aebac" />

---

### 7.2 Azure DevOps Boards

Often used in Microsoft-based ecosystems.

Supports:

7.2.1 Work items and boards  
7.2.2 Repos and pipelines integration  
7.2.3 End-to-end DevOps tracking  

---

### 7.3 ServiceNow

Common in large enterprises for IT support and incident management.

Used mainly for:

7.3.1 Incidents  
7.3.2 Change requests  
7.3.3 Production support workflows  

---

### 7.4 GitHub Issues

Lightweight ticketing system integrated directly into GitHub.

Best for:

7.4.1 Open source projects  
7.4.2 Small teams and startups  

---

### 7.5 GitLab Issues

Similar to GitHub Issues, integrated with GitLab CI/CD.

---

### 7.6 Trello / Asana / Monday.com

More project-management oriented, often used for non-engineering teams.

---

## 8. Relationship Between Tickets and Git Platforms (GitHub/GitLab/Bitbucket)

Tickets define **what work is required**.  
Git platforms track **how the work was implemented**.

Standard workflow:

8.1 Ticket is created in a ticketing system  
8.2 Developer creates a branch for that ticket  
8.3 Developer commits code changes  
8.4 Developer pushes branch to remote repository  
8.5 Developer creates a PR/MR for review  
8.6 Code is reviewed and approved  
8.7 PR/MR is merged into main branch  
8.8 QA validates changes  
8.9 Ticket is closed and included in release  

This is the normal software engineering delivery pipeline.

---

## 9. Branching Strategy (Ticket-Based Development)

In companies, developers do not directly push code into `main/master`.

Instead:

9.1 One ticket = one branch  
9.2 One ticket = one PR/MR  
9.3 One ticket = one tracked change set  

Common branch naming conventions:

9.4 `feature/PROJECT-101-add-student-api`  
9.5 `bugfix/PROJECT-202-fix-login-error`  
9.6 `hotfix/PROJECT-999-prod-crash-fix`  
9.7 `refactor/PROJECT-333-cleanup-student-service`  

Branch naming should always include the ticket ID.

---

## 10. Commit Message Standards (Professional Style)

Commit messages should reference the ticket number.

Bad examples:

10.1 fixed bug  
10.2 final commit  
10.3 update  

Good examples:

10.4 PROJECT-101 Added create student service  
10.5 PROJECT-101 Added validation for email uniqueness  
10.6 PROJECT-101 Added unit tests for student creation  

This helps track code history during audits and debugging.

---

## 11. What is a PR (Pull Request) / MR (Merge Request)?

A PR (GitHub/Bitbucket) or MR (GitLab) is the formal request to merge your changes into the main branch.

A PR is used for:

11.1 Code review  
11.2 Quality checks  
11.3 Approval tracking  
11.4 Automated testing verification  
11.5 Safe merging into shared codebase  

In professional teams, PR is mandatory.

---

## 12. Why PR Review is Mandatory in Real Projects

PR review prevents:

12.1 Bugs reaching production  
12.2 Bad coding practices  
12.3 Security issues  
12.4 Performance regressions  
12.5 Unreviewed database changes  
12.6 Unnecessary complexity  

PR is the main quality gate before code becomes official.

---

## 13. PR Description Format (Industry Standard)

A good PR should contain:

13.1 Ticket reference  
13.2 Summary of changes  
13.3 Technical approach  
13.4 Testing done  
13.5 Screenshots (if UI)  
13.6 Risks and deployment notes  

Example PR template:

13.7 Ticket: PROJECT-101  
13.8 Summary: Added student creation service and validations  
13.9 Changes:
     - Added createStudent service  
     - Added validation for email/phone  
     - Updated service configuration  
13.10 Testing:
     - Verified locally  
     - Tested DB insert/rollback  
     - Unit tests executed successfully  

---

## 14. Ticket to PR Linking (Professional Practice)

Most teams enforce a strict mapping:

14.1 Ticket ID must appear in branch name  
14.2 Ticket ID must appear in commit messages  
14.3 Ticket ID must appear in PR title or description  
14.4 PR must link back to ticket automatically or manually  

This creates traceability between requirements and code.

---

## 15. Release and Deployment Mapping (Tickets in Production Delivery)

A release usually contains multiple tickets.

Typical flow:

15.1 Tickets completed  
15.2 PRs merged  
15.3 QA testing completed  
15.4 Release candidate build generated  
15.5 Deployment to staging/UAT  
15.6 Final deployment to production  

Release notes are usually based on ticket IDs.

Example:

15.7 Release v1.4 includes PROJECT-101, PROJECT-115, PROJECT-120  

---

## 16. Agile Concepts Related to Tickets (Basic Understanding)

### 16.1 Sprint

A sprint is a fixed time window (usually 1 or 2 weeks) where selected tickets must be completed.

---

### 16.2 Backlog

Backlog is the list of all pending tickets not yet scheduled.

---

### 16.3 Kanban Board

Kanban is a continuous workflow board where tickets move through stages like:

16.3.1 To Do  
16.3.2 In Progress  
16.3.3 Review  
16.3.4 QA  
16.3.5 Done  

---

## 17. Common Beginner Mistakes (Must Avoid)

Most junior developers fail in professional teams due to these mistakes:

17.1 Working without a ticket reference  
17.2 Mixing multiple tickets in one PR  
17.3 Writing unclear commit messages  
17.4 Raising PR without testing  
17.5 Ignoring review comments  
17.6 Marking ticket as Done without QA confirmation  
17.7 Not updating ticket status properly  
17.8 Breaking branch naming conventions  

---

## 18. Senior Engineer Standard Expectations

A professional developer is expected to:

18.1 Understand ticket requirements clearly  
18.2 Follow branch naming conventions  
18.3 Write clean commits with ticket reference  
18.4 Raise high-quality PRs  
18.5 Respond to review comments professionally  
18.6 Keep changes minimal and ticket-focused  
18.7 Ensure proper testing before merge  
18.8 Maintain traceability (ticket → branch → commits → PR → release)  

---

## 19. Summary (Professional Ticket-to-Code Workflow)


<img width="491" height="491" alt="image" src="https://github.com/user-attachments/assets/d41bbeb9-4c43-47d3-ad89-22d76ae0ff39" />



The standard company workflow is:

19.1 Ticket created in ticketing system  
19.2 Developer creates branch using ticket ID  
19.3 Developer implements changes and commits with ticket ID  
19.4 Developer pushes changes to Git platform  
19.5 Developer raises PR/MR  
19.6 Reviewers approve after code review  
19.7 PR/MR is merged  
19.8 QA tests the build  
19.9 Ticket marked Done  
19.10 Ticket included in release deployment  

This is the foundation of how real-world engineering teams manage work.
