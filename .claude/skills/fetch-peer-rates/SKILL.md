---
name: fetch-peer-rates
description: Gather peer central-bank policy rates from the open web, each cited to an official source, and write them into data/peer-rates.csv with SRC-NNN citations. Public data only.
argument-hint: <optional list of countries/central banks; defaults to a standard peer set>
user-invocable: true
---

# Skill: fetch-peer-rates

Owned by **data-steward**. Fills `data/peer-rates.csv` (from the shipped
`peer-rates.template.csv` schema) with current peer policy rates, each traceable
to an official source. This is the web half of the flagship task.

## Preflight

1. Read the anchor and `sources/source-registry.md` (next free `SRC` ids).
2. Confirm the target peer set. Default: US Federal Reserve, ECB, Bank of England,
   Bank of Russia, Bank of Georgia (adjust to the user's ask).
3. **Safe-Zone check**: this skill sends only *public queries* to the web — never
   any internal/restricted data. A soft reminder fires before each web call.

## Steps

1. For each peer, use `WebSearch`/`WebFetch` to find the **current main policy
   rate** from the **issuing central bank** (P0) or its official bulletin (P1).
   Capture the *exact rate name* (e.g. "ECB main refinancing operations rate",
   "Fed funds target — upper bound") and its **`as_of` date**.
2. **Log each figure** as a `SRC-NNN` row in `sources/source-registry.md`: entity,
   the rate + as_of, type, tier (P0/P1), and the resolvable URL.
3. **Write the data**: copy `data/peer-rates.template.csv` to
   `data/peer-rates.csv`, **drop the template's `#` comment lines**, and add one
   row per peer — `country, central_bank, policy_rate, as_of_date, source_id` —
   where `source_id` is the `SRC-NNN` you just logged. **No row without a source.**
   The finished `peer-rates.csv` must contain only the header and data rows.
4. If a rate can't be found from an official source, leave it out and record
   "not found — no official source located" rather than guessing
   (`.claude/rules/evidence-and-figures.md`).
5. **Register** the dataset: add/update the `DS-NNN` row for `peer-rates.csv` in
   `data/_index.md` (class: public).

## QA (run before returning)

Run **`source-qa`** on `data/peer-rates.csv` + the new registry rows: every rate
has an official `SRC-NNN` with an `as_of` date and P0/P1 tier; no fabricated
numbers; the CSV matches the registry. Fix flags; escalate an unfixable hard
failure to Main Claude.

## Output / return

- `data/peer-rates.csv` populated, `data/_index.md` and
  `sources/source-registry.md` updated.
- A short table of what was fetched (bank · rate · as_of · SRC id) and any peer
  that came back "not found".

## Suggested next step

`analyze` to combine these with the cleaned CBA series.
