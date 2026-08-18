<!-- SPDX-License-Identifier: MIT -->

[← Previous: Chapter 21: Deployment, Operations and AgentOps](chapter-21-deployment-operations-and-agentops.md) · [Contents](../README.md) · [Next: Part IV: Delivery and Enterprise Enablement →](part-iv-delivery-and-enterprise-enablement.md)

# Chapter 22: Economics, FinOps and Sustainability

# Economics, FinOps and Sustainability

> **CHAPTER PURPOSE** Measure unit economics and total value while optimizing model routing, context, latency, infrastructure, human intervention and environmental impact.

## Background and context

Chapter 21 instrumented six operational planes so that a running intelligence system could be observed, diagnosed and improved continuously. One of those planes — economic — measures tokens, infrastructure and intervention cost, but stops short of the question those numbers exist to answer: is this system, at the cost it actually runs at, worth what it delivers. That is this chapter's job, and it closes Part III of the methodology for a reason — every engineering, security, governance and operational discipline before it has been about building and running a system correctly; this chapter is about proving that building and running it was, in fact, worth doing, in terms a finance function and a business sponsor can both evaluate.

Economics, FinOps and Sustainability sits deliberately last in this run of chapters because unit economics can only be measured honestly once the system it describes is actually in production and generating the operational telemetry Chapter 21 defined. A cost model built before go-live is a forecast; a cost model built from the economic plane's actual token, infrastructure, tool and intervention cost data is a fact, and the difference between those two matters enormously to a sponsor deciding whether to scale a system, hold it steady, or retire it. This chapter also closes Part III's arc back to where the methodology started: the value case built at initiation is only ever a hypothesis until this chapter's unit economics either confirm or contradict it.

Two companion articles operationalize the concepts here in more depth than a methodology chapter can sustain. [Architecture Perspective 5 — Inference Architecture](../architecture/perspective-05-inference-architecture.md#4-cost-governance) is where model-routing cost decisions get architected at the enterprise level — a centralized inference gateway, an approved model registry with cost tiers, and aggregate spend tracked centrally rather than left to accumulate silently across dozens of independently-procured systems. And the [Monitoring specification's economic plane metrics table](../monitoring/observability-and-telemetry-specification.md#economic-plane) is where the numbers this chapter's formulas consume are actually collected — token cost per request, infrastructure cost, tool cost and intervention cost, each with its own collection point and alert trigger, rolling up into the cost-per-successful-outcome figure that is this chapter's central measure.

## Economic model

OASIS evaluates the total cost of producing a successful outcome. This includes discovery and engineering, model inference, retrieval, tools, platform, licenses, integration, monitoring, human review, exception handling, failure, support, compliance and change. Benefits include revenue, productivity, quality, experience, risk reduction, working capital and strategic option value.

The word "total" is doing real work in that first sentence, and it is worth dwelling on why. It is tempting, and common, to measure an intelligence system's cost as inference spend alone — the token bill is the most visible, most easily itemized line, and it is the number most naturally surfaced by a model provider's own billing dashboard. But inference is frequently the smallest component of what it actually costs to produce a successful outcome once discovery, integration, human review, exception handling and the cost of the failures that inevitably occur are counted honestly. A system that looks cheap on a token-cost basis and expensive on a cost-per-successful-outcome basis is not an anomaly; it is the normal shape of the economics once human intervention and failure cost are included rather than assumed away.

> **UNIT ECONOMICS** Net outcome value = Outcome benefit − Delivery cost − Run cost − Human intervention cost − Expected failure and risk cost.

This formula's structure is itself a discipline: it forces every proposal and every retrospective to net benefit against the full cost stack rather than against run cost alone, which is the comparison that makes an intelligence system look most favorable and is, for that exact reason, the comparison worth being suspicious of. Expected failure and risk cost belongs in the formula as a first-class term rather than an afterthought, because a system with a low run cost and a high, uncounted failure cost — reversed transactions, complaints, remediation, regulatory exposure — is not actually the cheaper option once that cost is priced in.

| **Measure**                 | **Purpose**                                                    |
|-----------------------------|------------------------------------------------------------------|
| Cost per attempt            | Understand raw system consumption.                             |
| Cost per completed workflow | Include failures and retries.                                  |
| Cost per successful outcome | Relate cost to accepted business result.                       |
| Human minutes per outcome   | Expose exception and approval burden.                          |
| Failure-adjusted value      | Recognize reversals, complaints, remediation and risk.         |
| Marginal scale cost         | Test whether reuse improves economics.                         |
| Avoided legacy cost         | Capture decommissioning or reduced manual capacity where real. |

These seven measures are ordered from the least to the most informative, and each answers a question the one before it cannot. Cost per attempt is the easiest number to produce and the least useful on its own — it says nothing about how many attempts actually succeed. Cost per completed workflow corrects for retries and failed attempts, but a workflow can complete correctly and still not produce a business result anyone accepts, which is exactly the gap cost per successful outcome closes — the measure that should anchor most economic conversations about an intelligence system, because it is the one number that cannot be gamed by counting activity instead of results. Human minutes per outcome exists because intervention cost is easy to undercount when it is distributed across many people's partial attention rather than concentrated in one visible line item; a system that looks economical because its direct costs are low can still be expensive once the exception-handling burden it silently shifts onto operational staff is measured. Marginal scale cost and avoided legacy cost are the two measures that matter most for a scaling decision — whether a second and third use case genuinely get cheaper through reuse, and whether a claimed decommissioning saving is real capacity freed up rather than a nominal number nobody actually reclaims.

## Optimization sequence

54. **Remove unnecessary work, calls, tools and workflow depth.** This is the first step for a reason: eliminating a call is strictly cheaper than optimizing it, and a workflow with unnecessary depth carries cost, latency and failure surface that no amount of downstream optimization can fully recover.

55. **Improve retrieval, context selection and deterministic validation.** A model asked to reason over more context than a task requires pays for that context in tokens and in the added risk of the wrong evidence crowding out the right evidence; tightening retrieval and preferring deterministic checks where they suffice reduces cost and improves reliability simultaneously.

56. **Cache stable results and reuse structured intermediate artifacts safely.** Caching is only safe where the underlying evidence and the answer it produced remain valid — treat cache invalidation as seriously as cache population, since a stale cached result served with confidence is a groundedness failure wearing a cost-optimization disguise.

57. **Route simple tasks to smaller models and reserve stronger models for difficult cases.** This is the step [Inference Architecture's cost governance](../architecture/perspective-05-inference-architecture.md#4-cost-governance) exists to make an enterprise-wide capability rather than a per-system afterthought — a shared routing layer lets every consuming system benefit from the same tiered-model strategy instead of each team re-deriving it independently.

58. **Batch, parallelize or asynchronously process where the workflow permits.** Not every task needs a synchronous, real-time response, and forcing one onto a workflow that could tolerate batching or asynchronous processing is a common, avoidable source of both cost and unnecessary latency pressure on the model layer.

59. **Reduce human intervention through better interfaces and bounded automation only when quality supports it.** The qualifier at the end of this step is load-bearing — expanding automation to reduce intervention cost before the evaluation evidence in Chapter 18 supports that expansion trades a visible cost saving for an invisible, and usually larger, quality and risk cost.

60. **Reassess infrastructure, region, quantization, local deployment and vendor economics.** This step is placed last deliberately: it is the most disruptive and highest-effort lever, and working through steps 54–59 first frequently makes it unnecessary, or at least clarifies exactly what infrastructure decision the remaining cost actually justifies.

This sequence is ordered by leverage and by disruption, cheapest and least disruptive first, and it is worth resisting the temptation to skip to step 57 or 60 because they sound like the "real" optimization — in practice, steps 54 through 56 routinely remove more cost, with far less engineering risk, than a model-routing or infrastructure change delivers on its own.

## Sustainability

Sustainability follows the same discipline: avoid wasteful calls, select right-sized models and infrastructure, measure utilization, reuse results, schedule non-urgent processing, and include energy or carbon measures where material to enterprise commitments. Efficiency cannot justify lower safety or unacceptable quality.

The phrase "follows the same discipline" is precise rather than casual — every lever in the optimization sequence above that reduces cost also, in most cases, reduces energy and compute footprint, because the two are correlated through the same underlying driver: unnecessary inference and unnecessary infrastructure. That correlation is genuinely useful — a FinOps program and a sustainability program pulling on the same levers means neither has to compete with the other for engineering attention — but it should not be mistaken for identity. Cost and carbon intensity diverge in specific cases: a lower-cost model route is not automatically the lower-carbon one once the provider's underlying energy mix and data-center efficiency are accounted for, and a cost-optimal caching or batching strategy still needs to be evaluated against whatever carbon-reporting commitment an enterprise has made, rather than assumed to satisfy it by default.

The final sentence of this section is the one that governs every lever above it, and it is worth reading as a hard constraint rather than a closing caveat: efficiency cannot justify lower safety or unacceptable quality. A cheaper model route that degrades groundedness, a batching strategy that delays an escalation past the point it is useful, or a caching decision that serves stale evidence are all optimizations that fail this test, regardless of how favorably they move the cost-per-successful-outcome measure above — because a cheaper wrong answer is not a better outcome, it is a worse one that happens to cost less to produce.

---

[← Previous: Chapter 21: Deployment, Operations and AgentOps](chapter-21-deployment-operations-and-agentops.md) · [Contents](../README.md) · [Next: Part IV: Delivery and Enterprise Enablement →](part-iv-delivery-and-enterprise-enablement.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
