<!-- SPDX-License-Identifier: MIT -->

[← Previous: Part IV: Delivery and Enterprise Enablement](part-iv-delivery-and-enterprise-enablement.md) · [Contents](../README.md) · [Next: Chapter 24: Roles, Teams and Governance Forums →](chapter-24-roles-teams-and-governance-forums.md)

# Chapter 23: Forward Deployed Outcome Engineering


> **CHAPTER PURPOSE** Define the embedded execution model that observes real work, builds vertical slices, integrates the last mile and transfers reusable learning.

Forward Deployed Outcome Engineering (FDOE) is OASIS's embedded execution model. A small cross-functional pod works close to operational users until the outcome, the service and the transfer path are all stable. It is not staff augmentation, and not a mandate for permanent custom development.

## Background and context

Every chapter before this one in Part IV, including [Chapter 22](chapter-22-economics-finops-and-sustainability.md), assumes an initiative is already scoped, funded and staffed. None of them answers a practical question: once a team faces a real operational process, how does it turn an approved business case into a working outcome? FDOE answers that question.

Outcomes can rarely be specified up front. The messy detail of real work rarely survives a requirements document — it has to be discovered by engineers working alongside the people who do the job.

Teams that stay at arm's length build clean systems for the documented problem, not the lived one, then spend months fixing things after launch. Teams that overcorrect become permanent custom-build shops. FDOE sits between the two: close enough to see the undocumented rules, but structured to transfer ownership and feed reusable patterns into the platform described in [Chapter 25](chapter-25-enterprise-intelligence-platform.md).

A pod does not operate on its own. [Chapter 24 — Roles, Teams and Governance Forums](chapter-24-roles-teams-and-governance-forums.md) covers its reporting lines and the forums where findings turn into funding decisions, and names each pod role's enterprise counterpart. A pod is embedded inside a business process — it does not own that process. Read its work alongside [Architecture Perspective 3 — Process Architecture](../architecture/perspective-03-process-architecture.md), which draws the line between the process owner (always a named human or function) and the steps an agent is scoped to touch.

## FDOE mission

A pod's mission runs in a fixed order, though the work loops continuously.

It begins with observation: watching how work actually happens, including the undocumented rules and workarounds. That observation becomes something testable — outcome hypotheses that get proven or disproven in the field.

The pod then builds a thin, end-to-end vertical slice that touches every layer of the real workflow, rather than a complete version of just one layer. Going live means engineering the last mile: data access, tooling, identity and workflow integration. The pod then works alongside users through progressive activation, expanding the system's autonomy as trust and evidence build up.

The pod converts what it learns — failures, edge cases, reusable components — into evaluation criteria and platform demand, not tribal knowledge held by the pod alone. The mission closes with transfer: handing ownership back as the service stabilizes. A pod that never leaves has not done its job.

## Pod composition

A pod is small and cross-functional, built around the capabilities a real vertical slice touches. Each capability carries a specific, non-overlapping accountability.

| **Capability**                | **Core responsibility**                                                                         |
|-------------------------------|-------------------------------------------------------------------------------------------------|
| Outcome / Product Lead        | Outcome contract, backlog, priorities, value and stakeholder decisions.                         |
| Business Process Owner        | Operational truth, policy, users, authority and adoption.                                       |
| Forward-Deployed Engineer     | Vertical slice, integration, workflow, tooling and production problem-solving.                  |
| Intelligence Engineer         | Models, context, harness, tools, evaluation and behavior.                                       |
| Data / Knowledge Engineer     | Sources, ingestion, quality, retrieval, lineage and access.                                     |
| Experience / Change Lead      | Human–AI workflow, interface, training, trust and adoption.                                     |
| Reliability / Security / Risk | Production controls, observability, assurance and incident readiness; shared where appropriate. |

The Outcome / Product Lead owns the outcome contract, the backlog and the value trade-off calls. The Business Process Owner is the pod's link to operational truth. Per [Process Architecture](../architecture/perspective-03-process-architecture.md), this role can never be the agent itself — it must be a named human with the authority to change the process and accept the consequences of doing so. Without that person's participation, a pod builds against assumptions instead of reality.

The Forward-Deployed Engineer and Intelligence Engineer split the technical build: one drives the vertical slice and workflow wiring, the other owns models, context assembly, harness behavior, tools and evaluation. The Data / Knowledge Engineer is often the pacing factor, since sources and lineage rarely arrive in the state a plan assumed. The Experience / Change Lead owns adoption: workflow, interface, training and trust.

Reliability / Security / Risk brings production-grade controls and incident readiness in from the start. Per [Security and Trust Architecture](../architecture/perspective-08-security-and-trust-architecture.md), this capability is often shared across pods, especially for credential scoping and kill-switch authority.

## Field loop

The pod's rhythm is a closed loop, not a linear plan. It repeats at whatever cadence the outcome demands — often weekly, faster during an activation push.

It starts by observing: shadowing users, collecting real cases, watching where things fail. That observation leads to agreement on the next milestone and on what evidence will prove it was reached.

Building is deliberately minimal: the smallest vertical change that spans the whole workflow, not the most complete version of one layer. That build is demonstrated weekly to users and decision owners, showing working behavior rather than a slide deck. Once a slice earns confidence, it is activated progressively into production, with trace, human oversight and a fallback path built in.

Every cycle closes with learning: failures are classified, outcomes are measured against the milestone, and the evaluation suite is updated. Underneath every iteration sits the pod's obligation to transfer: document what was built, automate what can be automated, and hand ownership forward.

## Avoiding permanent bespoke delivery

The single greatest risk to an FDOE engagement is a pod that never leaves. At every iteration, the pod sorts its work into one of four buckets: platform capability, reusable deployment component, business-specific configuration, or genuinely bespoke requirement. This keeps the pod honest about whether it is building something durable or piling up one-off fixes nobody else can support.

When the same demand shows up repeatedly, it triggers a productization review — the same governance step as [Chapter 24's](chapter-24-roles-teams-and-governance-forums.md) platform productization forum. If it clears that review, it becomes a candidate for the shared capabilities in [Chapter 25 — Enterprise Intelligence Platform](chapter-25-enterprise-intelligence-platform.md), instead of a pattern each future pod has to rediscover on its own. This also connects to the enterprise capability map in [Business and Capability Architecture](../architecture/perspective-01-business-and-capability-architecture.md): recurring demand across pods is exactly the duplication that map is meant to surface at the quarterly portfolio review.

A pod's exit is judged against explicit, pre-agreed criteria, not a calendar date: the outcome has stabilized, a support owner is named, regression is automated, configuration is documented, users are trained, and there is a path for continued improvement without the pod. Meeting those criteria — not running out of budget — is what marks an FDOE pod's work as done.

> **RELATIONSHIP** OASIS is the transformation, delivery and assurance methodology; Forward Deployed Outcome Engineering is its embedded execution model.

---

[← Previous: Part IV: Delivery and Enterprise Enablement](part-iv-delivery-and-enterprise-enablement.md) · [Contents](../README.md) · [Next: Chapter 24: Roles, Teams and Governance Forums →](chapter-24-roles-teams-and-governance-forums.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
