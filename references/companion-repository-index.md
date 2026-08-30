<!-- SPDX-License-Identifier: MIT -->

[← Back to Contents](../README.md)

# Companion Repository Index

OASIS is the methodology: what to do, in what order, and why. It deliberately stops short of being an implementation guide for any one chapter — that depth lives in a set of separate, independently-versioned companion repositories, each one built out from a specific chapter or cluster of chapters. This index is the map from a chapter to the repository that implements it, and back.

Each companion repository names OASIS as its source, and now also names its *sibling* companions, in its own README's "Relationship to companion repositories" section (see the Back-reference column below). This page is the reverse direction: from OASIS, to them.

## Part III: Intelligence-System Engineering and Assurance

Part III (Chapters 14–22) has a dedicated companion for every chapter except one.

| Chapter | Companion repository | Depth | Back-reference |
|---|---|---|---|
| [Ch. 14 — Intelligence and Agent Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md) | [Ageis](https://github.com/knowledgetrailsai/Ageis) | Primary companion — end-to-end agentic delivery practice | [Ageis README § Relationship to companion repositories](https://github.com/knowledgetrailsai/Ageis/blob/main/README.md#relationship-to-companion-repositories) |
| [Ch. 15 — Data and Knowledge Engineering](../methodology/chapter-15-data-and-knowledge-engineering.md) | [Forge](https://github.com/knowledgetrailsai/Forge) | Primary companion — full retrieval/knowledge-engineering depth | [Forge README § Relationship to Companion Repositories](https://github.com/knowledgetrailsai/Forge/blob/main/README.md#relationship-to-companion-repositories) |
| [Ch. 16 — Human–AI Workflow and Experience Engineering](../methodology/chapter-16-human-ai-workflow-and-experience-engineering.md) | [Loom](https://github.com/knowledgetrailsai/Loom) | Primary companion | [Loom README § Relationship to Companion Repositories](https://github.com/knowledgetrailsai/Loom/blob/main/README.md#relationship-to-companion-repositories) |
| [Ch. 17 — Enterprise Integration and Tool Engineering](../methodology/chapter-17-enterprise-integration-and-tool-engineering.md) | [Helm](https://github.com/knowledgetrailsai/Helm) (`07-tool-integration/`) | **Light** — tool-contract principles and one pattern catalogue exist; no dedicated deep companion yet | [Helm README § Relationship to companion repositories](https://github.com/knowledgetrailsai/Helm/blob/main/README.md#relationship-to-companion-repositories) |
| [Ch. 18 — Evaluation and Reliability Engineering](../methodology/chapter-18-evaluation-and-reliability-engineering.md) | [Verity](https://github.com/knowledgetrailsai/Verity) (primary, full depth); [Helm](https://github.com/knowledgetrailsai/Helm) (`04-learning-loop/`, production tie-in only) | Verity owns the methodology depth; Helm owns where it plugs into live operations — see Verity's [what-is-evaluation-and-reliability-engineering.md](https://github.com/knowledgetrailsai/Verity/blob/main/01-foundations/what-is-evaluation-and-reliability-engineering.md) for the division of ownership | [Verity README § Relationship to Companion Repositories](https://github.com/knowledgetrailsai/Verity/blob/main/README.md#relationship-to-companion-repositories) · [Helm README § Relationship to companion repositories](https://github.com/knowledgetrailsai/Helm/blob/main/README.md#relationship-to-companion-repositories) |
| [Ch. 19 — Security and Responsible AI Engineering](../methodology/chapter-19-security-and-responsible-ai-engineering.md) | [Compass](https://github.com/knowledgetrailsai/responsible-ai) (`14-ai-security/`) | Substantive — nine files covering threat modeling, supply chain, incident response, and securing traditional ML/GenAI/agentic AI separately | [Compass README § Relationship to companion repositories](https://github.com/knowledgetrailsai/responsible-ai/blob/main/README.md#relationship-to-companion-repositories) |
| [Ch. 20 — Governance, Compliance and Regulatory Engineering](../methodology/chapter-20-governance-compliance-and-regulatory-engineering.md) | [Compass](https://github.com/knowledgetrailsai/responsible-ai) (`03-ai-governance/`, `10-regulations-and-standards/`) | Substantive — jurisdiction-specific coverage (US federal/state, EU AI Act, UK, China, Singapore, India, Canada) plus governance-model and board-structure content | [Compass README § Relationship to companion repositories](https://github.com/knowledgetrailsai/responsible-ai/blob/main/README.md#relationship-to-companion-repositories) |
| [Ch. 21 — Deployment, Operations and AgentOps](../methodology/chapter-21-deployment-operations-and-agentops.md) | [Helm](https://github.com/knowledgetrailsai/Helm) | Primary companion — full depth | [Helm README § Relationship to companion repositories](https://github.com/knowledgetrailsai/Helm/blob/main/README.md#relationship-to-companion-repositories) |
| [Ch. 22 — Economics, FinOps and Sustainability](../methodology/chapter-22-economics-finops-and-sustainability.md) | [Fulcrum](https://github.com/knowledgetrailsai/oasis-fulcrum) | Primary companion | [Fulcrum README § Relationship to companion repositories](https://github.com/knowledgetrailsai/oasis-fulcrum/blob/main/README.md#relationship-to-companion-repositories) |

**Known gap:** Chapter 17 has no repository at Forge/Loom/Verity's depth. Helm's tool-contract principles are sound as far as they go but do not yet cover a full pattern catalogue across enterprise system types (CRM, ERP, ticketing, and similar).

## Cross-cutting companions (not tied to one chapter)

| Repository | Relationship to OASIS | Back-reference |
|---|---|---|
| [Nexus](https://github.com/knowledgetrailsai/Nexus) | The opportunity catalog behind [Chapter 5 — Opportunity Portfolio and Transformation Horizons](../methodology/chapter-05-opportunity-portfolio-and-transformation-horizons.md): which use case, in which domain and function, before a use case enters the Chapter 7 lifecycle. | [Nexus README § Relationship to companion repositories](https://github.com/knowledgetrailsai/Nexus/blob/main/README.md#relationship-to-companion-repositories) |
| [Axiom](https://github.com/knowledgetrailsai/Axiom) | Background reference on AI model architectures (Transformers, MoE, SSMs, and related families) underpinning the model-selection decisions in [Chapter 14 §2 — Model Engineering](../methodology/chapter-14-intelligence-and-agent-engineering.md#2-model-engineering). Not itself an OASIS chapter companion — it is architecture-level background knowledge, not methodology. | [Axiom README § Relationship to companion repositories](https://github.com/knowledgetrailsai/Axiom/blob/main/README.md#relationship-to-companion-repositories) |

## Reading this index

A companion repository turns "what OASIS says to do" into "the actual schema, checklist, or runbook to use." When a chapter and a companion disagree on a specific point, the companion is more likely to be current on implementation detail; the chapter is more likely to be current on methodology intent. Flag the discrepancy rather than assuming either side is automatically right.

---

[← Back to Contents](../README.md)
