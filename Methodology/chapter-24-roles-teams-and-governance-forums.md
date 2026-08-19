<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 23: Forward Deployed Outcome Engineering](chapter-23-forward-deployed-outcome-engineering.md) · [Contents](../README.md) · [Next: Chapter 25: Enterprise Intelligence Platform →](chapter-25-enterprise-intelligence-platform.md)

# Chapter 24: Roles, Teams and Governance Forums

# Roles, Teams and Governance Forums

> **CHAPTER PURPOSE** Specify pod roles, enterprise counterparts, service ownership, separation of duties and the forums required to make timely evidence-based decisions.

## Background and context

[Chapter 23](chapter-23-forward-deployed-outcome-engineering.md) described a pod as a small, embedded team working close to real operational work. That only holds if every pod role has a named enterprise counterpart, and the pod's findings reach people with authority to act. This chapter maps pod-level roles onto the enterprise accountability structure, then defines the forums where evidence turns into decisions.

[Chapter 25 — Enterprise Intelligence Platform](chapter-25-enterprise-intelligence-platform.md) depends heavily on this chapter: platform investment, productization approvals and reuse targets are governed through the forums defined here, not decided unilaterally. [Operations and Observability Architecture](../architecture/perspective-09-operations-and-observability-architecture.md) is explicit that its rollup dashboards and incident classification feed these forums — without that view, a forum just reacts to whatever gets escalated verbally.

Two companion documents name responsibilities this chapter's role table only summarizes. [Agent Architecture](../architecture/perspective-02-agent-architecture.md) requires every production agent to carry a named accountable owner — a commitment the Business Outcome Owner and Platform Product Owner roles exist to satisfy. [Security and Trust Architecture](../architecture/perspective-08-security-and-trust-architecture.md) depends on permission and revocation authority being pre-assigned before an incident forces the question — the job of the Operations Owner and Independent Assurance roles below.

## Role model

The roles below sit above any single pod: enterprise positions a pod's local roles report into, escalate to, or draw funding from. Reading down the table traces a decision's path, from strategic sponsorship to the independent check that keeps the structure honest. For these roles combined with Chapter 23's pod-level roles and a default RACI for recurring decisions, see the [Master Glossary and Roles Roster](../references/master-glossary-and-roles-roster.md).

| **Role**                         | **Accountable for**                                                |
|-----------------------------------|----------------------------------------------------------------------|
| Executive Sponsor                | Strategic priority, funding and cross-functional resolution.       |
| Business Outcome Owner           | Outcome baseline, target, process authority and value realization. |
| Product / Service Owner          | Scope, release, service health, backlog and lifecycle.             |
| FDOE Pod Lead                    | Integrated discovery, engineering, activation and learning.        |
| Platform Product Owner           | Shared capability roadmap, service levels and adoption.            |
| Data / Knowledge Owner           | Authority, quality, access, freshness and lineage.                 |
| Model / AI Steward               | Model strategy, provider risk, evaluation and version policy.      |
| Security / Privacy / Legal / RAI | Requirements, challenge, advice and acceptance within mandate.     |
| Operations Owner                 | Runbook, support, incidents, capacity, change and recovery.        |
| Independent Assurance            | Objective challenge for high-impact evidence and controls.         |

The Executive Sponsor resolves cross-functional conflicts no single pod or product team can settle alone: competing priorities, contested funding, or a stalemate between functions. The Business Outcome Owner is the enterprise-level expression of the Business Process Owner from Chapter 23, accountable for the outcome baseline and target, and for authority to actually change the business process. This is the principle [Process Architecture](../architecture/perspective-03-process-architecture.md) calls "the process owner is never the agent" — accountability always sits with a named human.

The Product / Service Owner and FDOE Pod Lead carry delivery forward once an outcome is underway: one governs scope, release and service health; the other holds discovery, engineering, activation and learning as one thread. The Platform Product Owner is the role [Chapter 25](chapter-25-enterprise-intelligence-platform.md) depends on most: accountable for the shared capability roadmap, service levels, and adoption.

Three roles keep the system trustworthy under real operating conditions. The Data / Knowledge Owner is accountable for authority, quality, access and lineage of the knowledge domains a system draws on — the anchor for the domain map in [Information and Knowledge Architecture](../architecture/perspective-04-information-and-knowledge-architecture.md). The Model / AI Steward carries model strategy, provider risk and version policy, the counterpart to routing and fallback decisions in [Inference Architecture](../architecture/perspective-05-inference-architecture.md). Security / Privacy / Legal / RAI provides requirements, challenge and advice within a bounded mandate — a defined role, not an arbitrary veto, consistent with [Security and Trust Architecture](../architecture/perspective-08-security-and-trust-architecture.md).

The Operations Owner holds the runbook, support model, incidents, capacity and recovery — the owner behind the kill-switch and containment authority [Operations and Observability Architecture](../architecture/perspective-09-operations-and-observability-architecture.md) requires be pre-assigned, not improvised mid-incident. Independent Assurance closes the loop with objective challenge on high-impact evidence and controls, a check never held by whoever built the thing being assured.

## Governance forums

Roles only produce timely decisions if they meet on a cadence matched to the stakes involved — daily for operational friction, quarterly for portfolio-level commitment.

| **Forum**                      | **Cadence**                  | **Purpose**                                                            |
|-----------------------------------|---------------------------------|----------------------------------------------------------------------------|
| Pod stand-up                   | Daily                        | Blockers, evidence collection, incidents and next vertical slice.      |
| Working demonstration          | Weekly                       | Show live behavior on real cases; accept learning and scope decisions. |
| Outcome review                 | Monthly                       | Assess outcome, adoption, intelligence, risk, service and economics.   |
| Architecture / Risk review     | At gates and material change | Resolve design, authority, control and residual-risk decisions.        |
| Platform productization review | Monthly or quarterly         | Promote repeated components and manage shared-service demand.          |
| Portfolio review               | Quarterly                    | Fund, sequence, continue, scale, reframe or retire initiatives.        |

The daily pod stand-up is the fastest, least formal loop: it surfaces blockers and incidents while cheap to fix, keeping Chapter 23's field loop turning. The weekly working demonstration is where the pod shows actual behavior on real cases, not intended behavior in a status update. The monthly outcome review is the first forum with real portfolio weight, looking across outcome achievement, adoption, intelligence quality, risk, service health and economics, drawing on the rollups [Operations and Observability Architecture](../architecture/perspective-09-operations-and-observability-architecture.md) produces from every production system.

Architecture and risk reviews are convened by event, not calendar — at defined gates or whenever a material change demands a decision. The platform productization review is where Chapter 23's classification discipline pays off: repeated components are promoted, and shared-service demand is actively managed. The quarterly portfolio review is the highest-stakes forum, with authority to fund, sequence, continue, scale, reframe or retire initiatives. It runs at the same cadence as the capability map review in [Business and Capability Architecture](../architecture/perspective-01-business-and-capability-architecture.md): a portfolio decision made without visibility into capability duplication is made half-blind.

## Separation and consolidation

Small organizations will inevitably combine several of these roles in one person, and OASIS does not treat that as a failure condition. But accountability must stay explicit even when the people holding it overlap. A person who builds a control may reasonably self-test it for low-risk work. High-impact systems do not get that latitude: they need independent challenge from someone who did not build the thing being reviewed — precisely why Independent Assurance should not be folded into a delivery role, even in a small organization.

One line does not bend regardless of size: outcome ownership must remain with the business authority capable of changing the process and accepting the consequences. A platform team, a pod, or a vendor can build, operate and even recommend. But the decision to accept an outcome, and its accountability, stays with the business.

---

[← Previous: Chapter 23: Forward Deployed Outcome Engineering](chapter-23-forward-deployed-outcome-engineering.md) · [Contents](../README.md) · [Next: Chapter 25: Enterprise Intelligence Platform →](chapter-25-enterprise-intelligence-platform.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
