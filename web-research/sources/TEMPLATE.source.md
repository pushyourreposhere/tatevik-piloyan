<!--
WEB-SOURCE TEMPLATE — the standard shape of one WRS-NNN source entry. A web
source is a ROW in web-research/sources/_index.md (not a separate file), so this
template is a reference for how to fill that row, not a file to copy per source.
The template IS the quality standard: research-qa checks each source against these
fields. Log every source a brief cites — once — before or as the brief is written.
-->

# Web-Source entry (WRS-NNN) — standard

Each source the brief rests on is one row in `web-research/sources/_index.md`,
keyed by a stable `WRS-NNN` id (local to `web-research/`, distinct from the global
`SRC-NNN`). One source, one id — cite it by id, never by a bare URL
(`.claude/rules/evidence-and-figures.md`).

## Fields (every column required)

| Field | What goes here | Fail condition |
|---|---|---|
| **ID** | The next free `WRS-NNN`. Never reuse or delete an id — mark a retired source `Deprecated` with a reason. | A reused id, or a claim citing an id with no row |
| **Date accessed** | The day the page was read (`YYYY-MM-DD`). Web content changes — this dates the claim. | Missing date |
| **Title / publisher** | The publisher and the exact page/document title, e.g. `Bank of England — June 2026 Monetary Policy Summary`. | Vague ("a news site") or wrong publisher |
| **URL** | A resolvable link to the *exact* page the claim rests on — not a homepage or search page. | Bare/broken link, or a link that doesn't contain the claim |
| **Tier** | `P0`–`P4` per `sources/evidence-policy.md` (P0 = the issuing entity's own page … P4 = weak/undated). | Untagged, or an over-generous tier |
| **Raw capture** | Path under `raw/` to a saved snapshot if kept; else a short note (e.g. `not saved (site 403 to bot; read via WebSearch snippet quoting the release)`). | Blank when the page could not be fetched directly |
| **Used by (WRB)** | The `WRB-NNN` brief(s) that cite this source. | A source logged but cited by no brief |

## Tiers (summary — see `sources/evidence-policy.md` for the full table)

`P0` authoritative primary (the entity that sets/issues the figure) · `P1`
official interpretive (press release / bulletin) · `P2` independent structured
(reputable aggregator) · `P3` independent context (reputable news) · `P4` weak /
unverified (forum, blog, undated) — must be tagged and never the sole basis of a
load-bearing claim.

## Row format (paste into `sources/_index.md`)

```
| WRS-NNN | YYYY-MM-DD | Publisher — exact page title | https://…exact-page | raw/WRS-NNN-slug.html (or a "not saved" note) | WRB-NNN |
```

## Worked example

```
| WRS-006 | 2026-07-21 | Bank of England — "Bank Rate maintained at 3.75% — June 2026 Monetary Policy Summary and Minutes" | https://www.bankofengland.co.uk/monetary-policy-summary-and-minutes/2026/june-2026 | not saved (site 403 to bot; read via WebSearch snippet quoting the summary) | WRB-001 |
```

## Rules this entry must satisfy

- **Public only.** Only public queries and public pages ever enter `web-research/`
  (`.claude/rules/safe-zone.md`). Never log anything internal or restricted.
- **Resolvable & specific.** The URL must point to the exact page carrying the
  claim; if the page couldn't be fetched directly, say how it was read in *Raw
  capture* and tier it honestly.
- **Higher tier for load-bearing claims.** Prefer P0/P1; corroborate a
  load-bearing claim from a second angle. A claim resting only on P4 caps the
  brief's confidence at `Shaky`.
