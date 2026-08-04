<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 29: OASIS Adoption Roadmap](chapter-29-oasis-adoption-roadmap.md) · [Contents](README.md) · [Next: Chapter 31: Illustrative Use Cases →](chapter-31-illustrative-use-cases.md)

# Chapter 30: Tailoring OASIS

# Tailoring OASIS

> **CHAPTER PURPOSE** Control methodology depth by organizational size, solution risk, autonomy, data sensitivity, exposure, scale and maturity while preserving essential controls.

## Tailoring equation

> **REQUIRED ASSURANCE** f(impact, autonomy, data sensitivity, external exposure, scale, regulatory obligation, reversibility and organizational maturity).

Organization size affects how work is staffed and packaged. It does not determine risk. A small manufacturer using AI to support a safety-critical engineering decision may require deeper assurance than a large enterprise using an internal meeting-summary assistant.

| **Implementation level** | **Purpose**                                  | **Minimum engineering and governance**                                                                    |
|--------------------------|----------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| L0 — Exploration         | Understand technical possibility.            | Synthetic/non-sensitive data, experiment definition, prohibited-use boundary and basic evaluation.        |
| L1 — PoC                 | Test outcome and intelligence hypothesis.    | Outcome hypothesis, representative cases, risk screen and prototype controls.                             |
| L2 — Controlled pilot    | Validate with selected users and real data.  | Privacy/security review, access, human oversight, monitoring and pilot acceptance.                        |
| L3 — Production service  | Support a live business process.             | Production architecture, automated tests, AgentOps, runbook, service and outcome ownership.               |
| L4 — Enterprise scale    | Deploy across units and shared capabilities. | Platform services, capacity, federated governance, version support and portfolio management.              |
| L5 — Critical autonomy   | Execute consequential decisions or actions.  | Enhanced validation, independent assurance, strict authority, continuous evidence and emergency controls. |

## Organization-size patterns

| **Organization** | **Recommended form**                                                                                                  | **Do not remove**                                                                                         |
|------------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| Small            | One cross-functional team; combined artifacts; managed services; combined gates; short decision records.              | Outcome owner, risk classification, representative evaluation, authority limits, fallback and monitoring. |
| Medium           | Small portfolio office; shared platform defaults; specialist reviews on demand; monthly outcome governance.           | Production ownership, regression, access controls, incident process and value accounting.                 |
| Large / group    | Federated business ownership; central platform and standards; multiple pods; formal service and portfolio governance. | Clear decision rights, tenancy, productization discipline, independent assurance where warranted.         |

## Solution archetype tailoring

| **Archetype**                | **Emphasize**                                                                                |
|------------------------------|----------------------------------------------------------------------------------------------|
| Small productivity use       | Privacy, user guidance, adoption, cost and data leakage; light workflow integration.         |
| Knowledge assistant          | Source authority, access-filtered retrieval, citation, abstention and freshness.             |
| Customer-facing conversation | Disclosure, service quality, escalation, language, identity and complaint handling.          |
| Operational automation       | Tool contracts, transactions, idempotency, recovery, capacity and process ownership.         |
| Decision support             | Evidence, calibration, bias, human authority, contestability and decision records.           |
| Voice agent                  | Consent/notice, transcription, interruption, latency, hand-off and call outcome.             |
| Multi-agent system           | Inter-agent trust, state, isolation, propagation, orchestration and containment.             |
| High-risk or regulated       | Legal applicability, impact assessment, independent assurance, records and strict authority. |

## Tailoring record

Every initiative records its level, risk profile, activated workstreams, combined or omitted artifacts, gate cadence and rationale. Tailoring is revisited when purpose, model, provider, user population, data, geography, integration, transaction value, scale or autonomy changes.

---

[← Previous: Chapter 29: OASIS Adoption Roadmap](chapter-29-oasis-adoption-roadmap.md) · [Contents](README.md) · [Next: Chapter 31: Illustrative Use Cases →](chapter-31-illustrative-use-cases.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](LICENSE.md).
