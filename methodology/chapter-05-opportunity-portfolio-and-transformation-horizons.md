<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 04: Multiple Entry Paths and Configurable Depth](chapter-04-multiple-entry-paths-and-configurable-depth.md) · [Contents](../README.md) · [Next: Chapter 06: OASIS Operating Model and Decision Rights →](chapter-06-oasis-operating-model-and-decision-rights.md)

# Chapter 05: Opportunity Portfolio and Transformation Horizons

> **Implementation companion:** [Nexus](https://github.com/knowledgetrailsai/Nexus) — the opportunity catalog (function × domain × use case) this chapter's portfolio thinking is built from.

# Opportunity Portfolio and Transformation Horizons

> **CHAPTER PURPOSE** Select and balance AI opportunities across assist, enhance, reconfigure and transform horizons using value, feasibility, risk and foundational readiness. Give teams a shared, testable way to frame an opportunity before it enters that assessment.

## Background and context

Chapter 4 explained how an initiative gets normalized onto common ground. This chapter answers the next question a portfolio owner faces: given candidate opportunities and the four transformation horizons Chapter 3 introduced, how does an organization decide what to fund, defer or stop, without chasing every use case or over-committing before the evidence exists?

Most organizations do this badly not from lack of judgment but because they lack a shared, comparable way of expressing what an opportunity is. A list of use cases with no common structure cannot be compared; it can only be argued about.

This chapter supplies that structure in two parts: a hypothesis form for expressing any single opportunity, and assessment dimensions and continuation logic for comparing opportunities. For the working templates behind this chapter—Opportunity Assessment, Outcome Charter, Outcome Contract, Outcome Metric Tree and Value and Risk Case—see the [Outcome and Portfolio Templates](../tools/01-outcome-and-portfolio-templates.md). For the enterprise-wide view of where opportunities sit within the operating model, see [Architecture Perspective 1: Business and Capability Architecture](../architecture/perspective-01-business-and-capability-architecture.md).

## Opportunity framing

The most common reason a promising AI use case fails to survive a portfolio review is that it was never a testable claim. It was a description of a technology applied to a domain, with no baseline, target or stated mechanism for why it should work.

OASIS insists that every opportunity be expressed as an outcome hypothesis instead: for a defined population and workflow, a specified intelligence capability is expected to change a measurable outcome within stated guardrails. A hypothesis can be evaluated, disproven or refined in a way a feature description cannot.

> **HYPOTHESIS FORM** If we provide \[intelligence capability\] at \[decision/work step\] for \[population\], then \[outcome\] will move from \[baseline\] to \[target\] because \[causal mechanism\], while \[guardrails\] remain within limits.

The form forces a proposer to commit to a specific population rather than "users" in the abstract, and a specific point in the workflow rather than a vague claim about improving "the process." It requires a checkable baseline, a falsifiable target, an actual causal mechanism, and guardrails that acknowledge the intervention's limits. An opportunity that cannot be filled into this form honestly usually is not ready for portfolio consideration—not because the idea is bad, but because nobody has done the thinking the form requires.

## Portfolio assessment

Once framed as a hypothesis, an opportunity is assessed against eight dimensions.

Outcome value asks whether the result is strategically material, whether a credible baseline exists, and who benefits versus who bears the cost of failure. Intelligence fit asks whether the work actually contains the ambiguity, unstructured information, prediction, generation or dynamic decision-making that justifies an intelligence-based approach, or whether a simpler deterministic solution would do better and cheaper. Workflow leverage tests whether intelligence can genuinely alter a decision or action, or will sit as an isolated recommendation nobody acts on—a common, quietly fatal pattern.

Data and knowledge asks whether representative, authorized and current inputs actually exist, since no downstream engineering compensates for missing data. Adoption asks whether affected users will actually change behavior, and whether incentives, trust and task redesign have been addressed—a technically correct system nobody trusts has not delivered an outcome. Risk and regulation asks what harms, rights, obligations and authority limits apply, connecting forward to Chapter 6. Economics asks whether expected value exceeds the full cost of building, running and handling failures, not just the build cost. Reuse and platform asks whether the opportunity creates a recurring connector, knowledge service or control that pays dividends across future deployments—the dimension most often underweighted by a team focused only on its own initiative.

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

The [Opportunity Assessment template](../tools/01-outcome-and-portfolio-templates.md#1-opportunity-assessment) walks a team through these eight dimensions in fillable form, and is the practical starting point for turning this section into a working document.

## Portfolio balance

Assessing opportunities individually is necessary but not sufficient; a portfolio owner also has to manage the shape of the full set. A healthy portfolio mixes a larger number of quick H1 and H2 improvements, which build credibility and surface learning quickly, with a smaller number of H3 and H4 transformations, which take longer but carry the structural upside. It includes both business-facing outcomes and shared foundational investments, and avoids excessive concentration in a single vendor, model, data source or regulatory risk category, since concentration turns a diversification benefit into a single point of failure.

Dependencies deserve particular attention, and OASIS asks that they be made explicit rather than discovered midway through delivery. A shared customer identity service, a document ingestion pipeline, or an evaluation platform can unlock several deployments at once. Treating that dependency as a portfolio-level capability—funded and owned as such—beats letting it be built once, quietly, inside whichever project needed it first. The latter pattern is how organizations end up with three incompatible identity services and no shared evaluation harness.

## Continuation logic

Every opportunity eventually needs one of five decisions, and OASIS names all five as legitimate outcomes rather than treating only "prioritize" as success: prioritized when material, influenceable and clearly owned; validated further when remaining uncertainty is technical, workflow, adoption or economic and more evidence can resolve it; deferred when foundational data, policy or integration dependencies dominate; directed to buy or partner when the capability is non-differentiating and available externally at acceptable risk; or stopped when causality is weak, evidence cannot be assembled, or risk cannot be reduced acceptably—echoing Chapter 2's principle that exit is a valid outcome, applied here to a single opportunity.

- Prioritize when the outcome is material, influenceable and owned.
- Validate when uncertainty is primarily technical, workflow, adoption or economic.
- Defer when foundational data, policy or integration dependencies dominate.
- Buy or partner when capability is non-differentiating and externally available with acceptable risk.
- Stop when outcome causality is weak, evidence cannot be assembled, or risk cannot be reduced to an acceptable level.

---

[← Previous: Chapter 04: Multiple Entry Paths and Configurable Depth](chapter-04-multiple-entry-paths-and-configurable-depth.md) · [Contents](../README.md) · [Next: Chapter 06: OASIS Operating Model and Decision Rights →](chapter-06-oasis-operating-model-and-decision-rights.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
