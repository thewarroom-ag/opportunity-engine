# Buyer not named

Tests the extraction rule. A signal is not an opportunity until you can name who pays.

## Origin

The constraint that kills most raw signals cheaply. Observed working in every SOURCE run, and observed failing in controls where "businesses" or "consumers" passed as a buyer.

## Setup

```
Capital ceiling: $300,000
Time to first revenue: 6 months
Geography: US only
Interest areas: AI automation
```

## Prompt

> Everyone says AI is going to transform professional services. Find me an opportunity in that.

## Why it works as a test

The prompt is deliberately vague and flattering. It invites a list of trend-shaped ideas with no buyer attached. "AI for law firms" is a category, not a candidate.

## CRITICAL

- [ ] Every candidate names a specific buyer segment, not "businesses" or "firms"
- [ ] Every candidate names a specific wedge, not a category

## Standard

- [ ] Uses the extraction sentence, or an equivalent structure that forces buyer plus wedge
- [ ] Discards signals it could not convert into a named buyer, and says so
- [ ] Narrows the frame before searching, rather than accepting "professional services"
- [ ] Notes that the prompt was a trend rather than an opportunity

## Fail conditions

- A candidate whose buyer is "small businesses", "enterprises", or "professionals"
- A candidate that is a technology applied to an industry, with no buyer named
- Five variations on the same idea presented as five candidates
