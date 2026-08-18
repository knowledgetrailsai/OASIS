<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 15: Data and Knowledge Engineering](chapter-15-data-and-knowledge-engineering.md) · [Contents](../README.md) · [Next: Chapter 17: Enterprise Integration and Tool Engineering →](chapter-17-enterprise-integration-and-tool-engineering.md)

# Chapter 16: Human–AI Workflow and Experience Engineering

# Human–AI Workflow and Experience Engineering

> **CHAPTER PURPOSE** Redesign work around complementary human and machine strengths, explicit authority, usable oversight, trust calibration and accessible experiences.

## Background and context

Chapter 14 establishes what the intelligence system is capable of, and Chapter 15 makes sure it is fed with governed, sufficient evidence. Neither chapter answers a more basic organizational question: once a capable, well-informed system exists, who is actually allowed to do what with it, and how does a human and a machine hand a piece of work back and forth without either party losing the thread? That is the gap this chapter closes. It is also, in practice, where most AI programs succeed or fail — not on model quality, but on whether the surrounding work was redesigned to fit the new division of labor, or whether a capable system was simply dropped into a process built for humans acting alone.

This is deliberately positioned as engineering, not change management bolted on afterward. A workflow that never specifies who has authority over which decision, or what a person sees before approving an AI-prepared action, is not a workflow with a training gap — it is an unfinished design. The templates and blueprints in this chapter exist so that authority, evidence and fallback are decided at design time, alongside the model and the data pipeline, rather than negotiated informally once the system is already in front of users. The [Process Architecture](../architecture/perspective-03-process-architecture.md) perspective takes the view this chapter deliberately does not: where Chapter 16 designs a single hand-off between a human and an agent at one step, Process Architecture maps how that step sits inside a longer business process — claims intake through settlement, requisition through onboarding — that spans many steps, many systems and, usually, a process owner who is not the same person configuring the agent. Use that perspective once a workflow redesigned here needs to be located inside its wider process map, and its section on handback design in particular when the trigger for returning control to a human needs to be made explicit across an entire process rather than a single step.

Chapter 16 also produces the artifact that the rest of the methodology repeatedly points back to. The [Human–AI Workflow Blueprint](../tools/02-workflow-and-intelligence-templates.md#7-human-ai-workflow-blueprint) template turns the blueprint described below into a fillable specification, and it is worth completing early: Chapter 17's tool contracts assume the authority model is already decided, and Chapter 18's evaluation of escalation correctness assumes the escalation triggers named here already exist. Get the workflow design right first, and the tool and evaluation work that follows has something concrete to build against.

OASIS treats adoption as workflow engineering, not post-build communication. The target is a redesigned operating system in which human judgment, AI capability, deterministic controls and enterprise systems each perform the work for which they are best suited — not because that division is fashionable, but because each of those four actors is reliably good at different things and reliably bad at others, and a workflow that ignores the difference wastes the strongest capability of whichever actor it misuses.

## Human–AI workflow blueprint

Redesigning a workflow starts by naming what is actually changing and why, one row at a time, for every meaningful step in the process. The table below is the minimum set of design decisions a workflow needs before it is safe to build; skipping any one of them tends to surface later as an incident, an override nobody can explain, or a feature nobody trusts.

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

The first two rows are where most designs go wrong, because it is tempting to describe the AI contribution in terms of the technology ("uses a language model to draft a response") rather than the cognitive work it is actually replacing or augmenting ("drafts a first-pass response for human review, using retrieved policy text as evidence"). The second framing is the one that lets the rest of the table be filled in coherently: it tells you what evidence a human reviewer needs to see, what a fallback should look like if the draft is unusable, and what authority the human retains by virtue of reviewing before anything is sent. Authority deserves the same discipline — "who may decide" should resolve to a named role or a rule, not to "the AI, usually," because a workflow with no crisp answer to that question is one where accountability quietly evaporates the first time something goes wrong.

The blueprint is not paperwork to be filled in once and filed away. The [Human–AI Workflow Blueprint template](../tools/02-workflow-and-intelligence-templates.md#7-human-ai-workflow-blueprint) expresses every row above as a structured, step-by-step specification — AI role, human role, authority, evidence shown, interface, approval requirement, override mechanism, fallback, escalation trigger and target, and a feedback loop that links corrections back into the evaluation dataset described in Chapter 18. Filling it out per step, rather than describing the workflow in the abstract, is what turns "a human reviews the output" into something a build team can actually implement and a reviewer can actually rely on.

## Progressive autonomy model

Autonomy is not a single on/off decision made once at launch; it is a ladder a workflow climbs deliberately, one rung at a time, as evidence accumulates that the system performs reliably at the rung below.

| **Mode**         | **System role**                               | **Human role**                                |
|------------------|-----------------------------------------------|-----------------------------------------------|
| Shadow           | Observe and produce non-operational output.   | Perform normal work; compare retrospectively. |
| Recommend        | Offer advice and evidence.                    | Decide and act.                               |
| Assist           | Prepare work or populate transactions.        | Review, edit and submit.                      |
| Approve-to-act   | Propose a bounded action.                     | Explicitly approve execution.                 |
| Exception-based  | Execute routine cases within rules.           | Review exceptions and samples.                |
| Bounded autonomy | Plan and execute within authority and limits. | Own policy, monitor and intervene.            |

Shadow mode exists to answer one question cheaply and without operational risk: does this system's judgment agree with an experienced human's, across a representative range of cases, before anyone's job or a customer's outcome depends on it? Skipping shadow mode to save time is usually a false economy — it is the cheapest place to discover a systematic blind spot, long before it shows up as an incident in exception-based or bounded-autonomy mode. Each subsequent rung hands the system a little more of the work and a little less of the review, and the decision to move up a rung should be evidence-based rather than calendar-based: a workflow graduates from assist to approve-to-act because its evaluation results (Chapter 18) and production override rates support it, not because it has been live for a quarter. It is equally normal, and not a failure, for a workflow to move back down a rung — after a policy change, a model change, or a sustained rise in override rate — until confidence is re-established.

Most enterprise workflows never need to reach bounded autonomy, and that is fine: exception-based operation, where the system handles routine cases within clear rules and a human reviews exceptions and a sample of the rest, is a durable and appropriate end state for a large share of processes, particularly wherever a single wrong action is expensive or hard to reverse.

## Trust calibration

The objective is appropriate reliance, not maximum trust — a distinction that is easy to state and surprisingly hard to design for, because both directions of miscalibration look fine on the surface. A user who defers to every AI recommendation looks efficient right up until the recommendation is wrong and the deference was automatic rather than considered; a user who quietly re-does the AI's work every time looks diligent right up until you realize the workflow redesign delivered no benefit at all, because nobody actually trusts the system enough to rely on it.

Interfaces are the primary lever available to correct this. They should reveal source quality, uncertainty, limitations, the scope of the proposed action, and the consequence of approving it — not as a compliance disclosure buried in a tooltip, but as information positioned where a reviewer will actually see it before they act. Correction and escalation need to be genuinely easy, not merely possible in theory through a support ticket three clicks away; an override path people avoid using is an override path that will not get used when it matters. And because trust calibration is a behavioral property, it has to be measured behaviorally: track over-reliance, under-use, rubber-stamping (approvals granted without evidence of review — fast, uniform approval times are a useful proxy), automation bias, and the amount of workload that has quietly migrated into exception handling rather than disappeared. A workflow that looks efficient on its headline metrics while its exception queue silently grows is not actually working.

## Change and capability

Adoption work has to start earlier than most programs schedule it. Engaging users during discovery and evaluation — while the workflow is still being designed — surfaces objections and edge cases while they are still cheap to address, rather than after a training rollout has already been built around a design nobody who does the work actually validated. By the time training is the first point of contact, the roles, incentives and quality checks around the job have usually already been decided without the people who will live inside them.

That is the deeper point behind redesigning roles, capacity, incentives, quality checks and performance measures alongside the workflow itself, rather than leaving them as an afterthought: a workflow can be technically correct and still fail if the people operating it are still measured, incentivized or resourced as though the old process were still running. Training itself needs to go beyond "how to use the interface" to cover purpose, limits, how to interpret the evidence shown, what an approval actually commits the approver to, how to report an incident, and what data-handling responsibilities come with the role — the things a person needs to use appropriate judgment, not just the mechanics of clicking through a screen. Accessibility, language, channel and digital-literacy needs belong in that same design pass, not as a retrofit for a population that turns out to be excluded by the default interface.

Finally, treat the transition itself as something to measure, not just the steady state: time-to-proficiency, correct use, override rates, workaround behavior (people quietly going around the system rather than using it), and users' perceived sense of control are all early signals of a workflow design that is or is not landing — well before the outcome metrics in Chapter 18 have had time to move.

---

[← Previous: Chapter 15: Data and Knowledge Engineering](chapter-15-data-and-knowledge-engineering.md) · [Contents](../README.md) · [Next: Chapter 17: Enterprise Integration and Tool Engineering →](chapter-17-enterprise-integration-and-tool-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
