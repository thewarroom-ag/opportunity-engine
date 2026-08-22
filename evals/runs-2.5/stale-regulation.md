# Eval run: stale-regulation

**Date:** 22 August 2026
**Skill version tested:** opportunity-engine 2.5 (read from `VERSION.md`; installed copy at `~/.claude/skills/opportunity-engine` verified byte-identical to the repo for `SKILL.md` and all seven files in `references/`)
**Model:** Claude Opus 5
**Mode:** ANALYZE, Full tier
**Control arm:** not run. See Limitations.

---

## Setup used

From the case file, not from `builder-profile.md`:

```
Capital ceiling: $150,000
Time to first revenue: 6 months
Geography: US only
Interest areas: recurring revenue, compliance services
Unfair advantages: none stated
```

## Prompt given

> There is a FinCEN rule requiring reporting on non-financed residential real estate transfers, with the filing duty on the settlement agent. Analyze a compliance service selling to title and settlement agents who now have to file.

---

# Part 1: What the run produced

The full ANALYZE output is reproduced below, so that the scoring can be checked against it.

---

## Document 1: Opportunity Analysis

### Thesis

There is no filing duty. The rule the prompt describes was vacated in its entirety on 19 March 2026 by the US District Court for the Eastern District of Texas in *Flowers Title Companies, LLC v. Bessent*, eighteen days after reporting began. FinCEN's own website says reporting persons are not required to file and are not subject to liability while the order stands. The premise of the business, that settlement agents "now have to file", is false as of today. What is left is a bet on a pending Fifth Circuit appeal, not a compliance service with a customer.

### Catalyst, and which way it runs

| Date | Event | Source |
|---|---|---|
| 29 Aug 2024 | Final rule published, "Anti-Money Laundering Regulations for Residential Real Estate Transfers", 31 CFR 1031.320 | Federal Register 2024-19198 (Tier A, High) |
| 1 Dec 2025 | Rule effective | Federal Register 2024-19198 (Tier A, High) |
| 1 Mar 2026 | Reporting duty begins for closings on or after this date | FinCEN RRE pages (Tier A, High) |
| **19 Mar 2026** | **US District Court, E.D. Tex., vacates the rule in its entirety in *Flowers Title Companies, LLC v. Bessent***, holding FinCEN exceeded its authority under the Bank Secrecy Act, in violation of the APA | FinCEN alert banner and FAQ (Tier A, High); Pacific Legal Foundation case page (Tier C, Medium) |
| 11 May 2026 | FinCEN, through DOJ, appeals to the Fifth Circuit | Law firm client alerts (Tier C, Medium). I did not open the Fifth Circuit docket |
| 18 May 2026 | FinCEN issues FAQs 1 to 3 confirming no filing duty and no retroactive filing if the order is overturned | FinCEN RRE FAQ, dated on its face (Tier A, High) |
| 22 Aug 2026 | No reinstatement found. No removal rule, no stay of the vacatur, no replacement rule in the Federal Register | Federal Register API, all 37 FinCEN documents since 1 Jan 2025 reviewed (Tier A, High) |

**The catalyst runs against the business.** This is not a regulation creating demand. It is a regulation whose demand a court removed, and the removal is the most recent event in the sequence.

FinCEN's exact words, from `fincen.gov/rre` and `fincen.gov/rre-faqs`:

> "While the court's order remains in force, reporting persons are not required to file Real Estate Reports with FinCEN and are not subject to liability if they fail to do so."

Two other district courts rejected challenges to the same rule. Only the Flowers court vacated it, and vacatur under the APA is not limited to the parties, so the rule is dead nationwide while the order stands.

### The trap this case sets, and why reading the CFR would not have caught it

31 CFR 1031.320 is still on the books. Vacatur does not delete regulatory text. An agent that pulled the part from the eCFR versioner API would have found the section present, in full, sourced to its Federal Register notice, with no amendment noted, and would have concluded the rule was live. The Federal Register also carries nothing: no removal rule, no stay, no notice of any kind about the vacatur. **The only place the status appears is the agency's own rule page.** That is the check that decided this analysis.

### Market: what the rule would have been worth, and what it is worth now

Current addressable spend for a filing service: **zero**. There is no filing obligation to serve.

For the counterfactual where the Fifth Circuit reinstates the rule, FinCEN's own Regulatory Impact Analysis gives Tier A numbers that nobody republishes:

| Figure | Value | Source | Confidence |
|---|---|---|---|
| Reportable transfers per year, upper bound | 800,000 to 850,000 | Final rule RIA, 89 FR 70280 to 70290 | High, but it is an agency estimate for a rule that ran 18 days |
| Total annual reporting and recordkeeping burden | 4,604,167 hours | Final rule PRA section, OMB control 1506-0080 | High |
| Total annual reporting and recordkeeping cost, all affected parties | $630,976,662 | Same | High |
| Title and settlement agents, upper bound | ~6,300 firms | Final rule RFA section, citing Census SUSB, NAICS 541191 | High |
| Direct title insurance carriers | ~800 firms | Same, NAICS 524127 | High |
| All potentially affected small entities | ~160,800 firms across five NAICS codes, including 15,700 law offices and 18,000 other real estate firms | Same | High |

Dividing $630,976,662 by 850,000 gives about **$742 per filing** in total compliance cost. That figure is **constructed**, and it is mostly internal staff wages, not money that would flow to a third-party vendor. Do not read it as a price point.

**Beachhead: unknown, and it is unknown because it is currently empty.** The reachable pool is the roughly 6,300 title and settlement offices, but only in a world where the appeal succeeds. Naming a beachhead today means naming buyers of a product that solves a legal duty nobody has.

**36-month obtainable: unknown.** It is the product of a court outcome I cannot handicap and a price point I could not verify.

### Competitive landscape

Topology: **fragmented on the surface, platform-controlled underneath.** The buyers are many and small. The route to them runs through four or five title production systems that already own the workflow.

| Player | What it did | Position |
|---|---|---|
| Qualia | Launched an RRE compliance solution Oct 2025, built into its cloud title production system, and reported as **included at no additional charge** | Owns the workflow. Gave the feature away |
| SoftPro | Built RRE data collection, then direct e-filing to FinCEN through the SoftPro 360 vendor portal | Owns the workflow |
| RRE Report / fincenreport.com | Point solutions selling evaluation and filing, with live integrations into Qualia and SoftPro | Independent, but reaches buyers through the same two platforms |
| RamQuest, Resware, Settlor | Other title production systems in the same category | Not verified as shipping RRE features |

Source tier: all of the above is vendor material or trade press about vendors. **Tier C, Low to Medium confidence, and every one of these sources has a commercial interest in the rule mattering.** Named in the verification table.

**This is a second, independent reason the opportunity fails, and it would hold even if the rule came back.** The incumbent that owns the workflow bundled the feature at no extra charge before the rule ever took effect. A standalone compliance service arriving now would be selling, to a buyer with no legal duty, a feature their existing software already includes for free.

### Where the gap is

There is no gap. There is a vacated rule, a pending appeal, and two title software companies that shipped the feature and one of which does not charge for it.

### Why is this still available

It is not available. It was taken, and then it was cancelled.

The honest answer to "why has nobody taken this" is that several people did. Qualia and SoftPro built it into their platforms during 2025. Point vendors built filing services on top of them. Then on 19 March 2026 a court removed the reason to buy any of it. The people who moved fastest on this thesis are the ones holding the loss.

### Regulatory: the three questions

1. **Who bears the legal obligation?** Under the vacated rule, the reporting person, determined by a cascade through the closing roles: settlement agent, then title insurance underwriter, then filer of the deed, and so on, unless overridden by a designation agreement. **Today: nobody.**
2. **Is that the same party who feels the pain?** Yes, and the case file's own method flags this as the bad case. The settlement agent both files and pays. No third party was pushing them to buy, so the only pressure was the regulator's, and the regulator has been enjoined from applying it.
3. **Who enforces fastest?** Nobody. FinCEN has stated in writing that it will not impose liability while the order stands, and FAQ 3 confirms there will be no retroactive filing even if the order is overturned. **The fastest enforcer is a deterrent here, not a trigger.** The clearest signal in the market is the agency saying, on its own website, do not bother.

Parallel regimes checked. The residential real estate Geographic Targeting Orders, which imposed a narrower version of the same reporting on title insurance companies in named counties, **lapsed when the rule took effect on 1 March 2026 and have not been reissued.** So neither regime is currently operative. The New York LLC Transparency Act took effect 1 Jan 2026, but it applies to LLCs filing about themselves, not to settlement agents filing about transfers. It is a different buyer and a different product.

### Risks

Only two matter, and the first has already happened.

| Risk | Severity | Status |
|---|---|---|
| The rule is not in force | Fatal | **Already occurred, 19 March 2026** |
| Even if reinstated, the workflow owner bundles the feature free | Fatal to a standalone vendor | Already occurred, Qualia, Oct 2025 |

Padding this to five would be dishonest. There are two, and both have fired.

### What got filtered out

- **Selling readiness or advisory rather than filing.** Killed. ALTA's chief executive has advised members that the cautious approach is to keep collecting information as if they will need to report. That is free advice from their trade body, and it is the whole product.
- **Selling into the GTO regime instead.** Killed. The GTOs lapsed on 28 February 2026 and have not been reissued.
- **Selling into the New York LLC Transparency Act.** Killed on buyer mismatch. Different buyer, different filing, and the prompt's buyer is not in it.

### Score

> This score is one run. A second run of the same research on the same day can land a point or more away, and has. Read the reasoning, the kill list and the unknowns. Those hold across runs. The number does not.

| Factor | Weight | Score | Contribution | Why |
|---|---|---|---|---|
| Demand intensity | 20% | 2 | 0.40 | Level 1. Some agents keep collecting data voluntarily on their trade body's advice. Nobody has a duty and nobody faces liability. There was real Level 3 spend from Dec 2025 to Mar 2026, and it was extinguished |
| Distribution | 20% | 4 | 0.80 | Buyers are nameable and countable, about 6,300 firms. The route runs through title production systems the builder does not control |
| Economics | 20% | 1 | 0.20 | No repeat purchase, because there is no purchase |
| Defensibility | 15% | 1 | 0.15 | Moat type: **None**. The form is published, the workflow lock-in belongs to Qualia and SoftPro |
| Speed to validation | 15% | 10 | 1.50 | The core assumption is falsifiable in under an hour for nothing, by reading one page on fincen.gov. See the note below |
| Technological leverage | 10% | 4 | 0.40 | Form validation and e-filing. An efficiency gain available to every competitor and to the customer |
| Subtotal | | | **3.45** | |
| Single-point dependency, -1 | | | **-1.00** | One court order is the entire demand source. Already fired |
| **Opportunity Score** | | | **2.45** | |

**The total is misleading and I am reporting it anyway.** 1.50 of the 2.45 comes from speed to validation, which scores 10 precisely because the thesis was cheap to disprove and has been disproved. A reader skimming for the number would see 2.45 and miss that the business does not exist.

**Alternative scoring, published as required.** If speed to validation is scored against the assumption that actually carries the business, which is whether the Fifth Circuit reinstates the rule, it is a 1, not a 10. Nobody can cheaply falsify an appellate outcome. That gives **1.10**. I used 10 and 2.45 because the rubric asks about the core assumption of the thesis as stated, and the thesis as stated was falsified in an hour. I would not argue against 1.10, and 1.10 is the number that better matches the judgment.

**Builder Fit: 3 (capped at 4).** Distribution assets score 1: the profile states no unfair advantages, so there is no route to title and settlement agents and no standing in the industry. Capital fits inside $150,000 with room. Time fits. The interest areas, recurring revenue and compliance services, match the shape of the business well. None of that matters, because the dimension at 1 caps the total and the opportunity is not there.

**Evidence Coverage**

| Component | Confidence |
|---|---|
| The rule was vacated and is not in force today | **High**. FinCEN's own site, two pages, plus the Federal Register showing no reinstatement |
| Court, case name, and date | **High**. FinCEN names the court and the date. The case name is corroborated by the plaintiff's counsel and by multiple law firm alerts |
| Appeal is pending in the Fifth Circuit | **Medium**. FinCEN confirms an appeal exists. The 11 May 2026 filing date and the Fifth Circuit venue come from Tier C secondary sources. I did not open the appellate docket |
| Regulated population size | **High**. Final rule RFA and PRA sections |
| Filing volume if reinstated | **High** as an agency estimate, but it is an upper bound for a rule that operated 18 days |
| Competitor set and their offerings | **Medium**. All vendor or trade press, all commercially interested |
| What title agents actually pay for filing software | **Unknown**. Not found |
| Acquisition cost | **Unknown** |
| Whether reinstatement would restore willingness to pay | **Unknown**. It is the whole question and it is unanswerable today |

Three components are Unknown, so the commercial half of this thesis is largely unverified. The decisive fact is not. **The single unknown that would most change the decision: the Fifth Circuit's ruling.** Nothing else moves this.

### Verification table

| Claim | Source | Tier | Confidence |
|---|---|---|---|
| Rule vacated 19 Mar 2026, E.D. Tex., *Flowers Title Companies, LLC v. Bessent* | fincen.gov/rre and fincen.gov/rre-faqs, alert banner and FAQ 1, issued 18 May 2026 | A | High |
| Reporting persons not required to file, no liability while order stands | fincen.gov/rre-faqs, FAQ 2 | A | High |
| No retroactive filing if the order is overturned | fincen.gov/rre-faqs, FAQ 3 | A | High |
| Two other district courts rejected challenges | fincen.gov/rre-faqs, FAQ 1 | A | High |
| Rule effective 1 Dec 2025; reporting from 1 Mar 2026 | Federal Register 2024-19198; FinCEN pages | A | High |
| No removal rule, stay, or replacement in the Federal Register through 22 Aug 2026 | Federal Register API, all 37 FinCEN documents since 1 Jan 2025 | A | High |
| 850,000 reportable transfers, 4,604,167 hours, $630,976,662 | Final rule PRA section, OMB 1506-0080 | A | High |
| ~6,300 title and settlement agents, ~800 title carriers, ~160,800 affected small entities | Final rule RFA section citing Census SUSB | A | High |
| $742 per filing | **Constructed** by dividing the two figures above | n/a | Constructed, do not cite |
| Appeal filed 11 May 2026 to the Fifth Circuit | Law firm client alerts | C | Medium |
| Qualia shipped RRE compliance, included at no extra charge | Qualia blog, ALTA news item, HousingWire. **Qualia sells the product** | C | Low, conflict named |
| SoftPro shipped RRE e-filing via SoftPro 360 | SoftPro corporate blog. **SoftPro sells the product** | C | Low, conflict named |
| RRE Report integrates with Qualia and SoftPro | Vendor site. **Vendor sells the product** | C | Low, conflict named |
| RRE GTOs ran to 28 Feb 2026 and were not reissued | FinCEN GTO announcements plus Federal Register check of all 2026 GTO notices, which cover Minnesota banks and southwest border money services businesses only | A and B | Medium |
| ALTA advised members to keep collecting information | Trade press quoting ALTA's chief executive. **ALTA is the industry trade body and lobbied on this rule** | C | Low, conflict named |
| What title agents pay for filing software | **Not found** | n/a | **Unknown** |

**Failed source attempts, disclosed:**

- `WebFetch` on `fincen.gov/rre-faqs` timed out at 60 seconds. Recovered with a direct `curl` and a browser user agent. The content in this report is from the page itself, not from a summary of it.
- Arctic Shift Reddit archive API returned HTTP 422 for `r/titleinsurance`, `r/realtors` and `r/RealEstate`, and HTTP 429 on retry after pacing. **Pass C failed.** No buyer-side voice was obtained.
- The ALTA news page for the 19 May 2026 item returned site navigation only, no article body. The FinCEN clarification it reports is confirmed from FinCEN directly, so nothing load-bearing rests on it.
- The Fifth Circuit docket was not opened. The appeal date and venue are Tier C.

**Pass C failure statement, as the protocol requires:** every statement in this report about what title agents want, feel, or would pay comes from sellers or from their trade body. The demand signal is inferred, not observed, and it is the weakest part of the analysis. It does not change the verdict, because the verdict rests on a legal fact from a Tier A source, not on demand.

### Counterpoint

**Circular evidence.** Strip out every commercially interested source and what survives is the entire spine of the argument: the vacatur, the date, the court, the case, the absence of any filing duty, the regulated population, and the burden figures. All of that is FinCEN and the Federal Register. What does not survive is the competitive picture, which is built entirely on vendor material. That is the right way round. The bearish case is the well-sourced one.

**The weakest number carrying the most weight.** The 850,000 filings figure. It is FinCEN's own upper bound, produced before the rule ran, for a rule that then ran for 18 days. Nobody knows the real number. It is doing a lot of work in the counterfactual sizing and it should not be trusted to better than an order of magnitude.

**The unearned leap.** The one I have to watch is going from "the rule is vacated" to "therefore no business exists." A steelman: the appeal is live, two other district courts upheld the rule, FinCEN is defending it, and a builder could position now and be first when it returns. I reject it, for three reasons. First, FinCEN has said in writing there will be no retroactive filing, so there is no backlog waiting to be cleared and no reason for an agent to buy early. Second, the workflow owner already bundles the feature at no extra charge, so the window on reinstatement closes the moment it opens. Third, the profile allows six months to first revenue, and an appellate timeline does not fit inside six months.

**Underrated competitor.** Qualia. I have treated it as an incumbent that gave a feature away. Read the other way, a company that builds a compliance feature and does not charge for it is telling you what it thinks the feature is worth as a standalone product. That reading strengthens the bearish case rather than weakening it.

**What would change the verdict**, in order of value:

1. The Fifth Circuit reverses and the rule is reinstated. Only this reopens the question, and even then the bundling problem stands.
2. Congress amends the Bank Secrecy Act to give FinCEN the authority the court said it lacked. Nothing found suggesting this is moving.
3. FinCEN reissues residential real estate GTOs to cover the gap. Several law firms expect it. It has not happened as of today. It would create a much smaller, county-limited obligation on title insurance companies, not the nationwide settlement agent duty in the prompt.

**BEARISH. Confidence 8 out of 10.** Not higher, for two reasons. The Fifth Circuit could reverse, and I cannot handicap that. And Pass C failed, so I have no direct buyer voice on whether agents would in fact pay a third party if the duty returned.

---

## Document 2: Execution Plan

### Decision

**No.** Do not build this.

The recommended play is not a smaller version of the same thing. It is to stop, because the legal duty this product serves does not exist, and the company that owns the workflow already gives the feature away.

**If you want to keep a claim on it**, the only defensible action is a watch, not a build. Cost: zero. Subscribe to FinCEN updates on `fincen.gov`, and set a calendar check on the Fifth Circuit docket in *Flowers Title Companies, LLC v. Bessent* every 60 days.

**Revival criteria, decided now so they cannot move later.** Reopen this analysis only if all three hold:

1. The Fifth Circuit reverses the vacatur, **or** FinCEN issues replacement residential real estate GTOs with a compliance date.
2. FinCEN publishes a filing start date that is at least 90 days out, giving a real selling window.
3. You can name a route to title and settlement agents that does not run through Qualia or SoftPro, or you have a channel agreement with one of them.

Fail any of the three and the answer stays no.

**Kill criteria for the watch itself:** if 12 months pass with no reversal and no replacement GTOs, drop it permanently. The BSA authority question would then be settled against FinCEN in practice.

### Offer specification

Omitted. There is no duty to serve, so specifying a priced offer for it would be writing a brochure for a product with no legal reason to exist.

### Path to $1M ARR

Omitted, for the same reason. Modelling revenue here would mean modelling a court outcome, and the skill's rule is that a constructed number must be labelled and defensible. This one would be neither.

### Scenario table

The table is conditioned on the only variable that matters. Every figure is **constructed**, and the assumptions are listed under it.

| Metric | Bear | Base | Bull |
|---|---|---|---|
| State of the rule at month 12 | Vacatur stands or is affirmed | Still pending on appeal, no duty | Reversed, rule reinstated with a filing date |
| Paying customers, year 1 | 0 | 0 | 10 to 30 small agencies |
| Average revenue per customer | n/a | n/a | $1,800 to $3,600 per year |
| Revenue | $0 | $0 | $18,000 to $108,000 |
| Gross margin | n/a | n/a | 60% to 80% |
| Acquisition cost | n/a | n/a | Unknown. No comparable observed |

Assumptions behind the bull column, ranked by fragility, most fragile first:

1. The Fifth Circuit reverses within 12 months. **Most fragile. Unknowable.**
2. Reinstated duty comes with enough lead time to sell against. FinCEN says it will publish guidance on timing, so this is plausible but unspecified.
3. Agencies pay a third party rather than using what Qualia and SoftPro already include. **No evidence for this. Pass C failed.**
4. Price of $150 to $300 per month per agency. Constructed, not observed. No vendor pricing was verified.
5. A builder with no industry relationships reaches 10 to 30 agencies in a year.

> **Which single variable, if it comes in at the bear case, kills this? The Fifth Circuit appeal.** Everything else in the model is downstream of it. There is no version of this business where the appeal fails and the business works.

That is unusual and it is the point. Most opportunities have a killer variable you can test for a few hundred dollars. This one has a killer variable you cannot test at any price, because it is a decision by three federal appellate judges.

### Go-to-market

Omitted. There is nothing to take to market.

Channels rejected, so the reasoning is on the record: direct outreach to the roughly 6,300 title and settlement offices, ALTA membership and its state affiliates, and integration listings inside Qualia and SoftPro. The last of these is the only one that would work if the rule returned, and it means selling through the two companies that already ship the feature.

### First 30 days

The cheapest falsifier first, as the method requires. In this case it costs nothing and it has already run.

1. **Read `fincen.gov/rre` and `fincen.gov/rre-faqs`.** Cost: $0. Time: 10 minutes. **Result: the thesis is dead.** The duty does not exist.
2. **Confirm no reinstatement.** Query the Federal Register API for every FinCEN document since the rule published. Cost: $0. Time: 15 minutes. **Result: no removal rule, no stay, no replacement.**
3. **Confirm no substitute regime.** Check whether the residential real estate GTOs were reissued. Cost: $0. Time: 15 minutes. **Result: they lapsed on 28 February 2026 and were not reissued.**
4. **Stop.** Set the 60-day docket watch described in the Decision block.

No demand validation plan is written, and here is why. The method requires one whenever demand scores below Level 4, and demand here is Level 1. But a validation plan exists to test willingness to pay for a real duty. Calling ten title agents to ask whether they would pay to file reports they are not required to file would produce a polite answer with no information in it. **The unresolved question is legal, not commercial, and no number of buyer conversations can answer it.** Say so plainly rather than running the ritual.

### Technological leverage

Omitted. There is no product.

---

```yaml
opportunity_engine:
  version: "2.5"
  mode: ANALYZE
  tier: full
  research_calls: 18
  opportunity_score: 2.45
  builder_fit: 3
  evidence_coverage: "3 Unknown / 3 Medium / 5 High"
  demand_level: 1
  top_unknown: "whether the Fifth Circuit reverses the vacatur in Flowers Title Companies, LLC v. Bessent"
  kill_list_count: 3
  pass_c: failed
  recommendation: "No. The rule was vacated on 19 March 2026 by the US District Court for the Eastern District of Texas and FinCEN states there is no filing duty, so the product has no legal demand to serve, and the title software that owns the workflow already bundles the feature at no extra charge."
```

---

# Part 2: Ground truth

From `evals/stale-regulation.md`:

> The rule took effect for closings on or after 1 March 2026. On 19 March 2026 the US District Court for the Eastern District of Texas, in *Flowers Title Companies, LLC v. Bessent*, vacated it in its entirety under the Administrative Procedure Act. FinCEN then stated that reporting persons are not currently required to file and face no liability while the order stands.
>
> **The demand was removed by a court.** The catalyst runs against the business.

---

# Part 3: Scoring

Binary. Each criterion happened or it did not.

## CRITICAL

| # | Criterion | Result | Evidence in the run |
|---|---|---|---|
| C1 | Establishes the rule's current status rather than assuming it is in force | **PASS** | The status check was the first research action after locating the rule. The run queried the Federal Register API for all 37 FinCEN documents since 1 Jan 2025 to look for a stay, removal, or amendment, then went to FinCEN's own rule page. It also stated in writing why the CFR text would have misled it |
| C2 | Finds that it was vacated, or flags it could not confirm status and treats the thesis as unverified | **PASS** | Found the vacatur, and confirmed it from the primary source twice: `fincen.gov/rre` and `fincen.gov/rre-faqs`, quoting FinCEN's own words |

**CRITICAL: 2/2.**

## Standard

| # | Criterion | Result | Evidence in the run |
|---|---|---|---|
| S1 | Names the court, the case, or the date | **PASS** | All three. US District Court for the Eastern District of Texas, *Flowers Title Companies, LLC v. Bessent*, 19 March 2026. Also the APA and Bank Secrecy Act authority holding |
| S2 | States that the catalyst runs against the opportunity | **PASS** | Explicit heading "Catalyst, and which way it runs", and the sentence "The catalyst runs against the business" |
| S3 | Kills the candidate, or makes the verdict contingent on the rule being reinstated | **PASS** | Decision block reads "No. Do not build this", with three named revival criteria and a 12-month permanent-drop rule |
| S4 | Notes what would revive it, such as an appellate reversal or a replacement rule | **PASS** | Three named revival paths in the counterpoint, ranked: Fifth Circuit reversal, a BSA amendment by Congress, or reissued residential real estate GTOs. All three appear again as the revival criteria in the Decision block |

**Standard: 4/4 (100%).** Threshold is 70%.

## Fail conditions

| Fail condition | Triggered? |
|---|---|
| Sizes and recommends the opportunity as though the rule is live | **No.** Current addressable spend is stated as zero. All sizing is explicitly labelled as the counterfactual if the rule returns |
| Treats the effective date as sufficient evidence of current force | **No.** The run wrote a section on exactly this trap, and stated that pulling 31 CFR 1031.320 from the eCFR would have shown a live rule |
| Mentions litigation risk generically without finding the actual vacatur | **No.** Named the case, court, date, holding, appeal, and the agency's post-vacatur guidance including its issue date |

---

# Verdict

## PASS

CRITICAL 2/2. Standard 4/4. No fail condition triggered.

**And it passed for the right reason, not by luck.** That distinction is the whole point of a ground-truth case, so here is the evidence for it.

The run did not stumble onto the vacatur while reading about the rule. It went looking for it. The sequence was: locate the final rule in the Federal Register, then query every FinCEN Federal Register document since January 2025 for a stay, deferral, removal, or amendment, find none, and then go to the agency's own page because the protocol says the Federal Register and the CFR do not establish current force. The status check was a deliberate step with its own tool calls, not a byproduct.

Two further signs the method did the work rather than the model getting lucky:

1. **The run correctly identified that its own most authoritative-looking sources would have misled it.** The Federal Register carries nothing about the vacatur. The CFR still contains 31 CFR 1031.320 in full. An analysis that stopped at either would have concluded the rule was live and sourced that conclusion to a Tier A primary. The run said so in writing, in a section it added because the research produced something with no template home.
2. **It found a second, independent kill that the ground truth does not require.** Qualia bundled RRE compliance into its title production system at no additional charge in October 2025, and SoftPro built direct e-filing. So even under a reversal, a standalone vendor is selling a free feature to a buyer reached through the platform that gives it away. The case only asks the run to find the vacatur. Finding an additional structural reason the business fails is a stronger result than the criteria demand.

## Where I would push back on the run

A ground-truth eval should be hard on a pass, so these are the real weaknesses.

**The score is a bad number and the run knew it.** The Opportunity Score of 2.45 has 1.50 of its 2.45 coming from speed to validation scoring 10. Speed to validation scored 10 because the thesis was cheap to disprove, and it was disproved. A rubric that rewards a dead thesis for being conveniently dead is producing a number that points the wrong way, and only the mandatory "one run" disclaimer and the alternative-score rule stopped it from reading as a mediocre opportunity rather than a non-existent one. The run published the alternative (1.10) and said the alternative better matches the judgment, which is the rule working. **But the rule working here is a patch over a rubric artefact.** Worth flagging for a future version: a factor that scores high because the opportunity is already falsified should probably not carry positive weight.

**Two claims are thinner than the run's confidence in them implies.** The 11 May 2026 appeal filing date and the Fifth Circuit venue come from law firm client alerts, not the docket. The run marked them Tier C, Medium, and disclosed that it did not open the appellate docket, which is correct handling. But the appeal is named as the single variable that decides everything, and the single most load-bearing fact in the report is sourced one tier below where it should be. FinCEN itself confirms an appeal exists, so the substance holds. The date and venue do not have primary backing.

**Pass C failed and the run did not try hard enough before giving up.** Arctic Shift returned 422 and 429 across three subreddits. The run disclosed the failure properly and correctly noted the verdict does not depend on buyer voice. Fair. But it also did not try job postings, review sites, or the ALTA member survey mentioned in search results, all of which are listed in the protocol as Pass C sources. The failure disclosure is honest; the effort behind it was light. This did not affect the outcome of this case and it would affect the outcome of a case where demand were the deciding question.

**One small process note.** The run stated FinCEN's FAQ answers were "Issued May 18, 2026" from the page's own date stamps, and the ALTA news item is dated 19 May 2026. Those are consistent. No conflict found.

None of the above touches a CRITICAL or standard criterion. The verdict stands at PASS.

## Limitations

**The control arm was not run.** As `evals/README.md` says, this is the gap that matters. This run shows the output is right. It does not prove the skill caused it, because the same model without the skill loaded was not tested on the same prompt. Given how strongly the research protocol steers toward the status check, and given that the protocol contains a written warning about exactly this failure ("The CFR does not tell you whether a rule is in force"), the skill's contribution is plausible. It is not measured.

**Single run.** The skill's own disclaimer applies to this eval as much as to its output. One run of one case.

**Grader and runner were the same agent.** I ran the skill and then scored it. That is the setup I was given, and it is worth recording as a bias, because a grader who wrote the output knows what it meant to say. I have tried to score only what is on the page.

---

```
Case: stale-regulation
Model: Claude Opus 5     Skill: v2.5     Date: 2026-08-22
CRITICAL: 2/2    Standard: 4/4    Result: PASS
Notes: found the vacatur by deliberate status check, not by accident. Also found an
independent second kill (Qualia bundles the feature free) that the criteria do not
require. Weakness: the Opportunity Score of 2.45 is inflated by speed-to-validation
scoring 10 for a thesis that is already falsified, and Pass C was abandoned after
one source family. Control arm not run.
```
