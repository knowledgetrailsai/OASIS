<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 23: Forward Deployed Outcome Engineering](chapter-23-forward-deployed-outcome-engineering.md) · [Contents](../README.md) · [Next: Chapter 25: Enterprise Intelligence Platform →](chapter-25-enterprise-intelligence-platform.md)

# Chapter 24: Roles, Teams and Governance Forums

# Roles, Teams and Governance Forums

> **CHAPTER PURPOSE** Specify pod roles, enterprise counterparts, service ownership, separation of duties and the forums required to make timely evidence-based decisions.

## Background and context

[Chapter 23](chapter-23-forward-deployed-outcome-engineering.md) described a pod as a small, embedded team working close to real operational work. That description only holds together if every pod role has a named enterprise counterpart it reports into, and if the pod's findings — outcome hypotheses proven or disproven, capabilities ready for productization, risks surfaced under real production load — reach the people with the authority to act on them at the right cadence. This chapter is that connective layer: it takes the pod-level roles from Chapter 23 and maps them onto the enterprise accountability structure, then defines the forums where evidence turns into decisions. Without it, a pod can be technically excellent and still starve for lack of a decision-making venue, or worse, make consequential calls that were never anyone's to make.

The chapter that follows, [Chapter 25 — Enterprise Intelligence Platform](chapter-25-enterprise-intelligence-platform.md), depends heavily on what is defined here: platform investment decisions, productization approvals and reuse targets are governed through the forums this chapter establishes, not decided unilaterally by whichever team happens to be building at the time. The roles and forums here are also the organizational backbone several architecture perspectives assume already exists. [Operations and Observability Architecture](../architecture/perspective-09-operations-and-observability-architecture.md) is explicit that its enterprise rollup dashboards and enterprise incident classification exist to feed the governance forums defined in this chapter — and, in turn, that a governance forum without that rollup view is reduced to reacting to whatever gets escalated verbally rather than seeing the actual state of the portfolio. Read the two chapters together: this one names who sits in the room and how often it meets, that one supplies what they should be looking at when they get there.

Two further companion documents are worth reading alongside this chapter rather than after it, because they name responsibilities this chapter's role table only summarizes. [Agent Architecture](../architecture/perspective-02-agent-architecture.md) requires every production agent to carry a named accountable owner in its enterprise registry — a concrete organizational commitment that this chapter's Business Outcome Owner and Platform Product Owner roles exist to satisfy. [Security and Trust Architecture](../architecture/perspective-08-security-and-trust-architecture.md) similarly depends on permission issuance and revocation authority being pre-assigned to a real person before an incident forces the question — a responsibility that lands with the Operations Owner and Independent Assurance roles defined below, not with whoever happens to be on call.

## Role model

The roles below sit above any single pod: they are the enterprise positions a pod's local roles from Chapter 23 report into, escalate to, or draw funding and mandate from. Reading down the table roughly traces the path a decision travels, from strategic sponsorship down to the independent check that keeps the whole structure honest. For the same roles combined with the pod-level roles from Chapter 23 and the per-agent and per-credential accountability requirements named across the Architecture perspective articles, plus a default RACI for the recurring decisions this methodology names most often, see the [Master Glossary and Roles Roster](../references/master-glossary-and-roles-roster.md).

| **Role**                         | **Accountable for**                                                |
|----------------------------------|--------------------------------------------------------------------|
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

The Executive Sponsor sits above individual initiatives and exists to resolve the cross-functional conflicts that no single pod or product team can settle on its own — competing priorities, contested funding, or a stalemate between two functions that both have a legitimate claim on the same resource. The Business Outcome Owner is the enterprise-level expression of the Business Process Owner introduced in Chapter 23: the person accountable for the outcome baseline, the target it is measured against, and — critically — the authority to actually change the underlying business process, not merely to comment on it. This is the same non-negotiable principle [Process Architecture](../architecture/perspective-03-process-architecture.md) calls "the process owner is never the agent": accountability for a process outcome always sits with a named human, regardless of how many of that process's steps are now agent-executed.

The Product / Service Owner and FDOE Pod Lead carry the delivery engine forward once an outcome is underway — one governing scope, release and the ongoing health of the service, the other holding the pod's integrated work of discovery, engineering, activation and learning together as a single accountable thread rather than a set of disconnected workstreams. Sitting alongside them, the Platform Product Owner is the role [Chapter 25](chapter-25-enterprise-intelligence-platform.md) depends on most directly: the person accountable for the shared capability roadmap, its service levels, and driving adoption of platform components rather than letting every deployment reinvent them.

Three roles exist specifically to keep the system trustworthy under real operating conditions. The Data / Knowledge Owner is accountable for the authority, quality, access and lineage of the knowledge domains a system draws on — the organizational anchor for the domain map defined enterprise-wide in [Information and Knowledge Architecture](../architecture/perspective-04-information-and-knowledge-architecture.md). The Model / AI Steward carries model strategy, provider risk and version policy, the enterprise counterpart to the routing and fallback decisions governed in [Inference Architecture](../architecture/perspective-05-inference-architecture.md). And Security / Privacy / Legal / RAI provides requirements, challenge and advice within a clearly bounded mandate — not a veto exercised arbitrarily, but a defined role with defined authority, consistent with the permission-issuance principles in [Security and Trust Architecture](../architecture/perspective-08-security-and-trust-architecture.md).

Finally, the Operations Owner holds the runbook, support model, incident response, capacity and recovery — the accountable owner behind the kill-switch and containment authority that [Operations and Observability Architecture](../architecture/perspective-09-operations-and-observability-architecture.md) insists must be pre-assigned rather than improvised mid-incident. Independent Assurance closes the loop with objective challenge on high-impact evidence and controls: a check that, by design, is never held by the same person or team that built the thing being assured.

## Governance forums

Roles only produce timely decisions if they meet on a cadence matched to the stakes involved — daily for operational friction, quarterly for portfolio-level commitment, and everything in between scaled to how much damage a delay would cause.

| **Forum**                      | **Cadence**                  | **Purpose**                                                            |
|---------------------------------|-------------------------------|--------------------------------------------------------------------------|
| Pod stand-up                   | Daily                        | Blockers, evidence collection, incidents and next vertical slice.      |
| Working demonstration          | Weekly                       | Show live behavior on real cases; accept learning and scope decisions. |
| Outcome review                 | Monthly                      | Assess outcome, adoption, intelligence, risk, service and economics.   |
| Architecture / Risk review     | At gates and material change | Resolve design, authority, control and residual-risk decisions.        |
| Platform productization review | Monthly or quarterly         | Promote repeated components and manage shared-service demand.          |
| Portfolio review               | Quarterly                    | Fund, sequence, continue, scale, reframe or retire initiatives.        |

The daily pod stand-up is the fastest loop and the least formal: it exists to surface blockers and incidents while they are still cheap to fix, and to keep the field loop from Chapter 23 turning without friction. The weekly working demonstration raises the stakes slightly — it is where the pod shows actual behavior on real cases to the people who can accept or redirect the work, rather than describing intended behavior in a status update. The monthly outcome review is the first forum with real portfolio weight: it looks across outcome achievement, adoption, intelligence quality, risk posture, service health and economics together, drawing directly on the aggregate views [Operations and Observability Architecture](../architecture/perspective-09-operations-and-observability-architecture.md) rolls up from every production system.

Architecture and risk reviews are convened by event rather than by calendar — at defined gates or whenever a material change to design, authority or residual risk demands a decision before work continues. The platform productization review is where Chapter 23's classification discipline pays off: repeated components identified across pods are promoted here, and shared-service demand is actively managed rather than left to accumulate informally. The quarterly portfolio review is the highest-stakes forum in the table, with the authority to fund, sequence, continue, scale, reframe or retire initiatives — the same cadence at which the capability map in [Business and Capability Architecture](../architecture/perspective-01-business-and-capability-architecture.md) is reviewed, and deliberately so: a portfolio decision made without visibility into capability duplication and gaps is a decision made half-blind.

## Separation and consolidation

Small organizations will inevitably combine several of these roles in one person, and OASIS does not treat that as a failure condition — but accountability itself must stay explicit even when the people holding it overlap. A person who builds a control may reasonably self-test it for low-risk work, where the cost of a light-touch check is proportionate to the exposure. High-impact systems do not get that latitude: they require independent challenge from someone who did not build the thing being reviewed, which is precisely the role Independent Assurance exists to fill and precisely why it should not be folded into a delivery role even in a small organization.

One line does not bend regardless of organizational size: outcome ownership must remain with the business authority capable of changing the process and accepting the consequences of that change. A platform team, a pod, or a vendor can build, operate and even recommend — but the decision to accept an outcome, and the accountability that comes with it, stays with the business.

---

[← Previous: Chapter 23: Forward Deployed Outcome Engineering](chapter-23-forward-deployed-outcome-engineering.md) · [Contents](../README.md) · [Next: Chapter 25: Enterprise Intelligence Platform →](chapter-25-enterprise-intelligence-platform.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
