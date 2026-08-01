<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 20: Governance, Compliance and Regulatory Engineering](chapter-20-governance-compliance-and-regulatory-engineering.md) · [Contents](README.md) · [Next: Chapter 22: Economics, FinOps and Sustainability →](chapter-22-economics-finops-and-sustainability.md)

# Chapter 21: Deployment, Operations and AgentOps

# Deployment, Operations and AgentOps

> **CHAPTER PURPOSE** Run intelligence systems as production services with versioning, tracing, quality monitoring, incident response, rollback and learning loops.

## Production operating model

AgentOps extends DevOps and MLOps to the behavior of complete intelligence systems. It must show which prompt, context policy, knowledge version, model, tool, workflow, control and user authority produced an outcome. Monitoring joins service telemetry with quality sampling and business events.

| **Operational plane** | **Measures and controls**                                                                                  |
|-----------------------|------------------------------------------------------------------------------------------------------------|
| Service               | Availability, latency, throughput, errors, queue depth, capacity and dependency health.                    |
| Intelligence          | Correctness, grounding, retrieval, tool choice, completion, abstention and escalation.                     |
| Risk                  | Unauthorized attempts, incorrect actions, policy violations, complaints, near misses and control failures. |
| Human                 | Adoption, overrides, approval time, exception load, rework and workaround behavior.                        |
| Economic              | Tokens, model and infrastructure cost, tool cost, intervention and cost per successful outcome.            |
| Outcome               | Primary result, leading indicators, guardrails and distribution across segments.                           |

## Version and release management

- Immutable release manifest across model, prompt, context, index, tool, workflow, schema and control versions.

- Automated regression, security, integration and policy tests before release.

- Canary, cohort, shadow or percentage rollout with measurable stop conditions.

- Model-provider change detection and fallback compatibility.

- Rollback or forward-fix decision based on blast radius and state compatibility.

- Change communication to users, operations, risk owners and affected business processes.

## Incident diagnosis

Incidents are classified at the responsible layer: model reasoning, missing or unauthorized context, retrieval, tool selection, tool execution, state, workflow, policy, human approval or enterprise dependency. The incident record includes the business consequence, affected cases, configuration, trace, containment, correction, regression case and control improvement.

## Learning loop

> **PRODUCTION LOOP** Observe outcome and failures → diagnose the responsible layer → add or update evaluation cases → implement the smallest effective change → regression test → controlled release → verify outcome.

---

[← Previous: Chapter 20: Governance, Compliance and Regulatory Engineering](chapter-20-governance-compliance-and-regulatory-engineering.md) · [Contents](README.md) · [Next: Chapter 22: Economics, FinOps and Sustainability →](chapter-22-economics-finops-and-sustainability.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](LICENSE.md).
