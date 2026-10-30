---
name: winandscale-live-ads-check
description: Check how live Meta ads are doing in Win & Scale and what to do with each — cut, keep, duplicate, iterate or watch — judged on each ad's own goal. Use when the user asks how ads are doing now, which to pause or scale, or why an ad set is underperforming.
---

# Live ads check

1. **Freshness.** `meta_get_overview` returns `lastSyncedAt` and the account's
   recent numbers. If the sync is stale, offer `meta_sync_now`;
   `meta_backfill_insights` fills older days. Quote `coverage`: days before it
   read as zero, not as "no spend".
2. **Verdicts.** `meta_suggest_next` gives cut, keep, duplicate, iterate or
   watch for each ad, on its own goal. The targets behind it are set with
   `meta_set_thresholds`.
3. **Why.** `meta_get_ad_performance` for one ad's trend; `meta_get_breakdowns`
   for age, country and placement.
4. **Act only on the user's word.** A `cut` is advice: list the ads and let
   the user pick. Pausing is `meta_set_ad_status` with PAUSED; setting ACTIVE
   spends money and needs an explicit go-ahead. Targeting fixes
   (`meta_update_ad_set_targeting`) restart Meta's learning phase: confirm the
   ad set and the exact values, one ad set per call.

Report purchases and ROAS only where the purchase pixel fired. Low delivery is
inconclusive.
