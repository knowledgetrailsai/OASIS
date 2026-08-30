<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 27: Delivery Cadence and Management Practices](chapter-27-delivery-cadence-and-management-practices.md) · [Contents](../README.md) · [Next: Chapter 29: OASIS Adoption Roadmap →](chapter-29-oasis-adoption-roadmap.md)

# Chapter 28: Scaling and Productization

# Scaling and Productization

> **CHAPTER PURPOSE** Separate platform capability, reusable deployment components, business configuration and true custom work to scale without multiplying bespoke systems.

## Background and context

Chapter 27 gives a pod the operating discipline to deliver reliably for one business context. This chapter addresses what happens next: the same pod, or a different one, is asked to deliver something similar for a second business context, then a third. The organization has to decide whether each is a fresh bespoke build or a deployment of something that already exists.

Get that decision wrong one way and the enterprise ends up with dozens of near-identical systems, separately built, secured and maintained, none benefiting from what was learned building the others. Get it wrong the other way and a genuinely different business context gets forced into a one-size-fits-all platform that fits none of its users well, training people to work around it.

Scaling and productization prevents both failure modes by insisting on a clear separation between what is genuinely shared, what is configurable per context, and what is truly bespoke — and by not letting any of the three quietly turn into the other two through neglect. This is also where the FDOE pod's role changes: up to this point it has been proving and delivering a capability. From here, its job is increasingly to make itself unnecessary to that capability's ongoing operation, transferring it to a permanent owner rather than becoming its informal maintenance team.

Three companion documents carry this framework into architectural and template detail. [Architecture Perspective 1 — Business and Capability Architecture](../architecture/perspective-01-business-and-capability-architecture.md) gives the enterprise a durable capability map and portfolio view, making visible which capabilities exist once and which exist five redundant times — the question this chapter's asset-class distinctions answer before duplication happens. [Architecture Perspective 6 — Integration Architecture](../architecture/perspective-06-integration-architecture.md) makes the same point at the level of tool integrations: without an enterprise integration catalogue, every new deployment re-integrates with the same systems of record from scratch, multiplying build cost and duplicate credentials. The [Scale and Productization Assessment](../tools/05-risk-and-scale-templates.md#18-scale-and-productization-assessment) template turns the judgment calls in this chapter — demand, repeatability, contract stability, tenancy, support model, unit economics and risk at scale — into a structured artifact a platform owner completes before deciding whether a capability should be productized, kept bespoke, or retired.

## Scaling readiness

Scaling is rarely a single dial. An initiative can grow along several independent dimensions — more users, transactions, workflows, business units, geographies, data, integrations, decision-making authority — and each can shift risk and economics in a different direction. A system that goes from one thousand to ten thousand users mostly stresses infrastructure and support capacity. A system that goes from advisory output to autonomous execution stresses governance and control, regardless of user count. Treating "scale" as one undifferentiated growth curve is a reliable way to miss the dimension that actually matters.

Volume and risk should never be conflated as if one predicted the other. A low-volume decision with genuine safety consequences can require deeper assurance than a high-volume assistant whose worst-case failure is a mildly unhelpful answer — volume says nothing about what happens when a decision is wrong. Readiness to scale means having already answered, for the specific dimension about to grow, what changes in risk, governance and economics that growth will bring. It is not enough to confirm the infrastructure will hold under load.

Scaling readiness also depends on knowing what kind of asset is being scaled, since the four asset classes below carry different obligations. Core platform capability is a shared service with a stable contract and multiple consumers, owned by a platform product owner accountable for that contract holding as consumers multiply. A reusable deployment component — a portable agent, connector, evaluation pack, workflow or UI module — is owned by a component owner or a community, but needs an explicit support model; one with no one accountable for supporting it is a liability wearing the appearance of an asset. Business configuration covers the policies, taxonomies, prompts, thresholds, roles and sources specific to one domain, and belongs to the business and service owner — configuration is where a shared capability adapts to a local context without forking. A bespoke requirement is unique logic or integration that cannot yet be generalized, owned by the deployment team with explicit, acknowledged maintenance responsibility rather than left as an orphan nobody owns.

| **Asset class**               | **Definition**                                                                     | **Ownership**                                   |
|--------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------|
| Core platform capability      | Shared service with stable contract and multiple consumers.                        | Platform product owner.                           |
| Reusable deployment component | Portable agent, connector, evaluation pack, workflow or UI module.                 | Component owner / community with support model.   |
| Business configuration        | Policies, taxonomies, prompts, thresholds, roles and sources specific to a domain. | Business and service owner.                       |
| Bespoke requirement           | Unique logic or integration that cannot yet be generalized.                        | Deployment team with explicit maintenance.        |

## Configuration versus customization

The line between configuration and customization is where most productization efforts either succeed or decay into unmaintainable sprawl. Configuration changes data, policy and behavior through contracts the platform explicitly supports — a new taxonomy, an adjusted threshold, a different set of approved sources — without touching the code underneath. Customization changes core code, or creates a fork the platform team did not sanction and cannot support. A configuration change survives a platform upgrade; a customization typically has to be re-applied, re-tested and re-justified every time the platform moves.

OASIS's preference is unambiguous: configurable templates with validated extension points, so the parts of a system a business context needs to adjust are adjustable without forking anything. That preference is not absolute — bespoke work is accepted when it actually differentiates the business, or when the operating environment cannot be served any other way. The failure to avoid is not building bespoke systems, since sometimes that is the right call, but building them by accident, one unplanned exception at a time, until a shared capability has quietly become an unsupportable one-off nobody remembers the reasons for.

## Multi-business deployment

Taking a capability from its first successful deployment to a second business context is a distinct piece of work, not a formality. OASIS treats it as a defined sequence, not an assumption that what worked once will work again.

It starts by proving the capability in that second context on its own terms — new users, new data, new exceptions — rather than assuming the first deployment's evidence transfers automatically. A capability that worked for one business unit can fail in ways specific to another, and the only way to find out is to test it there directly. From that evidence, the team separates what is genuinely shared system behavior from what is local policy and workflow, applying the configuration-versus-customization distinction above case by case.

With that separation in place, the deployment defines tenancy, data isolation, entitlements and performance boundaries explicitly, rather than discovering them under incident conditions after two business units' data has already mixed. It establishes federated governance — enterprise-wide standards paired with genuine local ownership of outcome and policy, so neither the center nor the business unit is solely accountable. It sets version compatibility, rollout sequencing, support arrangements and change communication before the second deployment goes live, not after the first incident makes the gap obvious. Throughout, it measures reuse benefit and local outcome as two separate things — a deployment can deliver genuine local value while contributing little to platform reuse, or vice versa, and collapsing the two into a single number hides which one is true.

68. Prove the capability in a second business context with new users, data and exceptions.

69. Separate shared system behavior from local policy and workflow.

70. Define tenancy, data isolation, entitlements and performance boundaries.

71. Create federated governance: enterprise standards with business outcome and policy ownership.

72. Establish version compatibility, rollout sequencing, support and change communication.

73. Measure reuse benefit and local outcome independently.

## Reducing FDOE dependency

A capability is not genuinely productized until it can survive without the pod that built it. Transfer to a permanent owner needs automated evaluation the receiving team can run without the pod's help, reproducible deployment that does not depend on tribal knowledge, documented configuration a new operator can follow, stable tools, named service ownership genuinely accepted rather than assigned on paper, properly trained users, and an improvement process the receiving team can run on its own once the pod steps back.

The pod may reasonably stay involved for major expansions — a significant new business context, a substantial change in scope — where its accumulated expertise is still needed. What it should not become is the permanent, informal operator of routine local work. Every hour the pod spends running yesterday's capability is an hour it is not spending proving tomorrow's. An enterprise that lets this happen will find its FDOE pods multiplying while their throughput of new capability quietly declines.

---

[← Previous: Chapter 27: Delivery Cadence and Management Practices](chapter-27-delivery-cadence-and-management-practices.md) · [Contents](../README.md) · [Next: Chapter 29: OASIS Adoption Roadmap →](chapter-29-oasis-adoption-roadmap.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
