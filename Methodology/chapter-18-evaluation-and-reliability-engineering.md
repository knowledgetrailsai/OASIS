<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 17: Enterprise Integration and Tool Engineering](chapter-17-enterprise-integration-and-tool-engineering.md) · [Contents](../README.md) · [Next: Chapter 19: Security and Responsible AI Engineering →](chapter-19-security-and-responsible-ai-engineering.md)

# Chapter 18: Evaluation and Reliability Engineering

# Evaluation and Reliability Engineering

> **CHAPTER PURPOSE** Create the evidence system that measures response quality, agent behavior, workflow completion, resilience and business-outcome contribution.

## Background and context

Chapters 16 and 17 design who has authority over a piece of work and how the system reaches into enterprise applications to act on it. Neither answers whether that design was sound: how do you know, with evidence rather than confidence, that the system does what it should? This chapter pairs two questions: evaluation asks "is this good enough to ship," and reliability engineering asks "what happens when it isn't, right now." A system can have thorough evaluation coverage and still fail in the field if nothing contains failures evaluation didn't anticipate. It can have extensive guardrails and still be untrustworthy if nothing measures whether it accomplishes the task it was built for.

This chapter's implementation-level companion is [Engineering: Evaluation and Reliability Engineering](../engineering/evaluation-and-reliability-engineering.md), which turns the hierarchy and taxonomy below into a fifteen-dimension evaluation reference, an evaluation-progression ladder, a guardrails and recovery pattern library, and a grader-design checklist for using one model to grade another's output ("LLM-as-judge") — trustworthy only once the judge is checked against human-labeled cases, and re-checked as it drifts. The [Evaluation Strategy and Dataset](../tools/02-workflow-and-intelligence-templates.md#9-evaluation-strategy-and-dataset) and [Failure Taxonomy](../tools/02-workflow-and-intelligence-templates.md#10-failure-taxonomy) templates are the fillable instruments behind this chapter's two tables. The [Observability and Telemetry Specification's](../monitoring/observability-and-telemetry-specification.md) intelligence plane instruments the same quality dimensions as production metrics with alert thresholds — evaluation does not stop at go-live, it becomes continuous, sampled measurement of what was tested before release.

Chapter 19 picks up where this chapter's reliability discipline leaves off: robustness testing against adversarial input is the evaluation-side twin of the defense-in-depth controls described there. A failure found through evaluation is often the first evidence of a security gap, not just a quality one.

## Evaluation hierarchy

The most common evaluation mistake is picking one altitude — usually "is the model's response good" — and stopping there, because it is the easiest thing to test. It is also the least informative on its own: a fluent, correct-sounding response proves nothing about whether the right tool was called, the task completed, or the business outcome moved at all. OASIS evaluates at six distinct levels; a mature program maintains coverage at all of them, not just the extremes.

| **Level**      | **Question**                        | **Examples**                                                  |
|----------------|-------------------------------------|-----------------------------------------------------------------|
| Component      | Does one layer work?                | Retrieval relevance, schema validity, classifier accuracy.    |
| Model response | Is the output correct and grounded? | Factuality, citation, completeness, abstention.               |
| Agent step     | Was the next action appropriate?    | Tool choice, arguments, policy and state update.               |
| Workflow       | Was the task completed correctly?   | End-to-end completion, exception handling, human effort.       |
| Service        | Is production performance reliable? | Latency, availability, incident, cost and drift.               |
| Outcome        | Did business performance improve?   | Conversion, MTTR, first-time-right, cycle time, loss avoided.  |

Each level answers a question the level above it cannot. A system that passes every component and model-response test can still fail at the agent-step level by picking the wrong tool for a case it otherwise understands. A system that completes every workflow correctly in staging can still fail at the outcome level in production if correct steps don't, in aggregate, move the target metric. The [Engineering companion's evaluation-progression ladder](../engineering/evaluation-and-reliability-engineering.md#2-evaluation-progression-ladder) collapses this into four checkpoints — response, agent step, completed workflow, business outcome — mapped to where each is normally tested and who owns it.

## Evaluation dataset strategy

An evaluation dataset that only contains cases the system already handles well tells you nothing you didn't already believe. A sound dataset combines curated gold cases, production samples (rarely as clean as the gold set), historical failures (so a fixed bug cannot silently reappear), boundary cases, prompts with insufficient evidence (to test whether the system abstains rather than fabricates), adversarial inputs, and counterfactual variants. Development, regression and held-out sets must stay separate and firewalled: a case used to tune the system has no evidential value if it later shows up in the set used to certify it ready to ship.

Two disciplines are easy to skip under delivery pressure and expensive to skip in practice. Leakage protection — ensuring no case, or near-duplicate, crosses from development into the held-out set — must be actively enforced, not assumed. Where a case has parent-case variants (the same scenario with small perturbations), those variants belong in the same split, or a system can appear to generalize simply by memorizing one variant and being tested on a sibling. Every case should be versioned with its source evidence and expected behavior, so it's obvious which cases go stale when policy changes. The [Evaluation Strategy and Dataset template](../tools/02-workflow-and-intelligence-templates.md#9-evaluation-strategy-and-dataset) turns this into a fillable specification — fifteen quality dimensions, dataset composition and splits, per-case grader and pass threshold, a regression policy, and a production-sampling cadence.

## Failure taxonomy

Naming failures by family, before root-causing any incident, prevents the most common diagnostic error in AI operations: assuming every strange output is "a model problem" when the responsible layer is often elsewhere — a stale evidence source, a skipped workflow step, an escalation trigger that never fired.

| **Failure family**   | **Illustrative failures**                                                              |
|-----------------------|------------------------------------------------------------------------------------------|
| Intent and scope     | Wrong task, wrong field, wrong lifecycle or unsupported expansion.                     |
| Evidence and context | Missing source, stale source, irrelevant context, poisoned context, unsupported claim. |
| Model behavior       | Reasoning error, hallucination, poor uncertainty, instruction failure.                 |
| Tool and action      | Wrong tool, invalid arguments, duplicate action, excessive authority.                  |
| Workflow and state   | Looping, skipped step, stale state, failed hand-off, incomplete recovery.              |
| Human interaction    | Unclear approval, automation bias, poor escalation, unusable correction.               |
| Control and policy   | Unauthorized access, policy bypass, incorrect retention, audit gap.                    |
| Service and outcome  | Latency, outage, cost spike, adverse downstream effect, no outcome lift.               |

Production operations classifies incidents against this same taxonomy at intake — see the [Observability and Telemetry Specification's responsible-layer incident classification](../monitoring/observability-and-telemetry-specification.md#4-incident-classification-responsible-layer-taxonomy), which extends these families into ten responsible layers (model, context, retrieval, tool selection, tool execution, state, workflow, policy, human approval, enterprise dependency), each routed to a named first responder. This is deliberate: a failure family found in evaluation should map onto the category operations uses live. Every root-caused production incident should become a new regression case — via the [Failure Taxonomy template](../tools/02-workflow-and-intelligence-templates.md#10-failure-taxonomy), which adds severity, detectability, business impact, owner, containment action and confirmation a regression case was added. A fix never added as a regression case is free to repeat.

## Reliability engineering

Evaluation tells you whether the system is good enough to ship. Reliability engineering is what happens after: making sure it degrades safely, not catastrophically, when something outside the evaluation set occurs. Keep two objectives separate: a service-level objective (up, fast, within error budget) and an intelligence-quality objective (still correct and grounded) are not the same measurement. A system can meet one while badly failing the other — a fast, always-available system returning confidently wrong answers is reliable by the first definition and dangerous by the second.

Reliability has to be tested deliberately, not assumed because nothing has broken yet. Downstream outages, malformed tool output, model unavailability, context overflow and partial completion are foreseeable failure modes; each needs a defined behavior, not one discovered for the first time in production. The [Engineering companion's guardrails and recovery pattern library](../engineering/evaluation-and-reliability-engineering.md#3-guardrails-and-recovery-pattern-library) catalogues the standard responses — iteration and cost limits against runaway loops, safe retries restricted to idempotent operations, defined partial-completion states, compensating actions for non-idempotent operations, fallback models or workflows for degraded primaries, human escalation with an explicit trigger and target, and suspension or kill switches for an immediate stop — each mapped to the failure mode it addresses and cross-referenced to the [Security checklist](../security/agentic-ai-threat-and-control-checklist.md#4-containment-and-emergency-control-checklist). High-consequence steps deserve a deterministic check, redundancy, or mandatory human review, not the model's judgment alone.

Error budgets give this discipline teeth: define an acceptable rate of service and quality degradation in advance, and restrict releases automatically once breached, rather than relying on a judgment call made mid-incident. Every material change — a new model, a prompt edit, a reindexed knowledge base, a modified tool, a changed workflow, a revised policy — runs the full regression suite before release, per the [Observability and Telemetry Specification's release manifest checklist](../monitoring/observability-and-telemetry-specification.md#3-release-manifest-checklist): an immutable version record, passed regression/security/integration/policy tests, a rollout strategy with defined stop conditions, and a rollback-versus-forward-fix decision made before release, not improvised during it.

> **EVALUATION PRINCIPLE** A fluent response is not evidence of a successful workflow, and a successful workflow is not evidence of a valuable outcome.

---

[← Previous: Chapter 17: Enterprise Integration and Tool Engineering](chapter-17-enterprise-integration-and-tool-engineering.md) · [Contents](../README.md) · [Next: Chapter 19: Security and Responsible AI Engineering →](chapter-19-security-and-responsible-ai-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
