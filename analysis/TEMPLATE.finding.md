<!--
FINDING TEMPLATE — copy to analysis/FND-NNN-slug.md and fill every section.
The template IS the quality standard: analysis-qa checks a finding against these
sections. An Empty-confidence finding still fills every section (it says "none
found" where applicable) — it does not omit sections.
Delete these HTML comments in the final file.
-->

# FND-NNN — <one-line question this finding answers>

| Field | Value |
|---|---|
| **Question** | <the exact analytical question> |
| **Inputs** | <DS-NNN cleaned dataset(s), SRC-NNN sources, prior FND-NNN> |
| **Window** | <the time range the numbers cover, e.g. 2024-01 … 2026-06> |
| **Confidence** | Solid / Workable / Shaky / Empty <— justify in Method> |
| **QA** | PASS / NEEDS-REWORK (from analysis-qa) · rounds run: N |
| **Author** | analyst · <date> |

## Answer first

<2–4 sentences. The direct answer to the question, in plain language, leading
with the number that matters. A manager should be able to stop reading here.>

## Key figures

| Metric | Value | Traces to |
|---|---|---|
| <e.g. CBA refinancing rate, latest> | <X.XX% as of YYYY-MM-DD> | DS-001 row / SRC-NNN |
| <e.g. Median peer policy rate> | <X.XX%> | computed (see Method) over SRC-… |
| <e.g. CBA spread vs peer median> | <±X.XX pp> | computed |

Every value in this table must resolve to a dataset cell, a logged source, or the
Method section below. No exceptions.

## Method (how each computed number was produced)

<Describe the ephemeral analysis script in prose — inputs, the transformation,
the formula for each computed metric — precisely enough that the number could be
reproduced. The script itself was deleted after running (rules/ephemeral-compute);
this section is the surviving audit trail. State any assumptions (how ties were
broken, how a missing peer month was handled).>

## Independent verification

| Check | Method | Result |
|---|---|---|
| <e.g. spread recomputed from raw cells> | separate verification script recomputed from DS-001 + sources, asserted equality | **PASS** / FAIL |
| <e.g. every peer rate has an as_of date> | script asserted non-null as_of | **PASS** / FAIL |

Verification script was written independently of the analysis script, run, and
then deleted. Overall verdict: **PASS / FAIL**. `scratch/` confirmed empty.

## What it means (cause → effect)

<Interpretation, in official tone, tying each claim to a figure above. Prefer
"CBA holds a positive spread of X pp over the peer median, because it has held at
Y% while peers cut, which implies Z." Avoid marketing language — see
rules/report-style.md.>

## Caveats & open questions

<Data-quality caveats, single-source figures, missing peers, staleness. If
confidence is Shaky or Empty, the reason lives here. "None" only if truly none.>
