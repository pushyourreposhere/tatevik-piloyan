# Cleaning Log — CBA refinancing rate (DS-002)

- **Dataset**: DS-002 — CBA refinancing rate (monthly), class **public** (SRC-001, tier P4 shipped illustrative sample).
- **Raw (archived, untouched)**: `data/cba-refinance-rate.csv`
- **Cleaned output**: `data/cba-refinance-rate-cleaned.csv`
- **Date**: 2026-07-24
- **Method**: ephemeral two-script pattern (`.claude/rules/ephemeral-compute.md`) — a disposable analysis script wrote the cleaned CSV; a separate, independently-written verification script re-read the RAW cells and re-checked every claim. Both scripts lived only in `scratch/` and were deleted immediately after running. Standard library (`csv`) only; no `.xlsx`, so no venv needed.

## Detection rules used

- **Date format**: normalize every date to ISO `YYYY-MM-01`. Recognized variants: `YYYY-MM-DD` (already ISO), `YYYY/MM/DD`, `DD/MM/YYYY`, and `"<Month> YYYY"`. The `01/03/2023` token is read as **DD/MM/YYYY → 2023-03-01** (not MM/DD): it sits between 2023-02-01 and 2023-04-01 and carries 10.75, so March is the only reading that preserves the monthly sequence; MM/DD would produce a second January row and break the series.
- **Numeric rate**: strip a trailing `%`, parse as float. Blank/empty → explicit gap (`None`), never invented.
- **Duplicates**: exact identical `(date, rate)` pairs; keep first, drop the rest.
- **Out-of-range anomaly**: plausible policy-rate domain **0–25%**. Any value outside is treated as a decimal-place typo candidate; corrected only when the intended value is unambiguous from neighbours.

## Issues found and actions taken

| Raw line | Raw date | Raw rate | Issue | Action | Result |
|---|---|---|---|---|---|
| 4 | `01/03/2023` | 10.75 | Date format DD/MM/YYYY | Normalized to ISO | `2023-03-01, 10.75` |
| 9 | `2023-08-01` | *(blank)* | Missing value | Left as explicit gap (see below) | `2023-08-01,` (empty) |
| 10 | `2023-09-01` | **95.0** | Out-of-range outlier / decimal-place typo | Corrected 95.0 → 9.5 (÷10), justified from context | `2023-09-01, 9.5` |
| 14/15 | `2024-01-01` | 9.25 | Duplicate row (identical `2024-01-01, 9.25` twice) | Dropped the second occurrence | one `2024-01-01, 9.25` |
| 17 | `March 2024` | 8.75 | Date format "Month YYYY" | Normalized to ISO | `2024-03-01, 8.75` |
| 19 | `2024-05-01` | *(blank)* | Missing value | Left as explicit gap (see below) | `2024-05-01,` (empty) |
| 23 | `2024/09/01` | 7.5 | Date format YYYY/MM/DD | Normalized to ISO | `2024-09-01, 7.5` |
| 25 | `2024-11-01` | `7.25%` | Stray `%` sign in numeric field | Stripped `%`, parsed numeric | `2024-11-01, 7.25` |

All other rows carried through unchanged (verified by numeric equality, raw vs cleaned).

## How the outlier was handled (2023-09-01 = 95.0)

Treated as a **decimal-place typo correction**, not a silent change. The domain
rule flags 95.0 as impossible for this policy series. The surrounding, sourced
values are 2023-07-01 = 10.0 and 2023-11-01 = 9.25, with 2023-10-01 = 9.5; a
value of **9.5** (= 95.0 ÷ 10) is the only reading that fits the monotonic
decline between the neighbours (9.25 ≤ 9.5 ≤ 10.0). The correction is
unambiguous, so it is applied and logged here as a correction. This is derived
from existing sourced cells — no value was invented.

## How the two blanks were handled (2023-08-01, 2024-05-01)

**Left as explicit gaps** (empty rate cell), **not** filled. Method chosen:
*omit the value, keep the month row*. Rationale: filling either blank (e.g. by
interpolation or carry-forward) would create a figure with no source, violating
`evidence-and-figures.md` Rule 0 (never fabricate a number). A policy rate is set
by discrete decisions, so interpolation is not a defensible reconstruction. The
month rows are retained (so the monthly cadence is preserved and the gap is
visible) but their rate is blank and flagged here. Downstream analysis must treat
these as missing, not zero.

## Row accounting

- Raw data rows (excl. header): **31**
- Exact duplicates dropped: **1** (`2024-01-01, 9.25`)
- Cleaned data rows: **30** (Jan 2023 → Jun 2025, one row per month; 2 rows carry a blank rate)
- Row-count delta (31 − 30 = 1) equals duplicates dropped. ✓

## Independent verification

A separate `scratch/verify_cba.py` (written independently of the analysis script)
re-read the **raw** file and recomputed/re-validated from scratch, asserting:
cleaned header correct; all dates valid ISO `YYYY-MM-DD`; no duplicate dates;
sorted ascending; all numeric rates within 0–25%; row-count delta equals
duplicates dropped (=1); raw and cleaned month sets identical; 95.0→9.5
correction sits within its neighbours; both blanks preserved as empty gaps; the
`7.25%` stray-`%` normalized; and every non-blank, non-outlier raw value carried
through unchanged by numeric equality.

**Verification verdict: PASS.** Both ephemeral scripts were deleted after running;
`scratch/` contains only `.gitkeep`.

## First / last cleaned data points

- First: **2023-01-01 = 10.75%**
- Last: **2025-06-01 = 6.5%**

## Caveats / open questions

- Source is the **shipped illustrative sample** (SRC-001, tier **P4** — not
  authoritative). Refresh from the official CBA before any figure is published.
- Two months (2023-08, 2024-05) have **no rate**; they are honest gaps, not zeros.

## QA

- **clean-qa**: 2 rounds run, verdict **PASS** (2026-07-24). See notes below.
