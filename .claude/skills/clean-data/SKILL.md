---
name: clean-data
description: Detect and fix data-quality issues (missing values, duplicates, errors, format inconsistencies, anomalies) in a registered dataset using a throwaway Python script, then verify the result with a separate independent script. Writes a cleaned copy plus a cleaning log.
argument-hint: <DS-NNN or path to a registered dataset>
user-invocable: true
---

# Skill: clean-data

Owned by **data-steward**. Turns a raw, dirty dataset into a cleaned copy plus a
log of every change — using the ephemeral two-script pattern
(`.claude/rules/ephemeral-compute.md`). The raw file is never overwritten
(archive-then-analyze).

## Preflight

1. Confirm the dataset is registered in `data/_index.md` and its class is
   recorded (`public`/`internal`). If it's `restricted`, stop — it must be
   anonymized first (`.claude/rules/safe-zone.md`).
2. Read the header and a sample of rows to understand columns and expected types.

## Steps

1. **Detect** — write an ephemeral **analysis script** `scratch/analyze_<slug>.py`
   (stdlib `csv`/`statistics`; use the disposable `.venv` with pandas only if the
   input is `.xlsx`) that flags, per column:
   - **missing** values (blank / NA);
   - **duplicate** rows;
   - **type/format errors** (e.g. mixed date formats → normalize to `YYYY-MM-DD`;
     non-numeric in a numeric column);
   - **out-of-range anomalies** (a rate of `95.0` where the series sits near
     `9.5`; use a sane domain range and/or an IQR/z-score check — state the rule).
2. **Fix** — in the same script, apply defensible fixes and record each one:
   drop exact duplicates; normalize dates; correct an obvious decimal-place typo
   **only if** the intended value is unambiguous (else flag, don't guess); leave
   genuinely-missing values as explicit gaps (do **not** invent a value —
   `.claude/rules/evidence-and-figures.md`). Write the result to
   `data/<name>-cleaned.csv`. **Then delete the analysis script.**
3. **Verify** — write a **separate, independent** verification script
   `scratch/verify_<slug>.py` that re-reads the **raw** file and the cleaned file
   and asserts: no remaining duplicates; all dates match `YYYY-MM-DD`; no value
   outside the domain range; row-count change equals the number of dropped
   duplicates; every non-dropped raw row maps to a cleaned row. It prints
   `PASS`/`FAIL` with specifics. **Then delete the verification script.**
4. **Log** — write `analysis/<name>-cleaning-log.md`: a table of every issue
   found (row, column, issue, action) + the detection rules used + the
   verification verdict. Confirm `scratch/` is empty.
5. **Register** — set the `DS-NNN` status to `cleaned` in `data/_index.md` and
   note the cleaned file.

## QA (run before returning)

Run **`clean-qa`** on the cleaned dataset + log: all detected issues have an
action; the independent verification verdict is `PASS`; no `.py` remains;
`scratch/` empty; no invented values. Fix flags; escalate an unfixable hard
failure (e.g. verification FAIL) to Main Claude — do not return failing work.

## Output / return

- `data/<name>-cleaned.csv`, `analysis/<name>-cleaning-log.md`, updated
  `data/_index.md`.
- A plain-language summary: what was dirty, what was fixed, what was left as an
  honest gap, and the verification verdict.

## Suggested next step

`fetch-peer-rates` (if not done) then `analyze`.
