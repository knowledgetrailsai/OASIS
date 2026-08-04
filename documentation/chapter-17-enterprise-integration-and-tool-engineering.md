<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 16: Human–AI Workflow and Experience Engineering](chapter-16-human-ai-workflow-and-experience-engineering.md) · [Contents](../README.md) · [Next: Chapter 18: Evaluation and Reliability Engineering →](chapter-18-evaluation-and-reliability-engineering.md)

# Chapter 17: Enterprise Integration and Tool Engineering

# Enterprise Integration and Tool Engineering

> **CHAPTER PURPOSE** Connect intelligence safely to enterprise applications, APIs and transactions through well-designed tools, contracts, identity and recovery.

## Integration principles

- Expose the narrowest business capability required, not a broad technical API surface.

- Separate read, prepare and execute permissions; require explicit confirmation for material side effects.

- Authorize against the requesting user, business context, case and transaction—not only the agent identity.

- Validate inputs and outputs deterministically at tool and workflow boundaries.

- Design idempotency, timeouts, retries, partial failure, compensation and reconciliation.

- Record intent, parameters, result, authority, approval and downstream identifier.

## Tool contract

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

## Integration patterns

OASIS supports synchronous APIs, event-driven workflows, queues, managed connectors, robotic automation and human work queues. Selection follows transaction criticality, latency, legacy constraints and recovery needs. RPA may be acceptable for a bounded legacy bridge but should not hide brittle operations from the service owner.

## MCP and tool catalogues

Where standardized tool protocols are used, catalogue ownership, provenance, authentication, permission scopes, schema versions, test coverage and revocation. A tool description is part of system behavior and must be versioned and evaluated like code.

---

[← Previous: Chapter 16: Human–AI Workflow and Experience Engineering](chapter-16-human-ai-workflow-and-experience-engineering.md) · [Contents](../README.md) · [Next: Chapter 18: Evaluation and Reliability Engineering →](chapter-18-evaluation-and-reliability-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
