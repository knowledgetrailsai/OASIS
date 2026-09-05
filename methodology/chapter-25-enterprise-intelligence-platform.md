<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 24: Roles, Teams and Governance Forums](chapter-24-roles-teams-and-governance-forums.md) · [Contents](../README.md) · [Next: Part V: Measurement, Scaling and Institutionalization →](part-v-measurement-scaling-and-institutionalization.md)

# Chapter 25: Enterprise Intelligence Platform


> **CHAPTER PURPOSE** Define the shared capabilities that accelerate multiple deployments without forcing every business problem into one rigid architecture.

The Enterprise Intelligence Platform is a product portfolio of shared capabilities, not a single mandatory stack. It reduces time-to-value and control variance while still allowing business-specific configuration and last-mile integration at the deployment level.

## Background and context

By this point, [Chapter 23](chapter-23-forward-deployed-outcome-engineering.md) has described how a pod discovers what a business problem needs, and [Chapter 24](chapter-24-roles-teams-and-governance-forums.md) has established the governance forums — in particular the platform productization review — where recurring demand gets promoted into something shared. This chapter is where that work lands. It closes Part IV by defining what the enterprise builds once, so delivery does not repeat itself unmodified on every engagement.

This chapter carries more weight than its length suggests. Several enterprise-wide perspective articles treat it as the governance layer above their own scope. [Information and Knowledge Architecture](../architecture/perspective-04-information-and-knowledge-architecture.md) names it as home for shared knowledge domains once more than one system needs the same domain. [Inference Architecture](../architecture/perspective-05-inference-architecture.md) names it as the layer where model routing, fallback and cost pooling are shared rather than re-decided by every build team. [Integration Architecture](../architecture/perspective-06-integration-architecture.md) names it as the investment decision above individual tool contracts, where a shared connector catalogue avoids re-integrating with the same system five times.

The next chapter opens Part V, [Measurement, Scaling and Institutionalization](part-v-measurement-scaling-and-institutionalization.md). The connection is direct: a platform is the primary scaling mechanism OASIS relies on. An enterprise that rebuilds its identity model and evaluation harness for every deployment cannot scale past a handful of systems. A platform lets the fortieth deployment move at a fraction of the first deployment's cost.

## Platform capability map

The platform is organized into twelve capability domains, each independently useful and adoptable on its own schedule. Grouped loosely, they run from the infrastructure a deployment cannot function without — model access, agent execution, context assembly — through the knowledge and integration layers that connect a system to the enterprise, to the assurance layer of evaluation, observability and security that makes autonomy safe to grant, and finally to the delivery mechanics that get a system into production.

| **Capability**                     | **Scope**                                                                                    |
|--------------------------------------|--------------------------------------------------------------------------------------------------|
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

Three domains have a direct, named relationship to a companion architecture perspective. Model gateway and routing implements what [Inference Architecture](../architecture/perspective-05-inference-architecture.md) calls the enterprise inference layer: a routing point that lets any system swap models without an application rewrite, pools volume and cost across consumers, and gives one fallback strategy for a provider outage instead of many separate ones. Enterprise knowledge services is the shared half of the domain map in [Information and Knowledge Architecture](../architecture/perspective-04-information-and-knowledge-architecture.md) — it stops the enterprise from ending up with as many divergent copies of "the current policy" as it has systems. Integration and tool catalogue is the platform home for connector governance in [Integration Architecture](../architecture/perspective-06-integration-architecture.md): one integration per system, reused across every consuming agent, with a single credential registry that makes revocation executable across the whole estate.

The remaining domains matter just as much, even though they lack a dedicated companion article. Evaluation, observability and security are what make it safe to grant autonomy in the first place. A platform with fast routing and cheap storage but no matching evaluation layer is only half a platform.

## Platform versus deployment responsibilities

The line between what the platform standardizes and what a deployment owns is the most consequential design decision here. Draw it too far toward centralization and every deployment inherits delay it did not ask for. Draw it too far toward autonomy and the enterprise keeps paying to rebuild the same integration, evaluation harness and identity model.

| **Platform standardizes**                                        | **Deployment configures or owns**                                      |
|----------------------------------------------------------------------|------------------------------------------------------------------------------|
| Approved runtime, identity patterns, telemetry and policy hooks. | Outcome, workflow, case taxonomy, users and business rules.            |
| Reusable ingestion, retrieval, tool and evaluation services.     | Sources, entitlements, grounding policy and domain evaluation cases.   |
| Release, security, incident and cost controls.                   | Activation, operating authority, local support and outcome thresholds. |
| Supported versions and service levels.                           | Adoption, process change and business continuation decision.           |

The pattern is consistent across rows: the platform standardizes the "how" — runtime, identity model, controls — while the deployment keeps the "what" and "why": which outcome it pursues, which business rules apply. This mirrors [Process Architecture](../architecture/perspective-03-process-architecture.md): the platform can own the mechanism, but never the outcome.

## Reuse and productization strategy

A component earns its place in the platform only after clearing a real bar. Being built once and someone thinking other teams might like it is not enough. It has to repeat: something seen only once is a deployment artifact, not a platform candidate. It needs a stable contract and more than one credible consumer already identified. It has to be supportable as a real product — with an owner, a roadmap and service levels — not an orphaned dependency nobody maintains. And it must not smuggle business-specific policy into shared code; a component that encodes one business unit's rules becomes a liability the moment another unit tries to use it.

Target reuse is directional guidance, not a quota. Commonly 70–80% of the enabling capability behind a deployment can become shared, while the operational last mile — workflow, business rules, and the exceptions a Business Process Owner is accountable for — stays configurable. Chasing 100% reuse usually means business logic was forced into the platform layer. Chasing 0% reuse means Chapter 24's productization review isn't being convened often enough, or isn't trusted with the authority it needs.

## Platform anti-patterns

The failure modes below share a root cause: each inverts the relationship this chapter is built around, either letting the platform get ahead of proven demand or letting deployment teams route around its controls.

Building a large central platform before validating demand front-loads cost against capabilities nobody has proven they need. Treating one agent framework or model provider as the architecture, rather than a current choice, gives up model independence and exposes the enterprise to a single vendor's roadmap and pricing. Centralizing business decisions inside the platform team strips accountability from the business authority who should hold it.

Letting every deployment bypass shared identity, evaluation and observability defeats the purpose of the platform: a bypassed control is an unmanaged risk, not a faster path to production. Productizing unstable custom logic after a single implementation skips the repetition test the reuse bar depends on, and usually produces a component nobody else can safely build against. Measuring platform success only by API call volume, instead of deployment speed and outcome reuse, rewards the platform team for being used rather than for being useful.

---

[← Previous: Chapter 24: Roles, Teams and Governance Forums](chapter-24-roles-teams-and-governance-forums.md) · [Contents](../README.md) · [Next: Part V: Measurement, Scaling and Institutionalization →](part-v-measurement-scaling-and-institutionalization.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
