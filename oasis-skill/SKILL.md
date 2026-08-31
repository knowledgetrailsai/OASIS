<!-- SPDX-License-Identifier: MIT -->
---
name: oasis-methodology
description: Guide a user through the OASIS enterprise AI transformation methodology — find the right lifecycle phase, pick the right artifact for the decision at hand, and fill it against its JSON Schema. Use when a task involves starting, governing, evaluating, releasing or scaling an AI/agentic initiative under OASIS.
---

# OASIS Methodology Skill

This is a lightweight skill for any agent platform (Claude, Codex, or another agent runtime) working with the OASIS methodology. It does not replace reading the methodology — it tells an agent where to look and in what order, so it doesn't have to re-derive the ecosystem's structure from scratch every time.

## What OASIS is

OASIS (Outcome-as-a-Service using Intelligence Systems) is a 33-chapter enterprise AI transformation methodology with a six-phase lifecycle, six decision gates, and twenty numbered artifacts that carry every major decision. Nine companion repositories implement specific engineering disciplines in operating detail. Full map: [`llms.txt`](../llms.txt).

## Files this skill relies on

| File | What it's for |
|---|---|
| [`oasis-manifest.yaml`](../oasis-manifest.yaml) | The full machine index: parts, chapters, companion repos, phases, artifacts. Start here for anything structural. |
| [`oasis-lifecycle.yaml`](../oasis-lifecycle.yaml) | The six phases and six decision gates, structured: purpose, key artifacts, decision options, minimum evidence. |
| [`References/task-to-artifact-routing-table.md`](../References/task-to-artifact-routing-table.md) | Plain-language task → artifact lookup. Start here when the user describes a task rather than naming an artifact. |
| [`Schemas/<NN>-<slug>.schema.json`](../Schemas/) | One JSON Schema per artifact (fields, types, enums, required fields). The source of truth for what a filled artifact must contain. |
| [`Examples/`](../Examples/) | Worked, fictional example artifacts showing what a good instance looks like. |
| [`methodology/chapter-32-templates-checklists-and-tools.md`](../methodology/chapter-32-templates-checklists-and-tools.md) | Why each artifact exists and what separates a strong instance from a weak one — read this before filling one in, not just the schema. |
| [`Tools/`](../Tools/) | The human-fillable YAML/table version of each artifact, with inline guidance comments. |

## Workflow

1. **Identify the task.** If the user names an artifact directly, skip to step 3. Otherwise, match their task against [`References/task-to-artifact-routing-table.md`](../References/task-to-artifact-routing-table.md).
2. **Confirm the phase and gate.** Look up the artifact's `phase` in [`oasis-lifecycle.yaml`](../oasis-lifecycle.yaml) to understand what decision it feeds and what gate it supports. This matters because an artifact filled out of sequence (e.g. an Autonomy Matrix before an Outcome Contract exists) is usually a sign the user is skipping a step, not that the routing was wrong — say so.
3. **Read the chapter-32 section for that artifact** (the anchor is in the manifest's `artifacts` entry) before filling anything in. It states the decision the artifact supports and the difference between a strong and weak instance — the schema alone tells you the shape, not the judgment.
4. **Fill the artifact against its JSON Schema**, not free-form. Every field in the schema traces to a real decision input named in Chapter 32; do not add fields the schema doesn't define, and do not silently drop a required field — if it's genuinely not applicable, say so explicitly rather than omitting it.
5. **Apply the Template Use Rule.** Chapter 32's [PRACTICALITY rule](../methodology/chapter-32-templates-checklists-and-tools.md#template-use-rule): fill only what the decision actually needs. A field left blank should be a deliberate call ("this doesn't apply because...") not an oversight.
6. **Check [`Examples/`](../Examples/)** for a worked instance of the same artifact before producing your own — matching its level of specificity (concrete names, real numbers, not placeholders) is the bar for "strong," per Chapter 32's own strong-vs-weak framing.
7. **If the task spans multiple artifacts** (e.g. "start a new initiative," "prepare for go-live"), use the routing table's multi-artifact rows or `oasis-lifecycle.yaml`'s `key_artifacts` list for that phase, and produce them in phase order — later artifacts reference earlier ones by name (e.g. the Outcome Contract's `charter_reference` field).

## Platform notes

- **Claude / Claude Code / Cowork:** load this file as a Skill (the YAML frontmatter above follows the standard `SKILL.md` convention).
- **Codex and other agent platforms using `AGENTS.md`:** this repository's own [`AGENTS.md`](../AGENTS.md) points here; add a line such as "For OASIS artifact tasks, read `oasis-skill/SKILL.md` first" to your own project's `AGENTS.md` if you're consuming OASIS from another repository.
- **Any other agent runtime:** this file is plain Markdown with no platform-specific syntax beyond the frontmatter block above — safe to load as a system prompt, a retrieved document, or a tool-use reference.

## Guardrails

- Never fabricate a companion-repository link or file path. Verify with the manifest, `llms.txt`, or a direct file check before citing one — this ecosystem holds every cross-reference to that standard (see [`AGENTS.md`](../AGENTS.md)).
- An artifact is a decision-support instrument, not compliance paperwork. If a user is filling one out just to have a complete-looking document, point them back to the [Template Use Rule](../methodology/chapter-32-templates-checklists-and-tools.md#template-use-rule).
- Exactly one name belongs in an "Accountable" field (artifact 19) — flag it if a draft has two.
- A Decision-Gate Record (artifact 20) with no `expiry` on a conditional pass or hold is incomplete — Chapter 13 is explicit that this is the field most often left blank and how a conditional pass quietly becomes permanent.
