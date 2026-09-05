<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 30: Tailoring OASIS](chapter-30-tailoring-oasis.md) · [Contents](../README.md) · [Next: Chapter 32: Templates, Checklists and Tools →](chapter-32-templates-checklists-and-tools.md)

# Chapter 31: Illustrative Use Cases


> **CHAPTER PURPOSE** Show how the method changes across service, operations, knowledge, contracts, sentiment, maintenance, procurement and employee productivity use cases, and how the same underlying patterns recur across all of them.

## Background and context

The preceding thirty chapters describe OASIS as a method: phases, gates, artifacts, disciplines, governance. None of that shows what the method feels like on a live engagement. This chapter closes that gap.

It walks through eight use cases: customer service, back-office operations, knowledge work, legal review, sentiment and experience management, field maintenance, procurement, and individual productivity. Each shows how the six-phase lifecycle and the disciplines from Part III land differently depending on what the system does and who it touches.

Chapter 30 showed that OASIS scales its depth to risk, autonomy, exposure, and maturity. This chapter shows what that looks like in practice. A voice-based appointment agent and a contract-review assistant both use OASIS but stress different parts of it. The appointment agent lives or dies on identity resolution, channel handling, and hand-off quality. The contract reviewer lives or dies on clause retrieval fidelity, playbook discipline, and legal sign-off.

The use cases below are illustrative, not exhaustive. They cover the spread of agent types and deployment shapes described in [Architecture: Agent Architecture](../architecture/perspective-02-agent-architecture.md) and [Architecture: Process Architecture](../architecture/perspective-03-process-architecture.md): conversational agents, extraction-and-transaction agents, retrieval-and-advisory agents, and monitoring-and-recommendation agents. A reader building something not on this list can still find the nearest analog and borrow its pattern. Each row of the comparison table and each reusable pattern below maps back to specific chapters and to the fillable templates in [Chapter 32](chapter-32-templates-checklists-and-tools.md) and [Tools](../tools/01-outcome-and-portfolio-templates.md); use those links rather than treating this chapter as self-contained.

## Use-case patterns

Eight patterns recur often enough to walk through individually. Each is described by its outcome contract, its system emphasis, and its critical failure modes; the same three lenses an [Opportunity Assessment](chapter-32-templates-checklists-and-tools.md#1-opportunity-assessment) and [Value and Risk Case](chapter-32-templates-checklists-and-tools.md#5-value-and-risk-case) apply to a real candidate.

The **customer-service appointment agent** completes an eligible appointment and reduces repeat calls and missed visits. It is a narrow, transactional outcome, but higher-stakes than most conversational patterns because it commits the business to a real-world action. Its emphasis: intent recognition, policy application, live CRM and field-service integration, voice and chat channels, identity verification, and a confirmation-and-escalation path a human can step into cleanly.

Critical failures: an incorrect booking, a service promised to an ineligible customer, a privacy lapse during identity verification, or a hand-off that loses context. This pattern sits close to the [Human–AI Workflow Blueprint](chapter-32-templates-checklists-and-tools.md#7-human-ai-workflow-blueprint) and [Chapter 16; Human–AI Workflow and Experience Engineering](chapter-16-human-ai-workflow-and-experience-engineering.md).

The **order-booking intelligence system** targets first-time-right booking accuracy and a shorter order-to-fulfillment cycle. Its architecture centers on document and email ingestion, field extraction, mapping extracted values onto ERP transaction schemas, validation against business rules, and a review step before posting.

Because it writes directly into financial and operational systems of record, its failures are unforgiving: a wrong value silently accepted, a duplicate order from missed deduplication, an extraction mapped to a field the source never supported, or a gap in the audit trail. This is a [Data and Knowledge Readiness Assessment](chapter-32-templates-checklists-and-tools.md#8-data-and-knowledge-readiness-assessment) and [Evaluation Strategy and Dataset](chapter-32-templates-checklists-and-tools.md#9-evaluation-strategy-and-dataset) problem before it is a modeling problem. Extraction quality is bounded by source-document quality and by how well the evaluation set represents the real distribution of incoming documents.

The **contract analysis and review** pattern aims for faster review cycles that still hold an acceptable risk position. Its emphasis: clause retrieval against a governed corpus, a negotiation playbook, structured issue-spotting output, and deterministic (not generative) redlining constrained to pre-approved language, with legal approval as final authority. Failure modes: an invented clause not in the source contract, a jurisdictional error, or an unauthorized change slipping into redlined text unreviewed. This illustrates why [Chapter 14's workflow-pattern decision rule](chapter-14-intelligence-and-agent-engineering.md) matters; retrieval-and-extraction plus deterministic redlining is defensible where an open-ended generative rewrite would not be.

The **sentiment and next-best-action** pattern targets earlier issue detection and better closed-loop recovery; catching a deteriorating customer relationship before it becomes a churn event or complaint. It draws on multi-channel ingestion (calls, chat, surveys, social), identity resolution, a sentiment and issue taxonomy, trend analysis, and a recommendation surfaced into a CRM action a human executes.

Because it classifies people, its failure modes carry ethical weight: biased classification, misclassification that misroutes a customer, a design that edges into surveillance, or acting on an unverified identity match. Read this alongside [Chapter 19; Security and Responsible AI Engineering](chapter-19-security-and-responsible-ai-engineering.md) and its fairness and bias-testing guidance. The [Autonomy Matrix](chapter-32-templates-checklists-and-tools.md#12-autonomy-matrix) should keep any customer-facing action at a supervised or assisted level until evidence justifies more.

**Predictive maintenance and field service** reduces unplanned downtime and improves first-time fix rates. It combines telemetry ingestion, a prediction or anomaly-detection layer, retrieval against equipment manuals and service history, parts and tooling availability data, and integration into the technician's workflow and work-order system. It fails quietly if accurate in the lab but never reaches the technician at the point of decision.

Critical failures are physical-world ones: an unsafe recommendation, sensor drift degrading prediction quality unnoticed, or a false negative that misses a failure the system was built to catch. This connects to [Architecture: Deployment Architecture](../architecture/perspective-07-deployment-architecture.md), where edge and connectivity constraints shape what telemetry can reach the system in time.

The **enterprise knowledge assistant** delivers faster, authorized answers with lower search effort. It is likely the most common first intelligence system an enterprise builds, and one of the easiest to get wrong invisibly. Its emphasis: access-filtered retrieval (a user should never see an answer built from a document they cannot read), citation of sources, willingness to abstain rather than guess, index freshness, and a feedback loop for wrong or stale answers.

Its failure modes; data leakage across access boundaries, stale policy presented as current, false confidence in an unsupported answer; are exactly what [Chapter 18; Evaluation and Reliability Engineering](chapter-18-evaluation-and-reliability-engineering.md) means by groundedness and calibration. Access control is a retrieval-time concern, not a downstream filter.

**Procurement and supplier intelligence** pursues better cycle time, compliance, and supplier-risk visibility. It draws together sourcing data, contract terms, policy constraints, external supplier-risk information, an approval workflow, and ERP integration. Failure modes: unfair or opaque supplier scoring, unsupported external data treated as fact, and authority conflicts between the system's recommendation and an existing delegation-of-authority policy. This is a natural candidate for the [Risk and Control Register](chapter-32-templates-checklists-and-tools.md#17-risk-and-control-register), given how directly it touches financial commitment and vendor relationships.

The **employee productivity agent**; drafting, summarizing, scheduling, and retrieving across a knowledge worker's own documents, email, and calendar; reduces task time while holding quality steady. Its emphasis is almost entirely about respecting boundaries: correctly handled user context, tightly scoped document and communication access, and keeping the employee in control of what the agent can see and do on their behalf.

Its failures follow: oversharing across a boundary the user did not intend to cross, an accidental action taken without explicit confirmation, or a productivity claim nobody measured. Organizations often attempt this pattern first because it looks low-risk; which is exactly why these failure modes matter: "low-risk" is not "no governance," the distinction Chapter 30's tailoring equation makes explicit.

Read this table as a set of design choices, not a catalogue of AI demos. The outcome column states what must improve. The system-emphasis column identifies where engineering effort belongs. The final column names the failures that should shape evaluation and escalation. Teams usually underestimate that last column. A use case should not advance until those failures have representative test data, an accountable owner, and a tested fallback.

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

Read the eight use cases side by side and a shorter list of recurring building blocks emerges; components worth engineering once and reusing rather than rebuilding per project.

Identity resolution and authorization-aware context construction appears in the appointment agent, the sentiment pattern, and the knowledge assistant: whenever a system needs to know who it is dealing with and what they are entitled to see, the same logic applies. Document ingestion, structured extraction, and source citation form the backbone of the order-booking, contract-review, and knowledge-assistant patterns; different documents, different downstream use, but the same extraction-and-attribution discipline.

Enterprise search and knowledge retrieval underpins the knowledge assistant, the contract reviewer's clause lookup, and the maintenance technician's manual lookup. Built well once, retrieval quality is an asset the rest of the portfolio can draw on rather than rebuild per system. Approval, exception, and escalation workflow recurs everywhere a human must remain the final authority on a consequential decision, from procurement sign-off to a customer-service transfer. Action confirmation, idempotency, and transaction reconciliation matter anywhere a system writes to a system of record; order booking and procurement most obviously, but any pattern that books, cancels, or modifies something real needs the same discipline against duplicate or lost transactions.

An evaluation harness, a failure taxonomy, and outcome telemetry are not use-case-specific at all; every pattern above needs them, and [Chapter 18](chapter-18-evaluation-and-reliability-engineering.md) and the [Failure Taxonomy](chapter-32-templates-checklists-and-tools.md#10-failure-taxonomy) template are written to be reused verbatim across all eight. Voice transcription, call summarization, and hand-off logic serve the appointment agent and the sentiment pattern together. Agent trace, audit, incident, and cost measurement; the instrumentation described in [Chapter 21](chapter-21-deployment-operations-and-agentops.md) and the [Monitoring: Observability and Telemetry Specification](../monitoring/observability-and-telemetry-specification.md); lets an enterprise running many of these systems see what is happening across the portfolio, not just per project.

Recognizing these as reusable components rather than accidental similarities is itself a scaling decision. It connects to [Chapter 28; Scaling and Productization](chapter-28-scaling-and-productization.md) and the [Scale and Productization Assessment](chapter-32-templates-checklists-and-tools.md#18-scale-and-productization-assessment) template: a component built once for one pattern's identity resolution and reused for another's is a candidate for platform investment, not a coincidence to shrug off.

## Example outcome contract

The table below shows a worked outcome contract for the appointment-agent pattern, at the level of detail a real engagement would carry into a [Phase 1: Engage & Align](chapter-07-phase-1-engage-and-align.md) kickoff. It is deliberately concrete rather than templated, so a reader comparing it against the blank [Outcome Contract](chapter-32-templates-checklists-and-tools.md#3-outcome-contract) template in [Tools: Outcome and Portfolio Templates](../tools/01-outcome-and-portfolio-templates.md) can see what a filled field looks like versus a placeholder.

| **Field**          | **Appointment-agent example**                                                                  |
|--------------------|-----------------------------------------------------------------------------------------------|
| Population         | Eligible installation and service calls in defined product and geography.                      |
| Primary outcome    | Percentage of calls ending in a valid confirmed appointment without agent transfer.            |
| Baseline / target  | Measured current baseline; target set after representative validation.                         |
| Leading indicators | Intent resolution, slot availability, confirmation and hand-off quality.                       |
| Guardrails         | Incorrect bookings, complaints, repeat calls, privacy incidents and service-policy violations. |
| Authority          | May propose and book within policy; exceptions transfer to human.                              |
| Measurement        | Call-centre, CRM and field-service records reconciled by booking ID.                           |
| Review             | Weekly during pilot; monthly after stable operation.                                           |

Each row maps onto a chapter or template already covered: population and primary outcome are [Outcome Charter](chapter-32-templates-checklists-and-tools.md#2-outcome-charter) fields; guardrails and authority anticipate the [Autonomy Matrix](chapter-32-templates-checklists-and-tools.md#12-autonomy-matrix); measurement and review cadence anticipate the [Outcome Scorecard](chapter-32-templates-checklists-and-tools.md#15-outcome-scorecard) and the review rhythm in [Chapter 27; Delivery Cadence and Management Practices](chapter-27-delivery-cadence-and-management-practices.md). The next chapter, [Chapter 32](chapter-32-templates-checklists-and-tools.md), turns each of these fields into a fillable artifact; read this contract as the "why it looks like this," and the next chapter as the "here is the blank form."

---

[← Previous: Chapter 30: Tailoring OASIS](chapter-30-tailoring-oasis.md) · [Contents](../README.md) · [Next: Chapter 32: Templates, Checklists and Tools →](chapter-32-templates-checklists-and-tools.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
