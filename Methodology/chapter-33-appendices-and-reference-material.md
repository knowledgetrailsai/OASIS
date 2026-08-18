<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 32: Templates, Checklists and Tools](chapter-32-templates-checklists-and-tools.md) · [Contents](../README.md)

# Chapter 33: Appendices and Reference Material

# Appendices and Reference Material

> **CHAPTER PURPOSE** Consolidate the glossary, artifact catalogue, gate catalogue, metrics, risks, design patterns, maturity model and framework references — the closing chapter a reader returns to rather than reads straight through.

## Background and context

Every methodology handbook needs one chapter that is not meant to be read start to finish, and this is that chapter for OASIS. Thirty-two chapters have built up a specific vocabulary — outcome contract, autonomy ceiling, groundedness, blast radius, evidence gate — and referenced a specific set of comparable methods and external frameworks along the way. This chapter exists to give a reader a single place to look those terms and comparisons up again, months after first encountering them, without re-reading the chapter that originally introduced each one.

It follows directly from [Chapter 32](chapter-32-templates-checklists-and-tools.md), which just catalogued the twenty artifacts a team fills in during delivery; this chapter catalogues the vocabulary and external context that surrounds those artifacts — what the terms in them mean precisely, how OASIS relates to methods a reader may already know, and which external standards and regulatory frameworks its risk and governance practices are designed to sit alongside. Where Chapter 32 pointed outward to the [Tools](../tools/01-outcome-and-portfolio-templates.md) folder for fillable artifacts, this chapter points outward to two different companion locations for depth it deliberately does not try to replicate inline. The [References](../references/regulatory-framework-alignment-index.md) folder holds the actively maintained index of every regulatory and standards framework relevant to an OASIS engagement, updated as those frameworks themselves change; the [Standards](../standards/) folder holds the framework-specific alignment checklists that operationalize that index. This chapter's own framework-alignment section below is intentionally a pointer to that fuller material rather than an attempt to enumerate over twenty frameworks inline — a static appendix that tried to keep pace with EU AI Act amendments or new ISO editions would be stale within a year, while the References folder is built to be the thing that actually gets updated.

Because this is a reference chapter rather than a narrative one, its structure stays close to the original: a glossary, an artifact catalogue, a comparison with adjacent methods, a pointer to framework alignment, and a closing disclaimer. What has grown is the substance under each of those headings — enough that a reader unfamiliar with a term, a comparable method, or a framework's relevance can actually resolve the question here rather than being sent elsewhere for a one-line stub.

## Glossary

The terms below are used precisely and consistently throughout the Methodology, Architecture, Engineering, and Security material. Where a term was introduced or defined more fully in an earlier chapter, that chapter is the authoritative source; this glossary is the fast-lookup version.

| **Term**             | **Definition**                                                                                                                |
|----------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Agent                | A system that uses a model to choose and execute steps toward a goal within a harness and authority boundary.                 |
| AgentOps             | Practices for deploying, observing, controlling and improving production agent systems.                                       |
| Autonomy             | The degree to which the system may decide or act without case-by-case human approval.                                         |
| Autonomy ceiling      | The maximum decision or action authority a given system or action is permitted to hold at a point in time, recorded per action in the [Autonomy Matrix](chapter-32-templates-checklists-and-tools.md#12-autonomy-matrix) and raised only when evidence justifies the next bounded operating mode. |
| Blast radius          | The full extent of what an action-taking system could affect if it failed or misbehaved — accessible data, systems, transaction value, case volume, time window and downstream authority — defined for every action-taking system per [Chapter 19](chapter-19-security-and-responsible-ai-engineering.md) and central to emergency-control and containment design. |
| Context engineering  | Construction of the complete information environment available to the model at a decision point.                              |
| Defense-in-depth      | A control strategy that layers preventive, detective and corrective guardrails across input, context, model, tools, workflow, output and runtime, so that no single control failure results in an unmitigated harm — the organizing principle behind [Chapter 19](chapter-19-security-and-responsible-ai-engineering.md) and the [Security: Agentic AI Threat Model and Control Checklist](../security/agentic-ai-threat-and-control-checklist.md). |
| Evaluation           | Structured evidence that measures system behavior, reliability, risk and outcome contribution.                                |
| Evidence gate         | A decision gate whose pass, conditional-pass, hold or fail outcome is based on specific evidence reviewed and recorded, rather than on schedule pressure or unexamined assumption — the operating model of [Chapter 13 — Decision Gates and Evidence Model](chapter-13-decision-gates-and-evidence-model.md), recorded per passage in the [Decision-Gate Record](chapter-32-templates-checklists-and-tools.md#20-decision-gate-record). |
| FDOE                 | Forward Deployed Outcome Engineering: embedded cross-functional delivery close to users and operations.                       |
| Groundedness          | The degree to which a system's output is actually supported by its retrieved or provided sources, as opposed to fluent but unsupported generation — a core evaluation dimension in [Chapter 18 — Evaluation and Reliability Engineering](chapter-18-evaluation-and-reliability-engineering.md) and the [Evaluation Strategy and Dataset](chapter-32-templates-checklists-and-tools.md#9-evaluation-strategy-and-dataset) template. |
| Guardrail            | A preventive, detective or corrective control constraining input, context, model, tools, workflow, output or runtime.         |
| Harness              | The execution scaffold around the model that manages context, tools, state, loops, limits, recovery and completion.           |
| Intelligence system  | The integrated people, process, data, knowledge, models, context, tools, workflow, controls and runtime producing an outcome. |
| Outcome contract     | Owned agreement defining the measurable result, baseline, target, scope, value logic and guardrails.                          |
| Progressive autonomy | Increasing decision or action authority only when evidence supports the next bounded operating mode.                          |
| Vertical slice       | The smallest end-to-end implementation crossing the full outcome path, including integration and human interaction.           |

## OASIS artifact catalogue

Artifacts are grouped into six clusters that mirror the lifecycle they support: outcome and portfolio, workflow and experience, intelligence and data, architecture and governance, evaluation and assurance, and operations and scaling. The authoritative list of all twenty artifacts, each with its minimum content, its rationale, and the failure modes it guards against, is [Chapter 32 — Templates, Checklists and Tools](chapter-32-templates-checklists-and-tools.md); the fillable working version of every one of them lives in the five-part [Tools](../tools/01-outcome-and-portfolio-templates.md) series. Local methods and delivery teams may rename artifacts or combine adjacent ones to fit existing organizational paperwork, provided the underlying decision purpose each artifact exists to serve — described in Chapter 32 — is preserved rather than lost in translation. This appendix does not repeat that catalogue; it exists only to point back to it as the canonical source, since duplicating twenty artifact descriptions in two places would guarantee the two copies eventually disagree.

## Comparison with related methods

A reader arriving at OASIS from an Agile, DevOps, MLOps, ITIL, enterprise-architecture, or conventional systems-integration background will recognize pieces of their own discipline throughout this handbook, and it is worth being explicit about where OASIS extends familiar practice rather than replacing it.

Agile's contribution is iterative product delivery and continuous learning within a delivery team; OASIS does not compete with that, it supplies the outcome contracts, evidence gates, and intelligence-system-specific workstreams — Chapters 14 through 22 — that an iterative team needs but that generic Agile guidance does not specify, because generic Agile guidance was never written with model behavior, context assembly, or autonomy progression in mind. DevOps brought continuous, automated software delivery and operations discipline; OASIS extends that release and operations model — see [Chapter 21](chapter-21-deployment-operations-and-agentops.md) — to cover model, context, and tool behavior and outcome telemetry, dimensions a conventional software release pipeline has no native concept of. MLOps addressed the model and data lifecycle specifically — training, versioning, deployment, monitoring of a model as an artifact — and OASIS places that lifecycle inside human workflows, agent architectures, governance controls, and service accountability, because a well-managed model lifecycle is necessary but not sufficient for a well-managed outcome.

ITIL and ITSM bring service-management maturity: incident, change, and problem management discipline that most enterprises already run some version of. OASIS adds the intelligence-quality, autonomy, and business-outcome assurance layer that a conventional service-management practice does not natively cover, without asking an organization to abandon its existing service-management investment. Enterprise architecture practices bring capability, information, application, and technology coherence across a portfolio; OASIS complements that coherence with deployment evidence and productization demand signals — see [Chapter 28](chapter-28-scaling-and-productization.md) — that tell an architecture function which capabilities have actually proven themselves in production and are ready to be treated as shared platform assets. Conventional systems-integration practice, finally, emphasizes requirements gathering, build, integration, and handover as largely sequential phases; OASIS emphasizes embedded discovery, an early vertical proof of the outcome path, progressive authority earned through evidence rather than granted at handover, and continuous learning that does not stop once the system reaches production — a meaningfully different posture for engagements where the software's behavior itself is probabilistic and needs to be governed as it evolves, not just delivered once and left alone.

| **Method**              | **Primary focus**                                              | **OASIS relationship**                                                                              |
|--------------------------|------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Agile                   | Iterative product delivery and learning.                       | OASIS supplies outcome contracts, evidence gates and intelligence-system workstreams.               |
| DevOps                  | Software delivery and operations.                               | OASIS extends release and operations to model/context/tool behavior and outcome telemetry.          |
| MLOps                   | Model and data lifecycle.                                      | OASIS places models inside human workflows, agents, controls and service accountability.            |
| ITIL / ITSM             | Service management and support.                                | OASIS adds intelligence quality, autonomy and business-outcome assurance.                           |
| Enterprise architecture | Capability, information, application and technology coherence. | OASIS provides deployment evidence and productization demand.                                       |
| Conventional SI         | Requirements, build, integration and handover.                 | OASIS emphasizes embedded discovery, vertical proof, progressive authority and continuous learning. |

## Reference framework alignment

OASIS is an original methodology, developed independently of any single regulatory or standards body, and it does not certify compliance with any of them on its own. What it does is organize evidence — through the [Risk and Control Register](chapter-32-templates-checklists-and-tools.md#17-risk-and-control-register), the [Autonomy Matrix](chapter-32-templates-checklists-and-tools.md#12-autonomy-matrix), and the other governance artifacts in Chapter 32 — in a form that is compatible with how the frameworks below expect evidence to be structured, which materially shortens the distance between "we run OASIS" and "we can demonstrate alignment with framework X" when that demonstration becomes necessary.

Rather than enumerate every framework's clauses here, which would duplicate material that already exists and is actively maintained elsewhere, this section points to that maintained source. The [References: Regulatory and Standards Framework Alignment Index](../references/regulatory-framework-alignment-index.md) is the authoritative, living index — it categorizes frameworks by type (certifiable management-system standards, voluntary risk-management frameworks, and binding law), explains what alignment with each category actually buys a practitioner, walks through a global triage sequence for determining which frameworks actually apply to a given engagement, and links to the framework-specific alignment checklists in [Standards](../standards/) that operationalize [Chapter 20 — Governance, Compliance and Regulatory Engineering](chapter-20-governance-compliance-and-regulatory-engineering.md). Start there, not here, whenever a specific framework question arises — the sources below are the primary references that inform OASIS's risk, management, engineering, and agent practices, and should always be read in their current official form and interpreted for the organization's own jurisdiction and role:

- [NIST AI Risk Management Framework and Generative AI Profile](https://www.nist.gov/itl/ai-risk-management-framework)

- [ISO/IEC 42001 — Artificial intelligence management systems](https://www.iso.org/standard/42001)

- [ISO/IEC 23894 — Guidance on AI risk management](https://www.iso.org/standard/77304.html)

- [European Commission — EU AI Act regulatory framework](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai)

- [Government of India — Digital Personal Data Protection Act, 2023](https://www.meity.gov.in/static/uploads/2024/06/2bf1f0e9f04e6fb4f8fef35e82c42aa5.pdf)

- [Government of India — Digital Personal Data Protection Rules, 2025](https://www.meity.gov.in/documents/act-and-policies/digital-personal-data-protection-rules-2025-gDOxUjMtQWa)

- [OWASP — Agentic AI threats and mitigations](https://genai.owasp.org/resource/agentic-ai-threats-and-mitigations/)

- [OWASP Top 10 for Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/)

- [OpenAI — A practical guide to building AI agents](https://openai.com/business/guides-and-resources/a-practical-guide-to-building-ai-agents/)

- [Anthropic — Building effective AI agents](https://www.anthropic.com/engineering/building-effective-agents)

- [Anthropic — Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

- [Anthropic — Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents)

- [Microsoft Agent Framework overview](https://learn.microsoft.com/en-us/agent-framework/overview/)

For the framework-specific alignment checklists themselves — ISO/IEC 42001, the NIST AI RMF, the EU AI Act, and the India DPDP Act and Rules, plus guidance on the broader landscape of overlay standards such as OWASP, MITRE ATLAS, SOC 2, and sector-specific regulation — see [Standards](../standards/), indexed and explained in full at [References: Regulatory and Standards Framework Alignment Index](../references/regulatory-framework-alignment-index.md).

## Methodology disclaimer

OASIS provides a structured management and engineering method. It does not itself certify compliance, replace professional legal, security, safety, engineering or regulatory advice, or guarantee a business result. Each organization remains responsible for applicable obligations, risk acceptance and operational decisions. This disclaimer applies equally to every checklist, template, and alignment reference in the [Standards](../standards/) and [References](../references/) folders, and to every artifact produced using the [Chapter 32](chapter-32-templates-checklists-and-tools.md) toolkit — none of them substitute for qualified legal, security, or regulatory counsel engaged directly by the organization applying the methodology.

---

[← Previous: Chapter 32: Templates, Checklists and Tools](chapter-32-templates-checklists-and-tools.md) · [Contents](../README.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
