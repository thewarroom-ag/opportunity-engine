# Using it

Everything you need after install. What to type, what comes back, what it costs, and what to do when it goes wrong.

If you have not installed it yet, start with [README](README.md). If you have not set up research access and a Builder Profile, do [SETUP](SETUP.md) first. Skipping the profile is the single most common reason people find the output generic.

---

## Just type what you want

There is no command syntax. Ask in plain language and it picks the mode.

| You say | It runs |
|---|---|
| "Find me an opportunity in commercial cleaning" | SOURCE |
| "What should I build? I have no idea" | SOURCE, choosing categories from your profile |
| "Is a subscription dog food business worth doing?" | ANALYZE |
| "Vet this: managed IT for dental practices" | ANALYZE |
| "Quick scan on pet insurance" | ANALYZE, Quick Scan tier |
| "Deep dive on commercial solar maintenance, I'm about to commit money" | ANALYZE, Deep Dive tier |

If your request is ambiguous it will ask which you want rather than guess.

---

## The two modes

### SOURCE: you need options

Give it a category, a constraint, a theme, or nothing.

```
Source opportunities in specialty food manufacturing.

Source something under $50K, B2B, no inventory.

I have no idea what to build. Go.
```

**What you get back:**

1. **The frame.** What it decided to hunt and why. If you gave it nothing, this is where it explains which categories it picked from your profile.
2. **The kill list, first.** What it tested and rejected, with the reason. This comes before the good news deliberately.
3. **The ranked slate.** As many as survived the screen. Often 4 to 8, sometimes 3, occasionally more. Each one names a buyer, a specific wedge, a catalyst, a provisional score, and the single biggest risk. **A short slate usually means your constraints are tight, not that the run failed.** Tight constraints are the point of stating them.
4. **The evidence section.** Failed sources and what was used instead, figures with a conflict of interest named, and the unknowns that would change the ranking. This is the lighter cousin of the full verification table, which only ANALYZE produces.

**Read the kill list first.** It tells you whether the screen actually ran. If the obvious answer for that category is not in there, the screen was soft.

### ANALYZE: you have one thing

```
Analyze this: [your opportunity, in a sentence or two]
```

The more specific your sentence, the better the analysis. "A compliance service for X" beats "something in compliance."

**What you get back:** two documents.

**Document 1, Opportunity Analysis.** Answers *should I do this.* Thesis, catalyst with a date, market, competitive landscape, where the gap is, entry analysis, unit economics, risks, regulatory, what got filtered out, the score with its arithmetic, takeaways, profile fit, a verification table, and a counterpoint arguing against everything above it.

**Document 2, Execution Plan.** Answers *how.* Decision with kill criteria, offer specification with prices, a bottom-up path to $1M ARR, go-to-market, operating model, where AI helps and where it must not touch, and a first 30 days ordered so the cheapest thing that could disprove the thesis comes first.

---

## Three depth tiers

| Tier | Ask for it when | Roughly |
|---|---|---|
| **Quick Scan** | Triaging several ideas | 7 blocks, one verdict |
| **Full Analysis** (default) | Normal use | Both documents |
| **Deep Dive** | Real money is about to move | Full, plus 3 to 5 competitor teardowns, comparable peers where they exist, and a harder counterpoint |

Say "quick scan" or "deep dive" to override. Otherwise you get Full.

---

## Worked examples

Ten situations people actually arrive with. Copy the prompt, change the details.

### 1. You have capital and no idea

The hardest place to start, and the one SOURCE exists for.

> I sold my share of a landscaping business and have about $300K. I do not want another business where I am on site every day. Find me something to build. No category in mind.

It reads your profile, picks two or three categories, and says why. **Watch for:** whether the categories use something you already hold. If it picks purely on interests, tell it to weight your advantages instead.

### 2. You have one idea and want it stress-tested

> Analyze this: a mobile windscreen repair service sold to fleet managers, priced per vehicle per year instead of per repair.

**Watch for:** the counterpoint at the end. If it agrees with everything, ask it to argue harder.

### 3. You are choosing between three things you already like

> Quick scan each of these so I can compare: (1) a bookkeeping service for freelance tradespeople, (2) a Shopify app for pre-order management, (3) buying a laundromat route. Then tell me which one survives contact with my profile.

**Watch for:** Quick Scan is the right tier here. Do not spend a Deep Dive on three things you are still triaging.

### 4. You hold a license or credential and want the right vehicle for it

> I am a licensed structural engineer with 18 years in commercial construction. Source opportunities that are hard for anyone without that license.

This runs the credential gate backwards, which is the strongest use of it. **Watch for:** candidates that are merely adjacent to your license rather than gated by it.

### 5. You have an audience

> I run a 40,000-subscriber YouTube channel about woodworking. Most revenue is ad share and it is falling. Source businesses where that audience is the unfair advantage, not just a marketing channel.

**Watch for:** whether the audience shows up in the timeline score. If it only appears as a +1 bonus, it has been undercounted.

### 6. You want to buy, not build

> Analyze this as an acquisition rather than a startup: buying an established commercial cleaning contractor doing about $1.2M revenue in a mid-size metro. My ceiling is $600K plus SBA debt.

**Watch for:** the entry analysis section. Say "plus debt" explicitly or the capital gate will read your cash ceiling as the whole budget.

### 7. You are researching for a client

> My client is a regional insurance brokerage looking for an adjacent service line. Deep dive on offering outsourced HR compliance to their existing small-business book.

**Watch for:** profile fit will be weak, because the profile is yours and the business is theirs. Either write a temporary profile for the client or ignore that section.

### 8. A rule changed and you think there is an opening

> A new rule requires short-term rental hosts in my state to carry commercial insurance and file annual safety attestations starting next year. Is there a business in helping them comply?

**Watch for:** the three regulatory questions. Who is legally liable, is that who feels the pain, and who enforces fastest. The third often moves the whole go-to-market.

### 9. You have very little time

> I have a full-time job and about 8 hours a week. Ceiling is $15K. Source something that can reach $4K a month without me quitting.

**Watch for:** the honest answer may be that most candidates fail the timeline gate. A short slate is a real result, not a broken one.

### 10. You want to revisit a category that burned people

> Meal kit delivery destroyed a lot of capital between 2018 and 2023. Analyze whether anything structural has changed that makes a narrow version of it viable now.

**Watch for:** the catalyst section. If it cannot name a dated event that changed, the answer is no, and it should say so rather than manufacture one.

### Chaining the two modes

> Source opportunities in commercial real estate services, then deep dive whichever one scores highest.

Saves a round trip. You can also intervene: *"Skip the top one, deep dive number three, I like the buyer better."*

---

## What to expect

### Time and cost

A SOURCE run is the cheapest, usually 12 to 20 research calls. A Full Analysis runs 20 to 30 and takes several minutes. A Deep Dive runs 25 to 45 and takes longer. This is not a chat response, it is a research job, and the model will be working for a while before anything appears.

It is not cheap in tokens. If you are on a metered plan, a Deep Dive is a real spend. Use Quick Scan to triage and save Deep Dive for the one you are serious about.

### It will tell you no

Across the tested runs it reached BEARISH or CAUTIOUS more often than not. One run was handed a premise, found the regulation that invalidated it, and told the user the opportunity named the wrong buyer.

That is the tool working. If you want confirmation, this is the wrong tool.

### It will say "I don't know"

When a market size is not published, it says so and explains the gap instead of inventing a number. Some outputs contain more unknowns than figures.

This is deliberate. Knowing which numbers do not exist is more useful than a confident guess, and the rubric is built so that being honest about a gap does not cost you points against someone who fabricates one.

### It argues with itself

Every ANALYZE ends with a counterpoint that attacks the analysis above it: which evidence is circular, which number is carrying the most weight on the least support, where the reasoning made an unearned leap, and what would change the verdict.

The counterpoint is allowed to disagree with the decision. A conditional go with a bearish counterpoint means "worth testing cheaply, expect it to fail." That combination is common and it is not a bug.

### The score is for ranking, not deciding

It is one number out of 10 with the arithmetic shown. It ranks candidates against each other. It does not make the call.

When the number disagrees with the analysis, the output says so and points at the sub-score that tells the real story. A cheap fast service business will float up the ranking because capital and timeline carry half the weight. Read the defensibility score.

---

## Getting better results

**Fill in the Builder Profile properly.** Especially the unfair advantages. The difference between "no advantages" and "I have a 12,000-person email list" changed one tested analysis by four points on a factor worth a quarter of the score, and flipped the recommendation.

**Be honest about your capital ceiling and time window.** They are the two hard gates. A ceiling you do not mean produces a slate you cannot act on.

**Give it your hard nos.** "Nothing requiring a physical location" saves it from surfacing five things you will never do.

**Push back on it.** If a candidate looks wrong, say so and ask why it scored that way. The arithmetic is shown so you can argue with it.

**Ask it to chain.** "Source opportunities in X, then deep dive the winner" works and saves a round trip.

---

## When something looks off

| Symptom | Cause | Fix |
|---|---|---|
| No kill list in a SOURCE run | The screen did not run | Ask it to redo the screen. A non-empty kill list is required |
| Confident numbers with no sources | The skill did not load | Check `ls ~/.claude/skills/opportunity-engine/SKILL.md`. See README |
| No confidence levels anywhere | Same | Same |
| Every candidate scores 7 to 8 | The screen was too soft | Ask it to tighten the gates against your profile |
| Output feels generic | No Builder Profile | Do SETUP.md. This is the usual cause |
| It refuses to give a market size | Working correctly | It could not find one. Ask what would resolve it |
| A big red warning about no research access | Search is not available | See SETUP.md. Treat that output as a hypothesis |
| "I could not read the forum threads" | A Redlib instance was down | Ask it to try another instance. See research-protocol.md |
| It disagrees with a number you know | Possible, it runs on an LLM | Ask for the source. Every figure should have one or be labeled unverified |

---

## What it will not do

- **Decide for you.** It produces a verdict and kill criteria. You commit the money.
- **Replace diligence.** Verify anything that carries capital. The verification table exists so you know what to check.
- **Predict.** It reads catalysts, competitors and economics. It does not know what happens next.
- **Flatter you.** See above.
