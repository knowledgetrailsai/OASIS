<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: Model Engineering](model-engineering.md) · [Chapter 14: Intelligence and Agent Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md) · [Next: Tool and Integration Interface Specification →](tool-and-integration-interface-specification.md)

# Engineering: Context and Retrieval Engineering

> **PURPOSE** Turn Chapter 14 §3–4's data/retrieval and context-engineering principles into a fillable context architecture, retrieval pipeline specification, and context-quality checklist — the concrete companion to what the chapter states as a design philosophy.

**Primary OASIS source:** [Chapter 14 §3 — Data, Retrieval and Knowledge Foundations](../methodology/chapter-14-intelligence-and-agent-engineering.md#3-data-retrieval-and-knowledge-foundations) and [§4 — Prompt and Context Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md#4-prompt-and-context-engineering); cross-referenced with [Chapter 15 — Data and Knowledge Engineering](../methodology/chapter-15-data-and-knowledge-engineering.md) and the [Security checklist's](../security/agentic-ai-threat-and-control-checklist.md) context-layer controls.

**Implemented in:** [Forge](https://github.com/knowledgetrailsai/Forge) — the retrieval architectures (RAG variants, GraphRAG, hybrid search), embedding-model selection, chunking strategies, and grounding-policy schema this article references are built out there with formulas and worked examples, not repeated here.

## Background and context

People often use "context engineering" and "prompt engineering" interchangeably, but Chapter 14 treats them as separate disciplines with different scopes. Prompt engineering covers instructions — the fixed wording that tells a model what to do, what format to respond in, and what examples to follow. Context engineering covers everything else the model sees at a given decision point: retrieved evidence, conversation and workflow state, memory, tool definitions and results, applicable policy, and the token budget all of that has to fit inside. A well-engineered prompt still fails against a poorly engineered context, because the model is reasoning over the wrong, incomplete, or stale evidence. That is why Chapter 14 defines context engineering as "everything the model should see at a decision point," not a stylistic add-on to prompt design.

Retrieval has a specific failure mode worth naming: trying to fix context-quality problems by making the context window bigger, instead of making the retrieved evidence better. Larger context windows lower the *cost* of including more evidence, but they do not change the underlying principle Chapter 14 states directly — the goal is "the smallest sufficient and authoritative evidence set," not the largest possible context. A model given ten marginally-relevant documents performs worse, not better, than one given the two documents that actually answer the question, even when the ten would fit comfortably in the window. Irrelevant context competes for the model's attention and increases the surface area for injection and contamination (see the [Security checklist's](../security/agentic-ai-threat-and-control-checklist.md#1-defense-in-depth-control-layers-ch-19-mapped-to-owasp-llm-top-10) context-layer row). This is also why Chapter 14 requires evaluating retrieval *separately* from generation — a system can generate good answers from bad retrieved evidence by accident often enough to hide a retrieval problem until it fails in production, on a case the evaluation set didn't happen to cover.

**How to use this document:** design the retrieval pipeline (Section 2) before the context architecture (Section 1), since the context assembler consumes what the pipeline produces. Run the context-quality checklist (Section 3) against any context architecture before it goes to production, and evaluate retrieval quality (Section 4) independently from the [full evaluation suite](evaluation-and-reliability-engineering.md).

## 1. Context architecture template

```yaml
context_architecture:
  system_name: ""
  decision_point: ""                  # which harness step this context serves
  components:
    task_and_instructions:
      source: ""                       # prompt/instruction library reference
      token_budget: ""
    user_and_workflow_state:
      fields_included: []
      source: ""
    retrieved_evidence:
      retrieval_pipeline_reference: ""  # link to Section 2 below
      max_items: ""
      relevance_threshold: ""
    memory:
      memory_policy_reference: ""       # link to Memory and State Engineering
      items_included: ""
    tool_definitions_and_results:
      tools_available_at_this_point: []
      prior_tool_results_included: ""
    applicable_policy:
      source: ""
    examples:
      count: ""
      selection_method: "fixed | dynamic/similarity-selected"
  total_token_budget: ""
  ordering_strategy: ""                # how components are ordered/prioritized when budget is tight
  compression_strategy: ""             # summarization, truncation, or selective omission when over budget
```

## 2. Retrieval pipeline specification

| Stage | Design question to answer | Decision recorded |
|---|---|---|
| Ingestion | What sources feed this pipeline, and at what cadence? | |
| Parsing | How is each source format converted to usable text/structure? | |
| Normalization | What inconsistencies (formatting, terminology, units) are resolved here? | |
| Taxonomy | What classification scheme organizes this content for retrieval? | |
| Metadata | What fields (source, date, author, authority level, access class) are attached to every chunk? | |
| Chunking | What chunking strategy, and why (fixed-size, semantic, document-structure-aware)? | |
| Indexing | What index type, and what similarity/ranking method? | |
| Retrieval | What query construction and top-k / threshold strategy is used? | |
| Freshness | How is staleness detected, and how often is the index refreshed? | |
| Lineage | Can every retrieved chunk be traced back to its source document and version? | |
| Access control | Does retrieval respect the requesting user's authorization, not just the system's? | |

## 3. Context quality checklist

Chapter 14 requires context to be authorization-aware, source-attributed, fresh, compressed where necessary, and resistant to poisoning. Test each before production release.

| # | Property | Test method | Status |
|---|---|---|---|
| 1 | Authorization-aware | Confirm retrieval never returns content the requesting user/system is not authorized to see, even if it is topically relevant | |
| 2 | Source-attributed | Confirm every piece of retrieved evidence in the assembled context carries a traceable source reference | |
| 3 | Fresh | Confirm the freshness policy (Section 2) is enforced and stale content is flagged or excluded | |
| 4 | Compressed where necessary | Confirm the context assembler degrades gracefully (Section 1 compression strategy) rather than silently truncating when over budget | |
| 5 | Injection-resistant | Confirm retrieved/external content cannot be interpreted as instructions — see [Security checklist](../security/agentic-ai-threat-and-control-checklist.md#2-agentic-threat-model-ch-19-mapped-to-owasp-agentic-top-10-and-mitre-atlas) row 1 (prompt/context injection) | |

## 4. Retrieval evaluation template

Evaluate retrieval quality independently from end-to-end generation quality — a system can look correct in production while silently retrieving the wrong evidence.

```yaml
retrieval_evaluation:
  evaluation_date: ""
  query_set_reference: ""             # representative queries, ideally sourced from production
  metrics:
    precision_at_k: ""
    recall_at_k: ""
    mean_reciprocal_rank: ""
  failure_analysis:
    - query: ""
      expected_source: ""
      actual_retrieved: ""
      failure_type: "missed relevant | retrieved irrelevant | stale | wrong-authority-source"
  regression_cases_added: ""          # feeds Evaluation Strategy and Dataset
```


---

[← Back to Contents](../README.md) · [← Previous: Model Engineering](model-engineering.md) · [Chapter 14: Intelligence and Agent Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md) · [Next: Tool and Integration Interface Specification →](tool-and-integration-interface-specification.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
