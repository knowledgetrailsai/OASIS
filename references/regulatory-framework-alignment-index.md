<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 33: Appendices and Reference Material](../Methodology/chapter-33-appendices-and-reference-material.md)

# Reference: Regulatory and Standards Framework Alignment Index

> **PURPOSE** Index the framework-specific alignment checklists in `/standards` and explain how they relate to [Chapter 20 — Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) and [Chapter 33 — Appendices and Reference Material](../Methodology/chapter-33-appendices-and-reference-material.md#reference-framework-alignment).

**Status: alignment aid, not compliance.** OASIS is an original methodology. It organizes evidence in a form compatible with the frameworks below; it does not certify compliance, replace legal advice, or guarantee a conformity outcome. Applicability, current clause text, effective dates and required notices must be confirmed against each framework's official current source before relying on any checklist in this folder. See the [Methodology disclaimer](../Methodology/chapter-33-appendices-and-reference-material.md#methodology-disclaimer).

## Why this index exists

Chapter 20 establishes the *process* for regulatory engineering — identify roles and jurisdictions, build a Regulatory Applicability Register, map obligations to controls, define test cases and evidence, validate human oversight, and track change (steps 48–53). What it does not do, by design, is enumerate the specific clauses of any one law or standard, because OASIS is jurisdiction-neutral and framework-agnostic — a methodology chapter that hard-coded EU AI Act article numbers would go stale the moment the regulation was amended, and would be useless to a team whose applicable law is something else entirely.

This `/references` and `/standards` pairing closes that gap without breaking that neutrality. `/standards` holds one checklist per named framework — the concrete, framework-specific instrument. `/references` (this file) holds the index that explains how those instruments relate to each other and to the Chapter 20 process, so a delivery team can navigate the set without having memorized every framework in advance. Read this file first, then open only the checklist(s) that Step 0 of the Regulatory Applicability Register tells you are actually in scope.

## Understanding the framework landscape

The four frameworks currently covered fall into three distinct categories, and knowing which category a framework belongs to changes what "alignment" actually buys the organization:

- **Certifiable management-system standards** — currently [ISO/IEC 42001](../standards/iso-42001-alignment-checklist.md). These are voluntary to adopt but, once adopted, can be independently audited and certified by an accredited third party. Alignment here produces a certificate that can be shown to customers, auditors and regulators as external proof of a mature AI governance program.
- **Voluntary risk-management frameworks** — currently the [NIST AI RMF](../standards/nist-ai-rmf-alignment-checklist.md). These are not certifiable and carry no legal force by themselves, but function as a widely recognized common vocabulary for structuring an internal risk program, and are sometimes referenced by other frameworks, procurement requirements, or (for U.S. federal agencies specifically) government directives.
- **Binding law** — currently the [EU AI Act](../standards/eu-ai-act-alignment-checklist.md) and the [India DPDP Act and Rules](../standards/dpdp-act-alignment-checklist.md). These carry statutory force and financial penalties for non-compliance within their jurisdiction and scope. Alignment here is not optional once the applicability test (Step 0 in the EU AI Act checklist; the Data Fiduciary core obligations in the DPDP checklist) determines the organization is in scope — it is a legal obligation, and the checklist is a structuring aid toward meeting it, not a substitute for legal sign-off.

A useful mental model: certifiable standards and voluntary frameworks are things an organization *chooses* to align with because doing so is good practice or commercially advantageous; binding law is something the organization is *already* subject to the moment its risk-tier or data-processing activity crosses the applicability threshold, whether or not anyone has done the alignment work yet. Triage accordingly — determine binding-law applicability first, since the consequence of missing it is materially different from the consequence of not yet holding an ISO certificate.

## How this index relates to Chapter 20

Chapter 20's Regulatory Engineering Method (steps 48–53) is the process; the checklists below are the per-framework instrument that operationalizes step 49 (build the Regulatory Applicability Register) and step 50 (map each obligation to a control with a named owner). Start every engagement with the [Regulatory Applicability Register](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) to determine which frameworks in the table below are actually in scope — do not work every checklist by default.

## Framework checklists

| Framework | Type | Applies when | Checklist |
|---|---|---|---|
| ISO/IEC 42001 | Management-system standard (certifiable) | Organization wants a certifiable AI management system, or a customer/regulator expects one. | [ISO/IEC 42001 Alignment Checklist](../standards/iso-42001-alignment-checklist.md) |
| NIST AI RMF 1.0 + Generative AI Profile | Voluntary risk-management framework | US-market exposure, federal/public-sector counterparties, or as a general-purpose risk taxonomy regardless of jurisdiction. | [NIST AI RMF Alignment Checklist](../standards/nist-ai-rmf-alignment-checklist.md) |
| EU AI Act (Regulation (EU) 2024/1689) | Binding regulation | System is placed on the EU market, used in the EU, or its output is used in the EU, regardless of where the organization is based. | [EU AI Act Alignment Checklist](../standards/eu-ai-act-alignment-checklist.md) |
| India DPDP Act, 2023 + Rules, 2025 | Binding regulation (personal data) | System processes personal data of individuals in India, or of Data Principals as defined by the Act. | [DPDP Act Alignment Checklist](../standards/dpdp-act-alignment-checklist.md) |

## Which framework(s) actually apply — a triage sequence

Work through these questions in order; each one can add a checklist to the engagement's scope, but none of them removes the need to check the others:

1. **Does the system process personal data of individuals in India, or of Data Principals as the DPDP Act defines them?** If yes, the [DPDP Act Alignment Checklist](../standards/dpdp-act-alignment-checklist.md) applies regardless of anything else — this is usually the first checklist in scope for an India-headquartered organization.
2. **Is the system placed on the EU market, used within the EU, or does its output reach EU users or EU-based decisions?** If yes, run Step 0 of the [EU AI Act Alignment Checklist](../standards/eu-ai-act-alignment-checklist.md) to determine role and risk tier — this determines how much of that checklist is actually mandatory versus not applicable.
3. **Does the organization want a certifiable, auditable AI management system** — because a customer, tender, or internal governance mandate expects one? If yes, the [ISO/IEC 42001 Alignment Checklist](../standards/iso-42001-alignment-checklist.md) is the right instrument; note this is a choice, not a legal trigger.
4. **Is there no other mandated framework, or is a jurisdiction-neutral internal risk taxonomy needed regardless?** The [NIST AI RMF Alignment Checklist](../standards/nist-ai-rmf-alignment-checklist.md) is a strong default baseline even outside a U.S. context, and pairs well with ISO 42001 via NIST's own published crosswalk between the two.

Most real engagements land on more than one checklist at once — for example, an India-based deployer serving EU users, pursuing ISO 42001 certification as a customer trust signal, while using the NIST functions internally as the risk-review vocabulary. That is expected; see "Using multiple checklists together" below for how to avoid duplicating work across them.

## Related non-regulatory references (Chapter 33)

These inform engineering and security practice rather than legal compliance; see [Chapter 33 — Reference framework alignment](../Methodology/chapter-33-appendices-and-reference-material.md#reference-framework-alignment) for links:

- ISO/IEC 23894 — Guidance on AI risk management
- OWASP Agentic AI Threats and Mitigations; OWASP Top 10 for Agentic Applications
- OpenAI — A practical guide to building AI agents
- Anthropic — Building effective AI agents; Effective context engineering; Demystifying evals
- Microsoft Agent Framework overview

## Using multiple checklists together

Most engagements are in scope for more than one framework at once (e.g., an India-based deployer serving EU users under NIST-aligned internal risk practice). Where two checklists reference the same OASIS artifact — most commonly the [Risk and Control Register](../Methodology/chapter-32-templates-checklists-and-tools.md#17-risk-and-control-register), the [Autonomy Matrix](../Methodology/chapter-32-templates-checklists-and-tools.md#12-autonomy-matrix), and the [Data and Knowledge Readiness Assessment](../Methodology/chapter-32-templates-checklists-and-tools.md#8-data-and-knowledge-readiness-assessment) — populate it once and cross-reference it from each checklist's row rather than duplicating content, consistent with the [anti-bureaucracy test](../Methodology/chapter-13-decision-gates-and-evidence-model.md) in Chapter 13.

## Maintenance

Regulatory text, standards editions and thresholds change. Review this index and its checklists at least at every major regulatory update and at the cadence set in [Chapter 20, step 53](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) (track regulatory and standards change, reassess material modifications, retain decisions).

---

[← Back to Contents](../README.md) · [Chapter 33: Appendices and Reference Material](../Methodology/chapter-33-appendices-and-reference-material.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
