<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: Harness and Orchestration Engineering](harness-and-orchestration-engineering.md) · [Chapter 14: Intelligence and Agent Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md) · [Next: Evaluation and Reliability Engineering →](evaluation-and-reliability-engineering.md)

# Engineering: Memory and State Engineering

> **PURPOSE** Turn Chapter 14 §8's memory-and-state principles into a fillable classification table and memory-policy template that forces an explicit answer to "what persists, for whom, for how long" — rather than letting memory scope grow by accident as features are added.

**Primary OASIS source:** [Chapter 14 §8 — Memory and State Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md#8-memory-and-state-engineering); cross-referenced with the [Security checklist's](../security/agentic-ai-threat-and-control-checklist.md#2-agentic-threat-model-ch-19-mapped-to-owasp-agentic-top-10-and-mitre-atlas) memory-poisoning row and the [DPDP](../standards/dpdp-act-alignment-checklist.md) / other privacy-law checklists.

**Implemented in:** [Helm](https://github.com/knowledgetrailsai/Helm) — the memory-poisoning threat category in its [agentic threat model](https://github.com/knowledgetrailsai/Helm/blob/main/06-security-and-containment/agentic-threat-model.md) is the runtime-containment side of this article's memory and state policy; [Compass](https://github.com/knowledgetrailsai/responsible-ai) implements the privacy-law obligations (DPDP, GDPR-equivalents) that bound what state may be retained.

## Background and context

Chapter 14 draws a precise distinction that is easy to blur in practice: **state** records the current execution — steps taken, artifacts produced, approvals granted, tool results received, errors encountered, transaction status — and belongs to a single task's lifecycle. **Memory** retains information that may inform *future* work, and outlives any single execution. The chapter's own warning is worth repeating exactly as stated: do not equate memory with indefinite conversation storage. That warning exists because the default, path-of-least-resistance implementation of "give the agent memory" is often to simply retain full conversation history indefinitely and let the model search over it — which quietly turns every conversation into a permanent, growing, unaudited data store with no defined purpose, no retention policy, no correction mechanism, and no way to answer a data-subject access or erasure request under any privacy law the system happens to be in scope for.

Treating memory as an engineered artifact rather than an emergent side effect of long context windows means every piece of retained information needs the same governance questions a database schema needs: what is its purpose (why is this worth remembering at all), where did it come from (source and confidence — a fact the system inferred is not the same class of memory as a fact the user explicitly stated), who can access it, how long is it kept, can it be corrected or deleted, when does it expire, and what happens if it is contaminated — either by an honest error propagating forward, or by the adversarial memory-poisoning threat named explicitly in the [Security checklist](../security/agentic-ai-threat-and-control-checklist.md#2-agentic-threat-model-ch-19-mapped-to-owasp-agentic-top-10-and-mitre-atlas) (OWASP ASI06). A memory system with no answer to "how does a wrong memory get corrected" will, over enough production time, accumulate wrong memories that silently degrade every future decision that reads from it.

**How to use this document:** use Section 1 to classify every candidate piece of retained information as state or memory before deciding how to persist it. Use Section 2 to write the memory policy for anything classified as memory — state does not need this level of governance since it doesn't outlive its task. Use Section 3 when designing checkpoint/recovery behavior for long-running harness execution.

## 1. State vs. memory classification table

| Data element | State or memory? | Source | Confidence | Scope (task-only / cross-task) | Retention | Correction mechanism | Deletion trigger |
|---|---|---|---|---|---|---|---|
| | | | | | | | |
| | | | | | | | |

A quick test: if this data element becomes meaningless the moment the current task ends, it is state. If it should still be available and relevant the next time this user, case, or system interacts with the agent, it is memory — and needs a completed row in Section 2, not just this table.

## 2. Memory policy template

Complete one policy per distinct memory store (e.g., "user preference memory," "case-history memory," "learned-correction memory") — a single system may legitimately have several, each with different rules.

```yaml
memory_policy:
  memory_store_name: ""
  purpose: ""                          # why this is worth remembering — required, not optional
  source:
    origin: "user-stated | system-inferred | derived-from-outcome"
    confidence_scoring: ""             # how confidence is assigned and whether it decays over time
  access:
    who_can_read: []
    who_can_write: []
    cross_user_visibility: "none | aggregated-only | full"
  retention:
    default_period: ""
    max_period: ""
  correction:
    mechanism: ""                      # how a wrong memory is corrected — must not require a developer
    who_can_correct: []
  deletion:
    user_initiated_deletion_supported: true|false
    automatic_expiry_trigger: ""
    right_to_erasure_hook: ""          # link to applicable privacy-law checklist (DPDP, GDPR, etc.)
  contamination_controls:
    poisoning_defenses: ""             # see Security checklist ASI06
    propagation_limit: ""              # how far a single bad memory can influence downstream decisions before review
  expiry_review_cadence: ""
```

## 3. State persistence and checkpoint checklist

| # | Question | Answer |
|---|---|---|
| 1 | What state must survive a harness crash or restart mid-task? | |
| 2 | At what granularity are checkpoints taken (every step, every tool call, every N seconds)? | |
| 3 | Is checkpointed state sufficient to resume without repeating a non-idempotent action already completed? | |
| 4 | How long is completed-task state retained after the task ends, and for what purpose (audit, debugging, none)? | |
| 5 | Does resuming from a checkpoint re-validate context freshness, or trust the checkpointed context as-is? | |

---

[← Back to Contents](../README.md) · [← Previous: Harness and Orchestration Engineering](harness-and-orchestration-engineering.md) · [Chapter 14: Intelligence and Agent Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md) · [Next: Evaluation and Reliability Engineering →](evaluation-and-reliability-engineering.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
