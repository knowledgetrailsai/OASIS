<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 17: Enterprise Integration and Tool Engineering](chapter-17-enterprise-integration-and-tool-engineering.md) · [Contents](../README.md) · [Next: Chapter 19: Security and Responsible AI Engineering →](chapter-19-security-and-responsible-ai-engineering.md)

# Chapter 18: Evaluation and Reliability Engineering

# Evaluation and Reliability Engineering

> **CHAPTER PURPOSE** Create the evidence system that measures response quality, agent behavior, workflow completion, resilience and business-outcome contribution.

## Evaluation hierarchy

| **Level**      | **Question**                        | **Examples**                                                  |
|----------------|-------------------------------------|---------------------------------------------------------------|
| Component      | Does one layer work?                | Retrieval relevance, schema validity, classifier accuracy.    |
| Model response | Is the output correct and grounded? | Factuality, citation, completeness, abstention.               |
| Agent step     | Was the next action appropriate?    | Tool choice, arguments, policy and state update.              |
| Workflow       | Was the task completed correctly?   | End-to-end completion, exception handling, human effort.      |
| Service        | Is production performance reliable? | Latency, availability, incident, cost and drift.              |
| Outcome        | Did business performance improve?   | Conversion, MTTR, first-time-right, cycle time, loss avoided. |

## Evaluation dataset strategy

Datasets combine curated gold cases, production samples, historical failures, boundary cases, insufficient-evidence prompts, adversarial inputs and counterfactuals. Separate development, regression and held-out assurance sets. Protect against leakage, preserve parent-case variants in the same split where needed, and version source evidence with expected behavior.

## Failure taxonomy

| **Failure family**   | **Illustrative failures**                                                              |
|----------------------|----------------------------------------------------------------------------------------|
| Intent and scope     | Wrong task, wrong field, wrong lifecycle or unsupported expansion.                     |
| Evidence and context | Missing source, stale source, irrelevant context, poisoned context, unsupported claim. |
| Model behavior       | Reasoning error, hallucination, poor uncertainty, instruction failure.                 |
| Tool and action      | Wrong tool, invalid arguments, duplicate action, excessive authority.                  |
| Workflow and state   | Looping, skipped step, stale state, failed hand-off, incomplete recovery.              |
| Human interaction    | Unclear approval, automation bias, poor escalation, unusable correction.               |
| Control and policy   | Unauthorized access, policy bypass, incorrect retention, audit gap.                    |
| Service and outcome  | Latency, outage, cost spike, adverse downstream effect, no outcome lift.               |

## Reliability engineering

- Define service-level objectives and intelligence-quality objectives separately.

- Test downstream outages, malformed tool output, model unavailability, context overflow and partial completion.

- Use deterministic checks, redundancy or human review for high-consequence steps.

- Establish error budgets for service and quality degradation, with release restrictions when breached.

- Run regression tests for every material model, prompt, index, tool, workflow or policy change.

> **EVALUATION PRINCIPLE** A fluent response is not evidence of a successful workflow, and a successful workflow is not evidence of a valuable outcome.

---

[← Previous: Chapter 17: Enterprise Integration and Tool Engineering](chapter-17-enterprise-integration-and-tool-engineering.md) · [Contents](../README.md) · [Next: Chapter 19: Security and Responsible AI Engineering →](chapter-19-security-and-responsible-ai-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
