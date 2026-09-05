<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 18: Evaluation and Reliability Engineering](chapter-18-evaluation-and-reliability-engineering.md) · [Contents](../README.md) · [Next: Chapter 20: Governance, Compliance and Regulatory Engineering →](chapter-20-governance-compliance-and-regulatory-engineering.md)

# Chapter 19: Security and Responsible AI Engineering

> **Implementation companion:** [Compass](https://github.com/knowledgetrailsai/Responsible-AI) (`14-ai-security/`) for policy and the security catalog; [Helm](https://github.com/knowledgetrailsai/Helm) (`06-security-and-containment/`) for runtime containment.


> **CHAPTER PURPOSE** Embed defense-in-depth security, misuse prevention, fairness, transparency, human control and containment throughout the lifecycle.

## Background and context

Chapter 18 built the evidence system that tells a team whether an intelligence system is good enough to ship. That system has a blind spot: an evaluation dataset covers failures a team could imagine, not a deliberately engineered attack.

This chapter asks what happens when an adversary, a compromised dependency, or a user's mistake pushes the system outside every tested condition. A system nobody is attacking can still cause harm through bias, opacity, or a lack of human control — responsible AI engineering keeps that harm from being the default.

Security and responsible-AI engineering are one discipline wearing two names. A control that stops prompt injection also stops an honest user's ambiguous request from cascading into an unauthorized action, and a containment procedure built for a compromised agent is the same one used when a benign agent misbehaves. Splitting these into separate workstreams produces a security review that never asks whether a system is fair, and a fairness review that never asks whether an attacker could manipulate it.

Chapter 18's adversarial testing is the evaluation-side twin of the controls here — a failure found in evaluation is often the first sign of a security gap. Chapter 20 turns the properties and controls defined here into obligations, evidence, and accountable owners a regulator or auditor can inspect. Chapter 19 builds the controls; Chapter 20 proves you have them.

This chapter covers why and what, not how. The implementation companion is the [Security: Agentic AI Threat Model and Control Checklist](../security/agentic-ai-threat-and-control-checklist.md), which turns the control layers and threat model below into a fillable instrument mapped to the OWASP Top 10 for LLM Applications, the OWASP Top 10 for Agentic Applications, and MITRE ATLAS. The enterprise identity and trust model every control depends on is architected once in [Architecture Perspective 8 — Security and Trust Architecture](../architecture/perspective-08-security-and-trust-architecture.md), and the [OASIS Reference Architecture's defense-in-depth overlay](../architecture/oasis-reference-architecture.md#3-defense-in-depth-overlay) shows where each layer sits in a concrete diagram.

## Defense-in-depth control layers

No single control is trustworthy alone: an input filter can be bypassed by a novel encoding, a tool allow-list by a compromised credential, a model's safety training by a creative prompt. Defense-in-depth layers independent controls across the request's entire path, so a failure at one is caught by another instead of propagating unchecked. Helm's [Defense-in-Depth Control Layers](https://github.com/knowledgetrailsai/Helm/blob/main/06-security-and-containment/defense-in-depth-layers.md) works through these eight layers from a running system's point of view.

| **Layer**  | **Representative controls**                                                              |
|------------|--------------------------------------------------------------------------------------------------|
| Input      | File validation, malicious content detection, PII handling, rate and size limits.        |
| Context    | Source trust, authorization filters, provenance, data minimization, injection isolation. |
| Model      | Instructions, safety behavior, restricted capabilities, model-provider controls.         |
| Tool       | Allow lists, schemas, least privilege, confirmation, transaction and spend limits.       |
| Workflow   | Approvals, segregation of duties, checkpoints, escalation and compensation.              |
| Output     | Grounding, policy, privacy, schema and business-rule validation.                         |
| Runtime    | Sandboxing, network limits, secrets, step/time/token budgets and containment.            |
| Operations | Monitoring, incident response, revocation, rollback, kill switch and audit.              |

The layers follow the request's actual path. Input and Context controls exist because an attacker's most direct route in is the evidence the system reasons over, not the model itself — untrusted content must be treated as potentially adversarial the moment it crosses the trust boundary. Model-layer controls are the thinnest layer, since safety training belongs to the provider's model, not to anything built in-house — which is why the Context and Tool layers on either side are engineered to hold even when the model layer alone would not.

Tool and Workflow controls are where an agent's decisions become real-world actions: least-privilege access, spend limits, and approval checkpoints matter because a model's output is only a proposal until a tool executes it. Output validation catches the fluent-but-wrong response that upstream controls missed. Runtime and Operations assume everything above them will eventually fail unexpectedly — sandboxing and budgets bound the damage, and monitoring, incident response and kill switches stop it. The [Security checklist's mapping of these layers to the OWASP LLM Top 10](../security/agentic-ai-threat-and-control-checklist.md#1-defense-in-depth-control-layers-ch-19-mapped-to-owasp-llm-top-10) gives each row a named artifact and owner, and the [Reference Architecture's defense-in-depth overlay](../architecture/oasis-reference-architecture.md#3-defense-in-depth-overlay) shows exactly where each layer is enforced.

## Agentic threat model

An agent that can choose and execute actions has an attack surface a static model doesn't, which makes agentic threat modeling its own discipline. Helm's [Agentic Threat Model](https://github.com/knowledgetrailsai/Helm/blob/main/06-security-and-containment/agentic-threat-model.md) and Compass's [Securing Agentic AI](https://github.com/knowledgetrailsai/Responsible-AI/blob/main/14-ai-security/securing-agentic-ai.md) both catalog the categories below in depth: prompt and context injection, malicious or compromised tools, excessive agency, identity confusion, memory poisoning, secret leakage, insecure inter-agent communication, supply-chain compromise, goal manipulation, cascading failures and denial of wallet.

Prompt and context injection is the easiest entry point: it needs no privileged access, only adversarial text placed somewhere the system will read it. Excessive agency and identity confusion are specific to autonomy — a system acting on an attacker's behalf, or unsure what authority it's acting under, turns injection into a real-world consequence. Memory poisoning and insecure inter-agent communication extend the problem across time and system boundaries: an undetected manipulation can persist in memory or spread to every agent that trusts its output.

Multi-agent systems compound this: every extra agent adds a trust boundary, a surface for shared-state corruption, and a path for a compromised instruction to spread before a human or guardrail sees it, as Helm's threat model spells out in its [multi-agent systems section](https://github.com/knowledgetrailsai/Helm/blob/main/06-security-and-containment/agentic-threat-model.md#multi-agent-systems-compound-this). The [orchestration-pattern decision rule](../architecture/oasis-reference-architecture.md#4-selecting-the-orchestration-pattern-ch-14-7-decision-rule) therefore treats multi-agent design as something that must earn its complexity — an unjustified multi-agent design is a security finding as much as an architecture one.

This list is a starting point, not an endpoint — the field moves fast enough that a fixed taxonomy would be stale within a year. The [Security checklist's agentic threat model mapping](../security/agentic-ai-threat-and-control-checklist.md#2-agentic-threat-model-ch-19-mapped-to-owasp-agentic-top-10-and-mitre-atlas) ties each threat above to its OWASP Agentic category and the MITRE ATLAS tactic an attacker would use to get there: OWASP for what can go wrong, ATLAS for how an attacker gets there. It also flags two OWASP Agentic categories not named above — unexpected code execution and human-agent trust exploitation. Because every threat here depends on an agent's identity and trust boundary, [Architecture Perspective 8 — Security and Trust Architecture](../architecture/perspective-08-security-and-trust-architecture.md) is where credential issuance, scoping, revocation, and inter-agent authority inheritance are designed once, at the enterprise level.

## Responsible AI properties

Security controls stop a system from being made to fail by an adversary. Responsible AI properties stop it from causing harm when nothing is attacking it. Both must be engineered, not assumed. A system must demonstrate **validity and reliability** for its intended population and conditions, which is what [Chapter 18's evaluation hierarchy](chapter-18-evaluation-and-reliability-engineering.md#evaluation-hierarchy) verifies. **Safety, security and resilience** under foreseeable misuse and failure is this chapter's own territory: the layers and threat model above engineer this property rather than merely asserting it.

**Fairness and harmful-bias assessment** must be scoped to the groups a given system's decisions actually affect, not treated as one universal test, and belongs in the Chapter 18 evaluation dataset. **Privacy, data minimization and purpose limitation** means a system collects, retains and uses only the personal data its purpose requires — a legal obligation once personal data crosses into a regulated jurisdiction, where Chapter 20 picks up. **Transparency** about AI use, capabilities, limitations and generated content, and **explainability** sufficient for the decision at hand, exist so users never assume a capability the system doesn't have. **Human accountability, oversight, appeal and remedy** closes the loop: every property above is only as real as a human's ability to review, understand, and correct a decision.

These seven properties describe what a responsible system must demonstrate, not how to test for it. The [Security checklist's responsible-AI properties table](../security/agentic-ai-threat-and-control-checklist.md#3-responsible-ai-properties-where-deeper-standards-guidance-lives) points each to where it's operationalized: validity and reliability to Chapter 18 and the NIST AI RMF's Measure function, fairness to the NIST Generative AI Profile and ISO/IEC 42001 Annex A, privacy to the DPDP Act checklist and the [Regulatory Framework Alignment Index](../references/regulatory-framework-alignment-index.md), transparency and human oversight to the EU AI Act's Articles 13, 14 and 50, and explainability to ISO/IEC 42001 Annex A.9.

## Containment and emergency control

Every action-taking system must define its maximum blast radius: accessible data, systems, transaction value, case volume, time window and downstream authority. This answers, before an incident rather than during the scramble afterward, the question every review asks: how bad could this have been. Defining it means stating what data the system can touch at maximum authority, which systems and APIs it can reach directly or through a tool, the largest action or time-windowed aggregate it can take before triggering review, and whether its output auto-executes or waits on a human.

Emergency controls must be usable by operations without development intervention, and tested periodically. The moment containment is actually needed is the worst possible moment to discover that suspending an agent requires a code deployment. A kill switch never drilled is an assumption, not a functioning control. Suspension should preserve evidence and move work to a safe manual or deterministic path — stopping a misbehaving system must not destroy the trace record explaining what went wrong, or strand in-flight work. Helm's [Containment & Emergency Control](https://github.com/knowledgetrailsai/Helm/blob/main/06-security-and-containment/containment-and-emergency-control.md) and Compass's [containment principle](https://github.com/knowledgetrailsai/Responsible-AI/blob/main/14-ai-security/securing-agentic-ai.md#the-containment-principle) both operationalize this for a live system.

This section covers what containment must achieve, not a step-by-step procedure — that belongs in the [Security checklist's containment and emergency control checklist](../security/agentic-ai-threat-and-control-checklist.md#4-containment-and-emergency-control-checklist), ten ownable items including accessible data and systems, transaction-value and case-volume limits and their reset window, a named kill-switch owner who need not be a developer, the date and result of the last suspension drill, and the safe fallback path.

At enterprise scale this must operate above any single system, since a shared component's failure — a compromised model route, a shared integration, a poisoned knowledge domain — has a blast radius spanning every system consuming it. [Architecture Perspective 9 — Operations and Observability Architecture](../architecture/perspective-09-operations-and-observability-architecture.md) defines the tiered kill-switch authority for enterprise-wide containment: a system owner suspending their own agent, a platform owner suspending a shared component for every consumer, and a governance forum chair's emergency authority to suspend execution across the entire agentic estate.

---

[← Previous: Chapter 18: Evaluation and Reliability Engineering](chapter-18-evaluation-and-reliability-engineering.md) · [Contents](../README.md) · [Next: Chapter 20: Governance, Compliance and Regulatory Engineering →](chapter-20-governance-compliance-and-regulatory-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
