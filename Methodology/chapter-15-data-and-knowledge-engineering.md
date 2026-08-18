<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 14: Intelligence and Agent Engineering](chapter-14-intelligence-and-agent-engineering.md) · [Contents](../README.md) · [Next: Chapter 16: Human–AI Workflow and Experience Engineering →](chapter-16-human-ai-workflow-and-experience-engineering.md)

# Chapter 15: Data and Knowledge Engineering

# Data and Knowledge Engineering

> **CHAPTER PURPOSE** Build governed, authorized and measurable data and knowledge services that supply sufficient, current and attributable context to the system — the discipline behind the evidence every intelligence system reasons over.

## Background and context

[Chapter 14 §3](chapter-14-intelligence-and-agent-engineering.md#3-data-retrieval-and-knowledge-foundations) introduced data, retrieval and knowledge foundations as one of the twelve disciplines that make up a complete intelligence system, and stated its governing principle in a single sentence: the goal is the smallest sufficient and authoritative evidence set, not the largest possible context. This chapter exists because that principle is easy to state and difficult to operate. In practice, teams that struggle with a fielded intelligence system are rarely struggling with the model — they are struggling with what the model was given to reason over. A source that was never discovered, a document chunked in a way that destroyed the table it depended on, an index that went stale without anyone noticing, an access-control gap that let restricted content leak into a shared response: these are data-engineering failures wearing a model-quality costume, and they account for a disproportionate share of the incidents that reach production.

This chapter and Chapter 14 §3 cover the same ground from different distances. Chapter 14 states data and retrieval as one layer among twelve in the system equation; this chapter gives that one layer the full treatment its practical weight deserves — the lifecycle a knowledge service moves through, the readiness bar it has to clear before a system can rely on it, the grounding policy that governs when the system may answer from its own knowledge versus supplied evidence, and the specific failure modes worth designing against deliberately rather than discovering in production. Two companion documents go deeper still into the mechanics this chapter describes at governance altitude: [Context and Retrieval Engineering](../engineering/context-and-retrieval-engineering.md) is the implementation-level companion for a single system's retrieval pipeline — ingestion, chunking, indexing, and the context-quality checklist a build team runs before release — and [Information and Knowledge Architecture](../architecture/perspective-04-information-and-knowledge-architecture.md) is the enterprise-wide view, mapping the knowledge domains a whole organization draws on so that five systems do not each build their own divergent copy of "the current policy." Where this chapter states a principle, those two documents are where a team turns it into a pipeline and a platform decision, respectively.

## Knowledge-service lifecycle

Treat the path from raw source material to authorized, attributable context in a running system as a lifecycle with distinct stages, not a one-time ingestion project — because sources, quality, and access requirements all keep changing after go-live, and a knowledge service that only handles the initial load will start drifting from day one.

It begins with discovery: identifying which structured and unstructured sources are actually authoritative for a given domain, who owns each one, what classification it carries, and what purposes it may legitimately be used for. Discovery is followed by an honest assessment of what was found — its quality, its coverage of the cases the system will actually face, its freshness, the granularity at which it is written, its lineage back to wherever it originated, any licensing constraints on its use, and the privacy and access constraints that travel with it. Only once a source has cleared that assessment does ingestion happen, and it has to preserve what assessment found worth preserving: document structure, tables, metadata, identifiers, and the relationships between a source and the other material it depends on or supersedes. What follows is retrieval design proper — choosing taxonomy, lexical search, semantic search, structured filters, graph relationships, or purpose-built query tools, in whatever combination the domain actually needs rather than defaulting to one technique because it is fashionable. The context assembled from that retrieval has to be authorization-aware from the moment it is built, and has to carry citations back to the original source and its version, not just a generic "source: knowledge base" label. None of this is worth building without evaluating it — relevance, completeness, how conflicting evidence is handled, freshness, and resistance to malicious or low-trust content all need to be measured on their own terms, independently of how good the model's eventual answers happen to look. And the lifecycle does not end at launch: ingestion failures, access changes, source retirement, index refresh, and correction workflows are ongoing operational responsibilities, not one-time setup tasks. [Context and Retrieval Engineering](../engineering/context-and-retrieval-engineering.md) turns each of these stages into a fillable pipeline specification — its retrieval-pipeline table and context-quality checklist are the direct implementation counterpart to this lifecycle.

## Data and knowledge readiness

Before a system is allowed to depend on a knowledge source in production, that source should clear a readiness bar across eight dimensions. Authority asks whether a source owner and a system of record can actually be named — a source nobody owns is a source nobody will notice going stale. Coverage asks whether representative workflow cases, not just the easy ones, have sufficient evidence behind them. Quality asks whether known errors, missing data, and ambiguity have actually been measured, rather than assumed away. Freshness asks whether the update frequency of the source matches how sensitive the decisions built on it are — a policy document reviewed annually is fine for some decisions and dangerously stale for others. Access asks whether entitlements can genuinely be enforced at the moment of retrieval and at the moment a tool acts, not just at the perimeter of the system. Lineage asks whether an output can be traced back to its source, the transformation it went through, and its version. Purpose asks whether the intended use is actually compatible with whatever consent, notice, contract, or policy governs the source. And operations asks whether corrections, deletions, source outages, and index refresh are supported as ongoing capabilities rather than gaps discovered the first time something goes wrong.

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

This table is the [Data and Knowledge Readiness Assessment](chapter-32-templates-checklists-and-tools.md#8-data-and-knowledge-readiness-assessment) in compact form, and is worth running honestly rather than optimistically — a source that is "mostly ready" on all eight dimensions is a weaker foundation than a smaller source that is genuinely ready on all eight, because the gaps compound rather than average out.

## Grounding policy

Citation presence alone is not grounding, and this distinction is worth being blunt about because it is one of the most common ways teams fool themselves into believing a system is more reliable than it is. A response with a citation attached looks grounded; it is only actually grounded if the cited passage supports the material claim being made, and it is entirely possible for a fluent model to attach a real, retrievable citation to a claim that citation does not actually support. For any knowledge-bound task, the system needs an explicit policy covering when it may answer purely from supplied sources, when — if ever — it is permitted to draw on the model's own general knowledge instead, how it handles sources that conflict with each other, and exactly what it does when the available evidence is insufficient: whether it abstains, states its uncertainty, or escalates to a human, and under what conditions each of those applies.

Writing this policy down forces a decision that is otherwise made implicitly, case by case, by whatever the model happens to do when it runs out of good evidence — which is precisely the moment a system's behavior is least predictable and most consequential to get right. The [context quality checklist](../engineering/context-and-retrieval-engineering.md#3-context-quality-checklist) in the companion engineering article is the pre-release test of whether this policy actually holds in practice, checking source attribution, freshness enforcement, and injection resistance directly rather than trusting the policy document alone.

## Failure modes

Several failure patterns recur often enough across fielded systems to be worth naming explicitly and designing against, rather than waiting to discover them individually. The correct source sometimes simply is not retrieved, because the metadata attached to it or the language of the query does not line up — a source can be perfectly authoritative and still invisible to a weak retrieval strategy. A source can be retrieved correctly and then excluded anyway, squeezed out by the token budget or buried by context ordering that prioritized something less relevant. Stale or superseded material can be presented as though it were current, particularly when freshness is checked at ingestion time but never re-checked at retrieval time. An index shared across use cases, or a cached response reused across requests, can leak content to a user who was never authorized to see it. Conflicting sources can be merged into a single answer with no indication of precedence or uncertainty, producing a confident response built on an unresolved contradiction. Documents can carry embedded instructions that alter agent behavior when retrieved — a live instance of the prompt-injection risk this methodology treats as a first-class threat, not an edge case. And chunking, done without attention to document structure, can quietly destroy the tables, conditions, exceptions, and parent-child relationships that gave a source its actual meaning, leaving retrieval technically successful and substantively wrong.

- Correct source not retrieved because metadata or query language is weak.

- Relevant source retrieved but excluded by token budget or context ordering.

- Stale or superseded source presented as current.

- Unauthorized source leaks through a shared index or cached response.

- Conflicting sources are merged without precedence or uncertainty.

- Embedded instructions in documents alter agent behavior.

- Chunking destroys tables, conditions, exceptions or parent-child relationships.

Each of these has a named countermeasure in the companion engineering article's context-quality checklist and retrieval evaluation template — the [Context and Retrieval Engineering §3 and §4](../engineering/context-and-retrieval-engineering.md#3-context-quality-checklist) sections test authorization-awareness, freshness, injection resistance, and retrieval precision/recall directly, and its failure-analysis template is designed to capture exactly this taxonomy of failure when it appears in evaluation. At the enterprise scale, several of these failures — particularly stale sources and unauthorized leakage — are symptoms of a deeper platform gap: no single owned pipeline per knowledge domain, which is the problem [Information and Knowledge Architecture](../architecture/perspective-04-information-and-knowledge-architecture.md) is designed to prevent by naming exactly one authoritative source of truth per domain and requiring every consuming system's retrieval pipeline to index from it rather than becoming an alternate source of truth in its own right.

---

[← Previous: Chapter 14: Intelligence and Agent Engineering](chapter-14-intelligence-and-agent-engineering.md) · [Contents](../README.md) · [Next: Chapter 16: Human–AI Workflow and Experience Engineering →](chapter-16-human-ai-workflow-and-experience-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
