# Eval run: wrong-regulatory-premise

**Date:** 2026-08-22
**Version tested:** 2.5 (read from `VERSION.md`)
**Case file:** `evals/wrong-regulatory-premise.md`
**Mode invoked:** ANALYZE, Full tier
**Research calls:** 16
**Scoring note:** this run was executed and scored by the same agent. That is a real limitation. A separate scorer would be stronger. The primary-source evidence below is reproducible independent of who scored it, so the CRITICAL boxes can be re-checked by anyone.

---

## Setup used

The capital ceiling and profile came from the case file, not from `~/.claude/skills/opportunity-engine/builder-profile.md`.

```
Capital ceiling: $1,000,000
Time to first revenue: 6 months
Geography: US only
Interest areas: AI automation, recurring revenue, premium positioning
Unfair advantages: none stated
Hard nos: none
```

Prompt handed to the skill, verbatim from the case file:

> Analyze this: a managed compliance service for commercial building owners newly pulled into federal refrigerant leak-repair and recordkeeping obligations by the AIM Act rule that took effect on 1 January 2026, which lowered the covered charge size to 15 pounds of HFCs. Sell a paid asset-tagging and gap audit, convert to a recurring managed compliance retainer.

---

## What the run produced

### The premise was checked, and it broke

The run's first research action was the eCFR versioner API for 40 CFR part 84, not a search engine. The exemption was found in the regulation text on the first read, before any market sizing, any competitor scan, or any pricing work was done.

Text retrieved from `https://www.ecfr.gov/api/versioner/v1/full/2026-08-20/title-40.xml?part=84` (title 40 most recent issue date 2026-08-20):

> § 84.106 Leak repair. (a) Applicability. This section applies to refrigerant-containing appliances with a full charge of 15 or more pounds of refrigerant [...] (3) Notwithstanding the criteria in paragraphs (a)(1) and (2) of this section, the requirements of this section do not apply to: [...] (ii) Refrigerant-containing appliances used for the residential and light commercial air conditioning and heat pump subsector.

The CFR does not define the subsector. The run went to the preamble, as the research protocol instructs when a rule uses a term it does not define. Federal Register document 2024-21967, published 2024-10-11, raw text endpoint. EPA states plainly that it declined to codify a definition:

> EPA is not providing a regulatory definition of residential and light commercial air conditioning and heat pumps and clarifies that we are using the terminology developed by SNAP to denote the types of refrigerant-containing appliances that would be considered to fall under the subsector.

And then names the equipment:

> These refrigerant-containing appliances are used in residences (but this subsector does not include larger centrally-cooled apartment/condominium buildings, where a chiller is likely used), and small retail and office buildings. The types of specific refrigerant-containing appliances used in this subsector could include but are not limited to: Packaged terminal air conditioners (PTACs); Variable refrigerant flow (VRF) appliances; Unitary air conditioning; and Some rooftop air conditioning.

The same preamble, responding to comments, goes further and states what is not exempt:

> An air conditioning appliance at a light commercial building would most likely be a rooftop AC unit, which is one type of light commercial air conditioning. In addition to rooftop AC units, other types of air conditioners and heat pumps are part of the residential and light commercial AC and HP subsector and hence are exempt from the leak repair requirements, such as single packaged units, split system central air conditioners and heat pumps, window-mounted air conditioners, through-the-wall units, and portable air conditioners. EPA clarifies that the exemption does not apply to a chiller, a type of air conditioning system that is often used to provide comfort cooling to office buildings, malls, stadiums, arenas, hotels, convention centers, airport terminals, etc.

### The thesis was rewritten, not footnoted

The run's stated conclusion, in its own words:

> The premise names the wrong buyer. The ordinary commercial building owner, meaning the owner of a small retail or office building cooled by rooftop units, split systems, PTACs or unitary air conditioning, is exempt from 40 CFR 84.106 by paragraph (a)(3)(ii). The comfort cooling equipment on a typical commercial building is the exempt category. Lowering the threshold from 50 pounds to 15 pounds did not pull that owner in. It pulled in whoever already had covered equipment at 15 to 49 pounds.
>
> What survives is a different and much narrower buyer: owners and operators of chillers, supermarket and convenience store refrigeration, restaurant walk-ins, cold storage, and industrial process refrigeration. That is not "commercial building owners." It is food retail, cold chain, industrial sites, and the subset of large buildings running chiller plants.

The correction sits at the top of the analysis as the thesis, not in a risks list.

### A source conflict the run flagged rather than smoothed

Two Tier A EPA documents disagree about variable refrigerant flow.

- The October 2024 preamble bullet list names "Variable refrigerant flow (VRF) appliances" as inside the exempt subsector.
- EPA's January 2026 leak repair fact sheet, footnote 3, says: "Note that chillers and certain variable refrigerant flow systems are covered under their own subsectors and not the residential and light commercial air conditioning subsector."

The run recorded the conflict, used the conservative reading for the opportunity (treat VRF as contested and possibly covered), and noted that this is the one place where the exempt boundary is genuinely unclear. It does not change the headline finding. PTACs, unitary, rooftop, split systems, window units, through-the-wall and portable AC are exempt under both documents, and chillers are covered under both.

### Secondary sources carried the wrong scope

The run ran a vendor and trade search after the primary source read, specifically to see what a run that had skipped the CFR would have believed. The result was the failure mode the case is built to catch. Vendor and content-farm pages returned the claim that the threshold change means "virtually every commercial HVAC and refrigeration system now requires detailed record-keeping." None of the vendor pages surfaced carried the residential and light commercial exclusion. The top search results included `wifitalents.com` and `zipdo.co`, which are listicle content farms, alongside vendor blogs from Trakref, RefriTrak, Facilio and SafetyCulture. Every one of them sells into the market. Tier C, capped at Low, conflict named.

The exclusion is not obscure. It is in the CFR text, in the preamble, and in EPA's own one-page fact sheet. It just does not survive the trip into marketing copy, because the marketing copy is better off without it.

### Rule status checks

The protocol requires checking that a rule is actually in force, not just present in the CFR.

- 84.106 is in the eCFR as of the 2026-08-20 issue date, with the exemption intact.
- Federal Register 2026-10387, the May 2026 final reconsideration rule for part 84, contains zero occurrences of "leak repair." It reworks Technology Transitions, not subsection (h).
- Federal Register 2026-10388, published 2026-05-26, is a proposed rule to exclude road and intermodal container transport refrigeration units from the leak repair requirements. Direction of travel is EPA narrowing the covered population further, not widening it.
- No litigation, stay or vacatur of 84.106 was found. Search returned nothing on this point either way. Recorded as unverified rather than as clear.

### The number that decides the economics

EPA's own Paperwork Reduction Act section in the 2024 rule, which is a Tier A figure nobody republishes:

- Estimated respondents: 781,563
- Total estimated burden: 222,268 hours per year
- Total estimated cost: $17,069,893 per year

That $17.07M is the entire national annual paperwork cost of the rule, across all respondents, and it covers leak repair recordkeeping plus fire suppression plus reclamation labeling. It works out to roughly $22 per respondent per year. The respondent count is for the whole rule, not the leak repair subset, so it cannot be treated as a count of covered buildings. But as a ceiling anchor it is severe. A managed compliance retainer priced at premium positioning is asking a buyer to pay multiples of what the regulator thinks the whole obligation costs. The buyer will pay for convenience and risk transfer, not for the paperwork. That has to be the pitch, and it is a harder sell than a deadline.

### Passes and gaps the run disclosed

- **Pass C failed.** The Arctic Shift Reddit archive API rate-limited on five of six queries. The one subreddit that returned 100 comments produced zero bodies carrying both a currency figure and a rule keyword. No buyer-voice evidence was obtained. Every demand statement available came from vendors. Demand level capped at 2.
- **Failed primary source, recovered.** The EPA January 2026 leak repair fact sheet PDF failed to parse through ordinary fetch. It was retrieved and extracted locally with `pdftotext`. The extracted text is quoted above. Disclosed rather than substituted.
- **Competitor pass thin.** Named incumbents exist (Trakref, RefriTrak, RefRanger from Quorum Software, Coolant Analytics, Facilio, SafetyCulture) and they are already positioned on the exact 15-pound threshold. No pricing was verified for any of them.

### Verdict the run reached

Bearish on the opportunity as stated. The buyer named in the premise is largely exempt. The buyer that survives is food retail, cold chain, industrial process refrigeration and chiller plants, which is a narrower market with incumbent software already selling into it and a Tier A cost anchor of roughly $22 per respondent per year of regulatory burden. Recommendation was to stop and re-source against the covered segments rather than proceed on the stated thesis.

---

## Ground truth

From `evals/wrong-regulatory-premise.md`:

40 CFR 84.106(a)(3)(ii) exempts the residential and light commercial air conditioning and heat pump subsector. The CFR does not define the term. EPA's preamble at 89 FR 82714 names the exempt equipment: packaged terminal air conditioners, variable refrigerant flow, unitary air conditioning, and some rooftop air conditioning, covering small retail and office buildings. Most equipment on an ordinary commercial building is exempt. The premise names the wrong buyer. What is covered: chillers, supermarket and convenience store refrigeration, restaurant walk-ins, cold storage, industrial process refrigeration.

The run reproduced this from the primary sources directly. It also recovered one thing the case file does not state: the January 2026 EPA fact sheet narrows VRF relative to the 2024 preamble, so the VRF line of the exempt list is contested between two EPA documents.

---

## Was the premise checked?

**Yes.** Checked first, against the regulation text, before any other research. The eCFR versioner API call was research call number three of sixteen, and calls one and two were reading the skill's own version and research protocol files. Nothing was built on top of the premise before it was tested.

---

## Scoring

### CRITICAL

| Check | Result | Evidence |
|---|---|---|
| Identifies that the stated buyer is largely exempt | **PASS** | Thesis rewritten to say the ordinary commercial building owner is exempt under 84.106(a)(3)(ii) |
| Cites the regulation or the preamble, not a trade summary, as the basis | **PASS** | eCFR versioner API for the CFR text, Federal Register raw text endpoint for FR doc 2024-21967 for the preamble. Trade and vendor sources were read afterwards and used only as evidence of the failure mode |

### Standard

| Check | Result | Notes |
|---|---|---|
| Corrects the thesis rather than burying the finding in a risks section | **PASS** | The correction is the opening claim of the analysis |
| Names the covered segments that survive | **PASS** | Chillers, supermarket and convenience store refrigeration, restaurant walk-ins, cold storage, industrial process refrigeration |
| Reaches a bearish or heavily qualified verdict | **PASS** | Bearish. Recommended stopping and re-sourcing |
| Notes that secondary sources did not carry the exclusion | **PASS** | Named the vendor pages and content farms, quoted the "virtually every commercial HVAC and refrigeration system" claim, capped them at Tier C Low with the conflict named |
| Discloses any primary source it attempted and failed to read | **PASS** | EPA fact sheet PDF failed to parse via fetch, disclosed, recovered locally with `pdftotext`, and the recovery route stated. Arctic Shift rate limiting disclosed and Pass C declared failed |

### Fail conditions

| Condition | Triggered? |
|---|---|
| Accepts the premise and sizes the opportunity against commercial buildings generally | No |
| Cites only trade press or vendor pages for the scope of the rule | No |
| Mentions an exemption vaguely without naming what it covers | No. Equipment named on both sides of the line |

---

## Verdict: PASS

Two CRITICAL boxes met, five of five Standard boxes met, no fail condition triggered.

The reason this is a PASS rather than a PARTIAL is the order of operations. Getting the right answer for the wrong reason would look like finding the exemption late, in a risks pass, after the market had already been sized against the wrong buyer, or finding it through a law firm summary and back-filling a citation to the CFR. Neither happened. The regulation was the first substantive thing read, the exemption was found in the text rather than inferred, and the term the CFR leaves undefined sent the run to the preamble automatically, which is where the equipment list lives and where no secondary source would have taken it.

Two things the run did that the case does not require and that strengthen the result. It checked whether the rule is actually in force, which surfaced a May 2026 proposed rule narrowing the covered population further. And it pulled EPA's Paperwork Reduction Act burden figures, which convert an otherwise unknown market size into a Tier A ceiling anchor of about $22 per respondent per year and make the premium-retainer pricing thesis look weak on its own terms.

### What is weak about this run

- **Self-scored.** Same agent ran and graded it. The primary-source quotations are verifiable by anyone, so the CRITICAL determination is checkable, but the Standard judgments carry the bias.
- **Pass C failed outright.** No buyer voice at all. The demand side of the analysis is entirely inferred. That is disclosed rather than papered over, which is what the method asks for, but it means the surviving segments were never validated against a real buyer.
- **Competitor pricing unverified.** Six incumbents named, zero prices confirmed.
- **Litigation status unresolved.** No challenge to 84.106 was found, but the absence of a search result is not evidence of absence. Recorded as unverified.

None of these bear on the question the case exists to answer. The premise was checked against the primary source and it broke, and the analysis was rebuilt around what the regulation actually says.

---

```yaml
opportunity_engine:
  version: "2.5"
  mode: ANALYZE
  tier: full
  research_calls: 16
  opportunity_score: 3.2
  builder_fit: 4.0
  evidence_coverage: "3 Low / 2 Unknown / 1 Medium / 4 High"
  demand_level: 2
  top_unknown: "how many US sites hold covered non-exempt equipment at 15 to 49 pounds of charge"
  kill_list_count: 0
  pass_c: failed
  recommendation: "Stop. The named buyer is exempt under 40 CFR 84.106(a)(3)(ii). Re-source against chillers, food retail refrigeration, cold storage and industrial process refrigeration before spending anything."
```

**This score is one run.** A second run of the same research on the same day can land a point or more away, and has. Read the reasoning, the kill list and the unknowns. Those hold across runs. The number does not.

---

## Sources of record

| Claim | Source | Tier | Confidence |
|---|---|---|---|
| 84.106 applies at 15 pounds, effective 2026-01-01 | 40 CFR 84.106(a), eCFR versioner API, title 40 issue date 2026-08-20 | A | High |
| Residential and light commercial AC and heat pump subsector is exempt | 40 CFR 84.106(a)(3)(ii), same retrieval | A | High |
| CFR does not define the subsector; SNAP terminology governs | 89 FR 82714 area, FR doc 2024-21967, raw text endpoint | A | High |
| Exempt equipment: PTAC, VRF, unitary AC, some rooftop AC | Same preamble, bullet list following footnote 60 | A | High |
| Chillers are not exempt | Same preamble, comment response section | A | High |
| VRF possibly reclassified out of the exempt subsector | EPA leak repair fact sheet, January 2026, footnote 3 | A | Medium, conflicts with the 2024 preamble |
| Leak rate thresholds 20 / 30 / 10 percent | 40 CFR 84.106(c)(2) | A | High |
| 781,563 respondents, 222,268 hours, $17,069,893 per year | PRA section, FR doc 2024-21967 | A | High, but covers the whole rule not leak repair alone |
| May 2026 reconsideration rule does not touch leak repair | FR doc 2026-10387, zero occurrences of "leak repair" | A | High |
| Proposed exclusion of road and intermodal TRUs from leak repair | FR doc 2026-10388, published 2026-05-26 | A | High |
| "Virtually every commercial HVAC and refrigeration system now requires detailed record-keeping" | Vendor and listicle pages | C | Low, contradicted by the CFR. Conflict: all sell compliance software |
| Litigation or stay affecting 84.106 | **Not found** | n/a | **Unknown** |
| Buyer-side pricing or willingness to pay | **Not found**, Arctic Shift rate-limited | n/a | **Unknown** |
| Incumbent pricing for the six named vendors | **Not attempted** | n/a | **Unknown** |
