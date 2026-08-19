<!-- SPDX-License-Identifier: MIT -->

[← Previous: Part V: Measurement, Scaling and Institutionalization](part-v-measurement-scaling-and-institutionalization.md) · [Contents](../README.md) · [Next: Chapter 27: Delivery Cadence and Management Practices →](chapter-27-delivery-cadence-and-management-practices.md)

# Chapter 26: OASIS Measurement Framework

# OASIS Measurement Framework

> **CHAPTER PURPOSE** Use a balanced scorecard that joins business outcomes with adoption, intelligence quality, risk, reliability, economics, reuse and FDE effectiveness.

## Background and context

Part V shifts focus from building to running. Earlier chapters cover how a pod stands up an intelligence system and how a platform accumulates shared capability. This chapter and the four after it cover running what has been built, and knowing with evidence whether it should keep running. A portfolio can look busy — releases shipping, dashboards populated, users logging in — while failing to produce the outcomes it was funded for. The measurement framework closes that gap between activity and value.

Intelligence systems fail in ways conventional software rarely does. A system can be fast, available and correct in every request and still be wrong in aggregate: biased toward one segment, eroding trust, or costing more in human intervention than it saves. The eight scorecard dimensions below look at a system from enough angles that a problem in one cannot hide behind good numbers in another.

Two companion documents carry this framework into daily practice. The [Monitoring: Observability and Telemetry Specification](../monitoring/observability-and-telemetry-specification.md) turns the operational and intelligence-quality dimensions here into six instrumented planes — service, intelligence, risk, human, economic and outcome — with collection points and alert triggers. This chapter says what to measure and why; that specification says where and what should page someone. The [Outcome Metric Tree](../tools/01-outcome-and-portfolio-templates.md#4-outcome-metric-tree) template gives each initiative a place to define its primary outcome, leading indicators, operational drivers and guardrails, and the [Outcome Scorecard](../tools/04-readiness-and-operations-templates.md#15-outcome-scorecard) is the recurring artifact that reports against it. Chapter 27 takes the cadences here — daily, monthly, quarterly, event-driven — and builds the delivery rhythm and backlog structure around them.

## Balanced OASIS scorecard

No single number tells an organization whether an intelligence system is working. A model that answers correctly ninety percent of the time can still be a poor investment if the failures land on the highest-stakes cases, or if fixing them costs more than the rest is worth. The balanced scorecard requires evidence across eight dimensions before anyone declares success, spanning further than a conventional software scorecard because these failure modes go beyond availability and defect rate.

Business outcome sits at the center: the primary metric the initiative was funded to move, leading indicators, the outcome's distribution across segments, guardrails against unacceptable side effects, and attribution confidence — since claiming credit for a movement the system did not cause is a common way a scorecard misleads its sponsors. Adoption and operations show whether people actually use the system: eligible versus active use, completion rates, time genuinely saved after rework, and overrides and exceptions that signal a trust problem or a capability gap. Intelligence quality is specific to AI systems: correctness, groundedness against source evidence, retrieval precision, correct tool selection and invocation, task completion, and two measures easy to omit — abstention (does the system know when not to answer) and calibration (is its stated confidence justified).

Risk and guardrails track what a scorecard exists to prevent: incorrect actions taken, complaints, policy breaches, bias indicators, incidents and the near misses that preceded them. Service and reliability cover familiar ground — availability, latency, error rates, recovery time, capacity headroom, dependency health — necessary but no longer sufficient alone. Economics puts cost beside value: cost per successful outcome, intervention cost, failure-adjusted value, realized savings, and marginal cost at scale. Platform reuse asks whether the investment compounds: time saved, shared-service adoption, reduced duplicate builds, consumers supported — connecting directly to Chapter 28. FDOE effectiveness measures the pod itself: time to a working vertical slice, time to production, learning velocity, transfer readiness, and how much the business still depends on the pod to run what should by now be self-sustaining.

| **Dimension**           | **Representative measures**                                                                                 |
|-------------------------|-------------------------------------------------------------------------------------------------------------|
| Business outcome        | Primary outcome, leading indicators, distribution, guardrails and attribution confidence.                   |
| Adoption and operations | Eligible use, active use, completion, time saved, rework, override and exception load.                      |
| Intelligence quality    | Correctness, groundedness, retrieval, tool use, task completion, abstention and calibration.                |
| Risk and guardrails     | Incorrect actions, complaints, policy breaches, bias indicators, incidents and near misses.                 |
| Service and reliability | Availability, latency, errors, recovery, capacity and dependency health.                                    |
| Economics               | Cost per success, intervention cost, failure-adjusted value, savings and marginal scale cost.               |
| Platform reuse          | Time saved, shared-service adoption, duplicate reduction and supported consumers.                           |
| FDOE effectiveness      | Time to vertical slice, time to production, learning velocity, transfer readiness and dependency reduction. |

## Metric architecture

A scorecard with eight dimensions is coherent only if its metrics relate to one another in a defined way, not as an unstructured list. OASIS organizes every metric tree around a primary outcome — the number the initiative exists to move — supported by leading indicators that change earlier and faster, and bounded by guardrails that catch harm the primary metric would not otherwise reveal. Operational and intelligence-quality measures sit underneath and explain why the outcome moved. A leading indicator that never actually leads should be revisited or retired.

Every metric needs seven things before it is trustworthy: a named owner, a precise definition, a data source, a reporting cadence, a target, a segmentation so an average cannot hide a disparity, and an action threshold. A metric without a threshold is a data point; a metric with one is a control. The [Outcome Metric Tree](../tools/01-outcome-and-portfolio-templates.md#4-outcome-metric-tree) template captures this structure and is explicit that a tree with no guardrail row is incomplete.

Automation that shifts cost, risk or workload elsewhere in the organization does not count as value. A process that looks faster because exceptions are dumped on a downstream team, or because risk quietly transferred to a function without visibility to manage it, has relocated a cost, not created value. Treating that relocation as an efficiency gain is a damaging measurement error, and the metric architecture above is built to make it harder to get away with.

## Outcome reporting cadence

Different questions need answers at different speeds, so the framework does not force every metric onto one rhythm. A daily or weekly operational review covers incidents, quality shifts and exceptions — things needing a response in hours or days. A monthly outcome review joins business, user, intelligence, risk, service and cost evidence into one picture of whether the initiative is working. A quarterly portfolio review steps back further, to investment, dependencies, reuse, scale and retirement decisions that only make sense over a longer horizon, usually across more than one initiative. An event-driven review triggers whenever something material changes — a new model, provider, data change, jurisdiction, purpose, or a change in permitted autonomy. Waiting for the next scheduled review to notice that is itself a control failure.

This cadence is the backbone Chapter 27 builds its delivery rhythm around. The daily, monthly and quarterly reviews reappear there as concrete ceremonies with defined attendees, inputs and outputs, and the [Outcome Scorecard](../tools/04-readiness-and-operations-templates.md#15-outcome-scorecard) template is explicit that it should be reviewed at the cadence Chapter 27 sets. At enterprise scale, this cadence feeds the rollup views in [Architecture Perspective 9 — Operations and Observability Architecture](../architecture/perspective-09-operations-and-observability-architecture.md#1-enterprise-operations-dashboard-rollup-structure), where per-system scorecards aggregate into a portfolio view reviewed by governance forums.

## Evidence-based continuation

The scorecard's purpose is to make four kinds of decision defensible with evidence, not opinion. It supports continuing an initiative when value and controls are demonstrably stable. It supports correcting course when the outcome remains viable but performance has degraded — the everyday work of the next chapter's delivery cadence. It supports re-scoping when evidence shows the causal mechanism was wrong from the start, or the problem boundary was drawn incorrectly — uncomfortable to admit, but cheaper than admitting it late. And it supports stopping, when sustained evidence shows value, safety or economics do not hold up, regardless of what has already been invested. A measurement framework that cannot produce a credible "stop" decision is not really measuring anything.

---

[← Previous: Part V: Measurement, Scaling and Institutionalization](part-v-measurement-scaling-and-institutionalization.md) · [Contents](../README.md) · [Next: Chapter 27: Delivery Cadence and Management Practices →](chapter-27-delivery-cadence-and-management-practices.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
