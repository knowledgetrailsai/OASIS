<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: Readiness and Operations Templates](04-readiness-and-operations-templates.md) · [Chapter 32: Templates, Checklists and Tools](../methodology/chapter-32-templates-checklists-and-tools.md)

# Tools: Risk and Scale Templates

> **PURPOSE** Fillable versions of the risk-tracking and scaling artifacts named in [Chapter 32](../methodology/chapter-32-templates-checklists-and-tools.md). The Risk and Control Register below is the single shared register referenced across the [Standards](../standards/) and [Security](../security/agentic-ai-threat-and-control-checklist.md) checklists — populate it once per system and cross-reference it rather than keeping separate risk logs per framework, per the anti-bureaucracy test in [Chapter 13](../methodology/chapter-13-decision-gates-and-evidence-model.md).

Covers templates 17–18 of 20. See also: [Outcome and Portfolio Templates](01-outcome-and-portfolio-templates.md) · [Workflow and Intelligence Templates](02-workflow-and-intelligence-templates.md) · [System and Governance Templates](03-system-and-governance-templates.md) · [Readiness and Operations Templates](04-readiness-and-operations-templates.md).

## Background and context

These two templates carry the ongoing, cross-cutting work that outlives any single build: tracking risk continuously rather than only at gates, and deciding whether a capability that started as a one-off build should become a shared, supported platform asset. The Risk and Control Register in particular is deliberately the most heavily cross-referenced artifact in this toolkit — see the note at the top of its section — because a risk tracked once in a shared register survives audits, framework changes and personnel turnover far better than the same risk described independently in five different documents.

---

## 17. Risk and Control Register

**Chapter 32 minimum content:** Risk, cause, impact, inherent rating, controls, tests, residual rating, owner, treatment, evidence and review.

**Primary source:** [Chapter 20 — Governance, Compliance and Regulatory Engineering](../methodology/chapter-20-governance-compliance-and-regulatory-engineering.md); referenced throughout the [Standards](../standards/) checklists and the [Security checklist](../security/agentic-ai-threat-and-control-checklist.md).

| Risk ID | Description | Cause | Impact | Inherent rating | Controls in place | Control tests | Residual rating | Owner | Treatment (mitigate/transfer/avoid/accept) | Evidence | Last reviewed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| | | | | | | | | | | | |
| | | | | | | | | | | | |

This register is the single most cross-referenced artifact in the OASIS toolkit — every Standards checklist row and every Security checklist row that carries an unresolved risk should have a corresponding Risk ID here rather than a duplicate description. When adding a row sourced from a specific framework, note the source (e.g., "EU AI Act Art. 9", "OWASP ASI06") in the Description or Cause field so the cross-reference is traceable in both directions.

---

## 18. Scale and Productization Assessment

**Chapter 32 minimum content:** Demand, repeatability, consumers, contract stability, configuration, tenancy, support, economics, risk and roadmap.

**Primary source:** [Chapter 28 — Scaling and Productization](../methodology/chapter-28-scaling-and-productization.md).

```yaml
scale_and_productization_assessment:
  capability_name: ""
  demand:
    current_consumers: []
    pipeline_demand: ""
  repeatability:
    variance_across_consumers: "low | medium | high"
    what_varies: []                 # what changes per consumer vs. what's fixed
  contract_stability:
    interface_stability: "stable | evolving | volatile"
    breaking_change_history: ""
  configuration_vs_customization:
    configurable_parameters: []
    custom_build_required_for: []
  tenancy_model: "single-tenant | multi-tenant | hybrid"
  support_model:
    ownership: ""
    sla: ""
  economics:
    unit_cost_at_current_scale: ""
    unit_cost_at_target_scale: ""
    reuse_rationale: ""              # see Ch.25 platform-reuse guidance — directional, not a fixed quota
  risk_at_scale:
    concentration_risk: ""
    blast_radius_if_shared_component_fails: ""
  roadmap:
    productization_decision: "keep bespoke | productize | retire"
    next_milestone: ""
```

---

[← Back to Contents](../README.md) · [← Previous: Readiness and Operations Templates](04-readiness-and-operations-templates.md) · [Chapter 32: Templates, Checklists and Tools](../methodology/chapter-32-templates-checklists-and-tools.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
