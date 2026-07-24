---
name: source-qa
description: Two-round QA for a dataset + its source/provenance registration — checks classification is recorded and every external figure has a resolvable, tiered, dated citation with no fabricated numbers. Called by data-steward after intake / fetch-peer-rates; also user-invocable.
argument-hint: <DS-NNN / a data file, or "peer-rates">
user-invocable: true
---

# Skill: source-qa

Checks a dataset and its registry entries against `.claude/rules/qa.md`,
`safe-zone.md`, and `evidence-and-figures.md`. Returns **PASS** or
**NEEDS-REWORK** with an itemized list. Run it on your own output before
returning it (data-steward), or standalone.

## Round 1 — Compliance

1. **(hard)** The dataset has a `DS-NNN` row in `data/_index.md` with a **class**
   (`public`/`internal`/`restricted`) and a one-line reason.
2. **(hard)** Every external figure in the dataset has a `source_id` that resolves
   to a row in `sources/source-registry.md`.
3. **(hard)** Each source row has: entity, the exact figure/rate name, an
   **`as_of` date**, a **tier** (P0–P4), and a resolvable URL/file.
4. **(soft)** Peer policy rates are sourced **P0/P1** (issuing bank). A P2–P4-only
   rate is flagged and its confidence noted.

## Round 2 — Integrity

5. **(hard)** No fabricated numbers: every value traces to a source or the shipped
   file — nothing "recalled" or estimated (`evidence-and-figures.md` Rule 0).
6. **(hard)** The CSV and the registry agree — every data row's rate/as_of matches
   its cited source; no row cites a missing or duplicated `SRC` id.
7. **(hard)** Safe-Zone respected — nothing restricted was sent to a web tool;
   restricted data, if any, is tokenized (`PRT-NNN`), not raw.
8. **(soft)** "Not found" peers are recorded as such, not silently dropped or
   guessed.

## Verdict

Fix what you can in place. Any unfixed **hard** check ⇒ **NEEDS-REWORK** (and, if
the producer can't fix it, a blocker to escalate). All hard checks pass ⇒
**PASS**. Record on/near the registry: rounds run + verdict.
