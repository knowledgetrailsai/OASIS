<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: System and Governance Templates](03-system-and-governance-templates.md) · [Chapter 32: Templates, Checklists and Tools](../Methodology/chapter-32-templates-checklists-and-tools.md) · [Next: Risk and Scale Templates →](05-risk-and-scale-templates.md)

# Tools: Readiness and Operations Templates

> **PURPOSE** Fillable versions of the go-live readiness and running-service artifacts named in [Chapter 32](../Methodology/chapter-32-templates-checklists-and-tools.md). These pair directly with the [Monitoring: Observability and Telemetry Specification](../monitoring/observability-and-telemetry-specification.md) — its release-manifest checklist and operational-plane metrics are the evidence source for several fields below.

Covers templates 13–16 of 20. See also: [Outcome and Portfolio Templates](01-outcome-and-portfolio-templates.md) · [Workflow and Intelligence Templates](02-workflow-and-intelligence-templates.md) · [System and Governance Templates](03-system-and-governance-templates.md) · [Risk and Scale Templates](05-risk-and-scale-templates.md).

## Background and context

These four templates carry the transition from a built system to a running service: confirming it is safe to expose to live users, confirming it is actually working for them once it is, and giving the team that will operate it going forward the running record (scorecard, runbook) it needs to do so without re-deriving context from the build team. Production readiness and operational acceptance are deliberately separate gates rather than one — a system can be technically safe to release and still fail to deliver the outcome once real users touch it, and conflating the two gates hides that failure mode until it is expensive to fix.

---

## 13. Production Readiness Checklist

**Chapter 32 minimum content:** Architecture, security, privacy, evaluations, integration, resilience, monitoring, support, runbook, rollback and approvals.

**Primary source:** [Chapter 9 — Phase 3: Engineer & Integrate](../Methodology/chapter-09-phase-3-engineer-and-integrate.md); [Chapter 21 — Deployment, Operations and AgentOps](../Methodology/chapter-21-deployment-operations-and-agentops.md); [Monitoring: release manifest checklist](../monitoring/observability-and-telemetry-specification.md#3-release-manifest-checklist).

| # | Area | Requirement | Evidence | Status | Approver |
|---|---|---|---|---|---|
| 1 | Architecture | Intelligence-System Blueprint complete and reviewed | | | |
| 2 | Security | [Security checklist](../security/agentic-ai-threat-and-control-checklist.md) sections 1–4 complete | | | |
| 3 | Privacy | Applicable [Standards](../standards/) checklist(s) complete for data in scope | | | |
| 4 | Evaluations | Evaluation Strategy and Dataset thresholds met | | | |
| 5 | Integration | All tool contracts registered and tested ([Engineering spec](../engineering/tool-and-integration-interface-specification.md)) | | | |
| 6 | Resilience | Timeout, retry, idempotency and compensation behavior tested | | | |
| 7 | Monitoring | All six operational planes instrumented ([Monitoring spec](../monitoring/observability-and-telemetry-specification.md#1-the-six-operational-planes-instrumented)) | | | |
| 8 | Support | On-call ownership and escalation path defined | | | |
| 9 | Runbook | Service Runbook (template 16) complete | | | |
| 10 | Rollback | Rollback vs. forward-fix criteria documented | | | |
| 11 | Approvals | All named approvers have signed off | | | |

---

## 14. Operational Acceptance Checklist

**Chapter 32 minimum content:** Live users, task completion, quality, controls, adoption, fallback, incidents, training, service owner and accepted authority.

**Primary source:** [Chapter 10 — Phase 4: Activate & Adopt](../Methodology/chapter-10-phase-4-activate-and-adopt.md).

| # | Item | Target | Actual (at acceptance) | Status |
|---|---|---|---|---|
| 1 | Live users onboarded | | | |
| 2 | Task completion rate | | | |
| 3 | Quality (per evaluation thresholds) | | | |
| 4 | Guardrail/control breaches since launch | 0 unresolved | | |
| 5 | Adoption rate | | | |
| 6 | Fallback path exercised successfully | Yes | | |
| 7 | Incidents since launch | | | |
| 8 | User training completed | | | |
| 9 | Named service owner in place | | | |
| 10 | Accepted operating authority (per Autonomy Matrix) | | | |

Operational acceptance is a distinct gate from production readiness — readiness confirms the system is safe to expose to live users; acceptance confirms it is actually working for them.

---

## 15. Outcome Scorecard

**Chapter 32 minimum content:** Outcome, adoption, intelligence, risk, service, economics, reuse, trend, threshold, commentary and action.

**Primary source:** [Chapter 26 — OASIS Measurement Framework](../Methodology/chapter-26-oasis-measurement-framework.md); metric sources per the [Monitoring spec's operational planes](../monitoring/observability-and-telemetry-specification.md#1-the-six-operational-planes-instrumented).

| Dimension | Metric | Current | Threshold/target | Trend | Commentary | Action |
|---|---|---|---|---|---|---|
| Outcome | | | | | | |
| Adoption | | | | | | |
| Intelligence | | | | | | |
| Risk | | | | | | |
| Service | | | | | | |
| Economics | | | | | | |
| Reuse | | | | | | |

Review at the cadence set in [Chapter 27 — Delivery Cadence and Management Practices](../Methodology/chapter-27-delivery-cadence-and-management-practices.md). A scorecard with no "Action" entries for two consecutive reviews should prompt a check on whether it's actually being used to make decisions or just archived.

---

## 16. Service Runbook

**Chapter 32 minimum content:** Purpose, dependencies, dashboards, alerts, triage, fallbacks, escalation, recovery, changes, contacts and evidence retention.

**Primary source:** [Chapter 21 — Deployment, Operations and AgentOps](../Methodology/chapter-21-deployment-operations-and-agentops.md); [Chapter 19 — Containment and emergency control](../Methodology/chapter-19-security-and-responsible-ai-engineering.md#containment-and-emergency-control).

```yaml
service_runbook:
  service_name: ""
  purpose: ""
  dependencies:
    upstream: []
    downstream: []
  dashboards:
    - name: ""
      link: ""
  alerts:
    - name: ""
      trigger: ""
      severity: ""
      first_responder: ""
  triage_guide: ""                  # link to Monitoring spec's responsible-layer incident taxonomy
  fallback_path: ""                 # manual or deterministic path when suspended
  kill_switch:
    owner: ""
    activation_method: ""
    last_tested: ""
  escalation_chain: []
  recovery_procedure: ""
  recent_changes_log: ""            # link to release manifest history
  contacts:
    service_owner: ""
    on_call_rotation: ""
    business_owner: ""
  evidence_retention_policy: ""
```

---

[← Back to Contents](../README.md) · [← Previous: System and Governance Templates](03-system-and-governance-templates.md) · [Chapter 32: Templates, Checklists and Tools](../Methodology/chapter-32-templates-checklists-and-tools.md) · [Next: Risk and Scale Templates →](05-risk-and-scale-templates.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
