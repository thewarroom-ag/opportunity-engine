# Research protocol

Evidence is the whole product. Everything here protects it.

---

## Search ladder

Use the highest rung available.

**1. Native web search.** If the agent has it, use it.

**2. Firecrawl.** Needs `FIRECRAWL_API_KEY`. See `SETUP.md`.

**3. No research.** Then say so, loudly.

### Degraded mode

With no research access, open every output with this:

```
NO RESEARCH ACCESS. Every figure below comes from model knowledge,
is unverified, and may be wrong or out of date. No verification
table is provided. Treat this as a hypothesis, not analysis.
```

Then:

- Label every number unverified
- Produce no verification table
- Invent no citations, ever

Never quietly pretend to have researched. That is the single worst failure this skill can produce.

---

## Source hierarchy

| Tier | Sources | Use for |
|---|---|---|
| **A. Primary authoritative** | Statutes, regulations and their preambles, regulatory guidance, court decisions, government statistics, official filings, audited accounts. A company's own disclosures, but only for facts about that company | Anything load-bearing |
| **B. Independent secondary** | Academic work, trade bodies with no product to sell, investigative and business journalism, analysts who publish their methodology | Context, corroboration, market signals |
| **C. Interested** | Consultancies, commercial research houses, brokers, marketplaces, vendors, service providers | Direction of travel. Never the last word |
| **D. Anecdotal** | Forums, reviews, social posts, individual accounts | What people say they paid and what they complain about |

**Consulting firms and commercial research houses are Tier C, not the top tier.** This is a change, and it matters. A firm selling a $5,000 market report has a commercial interest in that market sounding large, and a firm paid on transaction volume has an interest in reporting record deal activity. Polished output is not independence. In testing, the two most persuasive statistics in one analysis both came from companies selling into the market the opportunity would have competed in.

A regulator and a consultancy do not belong in the same category because both publish PDFs with charts in them.

---

## Independence, not just tier

**Tier measures rigour. Independence measures bias. Score both.**

A source with a commercial interest in the claim is weaker than its tier suggests.

| Situation | Confidence cap |
|---|---|
| Tier B source paid on the outcome it reports | **Medium** |
| Tier C vendor making a claim about its own market | **Low** |
| Any statistic whose only source sells the solution | **Low**, and name the conflict |

### Examples

An M&A advisory firm reporting record deal volume is paid on deal volume. Tier C, capped at Medium.

A compliance software vendor claiming "30% of systems are non-compliant" is selling compliance software. Tier C, Low, and say so in the verification table.

**Name the conflict in the table.** Do not just downgrade quietly. The reader needs to know why.

---

## Attempting primary sources

For any load-bearing claim, try the primary source. Regulator, filing, or the original study.

### Government sources: use the agency API, not a scraper

Scrapers return navigation chrome on government sites. The agencies publish APIs. Use them first.

```bash
# Regulation text by CFR part
curl -s "https://www.ecfr.gov/api/versioner/v1/full/$(date +%F)/title-40.xml?part=84"

# Federal Register: find the rule, then fetch its raw text
curl -s "https://www.federalregister.gov/api/v1/documents.json?conditions\[term\]=<query>"
curl -s "<raw_text_url from that JSON>"
```

**The Federal Register raw text endpoint matters most, because it returns the preamble.** That is where an agency explains terms its own regulation leaves undefined.

In testing, a rule exempted an entire subsector using a term the CFR never defines. The list of exempt equipment existed only in the preamble. That one paragraph reversed the buyer definition of a whole analysis, and no secondary source carried it, including a law firm brief with nothing to sell.

**When a rule uses a term it does not define, go to the preamble.**

### The CFR does not tell you whether a rule is in force

**This one has already produced a wrong answer.** A run pulled a part from the eCFR versioner API and found the section present in full, sourced to its Federal Register notice, with no amendment noted. A federal court had vacated it nationwide five months earlier.

Vacatur does not remove text from the CFR. Neither does a stay, an enforcement-discretion policy, or a compliance-date extension. The text sits there looking authoritative until an agency publishes a removal rule, which can take years.

**So reading the regulation is necessary and not sufficient.** For any rule your thesis depends on, also check:

- The agency's own page for the rule, which usually carries litigation and enforcement notices
- The Federal Register for amendments, extensions, and proposed changes since publication
- Whether anyone has challenged it, and where that stands

A rule that is on the books and unenforceable is worse than no rule, because it looks like a catalyst.

Mine it for numbers nobody republishes: agency population estimates, and the Paperwork Reduction Act burden section, which gives an independent Tier A read on what a whole regulated population spends. In the same test that section turned an unknown market size into a scored one.

### Then Firecrawl, for everything without an API

Vendor sites, trade press, PDFs, and regulator pages with no API.

```bash
firecrawl scrape "<url>" --format markdown
firecrawl search "<query>" --limit 5
```

It handles PDFs that will not parse, HTTP 403 blocks, and JavaScript-rendered pages. Tested: it retrieved an EPA fact sheet PDF and an FTC guidance page that both failed ordinary fetches, and one of them changed a conclusion.

**Known limits, from testing. Do not plan around these being solved:**

| Source | Status |
|---|---|
| reddit.com | **Cannot scrape directly.** Firecrawl refuses it, the `.json` endpoint returns 403 even with a browser user-agent, and reader proxies get the same block. Use the front-end below |
| eCFR | **Fails**, returns navigation only. Use the versioner API above |
| LinkedIn | **Not retrievable** by any method. This is why individual practitioners often cannot be verified |
| Facebook groups | **Not retrievable.** Firecrawl refuses it, direct fetch returns HTTP 400 behind a login wall. No workaround found. Trade-group posts often carry the best realised-price evidence anywhere, and you cannot have it |
| Job-board search pages | **Fail**, JavaScript-rendered. Individual job posts scrape fine, so find them with a `site:` search and fetch them one at a time |

**A search snippet is not a source.** Blocked platforms leak fragments into search results, and a fragment showing exactly the number you want is the most tempting thing in research. You cannot see the scope, the country, or the date around it. Record it as unobtainable and move on.

### Reading Reddit anyway

Reddit is the best buyer-side evidence available in most consumer and small-business markets, and it is the one place people state what they actually paid rather than what they advertise. It is worth the extra step.

**The Redlib route is dead.** It worked in the morning and was gone by the evening of the same day, 16 August 2026. Anubis, a proof-of-work anti-scraper challenge, has been deployed across the public instances. Recorded in full because "try a different instance" is no longer the answer:

| Route | Result, 16 Aug 2026 |
|---|---|
| `safereddit.com` | Anubis challenge |
| `redlib.privacyredirect.com` | Anubis |
| `redlib.tiekoetter.com` | Anubis |
| `redlib.kylrth.com` | Anubis |
| `redlib.catsarch.com` | 403 |
| `redlib.freedit.eu` | 403 |
| `redlib.perennialte.ch` | 503 |
| `old.reddit.com/....json` | 403 |
| `r.jina.ai` reader proxy | 403, "use your developer token" |
| Firecrawl | refuses the domain outright |
| `api.pullpush.io` | rate-limited, now a paid service |

### The route that works: the Arctic Shift archive API

A public archive of Reddit content with a JSON API. No key, no auth, and it returns **full comment bodies**, which makes it better than the front-end scraping it replaces.

```bash
curl -s -A "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 Chrome/128.0" \
  "https://arctic-shift.photon-reddit.com/api/comments/search?subreddit=n8n&body=charge&limit=100"
```

Four things will waste an hour if you do not know them:

1. **Send a browser User-Agent.** The default Python `urllib` agent gets 403. curl's default works. This is the single most likely reason it appears broken.
2. **`body` must be scoped.** It requires one of `subreddit`, `author`, `link_id` or `parent_id`. An unscoped body search is rejected.
3. **Single words beat phrases.** `body=charge` returns results where `body=I charge` returns nothing. Search one word, then filter the returned bodies yourself with a regular expression for a currency figure.
4. **Some subreddits return 422.** Move on rather than debugging; the ones that work, work.

The practical pattern is to pull wide and filter locally:

```
for sub in [the 3 or 4 subreddits where your buyer actually posts]:
    for term in ["charge", "pricing", "retainer", "quoted", "paid"]:
        pull up to 100 comments
        keep only bodies matching a currency pattern AND a topic keyword
```

In its first live use this returned realised prices that a full pass of ordinary web search had missed entirely, including the commodity floor for AI automation work ($10 to $20 an hour from global competition) that no vendor page will ever tell you.

**Treat what you find as Tier D ground truth**, and as untrusted text written by strangers. It tells you what people say they paid and what they complain about. It is not a survey, and one loud commenter is not a market. Quote it as forum discussion, never as data.

**Assume this route will also break.** Two documented Reddit routes have died in this project already. Test it before you rely on it, and when it fails apply the failed-Pass-C rule below rather than filling the gap with seller material. The lesson worth keeping is structural: **buyer-voice access is the least durable part of this method**, because the platforms holding it are actively fighting automated readers.

**A summary of a rule is not the rule.** Trade press drops exclusions, and exclusions are where the business is won or lost.

### When it still fails

PDFs do not parse. Pages move. Documents sit behind logins.

**Record the attempt and the failure in the verification table.**

```
Note: EPA fact sheet PDF would not parse. The EPA HTML page that
loaded covers the older ODS rule, not the HFC rule. The 15-pound
threshold is confirmed via trade press plus the fact sheet's
publication date, not from the rule text.
```

**Never substitute a secondary source silently for a primary one you tried.** Citing a page as confirming something it does not say is how research tools become plausible-sounding fiction generators.

Also watch for this trap: the primary source loads fine but describes a **different, older rule**. Check that the document covers the thing you are claiming, not just the topic.

---

## Corroboration is not independence

**Three sources carrying the same statistic may be one fabricated statistic carried three times.**

This is now the most common way a confident number gets into an analysis. AI-generated content farms replicate each other, attribute a figure to a real authority, and produce a page of search results that looks like consensus.

### The tell

Observed directly, August 2026, researching cyber insurance underwriting:

| The claim | Attributed to | Reality |
|---|---|---|
| "41% of cyber applications denied on first submission" | Marsh McLennan, 2024 | No such figure in any Marsh publication |
| "96% of insurers mandate MFA, 88% require EDR" | Marsh McLennan, 2025 carrier survey | No such survey exists |
| "80% require MFA, 65% expect EDR" | Marsh | Contradicts the line above, same claimed source |
| "99% of applications include MFA questions" | Marsh | Not published anywhere |

Marsh's actual research on this reports **correlation coefficients between control deployment and breach likelihood**. It contains no carrier-mandate percentages of any kind. Every one of the figures above appeared only on content farms.

**The diagnostic is the disagreement.** 41, 80, 96 and 99 percent cannot all describe the same thing. When variants of one claim carry different numbers under the same attribution, you are looking at fabrication drifting through copies, not at a measurement.

### The rule

1. **A statistic is worth its named primary, not its citation count.** Go to the named source. If Marsh is credited, open Marsh. If the named primary does not carry it, **the statistic does not exist**, however many pages repeat it.
2. **Never raise confidence for repetition alone.** Ask whether the sources are independent of each other, not just independent of the outcome. Ten pages copying one press release is one source.
3. **Treat mutually inconsistent variants as disproof**, not as a range to average.
4. **Publish the cascade when you find one.** Naming a fabricated figure is more useful to the reader than silently omitting it, because they will meet it again.

## Check whether the series changed or the counting changed

A jump in a time series is a claim about the world only if the method held still.

Observed, same session: global ISO 27001 certificates appear to have **doubled** between 2023 and 2024, from 47,291 to 96,709. They did not. 2024 was the first year the ISO Survey was compiled from a certification database instead of voluntary reporting by certification bodies. Most of the "growth" is coverage arriving, and one country is understated because its accreditation body could not share data. The time series is broken at that point and cannot be read across it.

**Before reporting growth, ask what changed in the measurement.** Look for a restated prior year, a new data source, a definition change, or a segmentation change. Any of them means the trend is an artefact until proven otherwise.

### And check that the number is about the thing you think

The US ISO 27001 certificate count is widely reported as **28,783**, including by sources that get repeated widely. That figure is the US **ISO 9001** count from the same document. The 27001 figure is **4,260**, off by a factor of nearly seven.

Two numbers on one page, and the wrong one travelled. When a figure comes from a multi-standard, multi-country table, confirm you have the right row before you use it.

## Reconciling conflicts

When credible sources disagree:

1. Give the range
2. Explain the gap: methodology, definition, or time period
3. Use the conservative Tier A or B figure
4. State confidence

```
Market size: $2.3B to $6.7B (five sources).
Gap: definitions differ on whether adjacent services count.
Using $2.3B. Confidence: Medium.
```

---

## Unknown is an answer

If you cannot find a number, say so and explain the gap.

```
The compliance-specific market size is unknown. The number of
buildings holding qualifying systems is not published anywhere
found. It could be several hundred thousand or several million,
and that difference decides whether this is good or great.
```

This is more useful than a fabricated figure, and it tells the reader what to go find out.

**Never construct a number and present it as sourced.** If you build an estimate from assumptions, label it constructed and list the assumptions.

### Give an adjacent anchor

"Unknown" is honest but thin. When you can, follow it with a **sourced adjacent number, labeled for what it actually is.**

```
TAM: UNKNOWN. No published sizing for pet food label compliance
services exists.
Adjacent anchor: US pet food market $41B in 2025 (Market Data
Forecast, Medium confidence). This is the market served, not the
addressable market for this service. Do not present it as TAM.
```

The label is the whole point. "Market served", "channel spend", or "the category this sits inside" are honest. Calling it TAM is not.

This gives the reader a defensible number to work with and a caveat that survives being challenged. A fabricated TAM does neither.

---

## Verify while writing

Attribute each claim as you write it. Do not write first and audit later. Auditing later is how unsourced numbers survive.

---

## Verification table

Every ANALYZE output ends with a full one.

**SOURCE uses a lighter version**: failed source attempts, numbers with a named conflict of interest, and the unknowns that govern the ranking. Shape is in `sourcing-method.md`. G4 applies to both. Every printed number needs a source or an unverified label either way.

| Claim | Source | Tier | Confidence |
|---|---|---|---|
| [the claim] | [named source] | 1 to 4 | High / Medium / Low |
| [failed attempt] | **Not found** | n/a | **Unknown** |

Then a short list: what you could not verify, and what would resolve it.

---

## Regulatory research

For any regulatory catalyst, answer three questions explicitly:

1. **Who bears the legal obligation?**
2. **Is that the same party who feels the pain?**
3. **Who enforces fastest?**

The answer to the second is usually no. The gap between them is often the business.

### The third question decides go-to-market

The regulator is often not the fastest enforcer. A marketplace that suppresses a listing on a 90-day clock moves faster than a state agency running enforcement discretion on a six-year phase-in. A manufacturer that voids a warranty without proof of certification moves faster than either.

Find the fastest enforcer, because that is the one that creates the buying trigger. You are selling against whichever clock actually runs.

This changes the pitch completely. Selling against a distant regulatory deadline means selling a hypothetical. Selling against a platform that delists sellers next quarter means selling a dated, specific consequence.

In a live run, the EPA placed refrigerant liability on building owners. The contractor held the trust and touched the equipment. That single fact reversed the go-to-market, and it only surfaced from reading the regulator directly.

Read the regulator. Trade press summarises, and summaries drop exactly this kind of detail.

Also check for **parallel regimes**. Federal and state rules often run at once with different thresholds, clocks, and retention periods. Overlapping rules are a burden for the buyer and an opportunity for the seller.

---

## Finding the buyer's voice

**This is the pass that fails most often, and it decides the demand score.** Every analysis that ends "the demand signal is inferred, not observed" failed here. The cause is almost never that the evidence does not exist. It is that the obvious searches return sellers, because sellers optimize for search and buyers do not.

Search the way a buyer talks, not the way a vendor writes.

### Queries by demand level

Each family produces evidence for a specific rung of the ladder in `scoring-rubric.md`. Run the ones that would move your score.

**Level 3, existing spend.** The most valuable and the most reachable. Somebody is already paying.

```
"how much did you pay" [service] site:reddit.com
"quoted me" [service] price
"is $" [amount] "reasonable for" [service]
"we pay" [amount] "for" [category]
"what do you charge" [service]
"I charge" OR "I charged" [service] client
"my rate for" [service]
```

The practitioner-side queries matter as much as the buyer-side ones. People in trade subreddits state their own rates to each other constantly, and those are realized prices rather than list prices.

**Level 4, switching.** Buyers actively leaving an incumbent.

```
"alternative to" [incumbent]
"switching from" [incumbent] OR "moved off" [incumbent]
"why we left" [incumbent]
"replaced" [incumbent] "with"
"cancelled" [incumbent] OR "canceling" [incumbent]
[incumbent] "vs" [competitor] reddit
```

**Level 2, search behavior.** Cheap to find, weakest evidence.

```
"best way to" [job to be done]
"how do you handle" [painful task]
"anyone found a good" [category]
```

**Level 1, stated pain.** Complaints without action. Do not mistake volume here for a market.

```
[category] "is a nightmare" OR "hate" OR "frustrating"
[incumbent] complaints
```

### Where to look, and what each is worth

| Source | Reaches | Notes |
|---|---|---|
| **Reddit, via a Redlib front-end** | Levels 1 to 4 | The single best source. See the route above. Trade subreddits carry realized prices |
| **Job postings** | Level 3 | A posting naming a tool or a service proves somebody pays for it. Underused |
| **Freelance marketplaces** | Level 3, weakly | Posted budgets are real but noisy. In testing, several listings carried "$5.00" and "$10.00" placeholder fields that look like budgets and are not. Verify before citing |
| **Industry forums and Discords** | Levels 1 to 4 | Narrow but candid. Often the only place a niche talks |
| **Review sites** | Levels 1 and 4 | G2, Capterra, Trustpilot. Skewed by vendor-solicited reviews. Read the two-star reviews, not the one-star or the five |
| **Trade association surveys** | Level 3 | Check who paid for the survey before quoting it |
| **Facebook groups** | Levels 3 to 5 | **Unreachable.** Frequently the best evidence anywhere, and you cannot have it |

### The rules that stop this producing fiction

**A search snippet is not a source.** Blocked platforms leak fragments, and a fragment showing exactly the number you want is the most tempting thing in research. You cannot see the scope, the country, or the date around it.

**One commenter is not a market.** Quote forum evidence as forum evidence. Never aggregate three posts into a percentage.

**Practitioner rates are not clearing prices.** Trade communities have a strong norm of telling each other to charge more, so the numbers skew high. Marketplace budgets skew low, because they select for price shoppers. **The truth is usually between them, and saying so is more useful than picking one.**

**If you find nothing, say the pass failed.** Then say every demand claim in the analysis came from sellers, and put buyer conversations at the top of the first 30 days. Do not quietly fill the gap with vendor material.

---

## Coverage: the four passes

G2 needs all four.

| Pass | Covers |
|---|---|
| **A. Market and revenue** | Sizing, growth, unit economics, pricing benchmarks |
| **B. Competitive** | Named players, pricing, positioning, funding, weaknesses |
| **C. Customer and go-to-market** | Who buys, what they complain about, how to reach them, acquisition cost |
| **D. Operations and regulatory** | Delivery model, capacity, licensing, compliance |

Pass B fails most often. A sourcing scan will miss funded competitors. Search for them by name and by category, not just by problem.

### When Pass C returns nothing

Some markets have no reachable buyer-side voice. Forums are empty, review sites do not cover the category, and every page discussing it was written by someone selling into it.

**Do not fill the gap with seller material and call it customer research.** When every source describing demand is a vendor, say so explicitly and downgrade the whole demand thesis:

```
Pass C failed. Two attempts at forums and review sites returned
nothing usable. Every statement in this report about what buyers
want comes from sellers. The demand signal is inferred, not
observed, and should be treated as the weakest part of the
analysis.
```

Then make observing it the first item in the first 30 days. Ten buyer conversations cost nothing and resolve what no amount of further searching will.

An inferred demand signal is not a fatal flaw. Presenting one as observed is.
