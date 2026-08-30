<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 14: Intelligence and Agent Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md) · [Next: Context and Retrieval Engineering →](context-and-retrieval-engineering.md)

# Engineering: Model Engineering

> **PURPOSE** Turn Chapter 14 §2's model-selection principles into a fillable benchmarking record, routing design, and optimization ladder a build team can actually run through, rather than a one-paragraph description of what good model selection looks like.

**Primary OASIS source:** [Chapter 14 §2 — Model Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md#2-model-engineering); cross-referenced with [Chapter 22 — Economics, FinOps and Sustainability](../methodology/chapter-22-economics-finops-and-sustainability.md) and the [Evaluation and Reliability Engineering](evaluation-and-reliability-engineering.md) article.

**Implemented in:** [Axiom](https://github.com/knowledgetrailsai/Axiom) — the background reference on the model architectures (Transformers, MoE, SSMs, and related families) this article's selection criteria assume; [Fulcrum](https://github.com/knowledgetrailsai/oasis-fulcrum) implements the cost-governance and model-routing economics that inform the same decision.

## Background and context

Chapter 14 deliberately does not name specific models or providers. The model landscape changes faster than any methodology chapter could stay current with, and a team that selected models by reading a chapter rather than running its own benchmark would be optimizing for last quarter's leaderboard, not this task. What the chapter does prescribe is a discipline: benchmark against *representative tasks*, not general-purpose leaderboards; consider the full decision surface (reasoning depth, modality, deployment region, privacy, latency, cost, context window, tool-use reliability, operational support) rather than a single headline metric; and prove quality with the strongest appropriate model first, then optimize downward. It is far easier to discover a smaller model is "good enough" once you know what "good" looks like than to discover a cost-optimized choice was never good enough in the first place.

This ordering matters more than it might seem. Teams that start with a cost-optimized model and iterate upward tend to conflate two different failures — "the task is hard" and "the model is too weak" — because they never established a ceiling. Teams that start with the strongest available model and optimize down have a stable reference point: if the strongest model still fails a case, that's a task-design or context problem (see [Context and Retrieval Engineering](context-and-retrieval-engineering.md)), not a model problem, and no amount of model swapping will fix it. The optimization ladder in Section 4 makes that downward search systematic rather than ad hoc.

**How to use this document:** run Section 1 to define selection criteria before touching any model, Section 2 to record actual benchmark results per candidate, Section 3 to design the production routing/fallback strategy once a primary model is chosen, Section 4 when cost or latency pressure motivates looking for a smaller/cheaper option, and Section 5 only after Section 4's context/workflow/tool improvements have been exhausted.

## 1. Model selection criteria

| Dimension | Requirement for this task | Why it matters | Weight |
|---|---|---|---|
| Reasoning depth | | Does the task need multi-step reasoning, or is it closer to classification/extraction? | |
| Modality | | Text-only, or does the task require vision, audio, or structured-data input? | |
| Deployment region | | Data-residency or latency constraints on where inference can run | |
| Privacy | | Can this task's data leave the organization's environment, and under what terms? | |
| Latency | | Interactive (seconds) vs. batch (minutes/hours) tolerance | |
| Cost ceiling | | Maximum acceptable cost per successful outcome — link to [Value and Risk Case](../tools/01-outcome-and-portfolio-templates.md#5-value-and-risk-case) | |
| Context window | | Minimum context needed once [Context Architecture](context-and-retrieval-engineering.md#1-context-architecture-template) is designed | |
| Tool-use reliability | | Does the task require reliable structured tool calls? | |
| Operational support | | Provider SLA, versioning policy, deprecation notice period | |

## 2. Model benchmark record

Complete one record per candidate model, against the same task-representative evaluation set (see [Evaluation Dimension Reference](evaluation-and-reliability-engineering.md#1-evaluation-dimension-reference)) so results are comparable.

```yaml
model_benchmark_record:
  candidate_model: ""
  provider: ""
  benchmark_date: ""
  evaluation_dataset_reference: ""   # link to Evaluation Strategy and Dataset template
  results:
    - dimension: ""                  # e.g. correctness, groundedness, tool-selection accuracy
      score: ""
      pass_threshold: ""
      pass: true|false
  latency_p50_ms: ""
  latency_p95_ms: ""
  cost_per_1k_tokens_or_per_call: ""
  context_window: ""
  known_limitations: []
  recommendation: "primary | fallback | reject"
```

## 3. Model strategy and routing design

```yaml
model_strategy:
  primary_model: ""
  primary_model_rationale: ""
  fallback_model: ""
  fallback_trigger: ""                # e.g. primary timeout, primary error rate threshold, primary outage
  routing_criteria:
    - condition: ""                   # e.g. "task classified as simple extraction"
      route_to: ""
  version_support_policy:
    pinned_version: ""
    upgrade_testing_required: true|false
    provider_deprecation_notice_period: ""
  provider_change_detection: ""       # how the team learns of upstream model behavior changes — see Ch.21 release management
```

## 4. Optimization ladder

Work down this ladder only after the strongest appropriate model has proven the task is solvable at all. Each rung requires evidence that quality holds before moving further down — do not skip a rung to save time.

| Rung | Optimization | Trigger to consider it | Evidence required before adopting |
|---|---|---|---|
| 0 | Strongest appropriate model (starting point) | Always start here | Task proven solvable; establishes the quality ceiling |
| 1 | Smaller model for the same task | Cost/latency pressure and task appears simple enough | Benchmark record (Section 2) shows no quality regression on the full evaluation set |
| 2 | Routing (send easy cases to a smaller model, hard cases to the strongest) | Task difficulty varies meaningfully across cases | Routing classifier accuracy evidenced; regression suite passes for both routes |
| 3 | Caching (reuse prior results for repeated/similar inputs) | High rate of duplicate or near-duplicate requests | Cache hit rate and staleness policy evidenced; no correctness regression from stale cache hits |
| 4 | Compression (shorter prompts/context, distillation) | Context or prompt length is the binding cost driver | Compressed-context evaluation matches full-context evaluation within tolerance |
| 5 | Adaptation (fine-tuning) | See Section 5 — last resort, not a default optimization | Documented per Section 5 |

## 5. Fine-tuning decision checklist

Per Chapter 14 §12: fine-tuning is considered only when repeated, well-defined domain failures remain *after* context, workflow, tool and instruction improvements have been exhausted — it is not the default repair for every quality issue.

| # | Question | Answer required before proceeding |
|---|---|---|
| 1 | Has the failure been reproduced in the evaluation suite as a specific, well-defined case class? | |
| 2 | Has improving context (Section on [Context Architecture](context-and-retrieval-engineering.md#1-context-architecture-template)) been tried and failed to resolve it? | |
| 3 | Has improving the harness/workflow (see [Harness and Orchestration Engineering](harness-and-orchestration-engineering.md)) been tried and failed? | |
| 4 | Has improving tool contracts or instructions been tried and failed? | |
| 5 | Is the failure pattern frequent and well-defined enough to justify a training dataset, rather than a long tail of unrelated issues? | |
| 6 | Who owns the fine-tuned model's ongoing evaluation, versioning and retraining cadence going forward? | |

---

[← Back to Contents](../README.md) · [Chapter 14: Intelligence and Agent Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md) · [Next: Context and Retrieval Engineering →](context-and-retrieval-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
