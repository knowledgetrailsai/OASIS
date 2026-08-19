<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: Memory and State Engineering](memory-and-state-engineering.md) · [Chapter 18: Evaluation and Reliability Engineering](../methodology/chapter-18-evaluation-and-reliability-engineering.md) · [Chapter 14: Intelligence and Agent Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md)

# Engineering: Evaluation and Reliability Engineering

> **PURPOSE** Turn Chapter 18 (in full) and Chapter 14 §10–11 into a fillable evaluation-dimension reference, an evaluation-progression ladder, a guardrails/recovery pattern library, and a grader-design checklist — the concrete instrument behind "what constitutes acceptable behavior and change."

**Primary OASIS source:** [Chapter 18 — Evaluation and Reliability Engineering](../methodology/chapter-18-evaluation-and-reliability-engineering.md); [Chapter 14 §10 — Guardrails, Reliability and Recovery](../methodology/chapter-14-intelligence-and-agent-engineering.md#10-guardrails-reliability-and-recovery) and [§11 — Evaluation Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md#11-evaluation-engineering); cross-referenced with the [Evaluation Strategy and Dataset template](../tools/02-workflow-and-intelligence-templates.md#9-evaluation-strategy-and-dataset) and the [Security checklist's](../security/agentic-ai-threat-and-control-checklist.md) containment section.

## Background and context

Evaluation and reliability are paired in one chapter, and this article keeps that pairing, because they answer the same underlying question from two directions: evaluation asks "how do we know this system is good enough before it ships," and reliability/guardrails ask "what happens when it isn't, in production, right now." A system can have excellent evaluation coverage and still fail in production if it has no guardrails to contain the failures evaluation didn't anticipate; a system can have extensive guardrails and still be untrustworthy if nothing evaluates whether it's actually accomplishing the task. Chapter 14 §11 makes a point that most conventional software testing practice does not need to make explicitly: the evaluation *unit* has to progress from a single model response, to a single agent step, to a completed multi-step workflow, to the actual business outcome — because a system can pass every unit-level test and still fail to deliver the outcome it was built for, if the individual correct steps don't compose into a correct end-to-end result. Section 2 below turns that progression into a concrete ladder rather than leaving it as a sentence.

The current state of practice for grading model output — "LLM-as-judge," where one model evaluates another model's response against a rubric — deserves a specific caution that Chapter 18 implies but doesn't spell out mechanically: a judge model is itself a model, with its own failure modes, and using it uncritically risks building an evaluation suite that reliably agrees with a biased or miscalibrated judge rather than reliably measuring quality. Section 4 below treats grader design as an engineering task with its own validation step (calibrating the judge against a smaller set of human-labeled cases) rather than assuming any judge, once configured, can be trusted indefinitely without re-checking. This matters because an uncalibrated or drifting judge is a silent failure mode — the evaluation suite keeps reporting green while the underlying quality bar it's supposed to enforce has quietly moved.

**How to use this document:** use Section 1 to define what "good" means for a specific system before writing test cases. Use Section 2 to decide at what altitude (response/step/workflow/outcome) a given quality question should be tested. Use Section 3 as a pattern library when designing guardrails and recovery behavior — cross-referencing the [Security checklist](../security/agentic-ai-threat-and-control-checklist.md) for which threat each pattern addresses. Use Section 4 whenever a grader (human or model) is introduced or changed, and Section 5 as the release-gate reliability checklist.

## 1. Evaluation dimension reference

Chapter 14 §11 names fifteen dimensions to measure. Each row below adds what it actually measures, a typical grading method, and an example of what failure looks like.

| # | Dimension | What it measures | Typical grader | Example failure |
|---|---|---|---|---|
| 1 | Intent understanding | Did the system correctly interpret what was being asked? | Human or model-graded | Answers a plausible but different question than the one asked |
| 2 | Correctness | Is the substantive content of the response accurate? | Rubric or deterministic (where checkable) | Factually wrong answer stated with full confidence |
| 3 | Groundedness | Is the response supported by the retrieved/provided evidence, not invented? | Model-graded against source | Confident claim with no supporting source in context |
| 4 | Citation accuracy | Do cited sources actually say what's attributed to them? | Deterministic (source-text match) or human spot-check | Citation points to a real source that doesn't contain the claim |
| 5 | Structured output validity | Does output conform to the required schema? | Deterministic (schema validation) | Malformed JSON, missing required field, wrong type |
| 6 | Retrieval quality | See [Context and Retrieval Engineering §4](context-and-retrieval-engineering.md#4-retrieval-evaluation-template) | Deterministic (precision/recall) | Relevant document existed but wasn't retrieved |
| 7 | Tool selection and arguments | Right tool chosen, called with correct/valid arguments? | Deterministic (against tool contract) | Wrong tool called, or valid tool called with invalid parameters |
| 8 | Workflow completion | Did the multi-step task actually reach its termination criteria? | Deterministic (harness state) | Task loops indefinitely or exits without completing |
| 9 | Policy adherence | Did the system respect guardrails/business rules throughout? | Deterministic where possible, human review otherwise | Guardrail bypassed under adversarial or edge-case input |
| 10 | Escalation correctness | Did the system escalate when it should have, and not when it shouldn't? | Human-graded | Failed to escalate a case outside its authority; or over-escalated routine cases |
| 11 | Robustness | Does behavior hold under adversarial, malformed, or edge-case input? | Adversarial test set — see Section 5 | Small input perturbation causes large output change |
| 12 | Latency | Does response time meet the task's tolerance? | Deterministic (measured) | Interactive task takes minutes instead of seconds |
| 13 | Cost | Does cost per case stay within budget? | Deterministic (measured) — link to [Model Engineering](model-engineering.md) optimization ladder | Cost per successful outcome exceeds the Value and Risk Case ceiling |
| 14 | User acceptance | Do real users accept/trust the output, measured by behavior not just survey | Production telemetry (override rate, adoption) | High override rate despite passing offline evaluation |
| 15 | Outcome contribution | Does this system's behavior actually move the business outcome metric? | Outcome-level measurement — see Section 2 | Individually correct steps that don't move the metric they were built to move |

## 2. Evaluation progression ladder

| Level | What's tested | Typical environment | Owner |
|---|---|---|---|
| Response | A single model output against a single input, in isolation | Dev, pre-merge | Model/prompt engineer |
| Agent step | A single harness step (including tool selection/execution) in context | Dev/staging | Harness engineer |
| Completed workflow | The full multi-step task, end to end, including human-in-the-loop steps | Staging, pre-release | Engineering lead |
| Business outcome | Whether production behavior actually moves the [Outcome Metric Tree's](../tools/01-outcome-and-portfolio-templates.md#4-outcome-metric-tree) primary metric | Production | Outcome owner |

A system that only tests at the Response level has no evidence it works end to end; a system that only measures at the Outcome level has no diagnostic ability when the outcome metric moves the wrong way. Maintain evaluation coverage at every level, not just the extremes.

## 3. Guardrails and recovery pattern library

From Chapter 14 §10. Each pattern addresses a specific failure mode — cross-reference the [Security checklist](../security/agentic-ai-threat-and-control-checklist.md) for the threat each one is closing.

| Pattern | Implementation note | Failure mode addressed |
|---|---|---|
| Iteration/time/token/cost/transaction limits | See [Harness limits and budgets](harness-and-orchestration-engineering.md#4-limits-and-budgets-configuration) | Runaway loops, denial of wallet (Security §2 row 11) |
| Safe retries | Retry only idempotent operations; track against a retry limit | Transient failures compounding into duplicate side effects |
| Partial completion handling | Define what a "partially done" task state means and how it's surfaced | Silent data loss or inconsistent state on mid-task failure |
| Compensating actions | For non-idempotent operations, define the explicit undo/compensate action | Irreversible action taken in error with no recovery path |
| Fallback models or workflows | Defined route to a simpler, more reliable path when the primary fails | Primary model/workflow outage or degraded quality |
| Human escalation | Explicit trigger and target for handing a case to a human | Case outside system authority or confidence proceeding anyway |
| Suspension and kill switches | See [Security checklist's containment section](../security/agentic-ai-threat-and-control-checklist.md#4-containment-and-emergency-control-checklist) | Uncontrolled agent behavior requiring immediate stop |

## 4. Grader design and calibration checklist

| # | Item | Detail |
|---|---|---|
| 1 | Grader type | Human / fixed rubric / deterministic check / model-graded (LLM-as-judge) |
| 2 | Rubric definition | Is the passing criterion written down and unambiguous, not left to grader judgment? | |
| 3 | Calibration set | For model-graded evaluation: has the judge been checked against a human-labeled sample? | |
| 4 | Calibration result | Agreement rate between judge and human labels — below what threshold does the judge need re-work? | |
| 5 | Drift monitoring | How often is the judge re-calibrated against fresh human labels? | |
| 6 | Judge model independence | Is the judge a different model/version than the system being evaluated, to avoid self-grading bias? | |

## 5. Reliability testing checklist

| # | Test type | What it verifies | Status |
|---|---|---|---|
| 1 | Regression suite | Every known past failure has a corresponding case that now passes — see [Failure Taxonomy](../tools/02-workflow-and-intelligence-templates.md#10-failure-taxonomy) | |
| 2 | Load testing | System behavior under expected and peak concurrent volume | |
| 3 | Chaos/failure injection | Behavior when a dependency (model, tool, retrieval index) is degraded or unavailable | |
| 4 | Adversarial robustness | Behavior under inputs designed to probe the [Security checklist's](../security/agentic-ai-threat-and-control-checklist.md) threat categories | |
| 5 | Recovery drill | Kill-switch and checkpoint-resume tested end to end, not just designed | |

---

[← Back to Contents](../README.md) · [← Previous: Memory and State Engineering](memory-and-state-engineering.md) · [Chapter 18: Evaluation and Reliability Engineering](../methodology/chapter-18-evaluation-and-reliability-engineering.md) · [Chapter 14: Intelligence and Agent Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
