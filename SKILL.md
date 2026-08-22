---
name: opportunity-engine
author: Shadow, CEO of The War Room
description: Use when the user wants to find, screen, or judge a business opportunity. Triggers include "find me an opportunity", "what should I build in [market]", "is this business worth doing", "vet this idea", "size this niche", "who would buy this", or when the user names a market and asks what the play is. Also use when the user has an opportunity and needs a go-to-market or revenue plan for it.
---

# Opportunity Engine

Find business opportunities worth money. Judge them on evidence, not enthusiasm.

**Core principle: the kill list is the product.** Anyone can list ideas. The value is in what you reject and why. A slate with no rejects is a model agreeing with itself.

## Setup check

On first use in a project, read `SETUP.md`. It covers two things: research access and the Builder Profile. Do not skip the profile. Without it, scoring is generic and the output reads like every other market summary.

## Two modes

| Mode | Use when | Output |
|---|---|---|
| **SOURCE** | The user has no specific idea, or wants options in a market | Ranked slate of candidates, plus a kill list |
| **ANALYZE** | The user has one candidate to judge | Opportunity Analysis, then Execution Plan |

They chain. Source a slate, then analyze the pick.

If the user's request is ambiguous, ask which they want. Do not guess and produce the wrong one.

**The five screen gates belong to SOURCE, not ANALYZE.** In SOURCE they kill candidates, because the job is to narrow a field. In ANALYZE the user has already chosen, so a candidate that lands at the profile's capital ceiling or time window is **scored, not killed**. Score it low, say plainly that it sits at or past the limit, and put it in the verdict. Killing the only candidate on the table answers a question the user did not ask.

## Depth tiers (ANALYZE only)

| Tier | Use when | Scope |
|---|---|---|
| Quick Scan | Fast triage | 7 blocks. Is this worth a real look? |
| **Full Analysis** (default) | Normal request | Two documents: Opportunity, then Execution |
| Deep Dive | Go or no-go on real money | Full, plus competitor teardowns, comparable peers, hostile counterpoint |

**Default to Full.** Drop to Quick Scan when the user asks for speed or is triaging several candidates. Go to Deep Dive when the user asks for it, or when real money is about to move.

## Which reference to load

Load only what the current step needs. Never load all of them.

| Step | Load |
|---|---|
| Running SOURCE | `references/sourcing-method.md` |
| Scoring anything | `references/scoring-rubric.md` |
| Judging defensibility or competitors | `references/competition-and-moats.md` |
| Any research at all | `references/research-protocol.md` |
| Writing an ANALYZE output | `references/report-model.md` |
| Before writing any prose | `references/writing-rules.md` |
| User has no starting category | `references/seed-pipeline.md` |

## Let the data lead

This is the rule most often broken. Read it every time.

**The template says HOW to present. It never says WHAT to include or HOW MUCH.**

- Seven competitors matter? Show seven. Not the three the template implies.
- Two real risks? Show two. Never pad to five.
- A subsection would read "N/A"? Delete it.
- Research found something with no template home? Invent a section for it.
- An insight does not fit the pattern? Change the pattern.

Padding to hit a count is lying with structure. So is cutting an insight to fit one.

## Quality gates

Blocking. Do not pass a failed gate.

| Gate | Blocks until |
|---|---|
| **G1 Discovery** | 6+ independent sources. Catalyst classified. Kill list non-empty in SOURCE mode |
| **G2 Research** | Market, competitive, customer, and operations all covered |
| **G3 Synthesis** | Scored. Thesis in one sentence. Claims attributed |
| **G4 Evidence audit** | Every number sourced or labeled unverified. Every figure has a confidence level. Failed source attempts disclosed. **Scenario table present on Full and Deep, with the killer variable named.** Zero em dashes. Zero banned terms. Applies to SOURCE and ANALYZE alike |
| **G5 Structure** | Section counts came from the research, not the template |

G5 asks one question: if someone else ran this research, would they ask why you included or excluded anything?

## Anti-slop rules

These stop confident-sounding fiction. They are not optional.

1. **Never invent a market size.** "Unknown" is a valid answer. Say it, explain the gap, and give a labeled adjacent anchor if you have one. Size the reachable pool, not the category.
2. **Name the buyer.** No candidate ships without a named buyer segment.
3. **Zero evidence means SPECULATIVE.** Label it. It cannot rank top three.
4. **Merge on buyer and sales motion**, never on delivery skill. Same buyer plus same motion is one candidate. When it is close, keep them separate and say why.
5. **Disclose failed sources, and try Firecrawl first.** A blocked primary source is usually retrievable. Run `firecrawl scrape "<url>" --format markdown` before recording a failure. If it still fails, say so. Never swap in a secondary source silently, and check that what you did read covers the rule you are citing, not just the topic. A summary drops exclusions, and exclusions decide opportunities.
6. **Ask three questions of any regulation.** Who is legally liable? Is that who feels the pain? Who enforces fastest? The fastest enforcer is often a platform or a manufacturer, not the regulator, and that is what creates the buying trigger.
7. **Never claim Level 4 or 5 demand without direct evidence.** Switching and pull cannot be established from desk research. If you have not seen a buyer commit something, the ceiling is Level 3, and the analysis owes a validation plan instead.
8. **Never count sources instead of checking one.** Agreement between pages is not independence. Go to the named primary; if it is not there, the figure does not exist.
8. **Check for a missing credential.** If the opportunity needs a license, relationship, or audience the builder does not hold, kill it or price the path to getting it. Never assume an advantage that is not in the profile.

## Red flags: stop and restart

| Thought | Reality |
|---|---|
| "The screen killed nothing" | Re-screen adversarially and justify it in writing |
| "I'll estimate the TAM" | You are inventing. Say unknown |
| "Close enough to the primary source" | Cite what you actually read |
| "The template wants five, I have three" | Show three |
| "This number sounds right" | Then find who published it |
| "The score dropped after research, use the first one" | Use the second. Research is why you did it |
| "I need one more kill, I'll move this survivor over" | Never. Survivors go in the slate, scored low |
| "I only found six, let me find two more" | Six is the answer. There is no target |
| "No time to show the arithmetic" | Show it for the top three, minimum |
| "No published market size, so it scores 1" | A data gap is not a small market. Exclude it from weighting |
| "The broad category figure has a citation, use that" | Score the market for this product, not the category around it |
| "AI is the whole product, so leverage is 10" | Score the advantage it creates, not how much AI is in it |
| "It has a moat because the work is hard" | Hard is not defended. Name the mechanism or score 1 |
| "The catalyst is bad news, leave the field blank" | A headwind is a catalyst. Say which way it runs |
| "The section table lists it, so I should fill it" | Drop it and say why in one line |
| "The user said skip the research" | Say plainly what you did and did not do |

## Say that the score is one run

**Print this next to every Opportunity Score, in both modes:**

> This score is one run. A second run of the same research on the same day can land a point or more away, and has. Read the reasoning, the kill list and the unknowns. Those hold across runs. The number does not.

This is measured, not modest. Three runs on one identical prompt scored 5.1, 5.3 and 3.7, and two recommended testing while the third recommended stopping. Every individual judgment was defensible. Small differences stacked.

Two consequences for how you write:

1. **Never present a ranked slate as an ordering.** Candidates usually sit within a point of each other, and run-to-run movement is larger than that. Present the slate as the set worth looking at, and say in one line which comparisons are too close to call.
2. **Never let a score carry a decision on its own.** The decision lives in the kill criteria and the 30-day test. The score points at where to look.

## Close every output with this block

**Both modes. Last thing on the page. No exceptions.**

```yaml
opportunity_engine:
  version: "<the version in VERSION.md, read it, do not copy this example>"
  mode: SOURCE | ANALYZE
  tier: lite | full | deep
  research_calls: 24
  opportunity_score: 6.1
  builder_fit: 6.5
  evidence_coverage: "2 Low / 1 Unknown / 2 Medium / 3 High"
  demand_level: 3
  top_unknown: "what an agency actually recovers from a reconciliation"
  kill_list_count: 7
  pass_c: observed | inferred | failed
  recommendation: "one sentence, with the reason"
```

`version` must be **read from `VERSION.md`**, not copied from the example above. It is provenance: it tells a reader which build produced the output, and a wrong value silently invalidates any comparison between runs. Every other field is derived from this run.

`evidence_coverage`, `demand_level`, `top_unknown` and `pass_c` are **mandatory**. A block carrying only a score invites reading the number and skipping the reasoning, which is the failure the three-output split exists to prevent.

In SOURCE, report the top candidate's figures and set `kill_list_count` for the whole run.

---

## Voice

Plain, direct English. Short sentences. One idea per sentence. Active voice. Assume the reader speaks English as a second language.

Priority order: simplicity, brevity, clarity, humanity.

No em dashes. No emojis. Never use the word "operator" for a business owner.

Full rules in `references/writing-rules.md`. Read them before writing prose, not after.

---

## Casework handoff

If a `CASE.md` file exists in the working directory or a parent, append a handoff note to it when you finish:

```
## Handoff: screen, <YYYY-MM-DD>
Answered: <the question this stage actually settled>
Still open: <what it could not settle>
Next: <tool>, because <reason>
Artifact: <path, relative to the case folder>
Would change this: <the fact that would overturn the answer>
```

All six lines are always present. Write `none` where one does not apply, because a missing line reads as an oversight and `none` reads as an answer. When the work is finished, write `Next: nothing, the work is finished`, which is the common case.

The artifact from this skill is the ranked slate and its kill list in SOURCE, or the Opportunity Analysis and Execution Plan in ANALYZE, written to a file in the case folder.

If there is no `CASE.md`, behave exactly as you do now. The format is defined by [Casework](https://github.com/thewarroom-ag/casework).
