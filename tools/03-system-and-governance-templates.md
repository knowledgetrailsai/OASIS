<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: Workflow and Intelligence Templates](02-workflow-and-intelligence-templates.md) · [Chapter 32: Templates, Checklists and Tools](../Methodology/chapter-32-templates-checklists-and-tools.md) · [Next: Readiness and Operations Templates →](04-readiness-and-operations-templates.md)

# Tools: System and Governance Templates

> **PURPOSE** Fillable versions of the system-design and decision-governance artifacts named in [Chapter 32](../Methodology/chapter-32-templates-checklists-and-tools.md). The Intelligence-System Blueprint below is the fillable companion to the [Architecture Reference Architecture](../architecture/oasis-reference-architecture.md) — use that document's diagram to structure this template's content.

Covers templates 11–12 and 19–20 of 20. See also: [Outcome and Portfolio Templates](01-outcome-and-portfolio-templates.md) · [Workflow and Intelligence Templates](02-workflow-and-intelligence-templates.md) · [Readiness and Operations Templates](04-readiness-and-operations-templates.md) · [Risk and Scale Templates](05-risk-and-scale-templates.md).

## Background and context

These four templates carry the decisions about authority: what the system is architecturally, what it is allowed to do without a human, who is accountable for each decision, and what evidence justified each gate passage. They are grouped together because they share a common failure mode when skipped or filled superficially — an intelligence system with a complete blueprint but no autonomy matrix, or a project with clear roles but no decision-gate record, tends to accumulate authority informally over time rather than through evidenced, reviewable steps, which is exactly what Chapter 13's decision-gate model exists to prevent.

---

## 11. Intelligence-System Blueprint

**Chapter 32 minimum content:** Boundary, actors, models, context, knowledge, tools, workflow, memory/state, controls, runtime, telemetry and dependencies.

**Primary source:** [Chapter 14 — Intelligence and Agent Engineering](../Methodology/chapter-14-intelligence-and-agent-engineering.md); structure this using the [Architecture Reference Architecture](../architecture/oasis-reference-architecture.md#2-component-to-artifact-map) component map.

```yaml
intelligence_system_blueprint:
  system_name: ""
  boundary: ""                      # what is in scope vs. explicitly out of scope for this system
  actors:
    human_roles: []
    upstream_systems: []
    downstream_systems: []
  specification_reference: ""       # link to Ch.14 §1 Intelligence-System Specification
  model:
    primary: ""
    fallback: ""
    routing_criteria: ""
  context:
    sources: []                     # link to Data and Knowledge Readiness Assessment, template 8
    assembly_approach: ""
    token_budget: ""
  knowledge_and_retrieval:
    indexes: []
    freshness_policy: ""
  tools:
    - name: ""
      contract_reference: ""        # link to Engineering: Tool and Integration Interface Specification
  workflow_pattern: "deterministic function | explicit workflow | agent | multi-agent"
  workflow_pattern_rationale: ""    # required if agent or multi-agent — see Ch.14 §7 decision rule
  memory_and_state:
    what_persists: ""
    retention: ""
    correction_rights: ""
  controls:
    guardrail_layers_implemented: []   # see Security: Agentic AI Threat Model and Control Checklist
  runtime_and_telemetry:
    trace_fields: ""                # link to Monitoring: Observability and Telemetry Specification
  dependencies: []
```

---

## 12. Autonomy Matrix

**Chapter 32 minimum content:** Action, case class, risk, system capability, human authority, limits, evidence threshold, escalation and suspension.

**Primary source:** [Chapter 10 — Phase 4: Activate & Adopt](../Methodology/chapter-10-phase-4-activate-and-adopt.md); [Chapter 16 — Human–AI Workflow and Experience Engineering](../Methodology/chapter-16-human-ai-workflow-and-experience-engineering.md) (progressive-autonomy modes: Shadow, Assisted, Supervised, Bounded Autonomy, and beyond).

| Action | Case class | Risk level | Current system capability (evidenced) | Human authority required | Operating limits | Evidence threshold to progress | Escalation trigger | Suspension trigger |
|---|---|---|---|---|---|---|---|---|
| | | | | | | | | |
| | | | | | | | | |

One row per distinct action the system can take, not one row per system. An agent that both drafts customer replies and issues refunds needs two rows — the evidence threshold to trust drafting has nothing to do with the threshold to trust issuing money. Progression from one autonomy mode to the next requires evidence per row, not a blanket system-wide promotion.

---

## 19. Responsibility Assignment Matrix

**Chapter 32 minimum content:** Activity and decision mapped to accountable, responsible, consulted and informed roles.

**Primary source:** [Chapter 6 — OASIS Operating Model and Decision Rights](../Methodology/chapter-06-oasis-operating-model-and-decision-rights.md); [Chapter 24 — Roles, Teams and Governance Forums](../Methodology/chapter-24-roles-teams-and-governance-forums.md).

| Activity / decision | Accountable (A) | Responsible (R) | Consulted (C) | Informed (I) |
|---|---|---|---|---|
| Outcome Charter sign-off | | | | |
| Risk classification | | | | |
| Decision-gate pass/fail | | | | |
| Production release approval | | | | |
| Autonomy-mode promotion | | | | |
| Kill-switch activation | | | | |
| Incident severity classification | | | | |

Exactly one accountable owner per row — if two names appear under Accountable, the row is not yet resolved. Add or remove rows to match the engagement's actual decision inventory.

---

## 20. Decision-Gate Record

**Chapter 32 minimum content:** Decision, evidence, alternatives, conditions, residual risk, owner, due date, expiry and follow-up.

**Primary source:** [Chapter 13 — Decision Gates and Evidence Model](../Methodology/chapter-13-decision-gates-and-evidence-model.md).

```yaml
decision_gate_record:
  gate_name: ""                     # which of the six lifecycle gates, per Ch.13
  date: ""
  decision: "pass | pass with conditions | hold | fail"
  evidence_reviewed:
    - artifact: ""
      summary: ""
  alternatives_considered: []
  conditions_if_conditional: []
  residual_risk_accepted: ""
  residual_risk_accepted_by: ""
  owner: ""
  due_date_for_conditions: ""
  expiry: ""                        # when this decision must be revisited regardless of outcome
  follow_up_actions: []
```

Complete one record per gate passage, not one per project — a six-phase engagement produces at least six of these, and a conditional pass or hold should be tracked to its due date rather than left open indefinitely.

---

[← Back to Contents](../README.md) · [← Previous: Workflow and Intelligence Templates](02-workflow-and-intelligence-templates.md) · [Chapter 32: Templates, Checklists and Tools](../Methodology/chapter-32-templates-checklists-and-tools.md) · [Next: Readiness and Operations Templates →](04-readiness-and-operations-templates.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
