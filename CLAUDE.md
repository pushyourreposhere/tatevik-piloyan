# Central-Bank Rate Analysis Kit — Navigation

This workspace turns a data question into a **verified, sourced, management-ready
HTML presentation** — safely. Its flagship job: compare the CBA refinancing rate
to peer central banks (local file + public web data) → clean → analyze →
visualize → present. It is a teaching environment for safe, AI-assisted data
work, built on the agentic-context-engineering method.

This file is the map (a switchboard, not an encyclopedia). Read `README.md` once
when setting up. Read `context/analysis-brief.md` first every session — it is the
anchor. Come back here to find a specific piece.

## Quick navigation

| Directory | Contains | Load when |
|---|---|---|
| `context/analysis-brief.md` | **Anchor**: the decision, the flagship task, vocabulary, Safe-Zone posture | First, every session |
| `.claude/rules/` | The five standards (read via this file, the folder notes, and each agent/skill): Safe Zone, evidence, ephemeral compute, report style, QA | Before producing anything |
| `.claude/skills/` | The procedures (create + QA), one folder each | To actually do the work |
| `.claude/agents/` | The four domain specialists | If delegating a sub-task |
| `data/` | Raw datasets + `_index.md` (DS-NNN) | Importing or reading source data |
| `analysis/` | Cleaning logs, combined data, findings + `_index.md` (FND-NNN) + finding template | Analyzing or reading results |
| `presentations/` | Charts + HTML presentations + `_index.md` (CHT/RPT-NNN) + HTML template | Building or reading outputs |
| `web-research/` | Web sources + research briefs: `sources/_index.md` (WRS-NNN) + `findings/_index.md` (WRB-NNN) + brief template | Researching a question on the open web |
| `sources/` | `source-registry.md` (SRC-NNN) + `evidence-policy.md` | Any time a figure needs a citation |
| `scratch/` | The **only** place throwaway `.py` scripts may live — emptied after every run | Never persist anything here |

## Key rules — the three non-negotiables

1. **Classify before you use or send.** Every dataset is public / internal /
   restricted (`rules/safe-zone.md`). Restricted data never leaves the machine
   (no web tools, no external prompt). Decide this *before* touching the data —
   it is a human-in-the-loop checkpoint.
2. **No unsourced figures.** Every number in any output traces to a dataset
   cell, a logged ephemeral computation, or an official source in
   `sources/source-registry.md` (`rules/evidence-and-figures.md`). "Not sourced
   / not found" is an acceptable answer — never invent a plausible value.
3. **Compute with throwaway scripts, then verify independently.** Analysis runs
   as a disposable Python script in `scratch/`, deleted right after; then a
   *separate* verification script recomputes and checks it, and is also deleted
   (`rules/ephemeral-compute.md`). Only data/charts/HTML and the markdown record
   of the method + verdict persist. `scratch/` is empty at rest.

## Stable IDs

`DS-NNN` dataset · `SRC-NNN` source · `FND-NNN` finding · `CHT-NNN` chart ·
`RPT-NNN` report/presentation. Web-research (`web-research/`) keeps its own
folder-local ids: `WRS-NNN` web source · `WRB-NNN` research brief. Never reuse or
delete an ID (mark deprecated). Entity files are `PREFIX-NNN-slug`; always pair an
ID with its human name.

## Context-loading priority (when context is tight)

1. `context/analysis-brief.md` (anchor) →
2. the applicable rule(s) in `.claude/rules/` →
3. the skill that owns the procedure →
4. the relevant template (`analysis/TEMPLATE.finding.md`,
   `presentations/TEMPLATE.presentation.html`) →
5. the relevant `_index.md` registry — read it before creating (avoid
   duplicating an ID) and update it after finishing.

## Available agents (Main Claude orchestrates; it does not author entities itself)

| Agent | Owns | QA skill it runs on its own output before returning |
|---|---|---|
| `data-steward` | intake, Safe-Zone classification, web-rate fetch, cleaning | `source-qa`, `clean-qa` |
| `analyst` | combine + compute metrics/trends → findings | `analysis-qa` |
| `presenter` | KPIs, charts, executive summary, HTML presentation | `presentation-qa` |
| `web-researcher` | crawl the open web → sourced research brief (WRS/WRB) | `research-qa` |

Every agent's lifecycle is **preflight → create → qa → fix → qa → return**. An
artifact never leaves an agent until its QA skill returns PASS; an unfixable hard
failure is a **blocker** — the agent stops and reports to Main Claude rather than
returning failing work. Agents never create outside their own domain; they report
the missing dependency to Main Claude, which dispatches the right specialist.

## Tool policy

- `WebSearch` / `WebFetch` are allowed **only** to gather public figures (peer
  central-bank rates) from official sources. Never send internal or restricted
  data to a web tool. A soft reminder fires before each web call.
- Data processing uses `python3` via **throwaway scripts in `scratch/`** only. If
  a step needs pandas/openpyxl (e.g. reading `.xlsx`), create a disposable
  `.venv` and install into it; otherwise the Python standard library (`csv`,
  `statistics`) is enough for CSV. Either way, delete the script when done.
- Charts and presentations are **self-contained HTML** (inline SVG/CSS, no
  external hosts) so they render offline and can be published as an Artifact.

## Run it

Open Claude Code with this `Demo/` folder as the working directory, then:

```
/workflow "Compare the CBA refinancing rate to peer central banks for a board briefing"
```

or run the steps individually — `/intake`, `/clean-data`, `/fetch-peer-rates`,
`/analyze`, `/visualize`, `/presentation`, and `/qa-check` on any artifact.
`TRAINER-GUIDE.md` maps each course meeting to the skill that does its work.
