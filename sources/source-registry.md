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

<!--
Row template:
| SRC-002 | YYYY-MM-DD | US Federal Reserve | Fed funds target, upper bound = X.XX% as of YYYY-MM-DD | official web | P0 | https://www.federalreserve.gov/... |
Type   ∈ {local file, official web, official interpretive, independent, media}
Tier   ∈ {P0, P1, P2, P3, P4} — policy rates should come from P0/P1 (the issuing central bank).
Record the *specific* rate name (e.g. "ECB main refinancing operations rate") and its as_of date.
-->
