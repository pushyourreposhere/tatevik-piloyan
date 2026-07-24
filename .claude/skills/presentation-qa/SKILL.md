---
name: presentation-qa
description: Two-round QA for a chart (CHT-NNN) or an HTML presentation (RPT-NNN) — checks it is fully self-contained, every figure and chart cites a source, tone/structure follow report-style, and it renders in light and dark. Called by presenter after visualize / presentation; also user-invocable.
argument-hint: <CHT-NNN .svg or RPT-NNN .html>
user-invocable: true
---

# Skill: presentation-qa

Checks a chart or presentation against `.claude/rules/qa.md`, `report-style.md`,
and `evidence-and-figures.md`. Returns **PASS** / **NEEDS-REWORK**. Runs in
**chart mode** (an `.svg`) or **presentation mode** (an `.html`).

## Round 1 — Compliance

1. **(hard) Self-contained** — grep the file for external references: no
   `http(s)://` in `src`/`href`/`url(...)`, no `<script src>`, no CDN, no web
   font, no remote `<img>`, no `fetch`/`XHR`. Inline SVG/CSS only. Any external
   host ⇒ hard fail.
2. **(hard)** Follows its template/shape — chart has title + axis labels with
   **units**; presentation has the `TEMPLATE.presentation.html` sections
   (exec summary, KPIs, chart(s), detail table, sources footer).
3. **(hard)** Every figure shown and every chart carries a `SRC-NNN`/`FND-NNN`
   citation (chart via `<title>`/caption; presentation via table + footer).

## Round 2 — Integrity

4. **(hard)** Every number in the presentation matches the finding it came from —
   spot-check two figures against `FND-NNN`. No figure appears that isn't in the
   finding (the presenter does no computation).
5. **(hard)** Every `SRC-NNN` in the footer resolves to
   `sources/source-registry.md`; every `as_of` date is shown for a rate.
6. **(hard)** No restricted data is present (public data only for anything
   publishable).
7. **(soft)** Tone is official, answer-first, cause→effect; no marketing-pathos
   words (`report-style.md` blocklist).
8. **(soft)** Renders legibly in light **and** dark (theme-aware CSS present);
   chart type fits the message; wide content scrolls rather than overflowing.

## Verdict

Fix in place where possible. Any unfixed **hard** check ⇒ **NEEDS-REWORK**; an
external dependency, an unsourced figure, or restricted data present are hard,
escalatable failures. All hard checks pass ⇒ **PASS**. Record rounds + verdict in
`presentations/_index.md` (or a comment in the file).
