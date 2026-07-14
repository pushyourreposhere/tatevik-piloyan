---
name: clean-qa
description: Two-round QA for a cleaned dataset + its cleaning log — checks every detected issue has an action, the independent verification passed, no values were invented, and no scripts were left behind. Called by data-steward after clean-data; also user-invocable.
argument-hint: <the *-cleaned.csv or its cleaning log>
user-invocable: true
---

# Skill: clean-qa

Checks a cleaning result against `.claude/rules/qa.md`, `ephemeral-compute.md`,
and `evidence-and-figures.md`. Returns **PASS** / **NEEDS-REWORK**.

## Round 1 — Compliance

1. **(hard)** A `analysis/<name>-cleaning-log.md` exists and lists every detected
   issue (row/column/issue/action) plus the detection rules used.
2. **(hard)** A `data/<name>-cleaned.csv` exists and the **raw file is untouched**
   (archive-then-analyze).
3. **(hard)** The `DS-NNN` status is updated to `cleaned` in `data/_index.md`.

## Round 2 — Integrity

4. **(hard)** Independent verification ran and its verdict is **PASS**, recorded
   in the log (a separate `verify_*.py` that recomputed from the raw file).
5. **(hard)** No invented values — missing cells were left as explicit gaps or
   documented as unambiguous typo corrections, never filled with a guess
   (`evidence-and-figures.md`).
6. **(hard)** The cleaned file actually satisfies its claims: re-check no
   duplicates remain, dates are `YYYY-MM-DD`, no value is outside the stated
   domain range, and the row-count delta equals the duplicates dropped. (Spot-check
   a few rows directly; if in doubt, this is a hard fail.)
7. **(hard)** **`scratch/` is empty** (only `.gitkeep`); no `.py` file exists in
   `data/`, `analysis/`, or elsewhere persisted.
8. **(soft)** Ambiguous fixes (e.g. a possible typo that couldn't be confirmed)
   are flagged in the log's caveats rather than silently changed.

## Verdict

Fix in place where possible. Any unfixed **hard** check ⇒ **NEEDS-REWORK**; a
verification FAIL or a leftover script is a hard, escalatable failure — do not let
the artifact pass. All hard checks pass ⇒ **PASS**. Record rounds + verdict in the
log.
