# Trainer Guide — mapping the course onto the kit

This kit is the hands-on environment for **Weeks 3–4** of the course (Meetings 5–8
and the final project). Each meeting's practical part maps to one or more skills,
run against the shipped sample data. Everything the participants produce is
classified, sourced, verified, and QA'd by the kit's own machinery — so the
safety and quality lessons are enforced, not just discussed.

**Setup for every session:** open Claude Code with the `Demo/` folder as the
working directory. Read `README.md` once; the kit reads `CLAUDE.md` and
`context/analysis-brief.md` on its own.

---

## Meeting 5 — Data cleaning and basic analysis

| Topic | Kit piece | Do this |
|---|---|---|
| Working with Excel/CSV files | `data/cba-refinance-rate.csv` + `.xlsx` | Both ship; the `.xlsx` exercises the auto-install path |
| Importing data into a safe environment | `intake` skill + `rules/safe-zone.md` | `/intake data/cba-refinance-rate.csv` → watch it classify (public) and register `DS-001` |
| Missing values, errors, duplicates | `clean-data` skill | `/clean-data DS-001` → it finds the 2 blanks, the duplicate row, the `7.25%` type error |
| Anomaly detection | `clean-data` (range/IQR check) | It flags `95.0` (a ×10 typo of `9.5`) as an out-of-range outlier |
| Initial trend extraction + plain-language summary | `analyze` skill | Ask for the trend of the cleaned series; the finding's "Answer first" is the plain-language summary |

**Teaching beat:** the cleaning is done by a *throwaway* Python script that is
deleted, then an *independent* verification script re-checks it and is also
deleted (`rules/ephemeral-compute.md`). Show participants `scratch/` is empty
afterward and the cleaning log records what happened — the audit trail survives,
the code doesn't.

## Meeting 6 — Data structuring and visual presentation

| Topic | Kit piece | Do this |
|---|---|---|
| Role of visualization in decisions | `context/analysis-brief.md` | The whole brief is framed as "help a decision-maker" |
| Which chart for which case | `visualize` skill (decision guide) | Compare → bars, trend → line, spread → diverging bar |
| KPI presentation | `presentation` template (stat tiles) | Isolate the 2–4 headline numbers |
| ROI / cost dynamics / efficiency visuals | `fetch-peer-rates` → `analyze` → `visualize` | Here the "efficiency indicator" is the CBA-vs-peer **spread**; the "dynamics" is the rate trend |
| Prepare for presentation / report | `presentation` skill | `/presentation FND-001` → a self-contained HTML deck |

**Teaching beat:** `/fetch-peer-rates` pulls real peer rates from official sites,
each logged as a `SRC-NNN`. Every chart and KPI cites its source — visuals are not
decoration, and no number appears that isn't traceable.

## Meeting 7 — Financial and analytical report generation

| Topic | Kit piece | Do this |
|---|---|---|
| Executive Summary structure | `rules/report-style.md` | Situation → findings → cause→effect → implication → recommendation |
| Numbers → text conclusions | `presentation` skill + finding's "What it means" | Turn the spread/trend numbers into sentences |
| Official tone; cause-effect phrasing | `rules/report-style.md` (+ pathos blocklist) | No "game-changer / world-class"; state the mechanism |
| Human-in-the-loop | `qa-check` + the checklist in `rules/qa.md` | Participants review and revise the AI's draft before accepting |

**Teaching beat:** run `/qa-check` on the presentation and paste the
response-quality checklist. The point of Meeting 7 is that the human verifies and
owns the final text — the kit makes that a required, visible step.

## Meeting 8 — The full workflow with AI

The `workflow` skill **is** the seven-step workflow from this meeting:

| Step | In the kit |
|---|---|
| 1. Frame the problem | `workflow` step 1 (+ the anchor) |
| 2. Is the data in the Safe Zone? | `workflow` step 2 → `rules/safe-zone.md` classification (checkpoint) |
| 3. Anonymize if needed | `workflow` step 3 → `PRT-NNN` tokenization |
| 4. Build the prompt / plan | `workflow` step 4 (which agent owns each step) |
| 5. Process the data / generate | `workflow` step 5 → the agents + ephemeral compute |
| 6. Verify the result | `workflow` step 6 → independent verification + `qa-check` (checkpoint) |
| 7. Apply it in the work | `workflow` step 7 → human review, then use / publish |

**Guardrail exercise (hallucination + Safe-Zone):** ask the kit to include
`data/internal/loan-portfolio-CONFIDENTIAL.csv` in a web-bound step. The Safe-Zone
rule classifies it **restricted** and refuses to send it out — a concrete "where
was the risk and how did we manage it" moment. Then ask for a figure that isn't in
the data; the evidence rule answers "not found" instead of inventing one.

## Final project & individual application plan

Participants bring a task close to their own work:

1. `/intake <their file>` → decide **permissible or not** (the classification is
   the "are the data allowed?" decision).
2. If restricted → anonymize (`PRT-NNN`) or exclude; never send it out.
3. Run the pipeline (`clean-data` → `analyze` → `visualize` → `presentation`), or
   just `/workflow "<their question>"`.
4. `/qa-check` the result and review it themselves (human-in-the-loop).
5. Present the final, self-contained HTML.

## Final summary — the limitations to always remember

The kit encodes these; point participants back to the rules:

- **AI can fabricate numbers.** Every figure must trace to a source or a logged,
  verified computation. "Not found" beats a confident guess.
  (`rules/evidence-and-figures.md`)
- **The Safe Zone is a decision, not a default.** Classify before you use or
  send; restricted data never leaves the machine. (`rules/safe-zone.md`)
- **Verify independently.** A second, separate check catches what the first pass
  missed. (`rules/ephemeral-compute.md`, `rules/qa.md`)
- **The human owns the output.** Review and sign off before anything is used
  externally. (`rules/qa.md`, `workflow` step 7)

Three things to start using at work: (1) classify data before prompting;
(2) demand a source for every number; (3) run an independent check + a human
review before you act on an AI result.
