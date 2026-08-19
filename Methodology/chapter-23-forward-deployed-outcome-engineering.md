<!-- SPDX-License-Identifier: MIT -->

[← Previous: Part IV: Delivery and Enterprise Enablement](part-iv-delivery-and-enterprise-enablement.md) · [Contents](../README.md) · [Next: Chapter 24: Roles, Teams and Governance Forums →](chapter-24-roles-teams-and-governance-forums.md)

# Chapter 23: Forward Deployed Outcome Engineering

# Forward Deployed Outcome Engineering

> **CHAPTER PURPOSE** Define the embedded execution model that observes real work, builds vertical slices, integrates the last mile and transfers reusable learning.

Forward Deployed Outcome Engineering (FDOE) is OASIS's embedded execution model. A small cross-functional pod works close to operational users until the outcome, the service and the transfer path are all stable. It is not staff augmentation, and not a mandate for permanent custom development.

## Background and context

Every chapter before this one in Part IV, including [Chapter 22](chapter-22-economics-finops-and-sustainability.md), assumes an initiative is already scoped, funded and staffed. None answers a practical question: once a team faces a real operational process, how does it turn an approved business case into a working outcome? FDOE answers that. Outcomes can rarely be specified up front, because the messy detail of real work rarely survives a requirements document. It has to be discovered by engineers working alongside the people who do the job.

Teams that stay at arm's length build elegant systems for the documented problem, not the lived one, then spend months correcting after launch. Teams that overcorrect become permanent bespoke shops. FDOE sits between the two: close enough to see undocumented rules, but structured to transfer ownership and feed reusable patterns into the platform in [Chapter 25](chapter-25-enterprise-intelligence-platform.md).

A pod does not operate in isolation. Its accountability lines and the forums where findings become funding decisions are covered in [Chapter 24 — Roles, Teams and Governance Forums](chapter-24-roles-teams-and-governance-forums.md), which names each pod role's enterprise counterpart. A pod is embedded inside a business process, not the owner of it. Its work should be read alongside [Architecture Perspective 3 — Process Architecture](../architecture/perspective-03-process-architecture.md), which distinguishes the process owner — always a named human or function — from the steps an agent is scoped to touch.

## FDOE mission

A pod's mission runs in a fixed order, though the work loops continuously. It begins with observation: watching how work actually happens, including undocumented rules and workarounds. That becomes something testable — outcome hypotheses proven or disproven in the field.

The pod then builds a thin, end-to-end vertical slice touching every layer of the real workflow, not a comprehensive feature built on paper. Going live means engineering the last mile: data access, tooling, identity and workflow integration. The pod operates alongside users through progressive activation, expanding autonomy as trust and evidence accumulate. It converts what it learns — failures, edge cases, reusable components — into evaluation criteria and platform demand, not tribal knowledge. The mission closes with transfer: handing ownership back as the service stabilizes. A pod that never leaves has failed its job.

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

The Outcome / Product Lead owns the outcome contract, backlog and value trade-off calls. The Business Process Owner is the pod's link to operational truth. Per [Process Architecture](../architecture/perspective-03-process-architecture.md), this role can never be the agent itself — it is the named human with authority to change the process and accept the consequences. Without their participation, a pod builds against assumptions, not reality.

The Forward-Deployed Engineer and Intelligence Engineer split the technical build: one drives the vertical slice and workflow wiring; the other owns models, context assembly, harness behavior, tools and evaluation. The Data / Knowledge Engineer is often the pacing factor — sources and lineage rarely arrive in the state a plan assumed. The Experience / Change Lead owns adoption: workflow, interface, training and trust. Reliability / Security / Risk brings production-grade controls and incident readiness in from the start. Per [Security and Trust Architecture](../architecture/perspective-08-security-and-trust-architecture.md), this capability is often shared across pods, especially for credential scoping and kill-switch authority.

## Field loop

The pod's rhythm is a closed loop, not a linear plan, repeating at whatever cadence the outcome demands — often weekly, faster during an activation push. It starts by observing: shadowing users, collecting real cases, watching where things fail. That observation becomes agreement on the next milestone and what evidence proves it was reached.

Building is deliberately minimal: the smallest vertical change spanning the whole workflow, not the most complete version of one layer. That build is demonstrated weekly to users and decision owners, showing working behavior rather than a slide. Once a slice earns confidence, it is activated progressively into production, with trace, human oversight and a fallback path built in.

Every cycle closes with learning: failures are classified, outcomes measured against the milestone, and the evaluation suite updated. Underneath every iteration sits the pod's obligation to transfer: document what was built, automate what can be automated, and hand ownership forward.

## Avoiding permanent bespoke delivery

The single greatest risk to an FDOE engagement is a pod that never leaves. At every iteration, the pod classifies its work into one of four buckets: platform capability, reusable deployment component, business-specific configuration, or genuinely bespoke requirement. This keeps the pod honest about whether it is building something durable or accumulating one-off fixes nobody else can support.

When the same demand shows up repeatedly, it triggers a productization review — the same governance step as [Chapter 24's](chapter-24-roles-teams-and-governance-forums.md) platform productization forum. If it clears that review, it becomes a candidate for the shared capabilities in [Chapter 25 — Enterprise Intelligence Platform](chapter-25-enterprise-intelligence-platform.md), rather than a pattern each future pod rediscovers. This also connects to the enterprise capability map in [Business and Capability Architecture](../architecture/perspective-01-business-and-capability-architecture.md): recurring demand across pods is exactly the duplication that map surfaces at the quarterly portfolio review.

A pod's exit is judged against explicit, pre-agreed criteria, not a calendar date: the outcome has stabilized, a support owner is named, regression is automated, configuration is documented, users are trained, and there is a path for continued improvement without the pod. Meeting those criteria — not running out of budget — marks an FDOE pod's work as done.

> **RELATIONSHIP** OASIS is the transformation, delivery and assurance methodology; Forward Deployed Outcome Engineering is its embedded execution model.

---

[← Previous: Part IV: Delivery and Enterprise Enablement](part-iv-delivery-and-enterprise-enablement.md) · [Contents](../README.md) · [Next: Chapter 24: Roles, Teams and Governance Forums →](chapter-24-roles-teams-and-governance-forums.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
