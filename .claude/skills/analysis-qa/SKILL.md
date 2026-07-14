---
name: analysis-qa
description: Two-round QA for a finding (FND-NNN) — checks every figure is traceable, the independent verification passed, the template is complete, and confidence is calibrated to the evidence. Called by analyst after analyze; also user-invocable.
argument-hint: <FND-NNN>
user-invocable: true
---

# Skill: analysis-qa

Checks a finding against `.claude/rules/qa.md`, `evidence-and-figures.md`,
`ephemeral-compute.md`, and `report-style.md`. Returns **PASS** / **NEEDS-REWORK**.

## Round 1 — Compliance

1. **(hard)** The finding follows `analysis/TEMPLATE.finding.md` — every section
   present and non-empty (an Empty-confidence finding still fills every section).
2. **(hard)** Every value in the Key-figures table has a "Traces to" origin
   (`DS-NNN` cell / `SRC-NNN` / Method).
3. **(hard)** The finding has a `FND-NNN` row in `analysis/_index.md`, non-duplicate.
4. **(soft)** Window and units are stated; spreads state their sign convention.

## Round 2 — Integrity

5. **(hard)** Every number in the answer, KPIs, and interpretation traces to the
   Method section or a cited source — nothing asserted in prose but untraceable
   (`evidence-and-figures.md`).
6. **(hard)** The **Independent verification** section shows a separate script
   recomputed the headline numbers from raw cells and the verdict is **PASS**;
   `scratch/` is empty.
7. **(hard)** Spot-recompute one headline figure yourself (e.g. the spread vs the
   peer median) from `analysis/combined-rates.csv` and confirm it matches.
8. **(soft, fix aggressively)** Confidence matches the evidence per
   `evidence-policy.md` — a single-source, uncorroborated number is at most
   `Workable`; a P4-only figure at most `Shaky`. Correct an over-rating.
9. **(soft)** Interpretation is cause→effect and neutral — no marketing pathos
   (`report-style.md`).
10. **(hard) Date comparability.** If the CBA figure and the peer figures carry
    different `as_of` dates, the finding must state the mismatch as a caveat and
    must not present the spread as a same-dated comparison. A stale-vs-current
    spread shown as if same-dated is a hard failure.

## Verdict

Fix in place where possible. Any unfixed **hard** check ⇒ **NEEDS-REWORK**; a
missing/FAIL verification or an untraceable figure is hard and escalatable. All
hard checks pass ⇒ **PASS**. Record rounds + verdict in the finding.
