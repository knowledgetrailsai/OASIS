<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 12: Phase 6 — Optimize & Scale](chapter-12-phase-6-optimize-and-scale.md) · [Contents](../README.md) · [Next: Part III: Intelligence-System Engineering and Assurance →](part-iii-intelligence-system-engineering-and-assurance.md)

# Chapter 13: Decision Gates and Evidence Model

# Decision Gates and Evidence Model

> **CHAPTER PURPOSE** Use proportionate evidence reviews to commit, proceed, release, widen, scale, redesign or retire without turning governance into ceremonial approval.

*Figure 3. The lifecycle uses evidence to justify investment, release and authority.*

## Background and context

Every one of the six lifecycle phases in Chapters 7 through 12 ends the same way: a named decision outcome, reached by reviewing a defined minimum of evidence against the specific claim the phase was meant to test. This chapter is where that recurring pattern is stated once, in full, rather than repeated with minor variation six times. It exists because gates are the mechanism that makes the rest of the methodology enforceable — a phase description is only a set of good intentions until something actually checks, at a defined point, whether its exit condition was met before the next phase is allowed to begin.

The model here is deliberately not a stage-gate bureaucracy in the pejorative sense. A gate is not a form to be completed and filed; it is a decision, made by someone accountable, on the strength of evidence that would hold up to a skeptical outsider's questions. This chapter closes [Part II: The OASIS Lifecycle](part-ii-the-oasis-lifecycle.md), and it does so deliberately at the boundary between the lifecycle phases and [Part III's](part-iii-intelligence-system-engineering-and-assurance.md) engineering and assurance material, because the evidence a gate reviews is produced by that engineering and assurance work — a gate does not generate its own evidence, it consumes what the phase and its supporting disciplines already produced.

Two artifacts make this model operable rather than aspirational. Every gate passage should be recorded using the [Decision-Gate Record](../tools/03-system-and-governance-templates.md#20-decision-gate-record), template 20 in [System and Governance Templates](../tools/03-system-and-governance-templates.md) — a six-phase engagement produces at least six of these, one per gate, and a conditional pass or hold recorded there is tracked to its due date rather than left open indefinitely. And the "evidence gated" discipline this chapter describes is one of the ten cross-cutting [Architecture Principles](../architecture/oasis-reference-architecture.md#architecture-principles) in the reference architecture, which states it as a system-design principle applying equally to lifecycle progression and to autonomy-level progression within a live system — the same discipline, checked at two different granularities.

| **Gate**               | **Decision**                                      | **Minimum evidence**                                                                           |
|-------------------------|-----------------------------------------------------|--------------------------------------------------------------------------------------------------|
| Outcome Alignment      | Commit, refine, defer or decline.                 | Outcome, baseline, owner, scope, guardrails and validation plan.                               |
| Solution Viability     | Proceed, reframe, acquire or stop.                 | Vertical slice, representative evaluation, workflow fit, failure taxonomy, risk and economics. |
| Production Readiness   | Release, remediate or hold.                       | Architecture, controls, tests, observability, recovery, ownership and runbook.                 |
| Operational Acceptance | Accept, widen, reduce or suspend.                 | Live user evidence, outcomes, exceptions, adoption, controls and autonomy case.                |
| Outcome Performance    | Continue, correct, re-scope or retire.            | Outcome, intelligence, risk, service, cost and intervention trends.                            |
| Scale and Renewal      | Replicate, productize, renew, redesign or retire. | Repeatability, demand, economics, platform fit and reassessed risk.                            |

Read across a row rather than down a column and each gate resolves to the same underlying question asked at a different point in the system's life: given what we now know, does the level of investment, exposure or authority we're about to grant still match the evidence we have for it? The six gates correspond one-to-one with the exit conditions named in Chapters 7 through 12, and the "minimum evidence" column is deliberately a floor, not a template — it names what a gate cannot responsibly be passed without, leaving the exact form of that evidence to the artifacts and templates each phase chapter already points to. Each phase chapter (Chapters 7 through 12) includes a diagram placing its gate at the end of that phase's method sequence — see [Figure 6](chapter-07-phase-1-engage-and-align.md) through [Figure 11](chapter-12-phase-6-optimize-and-scale.md), or the full set in [diagrams/lifecycle-phases/](../diagrams/lifecycle-phases/). A gate that is passed on less than this minimum has not actually been passed; it has been deferred to whichever failure eventually surfaces the gap.

## Evidence qualities

- Relevant: directly supports the gate decision and intended operating context.

- Representative: covers normal, difficult, exceptional, insufficient-evidence and adversarial cases.

- Traceable: links source, configuration, model, workflow, tool results, human actions and outcome.

- Comparable: uses baselines, thresholds and consistent definitions.

- Current: reflects the latest material model, data, workflow, control and regulatory state.

- Independent where necessary: consequential claims are challenged by a role not rewarded for release speed.

Not every gate needs every quality applied with equal weight, but a reviewer who cannot locate all six somewhere in the evidence being presented should treat that as a signal, not a formality. Relevance is the most commonly violated quality in practice — teams under deadline pressure tend to bring the evidence they already have rather than the evidence the specific decision actually needs, and a well-run gate distinguishes between the two. Representativeness matters because a system evaluated only on easy cases will look better at the gate than it performs in production, which is precisely the gap Phase 2's evaluation discipline exists to close and that later gates depend on having been closed honestly. Traceability is what makes an incident, months later, answerable rather than an open investigation — it is the same trace-and-version discipline specified in the [Monitoring specification](../monitoring/observability-and-telemetry-specification.md#2-trace-and-version-record-what-every-event-must-carry), applied to gate evidence rather than only to live telemetry. Independence is the quality organizations most often skip when they are confident, and need most when they are wrong: a claim reviewed only by the people who built the system and are rewarded for shipping it carries a structural bias no amount of good faith fully offsets, which is why regulated or high-consequence gates should route consequential claims through a role without that incentive — a pattern the [Standards](../standards/) checklists (ISO/IEC 42001, the NIST AI RMF, the EU AI Act, and the DPDP Act alignment checklists) formalize further for the specific claims each framework requires evidenced.

## Gate mechanics

A gate is a decision meeting, not a document review. The owner presents the outcome, uncertainty, failure evidence and recommended authority. Reviewers record conditions, residual risk, decisions and expiry. A conditional decision has a named owner, due date and consequence. Evidence that has not changed is referenced rather than recopied.

That first sentence is the discipline the rest of this section exists to protect. A document review can be satisfied by an evidence pack that looks complete; a decision meeting cannot be satisfied by anything less than someone accountable stating, out loud, what they know and what they don't, and other accountable people testing that statement. The owner's role at the meeting is not to defend the artifact but to represent the honest state of the system, uncertainty included — a gate presentation that hides uncertainty to secure a pass has not passed the gate, it has deferred the failure to a point where it costs more to fix. Recording conditions, residual risk and expiry is what keeps a conditional pass from quietly becoming a permanent one: a condition with no due date is not a condition, and residual risk accepted without a named owner is risk nobody is actually accountable for. The [Decision-Gate Record](../tools/03-system-and-governance-templates.md#20-decision-gate-record) template captures exactly these fields, which is why it, rather than a slide deck, is the artifact of record for each gate passage.

> **ANTI-BUREAUCRACY TEST** If removing an artifact would not weaken a decision, combine or remove it. If removing a decision would hide material risk or uncertainty, retain it.

This test is the chapter's real center of gravity, and it cuts in both directions deliberately. It is as much a license to remove ceremony as it is a discipline to keep the reviews that matter. An organization that treats every gate in this chapter as mandatory paperwork, regardless of the stakes involved, will accumulate exactly the kind of ceremonial approval process this chapter opens by rejecting — and an organization that quietly drops a gate because it's inconvenient, without applying this test honestly, will eventually discover the material risk it was there to catch, at a worse time and a higher cost than a gate review would have cost.

---

[← Previous: Chapter 12: Phase 6 — Optimize & Scale](chapter-12-phase-6-optimize-and-scale.md) · [Contents](../README.md) · [Next: Part III: Intelligence-System Engineering and Assurance →](part-iii-intelligence-system-engineering-and-assurance.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
