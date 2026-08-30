<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: AI Engineering Maturity Model](oasis-ai-engineering-maturity-model.md)

# Assessment: OASIS Maturity Scorecard Template

> **PURPOSE** The fillable instance of the [AI Engineering Maturity Model](oasis-ai-engineering-maturity-model.md) — copy this template per assessment cycle (per organization, business unit, or major system, depending on scope), score each of the nine dimensions with real evidence, and track the result over time rather than as a one-off exercise.

**Primary OASIS source:** [Assessment: OASIS AI Engineering Maturity Model](oasis-ai-engineering-maturity-model.md).

## Background and context

A maturity score is only as trustworthy as the evidence behind it. That is why this template requires an evidence field alongside every score. "We think we're at Level 3," with no named artifact behind it, is really a Level 1 assessment practice making a Level 3 claim. Fill the evidence field with a specific, checkable reference — a completed template, a named forum's meeting record, a dashboard link — not a general impression.

Re-run this assessment on a fixed cadence — quarterly is a reasonable default, aligned with the portfolio review cadence in [Chapter 24](../methodology/chapter-24-roles-teams-and-governance-forums.md#governance-forums). Keep prior cycles rather than overwriting them, so the trend stays visible. A dimension stuck at the same level for three consecutive cycles, despite a stated target, is itself a signal worth raising at the next portfolio review. A stalled dimension usually means the gap is organizational — no owner, no budget, no forum — rather than technical.

## Scorecard

```yaml
assessment:
  scope: ""                        # e.g. "Enterprise-wide", "Retail Operations business unit", "Claims Copilot system"
  assessed_by: ""
  assessment_date: ""
  previous_assessment_date: ""     # blank if this is the first cycle
  next_scheduled_assessment: ""

dimensions:
  - name: "Outcome and Portfolio Discipline"
    current_level: null            # 0-4, per the maturity model
    target_level: null
    evidence: ""                   # specific artifact/forum reference, not a general impression
    gap: ""                        # what's missing between current and target
    owner: ""
    trend_since_last_cycle: "up | flat | down | first-cycle"

  - name: "Lifecycle and Evidence Gates"
    current_level: null
    target_level: null
    evidence: ""
    gap: ""
    owner: ""
    trend_since_last_cycle: ""

  - name: "Intelligence and Agent Engineering"
    current_level: null
    target_level: null
    evidence: ""
    gap: ""
    owner: ""
    trend_since_last_cycle: ""

  - name: "Architecture and Platform"
    current_level: null
    target_level: null
    evidence: ""
    gap: ""
    owner: ""
    trend_since_last_cycle: ""

  - name: "Security and Responsible AI"
    current_level: null
    target_level: null
    evidence: ""
    gap: ""
    owner: ""
    trend_since_last_cycle: ""

  - name: "Governance and Regulatory Compliance"
    current_level: null
    target_level: null
    evidence: ""
    gap: ""
    owner: ""
    trend_since_last_cycle: ""

  - name: "Operations and AgentOps"
    current_level: null
    target_level: null
    evidence: ""
    gap: ""
    owner: ""
    trend_since_last_cycle: ""

  - name: "Economics and FinOps"
    current_level: null
    target_level: null
    evidence: ""
    gap: ""
    owner: ""
    trend_since_last_cycle: ""

  - name: "Scaling and Reuse"
    current_level: null
    target_level: null
    evidence: ""
    gap: ""
    owner: ""
    trend_since_last_cycle: ""

result:
  overall_level: null              # = minimum current_level across all nine dimensions -- do not average
  weakest_dimension: ""            # the dimension driving the overall_level
  narrative_summary: ""            # 2-3 sentences: what this cycle's result means and what to do next
  escalated_to: ""                 # forum or role this result was reported to, per Chapter 24
```

## Reading and escalating a result

A completed scorecard is not the deliverable. The decision it informs is. Route the result to the forum matched to its stakes, per [Chapter 24's governance forum table](../methodology/chapter-24-roles-teams-and-governance-forums.md#governance-forums). An overall level below what a system's risk classification requires (see [Chapter 19](../methodology/chapter-19-security-and-responsible-ai-engineering.md)) is an Architecture/Risk review matter, not a monthly-outcome-review footnote. A weakest dimension that has been flat or declining across two or more cycles belongs at the quarterly portfolio review as a funding and ownership question, not a technical backlog item. A dimension stuck below target for that long usually means nobody has been made accountable for closing it.

---

[← Back to Contents](../README.md) · [← Previous: AI Engineering Maturity Model](oasis-ai-engineering-maturity-model.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
