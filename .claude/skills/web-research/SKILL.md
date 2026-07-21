---
name: web-research
description: Crawl the open web to answer a research question, capture each source as WRS-NNN with its URL, and synthesize a cited research brief (WRB-NNN) that answers the user's original intent. Public data only. Use when the user needs open-web research beyond the peer-rate fetch.
argument-hint: <the research question / intent to investigate>
user-invocable: true
---

# Skill: web-research

Owned by **web-researcher**. Turns a research question into a **sourced brief**:
crawl the open web, log every source it rests on as `WRS-NNN`, and write a
`WRB-NNN` brief in `web-research/findings/` that answers the user's *original
intent*. The brief is the deliverable; the sources are its audit trail.

## Preflight

1. Read the anchor (`context/analysis-brief.md`), `web-research/CLAUDE.md`, both
   registries — `web-research/sources/_index.md` (next free `WRS` id) and
   `web-research/findings/_index.md` (next free `WRB` id) — and both templates,
   `findings/TEMPLATE.brief.md` and `sources/TEMPLATE.source.md`.
2. **Pin the intent.** Restate the user's question in one sentence as the brief's
   *guiding question*, and list the sub-questions the brief must answer. Every
   later step serves this — do not drift into adjacent topics.
3. **Safe-Zone check** (`.claude/rules/safe-zone.md`): this skill sends only
   *public queries* to the web and stores only *public* pages. Never put internal
   or restricted material into a query or into `web-research/`. A soft reminder
   fires before each web call.

## Steps

1. **Crawl.** Use `WebSearch` to find candidate sources, then `WebFetch` the
   promising ones. Prefer authoritative/primary sources (higher tier — see
   `sources/evidence-policy.md`); gather enough to answer each sub-question **and**
   to corroborate the load-bearing claims from a second angle.
2. **Capture each source once.** For every source a claim will rest on, add a
   `WRS-NNN` row to `web-research/sources/_index.md` following
   `sources/TEMPLATE.source.md` (date accessed, title / publisher, resolvable URL,
   tier P0–P4, raw-capture note, and the `WRB` that uses it). One source, one id —
   cite it by id, never by a bare URL (`.claude/rules/evidence-and-figures.md`).
3. **Write the brief.** Create `web-research/findings/WRB-NNN-<slug>.md` from
   `findings/TEMPLATE.brief.md`, filling every section:
   - **Guiding question** (the pinned intent) and the sub-questions.
   - **Answer first** — the finding, stated plainly in the first few sentences.
   - **What the sources say** — the results, each claim citing its `WRS-NNN`;
     where two sources agree or disagree, say so.
   - **Gaps** — anything searched for but not found, marked "not found — no source
     located", never backfilled with a guess.
   - **Confidence** — `Solid` / `Workable` / `Shaky` / `Empty` per the
     evidence-policy vocabulary; a claim resting only on P4 is at most `Shaky`.
4. **Register** the brief: add its `WRB-NNN` row to
   `web-research/findings/_index.md` (topic, sources cited, status, file).
5. **Stay honest to intent.** If the web can't answer the guiding question, the
   brief says so — an `Empty` brief that reports the gap beats an padded one.

## QA (run before returning)

Run **`research-qa`** on the `WRB-NNN` brief + its `WRS-NNN` rows: every claim
traces to a resolvable, dated, tiered source; the brief answers the original
intent; nothing is fabricated; confidence is calibrated. Fix flags; escalate an
unfixable hard failure to Main Claude.

## Output / return

- `web-research/findings/WRB-NNN-<slug>.md` (the brief), with
  `web-research/findings/_index.md` and `web-research/sources/_index.md` updated.
- A short summary: the answer to the guiding question, the confidence rating, the
  sources it rests on (`WRS` ids), and any gap reported as "not found".

## Suggested next step

If the brief feeds the flagship comparison, hand it to `analyst`; otherwise refine
the guiding question and re-run for a deeper pass.
