<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 14: Intelligence and Agent Engineering](chapter-14-intelligence-and-agent-engineering.md) · [Contents](README.md) · [Next: Chapter 16: Human–AI Workflow and Experience Engineering →](chapter-16-human-ai-workflow-and-experience-engineering.md)

# Chapter 15: Data and Knowledge Engineering

# Data and Knowledge Engineering

> **CHAPTER PURPOSE** Build governed, authorized and measurable data and knowledge services that supply sufficient, current and attributable context to the system.

## Knowledge-service lifecycle

41. Discover authoritative structured and unstructured sources, owners, classifications and permitted purposes.

42. Assess quality, coverage, freshness, granularity, lineage, licensing, privacy and access constraints.

43. Ingest and normalize with document structure, tables, metadata, identifiers and source relationships preserved.

44. Design retrieval using taxonomy, lexical and semantic search, filters, graph relationships or query tools as appropriate.

45. Assemble authorization-aware context and maintain citations to the original source and version.

46. Evaluate retrieval relevance, completeness, conflict handling, freshness and resistance to malicious or low-trust content.

47. Operate ingestion failures, access changes, source retirement, index refresh and correction workflows.

## Data and knowledge readiness

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

## Grounding policy

For knowledge-bound tasks, the system must define when it may answer from supplied sources, when model knowledge is permitted, how conflicts are handled, and the exact abstention or escalation behavior for insufficient evidence. Citation presence alone is not grounding; the cited passage must support the material claim.

## Failure modes

- Correct source not retrieved because metadata or query language is weak.

- Relevant source retrieved but excluded by token budget or context ordering.

- Stale or superseded source presented as current.

- Unauthorized source leaks through a shared index or cached response.

- Conflicting sources are merged without precedence or uncertainty.

- Embedded instructions in documents alter agent behavior.

- Chunking destroys tables, conditions, exceptions or parent-child relationships.

---

[← Previous: Chapter 14: Intelligence and Agent Engineering](chapter-14-intelligence-and-agent-engineering.md) · [Contents](README.md) · [Next: Chapter 16: Human–AI Workflow and Experience Engineering →](chapter-16-human-ai-workflow-and-experience-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](LICENSE.md).
