<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 20: Governance, Compliance and Regulatory Engineering](../methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) · [Reference Framework Alignment Index →](../references/regulatory-framework-alignment-index.md)

# Standard: ISO/IEC 42001 Alignment Checklist

> **PURPOSE** Map ISO/IEC 42001 (Artificial Intelligence Management System, AIMS) clauses and Annex A controls to the OASIS mechanisms and artifacts that can produce conforming evidence. This is an alignment aid, not a conformity assessment — verify current clause text and applicability against the official standard before use.

**Primary OASIS source:** [Chapter 20 — Governance, Compliance and Regulatory Engineering](../methodology/chapter-20-governance-compliance-and-regulatory-engineering.md), [Chapter 19 — Security and Responsible AI Engineering](../methodology/chapter-19-security-and-responsible-ai-engineering.md), [Chapter 24 — Roles, Teams and Governance Forums](../methodology/chapter-24-roles-teams-and-governance-forums.md).

## Background and context

ISO/IEC 42001:2023 is the world's first international management-system standard written specifically for artificial intelligence. It was developed by ISO/IEC JTC 1/SC 42 (the joint technical committee responsible for AI standardization) and published in December 2023. Its full title is "Information technology — Artificial intelligence — Management system," and it defines requirements for establishing, implementing, maintaining and continually improving an **AI Management System (AIMS)** — the organizational structure, policies, processes and controls through which an organization governs how it develops, provides or uses AI.

The standard follows ISO's **Annex SL high-level structure**, the same ten-clause skeleton used by ISO 9001 (quality management) and ISO 27001 (information security management). Clauses 1–3 are scope, normative references and definitions; clauses 4–10 are the operative requirements: Context of the organization (4), Leadership (5), Planning (6), Support (7), Operation (8), Performance evaluation (9) and Improvement (10). Because of this shared structure, an organization that already runs an ISO 27001 or ISO 9001 management system does not need to build a parallel governance apparatus for AI — it can extend its existing management system with AI-specific clauses and Annex A controls, which is the approach most enterprise adopters take in practice.

Annex A of ISO 42001 lists control objectives and controls specific to AI — organized around themes such as AI policies, internal organization, resources for AI systems, AI system life cycle, data for AI systems, information for interested parties, use of AI systems, and third-party and customer relationships. These are analogous in spirit to ISO 27001's Annex A information-security controls, but scoped to AI-specific risks such as training-data provenance, AI system impact assessment, and the intended-use/restricted-use boundary of a deployed system.

Unlike the NIST AI RMF (voluntary, non-certifiable — see the [NIST AI RMF Alignment Checklist](nist-ai-rmf-alignment-checklist.md)), ISO 42001 is **certifiable**: an accredited third-party certification body can audit an organization's AIMS and issue a certificate of conformity, in the same way certification bodies issue ISO 27001 certificates today. This matters commercially — enterprise customers, public-sector procurement processes and increasingly regulators are beginning to ask for ISO 42001 certification (or evidence of an equivalent AIMS) as a trust signal, distinct from and in addition to any binding legal obligation such as the EU AI Act. ISO 42001 itself does not certify compliance with any specific law; it certifies that an organization has a systematic, auditable management system for governing AI, which in practice makes it easier to demonstrate compliance with laws such as the EU AI Act or India's DPDP Act because the underlying evidence trail already exists.

**How to use this checklist:** for each row, record status (Not started / In progress / Evidenced), the OASIS artifact that carries the evidence, and the accountable owner per the [Responsibility Assignment Matrix](../methodology/chapter-32-templates-checklists-and-tools.md#19-responsibility-assignment-matrix). Combine or split rows to match your organization's existing management-system documentation — do not duplicate an existing ISO 9001/27001 control if one already satisfies the clause. If certification is the goal, engage an accredited certification body early; this checklist supports internal readiness, not the certification audit itself.

## Clause 4–7: Organizational context, leadership, planning and support

| # | ISO/IEC 42001 area | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 1 | 4.1–4.2 | Determine internal/external issues and interested-party needs relevant to the AIMS. | Opportunity and transformation direction | [Opportunity Assessment](../methodology/chapter-32-templates-checklists-and-tools.md#1-opportunity-assessment); Ch. 3 | | |
| 2 | 4.3–4.4 | Define AIMS scope and establish, implement, maintain and improve the system. | OASIS operating model and lifecycle | Ch. 6 Operating Model; Ch. 7–12 phase gates | | |
| 3 | 5.1–5.3 | Leadership commitment, AI policy, roles/responsibilities/authorities. | Decision rights and governance forums | [Responsibility Assignment Matrix](../methodology/chapter-32-templates-checklists-and-tools.md#19-responsibility-assignment-matrix); Ch. 24 | | |
| 4 | 6.1 | Actions to address risks and opportunities; AI system impact assessment. | Value/risk case, risk classification | [Value and Risk Case](../methodology/chapter-32-templates-checklists-and-tools.md#5-value-and-risk-case); Ch. 20 Risk Classification | | |
| 5 | 6.2 | AI objectives and planning to achieve them. | Outcome contract targets | [Outcome Charter](../methodology/chapter-32-templates-checklists-and-tools.md#2-outcome-charter) | | |
| 6 | 7.1–7.3 | Resources, competence, awareness. | Roles, teams, capability model | Ch. 24; Ch. 16 Change and capability | | |
| 7 | 7.4–7.5 | Communication and documented information control. | Records and audit domain | Ch. 20 Governance Scope — Records and audit | | |

## Clause 8–10: Operation, performance evaluation and improvement

| # | ISO/IEC 42001 area | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 8 | 8.1 | Operational planning and control across the AI life cycle. | Six-phase lifecycle | Ch. 7–12; Ch. 13 Decision Gates | | |
| 9 | 8.2 (Annex A ref.) | AI system impact assessment prior to deployment. | Responsible AI impact assessment | Ch. 20 — Data Protection and AI Impact Assessments | | |
| 10 | 9.1 | Monitoring, measurement, analysis and evaluation. | Outcome measurement and scorecard | [Outcome Scorecard](../methodology/chapter-32-templates-checklists-and-tools.md#15-outcome-scorecard); Ch. 26 | | |
| 11 | 9.2 | Internal audit. | Audit and evidence plan | Ch. 20 — Audit and Evidence Plan | | |
| 12 | 9.3 | Management review. | Governance forums cadence | Ch. 24 Governance Forums; Ch. 27 Delivery Cadence | | |
| 13 | 10.1–10.2 | Nonconformity, corrective action, continual improvement. | Failure taxonomy and incident handling | [Failure Taxonomy](../methodology/chapter-32-templates-checklists-and-tools.md#10-failure-taxonomy); Ch. 20 — Incident, Complaint and Regulatory Reporting Procedure | | |

## Annex A control themes (representative, not exhaustive)

| # | Annex A theme | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|
| 14 | A.4 — Documentation of AI system objectives | Outcome contract | [Outcome Contract](../methodology/chapter-32-templates-checklists-and-tools.md#3-outcome-contract) | | |
| 15 | A.5 — Roles and responsibilities related to AI | Decision rights | Ch. 6; Ch. 24 | | |
| 16 | A.6 — Resources for AI systems (data, tooling, compute, human oversight) | Intelligence-system blueprint | [Intelligence-System Blueprint](../methodology/chapter-32-templates-checklists-and-tools.md#11-intelligence-system-blueprint) | | |
| 17 | A.7 — AI system life cycle | Phase model | Ch. 7–12 | | |
| 18 | A.8 — Data for AI systems | Data readiness and lineage | [Data and Knowledge Readiness Assessment](../methodology/chapter-32-templates-checklists-and-tools.md#8-data-and-knowledge-readiness-assessment); Ch. 15 | | |
| 19 | A.9 — Information for interested parties (transparency) | Transparency and disclosure | Ch. 19 Responsible AI properties — Transparency | | |
| 20 | A.10 — Use of AI systems (intended use, restrictions) | Autonomy matrix and authority limits | [Autonomy Matrix](../methodology/chapter-32-templates-checklists-and-tools.md#12-autonomy-matrix) | | |
| 21 | A.6 / A.10 — Third-party and customer relationships (model/vendor due diligence) | Vendor due diligence | Ch. 20 — Model, Vendor and Open-Source Due-Diligence Record | | |

---

[← Back to Contents](../README.md) · [Chapter 20: Governance, Compliance and Regulatory Engineering](../methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) · [Reference Framework Alignment Index →](../references/regulatory-framework-alignment-index.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
