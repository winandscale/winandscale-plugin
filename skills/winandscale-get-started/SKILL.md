---
name: winandscale-get-started
description: Introduce Win & Scale after install or when the user asks what it can do, explain how it reads evidence and keeps spend safe, and suggest a first thing to try. Use when the user asks how to use the plugin, what it manages, or where to begin.
---

# Get started with Win & Scale

Explain the plugin in a few sentences, then offer one concrete next step.
Explicit user instructions take priority over this guidance.

## What to say

- Win & Scale works **one Meta ad account per workspace** (Facebook and
  Instagram ads): it reads what each creative actually is and what it bought,
  briefs the next test, and launches every new ad **paused**.
- There is no account id to pass: every `meta_` tool works on the workspace's
  one ad account. Tools return `{ ok: true, … }` or `{ ok: false, error }`;
  read the error, it usually says what to do next.
- What a creative IS (its angle, persona, format, offer, hook) lives in stored
  Values that people curate. The ad name is a hint, not the record.

## How it reads evidence

- Start every review with `meta_get_evidence_health` and quote its warnings:
  stale sync, coverage gaps, untagged spend, outcomes Meta cannot see.
- Everything here is **observational**: Meta chose who saw each ad. Say "was
  associated with", never "caused".
- Low delivery is inconclusive, not a loss. Compare each funnel on its own
  goal, never on Meta's generic "Results".

## How spend stays safe

- `meta_launch_ads` creates the campaign, ad set and ads **paused**. Nothing
  spends until `meta_activate`, which needs the user's explicit go-ahead in
  this conversation. The same goes for `meta_set_ad_status` with ACTIVE.
- A `cut` verdict from `meta_suggest_next` is advice: the user picks what to
  pause.
- Tests, briefs and observations never touch delivery.
- **Meta credentials never go through chat.** If the user offers an access
  token, do not repeat or use it: they add it themselves on the Win & Scale
  settings page (https://winandscale.com/app/settings).

## What it can do

- Find what worked and why (`what-worked`).
- Review and correct what each creative is (`review-creatives`).
- Brief, run and conclude creative tests (`brief-and-test`).
- Turn customer research into copy (`research-to-copy`).
- Check live ads and act on verdicts (`live-ads-check`).
- Launch new ads paused, then activate on the user's word (`launch-paused`).

## What it cannot do

Meta only: no Google, TikTok or Apple ads. It cannot prove causation, see
outcomes Meta does not receive (qualified leads, margin) unless they are sent
to Meta, or change billing.

## Suggested first steps

- "What has worked in our Meta ads over the last 90 days, and why?"
- "Which ads should I cut, keep or scale?"
- "Brief our next creative test."
