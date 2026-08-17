<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 20: Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) · [Reference Framework Alignment Index →](../references/regulatory-framework-alignment-index.md)

# Standard: NIST AI Risk Management Framework (AI RMF 1.0 + Generative AI Profile) Alignment Checklist

> **PURPOSE** Map the four NIST AI RMF functions — Govern, Map, Measure, Manage — to OASIS mechanisms and artifacts. This is an alignment aid, not a certification of conformance; confirm current NIST guidance (AI RMF 1.0 and the Generative AI Profile, NIST AI 600-1) before use.

**Primary OASIS source:** [Chapter 20 — Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md), [Chapter 18 — Evaluation and Reliability Engineering](../Methodology/chapter-18-evaluation-and-reliability-engineering.md), [Chapter 13 — Decision Gates and Evidence Model](../Methodology/chapter-13-decision-gates-and-evidence-model.md).

## GOVERN — policies, accountability and culture

| # | AI RMF category | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 1 | Govern 1 | Legal/regulatory/risk-tolerance policies established and integrated. | Regulatory engineering method | Ch. 20 steps 48–53 | | |
| 2 | Govern 2 | Roles and responsibilities for AI risk clearly defined. | Decision rights, RACI | [Responsibility Assignment Matrix](../Methodology/chapter-32-templates-checklists-and-tools.md#19-responsibility-assignment-matrix); Ch. 6 | | |
| 3 | Govern 3 | Workforce diversity, equity and organizational culture for risk management. | Change and capability | Ch. 16; Ch. 24 | | |
| 4 | Govern 4 | Risk-management processes and outcomes documented and improved. | Risk and control register | [Risk and Control Register](../Methodology/chapter-32-templates-checklists-and-tools.md#17-risk-and-control-register) | | |
| 5 | Govern 5 | Mechanisms for input from external/internal stakeholders. | Governance forums | Ch. 24 | | |
| 6 | Govern 6 | Third-party risks (vendors, model providers, open source) addressed. | Vendor due-diligence record | Ch. 20 — Model, Vendor and Open-Source Due-Diligence Record | | |

## MAP — context and risk identification

| # | AI RMF category | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 7 | Map 1 | Context established: intended purpose, users, deployment setting. | Outcome charter, process map | [Outcome Charter](../Methodology/chapter-32-templates-checklists-and-tools.md#2-outcome-charter); [Process and Decision Map](../Methodology/chapter-32-templates-checklists-and-tools.md#6-process-and-decision-map) | | |
| 8 | Map 2 | Categorization of the AI system (capabilities, data, autonomy). | Risk classification | Ch. 20 Risk Classification (impact, autonomy, data, exposure, scale) | | |
| 9 | Map 3 | Benefits of the AI system are mapped. | Value and risk case | [Value and Risk Case](../Methodology/chapter-32-templates-checklists-and-tools.md#5-value-and-risk-case) | | |
| 10 | Map 4 | Risks and benefits from third-party components mapped. | Vendor due diligence, tool catalogue | Ch. 20; [Intelligence-System Blueprint](../Methodology/chapter-32-templates-checklists-and-tools.md#11-intelligence-system-blueprint) | | |
| 11 | Map 5 | Impacts to individuals, groups, communities, society mapped. | Responsible AI impact assessment | Ch. 19 Responsible AI properties; Ch. 20 — Data Protection and AI Impact Assessments | | |

## MEASURE — analysis and assessment of risk

| # | AI RMF category | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 12 | Measure 1 | Appropriate methods/metrics identified and applied. | Evaluation strategy | [Evaluation Strategy and Dataset](../Methodology/chapter-32-templates-checklists-and-tools.md#9-evaluation-strategy-and-dataset); Ch. 18 | | |
| 13 | Measure 2 | Evaluation for trustworthy characteristics (validity, safety, security, privacy, fairness, explainability). | Responsible AI properties as test dimensions | Ch. 19 Responsible AI properties; Ch. 18 | | |
| 14 | Measure 3 | Mechanisms for tracking identified risks over time. | Risk and control register, scorecard | [Risk and Control Register](../Methodology/chapter-32-templates-checklists-and-tools.md#17-risk-and-control-register); [Outcome Scorecard](../Methodology/chapter-32-templates-checklists-and-tools.md#15-outcome-scorecard) | | |
| 15 | Measure 4 | Feedback (incidents, user reports, monitoring) informs measurement. | Failure taxonomy, monitoring | [Failure Taxonomy](../Methodology/chapter-32-templates-checklists-and-tools.md#10-failure-taxonomy); Ch. 21 monitoring planes | | |

## MANAGE — risk prioritization and response

| # | AI RMF category | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 16 | Manage 1 | Risk responses prioritized and planned based on impact. | Decision-gate record, residual risk | [Decision-Gate Record](../Methodology/chapter-32-templates-checklists-and-tools.md#20-decision-gate-record); Ch. 13 | | |
| 17 | Manage 2 | Risk treatment (mitigate, transfer, avoid, accept) documented. | Risk and control register | [Risk and Control Register](../Methodology/chapter-32-templates-checklists-and-tools.md#17-risk-and-control-register) | | |
| 18 | Manage 3 | Third-party risks managed against policies and residual acceptance. | Vendor due diligence, residual-risk acceptance | Ch. 20 — Regulatory Change-Impact Assessment and Residual-Risk Acceptance | | |
| 19 | Manage 4 | Risk-treatment effectiveness monitored; incident response and recovery. | Containment and emergency control, service runbook | Ch. 19 Containment and emergency control; [Service Runbook](../Methodology/chapter-32-templates-checklists-and-tools.md#16-service-runbook) | | |

## Generative AI Profile — additional risks to track

| # | GAI risk area | OASIS mechanism | Artifact |
|---|---|---|---|
| 20 | Confabulation / hallucination | Evaluation groundedness checks, output validation layer | Ch. 18; Ch. 19 Output layer controls |
| 21 | Data privacy leakage via prompts/context/memory | Context layer controls, memory policy | Ch. 19 Context layer; Ch. 14 Memory Policy |
| 22 | Harmful bias and homogenization | Responsible AI fairness property, evaluation dataset diversity | Ch. 19; [Evaluation Strategy and Dataset](../Methodology/chapter-32-templates-checklists-and-tools.md#9-evaluation-strategy-and-dataset) |
| 23 | Dangerous, violent or hateful content | Model and output layer controls | Ch. 19 Model and Output layers |
| 24 | Information integrity / synthetic content disclosure | Transparency property, output labeling | Ch. 19 Transparency |
| 25 | Value chain and component integration risks (agentic, multi-tool) | Agentic threat model | Ch. 19 Agentic threat model |

---

[← Back to Contents](../README.md) · [Chapter 20: Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) · [Reference Framework Alignment Index →](../references/regulatory-framework-alignment-index.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
