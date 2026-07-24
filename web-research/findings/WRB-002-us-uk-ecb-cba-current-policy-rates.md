# WRB-002 — Current main policy / refinancing rate of the US, UK, Euro area, and Armenia (per each issuing central bank's own site)

| Field | Value |
|---|---|
| **Guiding question** | What is the current main policy / refinancing rate for each of the United States, United Kingdom, Euro area (EU), and Armenia, according to each issuing central bank's own official website? |
| **Sub-questions** | (1) US — Federal Reserve federal funds target range, incl. the upper bound, + as_of. (2) UK — Bank of England Bank Rate + as_of. (3) Euro area — ECB main refinancing operations (MRO) rate, + deposit facility rate in parentheses, + as_of. (4) Armenia — CBA refinancing rate + as_of. Each named exactly and dated. |
| **Sources** | WRS-001, WRS-006, WRS-007, WRS-011, WRS-012, WRS-013, WRS-014, WRS-015, WRS-016, WRS-017 |
| **Confidence** | Workable (Solid on the figures — each rests on the issuing bank's own page corroborated from a second angle; capped at Workable overall because every official page was read via WebSearch snippet, not fetched directly) |
| **QA** | PASS · rounds run: 2 |
| **Author** | web-researcher · 2026-07-21 |

## Answer first

As of 2026-07-21, the current main policy / refinancing rates are: **United States** — Federal Reserve federal funds target range of **3-1/2 to 3-3/4 percent (3.50%–3.75%; upper bound 3.75%)**, held on 17 June 2026 [WRS-001]; **United Kingdom** — Bank of England **Bank Rate of 3.75%**, maintained 17 June 2026 [WRS-006]; **Euro area** — ECB **main refinancing operations (MRO) rate of 2.40%** (deposit facility rate 2.25%), effective 17 June 2026 [WRS-012]; **Armenia** — Central Bank of Armenia **refinancing rate of 6.50%**, held 16 June 2026 [WRS-015]. Every figure was confirmed against the issuing central bank's own page (read via a search snippet quoting it, since each official site returns HTTP 403 to the fetch tool) and corroborated by a second source.

### Per-country table

| Country | Central bank | Exact rate name | Rate value | as_of / effective date | Source (WRS) |
|---|---|---|---|---|---|
| United States | Federal Reserve (FOMC) | Federal funds target range (upper bound in parentheses) | 3.50%–3.75% (upper bound 3.75%) | Decision 17 June 2026 (held) | WRS-001 (P0), corrob. WRS-011 (P2) |
| United Kingdom | Bank of England (MPC) | Bank Rate | 3.75% | Decision 17 June 2026 (held) | WRS-006 (P0), corrob. WRS-007 (P3) |
| Euro area (EU) | European Central Bank | Main refinancing operations (MRO) rate (deposit facility rate in parentheses) | 2.40% (deposit facility 2.25%) | Effective 17 June 2026 (decided 11 June 2026) | WRS-012 (P0), corrob. WRS-013 (P1), WRS-014 (P2) |
| Armenia | Central Bank of Armenia (Board) | Refinancing rate | 6.50% | Decision 16 June 2026 (held; in effect since 16 Dec 2025) | WRS-015 (P0), corrob. WRS-016 (P3), WRS-017 (P2) |

## What the sources say

**United States — federal funds target range 3.50%–3.75% (upper bound 3.75%).**
- The FOMC's 17 June 2026 statement maintained the target range for the federal funds rate at "3-1/2 to 3-3/4 percent" (a 12–0 vote), i.e. a lower bound of 3.50% and an upper bound of 3.75% — WRS-001 (federalreserve.gov, official page read via a snippet quoting the release).
- Corroborated by FRED's "Federal Funds Target Range – Upper Limit (DFEDTARU)" series, which shows the upper limit at 3.75% — WRS-011 (P2). The two agree.

**United Kingdom — Bank Rate 3.75%.**
- At its meeting ending 17 June 2026 the Bank of England Monetary Policy Committee voted by a majority of 7–2 to maintain Bank Rate at 3.75% — WRS-006 (bankofengland.co.uk, official page read via a snippet quoting the Monetary Policy Summary).
- Corroborated by SPF Private Clients reporting the same 3.75% hold in June 2026 — WRS-007 (P3). The next scheduled decision is 30 July 2026 (WRS-006), so this figure is current as of the access date but may change at that meeting.

**Euro area — ECB main refinancing operations (MRO) rate 2.40%; deposit facility rate 2.25%.**
- On 11 June 2026 the ECB Governing Council raised the three key rates by 25 bp: the deposit facility, main refinancing operations, and marginal lending facility rates were set to 2.25%, 2.40% and 2.65% respectively, with effect from 17 June 2026 — WRS-012 (ecb.europa.eu press release, read via a snippet quoting it). This was the ECB's first increase since September 2023. The user asked for the "refinance rate": the MRO rate (2.40%) is literally the ECB's main refinancing operations rate; the deposit facility rate (2.25%) is noted in parentheses as the ECB's de-facto key rate.
- Corroborated by Banco de España's Eurosystem write-up of the same decision — WRS-013 (P1) — and by Trading Economics' Euro Area interest-rate page showing 2.40% — WRS-014 (P2). All three agree.

**Armenia — CBA refinancing rate 6.50%.**
- At its 16 June 2026 meeting the Board of the Central Bank of Armenia kept the refinancing rate unchanged at 6.50% (page title "Policy rate left unchanged at 6.50%"), with the Lombard repo facility rate at 8.00% and the deposit facility rate at 5.00% — WRS-015 (cba.am press release, read via a snippet quoting it). This was the fifth consecutive hold; the rate has been at 6.50% since 16 December 2025.
- Corroborated by ARMENPRESS — WRS-016 (P3) — and by Trading Economics' Armenia refinancing-rate page — WRS-017 (P2). All three agree on 6.50%.

## Sources used

| WRS | Title / publisher | Tier | Date accessed | URL |
|---|---|---|---|---|
| WRS-001 | US Federal Reserve — FOMC statement, June 17 2026 | P0 | 2026-07-21 | https://www.federalreserve.gov/newsevents/pressreleases/monetary20260617a.htm |
| WRS-011 | FRED, Federal Reserve Bank of St. Louis — Federal Funds Target Range – Upper Limit (DFEDTARU) | P2 | 2026-07-21 | https://fred.stlouisfed.org/series/DFEDTARU |
| WRS-006 | Bank of England — "Bank Rate maintained at 3.75% — June 2026 Monetary Policy Summary and Minutes" | P0 | 2026-07-21 | https://www.bankofengland.co.uk/monetary-policy-summary-and-minutes/2026/june-2026 |
| WRS-007 | SPF Private Clients — "Bank of England votes to hold the base rate at 3.75 per cent in June 2026" | P3 | 2026-07-21 | https://www.spf.co.uk/insights/market-insights/bank-of-england-holds-base-rate-in-june-2026/ |
| WRS-012 | European Central Bank — "Monetary policy decisions" (press release, 11 June 2026) | P0 | 2026-07-21 | https://www.ecb.europa.eu/press/pr/date/2026/html/ecb.mp260611~4d41bd5e83.en.html |
| WRS-013 | Banco de España — "ECB raises rates by 25 basis points in June — Monetary policy decisions" | P1 | 2026-07-21 | https://www.bde.es/wbe/en/noticias-eventos/actualidad-bce/decisiones-politica-monetaria/bce-tipos-junio26.html |
| WRS-014 | Trading Economics — "Euro Area Interest Rate" | P2 | 2026-07-21 | https://tradingeconomics.com/euro-area/interest-rate |
| WRS-015 | Central Bank of Armenia — "Policy rate left unchanged at 6.50%" (press release, 2026-06-16) | P0 | 2026-07-21 | https://www.cba.am/en/press-releases/10144/preview/ |
| WRS-016 | ARMENPRESS Armenian News Agency — "Central Bank keeps policy rate unchanged at 6.50%" | P3 | 2026-07-21 | https://armenpress.am/en/article/1253144 |
| WRS-017 | Trading Economics — "Armenia Refinancing Rate" | P2 | 2026-07-21 | https://tradingeconomics.com/armenia/interest-rate |

Every row here also exists in `web-research/sources/_index.md`. Claims are cited by `WRS-NNN`, never by a bare URL.

## Gaps

- None of the four official central-bank pages (federalreserve.gov, bankofengland.co.uk, ecb.europa.eu, cba.am) could be fetched directly — each returned HTTP 403 to the fetch tool. Every official figure was therefore read via a WebSearch snippet that quotes the official page, and each was corroborated by a second source (P1–P3). No figure rests on an official page that could not be located or that was unquoted.
- No figure had to be marked "not found" — all four current rates were located and sourced.

## Caveats & confidence

- **Overall: Workable.** Each of the four rate values individually is well-evidenced (issuing-bank P0 page corroborated by a second source), which would support `Solid`; the overall rating is held to `Workable` because no official page could be fetched directly — all P0 sources were read through search snippets quoting them rather than the live page (an integrity limitation, not a disagreement between sources). No source conflicts were found: every corroborating source agreed with its P0 figure.
- **UK freshness (soft):** the BoE Bank Rate of 3.75% is current as of 2026-07-21 but the next MPC decision is scheduled for 30 July 2026 (WRS-006); the figure should be re-checked after that meeting.
- **US convention:** the fed funds rate is a range, not a single number; the upper bound (3.75%) is reported alongside the full range per the guiding question.
- **ECB naming:** the reported MRO rate (2.40%) is the ECB's main refinancing operations rate (the literal "refinancing rate"); the deposit facility rate (2.25%) is noted because it is the ECB's de-facto key policy rate.
- **Armenia:** the CBA figure rests on a P0 cba.am press release corroborated by P2/P3 sources; all agree on 6.50%.
