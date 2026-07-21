# Web-Research Source Registry (WRS-NNN)

Every web source a research brief cites is logged here **once**, with a stable
`WRS-NNN` id and its resolvable URL. Briefs cite the id; this table resolves the
id to where the material actually came from (`.claude/rules/evidence-and-figures.md`).
Read before adding (next free `WRS` id, avoid duplicates); update after capturing.

These ids are **local to `web-research/`** — distinct from the global `SRC-NNN` in
`sources/`. IDs are never reused or deleted — mark a retired source `Deprecated`
with a reason.

| ID | Date accessed | Title / publisher | URL | Raw capture | Used by (WRB) |
|---|---|---|---|---|---|
| WRS-001 | 2026-07-21 | US Federal Reserve — FOMC statement, June 17 2026 | https://www.federalreserve.gov/newsevents/pressreleases/monetary20260617a.htm | not saved (site 403 to bot; read via WebSearch snippet quoting the release) | WRB-001 |
| WRS-002 | 2026-07-21 | US Federal Reserve — FOMC Summary of Economic Projections (dot plot), June 17 2026 | https://www.federalreserve.gov/monetarypolicy/fomcprojtabl20260617.htm | not saved (site 403 to bot; read via WebSearch snippet) | WRB-001 |
| WRS-003 | 2026-07-21 | CNBC — "Fed interest rate decision June 2026: Fed holds rates steady" | https://www.cnbc.com/2026/06/17/fed-interest-rate-decision-june-2026.html | not saved (403; read via WebSearch snippet) | WRB-001 |
| WRS-004 | 2026-07-21 | Advisor Perspectives (dshort) — "Fed's Interest Rate Decision: June 17, 2026" | https://www.advisorperspectives.com/dshort/updates/2026/06/18/feds-interest-rate-decision-june-17-2026 | not saved (403; read via WebSearch snippet) | WRB-001 |
| WRS-005 | 2026-07-21 | Yahoo Finance — "Fed 'dot plot': Almost half of FOMC members project at least one interest rate hike this year" | https://finance.yahoo.com/economy/policy/article/fed-dot-plot-almost-half-of-fomc-members-project-at-least-one-interest-rate-hike-this-year-183645064.html | not saved (403; read via WebSearch snippet) | WRB-001 |
| WRS-006 | 2026-07-21 | Bank of England — "Bank Rate maintained at 3.75% — June 2026 Monetary Policy Summary and Minutes" | https://www.bankofengland.co.uk/monetary-policy-summary-and-minutes/2026/june-2026 | not saved (site 403 to bot; read via WebSearch snippet quoting the summary) | WRB-001 |
| WRS-007 | 2026-07-21 | SPF Private Clients — "Bank of England votes to hold the base rate at 3.75 per cent in June 2026" | https://www.spf.co.uk/insights/market-insights/bank-of-england-holds-base-rate-in-june-2026/ | not saved (403; read via WebSearch snippet) | WRB-001 |
| WRS-008 | 2026-07-21 | Mortgage Trading Association (MTA) — "Monetary Policy Committee Interest Rate Decision – June 2026" | https://www.mta.org.uk/resources/monetary-policy-committee-interest-rate-decision-june-2026/ | not saved (403; read via WebSearch snippet) | WRB-001 |
| WRS-009 | 2026-07-21 | HomeOwners Alliance — "Latest UK Interest Rate Forecasts: Will the BoE Cut on 30 July 2026?" | https://hoa.org.uk/news/interest-rate-predictions-2/ | not saved (403; read via WebSearch snippet) | WRB-001 |
| WRS-010 | 2026-07-21 | UK House of Commons Library — "Interest rates and monetary policy: Economic indicators" | https://commonslibrary.parliament.uk/research-briefings/sn02802/ | not saved (403; read via WebSearch snippet) | WRB-001 |

<!--
Row template:
| WRS-001 | YYYY-MM-DD | Bank of England — Monetary Policy Summary | https://www.bankofengland.co.uk/... | raw/WRS-001-boe-mps.html | WRB-001 |
Date accessed — the day the page was fetched (web content changes).
URL           — resolvable link to the exact page the claim rests on.
Raw capture   — optional path under raw/ to the saved page/snapshot, if kept.
Used by       — the WRB-NNN brief(s) that cite this source.
-->
