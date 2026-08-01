<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 30: Tailoring OASIS](chapter-30-tailoring-oasis.md) · [Contents](README.md) · [Next: Chapter 32: Templates, Checklists and Tools →](chapter-32-templates-checklists-and-tools.md)

# Chapter 31: Illustrative Use Cases

# Illustrative Use Cases

> **CHAPTER PURPOSE** Show how the method changes across service, operations, knowledge, contracts, sentiment, maintenance, procurement and employee productivity.

## Use-case patterns

| **Use case**                           | **Outcome contract**                                                    | **System emphasis**                                                                            | **Critical failures**                                           |
|----------------------------------------|-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| Customer-service appointment agent     | Completed eligible appointment; reduced repeat calls and missed visits. | Intent, policy, CRM/field-service tools, voice/channel, identity, confirmation and escalation. | Incorrect booking, ineligible service, privacy, poor hand-off.  |
| Order-booking intelligence system      | First-time-right booking and shorter cycle time.                        | Document/email ingestion, field extraction, mapping, validation, ERP transaction and review.   | Wrong values, duplicate order, unsupported mapping, audit gap.  |
| Contract analysis and review           | Faster review with accepted risk position.                              | Clause retrieval, playbook, structured issues, deterministic redlining and legal approval.     | Invented clause, jurisdiction error, unauthorized change.       |
| Sentiment and next-best action         | Earlier issue detection and better closed-loop recovery.                | Multi-channel ingestion, identity, taxonomy, trend analysis, recommendation and CRM action.    | Bias, misclassification, surveillance, unverified identity.     |
| Predictive maintenance / field service | Reduced downtime and improved first-time fix.                           | Telemetry, prediction, manuals, parts/tools, technician workflow and work order.               | Unsafe recommendation, sensor drift, false negative.            |
| Enterprise knowledge assistant         | Faster authorized answers with lower search effort.                     | Access-filtered retrieval, citations, abstention, freshness and feedback.                      | Data leakage, stale policy, false confidence.                   |
| Procurement and supplier intelligence  | Better cycle time, compliance and supplier risk visibility.             | Sourcing data, contracts, policy, external information, approvals and ERP.                     | Unfair scoring, unsupported external data, authority conflict.  |
| Employee productivity agent            | Reduced task time with maintained quality.                              | User context, documents, email/calendar/tools, privacy and personal control.                   | Oversharing, accidental actions, unmeasured productivity shift. |

## Cross-business reusable patterns

- Identity resolution and authorization-aware customer or employee context

- Document ingestion, structured extraction and source citation

- Enterprise search and knowledge retrieval

- Approval, exception and escalation workflow

- Action confirmation, idempotency and transaction reconciliation

- Evaluation harness, failure taxonomy and outcome telemetry

- Voice transcription, call summarization and hand-off

- Agent trace, audit, incident and cost measurement

## Example outcome contract

| **Field**          | **Appointment-agent example**                                                                  |
|--------------------|------------------------------------------------------------------------------------------------|
| Population         | Eligible installation and service calls in defined product and geography.                      |
| Primary outcome    | Percentage of calls ending in a valid confirmed appointment without agent transfer.            |
| Baseline / target  | Measured current baseline; target set after representative validation.                         |
| Leading indicators | Intent resolution, slot availability, confirmation and hand-off quality.                       |
| Guardrails         | Incorrect bookings, complaints, repeat calls, privacy incidents and service-policy violations. |
| Authority          | May propose and book within policy; exceptions transfer to human.                              |
| Measurement        | Call-centre, CRM and field-service records reconciled by booking ID.                           |
| Review             | Weekly during pilot; monthly after stable operation.                                           |

---

[← Previous: Chapter 30: Tailoring OASIS](chapter-30-tailoring-oasis.md) · [Contents](README.md) · [Next: Chapter 32: Templates, Checklists and Tools →](chapter-32-templates-checklists-and-tools.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](LICENSE.md).
