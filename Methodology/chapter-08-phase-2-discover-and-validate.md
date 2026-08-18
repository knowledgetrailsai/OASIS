<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 07: Phase 1 — Engage & Align](chapter-07-phase-1-engage-and-align.md) · [Contents](../README.md) · [Next: Chapter 09: Phase 3 — Engineer & Integrate →](chapter-09-phase-3-engineer-and-integrate.md)

# Chapter 08: Phase 2 — Discover & Validate

# Phase 2 — Discover & Validate

> **CHAPTER PURPOSE** Prove that intelligence can materially improve the real workflow on representative cases with acceptable quality, safety, adoption and economics.

## Background and context

Phase 1 produces a hypothesis; Phase 2 exists to test it honestly, before real budget goes into production engineering. That ordering matters because the two phases ask fundamentally different questions. Engage & Align asks whether an outcome is worth pursuing; Discover & Validate asks whether the specific mechanism proposed — intelligence applied to this workflow — actually works well enough, on the cases that matter, to justify building it properly. Conflating the two is one of the most common ways AI initiatives fail: a team that skips straight from a promising demo to a production build has never actually tested the hypothesis, only illustrated it.

The discipline this phase enforces is representativeness. It is easy to make almost any model or agent look capable on a handful of hand-picked examples; it is much harder, and much more informative, to make it work on the exceptions, the ambiguous cases, and the inputs where the available evidence is thin or contradictory. A vertical slice that only ever sees the happy path tells you nothing about what will happen in production, where the happy path is a minority of real traffic for most enterprise workflows. This is also the phase where the team confronts, in a controlled setting, the question of whether users can actually oversee and correct the system — a question that architecture diagrams cannot answer on their own.

What Phase 2 hands to [Phase 3 — Engineer & Integrate](chapter-09-phase-3-engineer-and-integrate.md) is evidence, not just a decision to proceed: a characterized set of failure modes, a sense of where the workflow needs redesign rather than automation, and an economic sensitivity analysis that tells the engineering team which quality thresholds actually matter. The data-readiness work done here connects directly to [Context and Retrieval Engineering](../engineering/context-and-retrieval-engineering.md), which is where knowledge-grounding failures identified in this phase get engineered away rather than merely diagnosed; the [Data and Knowledge Readiness Assessment](../tools/02-workflow-and-intelligence-templates.md#8-data-and-knowledge-readiness-assessment) produced here is the artifact that carries that diagnosis forward.

## Phase objective

Prove the intelligence and workflow hypothesis using representative cases and one end-to-end vertical slice.

A vertical slice, in this sense, is not a prototype of the whole system — it is a thin but complete path through every layer the production system will eventually need: input, context assembly, model or tool invocation, human review, and outcome capture. The point of building it thin is speed of learning; the point of building it complete is that a slice missing the human-review layer, for instance, will systematically overstate how well the system performs, because it never has to survive contact with the oversight it will actually operate under.

## Core questions

- Can intelligence improve quality, speed, cost or experience?

- Does it work on exceptions, not only happy paths?

- Can users operate and oversee it?

- Are likely economics and controls acceptable?

The first question is deliberately broad — "improve" can mean any of several different things, and a team should be explicit about which one it is claiming before it starts measuring. The second is where most Phase 2 work earns its keep: a system that performs well on average but fails silently on exceptions is often worse than no system at all, because it erodes the very workflow discipline that used to catch those exceptions manually. The third question is frequently under-tested — it is not enough for a system to be technically correct if the interface and workflow around it make oversight impractical, so users either rubber-stamp its output or abandon it. The fourth brings economics into the same conversation as quality, on the reasonable premise that a system which is accurate but too expensive to run, or whose intervention cost exceeds its savings, has not actually solved anything.

## Method

11. Map the current and target process, decisions, hand-offs, evidence sources, exceptions and failure consequences.

12. Assemble representative evaluation cases, including difficult, insufficient-evidence and adversarial examples.

13. Build a thin vertical slice across input, context, model, tool or workflow action, human review and outcome capture.

14. Compare against the current process and a simple deterministic baseline where appropriate.

15. Classify failures by data, context, model, tool, workflow, control, human interaction and enterprise-system cause.

16. Estimate run cost, intervention cost, failure cost and the sensitivity of value to quality and adoption.

The process map at step 11 should describe the workflow as it actually runs today, exceptions and workarounds included, using the [Process and Decision Map](../tools/02-workflow-and-intelligence-templates.md#6-process-and-decision-map) template — a map of the idealized process produces an evaluation dataset built to the wrong shape. Step 12's inclusion of adversarial and insufficient-evidence cases is not paranoia; production traffic reliably contains inputs where the honest answer is "I don't have enough information," and a system that has never been tested against that case will confidently hallucinate one instead. Step 14's deterministic baseline matters because intelligence is not always the right tool: if a simple rule or lookup performs nearly as well as the AI-driven approach, that is a valid and useful finding, not a failed experiment. Step 15's failure classification by responsible layer is the direct precursor to the failure taxonomy discipline used throughout operations later in the lifecycle, and step 16 is what turns a technically successful pilot into, or out of, a viable business case.

## Primary artifacts

- Process and Decision Map

- Human–AI Workflow Blueprint

- Evaluation Dataset and Scorecard

- Failure Taxonomy

- Vertical Slice

- Data/Knowledge Readiness Assessment

- Deployment Recommendation

These correspond directly to templates 6 through 10 in [Workflow and Intelligence Templates](../tools/02-workflow-and-intelligence-templates.md): the Process and Decision Map, the Human–AI Workflow Blueprint, the Evaluation Strategy and Dataset, the Data and Knowledge Readiness Assessment and the Failure Taxonomy. The evaluation dimensions worth scoring against are laid out in more technical detail in [Evaluation and Reliability Engineering](../engineering/evaluation-and-reliability-engineering.md#1-evaluation-dimension-reference); a Phase 2 team building its evaluation strategy from scratch rather than starting from that reference tends to under-cover dimensions like groundedness and escalation correctness that only become obviously important after a production incident has already happened.

> **DECISION OUTCOME** Solution Viability Review: proceed, reframe, acquire, defer or stop.

## Entry and exit conditions

| **Entry condition**                                                          | **Exit condition**                                                                                |
|--------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| The Outcome Charter is owned and the opportunity has permission to validate. | The team can explain performance, failure modes, workflow fit, controls and economic sensitivity. |

Note what the exit condition asks for: not a passing score, but an explanation. A Phase 2 that ends with "it works" and no account of where it doesn't has not actually validated anything — it has produced a demo with better documentation. The Solution Viability Review should be able to ask "what happens when the evidence is ambiguous" and get a specific, evidenced answer.

## Tailoring guidance

A PoC may use synthetic or de-identified data and simulated tools, but its test cases must represent the intended workflow. A controlled pilot requires real access, monitoring and human approval design.

The distinction between a proof of concept and a controlled pilot is not a matter of scale, it is a matter of what kind of claim each is entitled to support. A PoC built on synthetic data can validate that an approach is plausible; it cannot validate that it is safe or adoptable in production, because those properties depend on real data quality, real system latency and real human behavior under real stakes. Teams that treat a strong PoC result as sufficient evidence to skip a controlled pilot are usually the same teams surprised, later, by how differently the system performs once real users and real data are involved.

---

[← Previous: Chapter 07: Phase 1 — Engage & Align](chapter-07-phase-1-engage-and-align.md) · [Contents](../README.md) · [Next: Chapter 09: Phase 3 — Engineer & Integrate →](chapter-09-phase-3-engineer-and-integrate.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
