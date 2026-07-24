---
name: intake
description: Bring a dataset into the Safe Zone — classify it (public/internal/restricted), register it as DS-NNN, and record its provenance as SRC-NNN — before any analysis touches it. Use for a local file or a planned web pull.
argument-hint: <path to a local file, or a description of the data to fetch>
user-invocable: true
---

# Skill: intake

Owned by **data-steward**. The gate every dataset passes through before use. It
does no analysis — it *classifies* and *registers*, and it is a human-in-the-loop
checkpoint (`.claude/rules/safe-zone.md`).

## Preflight

1. Read the anchor `context/analysis-brief.md` and `data/_index.md` (next free
   `DS` id).
2. Identify the dataset: a local file path, or a description of data to fetch
   from the web (hand the actual fetching to `fetch-peer-rates`).

## Steps

1. **Inspect** the file's shape without loading it wholesale: header row, column
   names, a few sample rows, row count. (For CSV, `head`; for `.xlsx`, note that
   reading needs the disposable venv — see `.claude/rules/ephemeral-compute.md`.)
2. **Classify** — decide `public` / `internal` / `restricted` and write a
   one-line reason. Central-bank rates → public. Files under `data/internal/`, or
   anything with names/emails/phone/account ids → restricted. Unsure ⇒
   restricted, and ask the user. **This is a checkpoint: state the class and the
   reason to the user before proceeding.**
3. **Register the dataset** — add a `DS-NNN` row to `data/_index.md` (name, file,
   class, source id, `status: raw`, note any obvious dirtiness).
4. **Register provenance** — add a `SRC-NNN` row to `sources/source-registry.md`
   for where the data came from (local file → tier P4 if it's the illustrative
   sample; an official upload → its real tier). Shipped sample is already
   `SRC-001`.
5. **If restricted** — do not proceed to analysis. Point the user to the
   anonymization pattern in `.claude/rules/safe-zone.md`; the data must be
   tokenized to `PRT-NNN` first, and it must never go to a web tool.

## QA (run before returning)

Run **`source-qa`** on the registry state you just wrote (class recorded,
provenance logged, no fabricated figures). Fix anything it flags. If a hard check
fails and you can't fix it, stop and report the blocker to Main Claude.

## Output / return

- Updated `data/_index.md` (new `DS-NNN`) and `sources/source-registry.md` (new
  `SRC-NNN`).
- A one-paragraph summary: the dataset, its class + reason, its id, and whether
  it is cleared to proceed (public/internal) or blocked pending anonymization
  (restricted).

## Suggested next step

`clean-data <DS-NNN>` for a public/internal file; or `fetch-peer-rates` if this
intake registered a planned web pull.
