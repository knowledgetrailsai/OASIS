<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 33: Appendices and Reference Material](../Methodology/chapter-33-appendices-and-reference-material.md) · [Chapter 24: Roles, Teams and Governance Forums](../Methodology/chapter-24-roles-teams-and-governance-forums.md)

# Reference: Master Glossary and Roles Roster

> **PURPOSE** Give one place to look up any term or role used across the Methodology, Architecture, Engineering, Security, Monitoring, Standards and Tools material, instead of hunting through the chapter that happened to introduce it. Chapter 33's glossary is the original, narrower list scoped to the Methodology chapters; this document is the maintained, full-repository version and the one worth bookmarking.

**Primary OASIS source:** Terms and roles are drawn from across the full repository; where a term or role was defined more fully in a specific chapter or document, that source is linked as the authoritative definition — this page is the fast-lookup index, not a replacement for it.

## Background and context

A methodology this size accumulates precise terminology fast, and precision only helps if everyone means the same thing by the same word. "Autonomy" and "authority" are not interchangeable; "context engineering" and "prompt engineering" describe genuinely different disciplines with different failure modes; "groundedness" is a specific, measurable property, not a synonym for "sounds right." [Chapter 33's glossary](../Methodology/chapter-33-appendices-and-reference-material.md#glossary) already does this for the Methodology chapters. This document extends that same discipline across the companion folders — Architecture, Engineering, Security, Monitoring, Standards and Tools all introduced their own precise terms as they were built out, and until now there was no single place that pulled all of them together.

The same problem exists for roles. [Chapter 23](../Methodology/chapter-23-forward-deployed-outcome-engineering.md) defines pod-level roles; [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md) defines the enterprise roles those pod roles report into; and several Architecture perspective articles name accountability requirements (an agent's registered owner, a permission-issuance authority, a governance-forum chair) without necessarily using the exact same job title twice. Section 2 below is a single roster mapping every named role across the repository to what it's accountable for and where it's defined in full — useful when onboarding someone new, or when checking that a real organization chart actually has a named person behind every accountability this methodology assumes exists.

Treat both sections as living indexes: as new terms and roles get introduced elsewhere in the repository, add them here rather than letting a second, competing glossary start forming in some other document.

## 1. Master glossary

Alphabetical. Where a fuller definition exists elsewhere, follow the link — this entry is deliberately the short version.

| Term | Definition | Fuller source |
|---|---|---|
| Agent | A system that uses a model to choose and execute steps toward a goal within a harness and authority boundary. | [Chapter 14 §6](../Methodology/chapter-14-intelligence-and-agent-engineering.md#6-agent-harness-engineering) |
| AgentOps | Practices for deploying, observing, controlling and improving production agent systems. | [Chapter 21](../Methodology/chapter-21-deployment-operations-and-agentops.md) |
| Autonomy ceiling | The maximum decision or action authority a system or action is permitted to hold at a point in time. | [Chapter 33 glossary](../Methodology/chapter-33-appendices-and-reference-material.md#glossary) |
| Blast radius | The full extent of what an action-taking system could affect if it failed or misbehaved. | [Chapter 19](../Methodology/chapter-19-security-and-responsible-ai-engineering.md) |
| Capability map | An inventory of business capabilities an enterprise needs, independent of any single system or vendor implementing them. | [Business and Capability Architecture](../architecture/perspective-01-business-and-capability-architecture.md#1-capability-map-template) |
| Checkpoint | A saved execution state a long-running harness can resume from after an interruption, rather than restarting from scratch. | [Harness and Orchestration Engineering](../engineering/harness-and-orchestration-engineering.md) |
| Confabulation (hallucination) | A model producing fluent, confident output not actually supported by its inputs or training. | [Standards: NIST AI RMF checklist](../standards/nist-ai-rmf-alignment-checklist.md) |
| Context engineering | Construction of the complete information environment available to the model at a decision point — evidence, memory, tool definitions, policy, and token budget together. | [Chapter 14 §4](../Methodology/chapter-14-intelligence-and-agent-engineering.md#4-prompt-and-context-engineering) |
| Context window | The maximum amount of text/tokens a model can consider at once for a given call. | [Model Engineering](../engineering/model-engineering.md) |
| Decision gate | A defined checkpoint between lifecycle phases where progression is approved, conditionally approved, held, or rejected based on evidence. | [Chapter 13](../Methodology/chapter-13-decision-gates-and-evidence-model.md) |
| Decision rights | The explicit allocation of who has authority to make which category of decision, and at what level. | [Chapter 6](../Methodology/chapter-06-oasis-operating-model-and-decision-rights.md) |
| Defense-in-depth | A control strategy layering guardrails across input, context, model, tools, workflow, output and runtime so no single control failure causes unmitigated harm. | [Chapter 19](../Methodology/chapter-19-security-and-responsible-ai-engineering.md) |
| Evidence gate | A decision gate whose outcome is based on reviewed, recorded evidence rather than schedule pressure. | [Chapter 13](../Methodology/chapter-13-decision-gates-and-evidence-model.md) |
| Evaluation unit | The scope an evaluation measures at — response, agent step, completed workflow, or business outcome — progressively widening as a system matures. | [Chapter 18](../Methodology/chapter-18-evaluation-and-reliability-engineering.md) |
| FDOE | Forward Deployed Outcome Engineering: embedded, cross-functional delivery close to real users and operations. | [Chapter 23](../Methodology/chapter-23-forward-deployed-outcome-engineering.md) |
| Groundedness | The degree to which an output is actually supported by its retrieved or provided sources, as opposed to fluent but unsupported generation. | [Chapter 18](../Methodology/chapter-18-evaluation-and-reliability-engineering.md) |
| Guardrail | A preventive, detective or corrective control constraining one of the eight defense-in-depth layers. | [Chapter 19](../Methodology/chapter-19-security-and-responsible-ai-engineering.md) |
| Harness | The execution scaffold around a model that manages context assembly, tool calls, state, retries, limits, and completion. | [Chapter 14 §6](../Methodology/chapter-14-intelligence-and-agent-engineering.md#6-agent-harness-engineering) |
| Idempotency | A tool or operation's property of producing the same result if called more than once with the same inputs, so a retry after an ambiguous failure doesn't duplicate the effect. | [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md) |
| Intelligence-system specification | The behavioral contract for a system: what it must understand or do, what evidence it may use, expected output shape, permitted/prohibited actions, and cases requiring human authority. | [Chapter 14 §1](../Methodology/chapter-14-intelligence-and-agent-engineering.md#1-intelligence-system-specification) |
| Kill switch | A pre-assigned, tested mechanism to immediately suspend an agent's or a shared component's execution. | [Security checklist §4](../security/agentic-ai-threat-and-control-checklist.md#4-containment-and-emergency-control-checklist) |
| MCP (Model Context Protocol) | A standardized protocol for registering and calling tools across models and vendors, reducing per-integration custom glue code. | [Tool and Integration Interface Specification §4](../engineering/tool-and-integration-interface-specification.md#4-mcp-tool-catalogue-registration-fields) |
| Optimization ladder | The sequence of model-cost-reduction techniques to try, in order, after establishing a quality ceiling with the strongest appropriate model: routing, caching, compression, then fine-tuning as a last resort. | [Model Engineering §4](../engineering/model-engineering.md) |
| Orchestration pattern | The choice among deterministic function, explicit workflow, single agent, or multi-agent system for a given task. | [Chapter 14 §7](../Methodology/chapter-14-intelligence-and-agent-engineering.md#7-workflow-and-orchestration-engineering) |
| Progressive autonomy | Increasing a system's decision or action authority only when evidence supports the next bounded operating mode. | [Chapter 33 glossary](../Methodology/chapter-33-appendices-and-reference-material.md#glossary) |
| Responsible layer | The specific system component (model, context, retrieval, tool selection, tool execution, state, workflow, policy, human approval, enterprise dependency) an incident is classified against at intake. | [Monitoring §4](../monitoring/observability-and-telemetry-specification.md#4-incident-classification-responsible-layer-taxonomy) |
| System equation | The organizing formula for a complete intelligence system: Model + Context + Harness + Tools + Workflow + Memory/State + Controls + Evaluation + Runtime. | [Chapter 14](../Methodology/chapter-14-intelligence-and-agent-engineering.md) |
| Tool contract | The governed interface specification for anything a system can call — inputs, authorization, limits, failure semantics, audit. | [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md) |
| Trust boundary | A defined line across which content or authority is treated as more or less trusted by design (external input, enterprise perimeter, systems of record). | [Security and Trust Architecture §2](../architecture/perspective-08-security-and-trust-architecture.md#2-trust-boundaries) |
| Vertical slice | The smallest end-to-end implementation crossing the full outcome path, including integration and human interaction. | [Chapter 23](../Methodology/chapter-23-forward-deployed-outcome-engineering.md) |

## 2. Roles roster

Combines the pod-level roles ([Chapter 23](../Methodology/chapter-23-forward-deployed-outcome-engineering.md)), the enterprise roles ([Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md)), and the accountability requirements named across the Architecture perspective articles, into one lookup.

| Role | Level | Accountable for | Defined in full |
|---|---|---|---|
| Executive Sponsor | Enterprise | Strategic priority, funding, cross-functional resolution. | [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#role-model) |
| Business Outcome Owner | Enterprise | Outcome baseline, target, process authority, value realization — and, per [Process Architecture](../architecture/perspective-03-process-architecture.md#2-process-ownership-model), always a named human even when most process steps are agent-executed. | [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#role-model) |
| Product / Service Owner | Enterprise | Scope, release, service health, backlog, lifecycle. | [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#role-model) |
| FDOE Pod Lead | Pod | Integrated discovery, engineering, activation and learning for one pod. | [Chapter 23](../Methodology/chapter-23-forward-deployed-outcome-engineering.md); [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#role-model) |
| Platform Product Owner | Enterprise | Shared capability roadmap, service levels, adoption of platform components. | [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#role-model); [Chapter 25](../Methodology/chapter-25-enterprise-intelligence-platform.md) |
| Data / Knowledge Owner | Enterprise | Authority, quality, access, freshness, lineage for a knowledge domain. | [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#role-model); [Information and Knowledge Architecture §1](../architecture/perspective-04-information-and-knowledge-architecture.md#1-enterprise-knowledge-domain-map) |
| Model / AI Steward | Enterprise | Model strategy, provider risk, evaluation, version policy. | [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#role-model); [Inference Architecture](../architecture/perspective-05-inference-architecture.md) |
| Security / Privacy / Legal / RAI | Enterprise | Requirements, challenge, advice and acceptance within a bounded mandate. | [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#role-model) |
| Operations Owner | Enterprise | Runbook, support, incidents, capacity, change, recovery — and the pre-assigned kill-switch/containment authority. | [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#role-model); [Security checklist §4](../security/agentic-ai-threat-and-control-checklist.md#4-containment-and-emergency-control-checklist) |
| Independent Assurance | Enterprise | Objective challenge for high-impact evidence and controls; never held by the role that built the thing being assured. | [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#separation-and-consolidation) |
| Agent accountable owner | Per-agent | The named human accountable for a specific registered agent's actions, regardless of autonomy level. | [Agent Architecture §3](../architecture/perspective-02-agent-architecture.md#3-agent-registry) |
| Permission-issuance owner | Per-integration/credential | Approving, scoping and revoking a specific credential or agent permission scope. | [Security and Trust Architecture §3](../architecture/perspective-08-security-and-trust-architecture.md#3-enterprise-permission-issuance-principles) |
| Governance forum chair | Enterprise | Convening and running one of the six governance forums on its defined cadence. | [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#governance-forums) |

## 3. RACI quick reference

For the recurring, high-stakes decisions this methodology names most often, a compact default RACI — adapt to organizational context, but do not leave any of these decisions with no Accountable owner at all.

| Decision | Responsible | Accountable | Consulted | Informed |
|---|---|---|---|---|
| Approve a new agent's autonomy increase | FDOE Pod Lead | Business Outcome Owner | Security/Privacy/Legal/RAI, Independent Assurance | Executive Sponsor |
| Approve a production release | Platform Product Owner / Operations Owner | Business Outcome Owner | Model/AI Steward, Security/Privacy/Legal/RAI | Executive Sponsor |
| Invoke a kill switch / containment action | Operations Owner | Operations Owner | Security/Privacy/Legal/RAI | Executive Sponsor, Business Outcome Owner |
| Approve a model or provider change | Model / AI Steward | Model / AI Steward | Platform Product Owner, Security/Privacy/Legal/RAI | All affected system owners |
| Promote a component to shared platform status | Platform Product Owner | Platform Product Owner | Data/Knowledge Owner, all consuming system owners | Executive Sponsor |
| Retire or reframe an underperforming initiative | Business Outcome Owner | Executive Sponsor | Product/Service Owner, FDOE Pod Lead | Portfolio review forum |

---

[← Back to Contents](../README.md) · [Chapter 33: Appendices and Reference Material](../Methodology/chapter-33-appendices-and-reference-material.md) · [Chapter 24: Roles, Teams and Governance Forums](../Methodology/chapter-24-roles-teams-and-governance-forums.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
