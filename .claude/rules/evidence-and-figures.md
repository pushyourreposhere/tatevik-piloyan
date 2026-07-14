# Rule: Evidence & Figures (no unsourced numbers)

**Applies to** everything under `analysis/`, `presentations/`, and `sources/`. It is
referenced by the root `CLAUDE.md`, the analyze/QA skills, and the agents — read it
before writing any figure.

This is the anti-hallucination core. It outranks any pressure to make an output
look complete.

## Rule 0 — Never fabricate a figure. This outranks everything else here.

A number, rate, date, or percentage may appear in a finding, chart, or
presentation only if it came from one of exactly three places:

1. **A cell in a registered dataset** (`DS-NNN`) — the shipped file or an
   imported/fetched one.
2. **A computation** performed by an ephemeral script this session, whose method
   and result are recorded in a finding's Method section (`FND-NNN`) and computed
   *from* sourced inputs.
3. **An external figure** logged in `sources/source-registry.md` (`SRC-NNN`),
   with a resolvable URL/file and a tier (`sources/evidence-policy.md`).

Nothing else counts. Specifically, never use:

- A plausible level recalled from general knowledge ("Armenia's rate is around
  9%") — even if it turns out close. If it isn't sourced, it isn't usable.
- A number carried from an earlier document without re-tracing it. Cite the
  earlier `FND-NNN`/`SRC-NNN`, don't restate the number as freshly verified.
- Rounding, extrapolating, or "filling in" a gap so a table looks full.

**"Not found in the provided data / no official source located" is a complete,
acceptable, expected answer.** Padding an output with an invented number is a
worse outcome than an honest gap.

## Requirements

| Requirement | Standard | Fail condition |
|---|---|---|
| Every figure is traceable | Each number resolves to a `DS-NNN` cell, a `FND-NNN` Method step, or a `SRC-NNN` | A figure with no resolvable origin |
| Policy rates are P0/P1 | Peer central-bank rates come from the issuing bank (or its official bulletin); capture the exact rate name + `as_of` date | A published rate resting only on P2–P4, untagged |
| One source, one id | Each external figure is logged once in the registry and cited by id | A number cited to a bare URL not in the registry, or logged twice under different ids |
| Gaps are declared | Missing figures are marked "not found" / "not sourced", not estimated | A blank filled with a guess |
| Confidence reflects evidence | A figure resting only on P4 is at most `Shaky`; unsourced ⇒ it does not ship | Over-stated confidence on thin evidence |

## Prohibited

- Any number the reader could not trace back to a cell, a logged computation, or
  a cited source.
- Presenting a peer rate without its `as_of` date.
- Using the shipped illustrative sample (`SRC-001`, P4) as if it were an
  authoritative published figure.
