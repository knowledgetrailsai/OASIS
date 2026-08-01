<!-- SPDX-License-Identifier: MIT -->

[← Previous: Part III: Intelligence-System Engineering and Assurance](part-iii-intelligence-system-engineering-and-assurance.md) · [Contents](README.md) · [Next: Chapter 15: Data and Knowledge Engineering →](chapter-15-data-and-knowledge-engineering.md)

# Chapter 14: Intelligence and Agent Engineering

# Intelligence and Agent Engineering

> **CHAPTER PURPOSE** Engineer the complete intelligence system from specification and model strategy through context, harness, tools, memory, evaluation and AgentOps.

*Figure 4. OASIS engineers and evaluates the complete intelligence system.*

> **SYSTEM EQUATION** AI system = Model + Context + Harness + Tools + Workflow + Memory/State + Controls + Evaluation + Runtime.

## 1. Intelligence-system specification

Specify what the system must understand, decide, generate or execute; the inputs and evidence it may use; the expected output schema; permitted actions; uncertainty and abstention behavior; completion criteria; prohibited behavior; and cases requiring human authority. This is the behavioral contract for the intelligence, not a generic prompt.

## 2. Model engineering

Select and benchmark models against representative tasks. Consider reasoning needs, modality, deployment region, privacy, latency, cost, context window, tool use and operational support. Establish primary and fallback models, routing criteria and version support. Prove quality with the strongest appropriate model first, then optimize through smaller models, routing, caching, compression or adaptation.

## 3. Data, retrieval and knowledge foundations

Create governed services for ingestion, parsing, normalization, taxonomy, metadata, chunking, indexing, retrieval, freshness, lineage and access control. Evaluate retrieval separately from generation. The goal is the smallest sufficient and authoritative evidence set—not the largest possible context.

## 4. Prompt and context engineering

Prompt engineering defines instructions, examples, constraints and output structure. Context engineering constructs everything the model should see at a decision point: task, user and workflow state, retrieved sources, memory, tool definitions and results, policies, examples and token budget. Context must be authorization-aware, source-attributed, fresh, compressed where necessary and resistant to poisoning.

| **Context engineering**                                       | **Harness engineering**                                         |
|---------------------------------------------------------------|-----------------------------------------------------------------|
| Determines what the model sees now.                           | Determines how the system completes the task.                   |
| Selects instructions, knowledge, memory and tool information. | Runs loops, tools, state, retries, checkpoints and recovery.    |
| Manages relevance, ordering and token budget.                 | Manages execution limits, authority, escalation and completion. |
| Optimizes a decision point.                                   | Coordinates the end-to-end task lifecycle.                      |

## 5. Tool and action engineering

A tool is a governed interface through which the system retrieves, calculates or acts. Tool contracts define purpose, inputs, outputs, authentication, authorization, data classification, validation, idempotency, timeouts, retries, transaction boundaries, confirmations, audit, rollback and error semantics. Tools should be narrow enough to control and clear enough for reliable selection.

## 6. Agent-harness engineering

The harness is the software scaffold around the model. It assembles context, invokes the model, registers and calls tools, records state, processes results, enforces limits, requests approval, retries safely, checkpoints long work and terminates on explicit criteria. Harness assumptions must be retested as models, tools and workflows change.

## 7. Workflow and orchestration engineering

Use deterministic functions for fixed calculations; explicit workflows for known paths; agents for open-ended tasks requiring dynamic choice; and multi-agent systems only when specialization, isolation or parallelism creates measurable benefit. Orchestration covers sequential, concurrent, routing, hand-off, supervisor and human-in-the-loop patterns. Every path requires state, ownership and recovery.

## 8. Memory and state engineering

State records the current execution: steps, artifacts, approvals, tool results, errors and transaction status. Memory retains information that may inform future work. Define purpose, source, confidence, access, retention, correction, deletion, expiry and contamination controls. Do not equate memory with indefinite conversation storage.

## 9. Human–AI interaction, structured outputs and validation

Design evidence presentation, uncertainty, action preview, approval, override, correction, escalation and feedback. Machine-consumed outputs use explicit schemas, deterministic parsing and business-rule validation. High-consequence decisions expose sources and relevant reasoning evidence without relying on unverifiable narrative explanations.

## 10. Guardrails, reliability and recovery

Layer controls across input, context, model, tool, workflow, output, runtime and business policy. Establish iteration, time, token, cost and transaction limits; safe retries; partial completion handling; compensating actions; fallback models or workflows; human escalation; suspension and kill switches.

## 11. Evaluation engineering

Measure intent understanding, correctness, groundedness, citation, structured output, retrieval, tool selection and arguments, workflow completion, policy adherence, escalation, robustness, latency, cost, user acceptance and outcome contribution. Progress the evaluation unit from response to agent step, completed workflow and business outcome.

## 12. Runtime, AgentOps and adaptation

Version models, prompts, context policies, retrieval indexes, tools, workflows and controls. Trace model and tool calls, decisions, approvals and outcome events. Diagnose failure at the responsible layer. Fine-tuning is considered when repeated, well-defined domain failures remain after context, workflow, tool and instruction improvements; it is not the default repair for every issue.

## Engineering artifact set

| **Artifact**                        | **Decision supported**                                                 |
|-------------------------------------|------------------------------------------------------------------------|
| Intelligence Specification          | What behavior and authority are required?                              |
| Model Strategy and Benchmark        | Which model or route meets thresholds?                                 |
| Context Architecture                | What evidence and state are supplied at each decision?                 |
| Tool Catalogue and Action Contracts | What can the system access or execute, under what controls?            |
| Harness and Workflow Design         | How does the task progress, recover and terminate?                     |
| Memory and State Policy             | What persists, for whom, for how long and with what correction rights? |
| Evaluation and Regression Suite     | What constitutes acceptable behavior and change?                       |
| AgentOps Runbook                    | How is the system deployed, observed, supported and improved?          |

---

[← Previous: Part III: Intelligence-System Engineering and Assurance](part-iii-intelligence-system-engineering-and-assurance.md) · [Contents](README.md) · [Next: Chapter 15: Data and Knowledge Engineering →](chapter-15-data-and-knowledge-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](LICENSE.md).
