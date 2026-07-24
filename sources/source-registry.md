# Source Registry (SRC-NNN)

Every figure that comes from outside a computation — a rate read off a file or a
web page — is logged here, once, with a stable `SRC` id. Outputs cite the id;
this table resolves the id to where the number actually came from and how much to
trust it. No claim without a resolvable source (`rules/evidence-and-figures.md`).

IDs are never reused or deleted — mark a retired source `Deprecated` with a
reason. Tiers are defined in `evidence-policy.md` (P0 = authoritative primary …
P4 = weak/unverified).

| ID | Date logged | Entity | Figure / claim | Type | Tier | URL or file |
|---|---|---|---|---|---|---|
| SRC-001 | 2026-07-13 | CBA | Monthly refinancing-rate series (shipped sample) | local file | P4 | data/cba-refinance-rate.csv — **sample/illustrative, not authoritative; refresh from official CBA before publishing** |
| SRC-002 | 2026-07-14 | US Federal Reserve | Fed funds target range — upper bound = 3.75% (range 3.50%–3.75%), as of 2026-06-17 | official web | P0 | https://www.federalreserve.gov/newsevents/pressreleases/monetary20260617a.htm |
| SRC-003 | 2026-07-14 | Bank of England | Bank Rate = 3.75%, as of 2026-06-17 (MPC meeting ending 17 June 2026) | official web | P0 | https://www.bankofengland.co.uk/monetary-policy-summary-and-minutes/2026/june-2026 |

**source-qa on DS-001 / SRC-002 / SRC-003**: Round 1 (compliance) and Round 2 (integrity) both run 2026-07-14 — verdict **PASS**. Note: direct `WebFetch` of the two official pages returned HTTP 403 (bot-blocking); the rate, exact name, and `as_of` date were confirmed via `WebSearch` snippets quoting the official press release/summary text, corroborated by independent secondary reporting (FRED, Advisor Perspectives, CNBC) — no fabricated figures, both peers found.

<!--
Row template:
| SRC-002 | YYYY-MM-DD | US Federal Reserve | Fed funds target, upper bound = X.XX% as of YYYY-MM-DD | official web | P0 | https://www.federalreserve.gov/... |
Type   ∈ {local file, official web, official interpretive, independent, media}
Tier   ∈ {P0, P1, P2, P3, P4} — policy rates should come from P0/P1 (the issuing central bank).
Record the *specific* rate name (e.g. "ECB main refinancing operations rate") and its as_of date.
-->
