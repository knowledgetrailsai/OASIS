<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: Outcome and Portfolio Templates](01-outcome-and-portfolio-templates.md) · [Chapter 32: Templates, Checklists and Tools](../Methodology/chapter-32-templates-checklists-and-tools.md) · [Next: System and Governance Templates →](03-system-and-governance-templates.md)

# Tools: Workflow and Intelligence Templates

> **PURPOSE** Fillable versions of the discovery, workflow-design and intelligence-readiness artifacts named in [Chapter 32](../Methodology/chapter-32-templates-checklists-and-tools.md). See [Outcome and Portfolio Templates](01-outcome-and-portfolio-templates.md) for how this set fits together, and the [PRACTICALITY rule](../Methodology/chapter-32-templates-checklists-and-tools.md#template-use-rule): fill only what a decision actually needs.

Covers templates 6–10 of 20. See also: [Outcome and Portfolio Templates](01-outcome-and-portfolio-templates.md) · [System and Governance Templates](03-system-and-governance-templates.md) · [Readiness and Operations Templates](04-readiness-and-operations-templates.md) · [Risk and Scale Templates](05-risk-and-scale-templates.md).

## Background and context

These five templates carry the discovery and design work that turns an approved opportunity into a buildable intelligence system: mapping how the process actually works today, deciding what the AI and the human each do at every step, and confirming the data, evaluation and failure-handling foundations are solid before engineering begins in earnest. They sit between the outcome-and-portfolio decisions (which establish *whether* to build) and the system-and-governance templates (which establish *how much authority* the built system gets) — get the process map and data readiness assessment wrong here and every downstream artifact inherits the error.

---

## 6. Process and Decision Map

**Chapter 32 minimum content:** Actors, steps, systems, inputs, decisions, rules, evidence, queues, exceptions, pain points and outcome events.

**Primary source:** [Chapter 8 — Phase 2: Discover & Validate](../Methodology/chapter-08-phase-2-discover-and-validate.md).

| Step # | Actor | System(s) touched | Input | Decision made | Rule/policy applied | Evidence used | Queue / handoff | Exception path | Pain point | Outcome event? |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | | | | | | | | | | |
| 2 | | | | | | | | | | |
| 3 | | | | | | | | | | |

Add one row per meaningful step of the current process, end to end, before designing the intelligence system that will change it — the map should describe the process *as it exists today*, not the target state.

---

## 7. Human–AI Workflow Blueprint

**Chapter 32 minimum content:** AI role, human role, authority, evidence, interface, approval, override, fallback, escalation, feedback and outcome.

**Primary source:** [Chapter 16 — Human–AI Workflow and Experience Engineering](../Methodology/chapter-16-human-ai-workflow-and-experience-engineering.md).

```yaml
human_ai_workflow_blueprint:
  workflow_name: ""
  step_sequence:
    - step: ""
      ai_role: ""                  # what the system does at this step
      human_role: ""                # what the human does at this step
      authority: "AI acts | AI recommends, human decides | human acts, AI assists"
      evidence_shown_to_human: ""
      interface: ""                 # where/how the human interacts (dashboard, chat, embedded in existing tool)
      approval_required: true|false
      override_mechanism: ""
      fallback_if_ai_unavailable: ""
      escalation_trigger: ""
      escalation_target: ""
  feedback_loop:
    how_human_corrections_are_captured: ""
    how_corrections_feed_back_to_evaluation: ""     # link to Evaluation Strategy and Dataset, template 9
  outcome_event: ""                 # what marks this workflow as complete / successful
```

---

## 8. Data and Knowledge Readiness Assessment

**Chapter 32 minimum content:** Sources, owners, authority, quality, coverage, freshness, metadata, access, lineage, retention and operations.

**Primary source:** [Chapter 15 — Data and Knowledge Engineering](../Methodology/chapter-15-data-and-knowledge-engineering.md).

| Data / knowledge source | Owner | Authoritative? | Quality (1–5) | Coverage gaps | Freshness | Metadata available? | Access control | Lineage documented? | Retention policy | Operational status |
|---|---|---|---|---|---|---|---|---|---|---|
| | | | | | | | | | | |
| | | | | | | | | | | |

Score quality and coverage against the specific decision this data will support, not in the abstract — a source that is "quality 5" for reporting may still be unfit as retrieval evidence if it lacks source attribution.

---

## 9. Evaluation Strategy and Dataset

**Chapter 32 minimum content:** Quality dimensions, cases, sources, splits, expected behavior, graders, thresholds, regression and production sampling.

**Primary source:** [Chapter 18 — Evaluation and Reliability Engineering](../Methodology/chapter-18-evaluation-and-reliability-engineering.md).

```yaml
evaluation_strategy:
  quality_dimensions:               # what "good" means for this system
    - intent_understanding
    - correctness
    - groundedness
    - citation_accuracy
    - structured_output_validity
    - retrieval_quality
    - tool_selection_accuracy
    - workflow_completion
    - policy_adherence
    - escalation_correctness
    - robustness
    - latency
    - cost
    - user_acceptance
    - outcome_contribution
  dataset:
    total_cases: 0
    sources: []                     # synthetic, historical, expert-authored, production-sampled
    splits:
      dev: 0
      held_out: 0
      regression: 0
  case_design:
    - case_id: ""
      description: ""
      expected_behavior: ""
      grader: "human | rubric | model-graded | deterministic"
      pass_threshold: ""
  regression_policy: ""             # every production failure becomes a case — see Ch.21 learning loop
  production_sampling:
    sample_rate: ""
    review_cadence: ""
```

---

## 10. Failure Taxonomy

**Chapter 32 minimum content:** Failure family, severity, detectability, cause, evidence, impact, owner, containment, correction and regression case.

**Primary source:** [Chapter 21 — Deployment, Operations and AgentOps](../Methodology/chapter-21-deployment-operations-and-agentops.md) (responsible-layer incident classification); see also the [Monitoring incident taxonomy](../monitoring/observability-and-telemetry-specification.md#4-incident-classification-responsible-layer-taxonomy).

| Failure family | Responsible layer | Severity | Detectability | Root cause | Evidence | Business impact | Owner | Containment action | Correction | Regression case added? |
|---|---|---|---|---|---|---|---|---|---|---|
| | | | | | | | | | | |
| | | | | | | | | | | |

Classify by responsible layer (model / context / retrieval / tool-selection / tool-execution / state / workflow / policy / human-approval / enterprise-dependency) before root-causing — see the [Monitoring spec's incident taxonomy](../monitoring/observability-and-telemetry-specification.md#4-incident-classification-responsible-layer-taxonomy) for the full list.

---

[← Back to Contents](../README.md) · [← Previous: Outcome and Portfolio Templates](01-outcome-and-portfolio-templates.md) · [Chapter 32: Templates, Checklists and Tools](../Methodology/chapter-32-templates-checklists-and-tools.md) · [Next: System and Governance Templates →](03-system-and-governance-templates.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
