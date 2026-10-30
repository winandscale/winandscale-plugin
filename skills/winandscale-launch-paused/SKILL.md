---
name: winandscale-launch-paused
description: Launch new Meta ads through Win & Scale — campaign, ad set and ads created paused for review — and switch them on only on the user's explicit go-ahead. Use when the user wants to launch ads, put a test live, or activate a launch.
---

# Launch paused

1. **Where.** `meta_list_campaigns` to reuse a campaign or start a new one.
   If the brief names a Facebook Page or pixel, `meta_list_pages_and_pixels`.
2. **Names.** Every ad name must follow
   `id__locale__format__persona__angle__concept__variant`; a launch with a name
   that does not parse is refused. `meta_list_taxonomy` has the slugs.
3. **Launch.** `meta_launch_ads` with public creative URLs (and `testId` when
   the ads belong to a test). Everything is created **paused**: nothing spends.
4. **Review.** The user checks the launch in Meta Ads Manager or on the
   Launches page in Win & Scale. `meta_list_launches` shows its state.
5. **Activate only on the user's word.** `meta_activate` turns spend on. Call
   it only when the user says so in this conversation, after you have restated
   what will go live and its daily budget. A request to "launch" is not a
   request to activate.

`meta_pause_launch` pauses a launch's ads again. `meta_relink_launch` changes
the call to action, destination URL or ad text on every ad of a launch; active
ads go back through Meta's review and lose their likes and comments, so
confirm first.
