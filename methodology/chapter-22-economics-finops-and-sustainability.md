<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 21: Deployment, Operations and AgentOps](chapter-21-deployment-operations-and-agentops.md) · [Contents](../README.md) · [Next: Part IV: Delivery and Enterprise Enablement →](part-iv-delivery-and-enterprise-enablement.md)

# Chapter 22: Economics, FinOps and Sustainability

> **Implementation companion:** [Fulcrum](https://github.com/knowledgetrailsai/oasis-fulcrum).

# Economics, FinOps and Sustainability

> **CHAPTER PURPOSE** Measure unit economics and total value while optimizing model routing, context, latency, infrastructure, human intervention and environmental impact.

## Background and context

Chapter 21 instrumented six operational planes so a running intelligence system could be observed, diagnosed and improved continuously. The economic plane measures tokens, infrastructure and intervention cost, but stops short of the question those numbers exist to answer: is this system, at the cost it runs at, worth what it delivers. This chapter closes Part III of the methodology for that reason — proving the system was worth building, in terms a finance function and a business sponsor can both evaluate.

This chapter sits last because unit economics can only be measured honestly once a system is in production, generating the telemetry Chapter 21 defined. A cost model built before go-live is a forecast; one built from actual cost data is a fact, and that difference matters to a sponsor deciding whether to scale, hold steady, or retire a system. It also closes the arc back to where the methodology started: the value case built at initiation is only a hypothesis until this chapter's unit economics confirm or contradict it.

Two companion articles go deeper than a methodology chapter can. [Architecture Perspective 5 — Inference Architecture](../architecture/perspective-05-inference-architecture.md#4-cost-governance) is where model-routing cost decisions get architected at the enterprise level — a centralized inference gateway, an approved model registry with cost tiers, and aggregate spend tracked centrally rather than accumulating silently across independently-procured systems. The [Monitoring specification's economic plane metrics table](../monitoring/observability-and-telemetry-specification.md#economic-plane) is where the numbers this chapter's formulas consume are actually collected — token, infrastructure, tool and intervention cost, each with its own collection point and alert trigger, rolling up into the cost-per-successful-outcome figure that is this chapter's central measure.

## Economic model

OASIS evaluates the total cost of producing a successful outcome. This includes discovery and engineering, model inference, retrieval, tools, platform, licenses, integration, monitoring, human review, exception handling, failure, support, compliance and change. Benefits include revenue, productivity, quality, experience, risk reduction, working capital and strategic option value.

The word "total" matters. It is tempting to measure a system's cost as inference spend alone — the token bill is the most visible line, surfaced directly by a provider's billing dashboard. But inference is often the smallest component once discovery, integration, human review, exception handling and failure cost are counted honestly. A system cheap on a token-cost basis and expensive on a cost-per-successful-outcome basis is not an anomaly — it is the normal shape of the economics once intervention and failure cost are included.

> **UNIT ECONOMICS** Net outcome value = Outcome benefit − Delivery cost − Run cost − Human intervention cost − Expected failure and risk cost.

This formula forces every proposal and retrospective to net benefit against the full cost stack, not run cost alone — the comparison that makes a system look most favorable, and for that reason the one worth being suspicious of. Expected failure and risk cost belongs as a first-class term: a system with low run cost and high, uncounted failure cost — reversed transactions, complaints, remediation, regulatory exposure — is not actually cheaper once that cost is priced in.

| **Measure**                 | **Purpose**                                                    |
|-----------------------------|------------------------------------------------------------------|
| Cost per attempt            | Understand raw system consumption.                             |
| Cost per completed workflow | Include failures and retries.                                  |
| Cost per successful outcome | Relate cost to accepted business result.                       |
| Human minutes per outcome   | Expose exception and approval burden.                          |
| Failure-adjusted value      | Recognize reversals, complaints, remediation and risk.         |
| Marginal scale cost         | Test whether reuse improves economics.                         |
| Avoided legacy cost         | Capture decommissioning or reduced manual capacity where real. |

These seven measures run from least to most informative. Cost per attempt is easiest to produce and least useful alone — it says nothing about how many attempts succeed. Cost per completed workflow corrects for retries, but a workflow can complete and still not produce a result anyone accepts — the gap cost per successful outcome closes. That measure should anchor most economic conversations, because it can't be gamed by counting activity instead of results. Human minutes per outcome exists because intervention cost is easy to undercount when spread across many people's partial attention. Marginal scale cost and avoided legacy cost matter most for a scaling decision: whether reuse genuinely makes a second use case cheaper, and whether a claimed decommissioning saving is real capacity freed up rather than a nominal number nobody reclaims.

## Optimization sequence

54. **Remove unnecessary work, calls, tools and workflow depth.** Eliminating a call is strictly cheaper than optimizing it, and unnecessary workflow depth carries cost, latency and failure surface no downstream optimization can fully recover.

55. **Improve retrieval, context selection and deterministic validation.** A model reasoning over more context than a task requires pays for it in tokens and in the risk of wrong evidence crowding out right evidence; tighter retrieval and deterministic checks where they suffice reduce cost and improve reliability at once.

56. **Cache stable results and reuse structured intermediate artifacts safely.** Caching is only safe where the underlying evidence and answer remain valid — treat cache invalidation as seriously as cache population, since a stale cached result served with confidence is a groundedness failure in disguise.

57. **Route simple tasks to smaller models and reserve stronger models for difficult cases.** [Inference Architecture's cost governance](../architecture/perspective-05-inference-architecture.md#4-cost-governance) exists to make this an enterprise-wide capability rather than a per-system afterthought — a shared routing layer lets every consuming system benefit from the same tiered-model strategy.

58. **Batch, parallelize or asynchronously process where the workflow permits.** Not every task needs a synchronous, real-time response, and forcing one onto a workflow that could tolerate batching is a common, avoidable source of cost and latency pressure.

59. **Reduce human intervention through better interfaces and bounded automation only when quality supports it.** The qualifier is load-bearing — expanding automation before the Chapter 18 evaluation evidence supports it trades a visible cost saving for an invisible, usually larger, quality and risk cost.

60. **Reassess infrastructure, region, quantization, local deployment and vendor economics.** Placed last deliberately: it is the most disruptive, highest-effort lever, and steps 54–59 frequently make it unnecessary or at least clarify exactly what decision the remaining cost justifies.

This sequence is ordered by leverage and disruption, cheapest first — resist the temptation to skip to step 57 or 60 because they sound like the "real" optimization. Steps 54 through 56 routinely remove more cost, with far less engineering risk, than a model-routing or infrastructure change delivers alone.

## Sustainability

Sustainability follows the same discipline: avoid wasteful calls, select right-sized models and infrastructure, measure utilization, reuse results, schedule non-urgent processing, and include energy or carbon measures where material to enterprise commitments. Efficiency cannot justify lower safety or unacceptable quality.

Most levers in the optimization sequence above that reduce cost also reduce energy and compute footprint, since both are driven by the same thing: unnecessary inference and infrastructure. That correlation is useful — a FinOps program and a sustainability program pulling on the same levers means neither competes with the other for engineering attention — but it isn't identity. A lower-cost model route is not automatically the lower-carbon one once a provider's energy mix and data-center efficiency are accounted for, and a cost-optimal caching or batching strategy still needs evaluating against whatever carbon-reporting commitment an enterprise has made.

The final sentence of this section governs every lever above it: efficiency cannot justify lower safety or unacceptable quality. A cheaper model route that degrades groundedness, a batching strategy that delays an escalation past the point it's useful, or a caching decision serving stale evidence all fail this test regardless of how favorably they move cost-per-successful-outcome — a cheaper wrong answer is not a better outcome, it's a worse one that costs less to produce.

---

[← Previous: Chapter 21: Deployment, Operations and AgentOps](chapter-21-deployment-operations-and-agentops.md) · [Contents](../README.md) · [Next: Part IV: Delivery and Enterprise Enablement →](part-iv-delivery-and-enterprise-enablement.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
