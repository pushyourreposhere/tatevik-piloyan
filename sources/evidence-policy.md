# Evidence Policy

The standard every sourced figure in this workspace is held to. Works together
with `.claude/rules/evidence-and-figures.md` (the rule that enforces it) and the
QA skills (which check it).

## The prime rule

**Every factual figure carries a citation to a logged source, or is a logged
computation over cited figures. No number without a resolvable origin.**

A number may appear in a finding, chart, or presentation only if it is:

- **(a) a cell in a registered dataset** (`DS-NNN`), or
- **(b) the output of an ephemeral computation** whose method and result are
  recorded in a finding (`FND-NNN`), computed *from* (a) or (c), or
- **(c) a figure read from an external source** logged in
  `sources/source-registry.md` (`SRC-NNN`).

Never from general knowledge, memory of "the usual level," or a plausible-looking
guess. If you don't have a sourced number, say so — "not found in the provided
data / no official source located" is a complete, acceptable answer.

## Source tiers

| Tier | Meaning | Example for this workspace |
|---|---|---|
| **P0** | Authoritative primary — the entity that sets the number | The issuing central bank's own site (federalreserve.gov, ecb.europa.eu, cba.am) |
| **P1** | Official interpretive | An official press release / statistical bulletin summarizing the rate |
| **P2** | Independent structured | A reputable data aggregator (BIS, Trading Economics) — use to corroborate, not as the sole source |
| **P3** | Independent context | Reputable news reporting the decision |
| **P4** | Weak / unverified | Forum, blog, undated page, or the shipped illustrative sample — **must be tagged and must not be the sole basis of a published figure** |

## Rules for policy rates specifically

- A peer policy rate should be sourced **P0 or P1** (the central bank itself).
  If only P2/P3 is available, log it, tag the confidence down, and say so.
- Always capture **which rate** (name it exactly) and its **`as_of` date** — a
  rate without a date is not usable.
- If two sources disagree, prefer the higher tier, log both, and note the
  discrepancy in the finding.

## Confidence vocabulary (used in findings)

`Solid` (corroborated from a second angle) · `Workable` (one clean sourced path,
no corroboration) · `Shaky` (small/old/single-source or a known caveat) · `Empty`
(searched honestly, nothing usable found — reported plainly, not backfilled).
A figure resting only on P4 can never be rated above `Shaky`.
