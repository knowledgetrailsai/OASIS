<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 19: Security and Responsible AI Engineering](chapter-19-security-and-responsible-ai-engineering.md) · [Contents](../README.md) · [Next: Chapter 21: Deployment, Operations and AgentOps →](chapter-21-deployment-operations-and-agentops.md)

# Chapter 20: Governance, Compliance and Regulatory Engineering

# Governance, Compliance and Regulatory Engineering

> **CHAPTER PURPOSE** Translate applicable laws, policies, standards and risk appetite into testable controls, decision rights, records and operating evidence.

## Background and context

Chapter 19 built the controls: defense-in-depth across eight layers, an agentic threat model, seven responsible-AI properties, and a containment discipline for when something goes wrong anyway. None of that, by itself, answers a question every board, regulator, enterprise customer and internal risk committee eventually asks: how do you know those controls are actually in place, adequate to the obligation, and something a named person is accountable for — rather than a good-faith engineering effort nobody outside the build team can verify? That is what governance, compliance and regulatory engineering adds. It takes the properties and controls Chapter 19 defines and turns them into obligations mapped to controls, controls mapped to test cases, and test cases mapped to retained evidence and an accountable owner — the chain that lets an organization demonstrate, rather than assert, that a system is governed.

This chapter follows Chapter 19 for a structural reason, not merely a numbering one: you cannot meaningfully govern a system's fairness, privacy or containment posture until you have first engineered fairness, privacy and containment into it. Governance without engineered controls underneath it is theater — a policy binder describing behavior the system does not actually exhibit. And this chapter feeds directly into Chapter 21, which follows it: the release manifests, incident classification and audit trails that make deployment and operations governable in production are the same evidentiary discipline this chapter establishes, applied continuously rather than at a single point-in-time review.

OASIS is deliberately jurisdiction-neutral, and this chapter is written at that same altitude — it defines the process of regulatory engineering, not the content of any specific law, because the specific content changes by geography, sector and calendar year in ways a methodology chapter cannot track and should not attempt to hard-code. The concrete, framework-specific instruments that operationalize this chapter live in `/standards` — one alignment checklist per named framework — and are indexed by the [Regulatory and Standards Framework Alignment Index](../references/regulatory-framework-alignment-index.md), which additionally catalogues more than twenty other global frameworks (ISO/IEC 23894, 22989, 23053, 42005 and 42006; NIST CSF and SP 800-53; MITRE ATLAS; GDPR; DORA; HIPAA; PCI DSS; and country- and sector-specific cybersecurity rules among them) that become material depending on where and how a system operates. Read that index first — it explains which checklist actually applies to a given engagement — rather than treating this chapter as a substitute for enumerating every framework inline.

## Regulatory engineering

Regulatory engineering converts legal, contractual, policy and standards obligations into implementable requirements and verifiable evidence. OASIS is jurisdiction-neutral: applicability is assessed for each country, sector, role, use, population and deployment model. The methodology does not substitute for legal advice or a conformity assessment.

That last sentence is not a disclaimer inserted for liability's sake — it reflects a genuine boundary in what an engineering methodology can responsibly do. OASIS can structure the evidence a compliance program needs and connect it to the engineering artifacts that produce it; it cannot tell a specific organization, in a specific jurisdiction, with a specific risk profile, whether it is in fact compliant with a specific statute. The [Regulatory Framework Alignment Index](../references/regulatory-framework-alignment-index.md) draws a useful distinction worth internalizing here: some frameworks — currently ISO/IEC 42001 — are certifiable management-system standards a team chooses to align with, auditable by an accredited third party. Others, like the NIST AI RMF, are voluntary risk-management vocabularies with no certificate and no legal force of their own. And some, like the EU AI Act and India's DPDP Act, are binding law: an organization is subject to them the moment its role, geography, sector or data-processing activity crosses the applicability threshold, whether or not anyone has done the alignment work yet. Triage in that order — determine binding-law applicability before worrying about which voluntary framework to adopt — because the consequence of missing a legal obligation is categorically different from the consequence of not yet holding a certificate.

> **TRACEABILITY CHAIN** Obligation → control requirement → technical/process control → test case → operating evidence → accountable owner.

This traceability chain is the mechanism that makes the rest of the chapter operational rather than aspirational. Every row in every standards checklist in this repository — ISO/IEC 42001's clause-by-clause mapping, the NIST AI RMF's four functions, the EU AI Act's obligation tables, the DPDP Act's Data Fiduciary duties — follows exactly this pattern: a named obligation, the OASIS mechanism that addresses it, the artifact that carries the evidence, a status, and an owner. A governance program that cannot walk this chain end to end for a given obligation — that has a policy but no control, or a control but no test case, or a test case but no retained evidence — has a gap, regardless of how mature the policy documentation looks on its own.

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

These nine domains are the scope of governance in the sense that a gap in any one of them is a gap the others cannot compensate for. Business accountability exists because every other domain eventually needs someone with the authority to accept residual risk and renew that acceptance — a control register with no accountable owner is a list, not a governance mechanism. The AI inventory is the precondition for everything downstream of it: an organization cannot classify, assess or audit a system it does not know it operates, and "shadow AI" — systems built or adopted outside a formal inventory — is consistently one of the largest gaps enterprise governance programs actually discover once they look. Risk classification is what calibrates the intensity of everything else in this table to the system actually in front of you; a low-autonomy, low-exposure internal tool and a high-autonomy system touching regulated financial decisions should not carry the same assurance burden, and treating them identically either over-engineers the former or under-engineers the latter.

Data and privacy, and model and third party, are where an organization's obligations most often extend beyond its own build team's direct control — a model provider's data handling, a vendor's subprocessor chain, and a third-party tool's own security posture are all part of the system's actual risk surface even though no OASIS engineering team wrote a line of that code. Agent and tool authority is this chapter's governance mirror of Chapter 19's containment discipline — the same autonomy matrix and least-privilege posture engineered there is what a governance review actually inspects here. Responsible AI carries Chapter 19's seven properties into an auditable form: an impact assessment, a named set of affected groups, and a documented contestability and remedy path. Records and audit, and change and retirement, close the loop across the system's entire lifecycle — governance that stops at go-live, with no discipline for the system's eventual retirement or every material change along the way, is governance for a moment in time rather than for the system as it actually exists.

## Regulatory engineering method

The regulatory engineering method is a sequence, not a checklist to work in parallel — each step depends on evidence the step before it produced, and skipping ahead tends to produce a compliance program built on assumptions rather than a verified applicability determination.

48. **Identify the provider, deployer, user, operator and affected-party roles in every jurisdiction.** Most binding frameworks — the EU AI Act is the clearest current example — attach materially different obligations to each of these roles, and an organization can hold more than one role simultaneously across different jurisdictions for the same system. Getting the role determination wrong at this step invalidates every obligation mapped downstream of it.

49. **Create a Regulatory Applicability Register covering AI, data protection, cybersecurity, sector, consumer, employment, intellectual-property, records and accessibility obligations.** This register is the artifact the [Regulatory Framework Alignment Index's](../references/regulatory-framework-alignment-index.md) global triage sequence exists to populate — work through where the system is developed, hosted, offered and used, which binding laws apply in those locations, and which voluntary or certifiable frameworks are worth adopting, before opening any individual standards checklist.

50. **Map each obligation to system, process, vendor and human controls with a named accountable owner.** This is where the traceability chain above becomes concrete for a specific engagement, and where the framework-specific checklists in `/standards` earn their keep — [ISO/IEC 42001](../standards/iso-42001-alignment-checklist.md), the [NIST AI RMF](../standards/nist-ai-rmf-alignment-checklist.md), the [EU AI Act](../standards/eu-ai-act-alignment-checklist.md), and the [DPDP Act](../standards/dpdp-act-alignment-checklist.md) each already carry this exact mapping, row by row, for their respective obligations.

51. **Define compliance test cases and evidence retention before production engineering.** Compliance evidence produced retroactively, after a system is already live, is materially weaker than evidence generated as a designed-in output of the build — and in several frameworks, the absence of a contemporaneous record is itself treated as a finding independent of whether the underlying control actually worked.

52. **Validate human oversight as an operational capability: authority, information, time, override, escalation and record.** A human oversight requirement satisfied only on paper — a reviewer named in a policy document who has never actually been given the authority, the time, or the information needed to meaningfully override a system's decision — fails this step even though it would pass a documentation-only audit.

53. **Track regulatory and standards change, reassess material modifications and retain decisions.** Obligations are not static: the EU AI Act itself phases in on a staggered timeline through 2027, and every framework in the [Alignment Index](../references/regulatory-framework-alignment-index.md) is revised periodically. This step is what keeps a governance program current rather than accurate only as of the day it was built.

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

These nine artifacts are the durable output of the method above, and they are deliberately structured so that a single artifact can serve more than one framework at once rather than being rebuilt per standard. Where two standards checklists point to the same underlying control — most commonly the Risk and Control Register, the Autonomy Matrix, or the Data and Knowledge Readiness Assessment — populate it once and cross-reference it from each checklist's row, consistent with the anti-bureaucracy discipline established in Chapter 13. A globally deployed system may genuinely need ISO/IEC 42001 as its management-system backbone, the NIST AI RMF as a shared risk vocabulary, and separate legal overlays for every market it touches — that is expected, not a sign the governance program has grown out of control, provided the underlying artifacts are shared rather than duplicated.

## Alignment—not automatic compliance

OASIS can organize evidence in a form compatible with management and risk frameworks such as ISO/IEC 42001, ISO/IEC 23894 and the NIST AI RMF. It can also support obligations under laws such as the EU AI Act and India's Digital Personal Data Protection framework. Applicability, legal interpretation, effective dates, required notices and conformity mechanisms must be confirmed against current official sources.

This heading is worth taking literally rather than as boilerplate. Alignment means the evidence a governance program produces is organized in a shape a framework recognizes — the same nine domains above, the same traceability chain, the same accountable-owner discipline. It does not mean an ISO 42001 certificate has been issued, that a conformity assessment under the EU AI Act has been completed, or that legal counsel has signed off on a specific jurisdiction's interpretation of a specific obligation. Those steps require qualified legal and, where applicable, accredited third-party involvement that sits outside what any engineering methodology can provide. The [Regulatory Framework Alignment Index](../references/regulatory-framework-alignment-index.md) is explicit about this same boundary, and the practical discipline it recommends is to treat every checklist in `/standards` as a readiness aid that shortens the distance to a genuine compliance or certification outcome, not as the outcome itself.

---

[← Previous: Chapter 19: Security and Responsible AI Engineering](chapter-19-security-and-responsible-ai-engineering.md) · [Contents](../README.md) · [Next: Chapter 21: Deployment, Operations and AgentOps →](chapter-21-deployment-operations-and-agentops.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
