<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 04: Multiple Entry Paths and Configurable Depth](chapter-04-multiple-entry-paths-and-configurable-depth.md) · [Contents](../README.md) · [Next: Chapter 06: OASIS Operating Model and Decision Rights →](chapter-06-oasis-operating-model-and-decision-rights.md)

# Chapter 05: Opportunity Portfolio and Transformation Horizons

# Opportunity Portfolio and Transformation Horizons

> **CHAPTER PURPOSE** Select and balance AI opportunities across assist, enhance, reconfigure and transform horizons using value, feasibility, risk and foundational readiness, and give teams a shared, testable way to frame an opportunity before it enters that assessment.

## Background and context

Chapter 4 explained how an initiative, regardless of where it started, gets normalized onto common ground. This chapter picks up from that point and answers the next question a portfolio owner actually faces: given a normalized set of candidate opportunities, and given the four transformation horizons Chapter 3 introduced, how does an organization decide what to fund, what to defer, and what to stop—without either chasing every plausible use case or over-committing to a handful of ambitious bets before the evidence exists to support them? The honest answer is that most organizations do this badly not because they lack judgment, but because they lack a shared, comparable way of expressing what an opportunity actually is. A list of use cases with no common structure cannot be compared, prioritized or balanced; it can only be argued about.

This chapter supplies that structure in two parts: a disciplined hypothesis form for expressing any single opportunity, and a set of assessment dimensions and continuation logic for comparing opportunities against each other and against the portfolio's overall balance. Readers who want the working templates behind this chapter—the actual documents a team fills in to run an Opportunity Assessment, an Outcome Charter, an Outcome Contract, an Outcome Metric Tree and a Value and Risk Case—should turn to the [Outcome and Portfolio Templates](../tools/01-outcome-and-portfolio-templates.md), which operationalize everything described here into fillable form. And for the enterprise-wide view of where these opportunities sit within the organization's operating model—the capability map that Chapter 3 referenced only briefly—[Architecture Perspective 1: Business and Capability Architecture](../architecture/perspective-01-business-and-capability-architecture.md) gives the structural counterpart to this chapter's opportunity-by-opportunity view, useful once a portfolio owner needs to see the same opportunities laid out across the enterprise's capability map rather than one at a time.

## Opportunity framing

The single most common reason a promising-sounding AI use case fails to survive contact with a portfolio review is that it was never actually a testable claim—it was a description of a technology applied to a domain, with no baseline, no target, and no stated mechanism for why the intervention should work. OASIS insists that every opportunity be expressed as an outcome hypothesis instead: for a defined population and workflow, a specified intelligence capability is expected to change a measurable outcome within stated guardrails. That discipline is not bureaucratic overhead; it is what prevents a portfolio from becoming a disconnected list of features masquerading as a strategy, because a hypothesis can be evaluated, disproven, or refined in a way that a feature description cannot.

> **HYPOTHESIS FORM** If we provide \[intelligence capability\] at \[decision/work step\] for \[population\], then \[outcome\] will move from \[baseline\] to \[target\] because \[causal mechanism\], while \[guardrails\] remain within limits.

Notice what the form forces a proposer to commit to before an opportunity is taken seriously: a specific population rather than "users" in the abstract, a specific point in the workflow rather than a vague claim about improving "the process," a stated baseline that can be checked against reality, a target that makes success falsifiable, an actual causal mechanism rather than an assumption that intelligence automatically produces value, and guardrails that acknowledge the intervention has limits it must respect. An opportunity that cannot be filled into this form honestly is usually not ready for portfolio consideration yet—not because the idea is bad, but because nobody has done the thinking the form requires.

## Portfolio assessment

Once an opportunity is framed as a hypothesis, it can be assessed against eight dimensions that, taken together, cover the questions a portfolio owner actually needs answered before committing funding. Outcome value asks whether the result is strategically material, whether a credible baseline exists to measure against, and—often the question people are least comfortable asking directly—who benefits from success and who bears the cost if the initiative fails. Intelligence fit asks a more technical question: does the underlying work actually contain the ambiguity, unstructured information, prediction, generation or dynamic decision-making that justifies an intelligence-based approach, or would a simpler deterministic solution do the job better and more cheaply? Workflow leverage tests whether the intelligence can genuinely alter a decision or action, or whether it will sit as an isolated recommendation nobody is obligated to act on—the latter being a common and quietly fatal pattern in AI initiatives that never move a real metric.

Data and knowledge asks the unglamorous but decisive question of whether representative, authorized and sufficiently current inputs actually exist, because no amount of downstream engineering compensates for data that is not there. Adoption asks whether the affected users will actually change their behavior as a result of the intervention, and whether incentives, trust and task redesign have been addressed—an intelligence system that is technically correct but that nobody trusts enough to use has not delivered an outcome. Risk and regulation asks what harms, rights, obligations and authority limits apply, connecting this assessment forward to the operating model and decision rights described in Chapter 6. Economics asks the plain commercial question of whether expected value exceeds the full cost of building, running, and handling the failures and interventions the system will inevitably generate—not just the build cost alone. And reuse and platform asks whether the opportunity creates a recurring connector, knowledge service, evaluation pattern or control that will pay dividends across future deployments, which is the dimension most likely to be underweighted by a team focused only on its own initiative.

| **Dimension**       | **Questions**                                                                                                 |
|-----------------------|-------------------------------------------------------------------------------------------------------------------|
| Outcome value       | Is the result strategically material? Is a baseline available? Who benefits and who bears failure cost?       |
| Intelligence fit    | Does the work contain ambiguity, unstructured information, prediction, generation or dynamic decision-making? |
| Workflow leverage   | Can intelligence alter a decision or action, or will it remain an isolated recommendation?                    |
| Data and knowledge  | Are representative, authorized and sufficiently current inputs available?                                     |
| Adoption            | Will affected users change behavior? Are incentives, trust and task redesign addressed?                       |
| Risk and regulation | What harms, rights, obligations and authority limits apply?                                                   |
| Economics           | Is expected value greater than build, run, failure and intervention cost?                                     |
| Reuse and platform  | Does the opportunity create a recurring connector, knowledge service, evaluation or control pattern?          |

The [Opportunity Assessment template](../tools/01-outcome-and-portfolio-templates.md#1-opportunity-assessment) walks a team through exactly these eight dimensions in fillable form, and is the practical starting point for turning this section into a working document rather than a mental checklist.

## Portfolio balance

Assessing opportunities individually is necessary but not sufficient; a portfolio owner also has to look across the full set and manage its shape. A healthy portfolio deliberately mixes a larger number of quick H1 and H2 improvements—which build credibility, generate near-term value and surface operational learning quickly—with a smaller number of H3 and H4 transformations, which take longer to prove but are where the structural upside actually lives. It includes both business-facing outcomes and shared foundational investments, and it actively avoids excessive concentration in a single vendor, a single model, a single data source, or a single category of regulatory risk, because concentration of any of those kinds turns a portfolio-level diversification benefit into a portfolio-level single point of failure.

Dependencies deserve particular attention, and OASIS asks that they be made explicit rather than discovered midway through delivery. A shared customer identity service, a document ingestion pipeline, or an evaluation platform can unlock several deployments at once, and treating that kind of dependency as a portfolio-level capability—funded and owned as such—produces a much better outcome than letting it be built once, quietly, inside whichever project happened to need it first. The latter pattern is how organizations end up with three incompatible identity services and no shared evaluation harness at all, discovered only when someone tries to reuse one project's work in another.

## Continuation logic

Every opportunity in the portfolio eventually needs one of five decisions applied to it, and OASIS is deliberate about naming all five as legitimate outcomes rather than treating only "prioritize" as success. An opportunity is prioritized when its outcome is material, genuinely influenceable by the proposed intervention, and clearly owned. It is validated further when the remaining uncertainty is primarily technical, workflow, adoption or economic in nature—uncertainty that more evidence can actually resolve. It is deferred when foundational data, policy or integration dependencies dominate the picture, because pushing ahead against an unresolved foundational gap rarely produces a good outcome no matter how well the surrounding work is executed. It is directed to buy or partner when the underlying capability is non-differentiating and available externally at acceptable risk—building it in-house would simply be reinventing something the market already sells well. And it is stopped when the causal link between the intervention and the outcome turns out to be weak, when the evidence needed to justify continuing cannot realistically be assembled, or when risk cannot be reduced to an acceptable level—echoing Chapter 2's principle that exit is a valid outcome, applied here at the level of an individual opportunity rather than an entire methodology.

- Prioritize when the outcome is material, influenceable and owned.
- Validate when uncertainty is primarily technical, workflow, adoption or economic.
- Defer when foundational data, policy or integration dependencies dominate.
- Buy or partner when capability is non-differentiating and externally available with acceptable risk.
- Stop when outcome causality is weak, evidence cannot be assembled, or risk cannot be reduced to an acceptable level.

---

[← Previous: Chapter 04: Multiple Entry Paths and Configurable Depth](chapter-04-multiple-entry-paths-and-configurable-depth.md) · [Contents](../README.md) · [Next: Chapter 06: OASIS Operating Model and Decision Rights →](chapter-06-oasis-operating-model-and-decision-rights.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
