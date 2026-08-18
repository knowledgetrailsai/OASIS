<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 01: OASIS Executive Overview](chapter-01-oasis-executive-overview.md) · [Contents](../README.md) · [Next: Chapter 03: Enterprise AI Transformation Direction →](chapter-03-enterprise-ai-transformation-direction.md)

# Chapter 02: Methodology Foundations and Design Principles

# Methodology Foundations and Design Principles

> **CHAPTER PURPOSE** Establish the principles that keep the method outcome-led, evidence-driven, modular, risk-proportionate, technology-neutral and operationally accountable, and show how those principles are enforced rather than merely stated.

## Background and context

Chapter 1 defined what OASIS is and the problem it exists to solve. This chapter answers the harder question: why does OASIS take the specific shape it takes, and what would have to be true for an organization to trust that shape under pressure—when a deadline is slipping, when a sponsor wants to skip a gate, when a vendor's demo makes the evaluation step feel like an unnecessary delay? Every methodology sounds reasonable in a slide. What separates a methodology that survives contact with a real delivery timeline from one that quietly erodes is whether its principles are actually enforceable, and whether the people applying them can tell the difference between simplifying an artifact and removing the decision the artifact was protecting. This chapter sets out both: the ten design principles that shape every subsequent chapter, and the mandatory core that those principles are not permitted to compress away.

These principles are not abstract preference. They are the reason Chapter 3's enterprise direction insists on bottom-up evidence alongside top-down ambition, the reason Chapter 4 lets an organization enter the method from five different starting points without fragmenting into five different methods, and the reason Chapter 5's portfolio logic treats "stop" as a legitimate outcome rather than a failure to be hidden. If you find yourself later in the handbook wondering why a chapter insists on a particular gate or a particular piece of evidence, the answer is almost always traceable back to one of the ten rows below.

It is also worth knowing, before reading the table, that these principles are not confined to the business and delivery layers of the method. They recur, made concrete and checkable, at the level of system architecture: the [OASIS Reference Architecture](../architecture/oasis-reference-architecture.md#architecture-principles) restates this same set of commitments—secure by design, evidence gated, progressively autonomous, outcome oriented and the rest—as ten architecture principles with a named mechanism for checking each one against a real system. A reader who wants to see what "evidence before authority" or "proportionate assurance" actually looks like once it has been translated into a component diagram, a control checklist and a named template should treat that document as this chapter's technical counterpart.

## Design principles

Ten principles hold the method together, and they are best read as a connected argument rather than an unordered checklist, because each one closes a failure mode that the previous one leaves open. Outcome before solution is the first and most load-bearing: it requires a team to begin with the measurable result and the operational constraint it must respect, not with a preferred model or a favored vendor, precisely because starting from the technology makes it easy to build something impressive that never moves a business metric. System before model follows directly from that: because the outcome depends on the whole intelligence system—context, tools, workflow, humans and controls, not the model in isolation—evaluation has to cover that whole system too, or a team ends up with excellent model benchmarks and an unreliable production service.

Evidence before authority is the principle that governs how trust is earned rather than assumed: release scope and autonomy expand only after representative and live evidence supports the expansion, which means a system that performs well in a lab evaluation still has to prove itself against real, messy production conditions before it is trusted with more consequential decisions. Proportionate assurance follows the same logic outward: the depth of assurance required tracks impact, autonomy, data sensitivity, exposure and scale—not the size of the organization running the initiative, so a small team running a high-stakes deployment does not get to claim a lighter assurance track just because it is a small team, and a large enterprise running a low-stakes internal tool is not obligated to build the heaviest possible governance apparatus around it.

Multiple entry points recognizes a practical reality this handbook takes seriously rather than fighting: strategy, business demand, technology experiments, regulatory needs and existing solutions all legitimately generate AI initiatives, and forcing every one of them through a strategy-first funnel before they can be recognized wastes the energy that got them started in the first place. Chapter 4 develops this principle at length. Vertical proof before horizontal scale is the discipline that keeps ambition honest: prove one end-to-end outcome path completely before adding channels, use cases, agents or business units, because a shallow win replicated ten times is ten shallow failures waiting to surface, while one deep, proven path is a template worth replicating.

Deterministic where possible is a check against the temptation to reach for agentic sophistication by default: fixed rules, validation and workflows should handle the parts of the problem where uncertainty adds no value, and agent judgment should be reserved for genuine ambiguity, because every additional degree of dynamic judgment is also an additional surface for unpredictable behavior that then has to be governed. Production is the learning environment treats real exceptions, failures and human overrides not as noise to be tolerated but as raw material: they become evaluation cases and improvement backlog items, which is the mechanism that lets a system actually get better after launch instead of merely being maintained. Reuse what repeats asks an organization to standardize the platform services and components that recur across deployments—shared identity, shared retrieval, shared evaluation harnesses—while keeping the last operational mile, the part that is genuinely specific to one business context, configurable rather than forced into a one-size template.

The final principle, exit is a valid outcome, is the one organizations most often struggle to internalize, because stopping a funded initiative can feel like an admission of failure rather than a demonstration of discipline. OASIS treats it as the latter: when evidence no longer supports value, safety or economic viability, stopping, reframing or retiring the initiative is the methodologically correct move, and a portfolio that never stops anything is not a portfolio with an unusually good hit rate—it is a portfolio that has stopped looking honestly at its evidence.

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

Principles alone do not stop an under-pressure team from simplifying its way past a critical decision, so OASIS pairs the ten principles with a concrete floor: every initiative, regardless of size or ambition, must retain a minimal spine consisting of an owned outcome, a representative evaluation, a defined system boundary, a risk classification, clear human authority, production acceptance criteria, outcome monitoring and a renewal decision. None of these eight elements is optional, and none of them can be satisfied by a document that exists but is never used—each one has to actively inform a decision, or it is not doing its job.

Above that floor, depth is genuinely optional and should be activated according to the initiative's actual profile rather than applied uniformly. Formal regulatory engineering, multi-agent threat modelling, independent validation, disaster recovery planning and platform productization are all real, sometimes substantial, bodies of work, and OASIS does not ask a low-risk internal tool to carry the same weight as a customer-facing, high-autonomy, regulated deployment. The table below makes the boundary explicit: the left column is never negotiable, and the right column is added when the initiative's impact, autonomy, sensitivity or scale actually warrants it.

| **Always required**                       | **Activated when justified**                                            |
|--------------------------------------------|---------------------------------------------------------------------------|
| Outcome Charter and metric tree           | Formal Outcome Contract with commercial or cross-business commitments   |
| Representative cases and failure taxonomy | Independent assurance, red teaming and regulatory conformity assessment |
| Risk classification and autonomy boundary | High-risk impact assessment and jurisdiction-specific evidence pack     |
| Named business and service owners         | Federated governance and multiple operational service owners            |
| Basic trace, monitoring and fallback      | 24×7 SRE, disaster recovery and multi-region resilience                 |
| Continuation decision                     | Portfolio productization and platform transfer                          |

## OASIS quality test

There is one further test worth applying to any implementation of this method, separate from whether the mandatory artifacts exist: a methodology implementation is healthy when its artifacts improve decisions rather than merely document activity that has already happened. A team that can point from an outcome measure to the specific workflow behavior driving it, from a workflow failure to the system trace that explains it, from that trace to the layer of the system responsible, and from the diagnosis to a change that was actually tested before release, is running a live methodology. A team that produces the same documents but cannot walk that chain—whose Outcome Charter sits unread after sign-off, whose failure taxonomy nobody consults when something breaks—has the paperwork of OASIS without the discipline, and that gap is usually the first thing worth fixing before adding any further process.

---

[← Previous: Chapter 01: OASIS Executive Overview](chapter-01-oasis-executive-overview.md) · [Contents](../README.md) · [Next: Chapter 03: Enterprise AI Transformation Direction →](chapter-03-enterprise-ai-transformation-direction.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
