<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: Context and Retrieval Engineering](context-and-retrieval-engineering.md) · [Chapter 17: Enterprise Integration and Tool Engineering](../methodology/chapter-17-enterprise-integration-and-tool-engineering.md) · [Architecture: Reference Architecture](../architecture/oasis-reference-architecture.md) · [Next: Harness and Orchestration Engineering →](harness-and-orchestration-engineering.md)

# Engineering: Tool and Integration Interface Specification

> **PURPOSE** Turn Chapter 17's tool-contract table and integration principles into a fillable interface specification a build team can use directly, plus a worked example. This is the implementation-level companion to the [Tool Catalogue and Action Contracts](../methodology/chapter-14-intelligence-and-agent-engineering.md#engineering-artifact-set) artifact named in Chapter 14.

**Primary OASIS source:** [Chapter 17 — Enterprise Integration and Tool Engineering](../methodology/chapter-17-enterprise-integration-and-tool-engineering.md); [Chapter 14 §5–6 — Tool and Agent-Harness Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md); [Chapter 19 — Tool layer controls](../methodology/chapter-19-security-and-responsible-ai-engineering.md).

## Background and context

Chapter 17 treats every point where an intelligence system touches an enterprise application, API or transaction as a **tool** — a governed interface, not a raw technical connection. That framing matters because the industry's own tooling has converged on the same idea only recently. Through 2023–2024, most agent frameworks each defined tool-calling in their own incompatible way, which meant a tool built for one framework or model provider had to be redefined for every other one. Anthropic's **Model Context Protocol (MCP)**, released in November 2024, standardized how a model-facing application discovers and calls external tools, resources and prompts over a common interface; by 2025 it had been adopted across the major model providers and agent frameworks and become the closest thing the industry has to a common tool-integration standard — which is why Chapter 17 and this specification treat "standardized tool protocols... e.g. MCP" as the default assumption for how a tool catalogue is exposed, while keeping the underlying tool-contract discipline protocol-agnostic (a tool contract, as defined below, is what a tool *is*; MCP is one way, not the only way, a system can *expose* one).

That tool-contract discipline is itself borrowed from a much older engineering practice — API design — but tightened for the specific risk profile of a model choosing, rather than a human developer hard-coding, which tool to call and with what arguments. A conventional internal API can rely on a developer having read the documentation before wiring up a call; a tool exposed to a model must be narrow and unambiguous enough that the model selects it correctly at runtime, and must assume the caller's "judgment" can be manipulated by adversarial input (see the [Security checklist's](../security/agentic-ai-threat-and-control-checklist.md) coverage of OWASP ASI02 Tool Misuse & Exploitation and LLM06 Excessive Agency). That is why the contract fields below go well beyond a typical OpenAPI schema — authorization is bound to the requesting user and business context rather than just the calling service (Chapter 17's integration principles), and every tool must define confirmation, idempotency, and failure semantics explicitly rather than leaving them to convention.

**How to use this specification:** complete one tool contract (Section 1) per tool before it is registered in the harness, using the worked example in Section 2 as a template. Use Section 3 to choose and justify the integration pattern per tool, and Section 4 to register the tool in whatever catalogue mechanism (MCP or otherwise) the engagement uses. Cross-reference the [Security checklist](../security/agentic-ai-threat-and-control-checklist.md) for the threat model each contract field is designed to close, and the [Risk and Control Register](../tools/05-risk-and-scale-templates.md#17-risk-and-control-register) for tracking any residual risk a specific tool's authority represents.

## 1. Tool contract template

Every tool the system can call must have a completed contract before it is registered in the harness. Fields follow Chapter 17's tool-contract table, expanded to interface-specification level.

```yaml
tool:
  name: ""                       # unique, versioned identifier, e.g. booking.create_appointment.v1
  owner: ""                      # accountable system/business owner (Ch.20 RACI)
  purpose: ""                    # one sentence, narrowest business capability required (not a raw technical API)
  category: read | prepare | execute   # Ch.17: separate read, prepare and execute permissions

  inputs:
    - name: ""
      type: ""
      required: true|false
      source: "user | context | upstream-tool"
      validation: ""            # deterministic validation rule at the boundary

  preconditions: []              # e.g. identity verified; entitlement satisfied; prior step completed

  outputs:
    - name: ""
      type: ""
      description: ""

  side_effects:
    creates_or_changes: ""       # what state changes in the system of record
    reversible: true|false
    compensating_action: ""      # if reversible, how to undo

  authorization:
    authorize_against: "requesting user + business context + case + transaction"  # Ch.17: not agent identity alone
    required_scopes: []
    data_classification: ""

  limits:
    transaction_value_max: ""
    date_or_time_horizon: ""
    retry_count_max: ""
    rate_limit: ""

  confirmation:
    required_before: ""          # e.g. "customer commitment or charge"
    confirmation_method: ""      # e.g. explicit user approval step, dual control

  idempotency:
    key_strategy: ""
    duplicate_call_behavior: ""

  timeout_and_retry:
    timeout_ms: ""
    retry_policy: ""
    partial_failure_handling: ""

  failure_semantics:
    error_type: "typed error, not free text"
    state_on_failure: "preserved | rolled back"
    fallback_offered: ""
    escalation_path: ""

  audit:
    logs: [requester, approver, parameters, result, timestamp, downstream_identifier]
    retention: ""

  versioning:
    schema_version: ""
    test_coverage: ""
    deprecation_policy: ""
```

## 2. Worked example — Chapter 17's illustrative tool

Chapter 17 illustrates the contract with a service-booking tool. Filled out at interface-specification level:

```yaml
tool:
  name: booking.create_appointment.v1
  owner: Field Service Operations (outcome owner: VP Field Service)
  purpose: "Book an eligible service slot for a verified customer and product."
  category: execute

  inputs:
    - name: customer_id
      type: string
      required: true
      source: context
      validation: "must resolve to a verified customer record"
    - name: asset_id
      type: string
      required: true
      source: context
      validation: "must be an active, entitled asset"
    - name: service_type
      type: enum
      required: true
      source: user
      validation: "must be in eligible-service-type list"
    - name: geography
      type: string
      required: true
      source: context
    - name: time_preference
      type: datetime-range
      required: false
      source: user

  preconditions:
    - "Identity verified"
    - "Entitlement and service policy satisfied"

  outputs:
    - name: booking_id
      type: string
      description: "Unique identifier for the created appointment"
    - name: selected_slot
      type: datetime
      description: "Confirmed appointment slot"
    - name: technician_or_route_reference
      type: string
      description: "Assigned resource reference"
    - name: customer_message
      type: string
      description: "Confirmation text for the customer"

  side_effects:
    creates_or_changes: "Creates an operational appointment record"
    reversible: true
    compensating_action: "booking.cancel_appointment.v1"

  authorization:
    authorize_against: "requesting user + verified customer + asset entitlement + transaction"
    required_scopes: ["booking:write"]
    data_classification: "customer PII, service records"

  limits:
    transaction_value_max: "n/a (non-monetary transaction)"
    date_or_time_horizon: "eligible service types, within 90 days"
    retry_count_max: 2
    rate_limit: "per-customer and per-agent-session limits apply"

  confirmation:
    required_before: "customer commitment"
    confirmation_method: "explicit user approval step before slot is finalized"

  idempotency:
    key_strategy: "customer_id + asset_id + requested_slot hash"
    duplicate_call_behavior: "return existing booking_id, no duplicate record"

  timeout_and_retry:
    timeout_ms: 8000
    retry_policy: "safe retry on timeout only; no retry on business rejection"
    partial_failure_handling: "no partial bookings; all-or-nothing create"

  failure_semantics:
    error_type: "typed error (e.g. SLOT_UNAVAILABLE, ENTITLEMENT_DENIED, SYSTEM_TIMEOUT)"
    state_on_failure: "preserved — no appointment created"
    fallback_offered: "alternate available slots"
    escalation_path: "route to human scheduler on repeated failure"

  audit:
    logs: [requester, approver, parameters, result, timestamp, downstream_identifier]
    retention: "per data retention schedule, see references/regulatory-framework-alignment-index.md"

  versioning:
    schema_version: "1.0"
    test_coverage: "unit + integration + regression suite, evaluated like code (Ch.17)"
    deprecation_policy: "90-day notice, dual-run period"
```

## 3. Integration pattern selection

Chapter 17 identifies five integration patterns. Use this table to select and justify the choice per tool:

| Pattern | Best fit when | Latency profile | Recovery approach |
|---|---|---|---|
| Synchronous API | Low-latency, in-flow decisions where the workflow waits on the result. | Milliseconds–seconds | Retry with timeout, typed error |
| Event-driven workflow | Multi-step processes that outlive a single interaction. | Seconds–hours | Event replay, dead-letter queue |
| Queue-based | High-volume, decoupled processing where immediate response is not required. | Seconds–minutes | Requeue, poison-message handling |
| Managed connector | Standard enterprise system (CRM, ERP) with a supported integration layer. | Vendor-dependent | Vendor-native retry/rollback |
| Robotic automation (RPA) | Bounded legacy-system bridge with no API. | Seconds–minutes | Must not hide brittle operations from the service owner — treat as a tool contract like any other, with its own failure semantics |

RPA is an acceptable bridge, not a permanent architecture. Every RPA-backed tool contract must name a migration owner and target replacement pattern.

## 4. MCP / tool catalogue registration fields

Where a standardized tool protocol (e.g., MCP) is used, register each tool with:

| Field | Description |
|---|---|
| Provenance | Who built/maintains this tool definition, and from what source |
| Authentication | Mechanism and credential scope |
| Permission scopes | Exact scopes granted, mapped to the authorization field above |
| Schema version | Versioned like code; breaking changes require a new version, not a silent edit |
| Test coverage | Link to the test suite covering this tool's contract |
| Revocation | How and by whom this tool's access can be revoked immediately |

A tool description is part of system behavior. Treat a change to a tool's description or schema as a release requiring the same regression and security testing as a code change (Chapter 21, version and release management).

---

[← Back to Contents](../README.md) · [← Previous: Context and Retrieval Engineering](context-and-retrieval-engineering.md) · [Chapter 17: Enterprise Integration and Tool Engineering](../methodology/chapter-17-enterprise-integration-and-tool-engineering.md) · [Architecture: Reference Architecture](../architecture/oasis-reference-architecture.md) · [Next: Harness and Orchestration Engineering →](harness-and-orchestration-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
