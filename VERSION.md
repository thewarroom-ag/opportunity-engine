# Version

**Current: 2.5**

Check `CHANGELOG.md` for what changed and why.

---

## What is constitutional

These are the parts that make the method what it is. They do not change without evidence that they are wrong, and any change to them must pass the ground-truth evals first.

**The three outputs.** Opportunity Score, Builder Fit, Evidence Coverage. Never collapsed into one number. A good business for the wrong person, and a good score on thin evidence, are different problems and the reader must be able to see both.

**The kill list comes first.** Every SOURCE run reports what it rejected, with arithmetic, before it reports anything attractive. A screen that killed nothing needs an adversarial re-screen and a written justification.

**Unknown is an answer.** No fabricated market sizes. No category figure presented as the addressable market. A gap in the public record is reported as a gap, and it must never cost points against someone who invents a number.

**Source independence is scored separately from source quality.** A polished report from a party that profits from the claim is capped, and the conflict is named in the verification table.

**Failed primary sources are disclosed.** Never substitute a secondary source silently for a primary one you tried and could not read.

**Every analysis argues against itself.** The counterpoint is not optional and it is not decorative.

**Degraded mode is honest.** With no research access, the output says so at the top, labels every figure unverified, and invents no citations.

**No em dashes, no emojis, and never "operator" for a business owner.**

---

## What is free to change

Weights. Scoring bands. The seven lenses. Report section lists. Query templates. Tiers and budgets. Anything in `seed-pipeline.md`.

These are calibration, and calibration should move as evidence arrives.

---

## When the number goes up

**Major (2.0 to 3.0):** anything that makes scores non-comparable. A factor added or removed, a weight changed, a band redefined, or a required field added to the output block. If a score recorded under the old version would mislead someone under the new one, it is a major bump and the changelog says so at the top.

**Minor (2.0 to 2.1):** new lenses, new query templates, new eval cases, wording, anything in `seed-pipeline.md`. The scores still mean what they meant.

Do not accumulate a major's worth of change under a minor number. That happened once, across a single day, and it is why 1.5 was released as 2.0.

---

## Changing anything

1. Write the eval case that would catch the failure you are fixing, if one does not exist.
2. Make the change.
3. Run the three ground-truth cases: `wrong-regulatory-premise`, `stale-regulation`, `commodity-ai-wrapper`.
4. All three must pass. On a major bump, run all ten. Record the result in `evals/RESULTS.md`.
5. Update `CHANGELOG.md` with what changed and the evidence behind it.

A change with no failure behind it is a guess. This method has 44 fixes and every one came from watching something break.
