---
name: research-qa
description: Two-round QA for a web-research brief (WRB-NNN) + its sources (WRS-NNN) — checks every claim traces to a resolvable, dated, tiered source, the brief answers the user's original intent, nothing is fabricated, and confidence is calibrated. Called by web-researcher after web-research; also user-invocable.
argument-hint: <WRB-NNN / a brief file>
user-invocable: true
---

# Skill: research-qa

Checks a research brief and the web sources it rests on against
`.claude/rules/qa.md`, `evidence-and-figures.md`, and `safe-zone.md`. Returns
**PASS** or **NEEDS-REWORK** with an itemized list. Run it on your own output
before returning it (web-researcher), or standalone.

## Round 1 — Compliance

1. **(hard)** The brief has a `WRB-NNN` row in `web-research/findings/_index.md`
   and follows the expected shape: guiding question, answer-first finding, "what
   the sources say", gaps, and a confidence rating.
2. **(hard)** Every source the brief cites has a `WRS-NNN` row in
   `web-research/sources/_index.md` with a **resolvable URL** and a **date
   accessed**.
3. **(hard)** Every claim / figure in the brief cites a `WRS-NNN` — no assertion
   that the reader cannot trace to a source.
4. **(soft)** Each source carries a **tier** (P0–P4). Load-bearing claims rest on
   P0–P2; a claim resting on P3/P4 alone is flagged and its confidence noted.

## Round 2 — Integrity

5. **(hard)** No fabrication — every claim traces to a cited source; nothing is
   recalled from general knowledge, estimated, or "filled in"
   (`evidence-and-figures.md` Rule 0).
6. **(hard)** The brief **answers the original intent** — the guiding question is
   addressed and each sub-question is either resolved or explicitly marked "not
   found", not quietly dropped or replaced by an adjacent topic.
7. **(hard)** Sources resolve and support the claim — the URL points to the cited
   content, and the brief's wording matches what the source actually says (no
   misquote, no overreach beyond the source).
8. **(hard)** Safe-Zone respected — only public material was queried and stored;
   nothing internal or restricted reached a web tool or the brief.
9. **(soft)** Load-bearing single-source claims are corroborated from a second
   angle where it matters, or the confidence is tagged down; gaps are recorded as
   "not found", and confidence uses the evidence-policy vocabulary
   (`Solid`/`Workable`/`Shaky`/`Empty`) without being rounded up.

## Verdict

Fix what you can in place. Any unfixed **hard** check ⇒ **NEEDS-REWORK** (and, if
the producer can't fix it, a blocker to escalate). All hard checks pass ⇒
**PASS**. Record on/near the brief: rounds run + verdict.
