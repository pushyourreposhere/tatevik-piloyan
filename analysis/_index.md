# Findings Registry (FND-NNN)

Every finding produced by `analyze` is registered here. Cleaning logs and the
combined dataset also land in `analysis/` (as files), but the numbered,
QA'd analytical conclusions are tracked in this table. Read before creating (next
free `FND` id); update after the finding passes `analysis-qa`.

IDs are never reused or deleted — mark superseded findings `Deprecated`.

| ID | Question | Inputs (DS/FND) | Confidence | QA | Status | File |
|---|---|---|---|---|---|---|
| _(none yet)_ | | | | | | Run `analyze` to add the first finding. |

<!--
Row template:
| FND-001 | CBA rate vs peer central banks | DS-001, DS-002 | Workable | PASS | final | analysis/FND-001-cba-vs-peers.md
Confidence ∈ {Solid, Workable, Shaky, Empty} — see .claude/rules/qa.md
QA ∈ {PASS, NEEDS-REWORK} from analysis-qa
Status ∈ {draft, final, deprecated}
-->
