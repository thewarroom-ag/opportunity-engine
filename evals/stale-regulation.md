# Stale regulation

**Ground truth: yes.** The rule was vacated by a named court on a known date.

Tests whether the model checks that a regulation is still in force, rather than assuming a rule it read about is live.

## Origin

Observed 15 August 2026. A sourcing run identified this as the strongest dated regulatory opening available, then discovered the rule had been vacated sixteen days earlier and killed its own best candidate.

## Setup

```
Capital ceiling: $150,000
Time to first revenue: 6 months
Geography: US only
Interest areas: recurring revenue, compliance services
Unfair advantages: none stated
```

## Prompt

> There is a FinCEN rule requiring reporting on non-financed residential real estate transfers, with the filing duty on the settlement agent. Analyze a compliance service selling to title and settlement agents who now have to file.

## The right answer

The rule took effect for closings on or after 1 March 2026. On 19 March 2026 the US District Court for the Eastern District of Texas, in *Flowers Title Companies, LLC v. Bessent*, vacated it in its entirety under the Administrative Procedure Act. FinCEN then stated that reporting persons are not currently required to file and face no liability while the order stands.

**The demand was removed by a court.** The catalyst runs against the business.

## CRITICAL

- [ ] Establishes the rule's current status rather than assuming it is in force
- [ ] Finds that it was vacated, or explicitly flags that it could not confirm current status and treats the thesis as unverified

## Standard

- [ ] Names the court, the case, or the date
- [ ] States that the catalyst runs against the opportunity
- [ ] Kills the candidate, or makes the verdict contingent on the rule being reinstated
- [ ] Notes what would revive it, such as an appellate reversal or a replacement rule

## Fail conditions

- Sizes and recommends the opportunity as though the rule is live
- Treats the effective date as sufficient evidence of current force
- Mentions litigation risk generically without finding the actual vacatur
