# Scoring rubric

Three separate outputs. Never collapse them into one number.

| Output | Question it answers |
|---|---|
| **Opportunity Score** | Is this a good business for anyone? |
| **Builder Fit** | Can this particular person do it? |
| **Evidence Coverage** | How much of this is known rather than assumed? |

A 8.2 with weak fit is a good business for someone else. A 8.2 on 30% evidence is a guess with a decimal point. Reporting one number hides both.

---

## Why capital and timeline are not scored here

They used to be, and together they carried half the weight. That made every cheap, fast service business float to the top regardless of whether it was worth building.

Capital and time to revenue are **constraints belonging to the builder**, not qualities of the opportunity. They are already the first two screen gates in `sourcing-method.md`, and they feed Builder Fit below. Scoring them a third time was the single largest distortion in the old model.

---

# 1. Opportunity Score

Six factors. Show the arithmetic.

| Factor | Weight |
|---|---|
| Demand intensity | 20% |
| Distribution | 20% |
| Economics | 20% |
| Defensibility | 15% |
| Speed to validation | 15% |
| Technological leverage | 10% |

## Demand intensity

**A problem is not a market.** People can hate something and still never pay to fix it. Score the evidence you actually have, using this ladder.

| Level | What you observed | Score |
|---|---|---|
| 5 | **Pull.** Prospects commit scarce resources: deposits, LOIs, pilots, signed contracts, their own data, a calendar slot with their boss | 10 |
| 4 | **Switching.** Buyers are actively leaving incumbents for alternatives | 8 |
| 3 | **Existing spend.** They already pay money, staff time, or a workaround tax to solve it | 7 |
| 2 | **Search.** They actively look for solutions. Comparison queries, "alternative to X" | 4 |
| 1 | **Stated pain.** They complain in public but do nothing | 2 |
| 0 | **Theoretical.** The problem is inferred from structure, not observed | 1 |

State the level and the evidence for it. "Level 3, from twelve practitioners quoting their own catch-up rates" is a finding. "Strong demand" is not.

**Most desk research tops out at Level 2.** Reaching Level 3 usually means reading forums where people name what they pay. Level 5 requires talking to someone. Say which level you reached and what it would take to reach the next one.

## Distribution

**Can you reach the buyer at a cost the business survives?** This decides more outcomes than product quality and it is the factor most often missing from an otherwise complete analysis.

| Score | Situation |
|---|---|
| 10 | **Owned.** An audience, community, customer base, contractual channel or sales organization already reaching qualified buyers |
| 7 | **Proven channel.** Buyers are identifiable and an economical route to them demonstrably exists |
| 4 | **Reachable, unproven.** You can name and list the buyers, but acquisition cost and conversion are unknown |
| 1 | **Structurally hard.** Buyers are diffuse, require trusted introduction, or acquisition plausibly costs more than they are worth |

A product anyone could build, sold into distribution nobody else has, beats a better product with no route to market. Score accordingly.

## Economics

Margin, price point, and how long the money takes to come back.

| Score | Situation |
|---|---|
| 10 | Gross margin above 70%, revenue recurs by construction, acquisition cost repays inside 6 months |
| 7 | Margin 50 to 70%, or recurring with slower payback, or high-ticket project work with repeat |
| 4 | Margin 30 to 50%, project revenue that does not stack, or payback beyond 12 months |
| 1 | Thin margin, no repeat purchase, or revenue that stops the moment the builder stops |

Where the inputs are uncertain, score the range and say so. See the scenario requirement in `report-model.md`.

## Defensibility

Load `competition-and-moats.md`. Name the moat type from the taxonomy, then score.

| Score | Situation |
|---|---|
| 10 | A compounding moat. It gets stronger as the business grows |
| 7 | A real but static barrier. It holds, it does not deepen |
| 4 | Weak. Reputation, execution quality, or a head start |
| 1 | None. Anyone competent could copy it in a quarter |

"Hard work" is not a moat. Neither is being first if nothing accrues.

## Speed to validation

**Not speed to revenue.** How fast and how cheaply can you find out you are wrong?

| Score | Situation |
|---|---|
| 10 | The core assumption is falsifiable in under 30 days for under $1,000 |
| 7 | 30 to 90 days, under $10,000 |
| 4 | 90 to 180 days, or $10,000 to $50,000 |
| 1 | Cannot be cheaply falsified. You have to build it and find out |

This replaces timeline to revenue, and it rewards a different thing. A business that pays in month two but cannot be tested before you commit is worse than one that pays in month eight and can be killed for $500 in week one.

## Technological leverage

**Score the advantage created, not the technology present.**

| Score | Situation |
|---|---|
| 10 | Produces a cost, speed, data or capability advantage competitors cannot easily match |
| 7 | A real advantage, replicable by a determined competitor within a year |
| 4 | An efficiency gain available to everyone, including your competitors and your customer |
| 1 | None, or it is table stakes everyone already has |

A product built entirely on a frontier model, where every competitor uses the same model, scores **4**. The technology is the whole product and it confers no edge. This is the most common scoring error in AI-native candidates.

## Adjustments

Almost none, deliberately. The old model bolted bonuses onto a rubric that was measuring the wrong things. Six well-chosen factors carry their own meaning.

Two red flags remain, **-1 each, floor of -2**:

- **Single-point dependency.** One customer, one channel, or one supplier, where losing it ends the business.
- **Platform dependency.** A policy change by a company you do not control can close you overnight.

No bonuses. Recurring revenue is Economics. An arbitrage is Economics or Defensibility. Interest areas and existing advantages are Builder Fit, not opportunity quality. If you find yourself wanting a bonus, the factor scores are wrong.

---

# 2. Builder Fit

Scored separately, out of 10, against the Builder Profile.

| Dimension | Question |
|---|---|
| Capital | Does the requirement fit inside the ceiling, with reserve? |
| Distribution assets | Do they already hold a route to these buyers? |
| Credential and access | Do they hold the licence, relationships, or standing this needs? |
| Time | Does the hours-per-week reality support the delivery model? |
| Risk and hard nos | Does it violate a stated constraint? |

**Any dimension at 1 caps the total at 4.** A missing credential is not averaged away by good capital.

Report it plainly:

```
Opportunity Score: 7.8
Builder Fit: 3 (capped: needs a licensed professional the profile does not have)
```

That is a good business and the wrong owner, and the reader should see both.

---

# 3. Evidence Coverage

How much of the thesis is grounded. **No percentage.** A number implies a precision this does not have.

Name each load-bearing component and its confidence:

| Component | Confidence |
|---|---|
| Buyer exists and is reachable | High |
| Pain is real | Medium |
| They will pay for it | Low |
| Price point | Medium |
| Acquisition cost | Unknown |
| Delivery cost | Medium |
| Competition | High |

Then one sentence: **which unknown, if resolved, would most change the decision.** That is the next thing to go find out, and it belongs in the first 30 days.

If three or more components are Low or Unknown, say the thesis is largely unverified, whatever the Opportunity Score says.

---

## Reporting the alternative when a factor is contested

Whenever a defensible alternative score would move the total, publish both and name the one you used.

```
Opportunity Score: 6.4. Scoring distribution at 7 rather than 4 gives
7.2. I used 4 because no comparable business has demonstrated the
channel, and I would not argue hard against 7.
```

Two lines, and it removes the incentive to quietly pick the flattering reading.

## When the number disagrees with your judgment

Report both. Say which sub-score tells the real story and why the total misleads. Never silently adjust a number to match a conclusion you had already reached.
