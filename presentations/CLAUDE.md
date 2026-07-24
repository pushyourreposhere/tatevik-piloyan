# presentations/ — charts & HTML presentations (Layer 5)

The management-facing outputs. Charts are `CHT-NNN` (self-contained `.svg` or
inline SVG); presentations are `RPT-NNN` (self-contained `.html`). Both are
registered in `_index.md`; the HTML follows `TEMPLATE.presentation.html`.

**Standards for this folder**
- **Self-contained only**: inline CSS/SVG, no CDN, no web fonts, no remote images.
  The file must render with no network access and be publishable as an Artifact
  (`.claude/rules/report-style.md`, and the `dataviz` / `artifact-design` skills).
- Every figure shown and every chart cites its `SRC-NNN` / `FND-NNN`. A chart
  with an unsourced number is a hard QA failure.
- Chart type must fit the message (see the decision guide in
  `.claude/skills/visualize/SKILL.md`) — comparison → bars, trend over time →
  line, composition → stacked, not decoration.
- Executive summary follows the structure in `.claude/rules/report-style.md`
  (situation → findings → cause/effect → implication → recommendation), official
  tone, no marketing pathos.
- An output is not `final` until `presentation-qa` returns PASS.

**Primary files**: `_index.md` (registry) · `TEMPLATE.presentation.html` ·
`CHT-NNN-*.svg` · `RPT-NNN-*.html`.
