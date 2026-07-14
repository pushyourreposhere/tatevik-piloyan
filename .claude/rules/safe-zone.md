# Rule: Safe Zone

**Applies to** everything under `data/`, `analysis/`, and `presentations/`. It is
referenced by the root and folder `CLAUDE.md` files, by each skill's preflight, and
by every agent's "Applicable rules" — read it before touching any dataset.

The Safe Zone is the discipline of deciding, **before** you touch a dataset, what
class it is and therefore what you are allowed to do with it. This is the first
step of every task and a human-in-the-loop checkpoint — never skip it, never
infer it silently.

## Core rule

**Classify every dataset before it is used or sent anywhere. Restricted data
never leaves the machine.** If the class is unclear, treat it as restricted and
ask the user.

## The three classes

| Class | What it is | What you may do | What you must never do |
|---|---|---|---|
| **public** | Already-published figures: central-bank policy rates, official statistics, press releases | Combine, compute, chart, publish; send the *query* to `WebSearch`/`WebFetch` to gather more public figures | — |
| **internal** | Your organization's own non-public figures (budgets, internal ROI) | Use locally; compute; summarize in outputs meant for internal readers | Send the raw data to a web tool or any external service; publish it without sign-off |
| **restricted** | PII (names, emails, phone, account IDs) or anything marked confidential | Use **only** after anonymizing (below), or exclude it | Send to `WebSearch`/`WebFetch`; paste into any prompt/tool that leaves the machine; include raw in any output |

For this workspace: **central-bank rates are public.** The shipped
`data/internal/loan-portfolio-CONFIDENTIAL.csv` is **restricted** and exists only
to practice this decision — it must never reach a web tool.

## Requirements

| Requirement | Standard | Fail condition |
|---|---|---|
| Classify on intake | `intake` records `Class ∈ {public, internal, restricted}` in `data/_index.md` with a one-line reason | A dataset is used with no class recorded |
| Confirm before egress | Before any `WebSearch`/`WebFetch` or external call, confirm only public data (or a public *query*) is leaving | Restricted/internal data, or a prompt containing it, sent outward |
| Anonymize restricted data before use | Replace each identifier with a `PRT-NNN` token; keep the mapping in a **local, never-published** `analysis/anonymization-map.md`; strip the raw identifiers from anything downstream | A real name / email / account id appears in a finding, chart, presentation, or a prompt |
| Keep the map out of outputs | The `PRT-NNN` → real-value mapping is local only | The mapping is embedded in a shareable artifact |

## Anonymization pattern

When a restricted dataset must be analyzed:

1. Copy identifiers out into `analysis/anonymization-map.md` (local, gitignore if
   needed) as `PRT-001 = Jane Doe <jane@…>`, one row each.
2. In the working copy, replace every identifier with its `PRT-NNN` token.
3. Do all analysis on the tokenized copy. Findings and presentations show
   `PRT-NNN`, never the real value.
4. Never send the map, or any un-tokenized cell, to a web tool or external prompt.

## Prohibited

- Using or moving a dataset before its class is recorded.
- Sending restricted (or un-anonymized) data to `WebSearch`, `WebFetch`, an
  Artifact, or any external service.
- Publishing internal data without explicit human sign-off.
- Treating "it's probably fine" as a classification. Unsure ⇒ restricted ⇒ ask.
