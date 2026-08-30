<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: Inference Architecture](perspective-05-inference-architecture.md) · [Architecture: Reference Architecture](oasis-reference-architecture.md#6-enterprise-architecture-perspectives) · [Next: Deployment Architecture →](perspective-07-deployment-architecture.md)

# Architecture Perspective 6: Integration Architecture

> **PURPOSE** Define how agents interact with enterprise systems and tools at the portfolio level — the enterprise-wide framing of the per-tool [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md), covering the shared catalogue, connector governance, and integration-pattern standards every system's tool contracts should draw from.

**Primary OASIS source:** [Chapter 17 — Enterprise Integration and Tool Engineering](../methodology/chapter-17-enterprise-integration-and-tool-engineering.md); [Chapter 25 — Enterprise Intelligence Platform](../methodology/chapter-25-enterprise-intelligence-platform.md).

**Companion repository:** [Helm](https://github.com/knowledgetrailsai/Helm) (`07-tool-integration/`) — light coverage of Chapter 17 exists there (tool-contract principles and one pattern catalogue); see the [Companion Repository Index](../References/companion-repository-index.md) for the known depth gap on this chapter.

## Background and context

The [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md) gives one tool a complete contract: inputs, authorization, limits, failure semantics. That's the right granularity for building one tool. It's the wrong granularity for answering a portfolio question: how many independent integrations does the enterprise have into the claims system, built by how many different teams, with how many different authorization models?

Without an integration architecture, every system re-integrates with the same enterprise systems of record from scratch. That multiplies both build cost and the number of independently-configured credentials and permission scopes attached to the same underlying system — each one a separate thing to secure, audit and revoke.

Integration Architecture is the enterprise catalogue and governance layer above individual tool contracts: which enterprise systems have agent-facing integrations at all, which pattern each uses, and — critically — a single place to answer "if we revoke this credential, which agents across the enterprise lose access to what?"

## 1. Enterprise integration catalogue

Helm's [integration patterns and tool catalogues](https://github.com/knowledgetrailsai/Helm/blob/main/07-tool-integration/integration-patterns-and-tool-catalogues.md) note covers the pattern column below in more depth.

| Enterprise system | Integration pattern (per Tool spec §3) | Consuming agents/tools | Credential/scope owner | Read / Prepare / Execute surface exposed |
|---|---|---|---|---|
| | Synchronous API / Event-driven / Queue-based / Managed connector / RPA | | | |

## 2. Shared connector governance

| Principle | What it requires |
|---|---|
| One integration per enterprise system per pattern, reused | A second team needing the same enterprise system's data extends the existing integration's tool catalogue rather than building a parallel one — see the [Composable and reusable](oasis-reference-architecture.md#architecture-principles) principle. |
| Centralized credential and scope registry | Every credential used by any agent-facing integration is registered centrally, with an owner who can revoke it immediately — this is what makes the Security checklist's containment procedures executable at enterprise scale, not just per system. |
| RPA is tracked as enterprise technical debt | Per the Tool specification, every RPA-backed integration names a migration owner and target pattern; this perspective rolls those up into a single enterprise RPA-retirement view reviewed at the same cadence as the technology roadmap. |
| MCP / standardized protocol adoption is a portfolio decision | Where the enterprise adopts a standardized tool protocol (e.g., MCP), register it once at the integration-architecture level (see [Tool spec §4](../engineering/tool-and-integration-interface-specification.md#4-mcp-tool-catalogue-registration-fields)) rather than leaving each system to decide independently whether to support it. |

## 3. Integration risk view

Roll up integration-level risk for governance review:

| Enterprise system | Data classification exposed | Number of consuming agents | Highest autonomy level with execute access | Last credential/scope audit |
|---|---|---|---|---|
| | | | | |

A system exposing execute-level access to more than a handful of independently-built agents is a concentration-risk signal worth an architecture review, even if every individual integration passed its own review.

## 4. Cross-references

- Per-tool contract detail: [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md).
- Tool-layer security controls: [Security: Threat and Control Checklist](../security/agentic-ai-threat-and-control-checklist.md).
- Platform-level integration investment: [Chapter 25 — Enterprise Intelligence Platform](../methodology/chapter-25-enterprise-intelligence-platform.md).

---

[← Back to Contents](../README.md) · [← Previous: Inference Architecture](perspective-05-inference-architecture.md) · [Architecture: Reference Architecture](oasis-reference-architecture.md#6-enterprise-architecture-perspectives) · [Next: Deployment Architecture →](perspective-07-deployment-architecture.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
