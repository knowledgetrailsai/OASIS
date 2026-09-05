<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 14: Intelligence and Agent Engineering](chapter-14-intelligence-and-agent-engineering.md) · [Contents](../README.md) · [Next: Chapter 16: Human–AI Workflow and Experience Engineering →](chapter-16-human-ai-workflow-and-experience-engineering.md)

# Chapter 15: Data and Knowledge Engineering

> **Implementation companion:** [Forge](https://github.com/knowledgetrailsai/Forge).


> **CHAPTER PURPOSE** Build governed, authorized and measurable data and knowledge services that supply sufficient, current and attributable context to the system — the discipline behind the evidence every intelligence system reasons over.

## Background and context

[Chapter 14 §3](chapter-14-intelligence-and-agent-engineering.md#3-data-retrieval-and-knowledge-foundations) introduced data, retrieval and knowledge foundations as one of twelve disciplines in a complete intelligence system, and stated its governing principle: the goal is the smallest sufficient and authoritative evidence set, not the largest possible context. That principle is easy to state and hard to operate.

Teams struggling with a fielded system are rarely struggling with the model. They are struggling with what the model was given to reason over. A source never discovered, a document chunked in a way that destroyed a table it depended on, an index gone stale unnoticed, an access-control gap that leaked restricted content: these are data-engineering failures wearing a model-quality costume, and they account for a large share of production incidents.

This chapter gives that layer full treatment: the lifecycle a knowledge service moves through, the readiness bar it must clear, the grounding policy governing self-knowledge versus supplied evidence, and the failure modes worth designing against.

Two companion documents go deeper. [Context and Retrieval Engineering](../engineering/context-and-retrieval-engineering.md) is the implementation-level companion for a single system's retrieval pipeline. [Information and Knowledge Architecture](../architecture/perspective-04-information-and-knowledge-architecture.md) is the enterprise-wide view, mapping the knowledge domains an organization draws on so five systems don't each build their own divergent copy of "the current policy." Forge's [Knowledge-Service Lifecycle overview](https://github.com/knowledgetrailsai/Forge/blob/main/02-knowledge-service-lifecycle/lifecycle-overview.md) is this chapter's step-by-step implementation companion.

## Knowledge-service lifecycle

Treat the path from raw source material to authorized, attributable context as a lifecycle with distinct stages, not a one-time ingestion project. Sources, quality, and access requirements keep changing after go-live, so a knowledge service that only handles the initial load starts drifting from day one.

It begins with [discovery and assessment](https://github.com/knowledgetrailsai/Forge/blob/main/02-knowledge-service-lifecycle/discovery-and-assessment.md): which sources are actually authoritative, who owns each one, what classification it carries, and what purposes it may legitimately serve. Next comes an honest assessment — quality, coverage of real cases, freshness, granularity, lineage, licensing, and privacy and access constraints.

Only once a source clears assessment does [ingestion](https://github.com/knowledgetrailsai/Forge/blob/main/02-knowledge-service-lifecycle/ingestion-and-structure.md) happen, preserving document structure, tables, metadata, identifiers, and relationships to other material. Then [retrieval design](https://github.com/knowledgetrailsai/Forge/blob/main/02-knowledge-service-lifecycle/retrieval-pipeline-design.md): choosing taxonomy, lexical search, semantic search, structured filters, graph relationships, or purpose-built query tools, in whatever combination the domain needs. Assembled context must be authorization-aware from the moment it's built, and carry citations back to the original source and version, not a generic "source: knowledge base" label.

None of this is worth building without evaluating it — relevance, completeness, conflict handling, freshness, and resistance to malicious content, measured independently of how good the model's eventual answers look. The lifecycle doesn't end at launch: [ongoing operations](https://github.com/knowledgetrailsai/Forge/blob/main/02-knowledge-service-lifecycle/evaluation-and-ongoing-operations.md) — ingestion failures, access changes, source retirement, index refresh, and correction workflows — are ongoing responsibilities. [Context and Retrieval Engineering](../engineering/context-and-retrieval-engineering.md) turns each stage into a fillable pipeline specification.

## Data and knowledge readiness

Before a system depends on a knowledge source in production, it should clear a readiness bar across eight dimensions: authority (a named owner and system of record — an unowned source goes stale unnoticed), coverage (evidence behind representative cases, not just easy ones), quality (errors, gaps, and ambiguity actually measured), freshness (update frequency matching decision sensitivity), access (entitlements enforced at retrieval and tool time, not just the perimeter), lineage (outputs traceable to source, transformation, and version), purpose (use compatible with consent, notice, contract, and policy), and operations (corrections, deletions, outages, and index refresh as ongoing capabilities, not gaps found when something breaks).

| **Dimension** | **Ready when…**                                                         |
|---------------|-------------------------------------------------------------------------|
| Authority     | A source owner and system of record are identifiable.                   |
| Coverage      | Representative workflow cases have sufficient evidence.                 |
| Quality       | Known errors, missingness and ambiguity are measured.                   |
| Freshness     | Update frequency matches decision sensitivity.                          |
| Access        | Entitlements can be enforced at retrieval and tool time.                |
| Lineage       | Outputs can be traced to source, transformation and version.            |
| Purpose       | Use is compatible with consent, notice, contract and policy.            |
| Operations    | Corrections, deletions, source outages and index refresh are supported. |

This table is the [Data and Knowledge Readiness Assessment](chapter-32-templates-checklists-and-tools.md#8-data-and-knowledge-readiness-assessment) in compact form, and Forge's [readiness dimensions](https://github.com/knowledgetrailsai/Forge/blob/main/03-readiness-assessment/readiness-dimensions.md) turn it into a scored rubric with pass thresholds. Run it honestly. A source "mostly ready" on all eight dimensions is a weaker foundation than a smaller source genuinely ready on all eight, because gaps compound rather than average out.

### Governance runs on the agent's clock, not the audit calendar

Readiness is a point-in-time bar. Once a system is live, agents consume this data continuously, not on the quarterly or annual cycle most data-governance programs were designed around. A quality check that runs monthly against a source agents query every minute is a structural mismatch, not a minor lag — by the time the check catches a problem, agents have already acted on bad data thousands of times. Treat the Quality, Access and Operations dimensions above as standing pipeline behavior, not periodic review: automated quality checks on every write, lineage tracked as data moves rather than reconstructed after the fact, and access entitlements re-evaluated continuously rather than certified once a quarter. Forge's [governance principles](https://github.com/knowledgetrailsai/Forge/blob/main/05-enterprise-knowledge-architecture/governance-principles.md) and [evaluation and ongoing operations](https://github.com/knowledgetrailsai/Forge/blob/main/02-knowledge-service-lifecycle/evaluation-and-ongoing-operations.md) cover what this looks like built into a live pipeline.

## Grounding policy

Citation presence alone is not grounding — a common way teams fool themselves into believing a system is more reliable than it is. A response with a citation looks grounded, but it's only actually grounded if the cited passage supports the claim being made. A fluent model can attach a real, retrievable citation to a claim it doesn't support.

Any knowledge-bound task needs an explicit policy: when the system may answer purely from supplied sources; when, if ever, it may draw on the model's own general knowledge; how it handles conflicting sources; and what it does when evidence is insufficient — abstain, state uncertainty, or escalate, and under what conditions each applies.

Writing this down forces a decision otherwise made implicitly by whatever the model does when it runs out of good evidence — the moment behavior is least predictable and most consequential. The [context quality checklist](../engineering/context-and-retrieval-engineering.md#3-context-quality-checklist) is the pre-release test of whether the policy holds in practice. Forge's [grounding policy](https://github.com/knowledgetrailsai/Forge/blob/main/04-grounding-and-context-quality/grounding-policy.md) works the same test with a concrete method: an NLI entailment check that scores whether a cited passage actually supports the claim, plus a worked example and a fillable policy template.

## Failure modes

Several failure patterns recur often enough to be worth naming and designing against, rather than discovering individually:

- [Correct source not retrieved](https://github.com/knowledgetrailsai/Forge/blob/main/06-failure-modes/failure-modes-and-countermeasures.md#1-correct-source-not-retrieved-because-metadata-or-query-language-is-weak) because metadata or query language is weak.

- [Relevant source retrieved but excluded](https://github.com/knowledgetrailsai/Forge/blob/main/06-failure-modes/failure-modes-and-countermeasures.md#2-relevant-source-retrieved-but-excluded-by-token-budget-or-context-ordering) by token budget or context ordering.

- [Stale or superseded source](https://github.com/knowledgetrailsai/Forge/blob/main/06-failure-modes/failure-modes-and-countermeasures.md#3-stale-or-superseded-source-presented-as-current) presented as current.

- [Unauthorized source leaks](https://github.com/knowledgetrailsai/Forge/blob/main/06-failure-modes/failure-modes-and-countermeasures.md#4-unauthorized-source-leaks-through-a-shared-index-or-cached-response) through a shared index or cached response.

- [Conflicting sources are merged](https://github.com/knowledgetrailsai/Forge/blob/main/06-failure-modes/failure-modes-and-countermeasures.md#5-conflicting-sources-are-merged-without-precedence-or-uncertainty) without precedence or uncertainty.

- [Embedded instructions in documents](https://github.com/knowledgetrailsai/Forge/blob/main/06-failure-modes/failure-modes-and-countermeasures.md#6-embedded-instructions-in-documents-alter-agent-behavior) alter agent behavior.

- [Chunking destroys structure](https://github.com/knowledgetrailsai/Forge/blob/main/06-failure-modes/failure-modes-and-countermeasures.md#7-chunking-destroys-tables-conditions-exceptions-or-parent-child-relationships): tables, conditions, exceptions or parent-child relationships.

Each has a named countermeasure in the companion article's context-quality checklist and retrieval evaluation template — [Context and Retrieval Engineering §3 and §4](../engineering/context-and-retrieval-engineering.md#3-context-quality-checklist) test authorization-awareness, freshness, injection resistance, and retrieval precision/recall directly. At enterprise scale, several of these failures — particularly stale sources and unauthorized leakage — are symptoms of a deeper gap: no single owned pipeline per knowledge domain. [Information and Knowledge Architecture](../architecture/perspective-04-information-and-knowledge-architecture.md) prevents this by naming one authoritative source of truth per domain and requiring every consuming system to index from it rather than become an alternate source of truth.

---

[← Previous: Chapter 14: Intelligence and Agent Engineering](chapter-14-intelligence-and-agent-engineering.md) · [Contents](../README.md) · [Next: Chapter 16: Human–AI Workflow and Experience Engineering →](chapter-16-human-ai-workflow-and-experience-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
