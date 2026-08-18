<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 20: Governance, Compliance and Regulatory Engineering](chapter-20-governance-compliance-and-regulatory-engineering.md) · [Contents](../README.md) · [Next: Chapter 22: Economics, FinOps and Sustainability →](chapter-22-economics-finops-and-sustainability.md)

# Chapter 21: Deployment, Operations and AgentOps

# Deployment, Operations and AgentOps

> **CHAPTER PURPOSE** Run intelligence systems as production services with versioning, tracing, quality monitoring, incident response, rollback and learning loops.

## Background and context

Chapters 19 and 20 build and govern the controls a system needs before it can be trusted to run. This chapter is where those controls meet production reality: the point at which a system stops being something a team evaluates and starts being something real users depend on, continuously, under conditions no pre-release test suite fully anticipates. Deployment, Operations and AgentOps exists because running an intelligence system safely is a distinct discipline from building one correctly — a system that passed every evaluation and every governance review can still fail in production if nobody can answer, at 2 a.m. during an incident, which model, prompt and context version actually produced the output someone is now escalating.

AgentOps is this chapter's coinage, and the name matters: it names an extension of DevOps and MLOps to the behavior of complete intelligence systems, not a replacement for either. DevOps-era monitoring answers whether a service is up, fast and error-free; MLOps adds offline model-quality tracking on top of that. Neither tradition, on its own, accounts for the property that makes an agentic system different from either a conventional application or a static model: the same request can take a different path through models, retrieval, tools and human approval each time, decided dynamically by the system itself. That property is what makes service-plane monitoring alone insufficient — it can tell you whether a request succeeded, but not why an outcome was good or bad — and it is why this chapter defines six operational planes rather than treating AI monitoring as conventional monitoring with an extra dashboard bolted on.

This chapter's placement is deliberate on both sides. It follows Chapter 20 because the governance discipline established there — accountable owners, retained evidence, a traceable obligation-to-control chain — is exactly what production operations has to sustain continuously rather than demonstrate once at a point-in-time review; a release manifest and an incident record are, in effect, governance evidence generated automatically as a byproduct of running the system well. It precedes Chapter 22 because every operational plane instrumented here — particularly the economic plane — is the raw telemetry Chapter 22's unit-economics and FinOps discipline depends on; you cannot calculate a cost per successful outcome without the trace and cost data this chapter's instrumentation produces.

The direct implementation companion for everything in this chapter is the [Monitoring: Observability and Telemetry Specification](../monitoring/observability-and-telemetry-specification.md), which turns the six operational planes below into concrete metrics, collection points and alert triggers, defines the exact trace_event schema every logged decision must carry, specifies the release manifest checklist referenced under version management, and lays out the incident classification taxonomy and production learning loop in full operational detail. At enterprise scale, where a single organization runs many such systems at once, [Architecture Perspective 9 — Operations and Observability Architecture](../architecture/perspective-09-operations-and-observability-architecture.md) is the portfolio-level rollup — aggregate dashboards across every deployed system, enterprise-wide incident response for failures in a shared component, and the tiered kill-switch authority that governs containment above any single system's own runbook.

## Production operating model

AgentOps extends DevOps and MLOps to the behavior of complete intelligence systems. It must show which prompt, context policy, knowledge version, model, tool, workflow, control and user authority produced an outcome. Monitoring joins service telemetry with quality sampling and business events.

| **Operational plane** | **Measures and controls**                                                                                  |
|-----------------------|------------------------------------------------------------------------------------------------------------|
| Service               | Availability, latency, throughput, errors, queue depth, capacity and dependency health.                    |
| Intelligence          | Correctness, grounding, retrieval, tool choice, completion, abstention and escalation.                     |
| Risk                  | Unauthorized attempts, incorrect actions, policy violations, complaints, near misses and control failures. |
| Human                 | Adoption, overrides, approval time, exception load, rework and workaround behavior.                        |
| Economic              | Tokens, model and infrastructure cost, tool cost, intervention and cost per successful outcome.            |
| Outcome               | Primary result, leading indicators, guardrails and distribution across segments.                           |

Each plane exists because a healthy reading on the plane above it does not imply a healthy reading here. A service can be perfectly available and fast — every request answered within its latency budget — while the intelligence plane is quietly producing ungrounded, confidently wrong answers that no service-level dashboard would ever surface; this is the specific failure mode that makes intelligence-plane instrumentation non-optional rather than a nice-to-have. The risk plane exists because a system can be intelligent and available while still doing something it was never authorized to do — an unauthorized action attempt or a guardrail bypass is a distinct category of event from a quality miss, and it deserves its own zero-tolerance alerting rather than being buried inside a general error rate. The human plane captures the reality that adoption and trust are earned continuously, not granted once at launch — a rising override rate or a growing pattern of workaround behavior is often the earliest available signal that something upstream has quietly degraded, well before it shows up as a measurable outcome miss. Economic and outcome planes close the loop by asking the two questions every other plane serves: what does it cost to produce this result, and did the result actually move the business metric the system was built to move.

The [Monitoring specification's instrumentation of all six planes](../monitoring/observability-and-telemetry-specification.md#1-the-six-operational-planes-instrumented) gives each row here a representative metric, a collection point and an example alert trigger — the concrete answer to "measure what, from where, and alert on what threshold" that this table intentionally leaves open at the methodology level, since the right threshold is specific to a system's risk classification and cannot be set generically.

## Version and release management

- Immutable release manifest across model, prompt, context, index, tool, workflow, schema and control versions.

- Automated regression, security, integration and policy tests before release.

- Canary, cohort, shadow or percentage rollout with measurable stop conditions.

- Model-provider change detection and fallback compatibility.

- Rollback or forward-fix decision based on blast radius and state compatibility.

- Change communication to users, operations, risk owners and affected business processes.

Version management exists to answer, with certainty rather than reconstruction, the first question every incident review asks: what changed. An intelligence system has materially more moving, independently-versioned parts than a conventional application — a model, a prompt, a context policy, a knowledge index, a tool schema, a workflow definition and a control policy set can each change independently of the others, and a release that bundles several of those changes at once makes it genuinely difficult to isolate which one caused a regression if something goes wrong. An immutable release manifest is the discipline that prevents that ambiguity: every release records exactly which version of each component produced it, so a regression can be traced to a specific change rather than debated among several plausible candidates.

Rollout strategy and the rollback-versus-forward-fix decision deserve to be made in advance, not improvised under the pressure of an active incident — a canary or shadow rollout with defined stop conditions catches a regression against a small, contained population before it reaches everyone, and pre-agreeing the criteria for rolling back versus fixing forward (largely a function of blast radius and whether in-flight state remains compatible with the previous version) removes a high-stakes judgment call from the worst possible moment to make one well. Model-provider change detection matters for a reason specific to this domain: a system's primary model can change behavior — sometimes materially — through a provider-side update the build team never initiated, and a system with no detection for that has no way to distinguish "we changed something" from "the model changed under us." The [Monitoring specification's release manifest checklist](../monitoring/observability-and-telemetry-specification.md#3-release-manifest-checklist) turns every bullet above into a named, ownable, evidenced item — nine specific gates to clear before any release goes out, not a general reminder to be careful.

## Incident diagnosis

Incidents are classified at the responsible layer: model reasoning, missing or unauthorized context, retrieval, tool selection, tool execution, state, workflow, policy, human approval or enterprise dependency. The incident record includes the business consequence, affected cases, configuration, trace, containment, correction, regression case and control improvement.

Classifying at the responsible layer before root-causing is the discipline that prevents the single most common diagnostic error in AI operations: assuming every strange output is "a model problem" when the responsible layer is frequently somewhere else entirely — a stale retrieval index, a workflow that skipped a step, or an escalation trigger that never fired. A plausible-but-incorrect conclusion despite correct inputs genuinely is a model-reasoning failure; the same symptom caused by the model never having seen the evidence it needed is a context failure with an entirely different fix. Getting that classification right at intake, before anyone starts investigating, is what keeps an incident review from spending its first hour arguing about which team owns the problem instead of fixing it. The [Monitoring specification's incident classification taxonomy](../monitoring/observability-and-telemetry-specification.md#4-incident-classification-responsible-layer-taxonomy) extends the ten layers above with a typical symptom and a named first responder for each — the concrete routing table an on-call engineer actually uses at the moment an incident is declared, and every incident record it produces should follow the same [Failure Taxonomy](../monitoring/observability-and-telemetry-specification.md#4-incident-classification-responsible-layer-taxonomy) structure Chapter 18 defines for evaluation, so a failure discovered in production and a failure discovered in evaluation are classified the same way.

## Learning loop

> **PRODUCTION LOOP** Observe outcome and failures → diagnose the responsible layer → add or update evaluation cases → implement the smallest effective change → regression test → controlled release → verify outcome.

This loop is the mechanism that turns Chapter 18's evaluation discipline into a genuinely continuous one rather than a pre-release gate that is never revisited. Every incident that reaches production and gets root-caused is, by design, an admission that the evaluation dataset had a gap — a case the system needed to handle correctly that nobody had yet written down and tested for. Closing that loop by adding the failure back as a regression case is what prevents the system from being free to repeat a mistake it has already made once; skipping that step is the single most common way a production learning loop quietly stops learning. "Smallest effective change" is a deliberate constraint, not a hedge — the more of the system a fix touches, the larger the surface for a new, unrelated regression, and a narrow, well-targeted fix is both easier to verify and easier to roll back if it turns out to be wrong. The [Monitoring specification restates this loop as an operational runbook](../monitoring/observability-and-telemetry-specification.md#5-production-learning-loop-as-a-runbook), and at the enterprise level, [Operations and Observability Architecture's enterprise incident response flow](../architecture/perspective-09-operations-and-observability-architecture.md#2-enterprise-incident-response) extends this same loop to failures rooted in a shared component — a compromised model route or a shared integration — where the loop has to run once for the shared component but verify recovery across every system that consumes it.

---

[← Previous: Chapter 20: Governance, Compliance and Regulatory Engineering](chapter-20-governance-compliance-and-regulatory-engineering.md) · [Contents](../README.md) · [Next: Chapter 22: Economics, FinOps and Sustainability →](chapter-22-economics-finops-and-sustainability.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
