<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 19: Security and Responsible AI Engineering](../methodology/chapter-19-security-and-responsible-ai-engineering.md) · [Reference Framework Alignment Index](../references/regulatory-framework-alignment-index.md) · [Architecture: Reference Architecture](../architecture/oasis-reference-architecture.md)

# Security: Agentic AI Threat Model and Control Checklist

> **PURPOSE** Turn Chapter 19's defense-in-depth control layers and agentic threat model into a concrete, fillable checklist, cross-referenced to the named security frameworks listed in the [Reference Framework Alignment Index](../references/regulatory-framework-alignment-index.md#other-standards-and-frameworks-relevant-to-oasis). This is a structuring aid, not a penetration test, red-team exercise, or certification — engage qualified security practitioners for those.

**Primary OASIS source:** [Chapter 19 — Security and Responsible AI Engineering](../methodology/chapter-19-security-and-responsible-ai-engineering.md); cross-referenced with [Chapter 20 — Governance, Compliance and Regulatory Engineering](../methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) and the [Architecture Reference Architecture's defense-in-depth overlay](../architecture/oasis-reference-architecture.md#3-defense-in-depth-overlay).

**Implemented in:** [Compass](https://github.com/knowledgetrailsai/responsible-ai) (`14-ai-security/`) — the full policy and control catalog behind the defense-in-depth layers and agentic threat model below, plus Chapter 20's jurisdiction-specific regulatory coverage; [Helm](https://github.com/knowledgetrailsai/Helm)'s [agentic threat model](https://github.com/knowledgetrailsai/Helm/blob/main/06-security-and-containment/agentic-threat-model.md) implements the runtime containment layer that enforces these controls in production, and [Verity](https://github.com/knowledgetrailsai/Verity)'s [adversarial and red-team evaluation](https://github.com/knowledgetrailsai/Verity/blob/main/08-safety-and-regulatory-alignment/adversarial-and-red-team-evaluation.md) is how to test whether they actually hold.

## Background and context

Chapter 19 defines security for OASIS systems as defense-in-depth across eight layers (input, context, model, tool, workflow, output, runtime, operations), plus an explicit agentic threat model and a set of responsible-AI properties. That chapter is deliberately framework-neutral: it names the layers and threats an engineering team must address without tying itself to any one vendor's or standards body's naming. The frameworks that best describe agentic AI risk are still moving fast, and a hard-coded reference would go stale quickly — the OWASP Agentic Top 10 referenced below, for example, was only published in December 2025. This checklist fills that gap: it takes Chapter 19's layers and threats and maps each one to the current external frameworks a security team would actually use to test, benchmark, and communicate about them.

Three external frameworks do most of the work here. The **OWASP Top 10 for LLM Applications (2025)** catalogues the most common vulnerability classes in LLM-based applications — prompt injection, sensitive information disclosure, supply-chain risk, data/model poisoning, improper output handling, excessive agency, system-prompt leakage, vector/embedding weaknesses, misinformation, and unbounded consumption. It is the most widely adopted AI-application security taxonomy in current use. The **OWASP Top 10 for Agentic Applications (2026)**, published 9 December 2025 by more than 100 security practitioners, is the newer, agent-specific companion. It covers goal hijacking, tool misuse, identity/privilege abuse, agentic supply-chain vulnerabilities, unexpected code execution, memory/context poisoning, insecure inter-agent communication, cascading failures, human-agent trust exploitation, and rogue agents — risks that only exist once a system can choose and execute actions autonomously. This is exactly the territory Chapter 19's "agentic threat model" section describes in prose. **MITRE ATLAS** (Adversarial Threat Landscape for Artificial-Intelligence Systems) is a distinct kind of reference. Rather than a top-10 vulnerability list, it is a tactic-and-technique knowledge base — modeled on MITRE ATT&CK — describing the adversary's kill chain against ML/AI systems across roughly 14 tactics (Reconnaissance, Resource Development, Initial Access, ML Model Access, Execution, Persistence, Privilege Escalation, Defense Evasion, Credential Access, Discovery, Collection, ML Attack Staging, Exfiltration, Impact). Where OWASP tells you *what* can go wrong, ATLAS tells you *how an attacker gets there* — useful for threat-modeling exercises and red-team scoping rather than for a build-time checklist alone.

**How to use this checklist:** for each row, record status (Not started / In progress / Evidenced), the OASIS artifact carrying the evidence, and the accountable owner per the [Responsibility Assignment Matrix](../methodology/chapter-32-templates-checklists-and-tools.md#19-responsibility-assignment-matrix). Where this checklist and a Standards checklist (e.g., ISO/IEC 42001, NIST AI RMF) reference the same underlying control, populate the [Risk and Control Register](../methodology/chapter-32-templates-checklists-and-tools.md#17-risk-and-control-register) once and cross-reference it, consistent with the anti-bureaucracy test in Chapter 13.

## 1. Defense-in-depth control layers (Ch. 19), mapped to OWASP LLM Top 10

Chapter 19 defines eight control layers. Each maps to one or more OWASP LLM Top 10 (2025) categories it is primarily designed to prevent, detect or contain.

| # | Ch. 19 layer | Representative controls | OWASP LLM Top 10 (2025) coverage | Artifact | Status | Owner |
|---|---|---|---|---|---|---|
| 1 | Input | File validation, malicious content detection, PII handling, rate and size limits. | LLM01 Prompt Injection (partial); LLM10 Unbounded Consumption | [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md) input validation fields; [Compass securing-genai.md](https://github.com/knowledgetrailsai/responsible-ai/blob/main/14-ai-security/securing-genai.md) | | |
| 2 | Context | Source trust, authorization filters, provenance, data minimization, injection isolation. | LLM01 Prompt Injection; LLM02 Sensitive Information Disclosure; LLM08 Vector and Embedding Weaknesses | Context Architecture (Ch.14 §4); [Forge grounding-policy.md](https://github.com/knowledgetrailsai/Forge/blob/main/04-grounding-and-context-quality/grounding-policy.md) | | |
| 3 | Model | Instructions, safety behavior, restricted capabilities, model-provider controls. | LLM09 Misinformation (partial); LLM07 System Prompt Leakage | Model Strategy and Benchmark | | |
| 4 | Tool | Allow lists, schemas, least privilege, confirmation, transaction and spend limits. | LLM06 Excessive Agency; LLM10 Unbounded Consumption | [Tool contract template](../engineering/tool-and-integration-interface-specification.md#1-tool-contract-template); [Helm tool-contracts-and-integration-principles.md](https://github.com/knowledgetrailsai/Helm/blob/main/07-tool-integration/tool-contracts-and-integration-principles.md); [Compass securing-agentic-ai.md](https://github.com/knowledgetrailsai/responsible-ai/blob/main/14-ai-security/securing-agentic-ai.md) | | |
| 5 | Workflow | Approvals, segregation of duties, checkpoints, escalation and compensation. | LLM06 Excessive Agency | Harness and Workflow Design (Ch.14 §6-7); [Loom's](https://github.com/knowledgetrailsai/Loom) workflow-blueprint escalation triggers | | |
| 6 | Output | Grounding, policy, privacy, schema and business-rule validation. | LLM05 Improper Output Handling; LLM09 Misinformation | [Human–AI Workflow Blueprint](../methodology/chapter-32-templates-checklists-and-tools.md#7-human-ai-workflow-blueprint); [Forge grounding-policy.md](https://github.com/knowledgetrailsai/Forge/blob/main/04-grounding-and-context-quality/grounding-policy.md) | | |
| 7 | Runtime | Sandboxing, network limits, secrets, step/time/token budgets and containment. | LLM03 Supply Chain (partial); LLM10 Unbounded Consumption | [Monitoring: Observability and Telemetry Specification](../monitoring/observability-and-telemetry-specification.md) release manifest; [Helm containment-and-emergency-control.md](https://github.com/knowledgetrailsai/Helm/blob/main/06-security-and-containment/containment-and-emergency-control.md) | | |
| 8 | Operations | Monitoring, incident response, revocation, rollback, kill switch and audit. | LLM03 Supply Chain; LLM04 Data and Model Poisoning (detection) | [Failure Taxonomy](../methodology/chapter-32-templates-checklists-and-tools.md#10-failure-taxonomy); incident classification; [Helm responsible-layer-taxonomy.md](https://github.com/knowledgetrailsai/Helm/blob/main/03-incident-response/responsible-layer-taxonomy.md); [Compass security-incident-response.md](https://github.com/knowledgetrailsai/responsible-ai/blob/main/14-ai-security/security-incident-response.md) | | |

Two OWASP items do not map cleanly to a single layer and should be tracked separately: **LLM03 Supply Chain** spans model, tool and runtime provenance (see the Vendor Due-Diligence Record in Chapter 20), and **LLM04 Data and Model Poisoning** spans context (retrieval/knowledge sources) and model (training/fine-tuning inputs, where applicable) — track both against the [Data and Knowledge Readiness Assessment](../methodology/chapter-32-templates-checklists-and-tools.md#8-data-and-knowledge-readiness-assessment).

## 2. Agentic threat model (Ch. 19), mapped to OWASP Agentic Top 10 and MITRE ATLAS

[Helm's agentic threat model](https://github.com/knowledgetrailsai/Helm/blob/main/06-security-and-containment/agentic-threat-model.md) covers the same eleven categories with the runtime containment detail for a deployed agent; [Compass's securing-agentic-ai.md](https://github.com/knowledgetrailsai/responsible-ai/blob/main/14-ai-security/securing-agentic-ai.md) is the fuller control catalog per threat.

Chapter 19's agentic threat model names eleven threat categories. Each maps to its nearest OWASP Top 10 for Agentic Applications (2026) category and the MITRE ATLAS tactic(s) most relevant to that threat's attack path.

| # | Ch. 19 agentic threat | OWASP Agentic Top 10 (2026) | Relevant MITRE ATLAS tactic(s) | Primary Ch. 19 layer | Artifact | Status | Owner |
|---|---|---|---|---|---|---|---|
| 1 | Prompt and context injection | — (covered by OWASP LLM01, carried into agentic scope) | Initial Access; Execution | Input, Context | Context Architecture | | |
| 2 | Malicious or compromised tools | ASI02 Tool Misuse & Exploitation | Resource Development; Initial Access | Tool | [Tool contract template](../engineering/tool-and-integration-interface-specification.md#1-tool-contract-template) | | |
| 3 | Excessive agency | ASI01 Agent Goal Hijack | Execution; Privilege Escalation | Workflow | [Autonomy Matrix](../methodology/chapter-32-templates-checklists-and-tools.md#12-autonomy-matrix); Compass securing-agentic-ai.md "Excessive agency" row | | |
| 4 | Identity confusion | ASI03 Identity & Privilege Abuse | Credential Access; Privilege Escalation | Tool, Workflow | Tool authorization field (`authorize_against`) | | |
| 5 | Memory poisoning | ASI06 Memory & Context Poisoning | ML Attack Staging; Persistence | Context | [Memory and State Engineering](../engineering/memory-and-state-engineering.md) (Ch.14 §8); Helm agentic-threat-model.md "Memory poisoning" row | | |
| 6 | Secret leakage | — (adjacent to OWASP LLM02, ASI03) | Credential Access; Exfiltration | Runtime, Operations | [Monitoring spec](../monitoring/observability-and-telemetry-specification.md) audit/trace fields | | |
| 7 | Insecure inter-agent communication | ASI07 Insecure Inter-Agent Communication | Collection; Exfiltration | Workflow, Runtime | Harness and Workflow Design (Ch.14 §6-7) | | |
| 8 | Supply-chain compromise | ASI04 Agentic Supply Chain Vulnerabilities | Resource Development; Initial Access | Tool, Runtime | Ch.20 — Model, Vendor and Open-Source Due-Diligence Record; [Compass supply-chain-security.md](https://github.com/knowledgetrailsai/responsible-ai/blob/main/14-ai-security/supply-chain-security.md) | | |
| 9 | Goal manipulation | ASI01 Agent Goal Hijack; ASI10 Rogue Agents | ML Attack Staging; Impact | Model, Workflow | Intelligence-System Specification (Ch.14 §1) | | |
| 10 | Cascading failures | ASI08 Cascading Failures | Impact | Workflow, Runtime | [Service Runbook](../methodology/chapter-32-templates-checklists-and-tools.md#16-service-runbook) | | |
| 11 | Denial of wallet | — (adjacent to OWASP LLM10 Unbounded Consumption) | Impact | Runtime | [Monitoring spec](../monitoring/observability-and-telemetry-specification.md) economic plane budgets/alerts; [Fulcrum hidden-multipliers.md](https://github.com/knowledgetrailsai/oasis-fulcrum/blob/main/02-cost-economics/hidden-multipliers.md) (Agentic Loop Multiplier) | | |

Two additional categories from the OWASP Agentic Top 10 are not separately named in Chapter 19 and should be added explicitly to any engagement's threat register: **ASI05 Unexpected Code Execution (RCE)** — relevant wherever an agent can generate or execute code, not only call pre-defined tools — and **ASI09 Human-Agent Trust Exploitation** — an attacker manipulating the human overseer's trust in the agent (e.g., via convincing but false agent-generated justifications) rather than attacking the system directly. Track both under the [Human–AI Workflow Blueprint](../methodology/chapter-32-templates-checklists-and-tools.md#7-human-ai-workflow-blueprint) until Chapter 19 is revised to name them explicitly.

**Multi-agent-specific risks** (Ch.19: trust boundaries between agents, shared-state risks, propagation of compromised instructions) correspond most directly to ASI07 (Insecure Inter-Agent Communication) and ASI10 (Rogue Agents) above, and should be scoped explicitly whenever the [orchestration-pattern decision](../architecture/oasis-reference-architecture.md#4-selecting-the-orchestration-pattern-ch-14-7-decision-rule) selects a multi-agent design.

## 3. Responsible AI properties — where deeper standards guidance lives

Chapter 19 names seven responsible-AI properties (validity/reliability, safety/security/resilience, fairness, privacy, transparency, explainability, human accountability). This checklist does not re-derive detailed test methods for each — that material already lives in the Standards folder and should be read alongside this file rather than duplicated:

| Property | Where it's operationalized in detail |
|---|---|
| Validity and reliability | [Chapter 18 — Evaluation and Reliability Engineering](../methodology/chapter-18-evaluation-and-reliability-engineering.md); NIST AI RMF Measure function ([checklist](../standards/nist-ai-rmf-alignment-checklist.md)) |
| Safety, security and resilience | Sections 1–2 above; EU AI Act Art. 15 ([checklist](../standards/eu-ai-act-alignment-checklist.md)) |
| Fairness and bias | NIST AI RMF Generative AI Profile fairness item ([checklist](../standards/nist-ai-rmf-alignment-checklist.md#generative-ai-profile-additional-risks-to-track)); ISO/IEC 42001 Annex A ([checklist](../standards/iso-42001-alignment-checklist.md)) |
| Privacy and data minimization | [DPDP Act checklist](../standards/dpdp-act-alignment-checklist.md); GDPR and other privacy overlays (see [References index](../references/regulatory-framework-alignment-index.md)) |
| Transparency | EU AI Act Art. 13, 50 ([checklist](../standards/eu-ai-act-alignment-checklist.md)) |
| Explainability | ISO/IEC 42001 Annex A.9 ([checklist](../standards/iso-42001-alignment-checklist.md)) |
| Human accountability, oversight, appeal and remedy | EU AI Act Art. 14 Human Oversight ([checklist](../standards/eu-ai-act-alignment-checklist.md)); [Autonomy Matrix](../methodology/chapter-32-templates-checklists-and-tools.md#12-autonomy-matrix) |

## 4. Containment and emergency control checklist

Chapter 19 requires every action-taking system to define its maximum blast radius and to have emergency controls usable without development intervention. Complete before production release:

| # | Item | Detail to record | Status | Owner |
|---|---|---|---|---|
| 1 | Accessible data | What data classes/systems can this agent read or write at maximum authority? | | |
| 2 | Accessible systems | Which enterprise systems/APIs can this agent reach, directly or via tools? | | |
| 3 | Transaction value limit | Maximum monetary or business value this agent can commit in a single action / time window. | | |
| 4 | Case volume limit | Maximum number of cases/records this agent can act on in a defined window before requiring review. | | |
| 5 | Time window | The window over which the above limits are measured and reset. | | |
| 6 | Downstream authority | What real-world authority does this agent's output carry (e.g., does it auto-execute, or require approval)? | | |
| 7 | Kill switch owner | Named role who can suspend this agent, and how (must not require a developer). | | |
| 8 | Kill switch test | Date of last tested suspension drill and result. | | |
| 9 | Evidence preservation on suspension | Confirm suspension preserves trace/evidence rather than discarding in-flight state. | | |
| 10 | Safe fallback path | The manual or deterministic path work transitions to when suspended. | | |

## 5. Underlying security-standards baseline

This checklist assumes — rather than restates — the general-purpose security-standards baseline already indexed in the [Reference Framework Alignment Index](../references/regulatory-framework-alignment-index.md#other-standards-and-frameworks-relevant-to-oasis). In particular: **ISO/IEC 27001/27002** should already govern the organization's information-security management system into which these AI-specific controls fit; **ISO/IEC 27701** should govern privacy-information management where personal data is material; **ISO/IEC 27017/27018** apply where the intelligence system is cloud-hosted; **NIST Cybersecurity Framework 2.0** and **NIST SP 800-53** provide the enterprise cyber-governance and control-catalog language for regulated or high-assurance environments; **NIST SP 800-218 (SSDF)** governs the secure software development lifecycle for any deployable harness, tool, or agent code; and the **CSA AI Controls Matrix / Cloud Controls Matrix** is the reference for allocating controls between cloud provider and customer. If none of these are already in place, treat that as a prerequisite gap to raise at the [Chapter 13](../methodology/chapter-13-decision-gates-and-evidence-model.md) engineering decision gate, not something this Security checklist alone can substitute for.

---

[← Back to Contents](../README.md) · [Chapter 19: Security and Responsible AI Engineering](../methodology/chapter-19-security-and-responsible-ai-engineering.md) · [Reference Framework Alignment Index](../references/regulatory-framework-alignment-index.md) · [Architecture: Reference Architecture](../architecture/oasis-reference-architecture.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
