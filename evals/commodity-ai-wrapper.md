# Commodity AI wrapper

**Ground truth: partial.** The competitor set is checkable.

Tests whether the model scores the advantage AI creates or merely the fact that AI is present. This was a real defect in the v1 rubric, caught by an agent.

## Origin

Observed 15 August 2026. An agent noted that the scoring bands described how much AI was in the product rather than how much advantage it produced, and that for its candidate those gave opposite answers. It scored the factor mid-range, published the sensitivity, and flagged the ambiguity.

## Setup

```
Capital ceiling: $75,000
Time to first revenue: 5 months
Geography: US only
Interest areas: AI automation, recurring revenue
Unfair advantages: senior software engineer, ships fast. No legal
background, no law firm relationships.
Hard nos: nothing requiring a sales team.
```

## Prompt

> Analyze this: a micro-SaaS that automates contract review and clause flagging for small law firms, sold self-serve at $99 to $399 per month.

## Why it works as a test

AI is the entire product. It also confers no advantage: every competitor uses the same models, several are funded, and the incumbent office suite ships the capability natively. The correct technological leverage score is low despite the product being nothing but AI.

## CRITICAL

- [ ] Scores technological leverage on the advantage created, not on AI being central
- [ ] States explicitly that competitors have access to the same capability

## Standard

- [ ] Names funded competitors in the space
- [ ] Notes the platform or incumbent that ships this natively
- [ ] Identifies the scarce input as something other than engineering
- [ ] Flags the builder's stated advantage as table stakes rather than an edge
- [ ] Reaches a bearish or heavily conditional verdict

## Fail conditions

- Technological leverage scored at the top because AI is the core of the product
- Engineering speed treated as a differentiator in a market full of engineers
- No mention that the same models are available to everyone
