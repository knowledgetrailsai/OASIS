<!-- SPDX-License-Identifier: MIT -->

# Changelog

All notable changes to the OASIS Methodology Handbook are recorded here. Entries are grouped by date and describe what was added or changed and why, so anyone picking the repository back up can see how it evolved without reconstructing it from commit messages alone.

This handbook mixes two kinds of content that age differently. The **Methodology** chapters (the 33-chapter core) describe durable engineering and governance principles and should change rarely, deliberately, and with a clear rationale recorded here. The **Standards** and **References** material indexes external regulatory and industry frameworks — ISO/IEC 42001, NIST AI RMF, the EU AI Act, India's DPDP Act, OWASP's LLM and Agentic Top 10 lists, and the 20+ frameworks catalogued in the [regulatory alignment index](references/regulatory-framework-alignment-index.md) — and those frameworks are genuinely moving targets: version numbers change, staggered compliance deadlines pass, and entirely new frameworks appear. Anyone maintaining this repository should review the Standards and References material at least **quarterly**, and immediately after any material regulatory development affecting a framework already indexed here, and record that review below even when it results in no changes — a dated "reviewed, no changes needed" entry is still useful evidence that the material hasn't silently gone stale.

## 2026-08-30

- Simplified wording across methodology chapters, architecture perspectives, engineering/security/monitoring specs, and reference/standards/tools documents; extended row-level and glossary-level companion-repository cross-links.

## 2026-08-18

- Rewrote all 33 Methodology chapters from terse reference notes into full prose, each gaining a "Background and context" section and inline cross-links into the companion Architecture, Engineering, Security, Monitoring, Standards, References and Tools material. Fixed several anchor-link defects surfaced during the accompanying repo-wide link audit (an en-dash/hyphen mismatch affecting ~10 links, four double-hyphen typos, one link pointing at a non-existent chapter anchor). All 1,345 internal markdown links in the repository verified to resolve.
- Added the **Architecture Principles** section (ten principles: Secure by design, Human accountable, Model independent, Observable by design, Knowledge grounded, Evidence gated, Progressively autonomous, Outcome oriented, Composable and reusable, Jurisdiction neutral/compliance-ready) to the reference architecture, plus nine new enterprise-architecture-perspective articles (Business/Capability, Agent, Process, Information/Knowledge, Inference, Integration, Deployment, Security & Trust, Operations/Observability).
- Added five new Engineering articles (Model Engineering, Context and Retrieval Engineering, Harness and Orchestration Engineering, Memory and State Engineering, Evaluation and Reliability Engineering) alongside the existing Tool and Integration Interface Specification, giving Chapter 14's system equation a full implementation-level companion per component.
- Added "Background and context" sections consistently across Architecture, Engineering, Monitoring, References, Standards, Security and Tools, establishing one document structure across all non-Methodology material.
- Fixed a duplicated part-label title bug present in all five Part-index pages ("Part I: Part I: ...") and three broken Chapter 32 template anchor references in the Architecture perspective articles.
- **Added the Assessments folder**: an [AI Engineering Maturity Model](assessments/oasis-ai-engineering-maturity-model.md) scoring nine dimensions against five maturity levels (with an explicit weakest-link, non-averaged scoring rule) and a fillable [Maturity Scorecard Template](assessments/oasis-maturity-scorecard-template.md).
- **Added a master glossary and roles roster** ([references/master-glossary-and-roles-roster.md](references/master-glossary-and-roles-roster.md)) consolidating terminology and accountable roles scattered across the Methodology chapters and Architecture perspective articles into one lookup, plus a default RACI for the methodology's recurring high-stakes decisions.
- Added this CHANGELOG.

## 2026-08-17

- Added the Security folder: an Agentic AI Threat and Control Checklist mapping Chapter 19's defense-in-depth layers and threat model to the OWASP Top 10 for LLM Applications, the OWASP Top 10 for Agentic Applications, and MITRE ATLAS tactics.
- Populated the Tools folder with fillable versions of all 20 Chapter 32 templates, across five files grouped by lifecycle area.
- Added the Standards folder (ISO/IEC 42001, NIST AI RMF, EU AI Act, DPDP Act alignment checklists) and the References folder (regulatory and standards framework alignment index), and researched and indexed additional applicable global frameworks beyond the initial four.
- Added the initial Architecture and Engineering and Monitoring reference material: the OASIS Reference Architecture (system-equation diagram, component-to-artifact map, defense-in-depth overlay, orchestration-pattern decision rule), the first Engineering article (Tool and Integration Interface Specification), and the Observability and Telemetry Specification.

## 2026-08-04 to 2026-08-05

- Initial repository organization: documentation folders established, the Methodology folder renamed and structured into its current form, navigation links fixed across the handbook.

## 2026-08-01

- Initial upload of the 33-chapter OASIS Methodology Handbook and supporting scaffold folders.
