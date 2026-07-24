# data/ — raw datasets (Layer 3)

Source data lives here, one file per dataset, registered in `_index.md` as
`DS-NNN`. This is the boundary where the Safe Zone begins.

**Standards for this folder**
- Nothing is *used* until it is registered and **classified** in `_index.md`
  (public / internal / restricted — `.claude/rules/safe-zone.md`). Classification
  is a human-in-the-loop checkpoint; do it via the `intake` skill.
- `internal/` holds **restricted** examples. Files here never go to a web tool
  and never into a prompt that leaves the machine.
- Cleaned outputs do **not** overwrite raw files. `clean-data` writes a new
  `*-cleaned.csv` alongside the raw one and logs every change; the raw file stays
  as the archived original (archive-then-analyze).
- Shipped sample series are **illustrative** (tier P4, `SRC-001`) — refresh from
  the official source before any figure is published.

**Primary files**: `_index.md` (registry) · `cba-refinance-rate.csv` (shipped,
dirty) · `peer-rates.template.csv` (schema to fill from the web) ·
`internal/loan-portfolio-CONFIDENTIAL.csv` (restricted example).
