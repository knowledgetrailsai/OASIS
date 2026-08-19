<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 05: Opportunity Portfolio and Transformation Horizons](chapter-05-opportunity-portfolio-and-transformation-horizons.md) · [Contents](../README.md) · [Next: Part II: The OASIS Lifecycle →](part-ii-the-oasis-lifecycle.md)

# Chapter 06: OASIS Operating Model and Decision Rights

# OASIS Operating Model and Decision Rights

> **CHAPTER PURPOSE** Define how enterprise leadership, business domains, platform teams, governance functions, forward-deployed pods and service operations share accountability, and close the gap that decision rights left ambiguous elsewhere in the method most often cause in practice.

## Background and context

Chapters 3 through 5 described what an enterprise should fund, how initiatives enter the method, and how a portfolio should be assessed and balanced. None of that answers the question that determines whether any of it works: when a decision needs to be made—commit funding, release to production, expand autonomy, retire a service—who has the authority, and what evidence do they need first? Ambiguous decision rights are one of the most common reasons AI initiatives stall even after clearing every other gate. A model owner ends up making a business call by default because nobody else was positioned to; a sponsor approves a release without the technical evidence to know if it is safe. This chapter closes Part I by making the operating layers and decision rights explicit, so Part II's lifecycle has a clear answer, at every gate, to "accountable to whom, on what evidence."

The layered operating model below and the decision-rights table that follows are best read together: the layers describe who is broadly accountable for what, while the decision-rights table pins specific decisions to specific roles and evidence requirements. For the technical counterpart—how agents are typed and where an agent's authority stops and a human's accountability begins—see [Architecture Perspective 2: Agent Architecture](../architecture/perspective-02-agent-architecture.md). For tracing the regulatory obligations in this chapter's decision-rights table to external frameworks, see the [Regulatory and Standards Framework Alignment Index](../references/regulatory-framework-alignment-index.md).

## Operating layers

OASIS distributes accountability across seven layers, deliberately rather than incidentally—each exists because collapsing two of them together has a predictable failure mode. Enterprise leadership carries the AI ambition, investment envelope, enterprise outcomes and risk appetite—the layer Chapter 3 addressed directly. An AI Transformation Office or Center of Excellence sits below it, holding the portfolio, standards, capability building, governance coordination and value realization—the connective layer that keeps enterprise ambition from being reinterpreted differently by every business unit. The business domain owns the problem itself: process decisions, users, adoption, and the business outcome, which is why Chapter 5 insists on a named business owner.

The enterprise intelligence platform layer owns the reusable model, context, knowledge, tool, evaluation, security and runtime services that deployments draw on rather than rebuild—the layer Chapter 3's platform row and Chapter 2's reuse-what-repeats principle point toward. A forward-deployed pod carries operational discovery, vertical delivery, integration, activation and learning transfer back into the platform and portfolio—typically the layer turning an outcome hypothesis into a working system. Service operations owns reliability, support, incidents, changes, assurance and ongoing service economics once something is live—the layer that makes the "managed outcome service" from Chapter 1 durable rather than a launch-day claim. An independent risk or assurance function provides challenge, review and evidence validation wherever risk warrants a genuinely separate set of eyes.

| **Layer**                        | **Primary accountability**                                                                |
|-------------------------------------|-----------------------------------------------------------------------------------------------|
| Enterprise leadership            | AI ambition, investment envelope, enterprise outcomes and risk appetite.                  |
| AI Transformation Office / CoE   | Portfolio, standards, capability building, governance coordination and value realization. |
| Business domain                  | Problem ownership, process decisions, users, adoption and business outcomes.              |
| Enterprise intelligence platform | Reusable model, context, knowledge, tool, evaluation, security and runtime services.      |
| Forward-deployed pod             | Operational discovery, vertical delivery, integration, activation and learning transfer.  |
| Service operations               | Reliability, support, incidents, changes, assurance and service economics.                |
| Independent risk / assurance     | Challenge, review and evidence validation where risk warrants separation.                 |

## Decision rights

Naming the layers is only half the job. OASIS also separates four kinds of authority easily blurred together—outcome ownership, technical service ownership, model or platform stewardship, and risk acceptance—and assigns them to named roles rather than inferring them from whoever has technical control of the system. No model owner may become the de facto owner of a business decision simply because they are closest to the system. Capability is not authority: a methodology that lets the two collapse hands governance to whoever built the tool, not whoever is accountable for its consequences.

The table below pins six recurring decisions to an accountable role and the evidence required. Committing to an outcome sits with the Business Outcome Owner, on a baseline, metric tree, value logic, scope and guardrails—the elements Chapter 1's outcome-contract construct and Chapter 5's hypothesis form both require. Proceeding to production engineering is a joint call between the Outcome Owner and the Product or Service Owner, on a validated vertical slice, failure taxonomy, and an honest accounting of risk and economics—not a demo. Releasing to live use sits with the Service Owner, with risk acceptance added where applicable, requiring production readiness, acceptance tests, a fallback path and a runbook.

Increasing autonomy is assigned to the business authority owner rather than engineering, requiring live quality, override, incident, edge-case and control evidence: autonomy expands on what the system has actually done in production, not confidence in its design. Scaling or productizing sits with the Portfolio or Platform Owner, evidenced by repeatability, economics, demand and a clear isolation of configurable versus fixed elements. Retirement sits jointly with the Outcome and Service Owners, triggered by declining value, unacceptable risk, an available replacement, or a scheduled lifecycle decision—a legitimate outcome, as Chapter 2 established, not a failure to avoid.

| **Decision**                      | **Accountable role**                             | **Evidence expected**                                                    |
|--------------------------------------|-----------------------------------------------------|--------------------------------------------------------------------------|
| Commit to outcome                 | Business Outcome Owner                           | Baseline, metric tree, value logic, scope and guardrails.                |
| Proceed to production engineering | Outcome Owner with Product/Service Owner         | Validated vertical slice, failure taxonomy, risk and economics.          |
| Release to live use               | Service Owner with Risk acceptance as applicable | Production readiness, acceptance tests, fallback and runbook.            |
| Increase autonomy                 | Business authority owner                         | Live quality, override, incident, edge-case and control evidence.        |
| Scale or productize               | Portfolio / Platform Owner                       | Repeatability, economics, demand and isolation of configurable elements. |
| Retire                            | Outcome and Service Owners                       | Declining value, unacceptable risk, replacement or lifecycle decision.   |

## Funding model

Decision rights and funding are two sides of the same accountability structure, and OASIS lets funding evolve across the horizons rather than committing a single budget line for an initiative's life. Discovery funding is scoped narrowly to test genuine uncertainty—small enough that stopping is easy and consequence-free. Production funding creates the actual service once that uncertainty resolves in the initiative's favor. Run funding sustains outcomes on an ongoing basis, since a managed outcome service does not end at launch. Platform funding productizes capability proven repeatedly across deployments, converting project-specific spend into a shared enterprise asset.

Continuation is tied to evidence and learning, not sunk-cost protection: an initiative earns its next funding tranche because of what the evidence says it is worth spending on, not what has already been spent. Shared services should carry transparent allocation logic, so a local deployment can compare consuming a shared capability against building its own honestly, rather than treating the shared service as a free good or an opaque tax. With decision rights and funding explicit, Part II turns from how OASIS is organized to how it is run, phase by phase, beginning with Engage & Align.

---

[← Previous: Chapter 05: Opportunity Portfolio and Transformation Horizons](chapter-05-opportunity-portfolio-and-transformation-horizons.md) · [Contents](../README.md) · [Next: Part II: The OASIS Lifecycle →](part-ii-the-oasis-lifecycle.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
