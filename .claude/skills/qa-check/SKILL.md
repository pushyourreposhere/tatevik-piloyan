---
name: qa-check
description: User-facing QA dispatcher — detects what kind of artifact you point it at (dataset, cleaning result, finding, chart, or presentation) and runs the matching QA skill's two-round check. Use for a standalone re-check, e.g. after a manual edit.
argument-hint: <path to any artifact, or its ID (DS/FND/CHT/RPT)>
user-invocable: true
---

# Skill: qa-check

The single entry point when a human wants to re-check an artifact independently of
the agent that made it (e.g. after editing it by hand). It does not re-run the
checks itself — it **detects the artifact type and delegates** to the right QA
skill, all of which apply the two-round discipline in `.claude/rules/qa.md`.

## Dispatch

| You point it at… | It runs |
|---|---|
| a dataset / `data/*.csv` / `DS-NNN` / `peer-rates.csv` | `source-qa` |
| a `*-cleaned.csv` or `*-cleaning-log.md` | `clean-qa` |
| a finding / `analysis/FND-*.md` / `FND-NNN` | `analysis-qa` |
| a chart `presentations/CHT-*.svg` / `CHT-NNN` | `presentation-qa` (chart mode) |
| a presentation `presentations/RPT-*.html` / `RPT-NNN` | `presentation-qa` (presentation mode) |

If the type is ambiguous, ask the user which check they want.

## Steps

1. Identify the artifact type from the path/id (or ask).
2. Run the matching QA skill and collect its **PASS / NEEDS-REWORK** verdict and
   itemized list.
3. Apply the copyable response-quality checklist from `.claude/rules/qa.md` as a
   final human-facing pass.
4. Report the verdict and every issue found. Offer to fix soft issues in place;
   a hard failure is reported plainly (the artifact should not be treated as
   accepted until it's resolved).

## Output / return

The verdict, the itemized findings, and (if asked) the applied fixes. This is the
same check the owning agent already ran internally — here run on demand.
