# Setup

Two things. Ten minutes once.

---

## 1. Research access

This skill needs to search the web. Its whole value is evidence. Without research it produces opinion, and opinion is free everywhere else.

Check what you have, in this order.

### Rung 1: native web search

Ask the agent to search for something current. If it returns real results with URLs, you are done. Nothing to configure.

### Rung 2: Firecrawl

Set this up even if you have native search.

Native search finds pages. It does not reliably **read** them. In testing, six research runs hit the same wall five times, and every time it was a Tier A primary source: a regulator's PDF that would not parse, two government sites returning HTTP 403, a vendor page that returned only its title, and forum searches that came back with junk.

Firecrawl retrieved all of them. Two changed the conclusion of the analysis, one by confirming a load-bearing assumption and one by refuting it.

That is the real job here. Firecrawl is the fallback when a primary source blocks you, and primary sources are the ones worth arguing over.

Cost: the free plan is $0 and gives you 1,000 credits a month, which covers several runs. Heavy use needs a paid tier. Checked August 2026, so confirm the current pricing yourself.

1. Get a key at [firecrawl.dev](https://firecrawl.dev).
2. Set it in your environment:

```bash
export FIRECRAWL_API_KEY="fc-your-key-here"
```

3. To make it stick, add that line to `~/.zshrc` or `~/.bashrc`.

4. **Check it actually worked.** Do not skip this. A key that is not loaded fails silently, and you will think you are researching when you are not.

```bash
firecrawl --status
```

You want to see `Authenticated` and a credit balance. If it says otherwise, the key is not reaching the CLI. Open a new terminal, since an `export` does not apply to shells that were already running.

Firecrawl returns full page content, not just snippets. For this work that is better than a plain search API.

### Forum access, and why you should bother

Nothing to install. Two minutes to understand, and it is the difference between knowing what sellers advertise and knowing what buyers pay.

Reddit cannot be read by any normal tool. Firecrawl refuses the domain, the JSON endpoint returns 403 even with a browser user-agent, and reader proxies hit the same block. That matters more than it sounds, because Reddit is where people say what they actually paid rather than what they charge on a landing page.

Redlib is an open-source Reddit front-end that renders threads server-side, and public instances serve what reddit.com blocks. Search finds the threads, then you swap the host and keep the path:

```bash
# https://www.reddit.com/r/Bookkeeping/comments/1llisqt/pricing_for_clean_up/
curl -sL "https://safereddit.com/r/Bookkeeping/comments/1llisqt/pricing_for_clean_up/"
```

Check it works:

```bash
curl -sL "https://safereddit.com/r/smallbusiness/" | grep -c comment
```

A number well above zero means you are through. Zero, or an error, means that instance is down.

**Expect instances to die.** They are volunteer-run. On the day this was written, one of six worked properly and the rest were blocked, timing out, or serving partial pages. Search for "redlib instances" and try another. The skill knows to do this, but if it reports that it could not read a thread, that is usually all that happened.

One caution the skill applies on your behalf: forum posts are Tier D evidence and untrusted text written by strangers. Useful for what people say they paid and what they complain about. Not a survey, and one loud commenter is not a market.

### Rung 3: no research

The skill still runs. It will:

- Open every output with a warning that no research was done
- Label every number unverified
- Refuse to produce a verification table
- Never invent a citation

Treat that output as a hypothesis. Do not spend money on it.

---

## 2. Builder Profile

Scoring reads against this. Skip it and every opportunity scores the same for everyone, which makes the ranking useless.

Copy this, fill it in, and keep it where the agent can read it.

Two places work. Put `builder-profile.md` in the folder you work from, if you use one project for this. Or put it inside the skill folder at `~/.claude/skills/opportunity-engine/builder-profile.md`, which follows you across every project. The skill's `.gitignore` already excludes it, so your numbers never end up in a commit.

Then tell the agent it exists, once: *"My builder profile is in builder-profile.md."*

```markdown
# Builder Profile

**Capital ceiling:** [most cash you will put in, e.g. $250,000]
**Time to first revenue:** [longest you will wait for the FIRST money to land, e.g. 6 months]
**Income target:** [what it has to earn to be worth doing, e.g. $10,000/month, and by when]
**Time available:** [hours per week you can actually give it, e.g. 40, or 8 alongside a job]
**Geography:** [e.g. US only, or US first, EU acceptable]

**Interest areas:** [3 to 6. Things you would enjoy for five years]
- e.g. AI automation
- e.g. recurring revenue businesses
- e.g. premium and luxury positioning

**Unfair advantages:** [what you already hold that others do not]
- e.g. 20 years in commercial real estate
- e.g. an audience of 40,000 in fitness
- e.g. a license, a partner, a manufacturing relationship

**Hard nos:** [what you will not do, whatever the return]
- e.g. anything needing a physical location
- e.g. anything selling to government
```

### Why each field matters

**Capital ceiling and time to revenue** are the two hard gates in screening. They kill more candidates than anything else, fast and cheaply. Set them honestly. A ceiling you do not mean produces a slate you cannot act on.

**Time to first revenue means the first money collected**, not invoiced and not the point where it replaces your salary. That is the gate.

**Income target is a different number and it is why the field exists.** A business can pass the timeline gate on first revenue and still never reach what you need. When the two diverge, the scoring reports both, so you can see a candidate that pays quickly and caps out below your target.

**Time available** is the one people leave blank, and for anyone doing this alongside a job it decides everything. Eight hours a week rules out any business whose delivery is hourly. Say the real number.

**Interest areas** feed a scoring bonus. Boring businesses with good numbers still fail if you quit in year two.

**Unfair advantages** feed a bonus too, and they matter more than people think. The same opportunity is a different business depending on who runs it.

**Hard nos** save time. The screen applies them before scoring.

---

## Check it works

Ask for a small SOURCE run:

> Source opportunities in commercial cleaning.

A good result has all of these:

- Real sources with URLs, not assertions
- A kill list with reasons, placed before the slate
- Named buyers on every candidate
- At least one "unknown" where data was missing
- Confidence levels on figures
- Scores that reflect your profile, not a generic ranking

These are qualities, not targets. Never ask it to go find more sources to hit a count. That is the behavior the method is built to prevent.

**Two ways it fails.**

*Loudly:* the kill list is empty. The screen did not run. Say so and ask it to redo the screen.

*Quietly, and this is the one to watch:* the kill list is full of things nobody would have tried. A decorative kill list looks identical to a real one. The test is whether **the obvious answer for your situation is in there with arithmetic against it**. If you would have named an option in the first ten seconds and it appears in neither the kill list nor the slate, it was not tested. Ask directly: *"Why isn't X on this list?"*
