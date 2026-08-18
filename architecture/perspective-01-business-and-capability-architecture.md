<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Architecture: Reference Architecture](oasis-reference-architecture.md#6-enterprise-architecture-perspectives) · [Next: Agent Architecture →](perspective-02-agent-architecture.md)

# Architecture Perspective 1: Business and Capability Architecture

> **PURPOSE** Define what agentic capabilities the enterprise needs, as a durable capability map independent of any single system, model or vendor — the artifact a portfolio owner uses to decide what to build next, retire, or consolidate, distinct from any single [Opportunity Assessment](../Methodology/chapter-32-templates-checklists-and-tools.md#1-opportunity-assessment) or [Intelligence-System Blueprint](../Methodology/chapter-32-templates-checklists-and-tools.md#11-intelligence-system-blueprint).

**Primary OASIS source:** [Chapter 5 — Opportunity Portfolio and Transformation Horizons](../Methodology/chapter-05-opportunity-portfolio-and-transformation-horizons.md); [Chapter 3 — Enterprise AI Transformation Direction](../Methodology/chapter-03-enterprise-ai-transformation-direction.md); [Chapter 28 — Scaling and Productization](../Methodology/chapter-28-scaling-and-productization.md).

## Background and context

Every other perspective in this series (Agent, Process, Information, Inference, Integration, Deployment, Security, Operations) answers "how" a capability is delivered. This one answers "what" and "why" first, because an enterprise that jumps straight to agent design without a capability map ends up with as many disconnected agent implementations as it has business units — each solving a locally-scoped problem, none reusable, none comparable on value or risk. Business and Capability Architecture is the durable layer: a capability ("resolve a customer service inquiry", "underwrite a claim", "reconcile an account") persists even as the systems implementing it change model, vendor, or architecture underneath. Chapter 5's opportunity portfolio and horizon model already gives OASIS a way to inventory and prioritize opportunities; this perspective turns that inventory into an architectural artifact — a capability map that the enterprise-wide agent taxonomy (Perspective 2), process ownership model (Perspective 3), and platform investment decisions (Chapter 25, Chapter 28) all read from.

Treat this as the layer that answers a specific, recurring executive question badly served by a spreadsheet of individual initiatives: "across everything we're building, which capabilities do we have once, which do we have five redundant versions of, and which outcome-critical capability do we not have at all?" A capability map makes duplication and gaps visible in a way a project list does not.

## 1. Capability map template

One row per distinct business capability the enterprise either has, is building, or has identified as needed. A capability is defined by the outcome it produces, not by the team or system that currently implements it.

| Capability | Business outcome it serves | Maturity horizon (Ch.5) | Current implementation(s) | Owning function | Reuse potential |
|---|---|---|---|---|---|
| | | Horizon 1 / 2 / 3 | | | High / Medium / Low |
| | | | | | |

## 2. Capability classification

| Dimension | Question it answers | Why it matters architecturally |
|---|---|---|
| Autonomy ceiling | What is the highest autonomy level this capability is permitted to reach, per its risk classification? | Sets an upper bound the Agent Architecture (Perspective 2) and Progressively Autonomous principle must respect regardless of technical feasibility. |
| Reuse scope | Is this capability specific to one process, shared across a function, or a platform-level primitive? | Determines whether it belongs in a single system's Intelligence-System Blueprint or in the [Enterprise Intelligence Platform](../Methodology/chapter-25-enterprise-intelligence-platform.md). |
| Data dependency | What enterprise knowledge domains does this capability require (see Perspective 4)? | Flags capabilities blocked on data/knowledge readiness before any engineering work starts. |
| Regulatory exposure | Which [Standards](../standards/) checklists apply to this capability? | Routes the capability to the correct compliance review path before build, not after. |

## 3. Capability portfolio view

A capability map is only useful maintained as a portfolio, reviewed at the same governance cadence as the rest of the opportunity portfolio (Chapter 27). At minimum, review quarterly:

- Which capabilities moved horizon (1→2→3) since the last review, per [Chapter 5](../Methodology/chapter-05-opportunity-portfolio-and-transformation-horizons.md)'s horizon model.
- Which capabilities have more than one active implementation, and whether consolidation is now justified (see [Scale and Productization Assessment](../Methodology/chapter-32-templates-checklists-and-tools.md#20-scale-and-productization-assessment)).
- Which capabilities are named in the Outcome Portfolio but have no current implementation — the gap list for the next planning cycle.

## 4. Relationship to system-level artifacts

This capability map is upstream of, and does not replace, per-system artifacts. One capability may be served by one Intelligence-System Blueprint (small scope) or decomposed across several (large scope, e.g. a "resolve a customer inquiry" capability implemented as a routing agent plus several specialist agents — see [Agent Architecture](perspective-02-agent-architecture.md)). Do not populate this map at the level of individual tools or prompts; if a row looks like a tool contract, it belongs in the [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md) instead.

---

[← Back to Contents](../README.md) · [Architecture: Reference Architecture](oasis-reference-architecture.md#6-enterprise-architecture-perspectives) · [Next: Agent Architecture →](perspective-02-agent-architecture.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
