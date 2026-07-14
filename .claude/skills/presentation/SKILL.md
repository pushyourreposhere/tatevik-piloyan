---
name: presentation
description: Assemble a self-contained, management-ready HTML presentation from a finding and its charts — executive summary, KPIs, charts, detail table, cause→effect narrative, and sourced footnotes. Produces RPT-NNN.
argument-hint: <FND-NNN and the CHT-NNN charts to include>
user-invocable: true
---

# Skill: presentation

Owned by **presenter**. Produces the final `RPT-NNN` HTML — self-contained, so it
renders offline and can be published as an Artifact. Read the `artifact-design`
skill for layout/typography calibration.

## Preflight

1. Read the finding (`FND-NNN`), the charts (`CHT-NNN`),
   `presentations/TEMPLATE.presentation.html`, `presentations/_index.md` (next
   free `RPT` id), and the `artifact-design` skill.
2. Confirm every figure you'll show is traceable in the finding, and every chart
   is registered.

## Steps

1. Copy `TEMPLATE.presentation.html` to `presentations/RPT-NNN-<slug>.html`.
2. **Executive summary** — write it to the structure in
   `.claude/rules/report-style.md` (situation → key findings → cause→effect →
   implication → recommendation), official tone, answer-first, no marketing
   pathos.
3. **KPIs** — the 2–4 headline numbers as stat tiles, each also appearing in the
   detail table with its source.
4. **Charts** — **inline** the `CHT-NNN` SVG(s) directly into the file (no
   external `<img src>`), each with a caption naming its source.
5. **Detail table** — one row per bank: rate, `as_of`, `SRC-NNN`.
6. **Sources footer** — list every `SRC-NNN` cited, resolvable to
   `sources/source-registry.md`, plus a line pointing to the `FND-NNN` and noting
   independent verification + human review before distribution.
7. **Self-contained check**: no CDN, web font, remote image, or fetch — inline
   everything. **Register** the presentation in `presentations/_index.md`.

> This skill writes *words and layout* around already-verified numbers — it does
> **no** computation and introduces **no** new figure. Every number comes from
> the finding.

## QA (run before returning)

Run **`presentation-qa`** on the HTML: self-contained (no external hosts); every
figure and chart cites a source; exec-summary structure + official tone; template
sections present; charts render in light and dark. Fix flags; escalate an
unfixable hard failure to Main Claude.

## Output / return

- `presentations/RPT-NNN-<slug>.html`, updated `presentations/_index.md`.
- A one-line summary + the file path. Offer to publish it as an Artifact (it is
  self-contained and safe to publish — public data only).

## Suggested next step

`qa-check <the html>` for an independent re-check, or hand to the user for human
review before distribution.
