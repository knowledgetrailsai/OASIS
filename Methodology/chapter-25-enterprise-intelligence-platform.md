<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 24: Roles, Teams and Governance Forums](chapter-24-roles-teams-and-governance-forums.md) · [Contents](../README.md) · [Next: Part V: Measurement, Scaling and Institutionalization →](part-v-measurement-scaling-and-institutionalization.md)

# Chapter 25: Enterprise Intelligence Platform

# Enterprise Intelligence Platform

> **CHAPTER PURPOSE** Define the shared capabilities that accelerate multiple deployments without forcing every business problem into one rigid architecture.

The Enterprise Intelligence Platform is a product portfolio of shared capabilities, not a single mandatory stack. It reduces time-to-value and control variance while still allowing business-specific configuration and last-mile integration at the deployment level.

## Background and context

By this point in the methodology, [Chapter 23](chapter-23-forward-deployed-outcome-engineering.md) has described how a pod discovers what a business problem actually needs, and [Chapter 24](chapter-24-roles-teams-and-governance-forums.md) has established the governance forums — in particular the platform productization review — where recurring demand gets promoted from a one-off pattern into something shared. This chapter is where that promoted work lands. It closes Part IV by defining what the enterprise actually builds once, so the delivery model described in the two preceding chapters does not simply repeat itself, unmodified, on every new engagement.

This chapter carries more architectural weight than its length suggests, because several of the enterprise-wide perspective articles treat it as the governance layer that sits above their own scope. [Information and Knowledge Architecture](../architecture/perspective-04-information-and-knowledge-architecture.md) names this chapter as the home for shared knowledge domains once more than one system needs the same domain. [Inference Architecture](../architecture/perspective-05-inference-architecture.md) names it as the layer where model routing, fallback and cost pooling are architected as a shared capability rather than re-decided independently by every build team. [Integration Architecture](../architecture/perspective-06-integration-architecture.md) names it as the investment decision above individual tool contracts, where a shared connector catalogue prevents the enterprise from re-integrating with the same system of record five separate times. This chapter is written to actually support what those three perspectives claim of it, not merely to gesture at "a platform" in the abstract.

The chapter that follows this one opens Part V, [Measurement, Scaling and Institutionalization](part-v-measurement-scaling-and-institutionalization.md), and the connection is direct: a platform is itself the primary scaling mechanism OASIS relies on. An enterprise that has to rebuild its identity model, its evaluation harness and its retrieval pipeline for every new deployment cannot scale past a handful of systems no matter how good its delivery model is; a platform is what lets the fortieth deployment move at a fraction of the first deployment's cost.

## Platform capability map

The platform is organized as twelve capability domains, each independently useful and each capable of being adopted incrementally rather than as an all-or-nothing package. Grouped loosely, they run from the infrastructure a deployment cannot function without — model access, agent execution, context assembly — through the knowledge and integration layers that connect a system to the enterprise, to the assurance layer of evaluation, observability and security that makes autonomy safe to grant, and finally to the delivery mechanics that get a system into production and keep it there.

| **Capability**                     | **Scope**                                                                                    |
|-------------------------------------|------------------------------------------------------------------------------------------------|
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

Three of these domains carry a direct, named relationship to a companion architecture perspective, and each is worth reading in full before making an investment decision against it. The model gateway and routing domain is this chapter's implementation of what [Inference Architecture](../architecture/perspective-05-inference-architecture.md) calls the enterprise inference layer: a centralized routing point that lets any individual system swap models without an application-level rewrite, pools volume and cost across every consuming system rather than leaving each one to negotiate independently, and gives the enterprise a single fallback strategy for a provider outage instead of dozens of uncoordinated ones. Enterprise knowledge services is the shared-service half of the domain map defined in [Information and Knowledge Architecture](../architecture/perspective-04-information-and-knowledge-architecture.md) — the mechanism that keeps the enterprise from ending up with as many divergent copies of "the current policy" as it has systems, each silently drifting out of sync with the authoritative source. And the integration and tool catalogue domain is the platform-level home for the connector governance defined in [Integration Architecture](../architecture/perspective-06-integration-architecture.md): one integration per enterprise system, reused across every consuming agent, with a single credential and scope registry that makes a revocation decision actually executable across the whole estate rather than one system at a time.

The remaining domains are no less important for lacking a single dedicated companion article — evaluation, observability and security in particular are what make it safe to grant any of the autonomy the rest of this handbook describes, and a platform that ships fast routing and cheap storage without a matching evaluation and observability layer has built half a platform.

## Platform versus deployment responsibilities

The line between what the platform standardizes and what a deployment owns is the single most consequential design decision in building this platform, and getting it wrong in either direction is expensive. Draw the line too far toward centralization and every deployment inherits delay and rigidity it did not ask for; draw it too far toward deployment autonomy and the enterprise pays, repeatedly, for the same integration, the same evaluation harness and the same identity model to be rebuilt from scratch.

| **Platform standardizes**                                        | **Deployment configures or owns**                                      |
|--------------------------------------------------------------------|----------------------------------------------------------------------------|
| Approved runtime, identity patterns, telemetry and policy hooks. | Outcome, workflow, case taxonomy, users and business rules.            |
| Reusable ingestion, retrieval, tool and evaluation services.     | Sources, entitlements, grounding policy and domain evaluation cases.   |
| Release, security, incident and cost controls.                   | Activation, operating authority, local support and outcome thresholds. |
| Supported versions and service levels.                           | Adoption, process change and business continuation decision.           |

The pattern in that table is consistent even though the specifics differ row by row: the platform standardizes the "how" — the runtime a system executes on, the identity model it authenticates against, the controls it operates under — while the deployment retains the "what" and the "why": which outcome it is pursuing, which business rules apply, and the process decisions that no platform team is positioned to make on a business unit's behalf. That division mirrors the process ownership principle from [Process Architecture](../architecture/perspective-03-process-architecture.md): the platform can own the mechanism, but it never owns the outcome.

## Reuse and productization strategy

A component earns its place in the platform only after clearing a real bar, not simply because it has been built once and someone thinks other teams might like it. It has to repeat — a pattern seen only once is a deployment artifact, not a platform candidate. It needs a contract stable enough that consuming teams can build against it with confidence that it will not shift underneath them. It needs more than one credible consumer already identified, not a hypothetical future one. It has to be supportable as an actual product, with an owner, a roadmap and service levels, rather than becoming an orphaned shared dependency nobody maintains. And it must not smuggle business-specific policy into shared code — a platform component that quietly encodes one business unit's rules becomes a liability the moment a second business unit tries to use it.

Target reuse is directional guidance, not a quota to be gamed: commonly 70–80% of the enabling capability behind a deployment can become shared, while the operational last mile — the specific workflow, the specific business rules, the specific exceptions a Business Process Owner is accountable for — remains configurable rather than centralized. Chasing 100% reuse is usually a sign that business-specific logic has been forced into the platform layer where it does not belong; chasing 0% reuse is a sign the productization review described in Chapter 24 is not being convened often enough, or is not being trusted with the authority it needs.

## Platform anti-patterns

The failure modes below share a common root: each one inverts the relationship this chapter is built around, either by letting the platform get ahead of proven demand or by letting deployment teams route around the controls the platform exists to enforce.

Building a large central platform before validating recurring deployment demand front-loads cost and risk against capabilities nobody has yet proven they need — the platform equivalent of building a factory before confirming there is a product to make in it. Treating one agent framework or model provider as the architecture rather than as a current implementation choice quietly abandons the model-independence this chapter's gateway domain exists to protect, and leaves the enterprise exposed to a single vendor's roadmap and pricing decisions. Centralizing business decision ownership inside the platform team inverts the responsibility split defined above and strips accountability away from the business authority who is supposed to hold it.

Allowing every deployment to bypass shared identity, evaluation and observability defeats the purpose of having a platform at all — a bypassed control is not a faster path to production, it is an unmanaged risk with a production system attached to it. Productizing unstable custom logic after only one implementation skips the repetition test this chapter's reuse bar depends on, and typically produces a shared component nobody else can safely build against. And measuring platform success only by API call volume, rather than by deployment speed, quality and outcome reuse, rewards the platform team for being used rather than for being useful — a metric that looks healthy right up until someone asks whether deployments are actually getting faster or better because of it.

---

[← Previous: Chapter 24: Roles, Teams and Governance Forums](chapter-24-roles-teams-and-governance-forums.md) · [Contents](../README.md) · [Next: Part V: Measurement, Scaling and Institutionalization →](part-v-measurement-scaling-and-institutionalization.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
