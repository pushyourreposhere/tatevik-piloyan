# Rule: Quality Assurance

**Applies to** every artifact in `analysis/` and `presentations/`. It is referenced
by all four QA skills (`source-qa`, `clean-qa`, `analysis-qa`, `presentation-qa`)
and the `qa-check` dispatcher — they each apply their artifact-specific checks on top
of this shared shape.

The shared checking discipline. The QA skills (`source-qa`, `clean-qa`,
`analysis-qa`, `presentation-qa`) each apply *their* artifact-specific checks on
top of this shared shape; agents run the matching QA skill on their own output
before returning.

## Two rounds — always both

Check every artifact **twice** before it is accepted:

- **Round 1 — Compliance** (is it shaped right?): required sections/fields
  present and non-empty; Safe-Zone class recorded; every figure carries a
  `SRC-NNN` or `FND-NNN`/Method reference; the artifact follows its template.
- **Round 2 — Integrity** (is it true?): cited sources actually resolve; every
  number matches the finding's logged computation or its source cell; the
  independent-verification verdict is `PASS`; `scratch/` is empty; confidence is
  calibrated to the evidence, not rounded up.

Round 2 exists to catch problems introduced by Round 1's own fixes. If Round 2
surfaces something new, fix it and re-check once. If a *third* distinct issue
appears after two genuine rounds, stop looping — report it to the caller as a
known open issue rather than iterating forever.

## Hard vs soft failures

- **Hard** — invalidates the artifact if it can't be fixed. The producing agent
  must **not** return it as done: it fixes it, or (if unfixable) stops and
  reports the blocker to Main Claude. Examples: an unsourced/ fabricated figure;
  a verification verdict of FAIL or missing; restricted data that reached a web
  tool; a template section missing; a `.py` script left in a persisted folder.
- **Soft** — note it in the artifact's "Caveats / open questions" and continue.
  Examples: a single-source figure that would be stronger corroborated; a peer
  whose latest rate is a few weeks stale.

## The response-quality checklist (Meeting 8 — copyable)

Paste this after any AI-generated result — findings, summaries, presentations —
and fix everything it surfaces before accepting the output:

```
Review your work against:
- adherence to the task / brief
- adherence to the relevant rules (safe-zone, evidence, ephemeral-compute, report-style)
- factual correctness — every figure traces to a cell, a logged computation, or a cited source
- Safe-Zone compliance — nothing restricted left the machine; classification recorded
- verification — the independent check ran and passed; scratch/ is empty
- mistakes to fix (numbers, dates, units, spread signs)
- bad or missing source citations to fix
- missing updates in related files (registries/_index.md, source-registry.md)
- deprecated or superseded content to remove
- tone — official, cause→effect, no marketing pathos

Fix everything you found, then say what you changed.
```

## Recording a QA pass

Each QA skill records, on the artifact: how many rounds ran, the verdict
(`PASS` / `NEEDS-REWORK`), and any hard failure that had to be escalated rather
than fixed in place. A future reader should be able to see that QA actually
happened.
