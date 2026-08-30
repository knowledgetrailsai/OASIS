<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 20: Governance, Compliance and Regulatory Engineering](../methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) · [Reference Framework Alignment Index →](../references/regulatory-framework-alignment-index.md)

# Standard: NIST AI Risk Management Framework (AI RMF 1.0 + Generative AI Profile) Alignment Checklist

> **PURPOSE** Map the four NIST AI RMF functions — Govern, Map, Measure, Manage — to OASIS mechanisms and artifacts. This is an alignment aid, not a certification of conformance; confirm current NIST guidance (AI RMF 1.0 and the Generative AI Profile, NIST AI 600-1) before use.

**Primary OASIS source:** [Chapter 20 — Governance, Compliance and Regulatory Engineering](../methodology/chapter-20-governance-compliance-and-regulatory-engineering.md), [Chapter 18 — Evaluation and Reliability Engineering](../methodology/chapter-18-evaluation-and-reliability-engineering.md), [Chapter 13 — Decision Gates and Evidence Model](../methodology/chapter-13-decision-gates-and-evidence-model.md).

**Deeper standard source:** [Compass's NIST-AI-RMF.md](https://github.com/knowledgetrailsai/responsible-ai/blob/main/09-tools-and-frameworks/NIST-AI-RMF.md) — this checklist maps the four functions to OASIS mechanisms; Compass carries the fuller framework treatment.

## Background and context

The NIST AI Risk Management Framework (AI RMF 1.0) was published by the U.S. National Institute of Standards and Technology in January 2023, developed under a mandate from the National AI Initiative Act with extensive multi-stakeholder public input. Unlike ISO/IEC 42001, it is **voluntary and non-certifiable** — there is no accredited third-party audit and no certificate to obtain. It is best understood as a common vocabulary and a structured way of thinking about AI risk, meant to be adapted to an organization's context rather than certified against.

The framework is organized around **four core functions**, each containing categories and subcategories of practice:

- **GOVERN** — the foundational, cross-cutting function. It establishes the culture, policies, roles and accountability structures that make the other three functions possible. Unlike Map/Measure/Manage, Govern is not applied once per system; it operates continuously across the organization's entire AI portfolio.
- **MAP** — establishes context: what is this AI system for, who does it affect, what are its components, and what risks and benefits does that context imply. Map happens early and is revisited whenever context changes materially.
- **MEASURE** — analyzes, benchmarks and tracks identified risks and trustworthiness characteristics (validity, safety, security, privacy, fairness, explainability, accountability) using appropriate qualitative and quantitative methods.
- **MANAGE** — allocates resources to identified risks on a regular basis, prioritizes response, and monitors the effectiveness of risk treatments over time.

In July 2024, NIST published a companion document, the **Generative AI Profile (NIST AI 600-1)**, which identifies risks that are novel to or exacerbated by generative AI — such as confabulation (hallucination), information integrity, harmful bias and homogenization, and value-chain/component-integration risks in agentic systems — and cross-references each one back to the four core functions. That profile is the primary source for the "Generative AI Profile" section below.

The AI RMF is widely used in two ways: first, as a baseline internal risk taxonomy for organizations with no other mandated framework, because it is free, well-documented, and jurisdiction-neutral; and second, as a reference point for organizations with U.S. federal exposure, since U.S. federal agencies are directed to align with it under OMB Memorandum M-24-10. NIST also publishes a **Crosswalk** mapping AI RMF functions to ISO/IEC 42001 Annex A controls and to other frameworks, which is useful when an organization is pursuing more than one framework simultaneously (see the [Reference Framework Alignment Index](../references/regulatory-framework-alignment-index.md) for guidance on running multiple checklists together).

## GOVERN — policies, accountability and culture

| # | AI RMF category | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 1 | Govern 1 | Legal/regulatory/risk-tolerance policies established and integrated. | Regulatory engineering method | Ch. 20 steps 48–53 | | |
| 2 | Govern 2 | Roles and responsibilities for AI risk clearly defined. | Decision rights, RACI | [Responsibility Assignment Matrix](../methodology/chapter-32-templates-checklists-and-tools.md#19-responsibility-assignment-matrix); Ch. 6 | | |
| 3 | Govern 3 | Workforce diversity, equity and organizational culture for risk management. | Change and capability | Ch. 16; Ch. 24 | | |
| 4 | Govern 4 | Risk-management processes and outcomes documented and improved. | Risk and control register | [Risk and Control Register](../methodology/chapter-32-templates-checklists-and-tools.md#17-risk-and-control-register) | | |
| 5 | Govern 5 | Mechanisms for input from external/internal stakeholders. | Governance forums | Ch. 24 | | |
| 6 | Govern 6 | Third-party risks (vendors, model providers, open source) addressed. | Vendor due-diligence record | Ch. 20 — Model, Vendor and Open-Source Due-Diligence Record | | |

## MAP — context and risk identification

| # | AI RMF category | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 7 | Map 1 | Context established: intended purpose, users, deployment setting. | Outcome charter, process map | [Outcome Charter](../methodology/chapter-32-templates-checklists-and-tools.md#2-outcome-charter); [Process and Decision Map](../methodology/chapter-32-templates-checklists-and-tools.md#6-process-and-decision-map) | | |
| 8 | Map 2 | Categorization of the AI system (capabilities, data, autonomy). | Risk classification | Ch. 20 Risk Classification (impact, autonomy, data, exposure, scale) | | |
| 9 | Map 3 | Benefits of the AI system are mapped. | Value and risk case | [Value and Risk Case](../methodology/chapter-32-templates-checklists-and-tools.md#5-value-and-risk-case) | | |
| 10 | Map 4 | Risks and benefits from third-party components mapped. | Vendor due diligence, tool catalogue | Ch. 20; [Intelligence-System Blueprint](../methodology/chapter-32-templates-checklists-and-tools.md#11-intelligence-system-blueprint) | | |
| 11 | Map 5 | Impacts to individuals, groups, communities, society mapped. | Responsible AI impact assessment | Ch. 19 Responsible AI properties; Ch. 20 — Data Protection and AI Impact Assessments | | |

## MEASURE — analysis and assessment of risk

| # | AI RMF category | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 12 | Measure 1 | Appropriate methods/metrics identified and applied. | Evaluation strategy | [Evaluation Strategy and Dataset](../methodology/chapter-32-templates-checklists-and-tools.md#9-evaluation-strategy-and-dataset); Ch. 18 | | |
| 13 | Measure 2 | Evaluation for trustworthy characteristics (validity, safety, security, privacy, fairness, explainability). | Responsible AI properties as test dimensions | Ch. 19 Responsible AI properties; Ch. 18 | | |
| 14 | Measure 3 | Mechanisms for tracking identified risks over time. | Risk and control register, scorecard | [Risk and Control Register](../methodology/chapter-32-templates-checklists-and-tools.md#17-risk-and-control-register); [Outcome Scorecard](../methodology/chapter-32-templates-checklists-and-tools.md#15-outcome-scorecard) | | |
| 15 | Measure 4 | Feedback (incidents, user reports, monitoring) informs measurement. | Failure taxonomy, monitoring | [Failure Taxonomy](../methodology/chapter-32-templates-checklists-and-tools.md#10-failure-taxonomy); Ch. 21 monitoring planes | | |

## MANAGE — risk prioritization and response

| # | AI RMF category | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 16 | Manage 1 | Risk responses prioritized and planned based on impact. | Decision-gate record, residual risk | [Decision-Gate Record](../methodology/chapter-32-templates-checklists-and-tools.md#20-decision-gate-record); Ch. 13 | | |
| 17 | Manage 2 | Risk treatment (mitigate, transfer, avoid, accept) documented. | Risk and control register | [Risk and Control Register](../methodology/chapter-32-templates-checklists-and-tools.md#17-risk-and-control-register) | | |
| 18 | Manage 3 | Third-party risks managed against policies and residual acceptance. | Vendor due diligence, residual-risk acceptance | Ch. 20 — Regulatory Change-Impact Assessment and Residual-Risk Acceptance | | |
| 19 | Manage 4 | Risk-treatment effectiveness monitored; incident response and recovery. | Containment and emergency control, service runbook | Ch. 19 Containment and emergency control; [Service Runbook](../methodology/chapter-32-templates-checklists-and-tools.md#16-service-runbook) | | |

## Generative AI Profile — additional risks to track

| # | GAI risk area | OASIS mechanism | Artifact |
|---|---|---|---|
| 20 | Confabulation / hallucination | Evaluation groundedness checks, output validation layer | Ch. 18; Ch. 19 Output layer controls |
| 21 | Data privacy leakage via prompts/context/memory | Context layer controls, memory policy | Ch. 19 Context layer; Ch. 14 Memory Policy |
| 22 | Harmful bias and homogenization | Responsible AI fairness property, evaluation dataset diversity | Ch. 19; [Evaluation Strategy and Dataset](../methodology/chapter-32-templates-checklists-and-tools.md#9-evaluation-strategy-and-dataset) |
| 23 | Dangerous, violent or hateful content | Model and output layer controls | Ch. 19 Model and Output layers |
| 24 | Information integrity / synthetic content disclosure | Transparency property, output labeling | Ch. 19 Transparency |
| 25 | Value chain and component integration risks (agentic, multi-tool) | Agentic threat model | Ch. 19 Agentic threat model |

---

[← Back to Contents](../README.md) · [Chapter 20: Governance, Compliance and Regulatory Engineering](../methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) · [Reference Framework Alignment Index →](../references/regulatory-framework-alignment-index.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
