<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 15: Data and Knowledge Engineering](chapter-15-data-and-knowledge-engineering.md) · [Contents](../README.md) · [Next: Chapter 17: Enterprise Integration and Tool Engineering →](chapter-17-enterprise-integration-and-tool-engineering.md)

# Chapter 16: Human–AI Workflow and Experience Engineering

# Human–AI Workflow and Experience Engineering

> **CHAPTER PURPOSE** Redesign work around complementary human and machine strengths, explicit authority, usable oversight, trust calibration and accessible experiences.

## Background and context

Chapter 14 establishes what the intelligence system can do. Chapter 15 ensures it has governed, sufficient evidence. Neither answers who is allowed to do what with the system, or how a human and a machine hand work back and forth. That is the gap this chapter closes. Most AI programs succeed or fail here — not on model quality, but on whether the surrounding work was redesigned for the new division of labor.

This is engineering, not change management bolted on afterward. A workflow that never specifies who has authority over a decision, or what a person sees before approving an AI-prepared action, is an unfinished design, not a training gap. This chapter's templates decide authority, evidence and fallback at design time, alongside the model and data pipeline. The [Process Architecture](../architecture/perspective-03-process-architecture.md) perspective maps how a single hand-off sits inside a longer business process — use it to locate a workflow in that wider map, and its handback-design section when a return-to-human trigger must be explicit across a whole process.

Chapter 16 also produces the artifact the rest of the methodology points back to: the [Human–AI Workflow Blueprint](../tools/02-workflow-and-intelligence-templates.md#7-human-ai-workflow-blueprint) template. Complete it early — Chapter 17's tool contracts assume the authority model is decided, and Chapter 18's evaluation of escalation correctness assumes the escalation triggers named here already exist. OASIS treats adoption as workflow engineering, not post-build communication: human judgment, AI capability, deterministic controls and enterprise systems each doing the work they suit best.

## Human–AI workflow blueprint

Redesigning a workflow starts by naming what is changing and why, for every meaningful step. The table below is the minimum set of design decisions a workflow needs before it is safe to build. Skipping any one tends to surface later as an incident or an unexplained override.

| **Element**        | **Required design decision**                                                                |
|--------------------|---------------------------------------------------------------------------------------------|
| Task and decision  | What work is being changed and what outcome should improve?                                 |
| AI contribution    | Retrieve, classify, predict, generate, recommend, plan or execute?                          |
| Human contribution | Set intent, review evidence, approve, handle exception, empathize or accept accountability? |
| Authority          | Who may decide or act for each case class and threshold?                                    |
| Evidence           | What source, confidence and context must be visible?                                        |
| Fallback           | What happens when evidence, model, tool or downstream system fails?                         |
| Feedback           | How are corrections captured without creating surveillance or incentive problems?           |
| Outcome            | How is successful completion linked to the original business measure?                       |

The first two rows are where most designs go wrong. It is tempting to describe the AI contribution in terms of technology ("uses a language model to draft a response") rather than the cognitive work it replaces ("drafts a first-pass response for human review"). The second framing tells you what evidence a reviewer needs and what authority the human keeps by reviewing first. Authority deserves the same discipline: "who may decide" should resolve to a named role or rule, not "the AI, usually," or accountability evaporates the first time something goes wrong.

The [template](../tools/02-workflow-and-intelligence-templates.md#7-human-ai-workflow-blueprint) expresses every row above as a step-by-step specification — AI role, human role, authority, evidence shown, interface, approval requirement, override mechanism, fallback, escalation trigger and target, and a feedback loop into the Chapter 18 evaluation dataset. Filling it out per step turns "a human reviews the output" into something a team can build and rely on.

## Progressive autonomy model

Autonomy is not a single on/off decision made at launch. It is a ladder a workflow climbs one rung at a time, as evidence accumulates that the rung below is reliable.

| **Mode**         | **System role**                               | **Human role**                                |
|------------------|-----------------------------------------------|-----------------------------------------------|
| Shadow           | Observe and produce non-operational output.   | Perform normal work; compare retrospectively. |
| Recommend        | Offer advice and evidence.                    | Decide and act.                               |
| Assist           | Prepare work or populate transactions.        | Review, edit and submit.                      |
| Approve-to-act   | Propose a bounded action.                     | Explicitly approve execution.                 |
| Exception-based  | Execute routine cases within rules.           | Review exceptions and samples.                |
| Bounded autonomy | Plan and execute within authority and limits. | Own policy, monitor and intervene.            |

Shadow mode answers one question cheaply and safely: does the system's judgment agree with an experienced human's, across a representative range of cases? Skipping it is usually a false economy — it is the cheapest place to find a blind spot before it becomes a production incident. Moving up a rung should be evidence-based, not calendar-based: a workflow graduates from assist to approve-to-act because evaluation results (Chapter 18) and override rates support it, not because it has been live for a quarter. It is equally normal to move down a rung — after a policy or model change, or a sustained rise in override rate — until confidence is re-established.

Most enterprise workflows never need to reach bounded autonomy. Exception-based operation — routine cases run within clear rules, a human reviews exceptions and a sample of the rest — is a durable end state for most processes, especially where a wrong action is expensive or hard to reverse.

## Trust calibration

The objective is appropriate reliance, not maximum trust. A user who defers to every AI recommendation looks efficient until the recommendation is wrong. A user who quietly re-does the AI's work looks diligent until you realize the redesign delivered no benefit.

Interfaces are the primary lever for correcting this. They should reveal source quality, uncertainty, limitations, the scope of the proposed action, and the consequence of approving it — visible where a reviewer will see it, not buried in a tooltip. Correction and escalation need to be genuinely easy, or the override path will not get used when it matters. Trust calibration is behavioral, so measure it that way: track over-reliance, under-use, rubber-stamping (fast, uniform approval times are a useful proxy), automation bias, and workload quietly migrated into exception handling rather than eliminated.

## Change and capability

Adoption work has to start earlier than most programs schedule it. Engaging users during discovery and evaluation surfaces objections and edge cases while they are still cheap to address. By the time training is the first point of contact, the roles and incentives around the job are usually already decided without the people who live inside them.

Redesign roles, capacity, incentives, quality checks and performance measures alongside the workflow, not as an afterthought. A workflow can be technically correct and still fail if people are measured and resourced as though the old process were running. Training must cover purpose, limits, how to interpret the evidence shown, what an approval commits the approver to, and data-handling responsibilities — not just interface mechanics. Accessibility, language, channel and digital-literacy needs belong in that same design pass, not as a later retrofit.

Finally, measure the transition itself: time-to-proficiency, correct use, override rates, workaround behavior, and users' sense of control are early signals of whether a workflow is landing — well before the outcome metrics in Chapter 18 move.

---

[← Previous: Chapter 15: Data and Knowledge Engineering](chapter-15-data-and-knowledge-engineering.md) · [Contents](../README.md) · [Next: Chapter 17: Enterprise Integration and Tool Engineering →](chapter-17-enterprise-integration-and-tool-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
