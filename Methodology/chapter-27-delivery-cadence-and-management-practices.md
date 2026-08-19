<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 26: OASIS Measurement Framework](chapter-26-oasis-measurement-framework.md) · [Contents](../README.md) · [Next: Chapter 28: Scaling and Productization →](chapter-28-scaling-and-productization.md)

# Chapter 27: Delivery Cadence and Management Practices

# Delivery Cadence and Management Practices

> **CHAPTER PURPOSE** Establish a rhythm of field observation, demonstrations, releases, outcome reviews, portfolio decisions and managed learning backlogs.

## Background and context

Chapter 26 establishes what to measure and at what cadence. This chapter turns that cadence into an operating rhythm a delivery team lives inside week to week. A measurement framework with no delivery rhythm produces reports nobody acts on; a delivery rhythm with no measurement framework produces motion nobody can prove is progress.

The cadence here is layered because different decisions need different observation windows. A production incident needs a same-day response; reallocating a pod's roadmap does not. Forcing the latter into a daily standup either starves the daily conversation of its purpose or forces a strategic call onto incomplete evidence. This chapter's five cadences — daily, weekly, fortnightly, monthly, quarterly — give each class of decision the window it needs, and map onto the reporting cadence Chapter 26 introduced: the monthly outcome review here is the same review, now with defined attendees, inputs and outputs.

This chapter hands forward to [Chapter 28 — Scaling and Productization](chapter-28-scaling-and-productization.md) the operating discipline a capability needs before it is a candidate for reuse elsewhere: no stable backlog, no management registers and no working outcome cadence means it is not ready to be productized, however well it performs for its first consumer. At enterprise scale, this same cadence reappears as the "governance cadence" in [Architecture Perspective 9 — Operations and Observability Architecture](../architecture/perspective-09-operations-and-observability-architecture.md#4-governance-cadence), which names this chapter's delivery cadence as the input its operations rollup depends on.

## Delivery cadence

Delivery, in an intelligence system, is five nested rhythms, each answering a different question at the frequency it needs. The daily pod cadence is the shortest and most operational: cases worked, blockers, incidents raised, traces reviewed, and the next experiment worth running, feeding an updated task and learning backlog rather than a status report nobody reads. The weekly working demonstration shows working behavior against representative or live cases — not a slide deck, but the system actually doing the work. This is the fastest way a team discovers that a metric everyone believed was moving in the right direction is not what it looks like in practice. It produces accepted learning, design and scope decisions, made with the whole pod in the room.

The fortnightly release cadence turns accepted learning into tested increments and a controlled rollout, producing a release manifest and deployment evidence — the same artifact the [Monitoring specification's release manifest checklist](../monitoring/observability-and-telemetry-specification.md#3-release-manifest-checklist) expects completed before any release, with a named owner and evidence against every item. The monthly outcome review is where Chapter 26's balanced scorecard gets used: outcome, adoption, intelligence, risk, service and economics evidence reviewed together, producing continue-or-correct decisions and priority changes. The quarterly portfolio review is the widest lens: value pools, dependencies, concentration risk, platform investment and funding, producing decisions to scale, resequence, fund, reframe or retire that need a quarter's worth of evidence.

| **Cadence**                  | **Primary focus**                                               | **Output**                               |
|----------------------------------|----------------------------------------------------------------------------------|--------------------------------------------|
| Daily pod cadence            | Cases, blockers, incidents, traces and next experiment.           | Updated task and learning backlog.            |
| Weekly working demonstration | Working behavior on representative or live cases.                 | Accepted learning, design and scope decisions.    |
| Fortnightly release cadence  | Tested increments and controlled rollout.                         | Release manifest and deployment evidence.         |
| Monthly outcome review       | Outcome, adoption, intelligence, risk, service and economics.     | Continue/correct decisions and priority changes.  |
| Quarterly portfolio review   | Value pools, dependencies, concentration, platform and funding.   | Scale, sequence, fund, reframe or retire.         |

## Backlog structure

A single backlog cannot serve an intelligence system well, because the work items competing for a pod's attention are not comparable — a retrieval-quality fix and a resilience improvement address different failure modes and are usually owned by different people. OASIS splits the backlog into seven streams so each kind of work gets visible, deliberate prioritization instead of being outcompeted by whichever stream is loudest that week.

The outcome backlog holds changes expected to move the metric tree directly — work traceable to Chapter 26's primary outcome and leading indicators. The user and workflow backlog covers process, interface, adoption and exception handling improvements, work that often matters more to real-world performance than any model change and is correspondingly easy to under-resource. The intelligence backlog is where context, retrieval, model, tool, harness and evaluation changes live. The risk and control backlog tracks threats, regulatory obligations, controls, audit findings and evidence gaps, deserving the same rigor as the outcome backlog even though it rarely produces a headline metric improvement. The reliability backlog covers capacity, resilience, recovery, incident response and support, a discipline a production system cannot survive without regardless of intelligence quality. The reuse backlog is where component extraction, documentation, configuration work and platform transfer live, and determines whether a capability becomes a candidate for the multi-business deployment Chapter 28 describes. The learning backlog holds unanswered assumptions, planned experiments and production cases still worth investigating.

## Management registers

A pod running six or seven parallel backlogs needs a small set of registers to keep decisions, assumptions, dependencies, risks, issues and changes visible, rather than buried inside meeting notes or one person's memory. These registers are not bureaucratic overhead — they let a pod answer, months later, why a particular decision was made.

A decision record captures its context, the evidence behind it, the owner who made the call, the date, any attached conditions, and an expiry, since a decision made under one set of circumstances should not be treated as permanent once those circumstances change. Assumptions get the same discipline: each is either converted into a test that will confirm or falsify it, or consciously accepted as a risk the team is choosing to carry, rather than left as an unexamined premise. Dependencies are recorded with a provider, a consumer, a due date and a contingency, because a dependency without a named contingency is a single point of failure the team has not yet admitted to itself.

## Agile relationship

OASIS does not replace whatever agile framework a delivery team already uses — Scrum, Kanban, or a flow-based approach all work as the mechanical layer of iteration. What OASIS adds is an outcome and evidence structure wrapped around that iteration, because velocity alone is a poor proxy for progress in an intelligence system. A sprint that closes every planned story but leaves the outcome metric unmoved, and leaves the team no more certain about a key assumption than before, has not succeeded by OASIS's standard, even if it looks successful on a conventional burndown chart. A sprint succeeds when the team produces a tested capability, meaningfully reduces material uncertainty, or measurably improves an observed outcome. Story points closed is an input to that judgment, not a substitute for it.

---

[← Previous: Chapter 26: OASIS Measurement Framework](chapter-26-oasis-measurement-framework.md) · [Contents](../README.md) · [Next: Chapter 28: Scaling and Productization →](chapter-28-scaling-and-productization.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
