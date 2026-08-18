<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 13: Decision Gates and Evidence Model](../Methodology/chapter-13-decision-gates-and-evidence-model.md) · [Next: Maturity Scorecard Template →](oasis-maturity-scorecard-template.md)

# Assessment: OASIS AI Engineering Maturity Model

> **PURPOSE** Give an organization a way to answer "where are we, really?" across the nine areas this handbook covers — not as a single vague label like "we're doing AI," but as a per-dimension, evidence-backed level that names the specific gap standing between where the organization is and where it needs to be before it can safely go further. Use this before a portfolio review (Chapter 26/27) or before committing to a new transformation horizon (Chapter 5), and repeat it on a fixed cadence rather than once.

**Primary OASIS source:** [Chapter 13 — Decision Gates and Evidence Model](../Methodology/chapter-13-decision-gates-and-evidence-model.md) (the evidence discipline this model applies at the organizational level); [Chapter 2 — Methodology Foundations and Design Principles](../Methodology/chapter-02-methodology-foundations-and-design-principles.md); [Architecture Principles](../architecture/oasis-reference-architecture.md#architecture-principles).

## Background and context

Most maturity models in this space ask a handful of generic questions ("do you have an AI strategy?", "do you have governance?") and produce a single score that flatters everyone a little and tells no one anything actionable. That approach breaks down specifically for agentic AI systems, because the whole premise of this methodology — stated most directly in the [Evidence gated](../architecture/oasis-reference-architecture.md#architecture-principles) architecture principle — is that a single weak dimension can invalidate an otherwise strong system. An organization with excellent model engineering and no accountable-owner discipline is not "70% mature"; it is one incident away from a very bad week, because nobody can say who was supposed to catch the failure. A single blended score hides exactly the kind of gap this methodology exists to surface.

This model instead scores nine dimensions independently, one for each major area this repository covers in depth, and it deliberately does not average them into one number. The organization's overall maturity is reported as its **lowest-scoring dimension**, not its average — the same weakest-link logic Chapter 13 applies to individual decision gates, applied here at the portfolio level. A9-out-of-9 organization with one dimension at Level 0 is a Level 0 organization for the purposes of deciding what to fix next, even if the other eight dimensions are strong. This is a deliberately uncomfortable design choice, and it is the point: it stops "we're mostly there" from becoming an excuse to defer the one gap that will actually cause the incident.

Use this model at three points in particular. Before committing real budget to a new transformation horizon (Chapter 5), to know honestly what foundation is being built on. Before a portfolio or architecture review (Chapter 26/27), as the evidence base for the conversation rather than anecdote. And on a fixed cadence — quarterly is a reasonable default, matching the portfolio review cadence in [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#governance-forums) — so that maturity is tracked as a trend, not re-litigated from scratch each time someone asks "are we ready?" The companion [Maturity Scorecard Template](oasis-maturity-scorecard-template.md) is the fillable instance of this model; this document defines what each level actually means per dimension.

## 1. The five maturity levels

| Level | Name | What characterizes it |
|---|---|---|
| 0 | **Ad hoc** | Work happens, but through individual initiative and undocumented judgment calls. No named accountable owner, no repeatable artifact, no evidence trail. What worked last time is not reliably known, let alone why. |
| 1 | **Initiated** | At least one system or pilot exists with some of the relevant artifacts populated, but practice is inconsistent across teams and depends on specific individuals rather than an organizational standard. |
| 2 | **Managed** | A defined, repeatable practice exists and is followed for new work — the relevant OASIS artifacts (templates, checklists) are populated as a matter of course, not as an exception. Practice is consistent within a team or business unit but may still vary across the organization. |
| 3 | **Governed** | The practice is consistent across the organization, backed by a named accountable owner and a forum with real authority (per [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md)), and evidence is reviewed, not just produced. A gap in this dimension would be caught before it caused an incident, not after. |
| 4 | **Institutionalized** | The practice is self-improving: failures in this dimension feed back into the standard itself (per the production learning loop in [Chapter 21](../Methodology/chapter-21-deployment-operations-and-agentops.md)), the practice scales across new systems without re-deriving it each time, and it is treated as a durable organizational capability rather than a project deliverable. |

A dimension does not need to reach Level 4 to be "good enough" — the right target level depends on the risk classification of what the organization is building (per the autonomy and risk discipline in [Chapter 19](../Methodology/chapter-19-security-and-responsible-ai-engineering.md)). A low-stakes internal pilot may reasonably operate at Level 2 in most dimensions. A system with execute-level authority over regulated decisions should not be in production below Level 3 in Security & Responsible AI or Governance & Regulatory Compliance, regardless of how advanced its engineering is elsewhere.

## 2. The nine dimensions

### Dimension 1 — Outcome and Portfolio Discipline

*Primary chapters: [Chapter 5](../Methodology/chapter-05-opportunity-portfolio-and-transformation-horizons.md), [Chapter 26](../Methodology/chapter-26-oasis-measurement-framework.md), [Chapter 27](../Methodology/chapter-27-delivery-cadence-and-management-practices.md); primary artifacts: [Outcome Charter, Outcome Contract, Outcome Metric Tree](../Methodology/chapter-32-templates-checklists-and-tools.md#2-outcome-charter).*

| Level | What it looks like at this level |
|---|---|
| 0 | Initiatives are pursued because the technology is available, with no stated business outcome or owner. |
| 1 | Some initiatives have a stated outcome, but it's informal — no Outcome Contract, no agreed baseline or target. |
| 2 | New initiatives routinely get an Outcome Charter and Outcome Contract before build starts; targets are set with baselines. |
| 3 | The full opportunity portfolio is reviewed on a fixed cadence against the Outcome Metric Tree (per [Chapter 5](../Methodology/chapter-05-opportunity-portfolio-and-transformation-horizons.md#portfolio-balance)); underperforming initiatives are reframed or retired, not left running on inertia. |
| 4 | Outcome data from production (per [Monitoring's Outcome plane](../monitoring/observability-and-telemetry-specification.md#outcome-plane)) feeds back into portfolio prioritization automatically, and outcome measurement is a platform capability, not a per-project exercise. |

### Dimension 2 — Lifecycle and Evidence Gates

*Primary chapters: [Chapters 7–13](../Methodology/chapter-07-phase-1-engage-and-align.md); primary artifact: [Decision-Gate Record](../Methodology/chapter-32-templates-checklists-and-tools.md#20-decision-gate-record).*

| Level | What it looks like at this level |
|---|---|
| 0 | Phase transitions happen on calendar pressure or stakeholder confidence, with no recorded evidence. |
| 1 | Some gates are informally checked; no consistent Decision-Gate Record. |
| 2 | Every initiative passes through the six phases with gate evidence recorded, though what counts as "sufficient evidence" varies by reviewer. |
| 3 | Gate criteria are standardized and enforced by an independent reviewer (per [Chapter 13](../Methodology/chapter-13-decision-gates-and-evidence-model.md)); a project cannot self-certify its own gate passage. |
| 4 | Gate failure patterns are tracked across the portfolio and used to strengthen the gate criteria themselves — the organization gets measurably better at knowing what "ready" actually means over time. |

### Dimension 3 — Intelligence and Agent Engineering

*Primary chapters: [Chapters 14–18](../Methodology/chapter-14-intelligence-and-agent-engineering.md); primary artifacts: the six [engineering/](../engineering/) articles.*

| Level | What it looks like at this level |
|---|---|
| 0 | Systems are built by prompting a model directly, with no context architecture, tool contracts, or evaluation suite. |
| 1 | At least one system has a documented model choice and some evaluation, built by a small group with tacit knowledge of what works. |
| 2 | New systems are routinely specified, benchmarked and evaluated per the [engineering/](../engineering/) articles — context architecture, tool contracts, harness design and an evaluation suite are standard deliverables. |
| 3 | Engineering practice is consistent across teams, reviewed at an architecture forum, and every production agent is registered per [Agent Architecture](../architecture/perspective-02-agent-architecture.md#3-agent-registry). |
| 4 | Engineering components (context sources, tool contracts, evaluation suites) are built once and reused across systems, per the [Composable and reusable](../architecture/oasis-reference-architecture.md#architecture-principles) principle, rather than rebuilt per project. |

### Dimension 4 — Architecture and Platform

*Primary source: [architecture/](../architecture/) folder (reference architecture, principles, nine perspectives); primary artifact: [Intelligence-System Blueprint](../Methodology/chapter-32-templates-checklists-and-tools.md#11-intelligence-system-blueprint).*

| Level | What it looks like at this level |
|---|---|
| 0 | No shared architecture — each system is designed independently with no common vocabulary or component reuse. |
| 1 | At least one system has a documented architecture; others are built ad hoc. |
| 2 | New systems are designed against the [OASIS Reference Architecture](../architecture/oasis-reference-architecture.md), with a completed Intelligence-System Blueprint. |
| 3 | The organization maintains enterprise-wide registries per the nine [architecture perspectives](../architecture/oasis-reference-architecture.md#6-enterprise-architecture-perspectives) — a real agent taxonomy, a real capability map, a real integration catalogue — not just per-system diagrams. |
| 4 | Architecture decisions are made with full portfolio visibility (duplication, gaps, reuse potential) and platform investment is prioritized against that visibility, per [Chapter 25](../Methodology/chapter-25-enterprise-intelligence-platform.md). |

### Dimension 5 — Security and Responsible AI

*Primary chapter: [Chapter 19](../Methodology/chapter-19-security-and-responsible-ai-engineering.md); primary artifact: [Security: Threat and Control Checklist](../security/agentic-ai-threat-and-control-checklist.md).*

| Level | What it looks like at this level |
|---|---|
| 0 | No systematic threat model; security is addressed reactively after an incident. |
| 1 | Some systems have documented controls; coverage of the eight defense-in-depth layers is inconsistent. |
| 2 | New systems are reviewed against the [Security checklist](../security/agentic-ai-threat-and-control-checklist.md)'s defense-in-depth and threat-model tables before launch. |
| 3 | Kill-switch and containment authority is pre-assigned and tested (not improvised mid-incident), per [Security and Trust Architecture](../architecture/perspective-08-security-and-trust-architecture.md#3-enterprise-permission-issuance-principles). |
| 4 | Threats discovered in one system are checked against every other system with the same shared component, per the enterprise incident-response pattern in [Operations and Observability Architecture](../architecture/perspective-09-operations-and-observability-architecture.md#2-enterprise-incident-response). |

### Dimension 6 — Governance and Regulatory Compliance

*Primary chapter: [Chapter 20](../Methodology/chapter-20-governance-compliance-and-regulatory-engineering.md); primary source: [standards/](../standards/) and [references/regulatory-framework-alignment-index.md](../references/regulatory-framework-alignment-index.md).*

| Level | What it looks like at this level |
|---|---|
| 0 | No systematic tracking of which regulatory obligations apply to which systems. |
| 1 | Legal/compliance is consulted ad hoc, typically after a system is already built. |
| 2 | New systems are checked against the relevant [Standards](../standards/) checklist (ISO 42001, NIST AI RMF, EU AI Act, DPDP Act, or others per the [regulatory alignment index](../references/regulatory-framework-alignment-index.md)) before launch. |
| 3 | A named governance forum (per [Chapter 24](../Methodology/chapter-24-roles-teams-and-governance-forums.md#governance-forums)) reviews compliance status on a fixed cadence, with a real escalation path for gaps. |
| 4 | Regulatory changes are tracked proactively against the applicable-framework list and trigger a scheduled review of affected systems, rather than being discovered when a system is already non-compliant. |

### Dimension 7 — Operations and AgentOps

*Primary chapter: [Chapter 21](../Methodology/chapter-21-deployment-operations-and-agentops.md); primary artifact: [Monitoring: Observability and Telemetry Specification](../monitoring/observability-and-telemetry-specification.md).*

| Level | What it looks like at this level |
|---|---|
| 0 | No systematic monitoring beyond basic uptime; incidents are diagnosed from scratch each time. |
| 1 | Some telemetry exists for at least one system, but the six operational planes aren't consistently instrumented. |
| 2 | New systems are instrumented per the [Monitoring specification](../monitoring/observability-and-telemetry-specification.md), with a release manifest and incident-classification taxonomy in place before go-live. |
| 3 | An enterprise operations rollup exists (per [Operations and Observability Architecture §1](../architecture/perspective-09-operations-and-observability-architecture.md#1-enterprise-operations-dashboard-rollup-structure)) giving portfolio-wide visibility, not just per-system dashboards. |
| 4 | The production learning loop (Chapter 21) closes reliably — failures become regression cases, and mean-time-to-diagnose the responsible layer trends down over time. |

### Dimension 8 — Economics and FinOps

*Primary chapter: [Chapter 22](../Methodology/chapter-22-economics-finops-and-sustainability.md); primary source: [Inference Architecture — Cost governance](../architecture/perspective-05-inference-architecture.md#4-cost-governance).*

| Level | What it looks like at this level |
|---|---|
| 0 | No visibility into per-system AI spend; cost is discovered on the invoice. |
| 1 | Cost is tracked for at least one system, but not tied to outcome value. |
| 2 | New systems carry a Value and Risk Case with a stated cost budget, and per-system spend is tracked against it. |
| 3 | Aggregate spend is tracked centrally across the portfolio (per [Inference Architecture §4](../architecture/perspective-05-inference-architecture.md#4-cost-governance)), with cost-per-successful-outcome as a standard metric. |
| 4 | Cost governance actively informs model routing, optimization-ladder decisions and platform investment — economics is a design input, not a retrospective report. |

### Dimension 9 — Scaling and Reuse

*Primary chapter: [Chapter 28](../Methodology/chapter-28-scaling-and-productization.md); primary artifact: [Scale and Productization Assessment](../Methodology/chapter-32-templates-checklists-and-tools.md#18-scale-and-productization-assessment).*

| Level | What it looks like at this level |
|---|---|
| 0 | Every system is built from scratch; there is no shared component inventory. |
| 1 | Some reuse happens informally, through personal knowledge of what another team built. |
| 2 | Components with reuse potential are identified and tracked (per [Business and Capability Architecture](../architecture/perspective-01-business-and-capability-architecture.md#1-capability-map-template)) as candidates for productization. |
| 3 | A formal productization path exists — a component crossing the reuse threshold gets a named platform owner and shared service levels. |
| 4 | The majority of new systems are assembled substantially from existing platform components rather than built new, and the platform's reuse rate is itself a tracked metric. |

## 3. Scoring rule and how to read a result

Score each of the nine dimensions independently using the [Maturity Scorecard Template](oasis-maturity-scorecard-template.md). Report two numbers, not one: the **profile** (all nine scores, so the shape of strength and weakness is visible) and the **overall level**, defined as the minimum across all nine dimensions. Do not average. An organization at Level 3 in eight dimensions and Level 0 in Security and Responsible AI is a Level 0 organization for any decision involving that system's risk exposure — the average would report a comfortable 2.7 and miss the one gap that actually determines whether the organization is safe to proceed.

Use the profile, not just the overall level, to decide what to fix next: the overall level tells leadership how much risk exists somewhere in the portfolio; the profile tells the team exactly where.

---

[← Back to Contents](../README.md) · [Chapter 13: Decision Gates and Evidence Model](../Methodology/chapter-13-decision-gates-and-evidence-model.md) · [Next: Maturity Scorecard Template →](oasis-maturity-scorecard-template.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
