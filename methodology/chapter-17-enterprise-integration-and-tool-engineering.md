<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 16: Human–AI Workflow and Experience Engineering](chapter-16-human-ai-workflow-and-experience-engineering.md) · [Contents](../README.md) · [Next: Chapter 18: Evaluation and Reliability Engineering →](chapter-18-evaluation-and-reliability-engineering.md)

# Chapter 17: Enterprise Integration and Tool Engineering

> **Implementation companion:** [Helm](https://github.com/knowledgetrailsai/Helm) (`07-tool-integration/`) — light coverage; no dedicated deep companion yet. See the [Companion Repository Index](../references/companion-repository-index.md) for the known gap.


> **CHAPTER PURPOSE** Connect intelligence safely to enterprise applications, APIs and transactions through well-designed tools, contracts, identity and recovery.

## Background and context

Chapter 16 decides who has authority over a piece of work and how a human and an AI hand it back and forth. Chapter 17 is where that authority meets the enterprise's systems of record — where a recommendation becomes a booked appointment, or a proposed refund becomes money moving.

That is a different kind of risk than generating a plausible-sounding response. A wrong answer is a quality problem. A wrong action against a live system of record is operational and often financial, and may not be reversible.

OASIS treats every point of contact between the intelligence system and an enterprise application as a **tool** — a deliberately governed interface, not a raw technical connection reused as-is. That distinction became industry practice only recently: through 2023 and 2024, most agent frameworks defined tool-calling their own incompatible way.

Anthropic's Model Context Protocol (MCP), released November 2024, standardized how a model-facing application discovers and calls external tools, resources and prompts over a common interface, and by 2025 was the closest thing the industry has to a common tool-integration standard. This chapter's principles are protocol-agnostic: a tool contract is what a tool *is*, and MCP is one way to expose one, not the only way. Where an engagement uses a standardized protocol, the tool catalogues section below assumes it as default.

The [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md) is this chapter's implementation-level companion, turning the tool-contract table below into a fillable YAML specification with a worked example. Build teams should complete it field-by-field for every tool before registering it in the harness. Helm's [Tool Contracts & Integration Principles](https://github.com/knowledgetrailsai/Helm/blob/main/07-tool-integration/tool-contracts-and-integration-principles.md) covers the same ground for a system already in production, including where tool versioning belongs in the release manifest.

The [Integration Architecture](../architecture/perspective-06-integration-architecture.md) perspective takes the portfolio view instead — how many integrations the enterprise has into the same system of record, built by how many teams, under how many credentials. Use it once the question shifts from one tool contract to total exposed surface area. A tool is also the most direct path an adversary has into a system capable of acting, so the [Security: Agentic AI Threat and Control Checklist](../security/agentic-ai-threat-and-control-checklist.md) maps this chapter's tool-layer controls to OWASP's ASI02 (Tool Misuse & Exploitation) and LLM06 (Excessive Agency) categories.

## Integration principles

Good tool design resists the urge to expose whatever API already exists. A tool should expose the narrowest business capability required — "book an eligible service slot," not "write access to the scheduling database." A narrow surface is easier for a model to select correctly, and smaller as an attack or error surface.

Read, prepare and execute are different levels of consequence and should stay separate permissions, not one broad grant. Anything with a material side effect — sending money, committing a customer, changing a legal record — needs an explicit confirmation step. Helm's [Integration Principles](https://github.com/knowledgetrailsai/Helm/blob/main/07-tool-integration/tool-contracts-and-integration-principles.md#integration-principles) state this same narrow-surface rule for production tool design.

Authorization has to be bound tighter than a typical service-to-service integration allows. It is not enough to authorize the calling agent; a tool call must be authorized against the requesting user, the business context, the specific case and the transaction. An agent acting with its own blanket identity, rather than the authority held by whoever it acts for, is the excessive-agency failure mode seen repeatedly in agentic-AI incident reports. Inputs and outputs need deterministic validation at the tool and workflow boundary, regardless of what the model intended.

The remaining principles are ordinary production discipline, applied with more rigor because the caller is non-deterministic: design idempotency so a retry cannot double-book or double-charge; set sensible timeouts and retry policies; define partial-failure behavior and recovery; decide the compensating action for anything reversible; reconcile state with the system of record. Every call should leave a record — intent, parameters, result, authority, any approval, and the downstream identifier produced — so an incident is investigable, not guesswork.

## Tool contract

A tool contract makes the principles above concrete for one tool. The table below is this chapter's minimum contract; the [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md#1-tool-contract-template) expands every field into a full YAML template — including idempotency key strategy, typed failure semantics and schema versioning — with a worked example. Helm's [Tool Contract](https://github.com/knowledgetrailsai/Helm/blob/main/07-tool-integration/tool-contracts-and-integration-principles.md#the-tool-contract) walks the same fields for a tool already running in production.

| **Contract field** | **Example content**                                                                  |
|--------------------|--------------------------------------------------------------------------------------|
| Purpose            | Book an eligible service slot for a verified customer and product.                   |
| Inputs             | Customer, asset, service type, geography, time preference and authorization context. |
| Preconditions      | Identity verified; entitlement and service policy satisfied.                         |
| Output             | Booking ID, selected slot, technician/route reference and customer message.          |
| Side effect        | Creates or changes an operational appointment.                                       |
| Limits             | Eligible service types, date horizon, transaction value and retry count.             |
| Confirmation       | Required before customer commitment or charge.                                       |
| Failure            | Return typed error; preserve state; offer safe alternatives or escalation.           |
| Audit              | Who requested, who approved, parameters, result, timestamp and downstream record.    |

Two fields reward extra care. Preconditions stop a tool from being called correctly but inappropriately: a valid request arriving before identity is verified should still fail the check. Failure semantics determine whether a bad outcome stays contained. A typed error that preserves state and offers a safe alternative turns a failed booking into a recoverable moment; an untyped exception turns it into a reconciliation problem days later.

## Integration patterns

OASIS recognizes five integration patterns. The right one follows from the transaction's criticality, latency tolerance, legacy constraints and recovery needs — not from what is easiest to stand up: synchronous APIs for in-flow decisions the workflow waits on, event-driven workflows for multi-step processes, queues for high-volume decoupled processing, managed connectors for standard enterprise systems, and robotic process automation for legacy systems with no API.

The [Integration Architecture](../architecture/perspective-06-integration-architecture.md) perspective's pattern-selection guidance, drawing on the [Tool specification's pattern table](../engineering/tool-and-integration-interface-specification.md#3-integration-pattern-selection), works through that choice tool by tool. Helm's [Integration Patterns & Tool Catalogues](https://github.com/knowledgetrailsai/Helm/blob/main/07-tool-integration/integration-patterns-and-tool-catalogues.md#five-integration-patterns) lays out the same five patterns from a running system's perspective.

RPA deserves a specific call-out, as Helm's [RPA section](https://github.com/knowledgetrailsai/Helm/blob/main/07-tool-integration/integration-patterns-and-tool-catalogues.md#rpa-deserves-a-specific-call-out) stresses: it is reached for by default and examined least often afterward. It may be an acceptable bridge for a bounded legacy system, but it should never hide a brittle operation from the service owner.

An RPA-backed tool contract needs the same failure semantics, limits and audit trail as any other tool, and should name a migration owner and target replacement pattern from day one — not once it quietly becomes permanent infrastructure.

## MCP and tool catalogues

Where standardized tool protocols are used, the tool catalogue is not a passive inventory, per Helm's [MCP and Tool Catalogues](https://github.com/knowledgetrailsai/Helm/blob/main/07-tool-integration/integration-patterns-and-tool-catalogues.md#mcp-and-tool-catalogues-are-not-a-passive-inventory). It records ownership, provenance, authentication, permission scopes, schema versions, test coverage and revocation for every tool the system can call — the place an incident responder goes first to ask what an agent can reach and how to cut it off.

A tool description is part of the system's behavior, not documentation about it: an agent selects and argues a tool call based on how the tool is described. A change to a description or schema needs the same versioning and review as a code change, per the [Tool specification's registration fields](../engineering/tool-and-integration-interface-specification.md#4-mcp-tool-catalogue-registration-fields).

---

[← Previous: Chapter 16: Human–AI Workflow and Experience Engineering](chapter-16-human-ai-workflow-and-experience-engineering.md) · [Contents](../README.md) · [Next: Chapter 18: Evaluation and Reliability Engineering →](chapter-18-evaluation-and-reliability-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
