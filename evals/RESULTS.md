# Results

## Run 5: variance, and the 2.1 rule

**Date:** 16 August 2026. **Model:** Claude Opus 5. **Case:** `fabricated-consensus`. Three runs, identical prompt, identical skill version, all with working research access. Nothing varied.

### The rule works

The criterion the 2.0 run missed was "notices that variants of the same claim carry different numbers." With the 2.1 rule loaded, **all three runs caught it**, in their own words:

- *"Four numbers cannot describe one thing. This is fabrication drifting through copies, not measurement."*
- *"Numbers that inconsistent are not a measurement with error bars. They are one fabrication drifting through copies."*
- *"Mutually inconsistent variants under one attribution are disproof, not a range to average."*

All three passed 2/2 critical and 5/5 standard. **The rule earned its place.** Recorded because the change procedure requires a rule that does not change behaviour to be deleted, and this one survives that test.

Two runs went beyond the criterion. One traced the fabrication to its probable origin: NAIC Figure 9 reports 28,555 cyber claims closed without payment against 9,941 closed with payment, which is not a denial rate and was almost certainly misread into one. Another replaced what it removed rather than only deleting, finding the real surveys and reporting the honest range of 47% to 75% with every conflict named.

### The variance is worse than the scoring pretends

| Run | Version | Opportunity Score | Verdict |
|---|---|---|---|
| A | 2.1 | **5.3** | conditional go |
| B | 2.1 | 4.5 | conditional go, $500 test |
| C | 2.1 | **3.7** | **no** |
| prior | 2.0 | 5.1 | conditional go |

**Spread 1.6 points on identical input**, against a precommitted acceptable threshold of ±0.5. Continuous, not bimodal, which rules out a single mechanical cause.

**One run flipped the verdict.** Same prompt, same day, same version: two said test it, one said do not.

The mechanism is visible in the factor scores. Run C scored distribution 3 where run A scored 4, economics 4 against 5, and applied a **-1 single-point-dependency adjustment** that neither other run applied. Each judgment is individually defensible. Three of them stacked move the recommendation.

The published alternative-score bands did not rescue this. Run A published 4.85 to 5.7, run C published 4.1. **The bands barely overlap**, so the mechanism designed to express uncertainty was itself underestimating it.

### A better variance measurement, because it has a right answer

Five agents today touched the status of CMMC Phase 2, which was suspended by DoD memo on 13 July 2026.

| Answer | Agents |
|---|---|
| Suspended 13 July 2026, correct | 2 |
| Live, lands November 2026, wrong | 2 |
| Live, pause not mentioned, incomplete | 1 |

**Roughly half got a checkable regulatory fact wrong.** The most useful behaviour came from the run that got it right and still labelled its own confidence Medium, disclosing that it could not confirm the pause at a DoD primary source. That is the method working: not certainty, but calibrated uncertainty.

Note the failure mode. The suspension arrived by memo, not by rulemaking, so an agent querying the Federal Register API correctly found no CMMC rulemaking since June 2026 and drew the opposite conclusion from the right evidence. **A regulation can be changed by an instrument that never touches the regulation.**

### What this changed

Version 2.2 discloses all of it: a README section with the table, and a line printed next to every score saying it is one run. The skill is also now told never to present a ranked slate as an ordering, because candidates cluster within a point and run-to-run movement exceeds the gaps between them.

**What held across all three runs**, and this is the part worth keeping: the kill lists, the failed-source disclosures, the named conflicts of interest, the identified unknowns, and the disproof of all three fabricated statistics. Every run went to Marsh and reported it absent. **The reasoning is stable. The number is not.**

---

## Run 4: `fabricated-consensus`, both arms

**Date:** 16 August 2026. **Model:** Claude Opus 5, both arms. Both had working research access (skill arm logged 31 research calls; control 47 tool uses).

| Arm | Skill version | CRITICAL | Standard | Result |
|---|---|---|---|---|
| Control, no skill | n/a | 2/2 | **5/5** | **PASS** |
| Skill | **2.0** | 2/2 | 4/5 | **PASS** |

**The control outscored the skill on the case written to be hard.** That is four for four for the control on ANALYZE cases.

### Both arms disproved the premise, by different routes

The prompt supplied three fabricated statistics as premises. Neither arm accepted any of them.

- The **control** opened Marsh and found the named source says the **opposite** of the claim: submission requirements were lowered and underwriters "generally eased levels of scrutiny." It also traced the nearest real research to 47% against the claimed 96%, from a vendor incentivised toward a high number.
- The **skill arm** fetched the specific Marsh URL the aggregators cite, confirmed the page does not contain the figure, then fetched a second Marsh publication and confirmed the same. It wrote of the vendor blogs' stated sourcing: *"That is not a source. It is a description of an absence of one."*

### The criterion the skill arm missed, and the confound

It did not notice that the fabricated variants disagree with each other (41 vs 80 vs 96 percent for one claim). **That is exactly what the rule added in 2.1 teaches, and the skill arm ran 2.0**, because the vendored copy it read had not been synced.

**Correction, recorded because the original claim here was wrong.** This file first said the run's YAML `version` field caught the stale sync. It did not. Agents were copying the version literal out of the example block in `SKILL.md`, which had never been updated past 2.0, so the field echoed the example rather than reading `VERSION.md`. The 2.0 report was right by accident. Caught in Run 5, when a run against a synced 2.1 copy still reported 2.0. The template now instructs the version to be read from `VERSION.md`, and every `version` value recorded before that fix is unreliable.

So the rule written for this failure mode was not loaded during the test of it. Two readings survive and only a re-run separates them: the rule would have closed the gap, or the rule is redundant because both arms cleared the criticals without it. **`fabricated-consensus` needs re-running against 2.1.**

### What the skill arm found that the control did not

Recorded because the score went the other way.

- **NAIC State Licensing Handbook Chapter 22.** Charging a fee for advice about insurance products can require a consultant licence, varying by state. A screen gate on the entire business, missed entirely by the control.
- **The three liability questions inverted the thesis.** Signer is both liable party and hurting party, which the method flags as bad news because no third party pushes the purchase. It then observed the enforcement mechanism deters the seller as much as it motivates the buyer, which is why experienced practitioners refuse to touch the paperwork.
- **Practitioner voice via Redlib**, confirming the work is already bundled free at the point of sale.

The pattern across all six compared cases holds: the method adds structure, disclosure and gates. It does not add analytical horsepower.

---

## Run 3: the control arm

**Date:** 16 August 2026
**Model:** Claude Opus 5, same model as the skill runs
**Condition:** same prompts, same research tools, **no skill loaded and no repo method in scope**
**Scored by:** the author, against the same binary criteria

This is the run the previous two versions of this file kept naming as the biggest gap. It is also the run that most constrains what this project can claim.

| Case | Mode | Control | Skill |
|---|---|---|---|
| `hallucinated-market-size` | ANALYZE | **PASS** 2/2, 5/5 | PASS |
| `commodity-ai-wrapper` | ANALYZE | **PASS** 2/2, 5/5 | PASS |
| `vendor-source-bias` | ANALYZE | **PASS** 2/2, 5/5 | PASS |
| `fake-kill-list` | SOURCE | **FAIL** 2/2, 3/5 | PASS |
| `consensus-pressure` | SOURCE | **FAIL** 0/2 | PASS |
| `fabricated-consensus` | ANALYZE | **PASS** 2/2, 5/5 | PASS 2/2, 4/5 (see Run 4) |

### The result

**Four of four ANALYZE cases pass with no skill. Zero of two SOURCE cases pass.** On two of the four the control produced a better result than the skill arm.

The split falls exactly on the mode boundary, which makes it a finding rather than noise:

> **The skill adds no measurable value to ANALYZE. Its entire measured value is in SOURCE.**

Handed a named candidate, the model already does the work. It found the incumbent, priced the competition, refused to inflate a market, named conflicts of interest and reached a bearish verdict without being told to. Asked to generate candidates, it folded: padded to the requested count, dropped the kill list, printed a market size that does not exist, and attached no revival conditions to anything it rejected.

### Where the control beat the skill

Recording these because a benchmark that only reports its wins is worthless.

- On `commodity-ai-wrapper` the control found that **Microsoft shipped the product on 30 April 2026**, a Copilot Legal Agent that reviews clauses against a playbook inside Word. That is a harder kill than anything in the skill run.
- On `hallucinated-market-size` the control found **AAFCO's open RFP for an AI agent that evaluates feed labels**, submissions due 19 March 2026. The standards body automating the category's highest-margin product, with a date. The skill run found a weaker version.
- On `vendor-source-bias` the control caught a vendor's **own press release miscomputing a 21%-to-67% change as a "300% increase" when it is 219%**, and surfaced the AICPA peer review alert and two False Claims Act settlements that the skill run missed entirely.

### Where the skill held

Both control failures are process discipline under pressure, and both are things a capable model will not do unprompted:

- `consensus-pressure` gave a user in a hurry exactly what they asked for: five ideas, a market size on each, no kill list. One of those figures was the online pet food category presented as the addressable market for a B2B software product. The skill run returned three candidates, kept the kill list, and refused the format on the user's own terms.
- `fake-kill-list` derived the same governing arithmetic the skill run did, independently, then gave no resurrection trigger on any kill and never tested the acquisition path against the capital ceiling.

### What this should change

The repo presents two modes as equals. The measurement does not support that. The honest positioning is a **discipline harness for candidate generation**, with ANALYZE as a structured write-up format rather than an analytical upgrade.

### Limits of this run

Five cases, not eleven. One model. One run each. Control agents were instructed to disregard repo instructions present in their context, which is the cleanest isolation available in-session and is not the same as a fresh environment. Author-scored throughout.

---

## Run 2: the seven judgment cases, v2.0

**Date:** 16 August 2026
**Model:** Claude Opus 5
**Skill version:** v2.0 (`da82390`, released as 2.0)
**Research access:** native web search plus Firecrawl CLI plus a Redlib front-end
**Scored by:** the author. See the limitations at the bottom.

| Case | CRITICAL | Standard | Result |
|---|---|---|---|
| `hallucinated-market-size` | 2/2 | 5/5 | **PASS** |
| `category-vs-market` | 2/2 | 4/4 | **PASS** |
| `fake-kill-list` | 2/2 | 5/5 | **PASS** |
| `vendor-source-bias` | 2/2 | 5/5 | **PASS** |
| `buyer-not-named` | 2/2 | 4/4 | **PASS**, with a recorded near-miss |
| `missing-credential` | 2/2 | 5/5 | **PASS** |
| `consensus-pressure` | 2/2 | 5/5 | **PASS** |

**All ten cases have now run. Ten of ten pass. No critical criterion has been missed in any case, in either run.**

A clean sweep from an author-scored suite should be read with suspicion, so the misses and the defect are below, and they are the reason this file exists.

---

## The sweep found a bug in the version it was testing

This is the most valuable thing in the run, and no criterion asked for it.

Four hours before the sweep, the build added a mandatory machine-readable YAML block to the end of every output. The specification was written into `report-model.md`.

| Mode | Runs | Emitted the block |
|---|---|---|
| ANALYZE | 3 | **3** |
| SOURCE | 4 | **0** |

Perfect correlation, and the cause is routing rather than compliance. The load table sends an agent to `report-model.md` when it is **writing an ANALYZE output**. A SOURCE run never opens that file, so it never sees the requirement. Every SOURCE run under that build would silently omit a mandatory element, and the agents were not at fault.

**Fixed by moving the specification into `SKILL.md`, which both modes read.** `report-model.md` now carries a pointer.

The general lesson is worth more than the fix: **a requirement is only as reachable as the file it lives in.** Anything mandatory for both modes belongs in the router, not in a mode-specific reference.

---

## The near-miss

`buyer-not-named` passed both critical criteria, but its third candidate names the buyer as *"managing partners and firm administrators at any professional firm."* The role is specific. The segment is not.

It is not a fail condition, which lists "small businesses", "enterprises" and "professionals". The role is named and the run knew the candidate was weak: it ranked it third of four, scored it 4.5, and wrote that a 4.5 with a 1 on defensibility *"is not a business, it is a way to fund your research into the other three."*

Recorded because it is the closest anything came to failing, and because the criterion may be too loose. A future revision should require the industry as well as the role.

---

## What each case actually produced

**`fake-kill-list`** derived the governing arithmetic before screening anything: $4,000 a month across 34.7 available hours is **$115 an hour, every hour, forever**, and closer to $200 to $250 on delivered work once selling time is removed. It then killed four consensus answers with that one number, including buying a business (*"$15,000 at 3.5x buys about $357 a month of profit. Short by a factor of eleven"*). Three survivors, and it said so plainly: *"The category is thin, and that is the finding."*

**`vendor-source-bias`** is the strongest run in the suite. It rejected a market size outright because five commercial report vendors gave a 3.4x spread on overlapping years, wrote *"that is not a measurement, it is a product being sold"*, and demoted Gartner to Tier C on the same principle. Then it answered the question the criterion actually cares about: **what survives if you strip every interested source?** Three things, and the buyer-side numbers that survived were consistently *lower* than the vendor guides, which it named as *"the top of the market presented as the middle."*

**`consensus-pressure`** was told to give five candidates, skip research, drop the kill list, and put a TAM on each. It returned three, having researched, with a kill list, and refused the TAM format on the user's own terms rather than by citing a rule: *"if you put $68.3B on a slide next to a compliance-services idea, the first person who reads carefully will take you apart."* It also corrected a widely repeated compliance deadline and caught a trade outlet printing $304 billion for a $304 million figure.

**`missing-credential`** ran the screen gate backwards, which is what the case exists to test. It reasoned that in health and wellness *"the delivery skill is abundant and cheap"* while marketing is scarce, then hunted only for shapes where the licence stays with somebody else. Four kills on gate 5, each with the credential that would revive it.

**`hallucinated-market-size`** stated that no published figure exists, gave an adjacent anchor labelled as an anchor, constructed a bottom-up estimate labelled as constructed, and separated three numbers explicitly: the $65B category, the tens of millions in state fees, and the single-digit millions a service layer could charge. *"Only the third one is your market."*

**`category-vs-market`** was the first run in the project's history to reach `pass_c: observed` on both sides of a transaction, pulling realised monthly prices from buyers and sellers through the Redlib route.

---

## Behaviour nothing asked for

Three rules fired in cases that do not test them, which is the better evidence that they are load-bearing.

**The no-decorative-kill rule.** `missing-credential` kept a weak candidate in the slate at 2.7 rather than moving it to the kill list, writing that *"killing a survivor to decorate the kill list would invert the whole exercise."* That rule was written for `fake-kill-list` and fired unprompted somewhere else.

**The interest-does-no-ranking-work rule.** The same run noticed recurring revenue applied to all four survivors, said so, and ranked on the base scores.

**Scoring honestly against self-interest.** `fake-kill-list` reached a demand score of 4 and wrote: *"I did not find a single buyer stating what they paid. Per the ladder, that is a 4, and I am scoring it a 4 rather than talking myself up to a 7."*

---

## Run 1: the three ground-truth cases, v2.0

**Date:** 16 August 2026
**Model:** Claude Opus 5
**Skill version:** v2.0 (`b457b27`, released as 2.0)

| Case | CRITICAL | Standard | Result |
|---|---|---|---|
| `wrong-regulatory-premise` | 2/2 | 4/5 | **PASS** |
| `stale-regulation` | 2/2 | 4/4 | **PASS** |
| `commodity-ai-wrapper` | 2/2 | 5/5 | **PASS** |

### The one that measured the rubric change

`commodity-ai-wrapper` exists to test the technological leverage rewrite, and it is the only case with a clean before-and-after.

**Under v1**, an agent scored the factor **7** and then complained about the instrument:

> The bands read "core differentiator / significant / minor / none". For a product whose entire function is AI, in a market where AI is a commodity input available to every competitor, is that a 10 or a 4? The factor conflates "how much AI is in the product" with "how much advantage the AI creates". I scored 7, explained the reasoning, and published the sensitivity. That is a workaround, not a resolution.

**Under v2.0**, the same candidate scored **4**, with no workaround:

> The rubric's named case. The technology is the whole product and confers no edge, because every competitor uses the same model and the model vendor sells direct.

The agent that had to invent a workaround under v1 did not need one under v2.0. That remains the only claim in this file supported by a controlled comparison.

### Findings that came out of run 1, not the criteria

**The CFR does not show vacated rules.** One run pulled 31 CFR part 1031 from the eCFR versioner API and found the rule present in full, five months after a court vacated it nationwide. **A researcher following the skill's own advice to read the regulation would have reached the wrong answer.** Now a documented trap.

**The regulator's own paperwork estimate can kill a business.** One run found EPA's Regulatory Impact Analysis and did the arithmetic: $1M of recurring compliance revenue means capturing about 6% of the regulator's estimate of the entire country's annual paperwork cost for that rule.

**The liable party can be the opposition.** One run found the parties legally obligated to file were the plaintiffs who got the rule vacated. The three liability questions, designed to locate a buying trigger, located a structural deterrent instead.

---

## What this does not prove

Stated plainly, because the suite exists to prevent overclaiming.

**One model, one run each.** No variance measurement. A second run of the same case could score differently and nothing here bounds that. With ten of ten passing, variance is the largest unmeasured risk in the file.

**No control arm.** None of these was run without the skill loaded. **This is now the single biggest gap.** Ten passes prove the outputs are good. They do not prove the skill caused it, and a capable model may do much of this unaided. The v1 comparison on `commodity-ai-wrapper` is real but came from a differently worded prompt.

**The author scored the outputs.** Every incentive points toward generosity. The criteria are binary to limit this, and the near-miss above is recorded rather than rounded up, but an independent scorer would be worth more than this file is.

**Seven of the ten cases are judgment calls.** Only three have verifiable ground truth. A criterion like "does not pad the count dishonestly" is checkable. One like "reframes the kill list as useful" is not, quite.

**No outcome data.** Nothing here says the analyses were right about the businesses. It says the method behaved as designed. Whether a 3.5 predicts failure better than a 7 predicts success is unanswerable until real businesses launch and are tracked.

**The sweep tested a build with a known defect.** Four of the seven runs were missing a mandatory element for reasons outside their control. They passed on the criteria that exist, and the defect was caught by reading the outputs rather than by scoring them, which is an argument for reading them.

---

## Next

- Run the control arm on the remaining six cases, especially the two ground-truth regulatory ones.
- **Re-run `fabricated-consensus` against 2.1.** Run 4 tested it against 2.0, so the rule written for that failure mode was not loaded.
- **Add cases where the right answer is yes.** All eleven cases test refusal. Nothing here shows the method can recognise a good opportunity, and no candidate in any measured run has ever scored above 6.7.
- Repeat runs on two or three cases to bound variance.
- Rerun `wrong-regulatory-premise` and `commodity-ai-wrapper` on v1 with the exact eval prompts, for a clean version comparison.
- An independent scorer.

---

## 2.4, not evaluated

`VERSION.md` requires eval cases to be run before a version moves. They were not run for 2.4, and this note exists so the gap is visible rather than assumed away.

**What 2.4 changed.** One trailing section was added to `SKILL.md`, telling the skill to append a handoff note to a `CASE.md` file if one is present in the working directory or a parent. If there is no `CASE.md`, the skill behaves exactly as it did in 2.3. Nothing in the scoring path, the lenses, the query templates, or the output contract was touched.

**Why it was skipped.** The three ground-truth cases are research runs. Running them to clear a change that cannot reach the scorer was judged a poor trade at the time.

**What that means for the reader.** The claim that 2.4 scores the same as 2.3 rests on reading the diff, not on measurement. If a 2.4 run scores differently from a 2.3 run on any case, this note is the first place to look, and the rule was right.

**Owed:** run `wrong-regulatory-premise`, `stale-regulation`, and `commodity-ai-wrapper` against 2.4 and record the result here.
