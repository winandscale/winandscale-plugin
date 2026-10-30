---
name: winandscale-what-worked
description: Explain what has worked in a Meta ad account in Win & Scale — which angles, personas, formats and hooks bought more than their spend, with the evidence and its limits. Use when the user asks what worked, which creatives win, or what to learn from past ads.
---

# What worked

1. **Evidence first.** `meta_get_evidence_health`. Quote its warnings before
   any number.
2. **History.** `meta_get_account_history` for lifetime totals per ad. If it is
   empty, `meta_pull_account_history` and wait.
3. **Verdicts.** `meta_get_history_winners` with the window the user asked for
   (30, 90 or 180 days, or lifetime). It returns verdicts per ad, the Traits
   that bought more than their share of spend, and `nextTests`, each with its
   `basis`, `limits`, `reverseIf` and `prior` (what earlier tests on the same
   lesson concluded).
4. **Pivot.** `meta_get_cross_analysis` crosses two Dimensions (angle by
   persona, format by hook) within one funnel; `meta_get_performance_cube`
   splits by ad set or country.

Say what each finding rests on: spend, number of ads, days. Low delivery is
inconclusive. Everything is observational, so phrase findings as association
and point to a test (`brief-and-test`) to confirm the important ones. Report
purchases and ROAS only where the purchase pixel fired.
