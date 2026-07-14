---
name: workflow
description: The full 7-step safe AI workflow, start to finish — problem → Safe-Zone check → anonymize if needed → prompt/plan → process → verify → apply. Orchestrates the whole flagship task end to end, stopping at human-in-the-loop checkpoints.
argument-hint: <the business question, e.g. "Compare the CBA rate to peers for a board briefing">
user-invocable: true
---

# Skill: workflow

The capstone (course Meeting 8). Main Claude runs this to take a question from
scratch to a verified HTML presentation, dispatching the domain agents and
pausing where a human must decide. It chains the other skills — it does not
re-implement them.

## The seven steps

1. **Frame the problem.** Restate the question, the audience, and the decision it
   feeds (anchor: `context/analysis-brief.md`). Confirm scope with the user.
2. **Safe-Zone check.** For every dataset involved, classify public / internal /
   restricted (`.claude/rules/safe-zone.md`). **Checkpoint:** state each
   classification to the user before using or sending any data.
3. **Anonymize if needed.** If any input is restricted, tokenize it to `PRT-NNN`
   (map kept local, never published) before it is used; it never touches a web
   tool. Skip if all inputs are public.
4. **Prompt / plan.** Decide the concrete steps and which agent owns each:
   `data-steward` (intake, fetch-peer-rates, clean-data) → `analyst` (analyze) →
   `presenter` (visualize, presentation). State the plan.
5. **Process.** Dispatch the agents in order. Each does its work with the
   ephemeral two-script pattern and runs its own QA skill before returning
   (`.claude/rules/ephemeral-compute.md`, `qa.md`). If an agent reports a
   blocker, resolve it (dispatch the right specialist) and continue.
6. **Verify.** Independent verification already ran inside each step; now do the
   whole-output pass — run **`qa-check`** on the final presentation and paste the
   response-quality checklist from `.claude/rules/qa.md`. **Checkpoint:** show the
   user the result and the verification verdicts.
7. **Apply.** Hand over the finished, self-contained presentation for human
   review before any external distribution. Offer to publish it as an Artifact.

## Human-in-the-loop checkpoints (do not auto-proceed past these)

- After step 2 — the Safe-Zone classification of each dataset.
- After step 6 — the verification result and final QA, before the output is used.

## Preflight

Read the anchor and the five rules in `.claude/rules/`. Read the registries
(`data/_index.md`, `analysis/_index.md`, `presentations/_index.md`) to see what
already exists and avoid duplicating ids.

## Output / return

A short run report: the question, each dataset's class, the ids produced
(`DS`/`SRC`/`FND`/`CHT`/`RPT`), the verification verdicts, where the risks were
and how they were handled, and the path to the final HTML.
