<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 32: Templates, Checklists and Tools](../methodology/chapter-32-templates-checklists-and-tools.md) · [Schemas](../Schemas/)

# Examples: One Initiative, Seven Artifacts

A single fictional initiative — the **AP Invoice Exception Triage Assistant** at a fictional manufacturer, Meridian Manufacturing — followed through seven of the twenty OASIS artifacts, in lifecycle order. Each file validates against its corresponding [Schemas/](../Schemas/) JSON Schema and demonstrates the level of specificity Chapter 32 calls "strong": real numbers, named owners, honest uncertainty, not placeholder text.

This is a representative subset, not all twenty artifacts — filling all twenty for one fictional initiative would demonstrate volume, not judgment. The seven chosen span every lifecycle phase and both the two structural artifacts (Accountability, Gate Record) that apply throughout.

## The scenario

Meridian Manufacturing's accounts-payable team manually triages roughly 4,000 invoice exceptions a month — mismatched amounts, missing purchase orders, suspected duplicates — each requiring a human to research and decide a resolution. The initiative proposes an AI assistant that researches each exception and drafts a recommended resolution for a human AP analyst to approve, not an autonomous payment system.

## Artifacts included

| # | Artifact | Phase | File |
|---|---|---|---|
| 1 | Opportunity Assessment | Engage & Align | [01-opportunity-assessment.yaml](01-opportunity-assessment.yaml) |
| 2 | Outcome Charter | Engage & Align | [02-outcome-charter.yaml](02-outcome-charter.yaml) |
| 8 | Data and Knowledge Readiness Assessment | Discover & Validate | [08-data-and-knowledge-readiness-assessment.yaml](08-data-and-knowledge-readiness-assessment.yaml) |
| 12 | Autonomy Matrix | Activate & Adopt | [12-autonomy-matrix.yaml](12-autonomy-matrix.yaml) |
| 13 | Production Readiness Checklist | Engineer & Integrate | [13-production-readiness-checklist.yaml](13-production-readiness-checklist.yaml) |
| 15 | Outcome Scorecard | Operate & Assure | [15-outcome-scorecard.yaml](15-outcome-scorecard.yaml) |
| 20 | Decision-Gate Record | Outcome Alignment gate | [20-decision-gate-record.yaml](20-decision-gate-record.yaml) |

## What to notice

The Opportunity Assessment recommends "proceed" but flags a real, unresolved risk (duplicate-detection false positives) rather than presenting a clean case — Chapter 32's point that a strong assessment is honest about uncertainty. The Outcome Charter's `causal_hypothesis` field is filled in with an actual mechanism, not a restated goal. The Autonomy Matrix gives drafting and payment-hold actions separate rows with different evidence thresholds, per Chapter 32 §12's warning against collapsing distinct-risk actions into one system-wide rating. The Decision-Gate Record carries a real `expiry` date on its one condition, which is the field Chapter 13 says gets skipped most often.
