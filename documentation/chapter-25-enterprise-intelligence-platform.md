<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 24: Roles, Teams and Governance Forums](chapter-24-roles-teams-and-governance-forums.md) · [Contents](../README.md) · [Next: Part V: Measurement, Scaling and Institutionalization →](part-v-measurement-scaling-and-institutionalization.md)

# Chapter 25: Enterprise Intelligence Platform

# Enterprise Intelligence Platform

> **CHAPTER PURPOSE** Define the shared capabilities that accelerate multiple deployments without forcing every business problem into one rigid architecture.

The Enterprise Intelligence Platform is a product portfolio of shared capabilities, not a single mandatory stack. It reduces time-to-value and control variance while allowing business-specific configuration and last-mile integration.

## Platform capability map

| **Capability**                     | **Scope**                                                                                    |
|------------------------------------|----------------------------------------------------------------------------------------------|
| Model gateway and routing          | Provider abstraction, approved models, region, quotas, fallbacks, caching and cost controls. |
| Agent runtime and harness services | Execution, tool calling, checkpoints, limits, isolation and long-running state.              |
| Context services                   | Prompt/configuration management, context assembly, compression and policy.                   |
| Memory and state services          | Session, workflow and governed persistent memory.                                            |
| Enterprise knowledge services      | Ingestion, parsing, metadata, retrieval, lineage, citations and freshness.                   |
| Integration and tool catalogue     | Approved connectors, tool contracts, identity binding, schemas and versioning.               |
| Identity and access                | User, workload and agent identity; least privilege, consent and delegated authority.         |
| Evaluation platform                | Datasets, test execution, graders, regression, red teaming and scorecards.                   |
| Observability and AgentOps         | Traces, quality, service, cost, incidents and outcome telemetry.                             |
| Security and policy enforcement    | Guardrails, content/context controls, secrets, network, transactions and audit.              |
| Deployment pipelines               | Environment promotion, manifests, tests, canary, rollback and evidence.                      |
| Templates and accelerators         | Reference architectures, starter agents, UI patterns, evaluation packs and runbooks.         |

## Platform versus deployment responsibilities

| **Platform standardizes**                                        | **Deployment configures or owns**                                      |
|------------------------------------------------------------------|------------------------------------------------------------------------|
| Approved runtime, identity patterns, telemetry and policy hooks. | Outcome, workflow, case taxonomy, users and business rules.            |
| Reusable ingestion, retrieval, tool and evaluation services.     | Sources, entitlements, grounding policy and domain evaluation cases.   |
| Release, security, incident and cost controls.                   | Activation, operating authority, local support and outcome thresholds. |
| Supported versions and service levels.                           | Adoption, process change and business continuation decision.           |

## Reuse and productization strategy

A component enters the platform only when it repeats, has a stable contract, has more than one credible consumer, can be supported as a product and does not force business-specific policy into shared code. Target reuse is directional, not a quota: commonly 70–80% of enabling capability may become shared while the operational last mile remains configurable.

## Platform anti-patterns

- Building a large central platform before validating recurring deployment demand.

- Treating one agent framework or model provider as the architecture.

- Centralizing business decision ownership inside the platform team.

- Allowing every deployment to bypass shared identity, evaluation and observability.

- Productizing unstable custom logic after only one implementation.

- Measuring platform success only by API use rather than deployment speed, quality and outcome reuse.

---

[← Previous: Chapter 24: Roles, Teams and Governance Forums](chapter-24-roles-teams-and-governance-forums.md) · [Contents](../README.md) · [Next: Part V: Measurement, Scaling and Institutionalization →](part-v-measurement-scaling-and-institutionalization.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
