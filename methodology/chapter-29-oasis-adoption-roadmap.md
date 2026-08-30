<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 28: Scaling and Productization](chapter-28-scaling-and-productization.md) · [Contents](../README.md) · [Next: Chapter 30: Tailoring OASIS →](chapter-30-tailoring-oasis.md)

# Chapter 29: OASIS Adoption Roadmap

# OASIS Adoption Roadmap

> **CHAPTER PURPOSE** Provide a practical 90-day start and a maturity path for organizations establishing their first portfolio, pod, governance and platform foundations.

*Figure 5. OASIS retains one lifecycle while increasing assurance depth.*

## Background and context

The previous three chapters describe how a mature OASIS practice measures itself, runs its delivery rhythm and scales what it builds. This chapter is for the organization that has none of that yet, and is deciding this quarter how to actually begin. The gap between reading a methodology and adopting one is where most transformation efforts quietly stall: a sponsor reads the framework, agrees with it, then faces the harder question of what the first concrete Monday of adoption looks like. This chapter is that answer, compressed into a 90-day start and a five-level maturity path.

It is deliberately less prescriptive about engineering and governance detail than the chapters around it, because a first adoption has to survive contact with organizational reality — existing teams, tools and politics. This chapter asks an organization to get sequence and restraint right early: pick one bounded outcome rather than several ambitious ones, build the smallest team that can deliver it, and resist two temptations that derail most first attempts — moving to production before the hypothesis is proven, and building permanent platform infrastructure before there is real deployment demand to justify it. Chapter 28 shares that second temptation in reverse: it assumes reuse demand already exists and asks how to serve it well. This chapter is about not building for reuse demand that has not yet materialized.

The roadmap connects most directly to the next and final chapter of this pair. [Chapter 30 — Tailoring OASIS](chapter-30-tailoring-oasis.md) supplies the framework for deciding how much of the full methodology a given initiative needs, and the 90-day plan below is one worked example of that framework applied to a first adoption — light artifacts, borrowed specialist capability, and a deliberately bounded first outcome rather than the full weight of an enterprise-scale program. Organizations that have already completed a reference-architecture exercise may also find it useful to read the [OASIS Reference Architecture's tailoring section](../architecture/oasis-reference-architecture.md#5-tailoring-this-architecture) alongside this chapter, since it applies the same tailoring logic to system architecture.

## First 90 days

Ninety days is enough time to prove or disprove a genuine hypothesis about intelligence applied to a real workflow, but not enough to build a platform. Organizations that try to do the latter within this window usually end up doing neither well.

The first thirty days are about framing: assessing organizational maturity honestly, selecting one outcome material enough to matter and bounded enough to finish, naming a sponsor, an owner and a pod, and setting policy minimums so the work has guardrails from day one. This window produces an Outcome Charter, an initial portfolio entry, a risk track and an operating cadence.

Days thirty-one through sixty shift from framing to testing. The pod observes the actual work being done today, builds evaluation cases from real examples, constructs a vertical slice end to end, and identifies platform and data gaps. This window does not produce a working system yet — it produces a validated hypothesis, a first-draft failure taxonomy, and an honest recommendation on whether production investment is justified. A team that skips or rushes through this window makes the mistake [Chapter 8's Discover & Validate phase](chapter-08-phase-2-discover-and-validate.md) warns against: mistaking a promising demonstration for a tested hypothesis.

The final thirty days, sixty-one through ninety, engineer a controlled pilot on the strength of that evidence: tracing, controls, a runbook and an activation plan, plus a platform backlog for whatever shared capability the pilot revealed a genuine need for. The output is a pilot-ready service, an evidence gate the organization can stand behind, and a shared capability roadmap grounded in what the first ninety days actually showed.

| **Window** | **Priority actions**                                                                                            | **Expected output**                                                   |
|------------|-------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|
| Days 1–30  | Assess maturity; select one material but bounded outcome; name sponsor, owner and pod; create policy minimums.   | Outcome Charter, initial portfolio, risk track and operating cadence.     |
| Days 31–60 | Observe work; build evaluation cases and vertical slice; identify platform and data gaps.                        | Validated hypothesis, failure taxonomy and production recommendation.     |
| Days 61–90 | Engineer a controlled pilot; implement tracing, controls, runbook and activation plan; define platform backlog.  | Pilot-ready service, evidence gate and shared capability roadmap.         |

## Build the first pod

The instinct to build something large and permanent for a first adoption is understandable, and usually wrong. OASIS recommends starting with a small integrated team assembled around a real business owner — someone who actually owns the outcome the pod is chasing, not a proxy sponsor several layers removed. Specialist capability in risk, security and platform engineering should be borrowed for this first effort rather than hired or reassigned permanently: a large standing structure built before the organization has proven it can deliver one outcome is a bet on capability not yet demonstrated at that scale.

Choosing the right first opportunity matters as much as choosing the right team. The target should have measurable value, available cases for the vertical slice to work with, reachable users so adoption can be genuinely tested, and manageable integration so the pod is not fighting enterprise plumbing before validating the hypothesis. Avoid both extremes: an isolated demo that never touches a real workflow proves nothing transferable, and the most critical process in the enterprise carries too much consequence and friction to be a sensible first bet. Better to prove the methodology on something real but recoverable.

## Maturity model

Adoption does not stop at the first pilot. It progresses through five levels, each with a different characteristic failure mode and next focus.

Level 1, Experimental, is where most organizations start without realizing it — disconnected tools and proofs of concept, with success defined in purely technical terms because no one has yet connected the work to a business outcome. The next focus is establishing outcomes, an initial inventory, basic risk practice and evaluation discipline.

Level 2, Repeatable, is reached once the organization has a common lifecycle, working templates and genuinely controlled pilots. The next focus is production ownership, automation and real measurement — moving from "we can run a pilot" to "we can run one someone is accountable for afterward."

Level 3, Managed, adds a portfolio view, platform services, AgentOps discipline and regular outcome reviews. The next focus shifts to reuse, federated governance and economic accountability.

Level 4, Scaled, is where multiple businesses reuse a governed capability rather than each building their own version — the payoff of getting Chapter 28's scaling discipline right. The next focus becomes optimization, autonomy evidence, and capability transfer between businesses.

Level 5, Adaptive, is the level few organizations reach: production learning continuously renews strategy, platform and workforce as ordinary operation. The next focus is sustained innovation balanced against assurance, and retiring what no longer earns its keep.

| **Level**        | **Characteristic**                                                        | **Next focus**                                             |
|--------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------|
| 1 — Experimental | Disconnected tools and PoCs; success defined technically.                 | Outcomes, inventory, basic risk and evaluation.                 |
| 2 — Repeatable   | Common lifecycle, templates and controlled pilots.                        | Production ownership, automation and measurement.               |
| 3 — Managed      | Portfolio, platform services, AgentOps and outcome reviews.               | Reuse, federated governance and economics.                      |
| 4 — Scaled       | Multiple businesses reuse governed capability.                            | Optimization, autonomy evidence and capability transfer.        |
| 5 — Adaptive     | Production learning continuously renews strategy, platform and workforce. | Sustained innovation, assurance and retirement discipline.      |

## Common adoption risks

Most first adoptions fail not because the methodology was wrong, but because a predictable organizational pattern took hold before anyone noticed.

A central platform gets built without any deployment demanding it, absorbing budget a real pilot needed. Local proofs of concept proliferate with no ownership and no shared controls, each impressive and collectively ungovernable. Use-case volume gets treated as outcome evidence — a growing count of pilots substituting for proof that any of them work. Governance shows up late and can only function as a release blocker rather than the guardrail it was meant to be.

Business teams delegate outcome ownership to technology, breaking the accountability the measurement framework in Chapter 26 depends on. Successful prototypes get pushed into production without the service engineering — runbooks, controls, monitoring — that production requires, and the resulting incidents get treated as a surprise rather than a predictable consequence. FDOE pods, built to be temporary, become permanent bespoke delivery teams because no one enforced the transfer discipline Chapter 28 describes. And savings get claimed without measuring failure, rework or intervention cost — the exact false confidence Chapter 26's balanced scorecard exists to prevent.

- Central platform built without deployment demand.

- Local PoCs proliferate without ownership or shared controls.

- Use-case volume substitutes for outcome evidence.

- Governance appears late and becomes a release blocker.

- Business teams delegate outcome ownership to technology.

- Successful prototypes are pushed into production without service engineering.

- FDOE pods become permanent bespoke delivery teams.

- Savings are claimed without measuring failure, rework or intervention.

---

[← Previous: Chapter 28: Scaling and Productization](chapter-28-scaling-and-productization.md) · [Contents](../README.md) · [Next: Chapter 30: Tailoring OASIS →](chapter-30-tailoring-oasis.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
