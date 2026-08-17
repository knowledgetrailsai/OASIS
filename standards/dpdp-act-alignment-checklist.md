<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 20: Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) · [Reference Framework Alignment Index →](../references/regulatory-framework-alignment-index.md)

# Standard: India Digital Personal Data Protection (DPDP) Act, 2023 and Rules, 2025 — Alignment Checklist

> **PURPOSE** Map DPDP Act, 2023 and DPDP Rules, 2025 obligation categories to OASIS mechanisms and artifacts, for AI systems that process personal data of individuals (Data Principals) in scope of the Act. This is a structuring aid, not legal advice. Confirm current provisions, notified effective dates, and thresholds (including for Significant Data Fiduciary designation) against the official Act, Rules and any MeitY notifications.

**Primary OASIS source:** [Chapter 20 — Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md), [Chapter 15 — Data and Knowledge Engineering](../Methodology/chapter-15-data-and-knowledge-engineering.md), [Chapter 19 — Security and Responsible AI Engineering](../Methodology/chapter-19-security-and-responsible-ai-engineering.md).

## Data Fiduciary core obligations

| # | Obligation area | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 1 | Notice (Sec. 5) | Clear, itemized notice of personal data processed and purpose, in English or a scheduled language, before or at time of consent request. | Data governance domain, transparency property | Ch. 20 Data and privacy; Ch. 19 Transparency | | |
| 2 | Consent (Sec. 6) | Free, specific, informed, unconditional, unambiguous consent with clear affirmative action; as easy to withdraw as to give. | Regulatory applicability register; consent capture in workflow | Ch. 20; [Human–AI Workflow Blueprint](../Methodology/chapter-32-templates-checklists-and-tools.md#7-human-ai-workflow-blueprint) | | |
| 3 | Legitimate uses without consent (Sec. 7) | Identify and document any processing relying on a legitimate-use ground instead of consent. | Regulatory Applicability Register | Ch. 20 | | |
| 4 | General obligations of Data Fiduciary (Sec. 8) | Accuracy and completeness of data used for decisions; reasonable security safeguards; breach notification; erasure on purpose fulfillment/withdrawal; grievance redressal; processing via Data Processor under contract. | Data readiness, security controls, incident procedure | [Data and Knowledge Readiness Assessment](../Methodology/chapter-32-templates-checklists-and-tools.md#8-data-and-knowledge-readiness-assessment); Ch. 19 defense-in-depth; Ch. 20 — Incident, Complaint and Regulatory Reporting Procedure | | |
| 5 | Children's and persons-with-disability data (Sec. 9) | Verifiable parental/lawful-guardian consent; no tracking, behavioral monitoring or targeted advertising directed at children; exemptions must be verified. | Regulatory applicability register, risk classification | Ch. 20 | | |
| 6 | Significant Data Fiduciary obligations (Sec. 10) | If designated: Data Protection Officer, independent data-protection impact assessment and audit, additional obligations as notified. | Data protection and AI impact assessment | Ch. 20 — Data Protection and AI Impact Assessments | | |

## Data Principal rights (Sec. 11–14)

| # | Right | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 7 | Right to access information (Sec. 11) | Summary of personal data processed and processing activities on request. | Records and audit, AI/system record | Ch. 20 — AI/System Record | | |
| 8 | Right to correction and erasure (Sec. 12) | Correct inaccurate/incomplete data; erase data no longer necessary for the stated purpose. | Data lineage and retention controls | Ch. 15; Ch. 20 Change and retirement | | |
| 9 | Right of grievance redressal (Sec. 13) | Accessible means to register grievances, respond within prescribed timelines. | Incident, complaint and regulatory reporting procedure | Ch. 20 | | |
| 10 | Right to nominate (Sec. 14) | Mechanism for a Data Principal to nominate another individual to exercise rights on death/incapacity. | Not a system-design concern — process/legal function | — | | |

## Cross-border transfer, exemptions and enforcement

| # | Area | Requirement (summary) | OASIS mechanism | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 11 | Cross-border transfer (Sec. 16) | Transfers permitted except to countries restricted by Central Government notification; contractual/technical safeguards. | Regulatory applicability register, model/vendor due diligence | Ch. 20 — Model, Vendor and Open-Source Due-Diligence Record | | |
| 12 | Exemptions (Sec. 17) | Identify any applicable exemptions (state functions, research/statistics, legal proceedings, etc.) and their scope. | Regulatory applicability register | Ch. 20 | | |
| 13 | Data Protection Board and penalties (Sec. 18–33) | Awareness of complaint/inquiry process and penalty exposure for non-compliance; maintain evidence trail. | Audit and evidence plan | Ch. 20 — Audit and Evidence Plan | | |

## DPDP Rules, 2025 — operational detail (representative)

| # | Rule area | Requirement (summary) | OASIS mechanism | Artifact | Status |
|---|---|---|---|---|---|
| 14 | Notice content and form | Itemized notice standards, consent-manager interoperability where used. | Human–AI workflow blueprint | [Human–AI Workflow Blueprint](../Methodology/chapter-32-templates-checklists-and-tools.md#7-human-ai-workflow-blueprint) | |
| 15 | Reasonable security safeguards | Encryption, access control, monitoring, logging, backup, and breach-detection measures specified in the Rules. | Defense-in-depth control layers | Ch. 19 defense-in-depth layers | |
| 16 | Breach notification timelines and content | Notify Board and affected Data Principals per prescribed timelines and content. | Incident, complaint and regulatory reporting procedure | Ch. 20 | |
| 17 | Data retention and erasure schedules | Purpose-linked retention periods and erasure triggers by data/use category. | Data lineage and retention | Ch. 15; Ch. 20 Change and retirement | |
| 18 | Significant Data Fiduciary thresholds and additional duties | DPO appointment, annual audit, DPIA per notified thresholds. | Data protection and AI impact assessment | Ch. 20 | |

---

[← Back to Contents](../README.md) · [Chapter 20: Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) · [Reference Framework Alignment Index →](../references/regulatory-framework-alignment-index.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
