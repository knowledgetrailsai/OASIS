<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: Process Architecture](perspective-03-process-architecture.md) · [Architecture: Reference Architecture](oasis-reference-architecture.md#6-enterprise-architecture-perspectives) · [Next: Inference Architecture →](perspective-05-inference-architecture.md)

# Architecture Perspective 4: Information and Knowledge Architecture

> **PURPOSE** Define how enterprise knowledge and context are organized as a shared, governed asset — the enterprise-wide framing of the per-system [Context and Retrieval Engineering](../engineering/context-and-retrieval-engineering.md) article, for the domains, sources and access rules every intelligence system draws on.

**Primary OASIS source:** [Chapter 15 — Data and Knowledge Engineering](../methodology/chapter-15-data-and-knowledge-engineering.md); [Chapter 14 §3–4 — Data, retrieval and context](../methodology/chapter-14-intelligence-and-agent-engineering.md); [Chapter 25 — Enterprise Intelligence Platform](../methodology/chapter-25-enterprise-intelligence-platform.md).

## Background and context

[Context and Retrieval Engineering](../engineering/context-and-retrieval-engineering.md) specifies how one system assembles context for one task: ingestion, chunking, indexing, retrieval, and the authorization-aware, source-attributed, fresh, compressed context an individual harness consumes. That document is intentionally scoped to a single system's retrieval pipeline. This perspective is the layer above it: an enterprise typically has a small number of authoritative knowledge domains (product, policy, customer, case history, regulatory) that many systems need to draw on, and if each system builds its own independent ingestion and indexing pipeline against the same underlying source of truth, the enterprise ends up with as many divergent copies of "the current policy" as it has systems — each capable of drifting out of sync with the others and with the source of truth itself.

Information and Knowledge Architecture is the map of those enterprise knowledge domains, their authoritative source of truth, and the access rules that every system's context assembler must respect — so that "which system is authoritative for customer entitlement data" has one answer, not five.

## 1. Enterprise knowledge domain map

| Knowledge domain | Authoritative source of truth | Freshness requirement | Access classification | Consuming systems |
|---|---|---|---|---|
| | | | Public / Internal / Restricted / Regulated | |

## 2. Knowledge governance principles

| Principle | What it requires |
|---|---|
| One authoritative source per domain | Every knowledge domain names exactly one system of record; retrieval pipelines index from it, they do not become an alternate source of truth. |
| Access classification travels with the content | A retrieved passage carries its source classification into the context assembler, so authorization filtering (Ch.14 §4) can enforce it per request — this is the enterprise-scale mechanism behind the [Knowledge grounded](oasis-reference-architecture.md#architecture-principles) principle. |
| Freshness is a defined SLA, not an assumption | Each domain states an update cadence and a maximum staleness a consuming system may rely on before re-checking the source. |
| Attribution is preserved end to end | A generated output must be traceable to the specific source passage and its version — see [Context quality checklist](../engineering/context-and-retrieval-engineering.md#3-context-quality-checklist). |

## 3. Shared vs. system-specific knowledge

| Question | If yes | If no |
|---|---|---|
| Does more than one system need this domain? | Build/govern as a shared platform knowledge service (see [Chapter 25](../methodology/chapter-25-enterprise-intelligence-platform.md)). | Keep the retrieval pipeline scoped to the owning system per [Context and Retrieval Engineering](../engineering/context-and-retrieval-engineering.md). |
| Is the domain regulated (Ch.20, [Standards](../standards/))? | Register the domain's handling requirements in the relevant Standards checklist before any system indexes it. | Standard data-readiness review applies (see [Data and Knowledge Readiness Assessment](../methodology/chapter-32-templates-checklists-and-tools.md#8-data-and-knowledge-readiness-assessment)). |

## 4. Retirement and versioning

Knowledge domains change owners, get superseded, or get deprecated. Track domain-level version history the same way the [Monitoring specification](../monitoring/observability-and-telemetry-specification.md#2-trace-and-version-record-what-every-event-must-carry) tracks index versions per request — a domain migration is a release, and every consuming system's dependency on the old domain must be identified before cutover, not discovered after.

---

[← Back to Contents](../README.md) · [← Previous: Process Architecture](perspective-03-process-architecture.md) · [Architecture: Reference Architecture](oasis-reference-architecture.md#6-enterprise-architecture-perspectives) · [Next: Inference Architecture →](perspective-05-inference-architecture.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
