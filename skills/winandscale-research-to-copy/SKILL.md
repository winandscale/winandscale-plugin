---
name: winandscale-research-to-copy
description: Turn customer research into ad copy in Win & Scale — personas and angles, what each has bought, real customer verbatims, then drafted messaging. Use when the user wants copy, hooks or messaging for a persona or angle.
---

# Research to copy

1. **Who and why.** `meta_list_personas` and `meta_list_angles`.
2. **What each bought.** `meta_get_strategy_rollup` shows spend and results by
   persona and angle, so copy leans on what has worked.
3. **Their words.** `meta_list_verbatims` returns exact customer quotes from
   reviews and pages. Use them as written; never invent a quote.
   `meta_list_research_sources` shows where they came from. New sources (app
   reviews, a page, pasted reviews) are added by a person in Settings ›
   Customer research (https://winandscale.com/app/settings/research).
4. **Draft.** `meta_draft_messaging` writes hooks, headlines, primary texts
   and objection handlers for one angle, each citing the quotes it came from.

The lines land as drafts: a person approves them on the Research page before
they prefill a launch. Launching is `launch-paused`, and ads go live only on
the user's word.
