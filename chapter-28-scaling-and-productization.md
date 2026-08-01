<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 27: Delivery Cadence and Management Practices](chapter-27-delivery-cadence-and-management-practices.md) · [Contents](README.md) · [Next: Chapter 29: OASIS Adoption Roadmap →](chapter-29-oasis-adoption-roadmap.md)

# Chapter 28: Scaling and Productization

# Scaling and Productization

> **CHAPTER PURPOSE** Separate platform capability, reusable deployment components, business configuration and true custom work to scale without multiplying bespoke systems.

## Scaling readiness

Scaling means increasing users, transactions, workflows, business units, geographies, data, integrations or authority. Each dimension can change risk and economics independently. A low-volume safety decision may require greater assurance than a high-volume low-impact assistant.

| **Asset class**               | **Definition**                                                                     | **Ownership**                                   |
|-------------------------------|------------------------------------------------------------------------------------|-------------------------------------------------|
| Core platform capability      | Shared service with stable contract and multiple consumers.                        | Platform product owner.                         |
| Reusable deployment component | Portable agent, connector, evaluation pack, workflow or UI module.                 | Component owner / community with support model. |
| Business configuration        | Policies, taxonomies, prompts, thresholds, roles and sources specific to a domain. | Business and service owner.                     |
| Bespoke requirement           | Unique logic or integration that cannot yet be generalized.                        | Deployment team with explicit maintenance.      |

## Configuration versus customization

Configuration changes data, policy and behavior through supported contracts. Customization changes core code or creates an unsupported fork. OASIS favors configurable templates with validated extension points, but accepts bespoke work when it differentiates the business or the operating environment genuinely requires it.

## Multi-business deployment

68. Prove the capability in a second business context with new users, data and exceptions.

69. Separate shared system behavior from local policy and workflow.

70. Define tenancy, data isolation, entitlements and performance boundaries.

71. Create federated governance: enterprise standards with business outcome and policy ownership.

72. Establish version compatibility, rollout sequencing, support and change communication.

73. Measure reuse benefit and local outcome independently.

## Reducing FDOE dependency

Transfer requires automated evaluation, reproducible deployment, documented configuration, stable tools, named service ownership, trained users and an improvement process. The pod may remain for major expansions but should not become the permanent operator of routine local work.

---

[← Previous: Chapter 27: Delivery Cadence and Management Practices](chapter-27-delivery-cadence-and-management-practices.md) · [Contents](README.md) · [Next: Chapter 29: OASIS Adoption Roadmap →](chapter-29-oasis-adoption-roadmap.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](LICENSE.md).
