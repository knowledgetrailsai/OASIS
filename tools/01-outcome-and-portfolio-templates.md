<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 32: Templates, Checklists and Tools](../methodology/chapter-32-templates-checklists-and-tools.md) · [Next: Workflow and Intelligence Templates →](02-workflow-and-intelligence-templates.md)

# Tools: Outcome and Portfolio Templates

> **PURPOSE** Fillable versions of the outcome-and-portfolio artifacts named in [Chapter 32](../methodology/chapter-32-templates-checklists-and-tools.md#1-opportunity-assessment). Chapter 32 states each artifact's minimum useful content in one line; this file turns that line into a structure a team can actually fill in. Copy the relevant section into your own document, delete fields that don't apply, and keep only what's needed to make, evidence, and revisit the decision (the [PRACTICALITY rule](../methodology/chapter-32-templates-checklists-and-tools.md#template-use-rule)).

Covers templates 1–5 of 20. See also: [Workflow and Intelligence Templates](02-workflow-and-intelligence-templates.md) · [System and Governance Templates](03-system-and-governance-templates.md) · [Readiness and Operations Templates](04-readiness-and-operations-templates.md) · [Risk and Scale Templates](05-risk-and-scale-templates.md).

## Background and context

These five templates carry the earliest and highest-leverage decisions in an engagement: whether an opportunity is worth pursuing, what outcome it commits to, and what it will cost against what it returns. Chapter 32 states each artifact only as a one-line minimum-content statement because the chapter's job is to name the decision each artifact supports, not to prescribe its exact layout — a methodology chapter that shipped a rigid form would fight every organization's existing templates rather than sit alongside them. This file exists because a delivery team still needs *something* to open on day one of an engagement; treat every field below as a starting point to edit, not a fixed schema to match exactly.

---

## 1. Opportunity Assessment

**Chapter 32 minimum content:** Problem, affected workflow, outcome, baseline availability, stakeholders, intelligence fit, dependencies, risks, horizon and recommendation.

**Primary source:** [Chapter 5 — Opportunity Portfolio and Transformation Horizons](../methodology/chapter-05-opportunity-portfolio-and-transformation-horizons.md); used at the entry to [Chapter 7 — Phase 1: Engage & Align](../methodology/chapter-07-phase-1-engage-and-align.md).

```yaml
opportunity_assessment:
  title: ""
  submitted_by: ""
  date: ""
  problem_statement: ""            # the problem in the business's own language, not a solution
  affected_workflow: ""            # which process/workflow this touches, and who performs it today
  candidate_outcome: ""            # the measurable result this opportunity could produce
  baseline_availability:
    is_baseline_data_available: true|false
    source: ""
    known_gaps: ""
  stakeholders:
    outcome_owner: ""
    affected_teams: []
    executive_sponsor: ""
  intelligence_fit:                # does this need AI/agents, or a simpler fix?
    suitability: "strong | moderate | weak | not-a-fit"
    rationale: ""
  dependencies: []                 # systems, data, decisions this depends on
  risks: []                        # early risk flags, not a full assessment
  transformation_horizon: "H1 automate | H2 augment | H3 reinvent"   # see Ch.5
  recommendation: "proceed | park | decline"
  recommendation_rationale: ""
```

---

## 2. Outcome Charter

**Chapter 32 minimum content:** Outcome statement, population, baseline, target, causal hypothesis, scope, exclusions, owner, guardrails, timeline and next gate.

**Primary source:** [Chapter 3 — Enterprise AI Transformation Direction](../methodology/chapter-03-enterprise-ai-transformation-direction.md); [Chapter 7 — Phase 1: Engage & Align](../methodology/chapter-07-phase-1-engage-and-align.md).

```yaml
outcome_charter:
  outcome_statement: ""            # one sentence: what measurably improves, for whom
  population: ""                   # who/what is in scope (customers, cases, regions, products)
  baseline:
    metric: ""
    current_value: ""
    measurement_period: ""
  target:
    value: ""
    by_date: ""
  causal_hypothesis: ""            # why this intervention should move this metric
  scope:
    included: []
    excluded: []
  owner: ""                        # the single accountable outcome owner
  guardrail_metrics: []            # metrics that must not regress while pursuing the target
  timeline:
    start: ""
    next_gate: ""
    next_gate_date: ""
  next_gate_reference: ""          # which Ch.13 gate this charter feeds
```

---

## 3. Outcome Contract

**Chapter 32 minimum content:** Charter plus service responsibilities, measurement, data sources, review cadence, remedies, funding and renewal/exit conditions.

**Primary source:** [Chapter 1 — OASIS Executive Overview](../methodology/chapter-01-oasis-executive-overview.md) (outcome contract concept); [Chapter 8 — Phase 2: Discover & Validate](../methodology/chapter-08-phase-2-discover-and-validate.md).

```yaml
outcome_contract:
  charter_reference: ""            # link to the Outcome Charter this extends
  service_responsibilities:
    provider_commits_to: []
    business_commits_to: []
  measurement:
    metric_definitions: ""         # link to the Outcome Metric Tree
    measurement_method: ""
    data_sources: []
  review_cadence: ""                # e.g. monthly scorecard review, quarterly gate review
  remedies:
    if_target_missed: ""
    if_guardrail_breached: ""
  funding:
    model: "fixed | outcome-linked | hybrid"
    amount_or_formula: ""
  renewal_and_exit:
    renewal_trigger: ""
    exit_trigger: ""
    exit_procedure: ""
  signed_off_by:
    outcome_owner: ""
    provider_lead: ""
    date: ""
```

---

## 4. Outcome Metric Tree

**Chapter 32 minimum content:** Primary outcome, leading indicators, operational drivers, guardrails, definitions, sources, segmentation and thresholds.

**Primary source:** [Chapter 26 — OASIS Measurement Framework](../methodology/chapter-26-oasis-measurement-framework.md).

| Level | Metric name | Definition | Data source | Segmentation | Threshold / target | Owner |
|---|---|---|---|---|---|---|
| Primary outcome | | | | | | |
| Leading indicator | | | | | | |
| Leading indicator | | | | | | |
| Operational driver | | | | | | |
| Operational driver | | | | | | |
| Guardrail | | | | | | |
| Guardrail | | | | | | |

Add rows as needed. A metric tree with no guardrail row is incomplete — every outcome pursued through an intelligence system should have at least one metric that catches an unacceptable side effect, per the [Autonomy Matrix](../methodology/chapter-32-templates-checklists-and-tools.md#12-autonomy-matrix) escalation logic in [System and Governance Templates](03-system-and-governance-templates.md).

---

## 5. Value and Risk Case

**Chapter 32 minimum content:** Benefits, build/run/intervention/failure costs, uncertainty, impact, autonomy, data, exposure, reversibility and mitigation.

**Primary source:** [Chapter 22 — Economics, FinOps and Sustainability](../methodology/chapter-22-economics-finops-and-sustainability.md); [Chapter 20 — Governance, Compliance and Regulatory Engineering](../methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) (risk classification).

```yaml
value_and_risk_case:
  benefits:
    quantified: []                 # e.g. cost avoided, revenue lift, cycle-time reduction, with method
    qualitative: []                 # e.g. risk reduction, option value, strategic positioning
  costs:
    build_cost: ""
    run_cost: ""                    # ongoing model/infra/tool cost per Ch.22 unit economics
    intervention_cost: ""           # human time on exceptions/oversight
    failure_cost: ""                # expected cost of failure modes, weighted by likelihood
  uncertainty:
    confidence_level: "low | medium | high"
    key_assumptions: []
  risk_classification:               # see Ch.20 Risk Classification
    impact: "low | medium | high | critical"
    autonomy: "shadow | assisted | supervised | bounded-autonomous"
    data_sensitivity: "public | internal | confidential | restricted"
    exposure: ""                     # scale/population exposed
  reversibility: "easily reversible | reversible with cost | irreversible"
  mitigation: []                     # controls that reduce risk given the above classification
  net_recommendation: "proceed | proceed with conditions | decline"
```

---

[← Back to Contents](../README.md) · [Chapter 32: Templates, Checklists and Tools](../methodology/chapter-32-templates-checklists-and-tools.md) · [Next: Workflow and Intelligence Templates →](02-workflow-and-intelligence-templates.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
