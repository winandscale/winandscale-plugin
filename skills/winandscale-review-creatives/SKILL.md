---
name: winandscale-review-creatives
description: Review what each creative in a Meta ad account is in Win & Scale — its angle, persona, format, hook, offer and pain Values — and correct or merge them. Use when the user wants to see creatives, check tagging, fix a wrong label, or tidy the taxonomy.
---

# Review creatives

1. `meta_list_creatives` lists creatives with their Values, the classifier's
   confidence, and performance. Filter to what the user asked about.
2. `meta_get_creative` to look at one in detail. For a video read from its
   poster frame only, say so: no claim about scenes is possible.
3. `meta_list_taxonomy` (or `meta_list_personas`, `meta_list_angles`,
   `meta_list_formats`) for the names in use.
4. **Correct, on the user's word.** `meta_set_creative_links` sets one
   creative's Values; `meta_tag_creatives` applies Values to several.
   `meta_update_taxonomy_value` renames or describes a Value;
   `meta_merge_taxonomy_values` folds two names for one idea into one. These
   overwrite stored labels, so confirm the exact change first.

Corrections change how every later analysis groups spend, never what is
delivering.
