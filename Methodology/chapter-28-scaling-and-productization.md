<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 27: Delivery Cadence and Management Practices](chapter-27-delivery-cadence-and-management-practices.md) · [Contents](../README.md) · [Next: Chapter 29: OASIS Adoption Roadmap →](chapter-29-oasis-adoption-roadmap.md)

# Chapter 28: Scaling and Productization

# Scaling and Productization

> **CHAPTER PURPOSE** Separate platform capability, reusable deployment components, business configuration and true custom work to scale without multiplying bespoke systems.

## Background and context

Chapter 27 gives a pod the operating discipline to deliver reliably for one business context. This chapter addresses what happens next: the same pod, or a different one, is asked to deliver something similar for a second business context, then a third, and the organization has to decide whether each of those is a fresh bespoke build or a deployment of something that already exists. Get that decision wrong in one direction and the enterprise ends up with dozens of near-identical systems, each separately built, separately secured and separately maintained, none of them benefiting from what was learned building the others. Get it wrong in the other direction and a genuinely different business context gets forced into a one-size-fits-all platform that fits none of its users well, quietly training people to work around the system rather than through it.

Scaling and productization is the discipline that prevents both failure modes by insisting on a clear separation between what is genuinely shared, what is configurable per context, and what is truly bespoke — and by refusing to let any of the three quietly become the other two through neglect. This is also the chapter where the FDOE pod's role changes fundamentally: everything up to this point has been about the pod proving and delivering a capability; from here, the pod's job is increasingly to make itself unnecessary to that capability's ongoing operation, transferring it to a permanent owner rather than becoming its permanent, informal maintenance team.

Three companion documents carry this chapter's framework into architectural and template detail. [Architecture Perspective 1 — Business and Capability Architecture](../architecture/perspective-01-business-and-capability-architecture.md) gives the enterprise a durable capability map and portfolio view — the artifact that makes visible, at a glance, which capabilities exist once and which exist five redundant times, which is precisely the question this chapter's asset-class distinctions are built to answer before that duplication happens rather than after. [Architecture Perspective 6 — Integration Architecture](../architecture/perspective-06-integration-architecture.md) makes the same point at the level of individual tool integrations: without an enterprise integration catalogue, every new deployment re-integrates with the same systems of record from scratch, multiplying both build cost and the number of independently configured credentials attached to the same underlying system. And the [Scale and Productization Assessment](../tools/05-risk-and-scale-templates.md#18-scale-and-productization-assessment) template turns the judgment calls in this chapter — demand, repeatability, contract stability, tenancy, support model, unit economics and risk at scale — into a structured artifact a platform owner completes before deciding whether a capability should be productized, kept bespoke, or retired.

## Scaling readiness

Scaling is rarely a single dial. An initiative can grow along several independent dimensions — more users, more transactions, more workflows, more business units, more geographies, more data, more integrations, more decision-making authority — and each of those dimensions can shift risk and economics on its own, in a direction that has nothing to do with what the others are doing. A system that goes from one thousand to ten thousand users has scaled in a way that mostly stresses infrastructure and support capacity; a system that goes from advisory output to autonomous execution has scaled in a way that stresses governance and control, regardless of what happened to its user count. Treating "scale" as one undifferentiated growth curve is a reliable way to miss the dimension that actually matters for a given decision.

This is why volume and risk should never be conflated as if one predicted the other. A low-volume decision with genuine safety consequences can legitimately require deeper assurance than a high-volume assistant whose worst-case failure is a mildly unhelpful answer — the volume of a decision says nothing on its own about what happens when it is wrong. Readiness to scale, in the OASIS sense, means having already answered, for the specific dimension about to grow, what changes in risk, governance and economics that growth will bring — not simply confirming that the infrastructure will hold under load.

Scaling readiness also depends on knowing precisely what kind of asset is being scaled, because the four asset classes below carry very different obligations. Core platform capability is a shared service with a stable contract and multiple consumers, owned by a platform product owner who is accountable for that contract holding even as consumers multiply. A reusable deployment component — a portable agent, connector, evaluation pack, workflow or UI module — is owned by a component owner or a community, but critically needs an explicit support model; a reusable component with no one accountable for supporting it is a liability wearing the appearance of an asset. Business configuration covers the policies, taxonomies, prompts, thresholds, roles and sources specific to one domain, and belongs to the business and service owner rather than to the platform team — configuration is where a shared capability adapts to a local context without forking. And a bespoke requirement is unique logic or integration that genuinely cannot yet be generalized, owned by the deployment team with explicit, acknowledged maintenance responsibility rather than left as an orphaned exception nobody quite owns.

| **Asset class**               | **Definition**                                                                     | **Ownership**                                   |
|--------------------------------|--------------------------------------------------------------------------------------|---------------------------------------------------|
| Core platform capability      | Shared service with stable contract and multiple consumers.                        | Platform product owner.                           |
| Reusable deployment component | Portable agent, connector, evaluation pack, workflow or UI module.                 | Component owner / community with support model.   |
| Business configuration        | Policies, taxonomies, prompts, thresholds, roles and sources specific to a domain. | Business and service owner.                       |
| Bespoke requirement           | Unique logic or integration that cannot yet be generalized.                        | Deployment team with explicit maintenance.        |

## Configuration versus customization

The line between configuration and customization is where most productization efforts either succeed cleanly or slowly decay into unmaintainable sprawl, and it is worth being precise about where it sits. Configuration changes data, policy and behavior through contracts the platform explicitly supports — a new taxonomy, an adjusted threshold, a different set of approved sources — without touching the code underneath. Customization changes core code, or creates a fork the platform team did not sanction and cannot support the way it supports its own releases. The difference is not cosmetic: a configuration change survives a platform upgrade; a customization typically has to be re-applied, re-tested, and re-justified every time the platform underneath it moves.

OASIS's preference is unambiguous — configurable templates with deliberately validated extension points, so that the parts of a system a business context genuinely needs to adjust are adjustable without forking anything. But that preference is not absolute. Bespoke work is accepted, and should be accepted, when it is what actually differentiates the business, or when the operating environment genuinely cannot be served any other way. The failure to avoid is not building bespoke systems — sometimes that is the right call — but building them by accident, one unplanned exception at a time, until a system originally intended to be a shared capability has quietly become an unsupportable one-off with no one who remembers why each deviation was made.

## Multi-business deployment

Taking a capability from its first successful deployment to a second business context is a distinct piece of work, not a formality, and OASIS treats it as a defined sequence rather than an assumption that what worked once will simply work again. It starts by proving the capability in that second context on its own terms — new users, new data, new exceptions — rather than assuming the first deployment's evidence transfers automatically; a capability that worked well for one business unit's data and user population can fail in ways specific to a different one, and the only way to find out is to test it there directly. From that evidence, the team separates what is genuinely shared system behavior from what is local policy and workflow, which is the practical, case-by-case application of the configuration-versus-customization distinction above.

With that separation in place, the deployment defines tenancy, data isolation, entitlements and performance boundaries explicitly, rather than discovering them under incident conditions after two business units' data has already mixed somewhere it shouldn't have. It establishes federated governance — enterprise-wide standards paired with genuine local ownership of outcome and policy, so that neither the center nor the business unit ends up solely accountable for decisions that are properly shared between them. It sets version compatibility, rollout sequencing, support arrangements and change communication before the second deployment goes live, not after the first incident makes the gap obvious. And throughout, it measures reuse benefit and local outcome as two separate things — a deployment can deliver genuine local value while contributing little to platform reuse, or vice versa, and collapsing the two into a single number hides which one is actually true.

68. Prove the capability in a second business context with new users, data and exceptions.

69. Separate shared system behavior from local policy and workflow.

70. Define tenancy, data isolation, entitlements and performance boundaries.

71. Create federated governance: enterprise standards with business outcome and policy ownership.

72. Establish version compatibility, rollout sequencing, support and change communication.

73. Measure reuse benefit and local outcome independently.

## Reducing FDOE dependency

A capability is not genuinely productized until it can survive without the pod that built it, and this section is about what "can survive" actually requires in practice. Transfer to a permanent owner needs automated evaluation the receiving team can run without the pod's help, reproducible deployment that does not depend on tribal knowledge, documented configuration a new operator can follow, tools stable enough not to require constant relearning, named service ownership that is genuinely accepted rather than assigned on paper, users who have been properly trained rather than merely informed, and an improvement process the receiving team can run on its own once the pod has stepped back.

The pod may reasonably stay involved for major expansions — a significant new business context, a substantial change in scope — where its accumulated expertise is genuinely still needed. What it should not become is the permanent, informal operator of routine local work, quietly absorbing operational load that should have been transferred, because every hour the pod spends running yesterday's capability is an hour it is not spending proving tomorrow's, and an enterprise that lets this happen will find its FDOE pods multiplying in number while their throughput of new capability quietly declines.

---

[← Previous: Chapter 27: Delivery Cadence and Management Practices](chapter-27-delivery-cadence-and-management-practices.md) · [Contents](../README.md) · [Next: Chapter 29: OASIS Adoption Roadmap →](chapter-29-oasis-adoption-roadmap.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
