<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 18: Evaluation and Reliability Engineering](chapter-18-evaluation-and-reliability-engineering.md) · [Contents](README.md) · [Next: Chapter 20: Governance, Compliance and Regulatory Engineering →](chapter-20-governance-compliance-and-regulatory-engineering.md)

# Chapter 19: Security and Responsible AI Engineering

# Security and Responsible AI Engineering

> **CHAPTER PURPOSE** Embed defense-in-depth security, misuse prevention, fairness, transparency, human control and containment throughout the lifecycle.

## Defense-in-depth control layers

| **Layer**  | **Representative controls**                                                              |
|------------|------------------------------------------------------------------------------------------|
| Input      | File validation, malicious content detection, PII handling, rate and size limits.        |
| Context    | Source trust, authorization filters, provenance, data minimization, injection isolation. |
| Model      | Instructions, safety behavior, restricted capabilities, model-provider controls.         |
| Tool       | Allow lists, schemas, least privilege, confirmation, transaction and spend limits.       |
| Workflow   | Approvals, segregation of duties, checkpoints, escalation and compensation.              |
| Output     | Grounding, policy, privacy, schema and business-rule validation.                         |
| Runtime    | Sandboxing, network limits, secrets, step/time/token budgets and containment.            |
| Operations | Monitoring, incident response, revocation, rollback, kill switch and audit.              |

## Agentic threat model

Threat modelling covers prompt and context injection, malicious or compromised tools, excessive agency, identity confusion, memory poisoning, secret leakage, insecure inter-agent communication, supply-chain compromise, goal manipulation, cascading failures and denial of wallet. Multi-agent systems add trust boundaries between agents, shared-state risks and propagation of compromised instructions.

## Responsible AI properties

- Validity and reliability for the intended population and conditions

- Safety, security and resilience under foreseeable misuse and failure

- Fairness and harmful-bias assessment appropriate to affected groups

- Privacy, data minimization and purpose limitation

- Transparency about AI use, capabilities, limitations and generated content

- Explainability sufficient for the decision, review and contestability context

- Human accountability, oversight, appeal and remedy

## Containment and emergency control

Every action-taking system defines its maximum blast radius: accessible data, systems, transaction value, case volume, time window and downstream authority. Emergency controls must be usable by operations without development intervention and tested periodically. Suspension should preserve evidence and transition work to a safe manual or deterministic path.

---

[← Previous: Chapter 18: Evaluation and Reliability Engineering](chapter-18-evaluation-and-reliability-engineering.md) · [Contents](README.md) · [Next: Chapter 20: Governance, Compliance and Regulatory Engineering →](chapter-20-governance-compliance-and-regulatory-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](LICENSE.md).
