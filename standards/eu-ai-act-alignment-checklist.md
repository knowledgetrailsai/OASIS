<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 20: Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) · [Reference Framework Alignment Index →](../references/regulatory-framework-alignment-index.md)

# Standard: EU AI Act Alignment Checklist

> **PURPOSE** Map EU AI Act (Regulation (EU) 2024/1689) obligation categories to OASIS mechanisms and artifacts. This is a structuring aid, not legal advice or a conformity assessment. Applicability (role as provider/deployer/importer/distributor, risk tier, effective dates by provision, and required notified-body involvement) must be confirmed against the current official text and guidance for your jurisdiction and use case.

**Primary OASIS source:** [Chapter 20 — Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md), [Chapter 19 — Security and Responsible AI Engineering](../Methodology/chapter-19-security-and-responsible-ai-engineering.md).

## Background and context

Regulation (EU) 2024/1689, known as the EU AI Act, is the first comprehensive, horizontal AI-specific law enacted by a major regulator. It entered into force on 1 August 2024 and applies on a **staggered timeline**: prohibited-practice provisions (Art. 5) applied from 2 February 2025; obligations on general-purpose AI (GPAI) model providers applied from 2 August 2025; most high-risk system obligations apply from 2 August 2026 for Annex III use cases, with a longer runway to 2 August 2027 for AI systems that are safety components of products already regulated under other EU product-safety law (Annex I). Because provisions phase in at different times, the applicable obligation set for any given system depends on both its risk classification and the current date — always confirm current status against the official text rather than assuming full applicability.

The Act has **extraterritorial reach**: it applies to any provider placing an AI system on the EU market, any deployer using an AI system within the EU, and — notably — to providers and deployers located outside the EU whose AI system's *output* is used within the EU, regardless of where the organization is headquartered. This means a non-EU enterprise with no EU legal entity can still be in scope if its AI system's output reaches EU users or EU-based decisions.

The Act's core structure is a **risk-based tiered system**:

- **Unacceptable risk (prohibited, Art. 5)** — certain uses are banned outright, e.g. social scoring by public authorities, real-time remote biometric identification in public spaces (with narrow law-enforcement exceptions), and manipulative or exploitative AI targeting vulnerabilities.
- **High-risk (Annex III use cases, or Annex I safety components)** — systems used in contexts like employment and worker management, access to essential services and credit scoring, law enforcement, migration and border control, and administration of justice, or AI that is a safety component of a regulated product (medical devices, machinery, etc.). These carry the most extensive obligations, summarized in the table below.
- **Limited risk** — systems subject only to transparency obligations under Art. 50 (e.g., chatbots must disclose they are AI; synthetic content must be labeled).
- **Minimal risk** — the large majority of AI systems, with no AI-Act-specific obligations beyond voluntary codes of conduct.
- **General-Purpose AI (GPAI) models** — a separate obligation track (Chapter V) for providers of foundation/general-purpose models, with an additional, heavier obligation set for models classified as carrying "systemic risk" based on a compute-threshold test.

Non-compliance carries significant financial exposure: fines of up to **€35 million or 7% of global annual turnover** (whichever is higher) for violations of the prohibited-practices provisions, and up to €15 million or 3% of global annual turnover for most other violations — making risk-tier determination (Step 0 below) the highest-leverage first move in any EU AI Act workstream.

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
