<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 16: Human–AI Workflow and Experience Engineering](chapter-16-human-ai-workflow-and-experience-engineering.md) · [Contents](../README.md) · [Next: Chapter 18: Evaluation and Reliability Engineering →](chapter-18-evaluation-and-reliability-engineering.md)

# Chapter 17: Enterprise Integration and Tool Engineering

# Enterprise Integration and Tool Engineering

> **CHAPTER PURPOSE** Connect intelligence safely to enterprise applications, APIs and transactions through well-designed tools, contracts, identity and recovery.

## Background and context

Chapter 16 decides who has authority over a piece of work and how a human and an AI hand it back and forth. Chapter 17 is where that authority actually meets the enterprise's systems of record — where a recommendation becomes a booked appointment, a drafted email becomes a sent one, a proposed refund becomes a transaction that moves money. That is a materially different kind of risk than generating a plausible-sounding response, and it is why this chapter exists as a discipline distinct from the model and context work in Chapter 14: a wrong answer is a quality problem; a wrong action taken against a live system of record is an operational and often financial one, and it may not be reversible.

The framing OASIS uses throughout this chapter is that every point of contact between the intelligence system and an enterprise application is a **tool** — a deliberately governed interface, not a raw technical connection reused as-is. That distinction has become industry practice only recently. Through 2023 and into 2024, most agent frameworks defined tool-calling their own incompatible way, so a tool built for one framework had to be redefined for every other one it needed to run in. Anthropic's Model Context Protocol (MCP), released in November 2024, standardized how a model-facing application discovers and calls external tools, resources and prompts over a common interface, and by 2025 it had been adopted widely enough across model providers and agent frameworks to become the closest thing the industry has to a common tool-integration standard. This chapter's principles are protocol-agnostic on purpose — a tool contract is what a tool *is*; MCP is one way, not the only way, to expose one — but where an engagement does use a standardized protocol, the section on tool catalogues below assumes it as the default.

The [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md) is this chapter's direct implementation-level companion: it turns the tool-contract table below into a complete, fillable YAML specification, plus a worked example built from this chapter's own illustrative booking tool. Build teams should treat that specification, not this chapter, as the document they complete field-by-field for every tool before it is registered in the harness. Where this chapter designs a single tool's contract, the [Integration Architecture](../architecture/perspective-06-integration-architecture.md) perspective takes the portfolio view — how many independent integrations the enterprise already has into the same system of record, built by how many teams, under how many separately-configured credentials — and is the place to look once the question shifts from "is this one tool contract sound" to "how much surface area does the enterprise have exposed across all of them." And because a tool is also the most direct path an adversary has into a system capable of acting, the [Security: Agentic AI Threat and Control Checklist](../security/agentic-ai-threat-and-control-checklist.md) maps this chapter's tool-layer controls to OWASP's ASI02 (Tool Misuse & Exploitation) and LLM06 (Excessive Agency) categories, and is worth reading alongside this chapter rather than after it.

## Integration principles

Good tool design starts by resisting the natural urge to expose whatever API already exists. A tool should expose the narrowest business capability actually required — "book an eligible service slot," not "write access to the scheduling database" — because a narrow surface is both easier for a model to select correctly and dramatically smaller as an attack or error surface if something does go wrong. That same discipline carries into permissions: read, prepare and execute are different levels of consequence and should be separated as different permissions, not folded into one broad grant, and anything with a material side effect — sending money, committing a customer, changing a legal record — should require an explicit confirmation step rather than proceeding on the system's own initiative.

Authorization itself has to be bound tighter than a typical service-to-service integration allows. It is not enough to authorize the calling agent; a tool call has to be authorized against the requesting user, the business context, the specific case, and the transaction itself, because an agent acting with its own blanket identity — rather than the authority actually held by the person or process on whose behalf it is acting — is exactly the excessive-agency failure mode that shows up repeatedly in agentic-AI incident reports. Inputs and outputs both need deterministic validation at the tool and workflow boundary — not "the model was instructed to only send valid data," but a hard check that runs regardless of what the model intended.

The remaining principles are the same operational discipline that any production integration needs, just applied with more rigor because the caller is non-deterministic: design idempotency so a retried call cannot double-book or double-charge, set sensible timeouts and retry policies, define what a partial failure looks like and how it is recovered, decide what a compensating action is for anything reversible, and reconcile state with the system of record rather than assuming the tool call and the downstream system never drift apart. And every call should leave a record — intent, parameters, result, the authority under which it ran, any approval given, and the downstream identifier it produced — because that record is what makes an incident investigable after the fact rather than a matter of guesswork.

## Tool contract

A tool contract is the artifact that makes all of the principles above concrete for one specific tool. The table below is this chapter's minimum contract; the [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md#1-tool-contract-template) expands every one of these fields into a complete YAML template — including fields this summary implies but does not spell out, such as idempotency key strategy, typed failure semantics, and schema versioning — and walks through a full worked example using the same booking tool below.

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

Two fields reward extra care during design. Preconditions are what stop a tool from being called correctly but inappropriately — a syntactically valid request that arrives before identity has actually been verified should fail the precondition check even though every input is well-formed. And failure semantics are what determine whether a bad outcome stays contained: a typed error that preserves state and offers a safe alternative turns a failed booking into a recoverable moment; an untyped exception that leaves the system unsure whether the appointment was created or not turns the same failure into a reconciliation problem days later.

## Integration patterns

OASIS recognizes five integration patterns, and the right one for a given tool follows from the transaction's criticality, latency tolerance, legacy constraints and recovery needs rather than from what happens to be easiest to stand up first: synchronous APIs for in-flow decisions the workflow waits on, event-driven workflows for multi-step processes that outlive a single interaction, queues for high-volume decoupled processing, managed connectors for standard enterprise systems with a supported integration layer, and robotic process automation for bridging a legacy system that has no API at all. The [Integration Architecture](../architecture/perspective-06-integration-architecture.md) perspective's pattern-selection guidance (drawing on the [Tool specification's pattern table](../engineering/tool-and-integration-interface-specification.md#3-integration-pattern-selection)) is the place to work through that choice tool by tool.

RPA is worth calling out specifically because it is the pattern most often reached for by default and least often examined afterward. It may be an acceptable bridge for a bounded legacy system, but it should never be used to hide a brittle operation from the service owner — an RPA-backed tool contract needs the same failure semantics, limits and audit trail as any other tool, and it should name a migration owner and a target replacement pattern from the day it is built, not once it has quietly become permanent infrastructure five years later.

## MCP and tool catalogues

Where standardized tool protocols are used, the tool catalogue is not a passive inventory — it is where ownership, provenance, authentication, permission scopes, schema versions, test coverage and revocation get recorded for every tool the system can call, and it is the place an incident responder goes first when the question is "what can this agent actually reach, and how do we cut it off." A tool description is part of the system's behavior, not documentation about the system's behavior: an agent selects and argues a tool call based on how that tool is described to it, so a change to a tool's description or schema needs the same versioning, regression testing and review as a change to code, exactly as the [Tool specification's registration fields](../engineering/tool-and-integration-interface-specification.md#4-mcp-tool-catalogue-registration-fields) require. Treat an unreviewed edit to a tool description as a change to system behavior — because that is precisely what it is.

---

[← Previous: Chapter 16: Human–AI Workflow and Experience Engineering](chapter-16-human-ai-workflow-and-experience-engineering.md) · [Contents](../README.md) · [Next: Chapter 18: Evaluation and Reliability Engineering →](chapter-18-evaluation-and-reliability-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
