<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 10: Phase 4 — Activate & Adopt](chapter-10-phase-4-activate-and-adopt.md) · [Contents](../README.md) · [Next: Chapter 12: Phase 6 — Optimize & Scale →](chapter-12-phase-6-optimize-and-scale.md)

# Chapter 11: Phase 5 — Operate & Assure

# Phase 5 — Operate & Assure

> **CHAPTER PURPOSE** Sustain service health, intelligence quality, controls and business outcomes through monitoring, incident management and continuous assurance.

## Background and context

Phase 4 earns a service its initial operating authority; Phase 5 is where that authority has to be continuously re-earned, because nothing about a production intelligence system stays still once it is live. The knowledge it retrieves goes stale, the model behind it is upgraded or deprecated by a provider outside the organization's control, the workflow it serves gets redesigned around it, and the population of users interacting with it changes in ways that shift what "normal" input even looks like. Phase 5 is the longest-running phase in the lifecycle by a wide margin — most systems spend years here — and its job is to keep the outcome, the intelligence quality and the controls all within agreed limits despite that constant drift.

This is the phase where the monitoring and security material in this handbook stops being design guidance and becomes an operating discipline. The [Observability and Telemetry Specification](../monitoring/observability-and-telemetry-specification.md#1-the-six-operational-planes-instrumented) defines the six operational planes — service, intelligence, risk, human, economic and outcome — that a healthy operating rhythm monitors together, because a service that looks healthy on the service plane (uptime, latency) can simultaneously be failing badly on the intelligence plane (accuracy, groundedness) or the risk plane (control breaches), and a monitoring practice that only watches one plane will miss the others until a customer or a regulator finds them first. The [Agentic AI Threat and Control Checklist](../security/agentic-ai-threat-and-control-checklist.md#4-containment-and-emergency-control-checklist) is where the containment and emergency-control procedures this phase relies on during an incident are specified in full.

Phase 5 feeds [Phase 6 — Optimize & Scale](chapter-12-phase-6-optimize-and-scale.md) its raw material: the accumulated production evidence — what failed, what drifted, what users actually did with the system — that makes optimization and scale decisions evidenced rather than speculative. A system that has not been operated with real assurance discipline gives Phase 6 nothing reliable to optimize against.

## Phase objective

Sustain service health, intelligence quality, control effectiveness and business outcomes within agreed limits.

"Sustain" is doing real work in that sentence. It does not mean "leave alone" — a system left alone degrades, because the world around it keeps changing even when the system itself doesn't. Sustaining health means an active practice of monitoring, incident response and periodic reassessment substantial enough to catch degradation before it becomes visible to the business, rather than after.

## Core questions

- Is the outcome being delivered consistently?

- Where are users intervening and why?

- Are controls effective and proportionate?

- Has any component, data source, user behavior or external obligation changed?

The second question is one of the more diagnostically useful ones in the whole methodology. Where and why users override or escalate a system's output is one of the richest sources of evidence about where it is actually failing — often richer than any automated metric, because human intervention concentrates exactly at the cases the system handles worst. A team that does not systematically capture and analyze intervention patterns is discarding its best source of information about how to improve the system.

## Method

29. Monitor outcome, adoption, intelligence quality, risk, reliability, cost and intervention as connected layers.

30. Triage incidents using complete traces and classify root cause across the full intelligence system.

31. Manage knowledge freshness, model and prompt versions, tools, access, capacity, vendors and dependencies.

32. Sample completed work for quality and control testing; reconcile operational metrics with business outcomes.

33. Convert failures, overrides, complaints and near misses into evaluation cases and corrective actions.

34. Conduct service, outcome and compliance reviews; renew, re-scope, remediate or suspend as evidence dictates.

Step 29's instruction to monitor these layers "as connected" rather than separately is the practical antidote to the false-comfort problem described above. Step 30's incident triage depends entirely on the trace and version record specified in the [Monitoring specification](../monitoring/observability-and-telemetry-specification.md#2-trace-and-version-record-what-every-event-must-carry) — an incident that cannot be reconstructed from a complete trace turns into a guessing exercise, and root-cause classification against the [responsible-layer incident taxonomy](../monitoring/observability-and-telemetry-specification.md#4-incident-classification-responsible-layer-taxonomy) is what keeps that guessing from happening. Step 33 closes what is probably the single most important loop in this phase: every production failure, override and near miss that never becomes a regression case in the evaluation suite is a lesson the system will have to relearn the hard way, in production, more than once.

## Primary artifacts

- Outcome and Assurance Scorecard

- Service Runbook

- Incident and Problem Records

- Drift and Change Register

- Control Evidence Pack

- Learning Backlog

- Monthly Outcome Review

The Outcome and Assurance Scorecard corresponds to the Outcome Scorecard, template 15 in [Readiness and Operations Templates](../tools/04-readiness-and-operations-templates.md#15-outcome-scorecard), and its dimensions map onto the six operational planes from the Monitoring specification. The Service Runbook is template 16 in the same file, [Readiness and Operations Templates](../tools/04-readiness-and-operations-templates.md#16-service-runbook) — it is the document the on-call team actually opens during an incident, and it should never be rebuilt from scratch after go-live; step 22 of Phase 3 already produced it. The Control Evidence Pack draws on the Risk and Control Register, template 17 in [Risk and Scale Templates](../tools/05-risk-and-scale-templates.md#17-risk-and-control-register), which is deliberately the single shared risk register the [Standards](../standards/) checklists and the Security checklist all reference rather than duplicate.

> **DECISION OUTCOME** Outcome Performance Review: continue, correct, re-scope, reduce authority or retire.

## Entry and exit conditions

| **Entry condition**                                                                 | **Exit condition**                                                 |
|------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| The live service has an accepted owner, runbook, monitoring and authority boundary. | Performance is controlled and a traceable learning loop is active. |

There is no fixed calendar exit from Phase 5 in the way the other phases have one — a healthy service can remain in this phase indefinitely, cycling through monitoring and review, until either a problem forces a reduction in authority or an accumulation of evidence justifies moving into Phase 6's optimization and scale work.

## Tailoring guidance

Cadence follows volatility and consequence. A stable internal assistant may be reviewed monthly; a safety- or customer-critical action system may require continuous alerts and daily controls.

The right operating cadence is not a matter of organizational preference, it is a matter of how fast things can go wrong and how bad it would be if they did. A low-stakes internal tool with a stable knowledge base and a forgiving user base can be reviewed on a monthly rhythm without meaningful risk. A system that can take irreversible customer-facing action, or that operates in a domain where regulatory obligations shift, needs continuous alerting and daily control checks, because the cost of discovering a problem a month late is not proportional in the two cases.

---

[← Previous: Chapter 10: Phase 4 — Activate & Adopt](chapter-10-phase-4-activate-and-adopt.md) · [Contents](../README.md) · [Next: Chapter 12: Phase 6 — Optimize & Scale →](chapter-12-phase-6-optimize-and-scale.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
