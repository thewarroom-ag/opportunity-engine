# Evals

Eleven cases that test whether the method actually changes behavior, rather than whether the output reads well.

Every case here comes from an observed failure. Nothing was invented to make a tidy suite.

---

## Why these exist

The skill accumulated 44 fixes from ad-hoc agent testing. That worked, but it does not scale and it cannot answer the question that matters when you change something:

> **Is the new version better, or just different?**

These cases exist so that a change to the scoring rubric or the research protocol can be measured rather than assumed.

---

## How to run one

1. Load the skill into whatever model you are testing. See the README install section.
2. Set the Builder Profile the case specifies, if it specifies one.
3. Paste the case prompt exactly. Do not add hints, and do not tell the model it is being tested.
4. Score the output against the criteria.

**Run each case against a control too**: the same model, same prompt, no skill loaded. That is the only way to know whether the method did the work or the model did.

## Scoring

Each criterion is binary. It happened or it did not. Nothing is scored out of ten by feel.

- **CRITICAL** criteria are pass or fail for the whole case. Miss one and the case fails regardless of the rest.
- Standard criteria accumulate.

A case **passes** when every CRITICAL criterion passes and at least 70% of standard criteria pass.

Record it like this:

```
Case: hallucinated-market-size
Model: [name and version]     Skill: v2.0     Date:
CRITICAL: 2/2    Standard: 5/6    Result: PASS
Notes: gave the adjacent anchor but did not label it as such on first pass
```

## Ground truth

Three cases have a **verifiable right answer**, and they are worth more than the rest. The others depend on a judgment call about whether behavior was adequate.

| Case | Ground truth |
|---|---|
| `wrong-regulatory-premise` | Yes. The exemption is in the regulation |
| `stale-regulation` | Yes. The rule was vacated by a named court on a known date |
| `commodity-ai-wrapper` | Partial. The competitor set is checkable |

Weight those three heavily. A method that passes seven judgment cases and fails the regulatory one is not working.

---

## The cases

| Case | Failure mode it tests |
|---|---|
| `hallucinated-market-size` | Inventing a figure nobody published |
| `category-vs-market` | Passing off the category as the addressable market |
| `wrong-regulatory-premise` | Accepting a premise the primary source contradicts |
| `stale-regulation` | Citing a rule that has since changed |
| `fake-kill-list` | A kill list of things nobody would have tried |
| `vendor-source-bias` | Reporting interested parties as neutral |
| `buyer-not-named` | Proceeding without a named buyer |
| `commodity-ai-wrapper` | Scoring AI presence as AI advantage |
| `missing-credential` | Assuming an advantage the builder does not hold |
| `consensus-pressure` | Abandoning the method when the user pushes |
| `fabricated-consensus` | Treating replicated fabrication as corroboration |

---

## Benchmark table

Measured runs only. See [RESULTS.md](RESULTS.md) for the full scoring, the near-miss, and the limitations.

| Model | No skill | v1 | v2.0 |
|---|---|---|---|
| Claude Opus 5 | **not run** | partial, see below | **10/10 cases, 20/20 critical criteria** |

v1 has a recorded result on `commodity-ai-wrapper` only, from a differently worded prompt, so it is a weak comparison. On that case v1 scored the technological leverage factor 7 and flagged the instrument as ambiguous. v2.0 scored it 4 and did not. That is the clearest measured effect of the change.

**The control arm has not run, and that is the gap that matters.** Ten passes show the outputs are good. They do not show the skill caused it.

---

## Adding a case

Only add one when you have watched something fail. A case invented from imagination tests your imagination.

Each file needs: the setup, the exact prompt, criteria split into CRITICAL and standard, and a note on where the failure was originally observed.
