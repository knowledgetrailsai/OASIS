<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [← Previous: Agent Architecture](perspective-02-agent-architecture.md) · [Architecture: Reference Architecture](oasis-reference-architecture.md#6-enterprise-architecture-perspectives) · [Next: Information and Knowledge Architecture →](perspective-04-information-and-knowledge-architecture.md)

# Architecture Perspective 3: Process Architecture

> **PURPOSE** Define how agents participate in business processes — where an agent enters a process, what it owns within it, and where a human retains ownership — so process design and agent design happen together instead of an agent being retrofitted into a process it was not designed for.

**Primary OASIS source:** [Chapter 16 — Human–AI Workflow and Experience Engineering](../Methodology/chapter-16-human-ai-workflow-and-experience-engineering.md); [Chapter 9 — Phase 3: Engineer & Integrate](../Methodology/chapter-09-phase-3-engineer-and-integrate.md); [Chapter 14 §7 — Workflow and orchestration selection](../Methodology/chapter-14-intelligence-and-agent-engineering.md).

## Background and context

Chapter 16 addresses human-AI workflow design at the level of a single interaction: how a human and an agent hand off a task to each other, when to interrupt for approval, how to design for override. Process Architecture takes the wider view an enterprise process owner needs: a business process (claims intake through settlement; a hire from requisition through onboarding) is usually longer, more branched, and touches more systems than any single agent's scope — an agent typically owns one or a few steps within a process it does not own end-to-end. Without an explicit process map, it becomes unclear where an agent's authority starts and stops relative to the surrounding human-owned process, and process owners lose visibility into how much of "their" process now runs through agentic components they did not design.

This perspective is the map that keeps process ownership and agent ownership distinct and explicit, even as more steps of a process become agent-assisted or agent-executed over time (Chapter 12's optimize-and-scale trajectory).

## 1. Process-to-agent participation map

One row per process step, for each business process that includes agentic participation.

| Process | Step | Executed by (human / task agent / specialist agent) | Decision authority at this step | Handback trigger | Process owner |
|---|---|---|---|---|---|
| | | | | | |

## 2. Process ownership model

| Principle | What it means in practice |
|---|---|
| The process owner is never the agent | A named human or function owns the end-to-end process outcome regardless of how many steps are agent-executed — this is the process-level instance of the [Human accountable](oasis-reference-architecture.md#architecture-principles) principle. |
| Agent scope is a subset of process scope | An agent's [Autonomy Matrix](../Methodology/chapter-32-templates-checklists-and-tools.md#12-autonomy-matrix) entry is defined at the step level, never inherited automatically across the whole process. |
| Handback points are designed, not incidental | Every process with agentic steps names, in advance, the conditions under which control returns to a human — confidence threshold, policy exception, value threshold — per [Chapter 16](../Methodology/chapter-16-human-ai-workflow-and-experience-engineering.md). |
| Process change is versioned like system change | A process redesign that changes which steps are agent-executed follows the same release discipline as the [Monitoring release manifest](../monitoring/observability-and-telemetry-specification.md#3-release-manifest-checklist) — it is a change to system behavior, not just a documentation update. |

## 3. Process risk classification

| Process characteristic | Implication for agent participation |
|---|---|
| Irreversible or high-value step | Confirmation and human approval required before execution (Ch.17 category: execute with mandatory confirmation). |
| Regulated decision point (credit, employment, benefits eligibility) | Route through the applicable [Standards](../standards/) checklist before any agent participation is approved. |
| High-volume, low-variance step | Strongest candidate for higher autonomy — evaluate against the [Optimization ladder](../engineering/model-engineering.md#4-optimization-ladder) and Progressively Autonomous principle. |
| Cross-functional handoff | Requires explicit [Responsibility Assignment Matrix](../Methodology/chapter-32-templates-checklists-and-tools.md#12-responsibility-assignment-matrix) entry — ambiguous ownership at a handoff is where agentic processes most often fail silently. |

## 4. Relationship to system-level workflow design

A process map spans potentially many systems and agents; a single system's [Harness and Orchestration Engineering](../engineering/harness-and-orchestration-engineering.md) document governs how one agent or workflow executes its portion. Do not duplicate step-level implementation detail here — link to the owning system's harness design and keep this map at the process-step and ownership level.

---

[← Back to Contents](../README.md) · [← Previous: Agent Architecture](perspective-02-agent-architecture.md) · [Architecture: Reference Architecture](oasis-reference-architecture.md#6-enterprise-architecture-perspectives) · [Next: Information and Knowledge Architecture →](perspective-04-information-and-knowledge-architecture.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
