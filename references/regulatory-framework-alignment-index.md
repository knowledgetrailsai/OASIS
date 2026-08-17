<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 33: Appendices and Reference Material](../Methodology/chapter-33-appendices-and-reference-material.md)

# Reference: Regulatory and Standards Framework Alignment Index

> **PURPOSE** Index the framework-specific alignment checklists in `/standards` and explain how they relate to [Chapter 20 — Governance, Compliance and Regulatory Engineering](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) and [Chapter 33 — Appendices and Reference Material](../Methodology/chapter-33-appendices-and-reference-material.md#reference-framework-alignment).

**Status: alignment aid, not compliance.** OASIS is an original methodology. It organizes evidence in a form compatible with the frameworks below; it does not certify compliance, replace legal advice, or guarantee a conformity outcome. Applicability, current clause text, effective dates and required notices must be confirmed against each framework's official current source before relying on any checklist in this folder. See the [Methodology disclaimer](../Methodology/chapter-33-appendices-and-reference-material.md#methodology-disclaimer).

## How this index relates to Chapter 20

Chapter 20's Regulatory Engineering Method (steps 48–53) is the process; the checklists below are the per-framework instrument that operationalizes step 49 (build the Regulatory Applicability Register) and step 50 (map each obligation to a control with a named owner). Start every engagement with the [Regulatory Applicability Register](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) to determine which frameworks in the table below are actually in scope — do not work every checklist by default.

## Framework checklists

| Framework | Type | Applies when | Checklist |
|---|---|---|---|
| ISO/IEC 42001 | Management-system standard (certifiable) | Organization wants a certifiable AI management system, or a customer/regulator expects one. | [ISO/IEC 42001 Alignment Checklist](../standards/iso-42001-alignment-checklist.md) |
| NIST AI RMF 1.0 + Generative AI Profile | Voluntary risk-management framework | US-market exposure, federal/public-sector counterparties, or as a general-purpose risk taxonomy regardless of jurisdiction. | [NIST AI RMF Alignment Checklist](../standards/nist-ai-rmf-alignment-checklist.md) |
| EU AI Act (Regulation (EU) 2024/1689) | Binding regulation | System is placed on the EU market, used in the EU, or its output is used in the EU, regardless of where the organization is based. | [EU AI Act Alignment Checklist](../standards/eu-ai-act-alignment-checklist.md) |
| India DPDP Act, 2023 + Rules, 2025 | Binding regulation (personal data) | System processes personal data of individuals in India, or of Data Principals as defined by the Act. | [DPDP Act Alignment Checklist](../standards/dpdp-act-alignment-checklist.md) |

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
