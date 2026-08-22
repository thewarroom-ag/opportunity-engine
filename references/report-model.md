# Report model

What ANALYZE produces, by tier.

**The section tables below are patterns, not checklists.** Reread the "let the data lead" rule in `SKILL.md` before using them, and read the section on dropping sections at the bottom of this file. A filled table is not the goal.

---

## Quick Scan

Seven blocks. Answers one question: is this worth a real look?

1. **Thesis.** One sentence.
2. **Catalyst.** What changed, and when. Dates matter.
3. **Market.** Size and growth, or unknown with the reason.
4. **Competitive picture.** Who is already there.
5. **Economics snapshot.** Price, margin, cost to start.
6. **Score.** With the arithmetic.
7. **Biggest risk.** The one that kills it.

Then a verdict: look harder, or drop it.

---

## Full Analysis (default)

Two documents, in this order.

### Document 1: Opportunity Analysis

Answers "should we do this?"

| Section | Contents |
|---|---|
| **Thesis** | One paragraph. What changed, who hurts, what you sell |
| **Executive summary** | The structural picture. Tables beat prose here |
| **Catalyst** | The event, dated. Why now. Say if it runs against you |
| **Market** | Reachable economic pool, not headline TAM. See below |
| **Competitive landscape** | Named players, pricing, positioning, weakness, and the topology from `competition-and-moats.md` |
| **Where the gap is** | The specific opening, and why incumbents leave it |
| **Why is this still available** | Mandatory. See below |
| **Entry analysis** | Build or buy. Capital and time to first collected revenue |
| **Unit economics** | Ranges, not point estimates, plus the scenario table. See below |
| **Risks** | Real ones only, each with severity and mitigation |
| **Regulatory** | Only if it applies. See the liability rule below |
| **What got filtered out** | The kills, with reasons |
| **Score** | Three numbers: Opportunity, Builder Fit, Evidence Coverage. Never one |
| **Takeaways** | Numbered. What a reader must remember |
| **Profile fit** | Against the Builder Profile. Include where it fits badly |
| **Verification table** | Every claim, source, tier, confidence. Failed attempts disclosed |
| **Counterpoint** | See below |
| **Sources** | Links |

### Document 2: Execution Plan

Answers "how do we do this?"

| Section | Contents |
|---|---|
| **Decision** | Go, conditional go, or no. Recommended play. Kill criteria with dates |
| **Offer specification** | What you sell, priced, with the deliverable named |
| **Path to $1M ARR** | Bottom-up model. Every assumption stated and ranked by fragility |
| **Go-to-market** | Channels that work here. Name the ones you rejected |
| **Operating model** | Who does the work. Capacity. First hire and when |
| **Technological leverage** | The advantage it creates, if any. Where it must not touch |
| **First 30 days** | Numbered, costed, cheapest falsifier first. Carries the demand validation plan. See below |
| **Machine-readable block** | Fixed format, last thing in the output. See below |

**Offer comes before revenue.** You cannot model revenue for a product you have not specified. This ordering is not stylistic.

### Why is this still available

**Mandatory for every candidate you rank in the top three.** One paragraph, and it kills more weak theses than any other section.

> If this is as good as the analysis says, why has nobody taken it?

Acceptable answers are specific and dated:

- The enabling technology or cost curve only recently crossed viability.
- A regulation changed, and the date is on the record.
- Incumbents are structurally unable to serve this niche, and you can say why.
- The market was too small until something changed its size.
- Distribution shifted and the old route stopped working.
- The work is unglamorous, operationally painful, or requires field labor that software companies will not do.
- Organizational incentives at the incumbents point away from it.

One answer must stay on the table every time:

> **Somebody already did solve it, and the thesis is wrong.**

If you cannot answer this convincingly, say so. "No good explanation found for why this is unclaimed" is a finding, and usually a bearish one.

### Sizing: reachable pool, not headline TAM

A large category number tells you almost nothing about what a new entrant can reach. A $200M niche can carry an excellent $20M business. A $100B market can be functionally closed.

Give four figures where you can, and say which are constructed:

| Figure | What it is |
|---|---|
| Category size | The published number, if one exists. Context only |
| Serviceable | The slice your actual product and geography could serve |
| **Beachhead** | The first buyer segment you could realistically reach. **This one carries the decision weight** |
| 36-month obtainable | Realistic revenue under credible distribution and capacity assumptions |

Then: **reachable buyers times realistic annual spend.** That number, not the category, is what the business lives inside.

If the category figure is the only one available, say the others are unknown rather than presenting the category as the opportunity.

### Ranges, not point estimates

Uncertain inputs get ranges. A single number implies a precision the research does not support.

Not `CAC = $450`. Instead: **CAC likely $300 to $900, and here is why the range is that wide.**

Every ANALYZE at Full tier or above carries a scenario table:

| Metric | Bear | Base | Bull |
|---|---|---|---|
| Customers, year 1 | | | |
| Average revenue per customer | | | |
| Revenue | | | |
| Gross margin | | | |
| Acquisition cost | | | |

Then one line, and it is the most useful sentence in the model:

> **Which single variable, if it comes in at the bear case, kills this?**

That is the assumption to test first, and it belongs at the top of the first 30 days.

### The demand validation plan

**Required whenever demand scored below Level 4**, which is most of the time. It goes inside First 30 Days rather than in a section of its own, because it is the first thing to do, not a separate exercise.

Desk research tops out at Level 3. Levels 4 and 5 need contact with a human. So when the analysis says willingness to pay is Low or Unknown, the plan has to make that testable rather than leaving it as a caveat.

Five parts:

1. **Eight to twelve questions a real buyer can answer.** Not "would you use this." Ask what they do now, what it costs them, what they already pay, and what they tried before.
2. **A named target list.** Ten to thirty people, by role and by where you reach them. "Facility managers at multi-site grocery" is a list. "Small business owners" is not.
3. **Thresholds, decided before you start.** "Four of ten confirm they pay for this today, or the thesis is wrong." Precommitting stops the goalposts moving once you like the idea.
4. **Cost and calendar time**, which must fit inside the profile's constraints. If the cheapest honest test costs more than the builder can spend, say so, because that is itself a finding.
5. **What each result does to the score.** Which factor moves, and by how much, under each outcome.

The target is a plan that falsifies the thesis for **under $2,000 and inside 30 days**. If you cannot design one, say why. Some theses genuinely cannot be cheaply tested, and that belongs in the risks.

### The machine-readable block

Specified in `SKILL.md`, because both modes need it. Close every output with it.

### Where the verdict goes

**One verdict, in the Decision block of Document 2.** Go, conditional go, or no. That is the answer to the user's question.

The counterpoint's BULLISH, CAUTIOUS, or BEARISH is a **separate judgment about the evidence**, not a second verdict about the opportunity. It is allowed to disagree with the Decision, and when it does, that disagreement is useful: a conditional go with a bearish counterpoint means "worth testing cheaply, expect it to fail."

Do not put a third verdict in the executive summary. State the score and the decision there, and point at the Decision block.

---

## Deep Dive

Full Analysis, with three changes. Nothing else moves.

| Change | Where |
|---|---|
| **Competitor teardowns**, 3 to 5 | New section, straight after Competitive landscape |
| **Comparable peers**, conditional | New section, straight after the teardowns. See below |
| **Hostile counterpoint** | **Replaces** the standard Counterpoint section, same position |

A teardown covers: offer, pricing, proof, operations, moat, and weakness. The weakness line is the one that matters, because it is where your entry is or is not.

**Include a failure teardown when one exists.** A funded competitor that died in this exact market tells you more than three that are alive. Cover what it had, what happened, and what the lesson is for someone with less capital.

---

## Comparable peers (conditional)

Individual practitioners or small teams already at $500K to $2M in the same vertical.

**Include only when all of these hold:**

- It is a service business where individuals or small teams reach that scale
- You **found** 3 or more real people
- Each is **verified against 2 independent sources**
- Revenue can be estimated from client count times published pricing

### What "found" and "independent" mean

Both terms get stretched under pressure. Pin them down.

**Found means you opened a source about them.** Not that a search result mentioned their name and title. A name in a snippet is a string, not a person.

**Independent means a different author, not a different URL.** For a solo practitioner almost the entire public footprint is self-published, so this needs a worked example:

| Counts as one source | Counts as a second source |
|---|---|
| Their own website | A client case study on the client's domain |
| A second site they also own | A trade-press article about them |
| Their own LinkedIn | A directory listing with detail they did not write |
| Their own podcast appearance | A named engagement corroborated by the other party |

Two domains owned by the same person is one source.

**Expect this test to fail often, and let it.** In testing it failed three times out of three, because LinkedIn is not retrievable and solo practitioners rarely publish pricing. That is the rule working. A section that fires rarely is better than one that fires with invented numbers attached to real people's names.

**Omit entirely when:**

- It is a product business
- The market is only large firms
- You found fewer than 3 verifiable peers

The first clause usually settles it. A SaaS is a product business, and its customer counts are not observable from outside, so the fourth clause fails too.

**Do not pad this section.** If you cannot verify three, write one line saying you omitted it and why, then move on. A weakly sourced peer list is worse than none, because readers act on it.

### Two different failures, two different answers

The conditions above collapse two unrelated problems into one outcome. Separate them.

**Identity failure.** You cannot confirm these people exist or do this work. Two or fewer clear the two-source test. **Omit the section.** A list of maybe-real people is worthless.

**Revenue-opacity failure.** Conditions 1 to 3 pass. The people are real, named, and verifiable. Only condition 4 fails, because the segment publishes no pricing, no client counts, or neither.

In that second case, **include the peers with an explicit "no revenue estimate available" column.** Name each one, cite the two sources, state what they do and who they serve, and leave revenue blank. Never infer it from an hourly-rate band and a guessed utilisation.

Then say what the opacity itself tells you:

```
Four identifiable people run solo practices in this segment. None
publishes pricing or client counts, and neither do the two most
visible firms. That opacity is itself a finding: price discovery
in this market happens in the sales conversation, which is why
published floors and realised prices diverge.
```

A segment where nobody publishes anything is a segment where a newcomer cannot benchmark and an incumbent can hold price. That is worth knowing, and the old rule threw it away.

### Shape benchmarks are not peers

You will sometimes find a useful comparable in the **wrong vertical but the right business shape**: a bootstrapped software business that reached $1M ARR solo, a one-person consultancy at $800K in an unrelated field, a median time-to-$1M for the business type.

These are real and useful. They are not peers, and they must never be dressed up as one.

**Put them in Path to $1M ARR as a labeled sanity check**, with the confidence level and the reason they are not a peer:

```
Shape benchmark, not a peer: median micro-SaaS reaches $1M ARR in
about 2 years 9 months (Tier C aggregator, Low confidence).
Different vertical. Included as a pace check on the model above,
not as evidence about this market.
```

---

## The liability question

For any opportunity with a regulatory catalyst, answer three questions explicitly in the Regulatory section:

1. **Who bears the legal obligation?**
2. **Is that the same party who feels the pain?**
3. **Who enforces fastest?**

When the answer to the second is no, say what that means for go-to-market. The liable party is the customer. The party with the relationship is the channel.

When the answer to the second is **yes**, say that too, and note that it is unusual. It usually means no third party is pushing anyone to buy, which is worse for the business, not better.

Question three decides the pitch. The fastest enforcer is often a platform or a manufacturer, not the regulator. And sometimes the fastest enforcer creates a **deterrent** rather than a trigger, which inverts the whole thesis. Say so when it does.

---

## Counterpoint

Argue against the analysis you just wrote. Do it properly.

Cover:

- **Circular evidence.** Which claims trace back to parties selling the solution? Then say what survives if you strip every commercially interested source out. If nothing survives, that is the finding.
- **Weakest number carrying the most weight.** Which figure is doing the most work on the least support?
- **The unearned leap.** Where did "this is true" become "so people will buy"? Where did a preview become a certainty?
- **Underrated competitors.** Who did you dismiss too fast, and could the same evidence read the other way?
- **What would change the verdict.** Name the specific evidence, in order of value.

End with BULLISH, CAUTIOUS, or BEARISH, plus a confidence score out of 10, and say why the confidence is not higher.

**Do not write a soft counterpoint.** If the adversarial pass agrees with everything, it did not run. The most common real finding is that the demand signal is inferred rather than observed.

---

## Dropping and adding sections

The tables above have many rows. That creates a pull toward filling every one, because a missing row reads as an omission. Resist it.

**To drop a section, drop it and say so in one line**, so the reader knows it was a decision:

```
Regulatory: omitted. No regulation governs this category beyond
ordinary business licensing.
```

That one line is the difference between judgment and oversight. It costs nothing and it removes the incentive to pad.

**To add a section, add it.** Research that surfaced something with no home gets its own heading. The table is not a ceiling.

Counts inside a section follow the same rule. Six risks if there are six. Two if there are two.

---

## Common mistakes

| Mistake | Fix |
|---|---|
| Every section filled at equal length | Length follows substance. Some sections are two lines |
| Section kept because the table lists it | Drop it and say why in one line |
| Risks padded to five | Show the real ones |
| Market size invented to fill the table | Construct it and label it, or write unknown |
| Broad category size scored as this product's market | Score the market for this product |
| Counterpoint agrees with the thesis | Rewrite it. Argue the other side properly |
| Peers included with one source each | Omit the section |
| Shape benchmark presented as a peer | Move it to Path to $1M, labeled |
| Revenue modelled before the offer is specified | Reorder |
| First 30 days is generic advice | Make step one the cheapest thing that could prove it wrong |
| Founder-time cost never mentioned | Put it in risks or profile fit. It is invisible to the capital score |
