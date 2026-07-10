# CLAUDE.md

## 1. What this workspace does
Produces a recurring research report on the Central Bank of Armenia's refinance rate — the decision, its drivers, and supporting charts — as a versioned artifact in `03-registry/`.

## 2. What input it accepts
Only what's placed in `05-inputs/` for the current cycle: rate-decision announcements, CPI/FX data, source PDFs, user notes. Nothing outside that folder counts as input for a run.

## 3. What exists, and when to read it
- `CLAUDE.md` (this file) — every run, first.
- `03-registry/` — before starting, to see prior runs and avoid duplicating one.
- `05-inputs/` — when gathering facts for the current cycle.
- `02-template/` — when shaping the output.
- `.claude/rules/` — before drafting or reviewing, for the quality bar.
- `.claude/skills/` — when executing a task, for the how-to.
- `.claude/agents/` — only when delegating a subtask to a specific agent.
- `04-chart-packs/` — only when referencing or updating a specific report's charts.

## 4. Load order for a new task
1. This file
2. `03-registry/`
3. `05-inputs/`
4. `02-template/`
5. `.claude/rules/`
6. `.claude/skills/`

## 5. The one safety standard
Never put real (non-public) Armenia CBR or financial data anywhere under `.claude/`. That folder is the reusable kit — only data explicitly marked public and synthetic may live in `.claude/samples-public-synthetic/`.
