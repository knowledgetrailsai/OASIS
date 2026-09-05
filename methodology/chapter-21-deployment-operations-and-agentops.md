<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 20: Governance, Compliance and Regulatory Engineering](chapter-20-governance-compliance-and-regulatory-engineering.md) · [Contents](../README.md) · [Next: Chapter 22: Economics, FinOps and Sustainability →](chapter-22-economics-finops-and-sustainability.md)

# Chapter 21: Deployment, Operations and AgentOps

> **Implementation companion:** [Helm](https://github.com/knowledgetrailsai/Helm) — primary companion, full depth.


> **CHAPTER PURPOSE** Run intelligence systems as production services with versioning, tracing, quality monitoring, incident response, rollback and learning loops.

## Background and context

Chapters 19 and 20 build and govern the controls a system needs before it can be trusted to run. This chapter is where those controls meet production reality: the point where a system stops being something a team evaluates and starts being something users depend on continuously.

Running an intelligence system safely is a distinct discipline from building one correctly. A system that passed every evaluation and governance review can still fail in production if nobody can answer, mid-incident, which model, prompt and context version produced the output someone is now escalating.

AgentOps extends DevOps and MLOps to the behavior of complete intelligence systems, not a replacement for either. DevOps-era monitoring answers whether a service is up, fast and error-free; MLOps adds offline model-quality tracking. Neither accounts for what makes an agentic system different: the same request can take a different path through models, retrieval, tools and human approval each time, decided dynamically by the system itself.

Service-plane monitoring alone tells you whether a request succeeded, not why an outcome was good or bad. That is why this chapter defines six operational planes, set out in full in Helm's [Six Operational Planes](https://github.com/knowledgetrailsai/Helm/blob/main/00-foundations/the-six-operational-planes.md), rather than conventional monitoring with an extra dashboard.

Chapter 20 leaves operations with a practical obligation: keep accountable owners, retained evidence, and the obligation-to-control chain alive in production; a release manifest and an incident record are governance evidence generated as a byproduct of running the system well. It precedes Chapter 22 because every operational plane here, particularly the economic plane, is the raw telemetry Chapter 22's unit-economics discipline depends on.

The implementation companion is the [Monitoring: Observability and Telemetry Specification](../monitoring/observability-and-telemetry-specification.md), which turns the six planes below into concrete metrics, collection points and alert triggers, defines the trace_event schema every logged decision must carry, specifies the release manifest checklist, and lays out the incident classification taxonomy and learning loop in full detail. At enterprise scale, [Architecture Perspective 9; Operations and Observability Architecture](../architecture/perspective-09-operations-and-observability-architecture.md) is the portfolio-level rollup; aggregate dashboards across every deployed system, enterprise-wide incident response for shared-component failures, and the tiered kill-switch authority governing containment above any single system's runbook.

## Production operating model

AgentOps is only useful when it changes a decision. For each signal below, record the metric, data source, sampling rate, threshold, responder, and containment action. A release is not operationally ready until these signals are visible in a live-like environment and the on-call team has exercised the response. The service owner may reject the release when any required plane has no owner, threshold, or tested response.

AgentOps extends DevOps and MLOps to the behavior of complete intelligence systems. It must show which prompt, context policy, knowledge version, model, tool, workflow, control and user authority produced an outcome. Monitoring joins service telemetry with quality sampling and business events.

| **Operational plane** | **Measures and controls**                                                                                  |
|-----------------------|------------------------------------------------------------------------------------------------------------|
| Service               | Availability, latency, throughput, errors, queue depth, capacity and dependency health.                    |
| Intelligence          | Correctness, grounding, retrieval, tool choice, completion, abstention and escalation.                     |
| Risk                  | Unauthorized attempts, incorrect actions, policy violations, complaints, near misses and control failures. |
| Human                 | Adoption, overrides, approval time, exception load, rework and workaround behavior.                        |
| Economic              | Tokens, model and infrastructure cost, tool cost, intervention and cost per successful outcome.            |
| Outcome               | Primary result, leading indicators, guardrails and distribution across segments.                           |

A healthy reading on one plane does not imply a healthy reading below it. A service can be fully available and fast while the intelligence plane quietly produces ungrounded, confidently wrong answers no service dashboard would surface. The risk plane exists because a system can be intelligent and available while doing something it was never authorized to do; that deserves zero-tolerance alerting, not burial inside a general error rate.

The human plane matters because trust is earned continuously; a rising override rate is often the earliest signal something upstream has degraded, before it shows up as an outcome miss. Economic and outcome planes close the loop: what did this cost, and did it move the business metric the system was built to move.

The [Monitoring specification's instrumentation of all six planes](../monitoring/observability-and-telemetry-specification.md#1-the-six-operational-planes-instrumented) gives each row a representative metric, collection point and example alert trigger; the concrete answer to "measure what, from where, alert on what threshold" that this table leaves open, since the right threshold depends on a system's risk classification.

## Version and release management

- Immutable release manifest across model, prompt, context, index, tool, workflow, schema and control versions.

- Automated regression, security, integration and policy tests before release.

- Canary, cohort, shadow or percentage rollout with measurable stop conditions.

- Model-provider change detection and fallback compatibility.

- Rollback or forward-fix decision based on blast radius and state compatibility.

- Change communication to users, operations, risk owners and affected business processes.

Version management answers, with certainty rather than reconstruction, the first question every incident review asks: what changed, as Helm's [Release Manifest](https://github.com/knowledgetrailsai/Helm/blob/main/02-release-management/release-manifest.md) puts it. An intelligence system has more independently-versioned moving parts than a conventional application; model, prompt, context policy, knowledge index, tool schema, workflow definition and control policy can each change independently, and a release bundling several at once makes a regression hard to isolate.

An immutable release manifest prevents that: every release records exactly which version of each component produced it.

Rollout strategy and the rollback-versus-forward-fix decision should be made in advance, not improvised mid-incident. A canary or shadow rollout with defined stop conditions catches a regression against a small population before it reaches everyone, per Helm's [Rollout Strategies](https://github.com/knowledgetrailsai/Helm/blob/main/02-release-management/rollout-strategies.md). Pre-agreeing rollback-versus-forward-fix criteria; largely blast radius and state compatibility; removes a high-stakes call from the worst moment to make one, following the decision framework in Helm's [Rollback vs. Forward-Fix](https://github.com/knowledgetrailsai/Helm/blob/main/02-release-management/rollback-vs-forward-fix.md).

Model-provider change detection matters because a provider-side update can change a model's behavior without the build team initiating it; without detection, a team can't distinguish "we changed something" from "the model changed under us." The [Monitoring specification's release manifest checklist](../monitoring/observability-and-telemetry-specification.md#3-release-manifest-checklist) turns every bullet above into a named, ownable, evidenced item; nine gates to clear before any release.

## Incident diagnosis

Incidents are classified at the responsible layer: model reasoning, missing or unauthorized context, retrieval, tool selection, tool execution, state, workflow, policy, human approval or enterprise dependency; the ten layers in Helm's [Responsible-Layer Taxonomy](https://github.com/knowledgetrailsai/Helm/blob/main/03-incident-response/responsible-layer-taxonomy.md). The incident record includes the business consequence, affected cases, configuration, trace, containment, correction, regression case and control improvement.

Classifying at the responsible layer before root-causing prevents the most common diagnostic error in AI operations: assuming every strange output is "a model problem" when the cause is often a stale retrieval index, a skipped workflow step, or an escalation trigger that never fired. A plausible-but-incorrect conclusion despite correct inputs is a model-reasoning failure; the same symptom caused by the model never seeing the needed evidence is a context failure with a different fix. Getting this right at intake keeps a review from spending its first hour arguing about ownership instead of fixing the problem.

The [Monitoring specification's incident classification taxonomy](../monitoring/observability-and-telemetry-specification.md#4-incident-classification-responsible-layer-taxonomy) extends the ten layers above with a typical symptom and named first responder for each, and every incident record should follow the same [Failure Taxonomy](../monitoring/observability-and-telemetry-specification.md#4-incident-classification-responsible-layer-taxonomy) structure Chapter 18 defines for evaluation, so production and evaluation failures are classified the same way.

## Learning loop

> **PRODUCTION LOOP** Observe outcome and failures → diagnose the responsible layer → add or update evaluation cases → implement the smallest effective change → regression test → controlled release → verify outcome.

This loop turns Chapter 18's evaluation discipline into a continuous one rather than a pre-release gate nobody revisits, per Helm's [Production Learning Loop](https://github.com/knowledgetrailsai/Helm/blob/main/04-learning-loop/production-learning-loop.md). Every production incident that gets root-caused is an admission that the evaluation dataset had a gap; a case nobody had tested for. Adding the failure back as a regression case is what stops the system from repeating a mistake it has already made; skipping that step is how a learning loop quietly stops learning.

"Smallest effective change" is deliberate: the more of the system a fix touches, the larger the surface for a new regression, and a narrow fix is easier to verify and roll back. The [Monitoring specification restates this loop as an operational runbook](../monitoring/observability-and-telemetry-specification.md#5-production-learning-loop-as-a-runbook), and [Operations and Observability Architecture's enterprise incident response flow](../architecture/perspective-09-operations-and-observability-architecture.md#2-enterprise-incident-response) extends it to failures rooted in a shared component, where the loop runs once for the component but must verify recovery across every system consuming it.

---

[← Previous: Chapter 20: Governance, Compliance and Regulatory Engineering](chapter-20-governance-compliance-and-regulatory-engineering.md) · [Contents](../README.md) · [Next: Chapter 22: Economics, FinOps and Sustainability →](chapter-22-economics-finops-and-sustainability.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
