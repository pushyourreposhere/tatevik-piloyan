# Dataset Registry (DS-NNN)

Every dataset that enters this workspace is registered here **before** it is used
— local file or planned web pull. This is where `intake` records the Safe-Zone
classification and provenance. Read this before importing (to find the next free
`DS` id and avoid duplicates); update it after importing.

IDs are never reused and never deleted — mark a superseded dataset `Deprecated`
with a reason and point to the id that replaced it.

| ID | Name | File | Class | Source(s) | Status | Notes |
|---|---|---|---|---|---|---|
| DS-001 | Peer central-bank policy rates (US, UK) | data/peer-rates.csv | public | SRC-002, SRC-003 | raw | Already-published policy rates fetched from issuing central banks' official pages (federalreserve.gov, bankofengland.co.uk); safe to combine/chart/publish per safe-zone.md. Peer set limited to US and UK per this task. source-qa: 2 rounds run, verdict **PASS** (2026-07-14). |
| DS-002 | CBA refinancing rate (monthly) | data/cba-refinance-rate.csv (cleaned: data/cba-refinance-rate-cleaned.csv) | public | SRC-001 | cleaned | Published central-bank policy-rate series → public per safe-zone.md (free to combine/chart/publish). Shipped illustrative sample (tier P4 via SRC-001) — not authoritative; refresh from official CBA before publishing. Was dirty: blanks 2023-08 & 2024-05 (left as explicit gaps), outlier/typo 2023-09=95.0→9.5, duplicate 2024-01 (dropped), mixed date formats (01/03/2023, "March 2024", 2024/09/01) normalized to ISO, stray "%" on 2024-11 stripped. Cleaned 2026-07-24; log: analysis/cba-refinance-rate-cleaning-log.md; independent verification **PASS**. source-qa (intake): 2 rounds, **PASS** (2026-07-24). clean-qa: 2 rounds, **PASS** (2026-07-24). |

<!--
Row template:
| DS-001 | CBA refinancing rate (monthly) | data/cba-refinance-rate.csv | public | SRC-001 | raw | dirty: missing/dup/outlier/date issues to clean |
Class ∈ {public, internal, restricted} — see .claude/rules/safe-zone.md
Status ∈ {raw, cleaned, deprecated}
-->
