# Dataset Registry (DS-NNN)

Every dataset that enters this workspace is registered here **before** it is used
— local file or planned web pull. This is where `intake` records the Safe-Zone
classification and provenance. Read this before importing (to find the next free
`DS` id and avoid duplicates); update it after importing.

IDs are never reused and never deleted — mark a superseded dataset `Deprecated`
with a reason and point to the id that replaced it.

| ID | Name | File | Class | Source(s) | Status | Notes |
|---|---|---|---|---|---|---|
| _(none yet)_ | | | | | | Run `intake` to add the first dataset. |

<!--
Row template:
| DS-001 | CBA refinancing rate (monthly) | data/cba-refinance-rate.csv | public | SRC-001 | raw | dirty: missing/dup/outlier/date issues to clean |
Class ∈ {public, internal, restricted} — see .claude/rules/safe-zone.md
Status ∈ {raw, cleaned, deprecated}
-->
