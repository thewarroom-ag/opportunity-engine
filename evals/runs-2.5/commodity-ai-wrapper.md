# Eval run: commodity-ai-wrapper

```
Case:   commodity-ai-wrapper
Model:  Claude Opus 5 (claude-opus-5)
Skill:  v2.5
Date:   2026-08-22
CRITICAL: 2/2    Standard: 5/5    Result: PASS (with a method caveat, see Verdict)
```

---

## Provenance note, read this before trusting the version label

The skill was invoked from `~/.claude/skills/opportunity-engine`. That installed copy's `VERSION.md` reads **2.4**, not 2.5.

Checked before running: `SKILL.md` and every file in `references/` are **byte-identical** between the installed copy and the 2.5 repo at `/Users/alexeitrubetskoy/Desktop/THEWARROOM/opportunity-engine`. Only `CHANGELOG.md`, `README.md`, `USAGE.md` and `VERSION.md` differ. The 2.5 changelog entry confirms this: 2.5 removed two sample runs and edited documentation, and states "Nothing in the scoring path changed."

So the scoring path exercised here is 2.5's scoring path. The run is a valid test of 2.5.

**Separate defect found, not part of this case:** the installed copy will stamp `version: "2.4"` into every machine-readable block while running 2.5's logic. `VERSION.md` calls that field provenance and says a wrong value "silently invalidates any comparison between runs." Worth fixing.

---

## Setup used

The eval case's profile, not the repository's real builder profile.

```
Capital ceiling: $75,000
Time to first revenue: 5 months
Geography: US only
Interest areas: AI automation, recurring revenue
Unfair advantages: senior software engineer, ships fast. No legal
background, no law firm relationships.
Hard nos: nothing requiring a sales team.
```

Prompt, pasted exactly:

> Analyze this: a micro-SaaS that automates contract review and clause flagging for small law firms, sold self-serve at $99 to $399 per month.

Mode: ANALYZE. Tier: Full. Research: native web search available, so not degraded mode.

---
---

# THE RUN

## Document 1: Opportunity Analysis

### Thesis

Small US law firms review contracts by hand and pay for that time. A Word add-in that flags risky clauses and proposes redlines, sold self-serve at $99 to $399 a month, would sell that time back to them. The thesis fails on entry, not on need. At least eight funded companies already sell this exact product into this exact segment at this exact price, and on 30 April 2026 Microsoft shipped clause-by-clause contract review with tracked-change redlining natively inside Word for US tenants. The capability is not scarce. Access to lawyers is scarce, and the builder has none.

### Executive summary

| Question | Answer |
|---|---|
| Is the pain real? | Probably. Not observed directly, see the failed Pass C below |
| Is the capability scarce? | No. Every competitor uses the same frontier models, and so can the customer |
| Does the incumbent ship it? | Yes. Microsoft Word Legal Agent, 30 April 2026, US-only, which is the builder's exact geography |
| Is the price defended? | No. Gavel Exec sells contract review and redlining in Word at $99/month, the floor of the proposed band |
| Does the builder hold the scarce input? | No. The scarce input is trust and access to lawyers, not engineering |
| Opportunity Score | 4.2 |
| Builder Fit | 3, capped |
| Decision | See Document 2. It is a no |

> This score is one run. A second run of the same research on the same day can land a point or more away, and has. Read the reasoning, the kill list and the unknowns. Those hold across runs. The number does not.

### Catalyst, and it runs against you

**30 April 2026.** Microsoft released Legal Agent inside Word for Windows through its Frontier early-access program. It performs clause-by-clause contract review against a playbook, produces tracked-change redlines, and writes rationale comments. It requires Microsoft 365 Copilot licensing, with the E7 Frontier Suite priced at $99 per user per month from 1 May. At launch it is **US-only and Windows-only**.

Separately, Microsoft's own adoption documentation already lists contract review as a supported Copilot scenario: summarize a contract, compare two agreements in a table, extract key clauses and terms, and flag potential risks and unfavorable terms. That is the candidate's entire feature list, published by Microsoft, about Microsoft's product.

There is a catalyst here and it points the wrong way. The thing that changed recently is that the incumbent office suite started shipping this for free-ish inside the surface where lawyers already work. A US-only launch is the worst possible shape for a US-only builder.

### Market: reachable pool, not category

| Figure | Value | Note |
|---|---|---|
| Category size | **Unknown** | No published figure for US small-firm AI contract review that I could trace to a primary. Legal tech funding totals exist but a funding total is not a market |
| Serviceable | **Constructed, Low confidence** | See below |
| Beachhead | **Constructed, Low confidence** | See below |
| 36-month obtainable | **Unknown** | Depends entirely on acquisition cost, which is Unknown |

Construction, and every step is labeled:

- Roughly 463,000 US law firms in 2025, with about 75% at six or fewer attorneys (Tier C aggregator, Low confidence).
- Only a minority of small-firm work is transactional. Common solo practice areas are bankruptcy, civil litigation, family law, estate planning and immigration. None of those generate contract-redline volume. The one published transactional/litigation split I found (55 to 65% transactional) is on **Spellbook's own website**, and Spellbook sells contract review software. That is Tier C from an interested party, capped at Low, and I am not building a market estimate on it.
- ABA Legal Technology Survey: 30% of responding lawyers use AI, but only **18% of solo attorneys** do (Tier B trade body, Medium confidence). The average solo firm spends about half the US Census industry estimate on software (Tier C, Low).

Multiplying three Low-confidence numbers produces a number with no information in it. **I am not publishing a beachhead figure.** The honest statement is: the reachable pool is small-firm lawyers who do enough transactional volume to feel the pain, who are inside the 18% already using AI, and who are not already paying Clio or Spellbook or Gavel. That is a fraction of a fraction of a fraction, and nobody has published its size.

A data gap is not a small market, so this does not cost points on Demand. But it does mean nobody should model revenue off a category number here.

### Competitive landscape

**Topology: venture knife fight, inside a platform-controlled surface.** Both of the two worst topologies at once.

| Player | Price | Position | Funding | Why it matters here |
|---|---|---|---|---|
| **Microsoft Word Legal Agent** | $30/user/mo Copilot add-on; E7 Frontier $99/user/mo | Native in Word. Clause-by-clause review, tracked-change redlines, playbook review | n/a | The incumbent ships the product. US-only launch matches the builder's geography exactly |
| **Gavel Exec** | **$99/month** | Word add-in. Contract review, redlines, drafted clauses, negotiation comments. Explicitly solo to mid-size | Venture-backed | Sits on the exact floor of the proposed $99 to $399 band, with the same product, for the same buyer |
| **Spellbook** | roughly $89 to $199/user/mo, custom quotes | Word add-in. Explicitly targets 1 to 50 lawyer firms and solos | **$50M Series B, Oct 2025 (Khosla), plus $40M debt facility Mar 2026** | Owns the exact segment and price band, with 90x the builder's capital |
| **Clio Duo** | $49 to $59/mo on top of a $39 to $129 Clio base | AI attached to the practice management system small firms already run | Clio acquired vLex for about $1B in 2025 | Distribution the builder cannot buy. Already inside the account |
| **Ivo** | not published | Contract review | $55M Series B, 2026 | Funded |
| **Legora** | not published | Legal AI, moving down-market | $550M Series D, Mar 2026, $5.55B valuation | Capital that outlasts everyone |
| **Harvey** | not published | Legal AI, moving down-market | $200M raise, $11B valuation | Same |
| **Luminance, LegalOn, Definely, Summize, SpotDraft, Juro, LawGeex, LexCheck, Ironclad** | various | Contract review and CLM | Contract automation category has raised over $1.4B combined | The long tail is also funded |

Named by an independent trade publication as the vendors Microsoft's Word launch puts pressure on: Harvey, Legora, Spellbook, Luminance, Ironclad, BlueJ, LegalOn, Ivo, Definely, Gavel Exec. Also noted: Anthropic's Claude for Word as a second suite-native agent.

**The customer is also a competitor.** A lawyer can paste a contract into ChatGPT or Claude for $20 a month and get clause flagging. 62% of solo practitioners use or are considering ChatGPT (ABA, Medium confidence). The efficiency gain the candidate sells is available to the buyer directly, at a fifth of the price.

### Where the gap is

I did not find one. That is the finding.

The three candidate gaps I tested and rejected:

1. **"Funded players ignore small firms."** False. Spellbook markets to 1 to 50 lawyer firms and solos by name. Gavel Exec sells at $99 to solos.
2. **"Microsoft's version is enterprise-only."** Weak. It needs a Copilot licence, which is a real friction, but it is a $30 add-on to software small firms already buy, and Microsoft's incentive is to push it down-market, not up.
3. **"A narrow practice-area vertical, for example small-firm commercial real estate leases."** This is the only version with any structure left, and it is not the candidate as specified. It would need a legal domain expert as a co-founder, which the profile does not have, and it shrinks an already unsized pool.

### Why is this still available

**It is not.** This is the answer the report model says must stay on the table every time, and here it is the correct one.

Multiple funded companies solved this, are selling it now, at this price, to this buyer, in this geography. Then the platform owner shipped it natively. There is no dated enabling event that opened a window, no regulation that changed, no unglamorous work that software companies refuse to do. The work is writing prompts against a commodity model and shipping a Word add-in, which is precisely the work every well-capitalised legal tech company staffed up for two years ago.

**The thesis is wrong, and that is the honest reading.**

### Entry analysis

Capital to build is not the constraint and never was. A senior engineer can ship a credible Word add-in with clause flagging in eight to twelve weeks. Call it $8,000 to $25,000 all-in including inference, hosting, a SOC 2 readiness start, and an Apple/Microsoft store presence, well inside the $75,000 ceiling. First revenue inside five months is plausible.

That is the trap. **The cheap part is the part that is not scarce.** The expensive part, which is getting a risk-averse professional who has never heard of you to trust you with privileged client documents, is not solved by capital at this level either.

### Unit economics

| Metric | Bear | Base | Bull |
|---|---|---|---|
| Paying customers, year 1 | 8 | 35 | 110 |
| Average revenue per customer, per month | $99 | $149 | $220 |
| Revenue, year 1 | $6,000 | $47,000 | $180,000 |
| Gross margin | 55% | 75% | 85% |
| Acquisition cost per customer | $2,500 | $900 | $350 |
| Months to repay acquisition cost | never | 8 | 2 |
| Monthly logo churn | 9% | 5% | 2.5% |

Every cell is **constructed, not sourced**. There is no published CAC or churn benchmark for self-serve legal SaaS at this price point that I could trace to a primary. Margin is the one input I hold with reasonable confidence: frontier-model inference on contract-length documents runs a few dollars per active user per month at normal volumes, so 70% plus is realistic at $99 and better at $399.

> **Which single variable, if it comes in at the bear case, kills this? Acquisition cost.**

Nothing else is close. Margin is fine. Build cost is fine. Price is fine, though capped. If it costs $2,500 to acquire a lawyer who pays $99 a month and churns in eleven months, the business is arithmetically dead and no amount of product work fixes it. Legal is one of the most expensive acquisition categories there is, and the builder would be bidding against a company that just raised $50M and another that just raised $550M.

### Risks

| Risk | Severity | Mitigation |
|---|---|---|
| **Acquisition cost exceeds lifetime value** | Fatal | None available inside the profile. The hard no on a sales team removes the motion that works in this segment |
| **Microsoft absorbs the category** | Fatal | None. This already started on 30 April 2026 |
| **Platform dependency on Word** | Severe | Build outside Word, which makes the product worse, because the work happens in Word |
| **No legal credential or relationships** | Severe | Hire or partner with a lawyer, which the profile does not budget for and which changes the business |
| **Confidentiality and privilege objections** | Moderate | Real engineering work: no-training guarantees, data residency, SOC 2. It is table stakes, not an edge, and it delays revenue |
| **Frontier model price and policy changes** | Moderate | Multi-provider abstraction. Adds cost, buys no advantage, everyone does it |

### Regulatory

Omitted as a driver. No regulation creates a buying trigger here. Unauthorized practice of law and professional responsibility rules constrain how the product is marketed, but they are a compliance cost on the builder, not a mandate pushing lawyers to buy. The liability question is not worth running: there is no third party being forced to act by a dated rule.

### What got filtered out

ANALYZE mode does not kill the candidate, it scores it. But three framings were rejected on the way:

1. **"AI is the whole product, so technological leverage is high."** Rejected. See the scoring note.
2. **"Senior engineer who ships fast is the unfair advantage."** Rejected. See below.
3. **"$99 to $399 is affordable, so price is a wedge."** Rejected. Gavel Exec is already at $99 and Microsoft's add-on is $30. The band is not a wedge, it is a ceiling somebody else set.

### Score

**Opportunity Score: 4.2**

| Factor | Weight | Score | Contribution | Basis |
|---|---|---|---|---|
| Demand intensity | 20% | 7 | 1.40 | Level 3, existing spend. Inferred from live competitor pricing, not observed. See the alternative below |
| Distribution | 20% | 4 | 0.80 | Reachable, unproven. Buyers are listable. Cost and conversion unknown, and the no-sales-team rule removes the proven motion |
| Economics | 20% | 7 | 1.40 | Recurring by construction, 70%+ margin, but payback is unknown and price is capped by others |
| Defensibility | 15% | 1 | 0.15 | No moat. See below |
| Speed to validation | 15% | 7 | 1.05 | The demand question is cheap to test. The killer question, acquisition cost, is not |
| Technological leverage | 10% | **4** | 0.40 | See below. This is the factor the case is about |
| Subtotal | | | **5.20** | |
| Platform dependency | | **-1** | | Lives inside Word as an add-in. Microsoft controls the surface and just shipped a competing native agent |
| **Total** | | | **4.20** | |

**Technological leverage, scored at 4 and here is why.**

AI is 100% of this product. That is exactly why the score is not high. The rubric scores the advantage created, not the technology present. Ask what the model gives this business that it does not give everyone else:

- **Competitors have the same access.** Spellbook, Gavel Exec, Ivo, Luminance, Legora and Harvey all call the same frontier models through the same public APIs. No one of them holds a model the others cannot rent.
- **Microsoft has it natively**, in the application where the document already lives, at $30 a user.
- **The customer has it directly.** A lawyer with a $20 ChatGPT subscription gets clause flagging without buying anything from anyone in this table.
- **No proprietary data accrues.** The obvious data moat, pooling reviewed contracts to improve the model, is blocked by client confidentiality and privilege. The one asset that could compound is the one this business is not allowed to build.

That is the textbook definition of band 4: an efficiency gain available to everyone, including your competitors and your customer.

**Alternative scorings, published.**

```
Opportunity Score: 4.2.

Scoring technological leverage at 1 rather than 4 gives 3.9. A fair
argument: now that Microsoft ships clause review inside Word, this
is table stakes rather than an efficiency gain, and 1 is the band
for table stakes. I used 4 because the rubric reserves 1 for no
advantage at all, and a purpose-built playbook tool is still
meaningfully better than raw Copilot today. I would not argue hard
against 1.

Scoring demand at Level 2 (4) rather than Level 3 (7) gives 3.6.
The rubric says desk research usually tops out at Level 2, and my
buyer-voice pass failed outright, so I never saw a lawyer say what
they pay. I used 7 because Gavel Exec, Clio Duo and Spellbook are
live products with published prices in this exact band, which is
category spend even if I did not observe an individual buyer. This
is the softest number in the model.

Scoring distribution at 1 rather than 4 gives 3.6. Defensible:
lawyers buy on referral and the profile forbids the sales motion
that produces referrals. I used 4 because Gavel Exec demonstrates
that a self-serve motion exists at $99.

Every alternative moves the score down. None moves it up. That
asymmetry is itself the finding.
```

**Builder Fit: 3 (capped: no route to law firm buyers)**

| Dimension | Score | Reason |
|---|---|---|
| Capital | 8 | Build fits inside $75,000 with reserve. Not the constraint |
| Distribution assets | **1** | No legal audience, no law firm relationships, no list. This caps the total at 4 |
| Credential and access | 2 | No legal background. Lawyers buy contract tooling from people who have read a contract for a living |
| Time | 8 | Software product, builder ships fast. Fine |
| Risk and hard nos | 3 | "Nothing requiring a sales team" collides with the segment. Self-serve into law firms usually still needs a demo and a confidentiality conversation |

**On the stated advantage.** "Senior software engineer, ships fast" is not an edge in this market. It is the entry requirement. Every competitor in the table above employs senior engineers who ship fast, several employ dozens, and Spellbook has $50M plus a $40M debt facility to hire more. Shipping speed is a differentiator where engineering is the scarce input. Here it is the abundant one.

**The scarce input in this market is trust and access to lawyers**, held through bar association standing, practice experience, a legal audience, or an existing seat in the firm's software stack the way Clio has one. The profile explicitly holds none of these and explicitly rules out building the sales motion that substitutes for them.

**Evidence Coverage**

| Component | Confidence |
|---|---|
| Competitors exist, are funded, and sell this product | **High** |
| Microsoft ships the capability natively in Word | **High** |
| Competitor pricing overlaps the proposed band | Medium |
| Buyer exists and is reachable | Medium |
| Pain is real | Medium |
| Delivery cost and margin | Medium |
| They will pay a new vendor for it | **Low** |
| Acquisition cost | **Unknown** |

**Pass C failed.** Three attempts against the Arctic Shift archive API (r/LawFirm, r/Lawyertalk, r/smalllaw, r/legaltech; terms Spellbook, contract, redline, subscription) returned `Timeout. Maybe slow down a bit` and `Too many requests` on every scoped query, including a single paced retry with a 90 second timeout. One query returned a valid empty result set. No buyer-voice data was recovered. Every statement in this report about what buyers want or will pay is inferred from sellers and from one trade-body survey, not observed from buyers. The demand signal is the weakest part of this analysis and Level 3 should be read as a ceiling, not a measurement.

**The unknown that would most change the decision:** what it costs to acquire one paying small-firm lawyer through a self-serve channel, and whether that number survives Microsoft bundling the capability at $30. Everything else is either known or does not matter.

### Verification table

| Claim | Source | Tier | Independence | Confidence |
|---|---|---|---|---|
| Microsoft released Legal Agent in Word, 30 Apr 2026, clause-by-clause review with tracked-change redlines, US-only and Windows-only, needs Copilot Frontier licensing; E7 Frontier $99/user/mo from 1 May | ComplexDiscovery | B | Independent trade press | High |
| Microsoft documents contract review as a supported Copilot scenario: summarize, compare agreements, extract key clauses, flag risks and unfavorable terms | Microsoft Adoption scenario library | A, for facts about Microsoft's own product | Interested in its own product, but this is a self-disclosure of capability | High |
| M365 Copilot add-on is $30/user/mo | ComplexDiscovery, plus widely published | B | Independent | High |
| Spellbook raised $50M Series B Oct 2025 (Khosla), $20M Series A Jan 2024, $40M debt facility Mar 2026 | Sacra, Legaltech Hub | B/C | Independent trackers | Medium |
| Spellbook targets solos and 1 to 50 lawyer firms | Spellbook's own site | C | **Vendor, about itself. Positioning claim, which is what I am citing it for** | High for positioning |
| Spellbook pricing roughly $89 to $199/user/mo, not publicly listed | Four comparison blogs, several run by competing vendors | C | **Conflicted. Hyperstart, GC AI, Bind and AI Vortex all sell or review competing tools** | Low |
| Gavel Exec at $99/month, Word-based contract review and redlining, solo to mid-size | AI Vortex comparison chart | C | Conflicted, comparison site | Medium |
| Clio Duo $49 to $59/mo on a $39 to $129 base | Multiple pricing roundups | C | Conflicted | Medium |
| Legora $550M Series D Mar 2026 at $5.55B; Harvey $200M at $11B; Ivo $55M Series B | New Market Pitch, PlatinumIDS | C | Funding trackers, no stake in this claim | Medium |
| Contract automation category has raised over $1.4B combined | New Market Pitch | C | Aggregator | Low |
| Named vendors under pressure from Microsoft's launch: Harvey, Legora, Spellbook, Luminance, Ironclad, BlueJ, LegalOn, Ivo, Definely, Gavel Exec | ComplexDiscovery | B | Independent trade press | High |
| 30% of lawyers use AI; 18% of solos; 62% of solos use or consider ChatGPT | ABA Legal Technology Survey, via LawSites and ABA Journal | B | Trade body survey, mild self-interest in appearing current | Medium |
| Average solo firm spends about half the Census industry estimate on software | ABA Solo and Small Firm TechReport, via aggregator | B/C | Trade body | Low |
| About 463,000 US law firms; roughly 75% at six or fewer attorneys | Embroker, Orbital, referent.law | C | **Insurance broker and legal-data vendors selling to law firms** | Low |
| 55 to 65% of US lawyers do transactional work | **Spellbook's own content marketing** | C | **Direct conflict. Spellbook sells transactional contract software and profits from that number sounding large.** Not used in any calculation | Low |
| CAC, churn, and all scenario-table figures | **Constructed by me** | n/a | n/a | **Unverified** |

**Failed sources, disclosed:**

- **Arctic Shift Reddit archive API.** Three attempts, twelve scoped queries across r/LawFirm, r/Lawyertalk, r/smalllaw and r/legaltech. Rate-limited and timed out on all but one, which returned zero results. Pass C is failed, not skipped. Firecrawl was not available in this environment as a fallback.
- **Spellbook, Gavel and Clio official pricing pages.** Spellbook does not publish pricing at all. Every price in the table for Spellbook comes from third-party comparison blogs, several written by competitors, which is why that row is capped at Low.
- **Microsoft's own launch post for the Word Legal Agent.** Not retrieved directly. The date, capability and licensing come from independent trade press. The capability claim is independently corroborated by Microsoft's own scenario documentation, which I did retrieve.

### Counterpoint

**Circular evidence.** Most of what I know about this market comes from people selling into it. Spellbook's positioning comes from Spellbook. The transactional-lawyer percentage comes from Spellbook. Half the pricing comes from comparison blogs run by competing vendors. Strip every commercially interested source out and what survives is: Microsoft's own documentation of the capability, independent trade press reporting the 30 April launch and naming ten affected vendors, funding tracker data, and an ABA survey.

**That surviving set is enough, and it is enough for the bearish case specifically.** The bearish conclusion rests on facts that no interested party would want published: that the platform owner shipped the product, and that ten funded companies are already in the space. Those are the two load-bearing claims and neither comes from someone who profits from me believing it. The bullish case, by contrast, would rest entirely on vendor material. That asymmetry is the strongest thing in this analysis.

**Weakest number carrying the most weight.** The Demand score of 7. It carries 20% of the model and rests on an inference from competitor pricing pages, because Pass C failed. If small-firm lawyers are not actually buying at these prices and the funded vendors are living on mid-market and in-house budgets instead, Demand drops to 4 and the score goes to 3.6. Second weakest: the $99 Gavel Exec price, from one comparison chart, not from Gavel.

**The unearned leap.** I did not make the usual one. I made a different one: I moved from "Microsoft shipped a Legal Agent" to "Microsoft will absorb the category." The agent is in a Frontier early-access program, Windows-desktop only, and enterprise early-access programs frequently stall. A fair reading is that it will not reach solo practitioners for two years, which is a real window. I discounted that window because Microsoft's incentive is to bundle down-market and because the candidate cannot build a moat inside the window anyway. But the leap is there and a reader should see it.

**Underrated competitor, read the other way.** Clio. I treated it as a distribution threat. It could equally be read as evidence that the segment does buy software at these prices, since Clio built a large business selling exactly this buyer at $39 to $129 a month. That reading makes Demand look better than I scored it, and it is the single best argument against my Demand-at-4 alternative.

**Who I dismissed too fast.** The narrow-vertical reframe. A tool for one practice area with a fixed clause playbook, for example small-firm commercial leases or independent contractor agreements, is a genuinely different product from a horizontal contract reviewer, and the funded players will not chase a niche that small. I dismissed it because the profile has no legal domain expert, which is a Builder Fit objection rather than an Opportunity objection. Someone else could build it.

**What would change the verdict, in order of value:**

1. Ten small-firm transactional lawyers saying what they pay now for contract review and what they would pay a new vendor. This resolves Demand and it costs nothing but time.
2. A real CAC number from $2,000 of paid acquisition. This resolves the killer variable.
3. Evidence that Microsoft's Legal Agent will stay locked in enterprise Frontier tiers for two or more years. This reopens the window.
4. A named legal co-founder with practice experience and a referral network. This alone moves Builder Fit from 3 to roughly 6.

**BEARISH. Confidence 7 out of 10.**

Not higher because Pass C failed completely, so the demand side of this analysis is inferred rather than observed, and because a third of the pricing evidence comes from parties selling competing products. Not lower because the two facts that carry the verdict, that Microsoft ships this natively and that ten funded companies already occupy the segment, are both well sourced and neither is disputed by any source I found.

---
---

## Document 2: Execution Plan

### Decision

**No.** Do not build the horizontal product as specified.

The reason is not that the market is bad. It is that the candidate's only proposed advantage, engineering, is the abundant input in this market, while the scarce input, trusted access to lawyers, is one the profile explicitly lacks and explicitly refuses to build. Adding a well-executed eleventh entrant into a segment where the platform owner just shipped the feature natively is a way to spend $25,000 and five months confirming something two hours of research already showed.

**Conditional go, on a different product.** If the builder wants this market, the only version with structure left is a single-practice-area playbook tool built with a named lawyer as co-founder who brings the referral network. That is a different business, it violates the profile's implied solo-software shape, and it should be scored separately rather than smuggled in under this thesis.

**Kill criteria, if the builder proceeds against this recommendation.** Decide these now, before liking the idea:

| Date | Test | Kill if |
|---|---|---|
| Day 14 | 20 small-firm transactional lawyers contacted, 10 spoken to | Fewer than 4 name a current spend on contract review tooling, or fewer than 3 say Word Copilot would not be good enough |
| Day 30 | $1,500 of paid acquisition against a landing page with a real price | Fewer than 2 trial signups, or blended cost per signup above $250 |
| Day 60 | First 5 paying customers | Any acquisition cost above $1,200, or fewer than 3 of 5 still paying at day 90 |

Precommit to these. The reason for writing them down on day zero is that on day 45 the goalposts move.

### Offer specification

Specified only because revenue cannot be modelled without it, not as a recommendation.

Microsoft Word add-in, Windows and Mac. Upload or open a contract, pick a playbook, get clause-by-clause flags with severity, tracked-change redline suggestions, and a rationale comment on each. Three tiers: $99 solo (50 documents/month, 3 stock playbooks), $199 (unlimited documents, custom playbooks), $399 firm (5 seats, shared playbooks, audit log). No-training guarantee on customer documents, US data residency, and a signed BAA-equivalent confidentiality addendum, all of which are table stakes and none of which are a feature.

Note what is missing from that spec: anything a competitor cannot ship in a sprint.

### Path to $1M ARR

At the base-case $149 average, $1M ARR needs about **560 paying firms**. At the $99 floor it needs about 840.

Assumptions, ranked by fragility, most fragile first:

1. **Acquisition cost stays under $900.** Most fragile. Unverified, and legal is an expensive category with two competitors holding nine-figure war chests bidding the same terms.
2. **Monthly logo churn stays at or under 5%.** Unverified. At 5% the average customer lasts 20 months, which is barely enough at $900 CAC. At 9% the business never repays acquisition.
3. **Price holds at $149 average.** Fragile. Gavel Exec is at $99 and Microsoft's add-on is $30. Price goes down from here, not up.
4. **560 small firms will buy from an unknown vendor with no legal credential.** Unverified and untested.
5. Gross margin holds above 70%. Least fragile. This one is probably fine.

Shape benchmark, not a peer: median micro-SaaS reaches $1M ARR in roughly 2 to 3 years (Tier C aggregator, Low confidence). Different vertical, different competitive structure. Included as a pace check on the arithmetic above, not as evidence about this market.

Four of the five assumptions are unverified and the top two are the ones the model lives on. A path that depends on four unverified assumptions is not a path, it is a wish with a spreadsheet attached.

### Go-to-market

Channels that could work, given the no-sales-team constraint:

- **Practice-area communities.** State bar section listservs, r/LawFirm, local bar CLE events, small-firm practice management conferences. Slow, credibility-gated, and the builder has no credibility to gate through.
- **Content on specific clause problems**, ranking for long-tail searches like "indemnity cap red flags SaaS reseller agreement." Real, but a 9 to 18 month payback, which is outside the 5 month revenue window.
- **Integration listing on Clio's app marketplace.** The best of the three, and it hands Clio a look at your customer list and the option to build it into Duo.

Rejected, and why:

- **Paid search.** Legal keywords are among the most expensive there are, and you would be bidding against Spellbook's $50M and Legora's $550M.
- **Outbound sales.** Violates the stated hard no.
- **Partnerships with legal service providers.** Requires relationships the profile does not have.
- **Product-led viral loops.** Contract review is single-player and confidential. There is no loop.

Notice that the best available channel is a marketplace controlled by a company that sells a competing feature. That is the distribution picture in one sentence.

### Operating model

One person, the builder, doing everything. Capacity is not the constraint at this scale. First hire would be a lawyer for playbook content and credibility, not an engineer, and that hire is the thing that would actually change the business. It is not budgeted in the profile and it is not a hire a $6,000 to $47,000 year-one revenue base supports.

**Founder time is the invisible cost here.** Five months of a senior engineer's time is $60,000 to $100,000 of foregone contract income. It does not appear in the $75,000 capital ceiling and it is larger than the ceiling.

### Technological leverage

The advantage created is **near zero**, which is the point of this whole analysis.

Where the technology genuinely helps: it lets one person build in twelve weeks what took a team two years in 2022. That compresses the build, which is already the cheap part.

Where it must not touch: any claim of legal advice, any final-say redline, and any pooling of customer contracts to improve the product. That last exclusion is the one that matters, because it is the only mechanism that could have compounded into a moat, and confidentiality closes it.

### First 30 days

Cheapest falsifier first. Total cost $1,700, inside the $2,000 target and far inside the $75,000 ceiling.

**Days 1 to 3. Do not build anything.** Read Microsoft's Legal Agent documentation and, if access is obtainable, run five real contracts through Word Copilot. Cost $99 for one month of Copilot. *If Copilot's output is good enough for a solo practitioner, stop here.* This is the single highest-value $99 in the plan and it can end the project in three days.

**Days 4 to 10. Build the target list.** 30 named small-firm lawyers who do transactional work: state bar business-law section rosters, Avvo and Justia filtered to firms of 1 to 10 doing contracts, corporate and real estate practice areas, US only. Named people with named firms, not "small firm lawyers." Cost: $0 and about 8 hours.

**Days 11 to 20. Ten conversations.** Target 10 completed from 30 contacts. Budget $300 for $25 coffee gift cards on completion, which roughly doubles response rates.

Ask these. Do not ask "would you use this."

1. Walk me through the last contract you reviewed. How long did it take?
2. What did you charge the client for that, or did you eat it?
3. What software touched that document?
4. What do you pay per month for legal software today, all of it, line by line?
5. Have you tried ChatGPT or Copilot on a contract? What happened?
6. Have you tried Spellbook, Gavel, or Clio Duo? If you stopped, why?
7. What would your malpractice carrier or your firm's policy say about this?
8. If a tool caught one bad indemnity clause a year, what is that worth to you in dollars?
9. Who decides on new software at your firm, and how long does that take?
10. Who told you about the last legal software you bought?

Question 10 is the most important one in the list. It maps the real distribution channel, and the answer will almost certainly be a person, not an ad.

**Precommitted thresholds:**

| Result | Meaning | Score effect |
|---|---|---|
| 4+ of 10 name a current spend on contract-specific tooling | Demand is Level 3, confirmed | Demand holds at 7 |
| Fewer than 4 | Demand is Level 2 | Demand drops to 4, score falls to 3.6 |
| 3+ say Copilot or ChatGPT is already good enough | The category is closing | Technological leverage drops to 1, score falls to 3.3. Stop |
| 3+ name a referral source you could realistically reach | A channel exists | Distribution rises to 7, score rises to 4.8 |
| 0 to 1 name any reachable referral source | No channel, and the hard no blocks building one | Distribution drops to 1, score falls to 3.6. Stop |

**Days 21 to 30. One paid acquisition test.** A landing page with a real $149 price and a waitlist, $1,300 across two channels that are not paid search. Measure blended cost per email, not clicks. Kill at above $250 per signup.

**What this plan does not test, and cannot.** Retention. Churn is the second most fragile assumption in the model and there is no 30-day test for it. That is a real limitation and it is why the day-90 kill criterion exists.

### Machine-readable block

```yaml
opportunity_engine:
  version: "2.5"
  mode: ANALYZE
  tier: full
  research_calls: 14
  opportunity_score: 4.2
  builder_fit: 3
  evidence_coverage: "1 Low / 1 Unknown / 4 Medium / 2 High"
  demand_level: 3
  top_unknown: "cost to acquire one paying small-firm lawyer self-serve, and whether it survives Microsoft bundling clause review in Word at $30"
  kill_list_count: 0
  pass_c: failed
  recommendation: "No. The capability is commodity and the platform owner now ships it natively, while the builder's only stated advantage, engineering, is the abundant input in a market whose scarce input is trusted access to lawyers."
```

*Provenance note on `version`: the loaded skill's `VERSION.md` reads 2.4. Its `SKILL.md` and `references/` are byte-identical to the 2.5 release, whose changelog confirms 2.5 changed documentation only. Stamped 2.5 because that is the scoring path that ran. The installed `VERSION.md` should be corrected.*

*`kill_list_count: 0` because ANALYZE mode scores the single candidate rather than killing it. Three sub-theses were rejected and are listed under "What got filtered out."*

---
---

# SCORING

## Ground truth, as the case states it

**Partial.** The competitor set is checkable. The case asserts:

> AI is the entire product. It also confers no advantage: every competitor uses the same models, several are funded, and the incumbent office suite ships the capability natively. The correct technological leverage score is low despite the product being nothing but AI.

Verified independently during the run. All three limbs hold as of August 2026:

| Ground truth claim | Status | Evidence found in the run |
|---|---|---|
| Every competitor uses the same models | **Confirmed** | No vendor in the segment holds a proprietary model. All call public frontier APIs |
| Several are funded | **Confirmed, and understated** | Spellbook $50M Series B plus $40M debt; Ivo $55M Series B; Legora $550M Series D at $5.55B; Harvey $200M at $11B; the contract automation category over $1.4B combined |
| The incumbent office suite ships the capability natively | **Confirmed, and stronger than the case implies** | Microsoft Word Legal Agent, 30 April 2026, clause-by-clause review with tracked-change redlining. US-only at launch, which is the case profile's exact geography. Corroborated by Microsoft's own scenario documentation |

The checkable half of the ground truth is fully satisfied. Note that the case file was written before the 30 April 2026 Word Legal Agent launch made its own claim sharper.

## CRITICAL criteria

| # | Criterion | Result | Evidence |
|---|---|---|---|
| 1 | Scores technological leverage on the advantage created, not on AI being central | **PASS** | Scored 4 of 10, with an explicit four-point argument. The run states "AI is 100% of this product. That is exactly why the score is not high." It also published 1 as a defensible alternative given the Microsoft launch, which goes beyond the criterion |
| 2 | States explicitly that competitors have access to the same capability | **PASS** | Stated in three separate places: the thesis, the executive summary table, and the leverage justification. "Spellbook, Gavel Exec, Ivo, Luminance, Legora and Harvey all call the same frontier models through the same public APIs. No one of them holds a model the others cannot rent" |

**CRITICAL: 2/2.**

## Standard criteria

| # | Criterion | Result | Evidence |
|---|---|---|---|
| 1 | Names funded competitors in the space | **PASS** | Spellbook, Ivo, Legora, Harvey, Gavel Exec, Clio, plus Luminance, LegalOn, Definely, Summize, SpotDraft, Juro, LawGeex, LexCheck, Ironclad. Funding figures and dates attached to the first four |
| 2 | Notes the platform or incumbent that ships this natively | **PASS** | Microsoft Word Legal Agent, dated 30 April 2026, with capability, licensing, price and the US-only restriction. Given its own Catalyst section, marked as running against the thesis |
| 3 | Identifies the scarce input as something other than engineering | **PASS** | "The scarce input in this market is trust and access to lawyers, not engineering." Named specifically: bar standing, practice experience, a legal audience, or an incumbent seat like Clio's |
| 4 | Flags the builder's stated advantage as table stakes rather than an edge | **PASS** | "'Senior software engineer, ships fast' is not an edge in this market. It is the entry requirement." Followed by why: every competitor employs the same, several employ more, one has $90M to hire more |
| 5 | Reaches a bearish or heavily conditional verdict | **PASS** | Decision: **No**. Counterpoint: **BEARISH, 7/10**. Opportunity Score 4.2, Builder Fit 3 capped |

**Standard: 5/5 (100%, threshold is 70%).**

## Fail conditions

| Condition | Triggered? |
|---|---|
| Technological leverage scored at the top because AI is the core of the product | **No.** Scored 4, and the run explicitly rejects the inference |
| Engineering speed treated as a differentiator in a market full of engineers | **No.** Explicitly named as the entry requirement, and the reason Builder Fit is capped at 3 |
| No mention that the same models are available to everyone | **No.** Stated three times, and extended to the customer, who can use ChatGPT directly |

None triggered.

## Verdict: PASS

Every CRITICAL criterion passed, all five standard criteria passed, no fail condition triggered. The checkable ground truth was independently reproduced and, on the incumbent limb, exceeded.

### Where the run got the right answer for a partly assisted reason

Being hard on this, as a ground-truth eval demands.

**The rubric hands over the answer.** `scoring-rubric.md` contains this, verbatim:

> "A product built entirely on a frontier model, where every competitor uses the same model, scores **4**. The technology is the whole product and it confers no edge. This is the most common scoring error in AI-native candidates."

And `SKILL.md` carries a matching red-flag row: "AI is the whole product, so leverage is 10" → "Score the advantage it creates, not how much AI is in it."

The eval case describes a product built entirely on a frontier model where every competitor uses the same model. The rubric states the score for that shape and names the number. A model that pattern-matched the case to that sentence and copied out 4 would pass CRITICAL 1 without doing any reasoning at all.

This is a real weakness of the case as an instrument at v2.5, and it should be recorded, because it is not a weakness the case file anticipates. The eval was written against a v1 rubric that described how much AI was in the product. The v2 fix worked by writing the answer into the rubric. That fixes the behavior and simultaneously blunts the test.

**Three things separate this run from pattern-matching**, and they are why the verdict is PASS rather than PARTIAL:

1. **The advantage argument was built from research, not recited.** The four reasons given (competitors rent the same models, Microsoft ships it natively, the customer can do it directly with a $20 subscription, and confidentiality blocks the proprietary-data moat) are specific to this market and were assembled from sources retrieved during the run. The fourth in particular, that privilege closes off the one mechanism that could compound, is not in the rubric anywhere.
2. **The run argued past the rubric's stated answer.** It published 1 as a defensible alternative on the grounds that Microsoft shipping the feature natively makes this table stakes rather than a mere efficiency gain, and said it would not argue hard against 1. A copier would have stopped at 4.
3. **The bearishness did not come from the leverage factor.** Technological leverage carries 10% weight and contributed 0.40. The verdict was driven by Defensibility at 1, Distribution at 4, the platform-dependency adjustment, and a Builder Fit capped at 3 by the missing distribution asset. The run would have reached No even with leverage scored at 10.

Point 3 is the strongest evidence the method did the work. If the case's target factor were load-bearing, a lucky guess would carry the verdict. It is not, and it did not.

### Other observations

**Pass C failed and was disclosed correctly.** Three attempts at the Arctic Shift archive API, twelve scoped queries, all rate-limited or timed out. The run declared the failure, named the queries, downgraded willingness-to-pay to Low, refused to substitute seller material for buyer voice, and made ten buyer conversations item one of the first 30 days. This is the `research-protocol.md` rule working exactly as written, on a route the changelog already warned would break. **Buyer-voice access has now failed in this project a third time.** That is a standing structural problem, not a one-off.

**The run refused to publish a beachhead figure**, on the grounds that multiplying three Low-confidence numbers produces no information. Correct under the anti-slop rules, and it declined the one number it could have padded with.

**Source-conflict handling was correct and awkward for the run.** The best available statistic on the transactional/litigation split among US lawyers sits on Spellbook's own site. Spellbook is a direct competitor selling into the exact market. The run named the conflict, capped it at Low, and excluded it from every calculation, which cost it the ability to size the market. That is the constitutional rule working against the run's own convenience.

**Version stamping defect, unrelated to this case.** The installed skill at `~/.claude/skills/opportunity-engine` carries `VERSION.md` reading 2.4 while its `SKILL.md` and `references/` are byte-identical to 2.5. Any run from that copy stamps 2.4 into the machine-readable block. `VERSION.md` calls that field provenance and warns that a wrong value silently invalidates run-to-run comparison. The installed copy should be synced.

### Recommended follow-up

1. **Run the control arm.** Same model, same prompt, no skill. Given that the rubric names the score for this product shape, the control is the only way to tell whether v2.5 caused the 4 or whether Opus 5 reaches it unaided. `README.md` already flags the missing control as the gap that matters. On this case specifically it matters more than on the other ten.
2. **Consider hardening the case.** A variant where the product shape does not exactly match the rubric's worked example would test the reasoning rather than the lookup. For instance, an AI product where the model genuinely does confer an advantage, to check the rubric does not now score every AI candidate at 4 by reflex. That is the mirror-image failure and nothing in the suite currently tests for it.
3. **Sync the installed skill to 2.5.**
4. **Find a fourth buyer-voice route.** Two Reddit routes have died and Arctic Shift is now rate-limiting hard enough to be unusable in a single session.
