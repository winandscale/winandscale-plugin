---
name: winandscale-brief-and-test
description: Run Win & Scale's creative learning loop on Meta — brief the next test, commit it with a frozen hypothesis, hand the brief to whoever makes the creative, launch the uploads paused, observe, and conclude. Use when the user wants to plan a creative test, check a running test, or record what one showed.
---

# Brief and test

1. **What is already known.** `meta_list_tests` and `meta_get_test`: concluded
   tests, failures included, are the prior for the next one.
2. **Brief.** Start from `nextTests` in `meta_get_history_winners`, or the
   user's idea. Save it with `meta_save_briefs`; `meta_list_briefs` shows
   saved ones.
3. **Commit.** `meta_create_test` freezes the hypothesis and the rule it will
   be judged by. A committed test is never rewritten: to change it, abandon it
   (`meta_abandon_test`) and create a new one.
4. **Hand off, then launch.** Win & Scale doesn't make images or video: the
   creative is produced outside it, by a designer, a UGC creator or the user's
   own tool. Hand over the brief (`meta_get_brief`) and, for a static, the
   reference's recipe (`meta_get_recipe`: format, layout, copy and which slots
   are replaceable). Once the user has the files, launch them with
   `meta_launch_ads`, passing the test's `testId` (and the `briefId`); ads
   launch **paused**, and switching them on is the user's call
   (`launch-paused`). `meta_link_test_artifacts` attaches uploads, ads or
   launches made elsewhere, such as in Ads Manager.
5. **Observe.** After delivery, `meta_observe_test` appends what the numbers
   show. Observations are append-only.
6. **Conclude.** `meta_conclude_test` with supported, rejected, inconclusive or
   invalid. Low delivery means inconclusive, not rejected.

Tests, briefs and observations never change what is delivering.
