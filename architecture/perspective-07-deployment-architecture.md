<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: Integration Architecture](perspective-06-integration-architecture.md) · [Architecture: Reference Architecture](oasis-reference-architecture.md#6-enterprise-architecture-perspectives) · [Next: Security and Trust Architecture →](perspective-08-security-and-trust-architecture.md)

# Architecture Perspective 7: Deployment Architecture

> **PURPOSE** Define the broad placement of agentic workloads across cloud, on-premises, edge and regions — a perspective not otherwise covered by the per-system reference architecture, needed wherever data residency, latency, or sovereignty constraints affect where a component in the [system-equation diagram](oasis-reference-architecture.md#1-system-equation-as-a-diagram) is allowed to run.

**Primary OASIS source:** [Chapter 20 — Governance, Compliance and Regulatory Engineering](../methodology/chapter-20-governance-compliance-and-regulatory-engineering.md); [Chapter 21 — Deployment, Operations and AgentOps](../methodology/chapter-21-deployment-operations-and-agentops.md); [Regulatory and Standards Framework Alignment Index](../references/regulatory-framework-alignment-index.md).

**Companion repositories:** [Compass](https://github.com/knowledgetrailsai/responsible-ai) implements Chapter 20's jurisdiction-specific regulatory coverage (data residency and sovereignty obligations feed directly into this perspective's placement decisions); [Helm](https://github.com/knowledgetrailsai/Helm) implements Chapter 21's deployment and release-management practice.

## Background and context

Sections 1–5 of the reference architecture describe a *capability map, not a deployment topology* — each box is a responsibility, not a placement decision. That's correct for the per-system engineering view. But an enterprise operating across multiple jurisdictions cannot stay silent on placement indefinitely. Data residency rules (see the DPDP Act and EU AI Act checklists in [Standards](../standards/)), latency requirements for real-time workloads, and sovereign-cloud or on-premises mandates in regulated sectors all constrain *where* a component may physically execute, not just how it behaves logically. Deployment Architecture is the missing perspective that makes those placement constraints explicit and auditable, separate from the logical component design.

This is new content relative to the rest of this repository — no existing Engineering or Monitoring article addresses physical/regional placement. It sits at the intersection of infrastructure architecture (usually owned outside the AI delivery team) and the regulatory obligations this repository already indexes in Standards and References.

## 1. Placement decision table

For each component in the system-equation diagram (model layer, context/retrieval, tool execution, memory/state store, evaluation, runtime trace), record where it is permitted to run:

| Component | Permitted regions/environments | Data residency constraint | Latency requirement | Placement rationale |
|---|---|---|---|---|
| Model inference | | | | |
| Context/retrieval service | | | | |
| Memory/state store | | | | |
| Tool execution layer | | | | |
| Runtime trace / telemetry store | | | | |

## 2. Deployment topology patterns

| Pattern | Best fit when | Trade-off |
|---|---|---|
| Single-region cloud | No residency constraint, latency-tolerant workload, fastest to build and operate. | Concentration risk if the region has an outage; not viable where data must stay in-country. |
| Multi-region cloud, data-pinned | Enterprise serves multiple jurisdictions with different residency rules. | Higher operational complexity; requires the routing layer (see [Inference Architecture](perspective-05-inference-architecture.md)) to be region-aware. |
| On-premises / private cloud | Regulated sector mandate, or data classification too sensitive for third-party cloud model providers. | Limits model choice to what can be deployed or accessed on-prem; increases infrastructure ownership burden. |
| Edge | Latency-critical or intermittently-connected workload (e.g., field operations). | Constrains model size/complexity to what the edge device can run; harder to apply centralized guardrail updates quickly. |
| Hybrid | Most enterprises in practice — some components centralized, others regionally or on-prem placed per constraint. | Requires the placement decision table above to be maintained per component, not assumed uniform across the system. |

## 3. Sovereignty and residency checklist

For the jurisdiction-by-jurisdiction detail behind this checklist, see Compass's [regulatory comparison](https://github.com/knowledgetrailsai/responsible-ai/blob/main/10-regulations-and-standards/regulatory-comparison.md).

| # | Check | Evidence |
|---|---|---|
| 1 | Every component handling regulated data has a documented, approved region/environment | Placement decision table (§1) |
| 2 | Cross-border data transfer (if any) has a documented legal basis | See [DPDP Act checklist](../standards/dpdp-act-alignment-checklist.md), [EU AI Act checklist](../standards/eu-ai-act-alignment-checklist.md) |
| 3 | Model provider's own data-handling location matches the workload's residency requirement | [Inference Architecture — approved model registry](perspective-05-inference-architecture.md#1-approved-model-registry) |
| 4 | Disaster-recovery and failover placement also meets residency constraints (not just primary placement) | Deployment topology pattern selected (§2) |
| 5 | Placement decisions are reviewed when regulatory scope changes (new jurisdiction, new data type) | [Regulatory and Standards Framework Alignment Index](../references/regulatory-framework-alignment-index.md) |

## 4. Relationship to operations

Once deployed, ongoing placement compliance is monitored operationally rather than re-verified manually — see [Operations and Observability Architecture](perspective-09-operations-and-observability-architecture.md) and the [Monitoring specification](../monitoring/observability-and-telemetry-specification.md).

---

[← Back to Contents](../README.md) · [← Previous: Integration Architecture](perspective-06-integration-architecture.md) · [Architecture: Reference Architecture](oasis-reference-architecture.md#6-enterprise-architecture-perspectives) · [Next: Security and Trust Architecture →](perspective-08-security-and-trust-architecture.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
