<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 11: Phase 5 — Operate & Assure](chapter-11-phase-5-operate-and-assure.md) · [Contents](../README.md) · [Next: Chapter 13: Decision Gates and Evidence Model →](chapter-13-decision-gates-and-evidence-model.md)

# Chapter 12: Phase 6 — Optimize & Scale

# Phase 6 — Optimize & Scale

> **CHAPTER PURPOSE** Improve performance, expand justified autonomy, productize recurring patterns and scale only where production evidence supports reuse.

## Background and context

Phase 5 generates the evidence; Phase 6 is where that evidence gets acted on deliberately, rather than left to accumulate as a backlog nobody prioritizes. It is the phase most easily skipped under delivery pressure — a system that is operating within acceptable limits can look finished, and teams move on to the next opportunity rather than investing in improving what already works or in generalizing it beyond its original context. That instinct is understandable and usually costly: the same failure patterns and the same reusable components tend to recur across an organization's AI portfolio, and a methodology that never asks "what repeats" ends up rebuilding the same context pipeline, the same guardrail logic and the same evaluation suite for every new use case.

This phase has two genuinely distinct halves that share a chapter because they draw on the same evidence base. Optimization is local — improving quality, latency, cost or adoption for the system that exists. Scale is about generalization — recognizing that a component, pattern or capability built for one deployment is valuable enough, and stable enough, to become a shared platform asset serving several. Confusing the two leads to the two most common mistakes in this phase: optimizing a system that should really be retired, and prematurely productizing a component that has only ever been tested in one context. The capability-reuse discipline this phase draws on connects to [Architecture Perspective 1: Business and Capability Architecture](../architecture/perspective-01-business-and-capability-architecture.md#3-capability-portfolio-view), which is where capability consolidation across a portfolio is tracked at the enterprise level rather than one system at a time.

Phase 6 is also where the lifecycle loops back on itself: an optimization that changes behavior meaningfully, or a scale decision that expands the system's user base, exposure or authority, does not just get released — it re-enters the gate structure described in [Chapter 13](chapter-13-decision-gates-and-evidence-model.md), because a materially different system deserves the same evidence discipline a new one would.

## Phase objective

Improve quality, latency, economics and adoption; expand justified autonomy; and convert recurring patterns into reusable capability.

Each of these three objectives has a different failure mode if pursued alone. Optimization without a scale lens produces a system that is excellent but unrepeatable. Scale without optimization first productizes a component before it is actually good, baking its flaws into every future deployment that reuses it. Autonomy expansion pursued without the other two treats trust as something that accrues automatically over time rather than something that has to be earned against fresh evidence every time the system's authority increases.

## Core questions

- What should improve locally?

- What repeats across deployments?

- What belongs in platform, component or configuration?

- Is expansion economically and operationally justified?

The third question is where a lot of ambiguity in enterprise AI programs actually lives. Not everything that repeats belongs in a shared platform component — some things repeat because they are genuinely common across deployments, and some things merely look similar on the surface while differing in the details that matter (data sensitivity, regulatory obligation, user population). Distinguishing platform capability from business configuration from genuinely bespoke need is a judgment call this phase has to make explicitly, because getting it wrong in either direction is expensive: over-productizing forces every consumer into a shared component that doesn't quite fit them, and under-productizing means five teams independently rebuild and independently maintain the same thing.

## Method

35. Prioritize improvements using outcome contribution, failure frequency, risk, intervention and cost.

36. Optimize the responsible layer: workflow, data, retrieval, context, tool, harness, model, infrastructure or user experience.

37. Re-run regression and business-outcome tests before releasing changes.

38. Classify recurring assets as platform capability, reusable deployment component, business configuration or bespoke need.

39. Test repeatability in a second context before declaring an asset standard.

40. Reassess risk, regulation, capacity, support and economics before expanding users, geography, data, action authority or autonomy.

Step 36's instruction to optimize "the responsible layer" rather than the first plausible lever is the direct continuation of the responsible-layer failure classification introduced back in Phase 2 and used throughout Phase 5's incident triage — a latency problem caused by an inefficient retrieval pipeline will not be fixed by swapping the model, and misdiagnosing which layer is responsible wastes an optimization cycle without moving the metric. Step 39 is easy to skip and expensive to skip: an asset that has only ever run in its original context has not yet demonstrated it is actually reusable, only that it worked once; declaring it a platform standard on the strength of a single deployment is how organizations end up with "shared" components that quietly assume something specific to their first user. Step 40's reassessment before any expansion echoes the evidence-gating discipline of the whole methodology — expanding scope is itself a decision that deserves fresh evidence, not an assumption that what worked at the current scale will keep working at the next one.

## Primary artifacts

- Optimization Backlog

- Scale and Productization Assessment

- Reusable Asset Register

- Expanded Evaluation Pack

- Autonomy Evidence Pack

- Renewal Business Case

- Retirement Plan where applicable

The Scale and Productization Assessment is template 18 in [Risk and Scale Templates](../tools/05-risk-and-scale-templates.md#18-scale-and-productization-assessment), and it is worth reading before this phase's productization decisions are made rather than after, because its fields — demand, repeatability, contract stability, tenancy model, unit economics at scale — are precisely the evidence step 38's classification decision needs and step 40's expansion decision depends on.

> **DECISION OUTCOME** Scale and Renewal Review: improve, replicate, productize, renew, redesign or retire.

## Entry and exit conditions

| **Entry condition**                                                                   | **Exit condition**                                                                     |
|-------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| Sufficient production evidence exists to diagnose improvements or test repeatability. | A tested improvement, scale decision, reusable asset or retirement action is approved. |

The entry condition's emphasis on "sufficient production evidence" is a reminder that this phase draws on Phase 5, not around it — a system that has not yet accumulated a meaningful operating history has nothing reliable for Phase 6 to optimize or generalize from, and attempting this phase early usually means optimizing against noise.

## Tailoring guidance

Small organizations may reuse through templates and managed services. Large enterprises should establish product owners, service levels, version support and federated governance for shared components.

The scale side of this phase is where organizational size genuinely changes the right answer, more than in most other phases. A small organization rarely has the volume of deployments to justify a formal internal platform team; reuse there looks like good templates, shared configuration and managed-service defaults, carried forward by discipline rather than by dedicated ownership. A large enterprise running many deployments against shared components needs those components to behave like products — with named owners, defined service levels, a supported version history and governance that spans the business units consuming them — because an informally maintained shared component at that scale becomes a single point of failure for everyone depending on it.

---

[← Previous: Chapter 11: Phase 5 — Operate & Assure](chapter-11-phase-5-operate-and-assure.md) · [Contents](../README.md) · [Next: Chapter 13: Decision Gates and Evidence Model →](chapter-13-decision-gates-and-evidence-model.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
