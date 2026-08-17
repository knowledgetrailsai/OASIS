<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 20: Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) · [Reference Framework Alignment Index →](../references/regulatory-framework-alignment-index.md)

# Standard: EU AI Act Alignment Checklist

> **PURPOSE** Map EU AI Act (Regulation (EU) 2024/1689) obligation categories to OASIS mechanisms and artifacts. This is a structuring aid, not legal advice or a conformity assessment. Applicability (role as provider/deployer/importer/distributor, risk tier, effective dates by provision, and required notified-body involvement) must be confirmed against the current official text and guidance for your jurisdiction and use case.

**Primary OASIS source:** [Chapter 20 — Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md), [Chapter 19 — Security and Responsible AI Engineering](../Methodology/chapter-19-security-and-responsible-ai-engineering.md).

## Step 0 — Role and risk-tier determination (do this first)

| # | Question | OASIS mechanism | Artifact | Status |
|---|---|---|---|---|
| 1 | What role does the organization hold for this system — provider, deployer, importer, distributor, or product manufacturer? | Regulatory engineering method step 48 | Ch. 20 step 48 | |
| 2 | Is the system prohibited (Art. 5, unacceptable risk), high-risk (Annex III / Art. 6), limited-risk (transparency obligations, Art. 50), minimal-risk, or a General-Purpose AI (GPAI) model? | AI use-case risk classification | Ch. 20 — AI Use-Case Risk Classification and AI/System Record | |
| 3 | Which jurisdiction(s), sectors and populations does the system touch? | Regulatory Applicability Register | Ch. 20 — Regulatory Applicability Register | |

## High-risk system obligations (Chapter III, if applicable)

| # | Obligation area | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 4 | Risk management system (Art. 9) | Continuous, iterative risk identification, estimation, evaluation and mitigation across the lifecycle. | Risk and control register, decision gates | [Risk and Control Register](../Methodology/chapter-32-templates-checklists-and-tools.md#17-risk-and-control-register); Ch. 13 | | |
| 5 | Data and data governance (Art. 10) | Training/validation/testing data quality, relevance, representativeness, bias examination. | Data readiness assessment, evaluation dataset | [Data and Knowledge Readiness Assessment](../Methodology/chapter-32-templates-checklists-and-tools.md#8-data-and-knowledge-readiness-assessment); [Evaluation Strategy and Dataset](../Methodology/chapter-32-templates-checklists-and-tools.md#9-evaluation-strategy-and-dataset) | | |
| 6 | Technical documentation (Art. 11, Annex IV) | System description, design, capabilities, limitations sufficient for conformity assessment. | Intelligence-system blueprint | [Intelligence-System Blueprint](../Methodology/chapter-32-templates-checklists-and-tools.md#11-intelligence-system-blueprint) | | |
| 7 | Record-keeping / logging (Art. 12) | Automatic logging of events across the system lifecycle for traceability. | Records and audit domain, AgentOps telemetry | Ch. 20 Records and audit; Ch. 21 monitoring planes | | |
| 8 | Transparency and instructions for deployers (Art. 13) | Clear instructions, capabilities, limitations, human-oversight measures communicated. | Service runbook, transparency property | [Service Runbook](../Methodology/chapter-32-templates-checklists-and-tools.md#16-service-runbook); Ch. 19 Transparency | | |
| 9 | Human oversight (Art. 14) | Effective oversight — authority, information, time, override, escalation. | Human oversight and decision-authority matrix | Ch. 20 — Human Oversight and Decision-Authority Matrix; [Autonomy Matrix](../Methodology/chapter-32-templates-checklists-and-tools.md#12-autonomy-matrix) | | |
| 10 | Accuracy, robustness and cybersecurity (Art. 15) | Appropriate accuracy levels, resilience to errors/faults/attacks. | Evaluation and reliability engineering, defense-in-depth | Ch. 18; Ch. 19 defense-in-depth layers | | |
| 11 | Quality management system (Art. 17) | Provider QMS covering compliance strategy, design controls, testing, post-market monitoring. | OASIS operating model and lifecycle | Ch. 6; Ch. 7–12 | | |
| 12 | Conformity assessment and CE marking (Art. 43, 48) | Internal control or third-party assessment before placing on market. | Not covered by OASIS — engage qualified conformity body | — | | |
| 13 | Post-market monitoring (Art. 72) | Active, systematic collection and review of performance data after deployment. | Outcome scorecard, monitoring | [Outcome Scorecard](../Methodology/chapter-32-templates-checklists-and-tools.md#15-outcome-scorecard); Ch. 21 | | |
| 14 | Serious incident reporting (Art. 73) | Report serious incidents to market surveillance authority within required timeframes. | Incident, complaint and regulatory reporting procedure | Ch. 20 — Incident, Complaint and Regulatory Reporting Procedure | | |

## Transparency obligations for limited-risk systems (Art. 50)

| # | Obligation | OASIS mechanism | Artifact | Status |
|---|---|---|---|---|
| 15 | Disclose AI interaction to natural persons (chatbots, etc.), unless obvious from context. | Transparency property, interface design | Ch. 19 Transparency; [Human–AI Workflow Blueprint](../Methodology/chapter-32-templates-checklists-and-tools.md#7-human-ai-workflow-blueprint) | |
| 16 | Label synthetic/AI-generated or manipulated content. | Output layer controls | Ch. 19 Output layer | |
| 17 | Disclose emotion-recognition or biometric-categorization use where applicable. | Regulatory applicability register | Ch. 20 | |

## General-Purpose AI (GPAI) model obligations (Chapter V, if applicable as a provider)

| # | Obligation | OASIS mechanism | Artifact | Status |
|---|---|---|---|---|
| 18 | Technical documentation and information for downstream providers. | Model, vendor and due-diligence record | Ch. 20 — Model, Vendor and Open-Source Due-Diligence Record | |
| 19 | Copyright policy and training-data summary. | Not covered by OASIS — legal/IP function input required | — | |
| 20 | Systemic-risk model obligations (evaluation, adversarial testing, incident tracking, cybersecurity) — if the model is classified as systemic risk. | Evaluation strategy, agentic threat model | Ch. 18; Ch. 19 Agentic threat model | |

---

[← Back to Contents](../README.md) · [Chapter 20: Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) · [Reference Framework Alignment Index →](../references/regulatory-framework-alignment-index.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
