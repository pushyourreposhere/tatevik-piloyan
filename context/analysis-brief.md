# Analysis Brief — Central-Bank Rate Comparison

> **This is the anchor.** Read it first, every session. It is the ground truth
> for *what* this workspace is trying to decide and the vocabulary everything
> else uses. It does not tell you *how* to do the work — the procedures live in
> `.claude/skills/`, the standards in `.claude/rules/`.

## 1. The decision this feeds

Give a decision-maker (a board, a CFO, a policy team) a clear, sourced,
plain-language read on **how the Central Bank of Armenia (CBA) refinancing rate
compares to peer central banks**, where it is heading, and what that implies.

The workspace exists to take that question from raw data to a finished, verified
HTML presentation — safely, with every number traceable and every step
checkable.

## 2. The flagship task (end to end)

1. Bring the **local CBA refinancing-rate file** (`data/cba-refinance-rate.csv`,
   and `.xlsx` if present) into the Safe Zone and clean it.
2. **Fetch peer central-bank policy rates** from the open web (e.g. Fed, ECB,
   Bank of England, Bank of Russia, Bank of Georgia) — each figure cited to an
   official source.
3. **Combine and analyze**: CBA vs peers — spread, direction, volatility, recent
   moves.
4. **Visualize** the comparison as charts a manager can read in ten seconds.
5. **Assemble an executive HTML presentation** and verify it.

## 3. Vocabulary (so numbers mean the same thing everywhere)

| Term | Meaning in this workspace |
|---|---|
| **Refinancing rate** | The CBA's main policy interest rate (the rate this analysis centers on). |
| **Policy rate** | The equivalent main rate of a peer central bank (Fed funds target upper bound, ECB main refinancing operations rate, etc.). Always record *which* rate and its `as_of` date. |
| **Basis point (bp)** | 1 bp = 0.01 percentage point. A move from 9.50% to 9.25% is −25 bp. |
| **Spread** | CBA rate minus a peer's rate, in percentage points (or bp). Positive = CBA is higher. |
| **Direction** | The sign of the most recent change: cutting / holding / hiking. |
| **Volatility** | How much a series has moved over the window (std. dev. of period-over-period changes, or count of changes). State the window. |

## 4. Safe-Zone posture (the one thing never to get wrong)

Central-bank policy rates are **public** data — free to combine, chart, and
publish, and safe to send to a web search. But this workspace also ships an
example **restricted** file (`data/internal/loan-portfolio-CONFIDENTIAL.csv`) to
practice the discipline: **classify every dataset before you use it or send it
anywhere.** Restricted data never goes to `WebSearch`/`WebFetch` and never into a
prompt that leaves the machine. The rule is `.claude/rules/safe-zone.md`.

## 5. Where to go next

- Standards to obey: `.claude/rules/` (start with `safe-zone.md` and
  `evidence-and-figures.md`).
- Procedures to run: `.claude/skills/` (start with `intake`, or run the whole
  thing with `workflow`).
- What already exists: the `_index.md` registries in `data/`, `analysis/`,
  `presentations/`, and `sources/source-registry.md`.
