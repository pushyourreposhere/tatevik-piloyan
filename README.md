# Central-Bank Rate Analysis Kit

A working, agentic Claude Code environment for **safe, AI-assisted data analysis**.
It takes a data question from raw file to a **verified, sourced, management-ready
HTML presentation** — cleaning data, comparing figures, visualizing them, and
writing an executive summary, all under a Safe-Zone discipline with independent
verification and human-in-the-loop checkpoints.

It is a teaching environment, built on the agentic-context-engineering method
(the four mechanisms — `CLAUDE.md`, rules, skills, agents — plus stable IDs,
registries, business-logic templates, and a two-round QA system).

## The flagship task

Compare the **Central Bank of Armenia (CBA) refinancing rate** to peer central
banks:

1. Bring the local CBA rate file into the Safe Zone and clean it.
2. Fetch peer policy rates (Fed, ECB, BoE, …) from the open web — each cited.
3. Combine and analyze — spread, direction, volatility.
4. Visualize as charts a manager reads in ten seconds.
5. Assemble and verify a self-contained HTML presentation.

## Setup

1. **Open Claude Code with this `Demo/` folder as the working directory.** The kit
   is self-contained: `CLAUDE.md` is the root switchboard, `.claude/` holds the
   agents / rules / skills, and the content folders hold the data and outputs.
2. **Python 3** is used for data work. No install is needed for CSVs (standard
   library). If you point the kit at an Excel file (`.xlsx`), it will create a
   disposable `.venv` and install `pandas`/`openpyxl` automatically — then throw
   it away. If that install can't run, it falls back to CSV and tells you.
3. **Web access** (`WebSearch`/`WebFetch`) is used only to fetch public peer
   rates. A Safe-Zone reminder fires before each web call.

## Run it

The whole flagship, end to end:

```
/workflow "Compare the CBA refinancing rate to peer central banks for a board briefing"
```

…or step by step (each step is a skill; each producing step is checked by a QA
skill before it's accepted):

```
/intake data/cba-refinance-rate.csv     # classify (Safe Zone) + register  → source-qa
/clean-data DS-001                        # fix missing/dupes/outliers/dates → clean-qa
/fetch-peer-rates                         # peer rates from the web, cited   → source-qa
/analyze "CBA vs peers"                   # spread / direction / volatility  → analysis-qa
/visualize FND-001                        # self-contained SVG charts        → presentation-qa
/presentation FND-001                     # self-contained HTML presentation → presentation-qa
/qa-check presentations/RPT-001-*.html    # independent re-check on demand
```

## How it stays safe and honest (the three non-negotiables)

1. **Classify before you use or send.** Every dataset is public / internal /
   restricted. Restricted data never reaches a web tool or an external prompt.
   The shipped `data/internal/loan-portfolio-CONFIDENTIAL.csv` is a restricted
   example to practice this. → `.claude/rules/safe-zone.md`
2. **No unsourced figures.** Every number traces to a dataset cell, a logged
   computation, or an official source in `sources/source-registry.md`. "Not
   found" is an acceptable answer; a plausible guess is not. →
   `.claude/rules/evidence-and-figures.md`
3. **Compute with throwaway scripts, verify independently.** Analysis runs as a
   disposable Python script (deleted after), then a *separate* verification
   script recomputes and checks it (also deleted). Only the data, charts, HTML,
   and a markdown record of the method + verdict survive. →
   `.claude/rules/ephemeral-compute.md`

## What's in here

| Path | What it is |
|---|---|
| `CLAUDE.md` | Root switchboard — read the map here |
| `context/analysis-brief.md` | The anchor — the decision, vocabulary, Safe-Zone posture |
| `.claude/rules/` | The five standards (referenced by CLAUDE.md, the folder notes, and each agent/skill) |
| `.claude/skills/` | The procedures — producing skills + their QA skills |
| `.claude/agents/` | `data-steward`, `analyst`, `presenter` |
| `data/` | Datasets + registry (shipped: a dirty CBA rate file + a peer-rates template + a restricted example) |
| `analysis/` | Cleaning logs, combined data, findings + registry + finding template |
| `presentations/` | Charts + HTML presentations + registry + HTML template |
| `sources/` | Source registry (SRC-NNN) + evidence policy |
| `scratch/` | The only place throwaway scripts live — empty at rest |
| `TRAINER-GUIDE.md` | Maps the 8-meeting course onto the skills/exercises |

## The shipped sample data

- `data/cba-refinance-rate.csv` (and `.xlsx`) — a monthly CBA refinancing-rate
  series that is **deliberately dirty**: two missing values, one duplicate row,
  one out-of-range outlier (`95.0` where `9.5` was meant), mixed date formats, and
  a stray percent sign. It is **illustrative only** (source tier P4) — refresh
  from the official CBA before publishing any figure.
- `data/peer-rates.template.csv` — the empty schema `fetch-peer-rates` fills with
  real, web-sourced peer rates. No fabricated numbers are shipped.
- `data/internal/loan-portfolio-CONFIDENTIAL.csv` — a small, obviously-fictional
  restricted file for the classification exercise. It must never go to a web tool.

## A note on outputs

The kit ships **empty of results** (no findings, charts, or presentations yet) so
each cohort produces its own. Every artifact you generate is registered with a
stable ID in the relevant `_index.md`, verified, and QA'd before it's accepted.
Presentations are self-contained HTML — open them in any browser offline, or
publish one as an Artifact for review.
