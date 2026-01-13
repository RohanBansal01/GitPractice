# Engineering Foundations – GitHub

This document explains the **non-negotiable engineering fundamentals** that go beyond Git commands and PR mechanics.

These are the concepts that define **how senior engineers think, communicate, and operate** in real production systems.

> Tools get you hired.  
> Judgment keeps systems alive.

---

## 📚 Index

1. [What This Guide Is (And Is Not)](#1-what-this-guide-is-and-is-not)  
2. [Ownership in Engineering](#2-ownership-in-engineering)  
3. [Code Ownership](#3-code-ownership)  
4. [Service Ownership](#4-service-ownership)  
5. [On-Call Responsibility](#5-on-call-responsibility)  
6. [Escalation Paths](#6-escalation-paths)  
7. [What “Production” Really Means](#7-what-production-really-means)  
8. [Environments: Dev, Staging, Prod](#8-environments-dev-staging-prod)  
9. [Rollbacks and Blast Radius](#9-rollbacks-and-blast-radius)  
10. [Change Management Concepts](#10-change-management-concepts)  
11. [Safe Change Strategies](#11-safe-change-strategies)  
12. [Incident Vocabulary](#12-incident-vocabulary)  
13. [Blameless Postmortems](#13-blameless-postmortems)  
14. [Engineering Judgment](#14-engineering-judgment)  
15. [Final Senior Mental Model](#15-final-senior-mental-model)  

---

## 1. What This Guide Is (And Is Not)

This guide is about **operating software in the real world**.

It is **not**:

* A Git tutorial  
* A syntax guide  
* A framework comparison  

It **is**:

* How engineers protect systems  
* How teams avoid disasters  
* How seniors make decisions under pressure

---

## 2. Ownership in Engineering

Ownership is the foundation of professionalism.

Senior rule:

> If you touch it, you take responsibility for it.

Ownership applies to:

* Code  
* Services  
* Deployments  
* Failures

---

## 3. Code Ownership

**Code ownership** defines who is responsible for specific parts of the codebase.

Responsibilities include:

* Reviewing PRs  
* Maintaining quality  
* Understanding impact of changes

Ownership does **not** mean:

* Writing all the code  
* Blocking others unnecessarily

It means **accountability**, not control.

---

## 4. Service Ownership

A **service owner** is responsible for the service end-to-end:

* Availability  
* Performance  
* Data correctness  
* Incident response

Senior mindset:

> “This service failing is my problem — regardless of who wrote the code.”

---

## 5. On-Call Responsibility

On-call means:

* You respond when systems break  
* You prioritize recovery over blame  
* You act calmly under pressure

Being on-call changes how seniors write code:

* Safer defaults  
* Better logging  
* Easier rollbacks

---

## 6. Escalation Paths

Escalation is not failure.

It is:

* Asking for help early  
* Reducing downtime  
* Protecting users

Senior behavior:

> Escalate problems, not emotions.

---

## 7. What “Production” Really Means

**Production** is where:

* Real users exist  
* Real data lives  
* Real money flows

Senior rule:

> Production changes are business decisions, not just technical ones.

---

## 8. Environments: Dev, Staging, Prod

Typical environments:

* **Development** → fast iteration  
* **Staging** → production-like testing  
* **Production** → real users

Senior expectation:

* Bugs are expected in dev  
* Bugs are expensive in prod

---

## 9. Rollbacks and Blast Radius

Every change must answer:

* How do we undo this?  
* Who is affected if this fails?

Key terms:

* **Rollback** → revert safely  
* **Blast radius** → scope of impact

Smaller blast radius = safer system.

---

## 10. Change Management Concepts

Industry-standard terms you must know:

* Backward compatible  
* Breaking change  
* Hotfix  
* Patch / Minor / Major release

Senior rule:

> Most production pain comes from unmanaged change.

---

## 11. Safe Change Strategies

Common safety mechanisms:

* Feature flags  
* Canary releases  
* Rolling deployments  
* Gradual rollouts

Seniors prefer **slow and reversible** over fast and risky.

---

## 12. Incident Vocabulary

When things break, teams use precise language:

* Incident  
* Outage  
* Degradation  
* Root cause  
* Mitigation

Clear language prevents panic and confusion.

---

## 13. Blameless Postmortems

After incidents, teams write **postmortems**.

Purpose:

* Understand what failed  
* Improve systems  
* Prevent recurrence

Not for:

* Blaming individuals  
* Punishing mistakes

Senior belief:

> Systems fail. People learn.

---

## 14. Engineering Judgment

Judgment is choosing the **right trade-off**, not the perfect solution.

Common balances:

* Speed vs safety  
* Clean vs shipped  
* Ideal vs practical

Senior phrases:

* “This is an acceptable trade-off”  
* “Let’s not block on this”  
* “We’ll follow up later”

---

## 15. Final Senior Mental Model

> **Engineering is risk management.  
> Git tracks changes.  
> PRs verify intent.  
> Ownership protects systems.  
> Judgment keeps everything running.**

This is the layer that turns developers into engineers.
