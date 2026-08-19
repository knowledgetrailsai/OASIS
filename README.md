<!-- SPDX-License-Identifier: MIT -->

# OASIS Methodology Handbook

**Outcome-as-a-Service using Intelligence Systems**

This is a deliberately simple, Markdown-only GitHub package. All handbook pages are stored in this single folder and linked using relative Markdown links. Open this `README.md` file to navigate the handbook. See [CHANGELOG.md](CHANGELOG.md) for what's changed and when, including the review cadence expected for the Standards and References material.

## Handbook contents

- [Handbook Introduction](00-handbook-introduction.md)

### [Part I: Transformation Foundations](Methodology/part-i-transformation-foundations.md)

- [Chapter 01: OASIS Executive Overview](Methodology/chapter-01-oasis-executive-overview.md)
- [Chapter 02: Methodology Foundations and Design Principles](Methodology/chapter-02-methodology-foundations-and-design-principles.md)
- [Chapter 03: Enterprise AI Transformation Direction](Methodology/chapter-03-enterprise-ai-transformation-direction.md)
- [Chapter 04: Multiple Entry Paths and Configurable Depth](Methodology/chapter-04-multiple-entry-paths-and-configurable-depth.md)
- [Chapter 05: Opportunity Portfolio and Transformation Horizons](Methodology/chapter-05-opportunity-portfolio-and-transformation-horizons.md)
- [Chapter 06: OASIS Operating Model and Decision Rights](Methodology/chapter-06-oasis-operating-model-and-decision-rights.md)

### [Part II: The OASIS Lifecycle](Methodology/part-ii-the-oasis-lifecycle.md)

- [Chapter 07: Phase 1 — Engage & Align](Methodology/chapter-07-phase-1-engage-and-align.md)
- [Chapter 08: Phase 2 — Discover & Validate](Methodology/chapter-08-phase-2-discover-and-validate.md)
- [Chapter 09: Phase 3 — Engineer & Integrate](Methodology/chapter-09-phase-3-engineer-and-integrate.md)
- [Chapter 10: Phase 4 — Activate & Adopt](Methodology/chapter-10-phase-4-activate-and-adopt.md)
- [Chapter 11: Phase 5 — Operate & Assure](Methodology/chapter-11-phase-5-operate-and-assure.md)
- [Chapter 12: Phase 6 — Optimize & Scale](Methodology/chapter-12-phase-6-optimize-and-scale.md)
- [Chapter 13: Decision Gates and Evidence Model](Methodology/chapter-13-decision-gates-and-evidence-model.md)
- Lifecycle phase diagrams (PNG, one per phase): [diagrams/lifecycle-phases/](diagrams/lifecycle-phases/)

### [Part III: Intelligence-System Engineering and Assurance](Methodology/part-iii-intelligence-system-engineering-and-assurance.md)

- [Chapter 14: Intelligence and Agent Engineering](Methodology/chapter-14-intelligence-and-agent-engineering.md)
- [Chapter 15: Data and Knowledge Engineering](Methodology/chapter-15-data-and-knowledge-engineering.md)
- [Chapter 16: Human–AI Workflow and Experience Engineering](Methodology/chapter-16-human-ai-workflow-and-experience-engineering.md)
- [Chapter 17: Enterprise Integration and Tool Engineering](Methodology/chapter-17-enterprise-integration-and-tool-engineering.md)
- [Chapter 18: Evaluation and Reliability Engineering](Methodology/chapter-18-evaluation-and-reliability-engineering.md)
- [Chapter 19: Security and Responsible AI Engineering](Methodology/chapter-19-security-and-responsible-ai-engineering.md)
- [Chapter 20: Governance, Compliance and Regulatory Engineering](Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md)
- [Chapter 21: Deployment, Operations and AgentOps](Methodology/chapter-21-deployment-operations-and-agentops.md)
- [Chapter 22: Economics, FinOps and Sustainability](Methodology/chapter-22-economics-finops-and-sustainability.md)

### [Part IV: Delivery and Enterprise Enablement](Methodology/part-iv-delivery-and-enterprise-enablement.md)

- [Chapter 23: Forward Deployed Outcome Engineering](Methodology/chapter-23-forward-deployed-outcome-engineering.md)
- [Chapter 24: Roles, Teams and Governance Forums](Methodology/chapter-24-roles-teams-and-governance-forums.md)
- [Chapter 25: Enterprise Intelligence Platform](Methodology/chapter-25-enterprise-intelligence-platform.md)

### [Part V: Measurement, Scaling and Institutionalization](Methodology/part-v-measurement-scaling-and-institutionalization.md)

- [Chapter 26: OASIS Measurement Framework](Methodology/chapter-26-oasis-measurement-framework.md)
- [Chapter 27: Delivery Cadence and Management Practices](Methodology/chapter-27-delivery-cadence-and-management-practices.md)
- [Chapter 28: Scaling and Productization](Methodology/chapter-28-scaling-and-productization.md)
- [Chapter 29: OASIS Adoption Roadmap](Methodology/chapter-29-oasis-adoption-roadmap.md)
- [Chapter 30: Tailoring OASIS](Methodology/chapter-30-tailoring-oasis.md)
- [Chapter 31: Illustrative Use Cases](Methodology/chapter-31-illustrative-use-cases.md)
- [Chapter 32: Templates, Checklists and Tools](Methodology/chapter-32-templates-checklists-and-tools.md)
- [Chapter 33: Appendices and Reference Material](Methodology/chapter-33-appendices-and-reference-material.md)

## Standards and reference material

- [Regulatory and Standards Framework Alignment Index](references/regulatory-framework-alignment-index.md)
- [Standard: ISO/IEC 42001 Alignment Checklist](standards/iso-42001-alignment-checklist.md)
- [Standard: NIST AI RMF Alignment Checklist](standards/nist-ai-rmf-alignment-checklist.md)
- [Standard: EU AI Act Alignment Checklist](standards/eu-ai-act-alignment-checklist.md)
- [Standard: DPDP Act Alignment Checklist](standards/dpdp-act-alignment-checklist.md)
- Additional relevant standards and frameworks are listed in the alignment index.
- [Master Glossary and Roles Roster](references/master-glossary-and-roles-roster.md) (terms and roles across the whole repository, plus a default RACI)

## Assessments

- [AI Engineering Maturity Model](assessments/oasis-ai-engineering-maturity-model.md) (nine dimensions, five levels, weakest-link scoring)
- [Maturity Scorecard Template](assessments/oasis-maturity-scorecard-template.md) (fillable, per assessment cycle)

## Architecture, Engineering and Monitoring Reference

- [Architecture: OASIS Intelligence-System Reference Architecture](architecture/oasis-reference-architecture.md) (system diagram, design principles, enterprise perspectives)
  - [Architecture Principles](architecture/oasis-reference-architecture.md#architecture-principles)
  - Enterprise architecture perspectives:
    - [1. Business and Capability Architecture](architecture/perspective-01-business-and-capability-architecture.md)
    - [2. Agent Architecture](architecture/perspective-02-agent-architecture.md)
    - [3. Process Architecture](architecture/perspective-03-process-architecture.md)
    - [4. Information and Knowledge Architecture](architecture/perspective-04-information-and-knowledge-architecture.md)
    - [5. Inference Architecture](architecture/perspective-05-inference-architecture.md)
    - [6. Integration Architecture](architecture/perspective-06-integration-architecture.md)
    - [7. Deployment Architecture](architecture/perspective-07-deployment-architecture.md)
    - [8. Security and Trust Architecture](architecture/perspective-08-security-and-trust-architecture.md)
    - [9. Operations and Observability Architecture](architecture/perspective-09-operations-and-observability-architecture.md)
- Engineering (Chapter 14 companion articles, in build order):
  - [Model Engineering](engineering/model-engineering.md)
  - [Context and Retrieval Engineering](engineering/context-and-retrieval-engineering.md)
  - [Tool and Integration Interface Specification](engineering/tool-and-integration-interface-specification.md)
  - [Harness and Orchestration Engineering](engineering/harness-and-orchestration-engineering.md)
  - [Memory and State Engineering](engineering/memory-and-state-engineering.md)
  - [Evaluation and Reliability Engineering](engineering/evaluation-and-reliability-engineering.md)
- [Monitoring: Observability and Telemetry Specification](monitoring/observability-and-telemetry-specification.md)

## Security reference

- [Security: Agentic AI Threat Model and Control Checklist](security/agentic-ai-threat-and-control-checklist.md)

## Tools: fillable templates

Fillable versions of all 20 artifacts named in [Chapter 32](Methodology/chapter-32-templates-checklists-and-tools.md), grouped by lifecycle stage:

- [Outcome and Portfolio Templates](tools/01-outcome-and-portfolio-templates.md) — Opportunity Assessment, Outcome Charter, Outcome Contract, Outcome Metric Tree, Value and Risk Case
- [Workflow and Intelligence Templates](tools/02-workflow-and-intelligence-templates.md) — Process and Decision Map, Human–AI Workflow Blueprint, Data and Knowledge Readiness Assessment, Evaluation Strategy and Dataset, Failure Taxonomy
- [System and Governance Templates](tools/03-system-and-governance-templates.md) — Intelligence-System Blueprint, Autonomy Matrix, Responsibility Assignment Matrix, Decision-Gate Record
- [Readiness and Operations Templates](tools/04-readiness-and-operations-templates.md) — Production Readiness Checklist, Operational Acceptance Checklist, Outcome Scorecard, Service Runbook
- [Risk and Scale Templates](tools/05-risk-and-scale-templates.md) — Risk and Control Register, Scale and Productization Assessment

## License

Copyright (c) 2026 OASIS Methodology contributors.

Licensed under the [MIT License](LICENSE.md). Before public release, replace the contributor placeholder with the confirmed legal rights holder where necessary.
