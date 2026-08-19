<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 19: Security and Responsible AI Engineering](chapter-19-security-and-responsible-ai-engineering.md) · [Contents](../README.md) · [Next: Chapter 21: Deployment, Operations and AgentOps →](chapter-21-deployment-operations-and-agentops.md)

# Chapter 20: Governance, Compliance and Regulatory Engineering

# Governance, Compliance and Regulatory Engineering

> **CHAPTER PURPOSE** Translate applicable laws, policies, standards and risk appetite into testable controls, decision rights, records and operating evidence.

## Background and context

Chapter 19 built the controls: defense-in-depth across eight layers, an agentic threat model, seven responsible-AI properties, and a containment discipline. None of that answers a question every board, regulator and enterprise customer eventually asks: how do you know those controls are in place, adequate, and owned by a named person? This chapter turns Chapter 19's properties and controls into obligations mapped to controls, controls mapped to test cases, and test cases mapped to retained evidence and an accountable owner.

This chapter follows Chapter 19 because you cannot govern a system's fairness, privacy or containment posture until you have engineered those properties into it. Governance without engineered controls underneath it is a policy binder describing behavior the system doesn't exhibit. It feeds into Chapter 21: the release manifests, incident classification and audit trails that make production governable are the same evidentiary discipline this chapter establishes, applied continuously rather than at a single review.

OASIS is jurisdiction-neutral, and this chapter defines the process of regulatory engineering, not the content of any specific law — content changes by geography, sector and calendar year in ways a methodology chapter should not hard-code. The framework-specific instruments live in `/standards`, one checklist per framework, indexed by the [Regulatory and Standards Framework Alignment Index](../references/regulatory-framework-alignment-index.md), which also catalogues more than twenty other global frameworks (ISO/IEC 23894, 22989, 23053, 42005 and 42006; NIST CSF and SP 800-53; MITRE ATLAS; GDPR; DORA; HIPAA; PCI DSS; and country- and sector-specific rules) material depending on where and how a system operates. Read that index first to see which checklist applies.

## Regulatory engineering

Regulatory engineering converts legal, contractual, policy and standards obligations into implementable requirements and verifiable evidence. OASIS is jurisdiction-neutral: applicability is assessed for each country, sector, role, use, population and deployment model. The methodology does not substitute for legal advice or a conformity assessment.

That reflects a genuine boundary in what an engineering methodology can do. OASIS can structure the evidence a compliance program needs and connect it to the engineering artifacts that produce it; it cannot tell an organization whether it is compliant with a specific statute. The [Regulatory Framework Alignment Index](../references/regulatory-framework-alignment-index.md) draws a useful distinction: some frameworks — currently ISO/IEC 42001 — are certifiable management-system standards a team chooses to align with. Others, like the NIST AI RMF, are voluntary risk-management vocabularies with no certificate or legal force. Some, like the EU AI Act and India's DPDP Act, are binding law: an organization is subject to them once its role, geography, sector or data-processing activity crosses the applicability threshold, whether or not the alignment work has been done. Triage binding-law applicability first — missing a legal obligation is a different consequence from not yet holding a certificate.

> **TRACEABILITY CHAIN** Obligation → control requirement → technical/process control → test case → operating evidence → accountable owner.

This chain is what makes the chapter operational. Every row in every standards checklist in this repository — ISO/IEC 42001's clause-by-clause mapping, the NIST AI RMF's four functions, the EU AI Act's obligation tables, the DPDP Act's Data Fiduciary duties — follows this pattern: a named obligation, the OASIS mechanism addressing it, the evidence artifact, a status, and an owner. A governance program that cannot walk this chain end to end — a policy with no control, a control with no test case, a test case with no retained evidence — has a gap, regardless of how mature the documentation looks.

## Governance scope

| **Governance domain**    | **OASIS mechanism**                                                                                  |
|--------------------------|------------------------------------------------------------------------------------------------------|
| Business accountability  | Outcome owner, decision rights, residual-risk acceptance and renewal.                                |
| AI inventory             | System record, owner, purpose, models, data, tools, users, geography and lifecycle state.            |
| Risk classification      | Impact, autonomy, data, exposure and scale determine assurance.                                      |
| Data and privacy         | Purpose, lawful basis where applicable, minimization, access, retention, rights and breach handling. |
| Model and third party    | Due diligence, contractual controls, evaluation, region, change notice and exit.                     |
| Agent and tool authority | Autonomy matrix, least privilege, approvals, limits, logs and revocation.                            |
| Responsible AI           | Impact assessment, affected groups, transparency, human oversight, contestability and remedy.        |
| Records and audit        | Trace, configuration, decisions, test evidence, incidents, changes and approvals.                    |
| Change and retirement    | Impact reassessment, controlled release, rollback, decommissioning and record retention.             |

A gap in any one of these nine domains is a gap the others cannot compensate for. Business accountability exists because every domain needs someone with authority to accept residual risk — a control register with no owner is a list, not a governance mechanism. The AI inventory is the precondition for everything downstream: an organization cannot classify, assess or audit a system it doesn't know it operates, and "shadow AI" is consistently one of the largest gaps governance programs find. Risk classification calibrates the intensity of everything else to the system in front of you — a low-autonomy internal tool and a high-autonomy system touching regulated financial decisions should not carry the same assurance burden.

Data and privacy, and model and third party, are where obligations often extend beyond the build team's control — a model provider's data handling and a vendor's subprocessor chain are part of the system's real risk surface. Agent and tool authority mirrors Chapter 19's containment discipline: the same autonomy matrix and least-privilege posture is what a governance review inspects here. Responsible AI carries Chapter 19's seven properties into auditable form. Records and audit, and change and retirement, close the loop across the system's lifecycle — governance that stops at go-live is governance for a moment in time, not for the system as it exists.

## Regulatory engineering method

This is a sequence, not a checklist to work in parallel — each step depends on evidence the step before it produced.

48. **Identify the provider, deployer, user, operator and affected-party roles in every jurisdiction.** Most binding frameworks — the EU AI Act is the clearest example — attach different obligations to each role, and an organization can hold more than one role at once across jurisdictions. Getting this wrong invalidates every obligation mapped downstream.

49. **Create a Regulatory Applicability Register covering AI, data protection, cybersecurity, sector, consumer, employment, intellectual-property, records and accessibility obligations.** This is what the [Regulatory Framework Alignment Index's](../references/regulatory-framework-alignment-index.md) global triage sequence exists to populate — work through where the system is developed, hosted, offered and used, which binding laws apply, and which voluntary or certifiable frameworks are worth adopting, before opening any individual checklist.

50. **Map each obligation to system, process, vendor and human controls with a named accountable owner.** This is where the traceability chain becomes concrete, using the framework-specific checklists in `/standards` — [ISO/IEC 42001](../standards/iso-42001-alignment-checklist.md), the [NIST AI RMF](../standards/nist-ai-rmf-alignment-checklist.md), the [EU AI Act](../standards/eu-ai-act-alignment-checklist.md), and the [DPDP Act](../standards/dpdp-act-alignment-checklist.md), each already mapped row by row to their obligations.

51. **Define compliance test cases and evidence retention before production engineering.** Evidence produced retroactively, after go-live, is weaker than evidence generated as a designed-in output of the build — several frameworks treat a missing contemporaneous record as a finding on its own.

52. **Validate human oversight as an operational capability: authority, information, time, override, escalation and record.** A reviewer named in policy who has never been given the time or authority to override a decision fails this step, even though it would pass a documentation-only audit.

53. **Track regulatory and standards change, reassess material modifications and retain decisions.** Obligations are not static: the EU AI Act phases in through 2027, and every framework in the [Alignment Index](../references/regulatory-framework-alignment-index.md) is revised periodically. This keeps a governance program current, not accurate only as of the day it was built.

## Principal artifacts

- Regulatory Applicability Register and Legal/Policy Obligations Map

- AI Use-Case Risk Classification and AI/System Record

- Data Protection and AI Impact Assessments

- Model, Vendor and Open-Source Due-Diligence Record

- Human Oversight and Decision-Authority Matrix

- Regulatory Control Requirements and Compliance Test Pack

- Audit and Evidence Plan

- Incident, Complaint and Regulatory Reporting Procedure

- Regulatory Change-Impact Assessment and Residual-Risk Acceptance

These nine artifacts are structured so one can serve more than one framework rather than being rebuilt per standard. Where two checklists point to the same underlying control — most commonly the Risk and Control Register, the Autonomy Matrix, or the Data and Knowledge Readiness Assessment — populate it once and cross-reference it, consistent with the anti-bureaucracy discipline in Chapter 13. A globally deployed system may genuinely need ISO/IEC 42001 as its management-system backbone, the NIST AI RMF as a shared risk vocabulary, and separate legal overlays per market — expected, provided the artifacts are shared rather than duplicated.

## Alignment—not automatic compliance

OASIS can organize evidence in a form compatible with management and risk frameworks such as ISO/IEC 42001, ISO/IEC 23894 and the NIST AI RMF. It can also support obligations under laws such as the EU AI Act and India's Digital Personal Data Protection framework. Applicability, legal interpretation, effective dates, required notices and conformity mechanisms must be confirmed against current official sources.

Alignment means the evidence a governance program produces is organized in a shape a framework recognizes — the same nine domains, the same traceability chain, the same accountable-owner discipline. It does not mean a certificate has been issued, a conformity assessment completed, or legal counsel has signed off on a jurisdiction's interpretation. Those steps require qualified legal and, where applicable, accredited third-party involvement outside what any engineering methodology can provide. The [Regulatory Framework Alignment Index](../references/regulatory-framework-alignment-index.md) is explicit about this boundary: treat every checklist in `/standards` as a readiness aid, not the outcome itself.

---

[← Previous: Chapter 19: Security and Responsible AI Engineering](chapter-19-security-and-responsible-ai-engineering.md) · [Contents](../README.md) · [Next: Chapter 21: Deployment, Operations and AgentOps →](chapter-21-deployment-operations-and-agentops.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
