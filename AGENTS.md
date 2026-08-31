# Agent instructions for this repository

This file is for any AI coding agent working in this repo — read it before making changes. It complements, not replaces, `README.md` and `llms.txt` (a machine-readable map of this repo's key docs and its OASIS-ecosystem siblings).

## What this repo is

OASIS is the master OASIS methodology — the 33-chapter enterprise AI transformation, delivery and assurance handbook that the nine companion repos each implement in operating detail.

## Before you commit

- Run no automated checker exists here — manually verify every link you touched: `grep -n "](" <file>` then confirm each target with `ls`/`find` before committing. Do not commit a link you have not verified resolves.
- This repo has no `INDEX.md`; the README's own index table is the source of truth — update it if you add, rename, or remove a file.
- This repo has no `CONTRIBUTING.md` yet; follow the structural conventions already present in the existing files rather than introducing a new pattern.
- Never fabricate a file path or URL, in this repo or a sibling's. If you are not certain a target exists, check with `ls`/`find` (or the sibling's `llms.txt`/`INDEX.md`) before writing the link.

## Linking to sibling repositories

This repo is one of ten in the knowledgetrailsai OASIS ecosystem: Ageis, Forge, Loom, Helm, Verity, Compass, Fulcrum, Nexus, Axiom. When you add a cross-repo link, use the exact repository name and default branch — they are not uniform:

- OASIS (`knowledgetrailsai/OASIS`) — default branch `main`
- Ageis (`knowledgetrailsai/Agentic-Engineeering-SDLC`) — default branch `main`
- Forge (`knowledgetrailsai/Forge`) — default branch `master`
- Loom (`knowledgetrailsai/LOOM`) — default branch `master`
- Helm (`knowledgetrailsai/HELM`) — default branch `main`
- Verity (`knowledgetrailsai/VERITY`) — default branch `master`
- Compass (`knowledgetrailsai/responsible-ai`) — default branch `main`
- Fulcrum (`knowledgetrailsai/OASIS-AI-FINOPS`) — default branch `main`
- Nexus (`knowledgetrailsai/Nexus`) — default branch `main`
- Axiom (`knowledgetrailsai/AXIOM`) — default branch `master`

Prefer linking to a specific file at the exact section/row a claim maps to, not a generic "see this whole repo" pointer — that is the standard this ecosystem holds itself to.

## Writing style

Match the existing prose: short, direct sentences, one idea each. Explain a term of art in plain words the first time it appears on a page rather than assuming the reader already has the vocabulary. Avoid rhetorical flourishes that exist to sound authoritative rather than to inform (e.g. "X isn't Y — it's Z" constructions, stacked em-dash clauses). This is a reference meant to teach, not to impress.
