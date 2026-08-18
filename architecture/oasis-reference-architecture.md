<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md) · [Chapter 14: Intelligence and Agent Engineering](../Methodology/chapter-14-intelligence-and-agent-engineering.md) · [Engineering: Tool and Integration Interface Specification →](../engineering/tool-and-integration-interface-specification.md)

# Architecture: OASIS Intelligence-System Reference Architecture

> **PURPOSE** Give a first-pass, technology-neutral reference architecture for the intelligence system described conceptually in [Chapter 14](../Methodology/chapter-14-intelligence-and-agent-engineering.md), so a delivery team has a concrete component diagram to start from instead of reconstructing one from narrative each engagement. This is a starting point for the [Intelligence-System Blueprint](../Methodology/chapter-32-templates-checklists-and-tools.md#11-intelligence-system-blueprint) — tailor components, not the layering discipline, to the engagement.

**Primary OASIS source:** [Chapter 14 — Intelligence and Agent Engineering](../Methodology/chapter-14-intelligence-and-agent-engineering.md) (system equation and sections 1–12), cross-referenced with [Chapter 17 — Enterprise Integration and Tool Engineering](../Methodology/chapter-17-enterprise-integration-and-tool-engineering.md) and [Chapter 19 — Security and Responsible AI Engineering](../Methodology/chapter-19-security-and-responsible-ai-engineering.md) (defense-in-depth layers).

## Background and context

Chapter 14 is written at the altitude of an engineering *methodology* — it tells a team what decisions to make (model selection criteria, when to use an agent versus a deterministic function, what a tool contract must contain) but deliberately does not draw a picture, because the right picture differs by engagement and Chapter 14 has to stay technology- and vendor-neutral. That is correct for a methodology chapter, but it leaves a gap in practice: an engineering team starting a build still needs *something* to put on a whiteboard on day one, and re-deriving a component diagram from eleven pages of narrative every time a new engagement kicks off is wasted effort. This document is that starting diagram — a concrete, reusable first draft that a team can copy, mark up and discard the parts that don't apply, rather than an authoritative architecture every OASIS system must match exactly.

Three things to keep in mind while reading it. First, the diagram in Section 1 is a **capability map, not a deployment topology** — each box represents a responsibility the system must fulfil (assemble context, enforce a limit, validate an output), not a literal microservice, container, or team boundary. A small system might implement the Context assembler and the Harness as one function in one codebase; a large multi-tenant platform might implement each box as a separately owned service. The architecture is about which responsibilities exist and how they hand off to each other, not about deployment granularity. Second, the diagram deliberately mirrors the *order* Chapter 14 introduces its sections (specification → model → data/retrieval → context → tools → harness → workflow → memory → human interaction/validation → guardrails → evaluation → runtime), so Section 2's component-to-artifact map can be read top-to-bottom against the diagram and against the chapter simultaneously. Third, this is a **reference**, not a mandate: Section 5 explains explicitly which components a simpler system is allowed to omit, and Chapter 30's tailoring framework governs that decision, not this document.

If you are new to reading Mermaid flowcharts: boxes are components, arrows show the direction data or control flows, dashed arrows (`-.->`) indicate a fallback or feedback path rather than the primary flow, and boxes grouped inside a labelled `subgraph` belong to the same layer of the system equation below. GitHub, most IDEs, and most Markdown viewers render the diagrams inline automatically; if your viewer does not render Mermaid, the same information is repeated as prose and tables in Sections 2–4 so the document remains usable either way.

## 1. System equation, as a diagram

Chapter 14 states: **AI system = Model + Context + Harness + Tools + Workflow + Memory/State + Controls + Evaluation + Runtime.** The diagram below arranges those nine components as a request/response flow rather than a flat list.

```mermaid
flowchart TB
    subgraph TRIGGER[Trigger]
        U[User request, event, or schedule]
    end

    subgraph CTX[Context layer]
        RET[Retrieval and knowledge service]
        MEM[Memory and state store]
        POL[Policy and instruction library]
        CA[Context assembler]
        RET --> CA
        MEM --> CA
        POL --> CA
    end

    subgraph HAR[Harness]
        LOOP[Execution loop]
    end

    subgraph MDL[Model layer]
        M1[Primary model]
        M2[Fallback model / route]
    end

    subgraph WF[Workflow and orchestration]
        DET[Deterministic function]
        EXP[Explicit workflow]
        AGT[Agent]
        MA[Multi-agent]
    end

    subgraph TOOLS[Tools]
        T1[Tool / action contract]
        T2[Enterprise API / system of record]
    end

    subgraph CTRL[Controls]
        GR[Guardrails]
    end

    subgraph OUT[Output and human interaction]
        VAL[Structured output and validation]
        HAI[Human review / approval / override]
    end

    subgraph EVAL[Evaluation]
        EV[Evaluation and regression suite]
    end

    subgraph RUN[Runtime / AgentOps]
        TRC[Version and trace record]
    end

    U --> CA
    CA --> LOOP
    LOOP --> M1
    M1 --> LOOP
    LOOP -.fallback.-> M2
    LOOP --> WF
    WF --> DET
    WF --> EXP
    WF --> AGT
    WF --> MA
    AGT --> T1
    MA --> T1
    T1 --> T2
    T1 --> LOOP
    LOOP --> GR
    GR --> VAL
    VAL --> HAI
    HAI --> OUTCOME[Outcome event]
    LOOP --> TRC
    TRC --> EV
    EV -.feedback.-> M1
    EV -.feedback.-> CA
```

## 2. Component-to-artifact map

| # | Component | OASIS engineering section | Design decision it must answer | Primary artifact |
|---|---|---|---|---|
| 1 | Intelligence-system specification | Ch. 14 §1 | What must the system understand, decide, generate or execute — and what is explicitly prohibited? | [Intelligence-System Blueprint](../Methodology/chapter-32-templates-checklists-and-tools.md#11-intelligence-system-blueprint) |
| 2 | Model layer (primary + fallback) | Ch. 14 §2 | Which model/route meets quality, cost and latency thresholds for this task? | Model Strategy and Benchmark |
| 3 | Data, retrieval and knowledge foundations | Ch. 14 §3 | What is the smallest sufficient, authoritative evidence set? | [Data and Knowledge Readiness Assessment](../Methodology/chapter-32-templates-checklists-and-tools.md#8-data-and-knowledge-readiness-assessment) |
| 4 | Context assembler | Ch. 14 §4 | What does the model see at this decision point, and is it authorized, attributed, fresh and bounded? | Context Architecture |
| 5 | Harness (execution loop) | Ch. 14 §6 | How does the task progress, recover and terminate? | Harness and Workflow Design |
| 6 | Workflow/orchestration selector | Ch. 14 §7 | Deterministic function, explicit workflow, single agent, or multi-agent — and why? | Harness and Workflow Design |
| 7 | Tools / action contracts | Ch. 14 §5; Ch. 17 | What can the system access or execute, under what controls? | [Tool and Integration Interface Specification](../engineering/tool-and-integration-interface-specification.md) |
| 8 | Memory and state store | Ch. 14 §8 | What persists, for whom, for how long, and with what correction rights? | Memory and State Policy |
| 9 | Guardrails / controls | Ch. 14 §10; Ch. 19 | Which layer enforces which limit, and what happens on breach? | Risk and Control Register |
| 10 | Output validation & human interaction | Ch. 14 §9 | What schema, evidence and approval does a human or downstream system require? | [Human–AI Workflow Blueprint](../Methodology/chapter-32-templates-checklists-and-tools.md#7-human-ai-workflow-blueprint) |
| 11 | Evaluation & regression suite | Ch. 14 §11 | What constitutes acceptable behavior and change? | [Evaluation Strategy and Dataset](../Methodology/chapter-32-templates-checklists-and-tools.md#9-evaluation-strategy-and-dataset) |
| 12 | Runtime / AgentOps trace | Ch. 14 §12; Ch. 21 | Which version of every component produced this outcome? | [Monitoring: Observability and Telemetry Specification](../monitoring/observability-and-telemetry-specification.md) |

## 3. Defense-in-depth overlay

Chapter 19's eight control layers map directly onto this architecture rather than sitting beside it as a separate concern. Apply controls at the point they are drawn, not only at the perimeter:

| Ch. 19 layer | Where it sits in this architecture |
|---|---|
| Input | Trigger → Context assembler boundary |
| Context | Inside the Context assembler (source trust, authorization filters, injection isolation) |
| Model | Model layer (instructions, safety behavior, restricted capabilities) |
| Tool | Tool/action contracts (allow lists, schemas, least privilege, spend limits) |
| Workflow | Workflow/orchestration selector (approvals, segregation of duties, checkpoints) |
| Output | Output validation stage (grounding, policy, privacy, schema checks) |
| Runtime | Harness execution loop (sandboxing, budgets, containment) |
| Operations | Runtime/AgentOps trace (monitoring, incident response, kill switch, audit) |

## 4. Selecting the orchestration pattern (Ch. 14 §7 decision rule)

```mermaid
flowchart TD
    Q1{Is the calculation<br/>fixed and rule-based?}
    Q1 -->|Yes| DET[Deterministic function]
    Q1 -->|No| Q2{Is the path known<br/>and enumerable?}
    Q2 -->|Yes| EXP[Explicit workflow]
    Q2 -->|No| Q3{Does the task need<br/>dynamic, open-ended choice?}
    Q3 -->|Yes| Q4{Does specialization, isolation,<br/>or parallelism give a<br/>measurable benefit?}
    Q3 -->|No| EXP
    Q4 -->|Yes| MA[Multi-agent system]
    Q4 -->|No| AGT[Single agent]
```

Default to the simplest option that satisfies the task. Multi-agent is justified by measured benefit, not by default sophistication — an unjustified multi-agent design is itself an architecture-review finding.

## 5. Tailoring this architecture

Per [Chapter 30 — Tailoring OASIS](../Methodology/chapter-30-tailoring-oasis.md), not every engagement needs every component populated at full depth. A deterministic-function-only system (bottom path in §4) may legitimately omit the Model, Memory and Multi-agent boxes — but should still complete the Controls, Output validation and Runtime trace components, since those apply regardless of how much of the system is "AI."

---

[← Back to Contents](../README.md) · [Chapter 14: Intelligence and Agent Engineering](../Methodology/chapter-14-intelligence-and-agent-engineering.md) · [Engineering: Tool and Integration Interface Specification →](../engineering/tool-and-integration-interface-specification.md)

© 2026 OASIS Methodology contributors. Licensed under the [MIT License](../LICENSE.md).
