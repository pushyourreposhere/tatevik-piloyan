---
name: visualize
description: Turn a finding's numbers into self-contained SVG charts a manager can read in ten seconds. Picks the right chart type for the message and cites the source on every chart. Produces CHT-NNN.
argument-hint: <FND-NNN to visualize>
user-invocable: true
---

# Skill: visualize

Owned by **presenter**. Produces self-contained charts from a finding. Read the
`dataviz` skill first for palette, mark specs, and accessibility — this skill
governs *what* to chart and the workspace rules; `dataviz` governs *how* it
looks.

## Preflight

1. Read the finding (`FND-NNN`), `presentations/_index.md` (next free `CHT` id),
   and the `dataviz` skill.
2. Confirm every number you intend to chart is traceable in the finding.

## Chart-type decision guide (fit the message, not decoration)

| The message is… | Use | Not |
|---|---|---|
| "compare levels across banks right now" | horizontal/grouped **bar** | pie |
| "how the CBA rate moved over time" | **line** (time on x) | bar |
| "CBA vs one peer over time" | **two-line** comparison | stacked |
| "spread of CBA above/below each peer" | **diverging bar** (zero baseline) | 3-D anything |
| "a single headline number" | **KPI stat**, not a chart | gauge |

## Steps

1. For each chart, build **self-contained inline SVG** (no external hosts, no web
   fonts, no CDN) sized responsively (`viewBox`, `width:100%`). Apply the
   `dataviz` palette and accessibility rules (labels, sufficient contrast,
   readable in light and dark). Title it, label axes with **units** (%),
   and annotate the key value.
2. **Source line**: every chart embeds/accompanies its `SRC-NNN`/`FND-NNN` origin
   in a `<title>`/caption. A chart with an unsourced number is a hard failure.
3. Save each as `presentations/CHT-NNN-<slug>.svg` (standalone) — the
   `presentation` skill will inline it.
4. **Register** each chart in `presentations/_index.md` (id, title, type, source
   finding, file).

> This skill draws only from numbers already computed and verified in the
> finding — it performs **no** new computation. If a needed number isn't in the
> finding, that's a blocker: report to Main Claude (→ back to `analyze`).

## QA (run before returning)

Run **`presentation-qa`** in chart mode on each SVG: self-contained; correct
chart type for the message; axis units present; every value cites a source;
renders in light and dark. Fix flags; escalate unfixable hard failures.

## Output / return

- `presentations/CHT-NNN-*.svg`, updated `presentations/_index.md`.
- A note of which chart carries which message, ready for `presentation`.

## Suggested next step

`presentation` to assemble the HTML.
