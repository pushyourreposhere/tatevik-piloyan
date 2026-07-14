---
name: analyze
description: Combine the cleaned CBA series with peer policy rates and compute the comparison metrics (spread, direction, volatility, recent moves) using a throwaway script, verified by a separate independent script. Produces a finding (FND-NNN).
argument-hint: <the analytical question; defaults to "CBA vs peer central banks">
user-invocable: true
---

# Skill: analyze

Owned by **analyst**. Turns cleaned data into a numbered, verified, plain-language
finding using the ephemeral two-script pattern. Every figure must trace to a cell
or a logged computation (`.claude/rules/evidence-and-figures.md`).

## Preflight

1. Read the anchor, `analysis/_index.md` (next free `FND` id), and
   `analysis/TEMPLATE.finding.md`.
2. Confirm inputs exist: the cleaned CBA dataset (`clean-data`) and
   `data/peer-rates.csv` (`fetch-peer-rates`). If one is missing, that's a
   blocker — report it to Main Claude (which will dispatch the right skill).

## Steps

1. **Compute** — write an ephemeral **analysis script** `scratch/analyze_<slug>.py`
   that reads the cleaned CBA series + `peer-rates.csv` and computes, over a
   stated window:
   - CBA latest rate and its most recent change (bp, direction: cut/hold/hike);
   - peer median / range at the latest common `as_of`;
   - **spread** = CBA − each peer, and CBA − peer median (pp);
   - **volatility**: number (or std. dev.) of changes over the window for CBA.
   - **date comparability** — check the `as_of` dates. The CBA series and the peer
     rates may be *as of different dates* (the shipped sample CBA file ends before
     today, while web-fetched peer rates are current). Do **not** silently subtract
     a stale CBA rate from current peer rates. Either (a) compare each series at its
     own latest and record the date gap as a caveat with confidence downgraded, or
     (b) state plainly that a same-date comparison needs a refreshed CBA figure from
     the official source. Never present a stale-vs-current spread as if same-dated.
   Write the merged table to `analysis/combined-rates.csv` (include each figure's
   `as_of`). Mind units and the sign of each spread. **Then delete the analysis
   script.**
2. **Verify** — write a **separate, independent** verification script
   `scratch/verify_<slug>.py` that recomputes the headline numbers a different
   way from the **raw** cleaned cells (e.g. recompute the median by sorting, the
   spread by direct subtraction), `assert`s they match `combined-rates.csv` and
   the figures you're about to write, and prints `PASS`/`FAIL`. **Then delete it.**
3. **Write the finding** — copy `analysis/TEMPLATE.finding.md` to
   `analysis/FND-NNN-<slug>.md` and fill every section: answer-first; a key-figures
   table where each value cites a `DS`/`SRC`/Method origin; the **Method** section
   (prose record of the now-deleted script); the **Independent verification**
   table with the `PASS`/`FAIL` verdict; cause→effect interpretation
   (`.claude/rules/report-style.md`); caveats (**including any date mismatch between
   the CBA series and the peer rates**); a calibrated confidence rating.
4. **Register** — add the `FND-NNN` row to `analysis/_index.md`. Confirm
   `scratch/` is empty.

## QA (run before returning)

Run **`analysis-qa`** on the finding: every figure traceable; verification
verdict `PASS`; confidence matches the evidence; template complete; `scratch/`
empty. Fix flags; escalate an unfixable hard failure to Main Claude.

## Output / return

- `analysis/FND-NNN-<slug>.md`, `analysis/combined-rates.csv`, updated
  `analysis/_index.md`.
- The answer-first paragraph, ready to hand to `visualize`.

## Suggested next step

`visualize` (charts) then `presentation`.
