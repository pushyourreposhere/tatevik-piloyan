---
name: draft-insurance-regulation
description: Draft a Central Bank of Armenia (CBA) secondary regulation («Կանոնակարգ») for the insurance sector, in Armenian, following real CBA drafting conventions — a Board-decision preamble citing the empowering law, numbered chapters (Գլուխ) and points (կետ), a definitions chapter, report forms as annexes (Հավելված), and an entry-into-force clause. Grounds every structural/legal claim in web-research (WRB) and marks any unconfirmed article number, deadline or threshold as a clearly-labelled placeholder. Use when asked to draft or amend an Armenian insurance regulation.
argument-hint: <the regulation's subject, e.g. "incident reporting for insurers">
user-invocable: true
---

# Skill: draft-insurance-regulation

Produces a **draft** CBA insurance-sector «Կանոնակարգ» in Armenian, shaped like a
real CBA regulation. The output is a **draft for review** — never presented as an
enacted act. Substance and form must trace to web-research briefs
(`web-research/findings/`), and any specific that could not be confirmed from an
official source is a **placeholder**, never an invented value.

## Preflight

1. Read `context/analysis-brief.md`, this workspace's evidence rule
   (`.claude/rules/evidence-and-figures.md`) and Safe-Zone rule.
2. Read the grounding briefs. **Form/conventions:** `WRB-004` (CBA «Կանոնակարգ»
   anatomy, legal basis, the 3/xx series, the 3/04 reporting pattern). **Subject
   matter:** the relevant WRB (e.g. `WRB-003` for incident reporting). If no
   grounding brief exists for the subject, **stop and ask** Main Claude to run
   `web-research` first — do not invent the substantive rules.
3. Note the confirmed gaps in those briefs (e.g. exact empowering article number,
   3/04 deadlines) — each becomes a placeholder in the draft.

## The CBA regulation shape (from WRB-004 — follow it)

- **Instrument:** a «Կանոնակարգ» **approved by (annexed to) a CBA Board decision**
  («ՀՀ Կենտրոնական բանկի խորհրդի որոշում»); the decision number carries the
  normative **«-Ն»** suffix; insurance regulations use the **3/xx** series.
- **Board-decision preamble** citing the empowering law and article
  ("Հիմք ընդունելով … հոդվածը", "ղեկավարվելով …"), an operative clause
  **«հաստատել»** the Regulation as an annex, and a closing **entry-into-force**
  clause tied to official publication.
- **Regulation body** in numbered chapters **«Գլուխ»**, conventionally:
  - **«Գլուխ 1. Ընդհանուր դրույթներ»** — aim/subject/scope,
  - **«Գլուխ 2. Հիմնական հասկացությունները»** — definitions
    ("Սույն կանոնակարգում օգտագործվող հասկացություններն ունեն հետևյալ
    նշանակությունը …"),
  - substantive chapters,
  - **transitional / final provisions**.
- **Numbering:** Գլուխ → **կետ** (continuous through the whole regulation) →
  **մաս** → **ենթակետ**. Self-reference: **«սույն կանոնակարգի … կետ/գլուխ»**.
- **Obligation phrasing:** «պարտավոր է», «ներկայացնում է / ներկայացվում է»,
  «սահմանվում է», «ոչ ուշ, քան …» — declarative-imperative present tense.
- **Forms as annexes:** report templates attached as numbered **«Հավելված»**,
  referenced from the relevant point.

## Steps

1. **Pin the subject and the empowering basis.** State the regulation's subject in
   one line; cite the empowering law(s) from `WRB-004` (Law "On Insurance and
   Insurance Activities" HO-177; Law "On the Central Bank of the RA"; and, where
   relevant, cross-reference the Law "On Cybersecurity"). Mark the exact article
   number as a placeholder `[հոդված __]` if `WRB-004` flagged it unconfirmed.
2. **Draft the Board-decision wrapper** (preamble → «հաստատել» → entry-into-force),
   with the regulation number as a placeholder `Կանոնակարգ 3/[__]`, decision
   number `[թիվ __-Ն]`.
3. **Draft the Regulation** chapter by chapter, mapping the requested sections to
   «Գլուխ»/«կետ». Every substantive rule (a definition, a report type, a deadline,
   a threshold, a data field) either cites its grounding WRB or is a marked
   placeholder `[…]`. Never state a concrete deadline/threshold as settled if the
   brief did not confirm it — wrap it: e.g. «ոչ ուշ, քան [24] ժամ»`[նախագծային —
   ճշտել]`.
4. **Attach the report form** as a «Հավելված» (a data-field table).
5. **Add a drafter's note** at the top: this is a **draft**, list the placeholders
   still to be confirmed against primary CBA/arlis.am text, and the grounding WRBs.
6. **Language:** Armenian, formal normative register; keep instrument names, law
   titles and any English/EU term used for comparison in parentheses on first use.

## Evidence & Safe-Zone rules

- No invented article numbers, regulation numbers, decision numbers, deadlines or
  thresholds. Unconfirmed ⇒ placeholder `[…]` with a note. ("Not confirmed" is an
  acceptable, expected state for a draft — `evidence-and-figures.md` Rule 0.)
- Every substantive rule traces to a grounding WRB (form → WRB-004; subject → the
  subject brief). Public sources only.

## Output / return

- `regulations/DRAFT-<slug>-hy.md` — the Armenian draft (canonical), with the
  drafter's note, placeholders, and a short "grounding & sources" footer citing
  the WRBs/WRS.
- Optionally render a `.docx` twin (see the `docx` skill) for circulation.
- Return: the draft path, the chapter list, and the list of placeholders that must
  be confirmed before the draft could become a real instrument.

## Scope

This skill drafts a **proposal for review**, not an enacted regulation. It does not
file, submit, or represent the draft as official CBA text.
