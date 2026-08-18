<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 08: Phase 2 — Discover & Validate](chapter-08-phase-2-discover-and-validate.md) · [Contents](../README.md) · [Next: Chapter 10: Phase 4 — Activate & Adopt →](chapter-10-phase-4-activate-and-adopt.md)

# Chapter 09: Phase 3 — Engineer & Integrate

# Phase 3 — Engineer & Integrate

> **CHAPTER PURPOSE** Convert a validated vertical slice into a secure, reliable, observable, integrated and supportable production intelligence service.

## Background and context

Phase 2 answers whether intelligence can work; Phase 3 is where the organization commits to making it work reliably, at production scale, under real operating conditions and real adversarial pressure. The gap between those two things is larger than it looks from the outside. A vertical slice proved the concept on a curated set of representative cases with a small, forgiving user group; a production service has to survive the full, unfiltered variability of live traffic, integrate cleanly with the enterprise systems it depends on, degrade predictably when something upstream fails, and give the people who will support it at 2 a.m. enough visibility to know what went wrong without waking up the original build team.

This is deliberately the most engineering-dense phase in the lifecycle, and this chapter is intentionally light on the technical detail of how to do that engineering — that detail lives elsewhere in this handbook and is kept there rather than duplicated here. The [Architecture](../architecture/oasis-reference-architecture.md) folder's reference architecture is the structural backbone this phase builds against, and its ten [Architecture Principles](../architecture/oasis-reference-architecture.md#architecture-principles) — secure by design, observable by design, knowledge grounded, evidence gated, and the rest — are the judgment calls a Phase 3 team will make dozens of times without necessarily naming them explicitly. The six articles in the [Engineering](../engineering/) folder — covering model, context and retrieval, tool and integration, harness and orchestration, memory and state, and evaluation and reliability engineering — are the working-level specifications for each layer named in the method below. A reader arriving at this chapter to actually do Phase 3's work should treat it as a map to those documents, not a substitute for reading them.

What Phase 3 hands to [Phase 4 — Activate & Adopt](chapter-10-phase-4-activate-and-adopt.md) is not a live service but a service that has been proven ready to go live under controlled exposure — the distinction between "engineered correctly" and "actually working for real users" is exactly the gap the next phase exists to close.

## Phase objective

Create a secure, reliable, observable, scalable and supportable production intelligence service.

Each of those five adjectives corresponds to a body of engineering discipline this phase must apply, not just assert. "Secure" means the threat model in the [Security](../security/agentic-ai-threat-and-control-checklist.md) checklist has been worked through, not merely acknowledged. "Observable" means the trace and version record specified in the [Monitoring](../monitoring/observability-and-telemetry-specification.md#2-trace-and-version-record-what-every-event-must-carry) specification is actually being emitted, field by field, from the first release. "Supportable" is the adjective teams most often shortchange under deadline pressure — a system that only its original engineers can operate has not finished Phase 3, regardless of how well it performs.

## Core questions

- Can it operate safely across enterprise systems?

- Can failures be detected, contained and recovered?

- Can every material change be tested and rolled back?

- Is support ownership clear?

These four questions are the production-readiness bar stated as questions rather than a checklist, and they are ordered deliberately: safety and containment come before change management, and change management comes before ownership, because a system that cannot answer the first two honestly should not be released regardless of how clean its release process is. "Can failures be detected, contained and recovered" is worth dwelling on — detection without containment just produces a well-documented outage, and containment without recovery leaves the service stuck in a degraded state that someone eventually has to manually unwind.

## Method

17. Baseline the production architecture, system boundary, data flows, model and provider dependencies.

18. Engineer context, retrieval, harness, tools, workflow, memory, state, validation and human controls.

19. Implement identity, authorization, secrets, network, data protection, transaction limits and audit logging.

20. Automate evaluation, security, integration, resilience and regression tests in release pipelines.

21. Instrument end-to-end traces, quality measures, service measures, costs and outcome events.

22. Prepare runbooks, support model, fallback, rollback, recovery, capacity and operational acceptance evidence.

Step 18 is where most of the actual engineering effort concentrates, and each of its components maps to one article in the Engineering folder: context and retrieval to [Context and Retrieval Engineering](../engineering/context-and-retrieval-engineering.md), harness and orchestration to [Harness and Orchestration Engineering](../engineering/harness-and-orchestration-engineering.md), tools to the [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md), and memory and state to [Memory and State Engineering](../engineering/memory-and-state-engineering.md). Step 19's security controls should be checked directly against the [Security checklist's](../security/agentic-ai-threat-and-control-checklist.md#1-defense-in-depth-control-layers-ch-19-mapped-to-owasp-llm-top-10) defense-in-depth layers rather than reconstructed from memory. Step 20's automated evaluation suite is the production-grade successor to the evaluation dataset built in Phase 2, and its design principles are covered in [Evaluation and Reliability Engineering](../engineering/evaluation-and-reliability-engineering.md). None of this is optional scaffolding around the "real" engineering work — it is the engineering work, and a service that skips steps 20 through 22 to hit a launch date is deferring their cost to the first production incident, at a much higher price.

## Primary artifacts

- Intelligence-System Blueprint

- Production Architecture

- Tool and Integration Contracts

- Threat and Control Model

- Automated Evaluation Suite

- Production Readiness Checklist

- Service Runbook

- Release and Rollback Plan

The Intelligence-System Blueprint is template 11 in [System and Governance Templates](../tools/03-system-and-governance-templates.md#11-intelligence-system-blueprint), and it is deliberately structured around the reference architecture's [component-to-artifact map](../architecture/oasis-reference-architecture.md#2-component-to-artifact-map) so that a completed blueprint and the architecture diagram describe the same system in the same terms. The Production Readiness Checklist is template 13 in [Readiness and Operations Templates](../tools/04-readiness-and-operations-templates.md#13-production-readiness-checklist), and it is the artifact the Production Readiness Review below is actually run against — its rows pull directly from the security checklist, the standards checklists applicable to the data in scope, and the monitoring specification's release-manifest checklist.

> **DECISION OUTCOME** Production Readiness Review: release into controlled activation, remediate or hold.

## Entry and exit conditions

| **Entry condition**                                                  | **Exit condition**                                                             |
|------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| A representative vertical slice has met agreed viability thresholds. | The service is secure, observable, recoverable, supportable and release-ready. |

The exit condition is worth reading literally: "release-ready" is not the same claim as "released." Phase 3 proves the service is safe to expose to real users under controlled conditions; it does not itself expose them. That handoff, and the progressive widening of exposure that follows it, belongs to Phase 4.

## Tailoring guidance

Small deployments may use managed platform defaults and one service owner. High-impact systems require explicit segregation, resilience targets, independent testing and trace retention.

The tailoring lever here is proportional to blast radius, not to project size. A low-stakes internal tool operating on a managed platform can inherit most of that platform's defaults and lean on a single accountable owner. A system that can take irreversible action, touch regulated data, or affect customers directly should not inherit defaults it hasn't verified — it needs the independent testing and extended trace retention that let an incident review reconstruct exactly what happened, months later if necessary.

---

[← Previous: Chapter 08: Phase 2 — Discover & Validate](chapter-08-phase-2-discover-and-validate.md) · [Contents](../README.md) · [Next: Chapter 10: Phase 4 — Activate & Adopt →](chapter-10-phase-4-activate-and-adopt.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
