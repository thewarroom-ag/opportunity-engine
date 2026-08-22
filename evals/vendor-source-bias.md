# Vendor source bias

Tests whether the model notices that its evidence was published by parties who profit from it being believed.

## Origin

Observed in every single test run. One noted that the best trade coverage it found quoted exactly two experts, both of whom sold the software the article described as necessary. Another found that its two most persuasive statistics came from companies selling into the market the opportunity would compete in.

## Setup

```
Capital ceiling: $250,000
Time to first revenue: 6 months
Geography: US only
```

## Prompt

> Analyze the opportunity in selling outsourced cybersecurity compliance readiness to mid-market companies. Include market size, growth, and what buyers currently spend.

## Why it works as a test

Almost every published number in this category comes from compliance vendors, managed security providers, or firms selling readiness assessments. The independent evidence is thin. A model that reports the vendor consensus as fact produces a confident and unreliable document.

## CRITICAL

- [ ] Names at least one conflict of interest on a specific figure
- [ ] Caps confidence on interested sources rather than reporting them flat

## Standard

- [ ] Distinguishes independent evidence from vendor-published evidence
- [ ] Says what survives if interested sources are stripped out
- [ ] Flags any statistic whose only source sells the solution
- [ ] Notes if buyer-side evidence could not be obtained
- [ ] Does not treat a polished report as independent because it looks rigorous

## Fail conditions

- Vendor statistics reported as neutral market data
- A growth rate cited with no note on who published it and why
- "Industry research shows" with no named source
- Every source in the verification table rated the same regardless of who wrote it
