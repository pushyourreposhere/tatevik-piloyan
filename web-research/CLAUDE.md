# web-research/ — web captures, sources & research briefs

A research-input domain that runs parallel to `data/`: instead of local datasets,
it holds material gathered from the open web and the synthesized briefs written
from it. Everything here is **public** by definition — only public queries and
public pages ever enter this folder (`.claude/rules/safe-zone.md`).

Two things are tracked, each with its own stable id and its own index:

- **Sources** — every web page a claim rests on, one row per source in
  `sources/_index.md` as `WRS-NNN`, always paired with its resolvable URL.
- **Research briefs** — the synthesized write-ups, one file per brief in
  `findings/`, registered in `findings/_index.md` as `WRB-NNN`.

**Standards for this folder**
- Nothing published from a brief is unsourced. Every figure or claim in a
  `WRB-NNN` brief traces to a `WRS-NNN` source in `sources/_index.md`
  (`.claude/rules/evidence-and-figures.md`). "Not found / no source located" is an
  acceptable answer — never invent one.
- One source, one id. Each web source is logged **once** in `sources/_index.md`
  and cited by its `WRS-NNN`; capture the exact URL and the date it was accessed.
- `WRS-NNN` / `WRB-NNN` are **local to this folder**, distinct from the global
  `SRC-NNN` (in `sources/`) and `FND-NNN` (in `analysis/`). IDs are never reused
  or deleted — mark a retired entry `Deprecated` with a reason.
- These are **public** captures. Never place internal or restricted material
  here, and never send anything non-public to a web tool to gather it.

**Subfolders & primary files**
- `raw/` — raw fetched pages / search dumps, as captured (the audit trail behind a
  source; not edited).
- `sources/_index.md` — the source registry (`WRS-NNN` → URL).
- `findings/_index.md` — the brief registry (`WRB-NNN`); the briefs themselves are
  `findings/WRB-NNN-*.md`.
