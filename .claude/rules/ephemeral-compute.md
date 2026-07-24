# Rule: Ephemeral Compute + Independent Verification

**Applies to** all data processing (skills that touch `data/`, `analysis/`, and
`scratch/`). It is referenced by the clean-data and analyze skills and their agents
— follow it whenever you compute anything over data.

Data work in this workspace is done by **disposable** Python scripts, not by
scripts that live in the repo. The scripts are transient tooling; the artifacts
(cleaned data, computed metrics, charts) and the markdown record of *how* the
numbers were made are what persist. This keeps the workspace auditable by reading
it, and forces every result to be independently re-checked.

## Core rule

For any computation over data, run **two** throwaway scripts in sequence, each
deleted immediately after it finishes:

1. **Analysis script** — reads the data, does the work, writes the artifact
   (cleaned CSV, combined CSV, metrics). Then **delete it**.
2. **Verification script** — written **independently** of the analysis script
   (do not reuse its code or its intermediate values): it re-reads the *raw*
   inputs, recomputes the key results from scratch, `assert`s them against the
   artifact, and prints `PASS` or `FAIL` with specifics. Then **delete it**.

Record, in the finding/cleaning-log, the method in prose and the verification
verdict. That markdown is the surviving audit trail — the code is gone on
purpose.

## Where scripts live

- Scripts may be written **only** under `scratch/`, named
  `scratch/analyze_<slug>.py` / `scratch/verify_<slug>.py`.
- A `.py` file must **never** be written to `data/`, `analysis/`,
  `presentations/`, or anywhere else that persists.
- `scratch/` must be **empty** (except `.gitkeep`) when a skill returns. Deleting
  the scripts is part of the skill, not an afterthought.

## Requirements

| Requirement | Standard | Fail condition |
|---|---|---|
| Two-script pattern | Analysis and verification are separate scripts | One script that both computes and "checks" itself |
| Independent verification | The verifier recomputes from raw inputs, not from the analysis script's outputs or code | Verifier just re-prints the analysis result |
| Scripts deleted | Both scripts removed immediately after running (`rm scratch/…py`) | Any `.py` left behind after the skill returns |
| Clean at rest | `scratch/` contains only `.gitkeep` between runs | Stray scripts, `.venv` aside, in scratch |
| Verdict recorded | Finding/log states the method + `PASS`/`FAIL` | A number with no recorded verification |
| Verdict is honest | A `FAIL` blocks the artifact; it is reported, never hidden | Shipping a result whose verification failed or was skipped |

## Dependencies

- Prefer the **standard library** (`csv`, `statistics`, `json`) — it handles
  CSVs with no install.
- If a step genuinely needs pandas/openpyxl (e.g. reading `.xlsx`), create a
  disposable `.venv` (`python3 -m venv .venv && .venv/bin/pip install pandas
  openpyxl`) and run the script with `.venv/bin/python`. `.venv/` is gitignored and
  disposable — never a source of truth.
- **If the venv install fails** (offline, or no wheel for this Python), do not
  block: the shipped `.xlsx` has an identical `.csv` twin — process the `.csv` with
  the standard library instead, and say plainly that you used the CSV because
  openpyxl was unavailable. Only `.xlsx`-only inputs with no CSV twin are a genuine
  blocker (report it; don't guess at the contents).

## Example shape (illustrative — real scripts are written per task and deleted)

```
# scratch/analyze_cba.py  — reads data/…cleaned.csv, computes spread vs peers,
#                            writes analysis/combined-rates.csv. Then: rm this file.
# scratch/verify_cba.py   — re-reads the RAW cells, recomputes the spread with a
#                            different method, asserts it matches combined-rates.csv,
#                            prints PASS/FAIL. Then: rm this file.
```
