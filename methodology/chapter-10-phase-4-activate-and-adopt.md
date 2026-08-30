<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 09: Phase 3 — Engineer & Integrate](chapter-09-phase-3-engineer-and-integrate.md) · [Contents](../README.md) · [Next: Chapter 11: Phase 5 — Operate & Assure →](chapter-11-phase-5-operate-and-assure.md)

# Chapter 10: Phase 4 — Activate & Adopt

# Phase 4 — Activate & Adopt

> **CHAPTER PURPOSE** Introduce the service progressively into live operations, enable users, validate exceptions and earn higher operating authority through evidence.

## Background and context

Phase 3 proves a system is safe to release under controlled conditions. Phase 4 is where it meets real users, workload variability and consequences, and the organization decides — deliberately and in increments — how much it will let the system do without a human in the loop. "Engineered correctly" becomes "trusted in practice" here, closed by production evidence, not demo confidence.

The central idea is progressive autonomy. A system moves through operating modes — shadow, assisted, supervised, then some bounded autonomy — and each step is justified by evidence from the step below, not by elapsed time or enthusiasm. This is covered further in [Architecture Perspective 2: Agent Architecture](../architecture/perspective-02-agent-architecture.md#1-agent-type-taxonomy) and tracked through the [Autonomy Matrix](../tools/03-system-and-governance-templates.md#12-autonomy-matrix), which assigns evidence thresholds and escalation triggers per action and case class, not to the system as a whole. A system that drafts replies and also issues refunds needs two separate autonomy rows, because the evidence needed to trust each is unrelated.

Phase 4 hands [Phase 5 — Operate & Assure](chapter-11-phase-5-operate-and-assure.md) a service proven to work for real users at a stated, evidenced level of authority, with a verified fallback path and a trained user base, so ongoing operations start from a stable baseline rather than still discovering workflow-fit problems in production.

![Figure 9. Phase 4 — Activate & Adopt: method sequence and the Operational Acceptance Review gate.](../diagrams/lifecycle-phases/phase-4-activate-and-adopt.png)

*Figure 9. Phase 4 — Activate & Adopt: method sequence and the Operational Acceptance Review gate.*

## Phase objective

Introduce the service into live operations, enable users and progressively increase authority only when evidence supports it.

"Only" is doing real work here. The most common failure is authority creeping upward informally — a supervisor who stops reviewing every case because the system "seemed fine," or a team that quietly widens a cohort because the pilot group is happy. The Autonomy Matrix exists to make each authority increase a visible, evidenced, reversible decision, rather than a drift.

## Core questions

- Can users complete real work successfully?

- Do exception and fallback paths work?

- Is trust calibrated rather than merely high?

- Which case classes are ready for the next autonomy level?

The third question deserves attention because "high trust" is easy to misread as success. A user who stops checking output because the system has been right often enough is a control failure waiting to surface, not validation. Calibrated trust means users know which cases the system handles well and which it doesn't. That is built through training and interface design — it should never be assumed.

## Method

23. Begin in shadow, recommendation or assisted mode with a defined user group and monitoring window.

24. Train users on purpose, limits, evidence, uncertainty, approvals, overrides, escalation and incident reporting.

25. Validate real input variability, workload, downstream effects and human–AI hand-offs.

26. Measure adoption, completion, outcome lift, override, escalation, complaints, incorrect actions and time saved.

27. Tune workflow, context, controls and training before expanding user scope or authority.

28. Approve autonomy separately by action, risk class and case type; provide rapid reduction or suspension paths.

Step 23's shadow or assisted mode lets behavior be observed against real traffic before output reaches a decision. It is the only way to gather production-representative evidence without production-level risk. Step 24's training list is really about judgment, not interface mechanics: what the system is uncertain about, and what to do about it. Step 26's metrics are deliberately mixed. Adoption and time-saved measure usefulness, while override, escalation and incorrect-action rates measure trustworthiness; reporting only the first set is dishonest. Step 28's separate autonomy approval by action and risk class puts the Autonomy Matrix into practice. Its rapid-reduction path matters because a system with no fast way back down cannot be corrected once trust proves miscalibrated.

## Primary artifacts

- Activation Plan

- User Enablement Pack

- Autonomy Matrix

- Operational Acceptance Tests

- Pilot Scorecard

- Feedback and Exception Log

- Operational Acceptance Record

The Autonomy Matrix is template 12 in [System and Governance Templates](../tools/03-system-and-governance-templates.md#12-autonomy-matrix). The Operational Acceptance Tests correspond to the checklist in [Readiness and Operations Templates](../tools/04-readiness-and-operations-templates.md#14-operational-acceptance-checklist) — a deliberately distinct gate from Phase 3's Production Readiness Checklist. Readiness confirms the system is safe to expose to live users; acceptance confirms it actually works for them once it is.

> **DECISION OUTCOME** Operational Acceptance Review: accept, correct, widen, reduce or suspend.

## Entry and exit conditions

| **Entry condition**                                                                  | **Exit condition**                                                                         |
|------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| Production readiness evidence is complete and a bounded activation plan is approved. | Users and operations accept the service at a stated autonomy level with verified fallback. |

The exit condition names two constituencies deliberately. A service users like but operations cannot support sustainably has not exited Phase 4 cleanly, and neither has one operations can run but users route around because it doesn't fit how they work.

## Tailoring guidance

Low-risk productivity tools may move quickly from assist to routine use. Transactional, customer-facing or regulated systems should widen by cohort, case class and authority threshold.

The pace of widening should track consequence, not enthusiasm. A well-received internal assistant with no external exposure can move fast, because mistakes are cheap to catch. A system that moves money or operates in a regulated domain should widen cohort by cohort and threshold by threshold. The Autonomy Matrix's evidence requirement is what separates a considered expansion from an informal one.

---

[← Previous: Chapter 09: Phase 3 — Engineer & Integrate](chapter-09-phase-3-engineer-and-integrate.md) · [Contents](../README.md) · [Next: Chapter 11: Phase 5 — Operate & Assure →](chapter-11-phase-5-operate-and-assure.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
