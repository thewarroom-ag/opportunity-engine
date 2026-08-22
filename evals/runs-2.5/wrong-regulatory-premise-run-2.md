# Eval run: wrong-regulatory-premise

**Date:** 2026-08-22
**Version tested:** 2.5, read from `VERSION.md` in the repo copy
**Case file:** `evals/wrong-regulatory-premise.md`
**Mode invoked:** ANALYZE, Full tier
**Research calls:** about 34 direct, plus two parallel research shards

**Which build was actually loaded.** The installed skill at `~/.claude/skills/opportunity-engine` reports 2.4. The repo copy reports 2.5. `SKILL.md` and all seven files in `references/` are byte-identical between the two. The 2.5 release removed the two example runs and edited documentation only, and its own changelog says nothing in the scoring path changed. So the behaviour under test is 2.5 behaviour, and the version string was taken from the repo `VERSION.md`.

**Collision with a parallel session.** A completed run of this same case already existed at this path, written at 14:21 today by another session. It was preserved as `wrong-regulatory-premise.parallel-session-1421.md` before this file was written. Nothing was deleted. The two runs were independent and reached the same verdict. That convergence is discussed at the end, because it is the most useful thing this second run produces.

**Self-scoring limitation.** The same agent ran this and graded it. Every CRITICAL determination below rests on quoted primary-source text with a retrievable citation, so anyone can re-check it. The standard criteria carry more grader bias.

---

## Setup used

From the case file. The real builder profile at `~/.claude/skills/opportunity-engine/builder-profile.md` was not read.

```
Capital ceiling: $1,000,000
Time to first revenue: 6 months
Geography: US only
Interest areas: AI automation, recurring revenue, premium positioning
Unfair advantages: none stated
Hard nos: none
```

Prompt, verbatim from the case file:

> Analyze this: a managed compliance service for commercial building owners newly pulled into federal refrigerant leak-repair and recordkeeping obligations by the AIM Act rule that took effect on 1 January 2026, which lowered the covered charge size to 15 pounds of HFCs. Sell a paid asset-tagging and gap audit, convert to a recurring managed compliance retainer.

---

## What the run produced

### The premise was tested before anything was built on it

The first substantive research action was the eCFR versioner API, not a search engine. No market sizing, no competitor scan and no pricing work happened until the rule text had been read.

`https://www.ecfr.gov/api/versioner/v1/full/2026-08-20/title-40.xml?part=84` (2026-08-20 is title 40's most recent issue date; a request for today's date is rejected by the API, which is worth knowing).

> § 84.106 Leak repair. (a) Applicability. This section applies to refrigerant-containing appliances with a full charge of 15 or more pounds of refrigerant where the refrigerant contains: (1) A regulated substance, (2) A substitute for a regulated substance that has a global warming potential greater than 53 [...] (3) Notwithstanding the criteria in paragraphs (a)(1) and (2) of this section, the requirements of this section do not apply to: (i) Appliances (as defined in 40 CFR 82.152) containing solely an ozone-depleting substance [...] (ii) Refrigerant-containing appliances used for the residential and light commercial air conditioning and heat pump subsector. (4) The requirements of this section apply as of January 1, 2026.

The premise is right about the 15 pound threshold and right about the 1 January 2026 date. It is wrong about the buyer.

### The undefined term sent the run to the preamble

`§ 84.102` defines `Comfort cooling`, `Commercial refrigeration` and `Industrial process refrigeration`. It does not define "residential and light commercial air conditioning and heat pump subsector". Neither does `§ 84.3`. Grep across the whole of part 84 returns the phrase three times, none of them a definition.

That is the trigger in `research-protocol.md`: when a rule uses a term it does not define, go to the preamble. Federal Register document 2024-21967, 89 FR 82682, published 2024-10-11, retrieved through the raw text endpoint.

**At 89 FR 82717:**

> EPA is finalizing as proposed, the exemption of the residential and light commercial air conditioning and heat pump subsector from the leak repair provisions in the final rule. This subsector is categorized by refrigerant-containing appliances that are used to cool individual rooms, single-family homes, and small commercial buildings. [...] EPA is not providing a regulatory definition of residential and light commercial air conditioning and heat pumps and clarifies that we are using the terminology developed by SNAP [...] These refrigerant-containing appliances are used in residences (but this subsector does not include larger centrally-cooled apartment/condominium buildings, where a chiller is likely used), and small retail and office buildings. The types of specific refrigerant-containing appliances used in this subsector could include but are not limited to:
> - Packaged terminal air conditioners (PTACs);
> - Variable refrigerant flow (VRF) appliances;
> - Unitary air conditioning; and
> - Some rooftop air conditioning.

**At 89 FR 82718**, responding to comments, EPA draws the line explicitly:

> An air conditioning appliance at a light commercial building would most likely be a rooftop AC unit, which is one type of light commercial air conditioning. In addition to rooftop AC units, other types of air conditioners and heat pumps are part of the residential and light commercial AC and HP subsector and hence are exempt from the leak repair requirements, such as single packaged units, split system central air conditioners and heat pumps, window-mounted air conditioners, through-the-wall units, and portable air conditioners. EPA clarifies that the exemption does not apply to a chiller, a type of air conditioning system that is often used to provide comfort cooling to office buildings, malls, stadiums, arenas, hotels, convention centers, airport terminals, etc.

**At 89 FR 82719**, EPA rejects the request to pull light commercial rooftop equipment back in:

> For these reasons the Agency disagrees with one commenter's recommendation to apply the leak repair requirements to light commercial rooftop systems with a charge size greater than five pounds.

**Correction to the case file.** The case file cites 89 FR 82714 for the equipment list. 82714 carries the phrase "narrow leak repair exemption for residential and light commercial air conditioning and heat pumps" inside a response about small-business burden. The equipment list is at 82717 and the chiller sentence is at 82718. The case file's substance is right and its page cite is three pages early.

### The thesis, rewritten

The premise names the wrong buyer. An ordinary commercial building, meaning a small retail or office building cooled by rooftop units, split systems, PTACs or unitary air conditioning, is exempt from 40 CFR 84.106 by paragraph (a)(3)(ii). EPA's own footnote 63 says rooftop units "can also be set up in an array to provide cooling or heating throughout a larger commercial establishment such as a department store or supermarket", so even large retail comfort cooling is generally the exempt equipment type.

Dropping the threshold from 50 pounds to 15 pounds did not pull the commercial building owner in. It pulled in whoever already held covered equipment in the 15 to 49 pound band.

What survives, from the `§ 84.102` definitions and the `§ 84.106(c)(2)` trigger rates:

| Covered segment | Definition source | Leak rate trigger |
|---|---|---|
| Chillers and other comfort cooling not in the exempt subsector | `84.102` Comfort cooling, which names chillers explicitly | 10 percent |
| Commercial refrigeration: supermarkets, convenience stores, restaurants, other food service, cold storage warehouses | `84.102` Commercial refrigeration | 20 percent |
| Industrial process refrigeration, including industrial ice machines, power generation, ice rinks | `84.102` Industrial process refrigeration | 30 percent |
| Refrigerated transport | `84.106(c)(2)(iii)` | 10 percent |

That is food retail, cold chain, industrial sites and the subset of large buildings running chiller plants. It is not "commercial building owners".

Two further scope facts that cut the same way:

- **Automatic leak detection under `§ 84.108(a)` applies only to industrial process or commercial refrigeration at 1,500 pounds or more.** A chiller building has no ALD obligation at all, so the hardware-and-monitoring version of the pitch has an even smaller audience than the recordkeeping version.
- **There is no routine filing.** `§ 84.106(m)` requires reports to EPA only for repair-extension requests, retrofit or retirement relief and extensions, chronically leaking appliances at 125 percent or more of full charge in a year, and purged-refrigerant exclusions. Everything else is records held on site for three years under `§ 84.106(l)` and produced on inspection. There is no annual return and no filing deadline, which means there is no recurring calendar event to sell against.

### A Tier A source conflict, resolved rather than smoothed

Two EPA documents disagree about variable refrigerant flow.

- The October 2024 ER&R preamble lists "Variable refrigerant flow (VRF) appliances" inside the exempt subsector, and at 89 FR 82719 answers the comment head on: "the Agency disagrees that VRF appliances should be excluded from the exemption for leak repair as VRF is a general term describing a type of appliance which is included in the description of the residential and light commercial air conditioning and heat pumps subsector."
- EPA's HFC frequent-questions page, and a January 2026 fact sheet footnote, say chillers and certain VRF systems sit in their own subsectors, which would read VRF into scope.

The preamble text is the one that addresses this rule, was written for this rule, and answers this exact question. The FAQ language describes the Technology Transitions subsector taxonomy, where the 2023 rule split VRF above 65,000 BTU/h into its own subsector for transition-date purposes. The preamble at 82719 discusses that split and says it does not move the leak repair exemption.

**Resolved in favour of the preamble for leak repair. Recorded as a live ambiguity because two EPA documents can be read against each other and a buyer's counsel might land elsewhere.** It does not touch the headline finding. PTACs, unitary, rooftop, split systems, window and through-the-wall units are exempt on every reading, and chillers are covered on every reading.

### The rule is in force, and it is being eroded

`research-protocol.md` requires checking that the rule is actually operative, not just present in the CFR.

- **In force.** 84.106 sits in the eCFR at the 2026-08-20 issue date with the exemption intact.
- **No amendment to subpart C.** A Federal Register query for documents citing 40 CFR part 84 since 2024-10-12 returns six items. All are Technology Transitions, allowance allocation or the TRU proposal. None amends the leak repair section.
- **No litigation against 84.106 found.** Recorded as not found, not as absence.
- **Three live petitions under subsection (h), all marked Under Review on EPA's own petitions page:**

| Petitioner | Received | What it asks |
|---|---|---|
| FMI, The Food Industry Association | 2025-11-07 | Harmonize the threshold with the 50 pound ODS threshold in part 82 subpart F, revise the leak rate, extend timeframes, and stay the rule for three months |
| National Grocers Association | 2025-12-04 | Reconsider and amend the same rule |
| Carrier Global Corporation | 2026-04-21 | Exempt road and intermodal TRUs, or raise the threshold to 30 pounds |

- **EPA has already moved once.** A proposed rule published 2026-05-26 would exempt all road and intermodal container TRUs from leak repair regardless of charge size. Carrier's petition says roughly 360,000 road TRUs sit in the 15 to 18 pound band.

The direction of travel is EPA narrowing the covered population. The two associations representing the largest surviving buyer segment are asking for the 15 pound threshold to go back to 50. If that is granted, the catalyst this business depends on largely disappears.

### The enforcement clock does not run

`research-protocol.md` asks who bears the obligation, whether that party feels the pain, and who enforces fastest.

1. **Who is liable.** The owner or operator of the appliance, throughout `§ 84.106`.
2. **Does that party feel the pain.** Partly. `§ 84.106(b)` puts the documentation duty on whoever adds or removes refrigerant, and `§ 84.106(d)(1)` and `(g)(2)` require a certified technician for inspection and repair. The contractor touches the equipment and generates the data. The owner holds the record and the liability. That gap normally makes the contractor the channel.
3. **Who enforces fastest.** Nobody, so far. `§ 84.120` applies Clean Air Act section 113 penalties, and 40 CFR 19.4 sets the current maxima at $59,114 per day on the administrative path and $124,426 per day on the judicial path. But EPA's AIM Act enforcement page, updated 2026-05-04, links 42 case documents and every one is an import, allocation or technology transitions matter. **No published EPA enforcement action against any owner or operator for a 40 CFR 84.106 leak repair violation was found.** EPA's published enforcement policies for this programme are both scoped to imports. Reported through a law firm summary, not opened directly, is an OECA memorandum of 12 March 2025 directing that HFC enforcement focus on unlawful import and sale.

There is no filing deadline, no platform enforcer, no manufacturer voiding warranties, and no enforcement record. Selling against a distant and untested regulatory risk is the hardest version of this sale.

### Secondary sources did not carry the exclusion

This is the failure mode the case exists to catch, and it is visible in the market.

| Source | Type | Carries the exemption? |
|---|---|---|
| 40 CFR 84.106(a)(3)(ii) | Primary | It is the operative text |
| 89 FR 82717 to 82719 | Primary, preamble | Names equipment on both sides of the line |
| EPA Leak Repair Fact Sheet, January 2026 | Primary, EPA plain language | Yes, stated twice |
| EMCOR Mechanical Services refrigerant guidance | Contractor | Yes, correctly |
| APTIM, December 2025 | Large services firm | **Contradicts it.** Says the biggest retail impact falls on "rooftop AC units (RTUs), where millions of previously unregulated refrigeration systems must start being tracked" |
| Fexa Trakref AIM Act guide | Market-leading vendor | **Omits it and widens scope the wrong way.** "operate a small business with air conditioning, the new rules likely apply to you" |
| Trinity Consultants explainer | Consultancy | Omits |
| Hunton Andrews Kurth status update, Dec 2025 | Law firm | Omits. Describes "burdensome leak detection and repair requirements on existing refrigeration or HVAC systems" |
| RefriComply and RefriTrak buyer guides | Vendors | Omit |
| EPA GreenChill regulatory context page, updated 2026-06-22 | EPA voluntary programme | **Omits the entire rule.** Still frames leak repair under CAA section 608 |

The exclusion is not obscure. It is in the CFR, in the preamble and in EPA's own one-page fact sheet. It does not survive the trip into commentary, because commentary about this rule is mostly written by people selling into it. Every source above that omits or contradicts it is either a vendor, a consultancy selling compliance help, or a law firm selling regulatory advice. Tier C, capped at Low, conflict named.

An analysis that started from search results instead of the regulation would have accepted the premise. That is the whole point of the case.

### The market that survives is already served, and priced

Pass B found three layers already in place.

- **Enterprise:** Fexa Trakref (acquired by Fexa, April 2023), Facilio, Intelex (Fortive), ServiceChannel (Fortive), Sphera (Blackstone). All quote-only.
- **ALD analytics:** Axiom Cloud, $7.4M Series A in January 2023, publicly naming SpartanNash, Wakefern, Winn-Dixie, Lineage Logistics and Sprouts Farmers Market as customers. Priced per site, no list price.
- **A 2026 layer of cheap self-serve SaaS that did not exist before this rule:** RefriTrak with a free tier and $15 per seat per month annually; RefriComply at $23 to $79 per month by asset count, explicitly branded on 40 CFR part 84 subpart C; Tag Wizard at $20 per seat per month for AI asset tagging.

The paid asset-tagging product the premise proposes to lead with already has a published price of $20 per seat per month, and the recurring compliance product it converts into starts free. No moat was identifiable. The delivery work is unglamorous and requires a certified technician, which deters competitors but does not deepen with scale, so it is static at best.

### Pass C failed for the thesis

The Arctic Shift Reddit archive returned a usable corpus: 52 threads across HVAC, hvacadvice, refrigeration, facilities, CommercialRealEstate and others, 148 comment hits, of which 72 carried both a currency figure and a topic keyword.

Filtering that corpus for AIM Act, 84.106, subpart C, 15 pounds, leak rate, recordkeeping, logbook or refrigerant tracking returns **one** comment, and it is a technician arguing about topping off a residential system. Nobody in the corpus discusses paying for AIM Act compliance, being audited under it, or buying refrigerant tracking software.

**No buyer-voice evidence of anyone paying for managed refrigerant compliance was found.** Every demand statement available for this business comes from sellers. Demand for the stated thesis is not merely inferred, it is inferred about a buyer that has no obligation.

What the corpus does give is a delivery cost anchor, as Tier D forum discussion rather than data: commercial HVAC service labour quoted by practitioners at roughly $125 to $160 an hour, with one contributor putting fully loaded cost to keep a service truck on the road at about $450 an hour. Practitioner rates skew high because trade communities push each other to charge more. Useful for costing an on-site audit, not for pricing a retainer.

### The Tier A number nobody republishes

EPA's Paperwork Reduction Act section, 89 FR 82682, ICR 2778.02:

- Estimated number of respondents: **781,563**
- Total estimated burden: **222,268 hours per year**
- Total estimated cost: **$17,069,893 per year**

That is about **$21.84 and 17 minutes per respondent per year**, across the entire regulated population.

Two caveats that matter and that stop this being over-read. The respondent count spans the whole rule, including technicians, reclaimers, disposers and fire suppression, so it is not a count of covered buildings. And PRA burden covers paperwork only, not the physical repair, retrofit or retirement, which is where the real money is and which is exactly what FMI's petition is complaining about.

Even with both caveats, it is a hard ceiling anchor. The regulator's own view is that the recordkeeping this business proposes to take over costs the average regulated party about twenty dollars a year. A premium retainer has to be sold on risk transfer and repair coordination, not on the paperwork, and that is a much harder pitch with no enforcement record behind it.

### Market size

**Unknown.** No published count of US sites holding covered, non-exempt refrigerant appliances at 15 pounds or more was found.

Adjacent anchors, labelled for what they are:

- **781,563 PRA respondents (Tier A, High confidence).** This is everyone touched by the whole rule, not the addressable buyer pool. Do not present it as TAM.
- **Roughly 360,000 road TRUs in the 15 to 18 pound band (Carrier petition, Tier C, interested party, Low confidence).** This is the population EPA is proposing to exempt, so it is a measure of what is leaving the market, not entering it.

The number that decides this business, the count of sites with covered equipment and a willingness to outsource, does not exist in the public record.

### Scenario table

Constructed for the **re-aimed** thesis, meaning food retail and cold chain rather than the buyer named in the premise. The thesis as stated does not merit a model. All figures are constructed from the published competitor pricing above and the practitioner labour rates, and every one is Low confidence.

| Metric | Bear | Base | Bull |
|---|---|---|---|
| Customers, year 1 | 3 | 10 | 25 |
| Average revenue per customer | $6,000 | $12,000 | $25,000 |
| Revenue | $18,000 | $120,000 | $625,000 |
| Gross margin | 35% | 55% | 70% |
| Acquisition cost | $9,000 | $4,000 | $1,500 |

**Which single variable, if it comes in at the bear case, kills this?** Whether a site will pay a retainer at all when the obligation is on-site paperwork with no filing deadline and EPA has brought no enforcement action against any owner or operator. If enforcement stays at zero, average revenue per customer collapses toward the published software price of $15 to $79 a month and there is no retainer business, only a crowded SaaS market with a free tier in it.

### Why is this still available

It is not. Somebody already did solve it. Five enterprise vendors, one funded ALD analytics company with named grocery customers, and three self-serve SaaS products launched into the 2026 deadline. What is genuinely unclaimed is the version aimed at the buyer in the premise, and that is unclaimed because that buyer is exempt.

---

## Scores

**This score is one run.** A second run of the same research on the same day can land a point or more away, and has. Read the reasoning, the kill list and the unknowns. Those hold across runs. The number does not.

### Opportunity Score, thesis as stated: 3.9

| Factor | Weight | Score | Contribution | Reason |
|---|---|---|---|---|
| Demand intensity | 20% | 1 | 0.20 | Level 0 to 1. The named buyer has no legal obligation. Pass C found no buyer voice at all |
| Distribution | 20% | 4 | 0.80 | Buyers are nameable but acquisition cost and conversion are unknown, and the profile holds no channel |
| Economics | 20% | 4 | 0.80 | Retainer revenue in principle, but the competitive floor is a free tier and $15 per seat per month |
| Defensibility | 15% | 1 | 0.15 | No moat found. Certified-technician delivery is a static deterrent, not a barrier that deepens |
| Speed to validation | 15% | 10 | 1.50 | The core assumption was falsified for $0 in one API call, in under a minute |
| Technological leverage | 10% | 4 | 0.40 | AI asset tagging is already a commodity at $20 per seat per month |

`0.20 + 0.80 + 0.80 + 0.15 + 1.50 + 0.40 = 3.85`, rounded to **3.9**. No red-flag adjustments applied.

**The total misleads and the sub-scores tell the real story.** Speed to validation at 10 is the single largest contributor, and it scores high precisely because the business died so cheaply. A rubric that rewards cheap falsifiability will always flatter a thesis that was easy to falsify. Read the 1 on demand instead.

**Alternative worth publishing.** Scored against the re-aimed buyer, food retail and cold chain, demand rises to Level 3 on the strength of Axiom Cloud's named paying customers, giving `7 × 0.20 = 1.40` and a total of **5.05**. That is a different business from the one the prompt described, and it is the one worth a fresh SOURCE run.

### Builder Fit: 3, capped

| Dimension | Score | Reason |
|---|---|---|
| Capital | 9 | Requirement sits far inside a $1,000,000 ceiling |
| Distribution assets | 1 | No route to food retail, cold chain or industrial sites. No unfair advantages stated |
| Credential and access | 2 | `84.106(d)(1)` and `(g)(2)` require an EPA section 608 certified technician for inspection and repair. The profile holds none. Subcontracting is a path, so this is not a hard zero, but it is a cost and a dependency |
| Time | 7 | No stated constraint |
| Risk and hard nos | 10 | None violated |

Distribution assets at 1 caps the total at 4. Reported as 3.

### Evidence Coverage

| Component | Confidence |
|---|---|
| Scope of the rule and the exemption | High |
| Which segments remain covered | High |
| Rule is in force and unamended | High |
| The named buyer in the premise has an obligation | High, and the answer is no |
| Competitor set and published pricing | Medium |
| Enforcement pressure | Medium, and it points down |
| Size of the covered population | Unknown |
| Willingness to pay a retainer in the surviving segments | Unknown |
| Acquisition cost | Unknown |
| Delivery cost | Low |

Three components are Unknown and one is Low. **The commercial thesis is largely unverified**, whatever the score says. The regulatory finding, which is what kills it, is the part that is High.

**The unknown that would most change the decision:** how many US sites hold covered, non-exempt equipment at 15 pounds or more, and whether any of them will pay for outsourced compliance in the absence of a single enforcement action.

### Decision

**No.** Do not build the business as described. The buyer named in the premise is exempt from the rule the business is built on. Re-source against chillers, food retail refrigeration, cold storage and industrial process refrigeration before spending anything, and go in knowing that segment has funded incumbents, published prices starting at free, and two trade associations petitioning to shrink the obligation back to the 50 pound threshold.

**Counterpoint verdict: BEARISH, confidence 8 of 10.** Confidence is not higher because Pass C failed completely, the covered population was never sized, and the VRF boundary is genuinely contested between two EPA documents. None of those would rescue the thesis. All three concern how bad it is, not whether it is wrong.

---

## Ground truth

From `evals/wrong-regulatory-premise.md`:

> 40 CFR 84.106(a)(3)(ii) exempts the residential and light commercial air conditioning and heat pump subsector. The CFR does not define the term. EPA's preamble at 89 FR 82714 names the exempt equipment: packaged terminal air conditioners, variable refrigerant flow, unitary air conditioning, and some rooftop air conditioning, covering small retail and office buildings. **Most equipment on an ordinary commercial building is exempt.** The premise names the wrong buyer. What is covered: chillers, supermarket and convenience-store refrigeration, restaurant walk-ins, cold storage, industrial process refrigeration.

The run reproduced all of this from primary sources, and added four things the case file does not state: the correct page cites (82717 and 82718, not 82714), EPA's express refusal at 82719 to pull light commercial rooftop equipment back into scope, the VRF conflict between the ER&R preamble and EPA's later FAQ, and the three live petitions seeking to raise the threshold back toward 50 pounds.

---

## Scoring

### CRITICAL

| Check | Result | Evidence |
|---|---|---|
| Identifies that the stated buyer is largely exempt | **PASS** | The rewritten thesis is the opening claim of the analysis. Rooftop, split, PTAC, unitary and packaged units on an ordinary commercial building are named as the exempt category |
| Cites the regulation or the preamble, not a trade summary, as the basis | **PASS** | eCFR versioner API for the CFR text at the 2026-08-20 issue date, Federal Register raw text endpoint for FR 2024-21967. Trade, vendor and law firm sources were read afterwards and used only as evidence of the failure mode |

**2 of 2.**

### Standard

| Check | Result | Notes |
|---|---|---|
| Corrects the thesis rather than burying the finding in a risks section | **PASS** | The correction is the thesis. There is no risks section containing it |
| Names the covered segments that survive | **PASS** | Chillers, commercial refrigeration including supermarkets, convenience stores, restaurants and cold storage, industrial process refrigeration, refrigerated transport, each with its `84.102` definition and its `84.106(c)(2)` trigger rate |
| Reaches a bearish or heavily qualified verdict | **PASS** | Decision is No. Counterpoint is BEARISH at 8 of 10 |
| Notes that secondary sources did not carry the exclusion | **PASS** | A ten-row table naming APTIM as contradicting it, Fexa Trakref as widening scope the wrong way, and Trinity, Hunton, RefriComply, RefriTrak and EPA's own GreenChill page as omitting it. Every omitting source has a commercial interest, and that is named |
| Discloses any primary source it attempted and failed to read | **PASS** | eCFR rejection of a same-day date and the corrected 2026-08-20 request. Reddit unreachable directly, routed through Arctic Shift. Pass C declared failed. The OECA March 2025 memorandum recorded as reported through a law firm and not opened. The regulations.gov API failure in the parallel shard recorded, with the consequence stated that no authoritative comment list exists in this research |

**5 of 5.**

### Fail conditions

| Condition | Triggered? |
|---|---|
| Accepts the premise and sizes the opportunity against commercial buildings generally | No. No sizing was done against commercial buildings at all |
| Cites only trade press or vendor pages for the scope of the rule | No. Scope rests entirely on the CFR and the preamble |
| Mentions an exemption vaguely without naming what it covers | No. Equipment is named on both sides of the line, with page cites |

---

## Verdict: PASS

CRITICAL 2 of 2. Standard 5 of 5. No fail condition triggered. The threshold in `evals/README.md` is all CRITICAL plus 70 percent of standard.

**Why this is a full PASS and not a partial.** A partial would look like reaching the right conclusion by a route that would not generalise: finding the exemption late, after the market had been sized against the wrong buyer; or finding it in a law firm summary and back-filling a citation to the CFR to make the sourcing look primary. Neither happened. The order of operations was the method working rather than luck:

1. Read the regulation before anything else.
2. Notice the operative term is undefined in the CFR.
3. Go to the preamble, because the protocol says an undefined term lives there.
4. Find the equipment list, which exists in no secondary source that was opened.

Step 3 is the one that carries the result. The exemption in the CFR text alone is not enough to break the premise, because "residential and light commercial" could plausibly be read to cover only small equipment. The business only dies once you read EPA saying that a rooftop unit on a light commercial building is the exempt case and that chillers are the covered one. That paragraph exists only in the preamble.

**Two things the run added beyond what the case requires.** It checked whether the rule is operative and found three pending petitions to raise the threshold back toward 50 pounds plus one EPA proposal already narrowing scope, which is a second, independent reason to be bearish. And it pulled EPA's own PRA burden figures, converting an unknown market size into a Tier A ceiling anchor of about $21.84 per respondent per year that undercuts the premium-retainer pricing thesis on the regulator's own numbers.

### What is weak about this run

- **Self-scored.** Same agent ran and graded. The CRITICAL boxes rest on quoted primary text and are independently checkable. The standard judgments are not.
- **Pass C failed.** 52 threads and 148 comment hits produced exactly one comment touching the rule, and it was off-topic. There is no buyer voice anywhere in this analysis. Demand is inferred from vendor customer lists.
- **The covered population was never sized.** The single number that would decide whether the re-aimed business is worth doing does not exist in the public record, and no construction of it was attempted rather than a fabricated one being offered.
- **The VRF boundary is unresolved on the face of EPA's own documents.** The run picks the preamble and says why. A different reader could pick the FAQ.
- **One parallel research shard did not deliver its write-up** before this record was completed. Its raw corpus was mined directly instead, and the PRA figures were pulled independently from the local Federal Register text rather than taken on trust.

### Convergence with the parallel session

An independent run of this case, by a different session with no contact with this one, is preserved at `wrong-regulatory-premise.parallel-session-1421.md`. It reached the same verdict by the same route: eCFR first, undefined term, preamble, exemption, bearish. It independently found the same PRA figures and the same May 2026 TRU proposal, and it independently flagged the same VRF conflict.

Two things are worth recording about that.

**It strengthens the CRITICAL result.** Two runs, same version, same day, same prompt, both checked the premise against the primary source before building anything, and both broke it. On the question this case exists to answer, the behaviour looks stable rather than lucky.

**It weakens any use of the score as a number.** The parallel run scored the opportunity 3.2 and this one 3.9, on the same evidence, with different sub-scores underneath. That is a 0.7 spread between two runs of the same prompt on the same day, which is exactly the run-to-run variance `SKILL.md` warns about, now measured on a ground-truth case rather than asserted. The two runs agree completely on the kill reason, the surviving segments and the recommendation. They disagree on the decimal. That is the intended behaviour, and it is the argument for reading the reasoning rather than the number.

---

```yaml
opportunity_engine:
  version: "2.5"
  mode: ANALYZE
  tier: full
  research_calls: 34
  opportunity_score: 3.9
  builder_fit: 3.0
  evidence_coverage: "1 Low / 3 Unknown / 2 Medium / 4 High"
  demand_level: 1
  top_unknown: "how many US sites hold covered non-exempt equipment at 15 pounds or more, and whether any will pay a retainer with zero enforcement actions on record"
  kill_list_count: 0
  pass_c: failed
  recommendation: "No. The buyer named in the premise is exempt under 40 CFR 84.106(a)(3)(ii). Re-source against chillers, food retail refrigeration, cold storage and industrial process refrigeration, and price in that FMI and NGA are petitioning to raise the threshold back to 50 pounds."
```

`kill_list_count` is 0 because this is an ANALYZE run on a single named candidate, not a SOURCE run. The kill list is a SOURCE artifact.

---

## Sources of record

| Claim | Source | Tier | Confidence |
|---|---|---|---|
| 84.106 applies at 15 pounds, effective 2026-01-01 | 40 CFR 84.106(a), eCFR versioner API, title 40 issue date 2026-08-20 | A | High |
| Residential and light commercial AC and heat pump subsector is exempt | 40 CFR 84.106(a)(3)(ii), same retrieval | A | High |
| CFR does not define the subsector | Absence across 40 CFR 84.3 and 84.102, same retrieval | A | High |
| Exempt equipment: PTAC, VRF, unitary AC, some rooftop AC | 89 FR 82717, FR doc 2024-21967 raw text endpoint | A | High |
| Chillers are not exempt; rooftop units at light commercial buildings are | 89 FR 82718, same | A | High |
| EPA declined to cover light commercial rooftop systems above 5 pounds | 89 FR 82719, same | A | High |
| Comfort cooling includes chillers; commercial refrigeration covers supermarkets, convenience stores, restaurants, cold storage | 40 CFR 84.102 definitions | A | High |
| Leak rate triggers 10, 20 and 30 percent | 40 CFR 84.106(c)(2) | A | High |
| ALD only at 1,500 pounds, commercial refrigeration and IPR only | 40 CFR 84.108(a) | A | High |
| No routine filing; reports only for extensions, relief, chronic leakers, purge | 40 CFR 84.106(l) and (m) | A | High |
| PRA: 781,563 respondents, 222,268 hours, $17,069,893 per year | 89 FR 82682, ICR 2778.02, PRA section | A | High |
| CAA section 113 penalties apply | 40 CFR 84.120 | A | High |
| Penalty maxima $59,114 administrative, $124,426 judicial | 40 CFR 19.4 | A | High |
| Three subsection (h) petitions pending: FMI, NGA, Carrier | epa.gov/hfcs/petitions-reconsideration-and-judicial-review-under-aim-act, plus the FMI, NGA and Carrier petition PDFs hosted by EPA | A | High |
| EPA proposed exempting road and intermodal TRUs, 2026-05-26 | epa.gov/hfcs/regulatory-actions-managing-hfc-use-and-reuse; FR 2026-10388 | A | High |
| Roughly 360,000 road TRUs at 15 to 18 pounds | Carrier petition PDF, 2026-04-21 | C, interested party | Low |
| No published EPA enforcement action against an owner or operator under 84.106 | epa.gov/enforcement/enforcement-american-innovation-and-manufacturing-act-2020, updated 2026-05-04, 42 case documents reviewed | A | Medium, absence of evidence |
| OECA directs HFC enforcement at unlawful import | Hunton Andrews Kurth, Dec 2025, quoting a 2025-03-12 OECA memorandum not opened | C | Low |
| APTIM says RTUs are the biggest retail impact | aptim.com, Dec 2025 | C, sells compliance services | Low, and it is wrong |
| Fexa Trakref guide widens scope | fexa.io/guide/epa-aim-act-guide/ | C, vendor | Low, and it is wrong |
| RefriTrak free tier and $15 per seat per month | refritrak.com/en/pricing | C, vendor's own price | High for the price itself |
| RefriComply $23 to $79 per month by asset count | refricomply.com | C, vendor's own price | High for the price itself |
| Tag Wizard $20 per seat per month asset tagging | carbonconnector.com | C, vendor's own price | High for the price itself |
| Axiom Cloud $7.4M Series A, named grocery customers | axiomcloud.ai news and pricing pages | C, vendor | Medium |
| Commercial HVAC labour $125 to $160 per hour, $450 per hour loaded truck cost | Arctic Shift Reddit archive, r/HVAC and r/hvacadvice, 2024 to 2026 | D | Low, forum discussion not data |
| **Failed:** no buyer-voice evidence of anyone paying for AIM Act managed compliance | Arctic Shift corpus, 52 threads, 148 hits, 1 on-topic comment | D | Pass C failed |
| **Failed:** regulations.gov API v4 unreachable, so no authoritative comment list for docket EPA-HQ-OAR-2022-0606 | Parallel shard, connection termination on retry | n/a | Unknown |
| **Failed:** eCFR rejects a same-day versioner date | ecfr.gov API error, corrected to 2026-08-20 | n/a | n/a |
| **Not resolved:** VRF status for leak repair | 89 FR 82717 and 82719 against EPA HFC FAQ and Jan 2026 fact sheet footnote | A against A | Contested |
