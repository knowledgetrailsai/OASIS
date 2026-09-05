<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 01: OASIS Executive Overview](chapter-01-oasis-executive-overview.md) · [Contents](../README.md) · [Next: Chapter 03: Enterprise AI Transformation Direction →](chapter-03-enterprise-ai-transformation-direction.md)

# Chapter 02: Methodology Foundations and Design Principles


> **CHAPTER PURPOSE** Establish the principles that keep the method outcome-led, evidence-driven, modular, risk-proportionate, technology-neutral and operationally accountable. Show how those principles are enforced, not just stated.

## Background and context

Chapter 1 defined what OASIS is and the problem it solves. This chapter explains why OASIS takes this shape, and what has to be true for an organization to trust it under pressure—a slipping deadline, a sponsor wanting to skip a gate, a vendor demo making evaluation feel unnecessary.

A methodology survives a real delivery timeline only if its principles are enforceable, and only if people can tell the difference between simplifying an artifact and removing the decision it protects. This chapter sets out the ten design principles that shape every later chapter, and the mandatory core those principles cannot compress away.

These principles are why Chapter 3 insists on bottom-up evidence alongside top-down ambition, why Chapter 4 lets an organization enter from five different starting points without fragmenting into five methods, and why Chapter 5 treats "stop" as a legitimate outcome. They also recur, made concrete and checkable, at the level of system architecture: the [OASIS Reference Architecture](../architecture/oasis-reference-architecture.md#architecture-principles) restates the same commitments as ten architecture principles with a named mechanism for checking each against a real system.

## Design principles

Ten principles hold the method together. Each one closes a failure mode the previous one leaves open.

Outcome before solution: begin with the measurable result and operational constraint, not a preferred model or vendor. Starting from the technology makes it easy to build something impressive that never moves a metric. System before model: the outcome depends on the whole intelligence system, so evaluation must cover context, tools, workflow, humans and controls, not model benchmarks alone.

Evidence before authority governs how trust is earned: release scope and autonomy expand only after representative and live evidence supports it. A system that performs well in a lab still has to prove itself in real production conditions first. Proportionate assurance follows the same logic outward: assurance depth tracks impact, autonomy, data sensitivity, exposure and scale, not organizational size.

Multiple entry points recognizes that strategy, business demand, technology experiments, regulatory needs and existing solutions all legitimately generate AI initiatives. Forcing every one through a strategy-first funnel wastes the energy that started them (Chapter 4 develops this at length). Vertical proof before horizontal scale keeps ambition honest: prove one end-to-end outcome path before adding channels, use cases, agents or business units. A shallow win replicated ten times is ten shallow failures waiting to surface.

Deterministic where possible checks the pull toward agentic sophistication by default: fixed rules and workflows should handle the parts of a problem where uncertainty adds no value, reserving agent judgment for genuine ambiguity. Production is the learning environment turns real exceptions, failures and overrides into evaluation cases and backlog items, letting a system improve after launch. Reuse what repeats standardizes platform services that recur across deployments—shared identity, retrieval, evaluation harnesses—while keeping the operational last mile, the part specific to one business context, configurable.

Exit is a valid outcome is the principle organizations struggle most to internalize, because stopping a funded initiative can feel like failure rather than discipline. OASIS treats it as discipline: when evidence no longer supports value, safety or economic viability, stopping, reframing or retiring is correct. A portfolio that never stops anything has stopped looking honestly at its evidence.

| **Principle**                          | **Practical interpretation**                                                                                              |
|----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| Outcome before solution                | Begin with the measurable result and operational constraint, not the preferred model or vendor.                           |
| System before model                    | Evaluate the model together with context, tools, workflow, humans, controls and runtime.                                  |
| Evidence before authority              | Increase release scope and autonomy only after representative and live evidence supports it.                              |
| Proportionate assurance                | Depth follows impact, autonomy, data sensitivity, exposure and scale—not organizational size alone.                       |
| Multiple entry points                  | Strategy, business demand, technology experiments, regulatory needs and existing solutions can all enter the same method. |
| Vertical proof before horizontal scale | Prove one end-to-end outcome path before adding channels, use cases, agents or business units.                            |
| Deterministic where possible           | Use fixed rules, validation and workflows where uncertainty adds no value; reserve agent judgment for genuine ambiguity.   |
| Production is the learning environment | Convert real exceptions, failures and overrides into evaluation cases and improvement backlog items.                      |
| Reuse what repeats                     | Standardize recurring platform services and components while keeping the operational last mile configurable.              |
| Exit is a valid outcome                | Stop, reframe or retire when evidence no longer supports value, safety or economic viability.                             |

## Mandatory core and selectable depth

Principles alone will not stop a team under pressure from simplifying past a critical decision. So OASIS pairs the ten principles with a concrete floor: every initiative must keep a minimal spine—an owned outcome, a representative evaluation, a defined system boundary, a risk classification, clear human authority, production acceptance criteria, outcome monitoring and a renewal decision. None of these eight elements is optional, and none is satisfied by a document that exists but is never used.

Above that floor, depth is optional and activated according to the initiative's actual profile. Formal regulatory engineering, multi-agent threat modelling, independent validation, disaster recovery planning and platform productization are real, sometimes substantial, bodies of work. A low-risk internal tool does not need to carry the same weight as a customer-facing, high-autonomy, regulated deployment.

The table below makes the boundary explicit: the left column is never negotiable, the right is added when impact, autonomy, sensitivity or scale warrants it.

| **Always required**                       | **Activated when justified**                                            |
|--------------------------------------------|-----------------------------------------------------------------------------|
| Outcome Charter and metric tree           | Formal Outcome Contract with commercial or cross-business commitments   |
| Representative cases and failure taxonomy | Independent assurance, red teaming and regulatory conformity assessment |
| Risk classification and autonomy boundary | High-risk impact assessment and jurisdiction-specific evidence pack     |
| Named business and service owners         | Federated governance and multiple operational service owners            |
| Basic trace, monitoring and fallback      | 24×7 SRE, disaster recovery and multi-region resilience                 |
| Continuation decision                     | Portfolio productization and platform transfer                          |

## OASIS quality test

There is one further test, separate from whether the mandatory artifacts exist: implementation is healthy when its artifacts improve decisions rather than merely document activity already completed.

A team that can trace from an outcome measure to the workflow behavior driving it, to the system trace that explains a failure, to the responsible layer, and to a tested fix, is running a live methodology. A team with the same documents but an unread Outcome Charter and an unconsulted failure taxonomy has the paperwork of OASIS without the discipline—usually the first thing worth fixing.

---

[← Previous: Chapter 01: OASIS Executive Overview](chapter-01-oasis-executive-overview.md) · [Contents](../README.md) · [Next: Chapter 03: Enterprise AI Transformation Direction →](chapter-03-enterprise-ai-transformation-direction.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
