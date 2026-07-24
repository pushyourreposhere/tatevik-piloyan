# Outputs Registry (CHT-NNN charts · RPT-NNN presentations)

Every chart and every presentation is registered here. Read before creating
(next free id); update after the artifact passes `presentation-qa`.

IDs are never reused or deleted — mark superseded outputs `Deprecated`.

## Charts (CHT-NNN)

| ID | Title | Chart type | Built from (FND/DS) | File | Status |
|---|---|---|---|---|---|
| CHT-001 | CBA refinancing rate, 2023–2025 | line | DS-002 (cleaned) | presentations/CHT-001-cba-refinance-trend.svg | final |

## Presentations (RPT-NNN)

| ID | Title | Findings included | Charts included | QA | File | Status |
|---|---|---|---|---|---|---|
| RPT-001 | The CBA Refinancing Rate, 2023–2026 | DS-002, WRB-002 | CHT-001 | — | presentations/RPT-001-cba-refinance-rate.md | final |

<!--
Chart row:   | CHT-001 | CBA vs peers, latest policy rate | grouped bar | FND-001 | presentations/CHT-001-cba-vs-peers.svg | final |
Present row: | RPT-001 | CBA Rate in Regional Context | FND-001 | CHT-001, CHT-002 | PASS | presentations/RPT-001-cba-context.html | final |
Chart types — see the decision guide in .claude/skills/visualize/SKILL.md
QA ∈ {PASS, NEEDS-REWORK} from presentation-qa
-->
