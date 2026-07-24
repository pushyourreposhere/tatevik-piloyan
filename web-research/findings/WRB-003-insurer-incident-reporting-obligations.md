# WRB-003 — Regulatory obligations for incident reporting by (re)insurance undertakings: FSB FIRE, EU DORA, IAIS, EIOPA and national regimes

| Field | Value |
|---|---|
| **Guiding question** | What are the current regulatory obligations for incident reporting by insurance/reinsurance undertakings — how must insurers report operational, ICT-related, cyber and major operational-resilience incidents to supervisors: WHAT must be reported, BY WHOM, TO WHOM, WHEN (timelines), in WHAT FORMAT/template, and against WHAT materiality/severity thresholds? |
| **Sub-questions** | (1) Definition of a reportable "incident" per regime and how "major"/"significant"/"material" is classified (quantitative & qualitative thresholds). (2) Reporting timelines: initial / intermediate / final. (3) Content & format: mandated templates, key fields, taxonomies; how FSB FIRE harmonizes formats. (4) Recipients & channels; onward sharing. (5) Overlaps & divergences a cross-border insurer must reconcile. (6) Direction of travel 2024–2026: changes / pending measures, effective dates, draft vs in-force. |
| **Sources** | WRS-018, WRS-019, WRS-020, WRS-021, WRS-022, WRS-023, WRS-024, WRS-025, WRS-026, WRS-027, WRS-028, WRS-029, WRS-030, WRS-031, WRS-032, WRS-033, WRS-034, WRS-035 |
| **Confidence** | Workable (leaning Solid on DORA/NAIC/FSB; Shaky on exact per-criterion DORA numeric thresholds and on Armenia insurance-specific rules — see Caveats) |
| **QA** | PASS · rounds run: 2 |
| **Author** | web-researcher · 2026-07-24 (web access date 2026-07-21) |

## Answer first

There is no single global incident-reporting rule for insurers; a (re)insurer faces a **layered stack** of regimes. The **only legally binding, prescriptive incident-reporting regime for EU (re)insurers is EU DORA** (Regulation (EU) 2022/2554, applicable since 17 January 2025): a financial entity must report a **major ICT-related incident** to its **competent authority** in three stages — an **initial notification within 4 hours of classifying the incident as major (and no later than 24 hours of becoming aware of it)**, an **intermediate report within 72 hours**, and a **final report within one month** — using **mandatory templates and a taxonomy set in Level-2 standards** (RTS on classification 2024/1772; RTS on content/timelines 2025/301; ITS on templates 2025/302) (WRS-021, WRS-022, WRS-023, WRS-024, WRS-025). The **FSB's FIRE** (final, 15 April 2025) is **not itself an obligation** — it is a common, voluntary **format** (87 information items, 39 optional) that authorities can adopt to harmonize reporting across regimes, building on the FSB's 2023 cyber-incident-reporting convergence recommendations (WRS-018, WRS-019, WRS-020). **IAIS** ICPs and its 2026 operational-resilience Application Paper are **principles/guidance, not hard timelines** (WRS-028, WRS-029). In the **US**, the NAIC Insurance Data Security Model Law requires notice to the state insurance **Commissioner within 72 hours** of determining a cybersecurity event occurred (WRS-030, WRS-031). The **UK** finalised (18 March 2026, in force 18 March 2027) a unified operational-incident and third-party reporting regime that expressly covers **UK Solvency II insurers and Lloyd's** (FCA PS26/2; PRA PS7/26, incl. SS1/26; BoE FMI PS) (WRS-032, WRS-035, WRS-033). For **Armenia**, a horizontal Law "On Cybersecurity" (in force 4 January 2026) imposes 72-hour reporting to an Authorized Body with CBA enforcement for financial firms; no insurance-*specific* incident-reporting template was located (WRS-034).

## What the sources say

### Sub-question 1 — Definition of a reportable incident; how "major/significant/material" is classified

**EU DORA.**
- DORA distinguishes an **"ICT-related incident"** (managed under Art. 17), a **"major ICT-related incident"** (which must be reported under Art. 19), and a **"significant cyber threat"** (voluntary notification) (WRS-021).
- Level-1 Art. 18 sets **seven classification criteria** an entity assesses to decide if an incident is "major": (a) clients / financial counterparts / transactions affected; (b) reputational impact; (c) duration and service downtime; (d) geographical spread; (e) data losses (availability, authenticity, integrity, confidentiality); (f) criticality of services affected; (g) economic impact (WRS-021).
- The **RTS Commission Delegated Regulation (EU) 2024/1772** codifies the materiality thresholds. An incident is classified **major** where the criticality of services is adversely impacted **and** either (i) any successful, malicious and unauthorised access to network and information systems that may result in data losses occurs, **or** (ii) **two or more** of the materiality thresholds are met (WRS-023, WRS-024). Per-criterion thresholds reported by the Austrian FMA and DORA aggregators include: clients/transactions affected **above 10%**, economic impact **above EUR 100,000**, and service downtime **over 2 hours** for services supporting critical or important functions (WRS-024, WRS-023). *(These exact numeric values rest on P1/P2 renderings, not a direct fetch of 2024/1772 — see Caveats.)* Recurring incidents that individually fall below threshold can require reporting on a **cumulative** basis (WRS-023).

**FSB FIRE / FSB 2023 CIR.** FSB's 2023 work stresses a **common definition of "cyber incident"** (via the updated Cyber Lexicon) to "avoid over-reporting of incidents that are not meaningful for financial authorities or financial stability" (WRS-020). FIRE itself is a format for **operational incidents, including cyber incidents**, and does not set a binding materiality threshold — thresholds remain with each adopting authority (WRS-018, WRS-019).

**IAIS.** ICP 8 (Risk Management and Internal Controls) and ICP 16 (ERM) require insurers to identify, assess, monitor and **communicate** risks, and are principle/standard/guidance in nature rather than prescriptive incident triggers (WRS-028). The 2026 Application Paper defines operational-resilience objectives and a supervisory **toolkit**, explicitly framed as supporting (not replacing) the ICPs (WRS-029).

**US NAIC.** A **"Cybersecurity Event"** is defined in §3; §6 notification is triggered when a licensee **determines** such an event occurred and certain criteria are met (e.g., **250 or more** consumers affected in another state, or a reasonable likelihood of material harm to a consumer or to the licensee's operations) (WRS-030, WRS-031).

**UK.** The PRA requires reporting where an incident poses a risk to (i) UK financial stability (for O-SIIs and Solvency II firms), (ii) the firm's safety and soundness, or (iii) **policyholder protection** (for insurers); the FCA covers incidents impacting its statutory objectives (WRS-032).

**Armenia.** Under the Law "On Cybersecurity," a cyber incident is "serious" if it threatens human life/health, national security or the economy, or disrupts critical-infrastructure functioning (WRS-034).

### Sub-question 2 — Reporting timelines (initial / intermediate / final)

- **DORA:** initial notification **within 4 hours of classification** as major, and in any case **no later than 24 hours** after the entity became aware of the incident; **intermediate report within 72 hours** of the initial notification (even if status unchanged); **final report within one month** (WRS-022, WRS-024, WRS-025). Corroborated across the RTS text mirror, the Austrian FMA, and the EBA joint-standards page.
- **NAIC:** **"as promptly as possible but in no event later than 72 hours"** from a determination that a cybersecurity event occurred (WRS-030, WRS-031).
- **UK:** PS26/2 / PS7/26 (incl. new PRA Supervisory Statement SS1/26) establish staged operational-incident reporting; the rules come into force **18 March 2027** (published 18 March 2026) (WRS-032, WRS-035). *(Exact hour-by-hour UK deadlines not confirmed from the official text — see Gaps.)*
- **Armenia:** updated information to the Authorized Body **within 72 hours** of becoming aware of a cyber incident (WRS-034).
- **FSB FIRE / IAIS:** no timelines of their own — FIRE is a format; IAIS is principles/guidance (WRS-018, WRS-028, WRS-029).

### Sub-question 3 — Content & format: templates, fields, taxonomies; FSB FIRE harmonization

- **DORA:** content, standard forms, templates and procedures are set by **ITS (EU) 2025/302** and **RTS (EU) 2025/301**; the classification taxonomy is in **RTS (EU) 2024/1772** (WRS-022, WRS-023, WRS-025). The initial notification must contain all information the competent authority needs to determine the incident's significance and assess cross-border impact (WRS-021).
- **FSB FIRE (final, 15 Apr 2025):** a common format of **87 information items, of which 39 are optional** (the October 2024 consultation had 99 items) (WRS-018, WRS-019). FSB released a **taxonomy package** with a data model based on the **Data Point Model (DPM)**, enabling machine-readable formats such as **XBRL** plus validation rules (WRS-018). FIRE is designed to be **interoperable** with existing systems and supports **phased implementation**, aiming to reduce duplicative reporting for firms operating across jurisdictions — the harmonization mechanism is a shared vocabulary/field set that authorities map their own regimes onto (WRS-018, WRS-019). It builds directly on the FSB's **2023 Recommendations to Achieve Greater Convergence in Cyber Incident Reporting** and the updated **Cyber Lexicon** (WRS-020).
- **NAIC:** notification is to the Commissioner with prescribed information about the event; no XBRL/machine-readable taxonomy (WRS-030).
- **UK:** standardized operational-incident reports plus a material-third-party register are introduced under PS26/2 / PS7/26; PS7/26 amends the Reporting and Notifications Parts of the PRA Rulebook and adds SS1/26 (WRS-032, WRS-035). *(Field-level template detail not confirmed — see Gaps.)*

### Sub-question 4 — Recipients & channels; onward sharing

- **DORA:** the financial entity reports to its **relevant competent authority** (for insurers in the EU, the national insurance supervisor); the competent authority provides **details onward** to the ESAs, the ECB, and (as relevant) ENISA, resolution authorities and CSIRTs to assess cross-border impact (Art. 19(6)) (WRS-021, WRS-024). DORA also mandated an ESA feasibility study (due 17 Jan 2025) on a **single EU Hub** for centralised incident reporting (WRS-025).
- **NAIC:** the **state insurance Commissioner**; notice also to the Commissioner of another state where **250+** residents are affected (WRS-030, WRS-031).
- **UK:** the **FCA / PRA** (and the **Bank of England** for financial market infrastructures); for insurers this is the PRA under PS7/26 (WRS-032, WRS-035, WRS-033).
- **Armenia:** the **Authorized Body** designated under the Law "On Cybersecurity," with the **CBA** enforcing operational-resilience obligations on financial organisations via supervisory inspections (WRS-034).
- **FSB FIRE:** authority-to-authority and firm-to-authority exchange; the FSB is the standard-setter, not a recipient (WRS-018).

### Sub-question 5 — Overlaps & divergences a cross-border insurer must reconcile

- **Binding vs. voluntary/soft law:** DORA, NAIC (once adopted by a state) and the UK PS regime are **binding**; FSB FIRE and IAIS ICPs/Application Paper are **not directly binding** on firms — FIRE is a format authorities may adopt; IAIS materials guide supervisors (WRS-018, WRS-028, WRS-029 vs WRS-021, WRS-030, WRS-032).
- **Different clocks:** DORA's 4h/24h → 72h → 1-month staged model contrasts with NAIC's single **72-hour** determination-based deadline and Armenia's **72-hour** cyber-incident deadline (WRS-022/WRS-024 vs WRS-030 vs WRS-034).
- **Scope:** DORA and the UK regime cover **operational** incidents broadly (including but not limited to cyber); NAIC and Armenia's law are **cyber/data-security**-centric (WRS-021, WRS-032 vs WRS-030, WRS-034).
- **Harmonization aim:** FIRE exists precisely to reduce the fragmentation among DORA, NAIC-type regimes and others by offering a common field set/taxonomy authorities can map to (WRS-018, WRS-019, WRS-020).
- **EU consolidation:** EIOPA **withdrew its 2020 Guidelines on ICT security and governance** (effective around DORA's application) so that DORA is the single lex specialis for EU insurers, removing the pre-DORA overlap (WRS-027, WRS-026).

### Sub-question 6 — Direction of travel 2024–2026 (draft vs in-force; effective dates)

- **DORA:** **in force / applicable since 17 January 2025**; Level-2 RTS/ITS (2024/1772; 2025/301; 2025/302) accompany it (WRS-025, WRS-026, WRS-023).
- **EIOPA:** first set of DORA technical standards published **17 January 2024**; 2020 ICT Guidelines **revoked 19 December 2024** (WRS-026, WRS-027).
- **FSB FIRE:** **final 15 April 2025**; FSB plans an industry/authority **workshop in 2027** to review implementation experience (WRS-018, WRS-019).
- **IAIS:** Application Paper on operational resilience objectives and toolkit **finalised February 2026** (consultations 2024–2025) (WRS-029).
- **UK:** unified operational-incident & third-party reporting **finalised 18 March 2026**, **in force 18 March 2027**; PS7/26 applies to UK Solvency II insurers, the Society of Lloyd's and its managing agents (WRS-032, WRS-035, WRS-033).
- **Armenia:** Law "On Cybersecurity" **in force 4 January 2026** (WRS-034).

### Comparative table

| Regime | Reportable incident / threshold | Timelines (initial / intermediate / final) | Format / template | Recipient | Status |
|---|---|---|---|---|---|
| **FSB FIRE** (WRS-018, WRS-019) | Operational incidents incl. cyber; no binding threshold (set by adopting authority) | None of its own (format only) | Common format: 87 info items (39 optional); DPM taxonomy, XBRL-ready | Authorities adopting it (firm→authority, authority→authority) | Final 15 Apr 2025; **voluntary** |
| **EU DORA** (WRS-021, WRS-022, WRS-023, WRS-024, WRS-025) | "Major ICT-related incident": 7 Art.18 criteria; major if critical-service impact + malicious-access/data-loss condition OR ≥2 materiality thresholds (2024/1772) | Initial ≤4h from classification (≤24h from awareness) / intermediate ≤72h / final ≤1 month | Mandatory templates (ITS 2025/302) + content/timelines (RTS 2025/301) | National competent authority; onward to ESAs, ECB, ENISA | **In force**, applicable since 17 Jan 2025 |
| **IAIS** (WRS-028, WRS-029) | Principles-based (ICP 8, ICP 16); operational-resilience objectives | None prescribed | None prescribed (toolkit/guidance) | Insurance supervisor (via ICP framework) | ICPs Dec 2024; Application Paper final Feb 2026; **guidance** |
| **EIOPA** (WRS-026, WRS-027) | Applies DORA to EU insurers; 2020 ICT Guidelines withdrawn | Per DORA | Per DORA ITS/RTS | National insurance supervisors / EIOPA | DORA STS from 17 Jan 2024; old guidelines revoked 19 Dec 2024 |
| **US NAIC Model #668** (WRS-030, WRS-031) | "Cybersecurity Event" (§3); triggers incl. 250+ consumers / material-harm likelihood | ≤72h from determination (single deadline) | Prescribed notice content; no XBRL taxonomy | State insurance Commissioner (+ other states if 250+ residents) | Model law; **in force in adopting states** |
| **UK PRA/FCA/BoE** (WRS-032, WRS-035, WRS-033) | Operational incident risking financial stability / safety & soundness / policyholder protection; PS7/26 covers Solvency II insurers & Lloyd's | Staged reporting (exact hours not confirmed) | Standardized reports + material-third-party register (PRA: SS1/26, Rulebook amendments) | FCA / PRA (BoE for FMIs) | Final 18 Mar 2026; **in force 18 Mar 2027** |
| **Armenia (Law on Cybersecurity; CBA)** (WRS-034) | "Serious" cyber incident (life/health, national security/economy, critical infrastructure) | ≤72h to Authorized Body | Not located (insurance-specific) | Authorized Body; CBA enforces for financial firms | Law in force 4 Jan 2026; **no insurance-specific template located** |

## Sources used

| WRS | Title / publisher | Tier | Date accessed | URL |
|---|---|---|---|---|
| WRS-018 | FSB — "FSB finalises the common Format for Incident Reporting Exchange (FIRE)" (press release, 15 Apr 2025) | P0 | 2026-07-21 | https://www.fsb.org/2025/04/fsb-finalises-the-common-format-for-incident-reporting-exchange-fire/ |
| WRS-019 | FSB — "Format for Incident Reporting Exchange (FIRE): Final report" (15 Apr 2025) | P0 | 2026-07-21 | https://www.fsb.org/uploads/P150425-1.pdf |
| WRS-020 | FSB — "Recommendations to Achieve Greater Convergence in Cyber Incident Reporting: Final report" (13 Apr 2023) | P0 | 2026-07-21 | https://www.fsb.org/2023/04/recommendations-to-achieve-greater-convergence-in-cyber-incident-reporting-final-report/ |
| WRS-021 | EUR-Lex — Regulation (EU) 2022/2554 (DORA), Arts 17–23 | P0 | 2026-07-21 | https://eur-lex.europa.eu/eli/reg/2022/2554/oj/eng |
| WRS-022 | Springlex — DORA RTS on incident reporting, Art. 5 time limits (reproducing Del. Reg (EU) 2025/301) | P2 | 2026-07-21 | https://www.springlex.eu/en/packages/dora/rts-ir-regulation/article-5/ |
| WRS-023 | EUR-Lex — Commission Delegated Regulation (EU) 2024/1772 (RTS on classification of major ICT-related incidents) | P0 | 2026-07-21 | https://eur-lex.europa.eu/eli/reg_del/2024/1772/oj/eng |
| WRS-024 | FMA Österreich — "DORA – ICT-related incidents" | P1 | 2026-07-21 | https://www.fma.gv.at/en/cross-sectoral-topics/dora/dora-ict-related-incidents/ |
| WRS-025 | EBA — "Joint Technical Standards on major incident reporting" under DORA | P0 | 2026-07-21 | https://www.eba.europa.eu/activities/single-rulebook/regulatory-activities/operational-resilience/joint-technical-standards-major-incident-reporting |
| WRS-026 | EIOPA — "ESAs publish first set of rules under DORA … incident classification" (17 Jan 2024) | P1 | 2026-07-21 | https://www.eiopa.europa.eu/esas-publish-first-set-rules-under-dora-ict-and-third-party-risk-management-and-incident-2024-01-17_en |
| WRS-027 | EIOPA — "EIOPA revokes previous guidelines to avoid duplications and overlaps with DORA" (19 Dec 2024) | P1 | 2026-07-21 | https://www.eiopa.europa.eu/eiopa-revokes-previous-guidelines-avoid-duplications-and-overlaps-dora-2024-12-19_en |
| WRS-028 | IAIS — "Insurance Core Principles and ComFrame" (Dec 2024; ICP 8, ICP 16) | P0 | 2026-07-21 | https://www.iais.org/uploads/2025/06/IAIS-ICPs-and-ComFrame-December-2024.pdf |
| WRS-029 | IAIS — "Final version of the Application Paper on operational resilience objectives and toolkit published" (Feb 2026) | P0 | 2026-07-21 | https://www.iais.org/2026/02/final-version-of-the-application-paper-on-operational-resilience-objectives-and-toolkit-published/ |
| WRS-030 | NAIC — "Insurance Data Security Model Law" (Model #668), §6 | P0 | 2026-07-21 | https://content.naic.org/sites/default/files/model-law-668.pdf |
| WRS-031 | NAIC — "The NAIC Insurance Data Security Model Law" (government-affairs brief, Aug 2025) | P1 | 2026-07-21 | https://content.naic.org/sites/default/files/government-affairs-brief-data-security-model-law.pdf |
| WRS-032 | FCA — "PS26/2: Operational incident and third party reporting" (18 Mar 2026) | P0 | 2026-07-21 | https://www.fca.org.uk/publications/policy-statements/ps26-2-operational-incident-third-party-reporting |
| WRS-033 | Bank of England — "Operational resilience: operational incident and outsourcing and third-party reporting for FMIs" (2026) | P0 | 2026-07-21 | https://www.bankofengland.co.uk/paper/2026/ps/operational-resilience-operational-incident-and-outsourcing-and-third-party-reporting-for-fmis |
| WRS-034 | Chambers and Partners — "Cybersecurity 2026 – Armenia" Global Practice Guide | P3 | 2026-07-21 | https://practiceguides.chambers.com/practice-guides/cybersecurity-2026/armenia |
| WRS-035 | Bank of England / PRA — "PS7/26: Operational resilience: Operational incident and third-party reporting" (Solvency II insurers & Lloyd's; incl. SS1/26) | P0 | 2026-07-21 | https://www.bankofengland.co.uk/prudential-regulation/publication/2026/march/operational-incident-and-third-party-reporting-policy-statement |

Every row above also appears in `web-research/sources/_index.md`. Claims are cited by `WRS-NNN`, never by bare URL.

## Gaps

- **Exact per-criterion DORA numeric thresholds** in RTS (EU) 2024/1772 (e.g., the precise percentages, currency amounts and downtime hours per criterion) could not be read from the primary EUR-Lex text (403 to WebFetch); the figures shown (clients >10%, economic impact >EUR 100,000, downtime >2 hours) rest on the Austrian FMA (P1) and DORA aggregators (P2) and should be verified against 2024/1772 before publication in a binding document.
- **UK exact staged deadlines (hours/days)** and the field-level template of PS26/2 / PS7/26 — not confirmed from the official policy statements; only the trigger, recipients, and 18 Mar 2027 in-force date are sourced. Marked "not confirmed from official text".
- **Central Bank of Armenia insurance-*sector*-specific incident-reporting requirement** (dedicated template, deadline, threshold for insurers) — **not found in official sources**. Only the horizontal Law "On Cybersecurity" (72h, in force 4 Jan 2026) and CBA enforcement via inspections were located, via a law-firm practice guide (P3), not a cba.am page.
- **IAIS ICP 21 (Countering Fraud) supervisory-reporting specifics** — not separately confirmed; IAIS materials reviewed are principle/guidance-level with no incident-reporting deadline.
- **FIRE final item count** (87 items / 39 optional) is corroborated across two search renderings of the FSB final report but was not read from a directly-fetched FSB PDF (site 403).

## Caveats & confidence

- **Overall: Workable.** The core, load-bearing obligations (DORA's 4h/24h→72h→1-month staged model and its Level-2 instruments; NAIC's 72-hour rule; FSB FIRE's nature, date and item count; the UK 18 Mar 2027 in-force date; DORA's recipient/onward-sharing) are each corroborated from a primary/official angle plus at least one second source, warranting **Solid**-level trust individually.
- **Shaky sub-elements, tagged down:** (i) the *precise numeric* DORA classification thresholds rest on P1/P2 renderings, not the fetched primary RTS; (ii) UK hour-level deadlines and template fields are unconfirmed; (iii) the **Armenia** finding rests on a **single P3** law-firm practice guide and is **not insurance-specific** — it must not be presented as a CBA insurance rule. These pull the overall rating below Solid.
- **Access method:** official EU/FSB/IAIS/NAIC/UK sites returned 403 to WebFetch; all official text was read via WebSearch snippets quoting the source, with a second corroborating angle for load-bearing claims, per the approved fallback. Tiers reflect the *source* (P0 issuing body / P1 official interpretive), not the retrieval method.
- **Nature-of-instrument caveat:** FSB FIRE and IAIS outputs are **not** binding obligations on firms; presenting them alongside DORA/NAIC/UK must preserve that distinction.
