# Changelog

Every entry names the evidence behind the change. Changes with no observed failure behind them are not made.

---

## 2.5

### Removed

**Both sample runs.** `examples/sample-source-run.md` and `examples/sample-analyze-run.md` were labelled "real output, not written for the documentation", and they were. Each ran against a Builder Profile carrying a capital figure and a career history. That is the operator's own position, and publishing a worked run publishes it.

The runs were the best documentation in the repository, which is why they were there and why this is a real loss. The `## See a real one first` section of `USAGE.md` is gone with them, and the two rows in the README file table.

A replacement has to be built from a profile nobody holds. The eval cases in `evals/` already work that way and are unaffected.

**Not removed, because it was never a disclosure.** `SETUP.md` shows a capital ceiling of $250,000 inside a template, as an illustrative placeholder for the reader to replace. The scoring rubric's dollar bands are thresholds, not anyone's money. Both stay.

**No eval run.** This release touches documentation and removes files. Nothing in the scoring path changed, so the three ground-truth cases `VERSION.md` requires were not run. Same gap as 2.4, recorded for the same reason: it should be visible rather than assumed away.

---

## 2.4

### Added

**A Casework handoff block at the end of `SKILL.md`.** If a `CASE.md` file sits in the working directory or a parent, a finished run now appends a six-line note to it: what the run settled, what it could not settle, which tool comes next and why, where the artifact is, and the fact that would overturn the answer. All six lines are always written, with `none` where a line does not apply, because a missing line reads as an oversight.

*Evidence: five skills covered one pipeline and none of them knew the others existed. A slate could not move to the next stage without a person retyping the context into the next tool, and what got retyped was the score rather than the kill list and the unknowns, which is the part that holds across runs.*

The format belongs to Casework, not to this skill. The closing YAML block is unchanged, and with no `CASE.md` present a run behaves exactly as it did before.

**`author` in the `SKILL.md` frontmatter.**

---

## 2.3

### Fixed

**The Reddit route died and has been replaced.** Redlib worked in the morning of 16 August 2026 and was gone by that evening, with Anubis proof-of-work challenges deployed across every public instance. Eleven routes tested and recorded, because "try another instance" is no longer the answer.

**Replaced with the Arctic Shift archive API**, which is better than what it replaces: a JSON API, no auth, returning full comment bodies and searchable within a subreddit. Documented with the four gotchas that cost an hour to find, including that the default Python user agent gets a 403 while curl's does not.

*Evidence: found while running the method live, when a SOURCE run lost its entire buyer-voice pass. The new route recovered realised prices that a full pass of ordinary web search had missed, including the commodity floor for AI automation work.*

Also added the structural lesson: **buyer-voice access is the least durable part of this method.** Two documented Reddit routes have now died in this project. Assume the third will too, and test before relying on it.

---

## 2.2

### Added

**Run-to-run variance is now disclosed, in the README and in every output.** *Evidence: three runs of one identical prompt, same version, same model, same day, scored 5.3, 4.5 and 3.7, with a fourth run on the previous version at 5.1. Two recommended testing the opportunity and one recommended stopping. The published alternative-score bands from two of those runs barely overlapped, so the bands were not capturing the real uncertainty either.*

Every score now carries a line saying it is one run. The skill is also told never to present a ranked slate as an ordering, because candidates typically sit within a point of each other and run-to-run movement is larger than that gap.

What held across all three runs: the kill lists, the failed-source disclosures, the named conflicts of interest, and the unknowns. Two runs independently traced the same fabricated statistic to the same absent primary. **The reasoning is stable. The number is not.**

---

## 2.1

### Measured

**The control arm ran.** Same prompts, same model, no skill. Three of three ANALYZE cases pass unaided. Zero of two SOURCE cases pass. The split falls on the mode boundary: **the measured value of this method is in candidate generation, not in analysis.** Recorded in full, including the three cases where the control produced a better finding than the skill did. See `evals/RESULTS.md`.

### Added

**Corroboration is not independence.** Three sources carrying a statistic may be one fabrication carried three times. *Evidence: five figures about cyber insurance underwriting, all attributed to a named research firm, none present in any of its publications, all sitting on AI-generated content farms. The variants disagreed with each other, 41% against 80% against 96% for the same claim, which is the diagnostic. A researcher counting sources would have called it well corroborated.*

**Check whether the series changed or the counting changed.** *Evidence: ISO 27001 certificates appear to double in one year. The survey switched from voluntary reporting to a certification database that year, so most of the growth is coverage. Same finding: the US certificate count is widely reported as 28,783, which is that document's ISO 9001 row. The real figure is 4,260.*

**`evals/fabricated-consensus`**, which hands the model three invented statistics as premises and checks whether it goes to the named primary or counts pages.

---

## 2.0

**Scores from 1.x are not comparable to scores from 2.0.** Two factors left the Opportunity Score, a sixth arrived, and the weights moved. A 6.1 under this version and a 6.1 under 1.0 are different quantities. If you recorded a score under 1.x, rerun it rather than compare it.

Nothing about how you use the skill changed. Same two modes, same three tiers, same seven lenses, same five gates, same install. The interface is stable and the method is not, which is why this is a major version.

The decision model. V1's research was better than the scoring that consumed it, and four independent test agents said so.

### Changed

**Capital and timeline left the Opportunity Score.** They carried half the weight and floated every cheap, fast service business to the top. They are constraints belonging to the builder, not qualities of the opportunity, and they were already screen gates. *Evidence: multiple runs where a generic service ranked above a structurally better business, and one agent that reported "this is the most generic idea on the slate and it ranks fourth, that is a rubric artifact."*

**One score became three.** Opportunity Score, Builder Fit, Evidence Coverage. *Evidence: a run that had to write "eight of nine profile items fit, the ninth decides everything," which a single number could not express.*

**Six factors replaced five.** Demand intensity, distribution, economics, defensibility, speed to validation, technological leverage.

**Technological leverage scores the advantage created, not the technology present.** *Evidence: an agent scored the old factor 7 on a product where AI was everything and conferred nothing, then wrote that the bands "conflate how much AI is in the product with how much advantage the AI creates" and called its own answer "a workaround, not a resolution." Under 2.0 the same candidate scores 4 with no complaint.*

**Speed to validation replaced speed to revenue.** A business that pays in month two but cannot be tested before you commit is worse than one that pays in month eight and dies for $500 in week one.

**Distribution became a first-class factor.** *Evidence: a run where an existing audience moved the old timeline score by four points and inverted the ranking. Distribution was deciding outcomes from the wrong box.*

**Demand got a six-level evidence ladder.** Theoretical pain through to buyers committing money. Most desk research reaches Level 2 and now has to say so.

**Competition topology replaced the flat competitor penalty.** Five rivals can mean a commodity bloodbath or a validated category. *Evidence: an agent noting a stricter reader would drop the old penalty entirely because the competitors sold software, not the service.*

**Source hierarchy became A/B/C/D, and consultancies moved out of the top tier.** A firm selling a market report has a commercial interest in that market sounding large. *Evidence: two runs where the most persuasive statistics came from companies selling into the market the opportunity would compete in.*

**Adjustments almost entirely removed.** Bonuses were compensating for a rubric measuring the wrong things.

### Added

**A moat taxonomy**, with the question that separates real from decorative: does it compound as the business grows?

**"Why is this still available"** as a mandatory section for top candidates.

**Reachable pool and beachhead sizing** in place of headline TAM.

**Ranges and a scenario table** instead of point estimates, plus the variable that kills the thesis if it lands at bear.

**Resurrection triggers** on every kill. *Evidence: a run that killed its best candidate because a court vacated the regulation behind it sixteen days earlier, and had nowhere to record what would bring it back.*

**A Reddit route.** Firecrawl refuses the domain, the JSON endpoint 403s, reader proxies get the same block. Redlib front-ends serve what reddit.com blocks. *Evidence: every run before this named seller-only demand evidence as its own biggest weakness. The first run with the route pulled practitioners stating what they actually charge.*

**The CFR-in-force trap.** A run pulled a part from the eCFR versioner API and found the rule present in full, five months after a court vacated it nationwide. Vacatur does not remove text from the CFR. Reading the regulation is necessary and not sufficient.

**`evals/`**, ten cases, every one from an observed failure. Three have verifiable ground truth.

### Fixed after the eval sweep

**The machine-readable block moved from `report-model.md` into `SKILL.md`.** *Evidence: the sweep emitted it in three of three ANALYZE runs and none of four SOURCE runs. The load table sends an agent to `report-model.md` only when writing an ANALYZE output, so a SOURCE run never saw the requirement. Perfect correlation, and the agents were not at fault. Anything mandatory for both modes belongs in the router.*

### Measured

All ten eval cases run against 2.0. **Ten of ten pass, no critical criterion missed**, one near-miss recorded on `buyer-not-named`.

The version number is a claim and it should be read with its limits attached: the suite is author-scored and **no control arm has run**, so ten passes show the outputs are good without showing the skill caused it. See `evals/RESULTS.md` for the full list of what this does not prove.

---

## 1.0

Initial release. The method extracted from a working system that had shipped 17 report pairs.

Two modes, three depth tiers, seven sourcing lenses, five screen gates, five quality gates, a weighted rubric, a source hierarchy, and a writing voice.

Built by running the method live, then testing the packaged version against nine independent agents including two adversarial pressure tests and one known-answer regression. **Forty-four fixes came out of that**, every one from watching the method fail rather than theorizing about it.

The regression test is the one that mattered: handed a premise its own author had got wrong, with no hint, an agent found the regulatory exclusion that invalidated it, traced the term from the regulation into the Federal Register preamble where it was actually defined, and rewrote the thesis.
