# Opportunity Engine

A research method for finding business opportunities worth money, and judging them on evidence instead of enthusiasm.

It is not software. It is a folder of plain text instructions that changes how the model researches, screens, and writes. Anything you can hand files to should run it. Every measurement in this repo was taken on one model, so treat the rest as designed-for rather than proven.

---

## What it actually does

**It does not make the model smarter. It makes it refuse.**

That is a smaller claim than this file used to make, and it is the one the measurements support.

Ask a capable model to analyse an opportunity you name and it already does well. In a controlled run, the same model with **no skill loaded** passed every analysis case: it found the incumbent, priced the competition, declined to inflate a market it could not size, flagged sources that profit from the claim, and reached a bearish verdict unprompted. On three cases it found something better than the skill run did.

Ask that same model to **generate** candidates and it stops behaving. It pads to the number you asked for. It puts a market size on an idea that has none. It drops the list of what it rejected, because rejection does not look like helpfulness. Under time pressure it does all three at once.

That is the gap this closes.

| Asked to generate candidates | Without | With |
|---|---|---|
| How many you get | The number you asked for | The number that survived, stated as a finding |
| Rejected options | Absent | The kill list, with the arithmetic that killed each one |
| Killed for a reason that expires | No record | A resurrection trigger on every kill |
| Market size that does not exist | Printed anyway | Named as unknown, with how to resolve it |
| A user in a hurry asking for shortcuts | Complied | Refused, in the user's own terms |

**Measured:** five cases, same prompts, same model, with and without. Three of three analysis cases pass without it. Zero of two generation cases pass without it. Full scoring and the cases where the control won are in [evals/RESULTS.md](evals/RESULTS.md).

---

## Two modes

**SOURCE is the one that earns its keep.** You have no idea, or you want better ones. Give it a category, a constraint, or nothing at all. It runs seven signal lenses, extracts candidates, screens them against your constraints, scores the survivors, and returns a ranked slate **plus everything it killed and the arithmetic behind each kill.**

**ANALYZE is a format, not an upgrade.** You have one opportunity and you want it written up properly. It produces an Opportunity Analysis that answers "should I do this" and an Execution Plan that answers "how", at three depth tiers, with confidence on every figure and a verification table. Useful for producing a document someone else has to read and act on. Do not expect it to out-think the model you are already talking to, because in testing it did not.

They chain. Source a slate, analyze the winner.

---

## Install

**Find yourself in this table, then read only that section.** Every route works. None takes more than ten minutes.

| What you use | Go to |
|---|---|
| ChatGPT, Claude in a browser, Gemini, Copilot Chat, or anything you upload files to | **A** |
| An AI chat with no file upload | **B** |
| Claude Code in a terminal | **C** |
| Cursor, Windsurf, Copilot CLI, or another coding tool with a skills folder | **D** |

Everything here is plain text files. There is no software, no account, and nothing to pay for.

---

### A. Chat apps you can upload files to

This is most people. Five minutes.

1. At the top of this page click the green **Code** button, then **Download ZIP**.
2. Unzip it. You get a folder called `opportunity-engine-main`.
3. Open a new chat, project, or Gem in whatever you use.
4. Upload **seven files**: `SKILL.md` from the main folder, and all six files inside the `references` folder.
5. Send this as your first message:

> Follow SKILL.md. Load the reference files as it directs you.

That is it. Now ask it for something:

> Find me an opportunity in commercial cleaning.

**Do not upload the `examples` folder** unless you want it copying the sample layout. Those two files are long and will crowd out your actual work.

**If your tool has a "project" or "custom GPT" feature, use it.** Upload the files there once and every new chat in that project already knows the method. Otherwise you re-upload each time.

---

### B. An AI chat with no file upload

Works fine. Slightly more typing.

1. Open `SKILL.md` on this page and copy all of it.
2. Paste it into the chat, then add:

> Follow this. When you need a reference file, tell me which one and I will paste it.

3. It will ask for a file by name, for example `references/sourcing-method.md`. Open that file here, copy it, paste it in.

You will paste two or three files over a session, not all six.

---

### C. Claude Code in a terminal

One line:

```bash
git clone https://github.com/thewarroom-ag/opportunity-engine.git ~/.claude/skills/opportunity-engine
```

Restart Claude Code and ask for something in plain language. No command syntax.

Prefer not to use git? Follow the ZIP steps in section A, then move the folder to `~/.claude/skills/` and **rename it from `opportunity-engine-main` to `opportunity-engine`**. Dropping the `-main` is the step people get wrong.

On Windows the folder is `%USERPROFILE%\.claude\skills\`.

---

### D. Coding tools with a skills folder

Put the folder wherever your tool looks for skills. It is markdown, so nothing needs converting.

If your tool has no skills folder, use section A or B instead. Point the model at `SKILL.md` and tell it to follow the file.

---

### Check it actually loaded

Ask it something the skill covers:

> Is a subscription dog food business worth doing?

A real run gives you **a list of what it rejected, confidence levels on the numbers, and a note on what it could not verify**. If you get a confident answer with none of those three, the files did not load. Re-upload, or tell it directly: *"Read SKILL.md and follow it."*

This matters because a failed load looks like a working tool giving a boring answer.

---

### Then spend ten minutes on setup

**[SETUP.md](SETUP.md)** covers two things, and both are worth it.

Research access, so it works from evidence rather than memory. And a short profile of your capital, timeline, hours and what you already have going for you, so the scoring answers *your* question instead of a generic one. Skipping the profile is the most common reason people find the output bland.

**[USAGE.md](USAGE.md)** is what to type, what comes back, and ten worked examples.

---

## It is not deterministic

Run the same prompt twice and you will not get the same score.

This is measured, not a disclaimer. Three runs, identical prompt, identical version, same model, same day:

| Run | Opportunity Score | Verdict |
|---|---|---|
| 1 | 5.3 | test it |
| 2 | 4.5 | test it |
| 3 | **3.7** | **do not** |

A fourth run on the previous version scored 5.1. Full spread **3.7 to 5.3**, and it is a continuous range rather than two clusters.

Every individual judgment inside those runs was defensible. Distribution scored 3 in one and 4 in another. One run applied a single-point-dependency penalty and another did not. Stack three small differences and the verdict moves.

**What holds across runs, and what does not.** In every run measured, the kill lists, the disclosed failed sources, the named conflicts of interest and the identified unknowns stayed consistent. Two runs independently traced the same fabricated statistic to the same absent primary. The reasoning is stable. The arithmetic on top of it is not.

So:

- **Do not read the score as a measurement.** It is one run's judgment expressed as a number.
- **Run it twice on anything that matters.** Read both side by side. Where they agree, the finding is solid. Where they diverge is exactly where you should stop researching and make a phone call.
- **Ranking a slate is the weakest thing it does.** Candidates typically sit within a point of each other, and run-to-run movement is larger than that gap. Read the slate as a set worth looking at, not as an order of merit.
- **The kill list is more useful than the score**, which is the whole design intent and now also the measured result.

This is a discipline, not an instrument. It makes the model show its work, name its sources, and say what it does not know. It does not make the model repeatable.

---

## Requirements

**Web search is the one thing that matters.** The method runs on evidence. Without it you get opinion, which is free everywhere else. Most tools have browsing built in and you are already done.

**No search available?** It still runs, and it tells you: a warning at the top, every figure labelled unverified, and no invented citations. Treat that output as a hypothesis, not analysis.

**Firecrawl (optional, free tier).** Worth adding if you have a terminal. Ordinary search finds pages but often cannot read them, and regulators are the worst offenders. Setup is in `SETUP.md`. Browser-only tools cannot run it, which is fine, it just means some primary sources stay out of reach and the skill says so when it hits one.

---

## What is in the box

| File | What it holds |
|---|---|
| `VERSION.md` | Current version, and what is constitutional |
| `CHANGELOG.md` | What changed, and the evidence behind each change |
| `SKILL.md` | The router. Modes, gates, anti-slop rules, voice |
| `SETUP.md` | Research access and Builder Profile. Do this once |
| `USAGE.md` | **How to use it**: what to type, what comes back, what to expect, troubleshooting |
| `references/sourcing-method.md` | Seven lenses, extraction, the five-gate screen, ranking |
| `references/scoring-rubric.md` | Opportunity Score, Builder Fit, Evidence Coverage |
| `references/competition-and-moats.md` | Competition topology and the moat taxonomy |
| `references/research-protocol.md` | Search ladder, source tiers, independence, verification |
| `references/report-model.md` | Section definitions per tier |
| `references/writing-rules.md` | Voice and hard rules |
| `references/seed-pipeline.md` | A categorized starting universe |
| `evals/` | Ten test cases. Every one from an observed failure |

**Version 2.3.** See [CHANGELOG.md](CHANGELOG.md).

`SKILL.md` plus all six references is about 15,000 tokens, which fits in any current model with room to spare. In Claude Code the references load only when a step needs them. Everywhere else, hand it the lot and stop thinking about it.

---

## Fair warning

**This will tell you no.** Across the tested runs it reached BEARISH or CAUTIOUS more often than not, and in one case it overturned the premise it was handed and told the user the opportunity named the wrong buyer.

That is the point. A research tool that agrees with you is an expensive way to feel good. If you want to be told your idea is great, this is the wrong tool.

**It is not fast or cheap in tokens.** A Full Analysis runs 20 to 30 research calls. A Deep Dive runs more. This is a research job, not a chat reply, and the model works for several minutes before anything appears.

**It will also say "I don't know."** When a market size is not published, it says so and explains the gap rather than constructing a number that looks like research. Several outputs contain more unknowns than figures. That is the honest state of most markets, and knowing which numbers do not exist is worth more than a confident guess.

---

## How it was built

Every rule in here came from watching the method fail, not from theorizing about it.

The method was run live, then packaged, then tested against nine independent agents: normal runs, two deliberate attempts to pressure it into breaking its own rules, and one regression test with a known answer where the author had previously got it wrong. Thirty-six fixes came out of that. The agents found problems the author did not, including a scoring flaw where telling the truth about a missing market size cost you points against someone who fabricated one.

The regression test is the one that matters. Given a deliberately wrong premise and no hint, an agent following this method found the regulatory exclusion that invalidated it, traced it from the regulation to the preamble where the term was actually defined, and rewrote the thesis. That is the behavior the whole document exists to produce.

That test, and nine others drawn from real failures, are in [`evals/`](evals/README.md). Run them against your own model, with and without the skill loaded. Three have a verifiable right answer rather than a judgment call, and those are the ones worth weighting.

---

## License

Free to use for anything, including paid client work. Modify it as you like. Anything it helps you produce is yours.

Do not repackage it and sell it as your own, and keep the credit line. Full terms in [LICENSE](LICENSE).

---

Authored by Shadow, CEO, The War Room.

