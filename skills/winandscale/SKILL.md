---
name: winandscale
description: Use Win & Scale from Claude Code — what worked in a Meta ad account and why, creative review and tagging, the brief-and-test loop, live-ad checks, and paused launches. Use when the user asks about Meta (Facebook or Instagram) ads managed in Win & Scale.
---

# Win & Scale

## Authorization

**OAuth** is how a person connects: the client discovers the authorization
server from the MCP URL and prompts in a browser. There is no token to copy.

**An `rsk_` API key** — the same key the REST API at `/api/v1` takes — is
the credential for a headless agent. Send it as `Authorization: Bearer rsk_…`.
Its scope may be narrower than an OAuth session, and revoking it stops MCP and
REST together.

You are connected to Win & Scale. The authenticated workspace holds ONE Meta ad account, read from a nightly warehouse, written to as PAUSED drafts. Tools are `meta_*` and return `{ ok: true, ... }` or `{ ok: false, error }`.

## Orientation
- A session reaches the whole workspace (an `rsk_` key may be narrower). Call `meta_get_workspace` first: `adAccountId` is the account every call hits (`meta_switch_workspace` changes it).
- Money is real. `meta_launch_ads` creates campaign, ad set and ads PAUSED; `meta_activate` is the money-moving flip and needs the human's go-ahead.
- Two kinds of numbers. The WAREHOUSE (`meta_get_overview`, `meta_get_performance_cube`…) is daily; its `coverage` says from when; earlier days read zero, not "no spend". The HISTORY (`meta_get_account_history`) is lifetime per ad. `meta_get_history_winners` and `meta_get_cross_analysis` read either (`window`).
- What a creative IS lives in stored Values (angle, persona, offer, format, hook…); the ad name is a hint, not the record.
- Read `meta_get_strategy` and `meta_list_learnings` before any brief or copy. Save an operator's copy correction with `meta_update_strategy` (`mode: "suggest"`) or it is lost.

## Evidence first
Start every review with `meta_get_evidence_health` and quote its warnings (stale sync, coverage gaps, untagged spend, poster-only videos, unseen outcomes). Compare funnels on their own goal, not Meta's "Results". Low delivery is inconclusive, not a loss. Hook rate is not the goal.

## Golden paths
**What worked**: `meta_get_account_history` (`meta_pull_account_history` if empty) → `meta_get_history_winners({ window })`: verdicts, Traits, `nextTests`. `meta_get_cross_analysis` pivots two Dimensions; `meta_get_performance_cube` splits by ad set or country.

**Library** (/app/library) files: `meta_list_creatives` → `meta_get_creative` → `meta_tag_creatives` / `meta_set_creative_links` to correct, `meta_update_creative` renames, `meta_delete_creatives` removes. Values (audiences, messages, formats, offers…): `meta_list_taxonomy` → `meta_create_taxonomy_value` / `meta_update_taxonomy_value` (rename, archive) / `meta_merge_taxonomy_values` for two names of one idea. Copy: `meta_draft_messaging` or `meta_save_messaging` → `meta_set_messaging_status` (approve / reject; a rejected line is not redrafted).

**Briefs › Tests** — the learning loop: brief a Next test (`meta_save_briefs`, `meta_list_briefs`) → `meta_create_test` commits it (frozen hypothesis and rule) → the team makes the creative from the brief → `meta_launch_ads` with its `testId` (still PAUSED) → after delivery, `meta_observe_test` → `meta_conclude_test` with a verdict. Supersede a test, never rewrite it.

**Sources** (added in Settings › Customer research): `meta_list_research_sources` → `meta_list_verbatims` → `meta_link_verbatims` to a persona or angle → `meta_get_strategy_rollup`.

**Live ads**: `meta_get_overview` (`meta_sync_now` if stale, `meta_backfill_insights` for older days) → `meta_suggest_next` (cut / keep / duplicate / iterate / watch; targets via `meta_set_thresholds`) → `meta_get_breakdowns` (age / country / placement), fixed with `meta_update_ad_set_targeting` (restarts learning). Purchases and ROAS need the purchase pixel.

**Launch**: `meta_list_campaigns` → `meta_launch_ads` (`briefId` / `testId`; `meta_list_pages_and_pixels` for a Page) → show its `strategyCautions` → the human reviews in Ads Manager or Ads › Launches (/app/ads/launches) → `meta_activate`. Instant forms: `meta_list_lead_forms` / `meta_create_lead_form` → `OUTCOME_LEADS` with `adSet.leadForm` + `copy.leadFormId` → `meta_send_test_lead` before activating.

## Rules
- Ad names are `id__locale__format__persona__angle__concept__variant`; launching refuses one that does not parse.
- Never activate without the human saying so in this conversation; the same for `meta_set_ad_status` ACTIVE. A `cut` verdict is advice: the human picks what to pause.
- A test, a brief or an observation never touches delivery.
