# analysis/ — cleaning logs, combined data, findings (Layer 4)

Where raw data becomes analytical conclusions. Cleaning logs and the combined
dataset are files here; numbered conclusions are `FND-NNN`, registered in
`_index.md` and shaped by `TEMPLATE.finding.md`.

**Standards for this folder**
- Every finding follows `TEMPLATE.finding.md` — including a **Method** section
  (the surviving audit trail of the deleted analysis script) and an **Independent
  verification** section with a PASS/FAIL verdict (`.claude/rules/ephemeral-compute.md`).
- Every figure in a finding traces to a `DS-NNN` cell, a `SRC-NNN` source, or the
  finding's own Method (`.claude/rules/evidence-and-figures.md`).
- A finding is not `final` until `analysis-qa` returns PASS. Confidence is
  calibrated, not optimistic (`.claude/rules/qa.md`).
- Cleaning logs record every detected issue (missing / duplicate / outlier /
  format) and what was done about it, plus the verification verdict.

**Primary files**: `_index.md` (registry) · `TEMPLATE.finding.md` ·
`FND-NNN-*.md` findings · `*-cleaning-log.md` (from clean-data; the cleaned CSV
itself lands in `data/`, not here) · `combined-rates.csv` (from analyze).
