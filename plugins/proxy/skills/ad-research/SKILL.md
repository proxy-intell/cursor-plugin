---
name: ad-research
description: Research a brand's or competitor's live ads across Meta, Google, LinkedIn and TikTok using the Proxy MCP tools. Use when asked what a company is advertising, to compare competitors' ads, find ads by keyword, get a competitive brief, or analyze ad creatives.
---

# Ad research with Proxy

All data comes from the `proxy` MCP server. No API keys. First call triggers a one-time sign-in.

## Playbooks

For a research job, call `get_playbook` first and follow it: `script_writing` (video scripts, hooks), `competitor_teardown` (angles, offers, gaps), `product_hunt` (winning products, saturation), `who_is_advertising` (prospect lists), `competitor_watch` (what changed since last time).

## Which platform

No platform named → search Meta and Google. Brand not found on one platform → say so, try the others.

## Meta (Facebook / Instagram)

1. `get_meta_platform_id` with the brand name. Pick the top candidate (verified, most followers). If `may_be_inactive` is true, say the page may not be running ads.
2. `get_meta_ads` with the `page_id`.
3. Topic, not brand → `search_meta_ads_by_keyword`.

## Google

1. `get_google_platform_id` with the brand name or domain.
2. `get_google_ads` with the advertiser ID or domain.
3. `get_google_ad_details` with an `ad_url` for creative variations and targeting.

## LinkedIn

1. `search_linkedin_ads` by company name, keyword, or company ID.
2. `get_linkedin_ad_details` with a result `id` for targeting and impressions.
3. Pass `paginationToken` back as `pagination_token` for the next page.

## TikTok (EU ad library)

1. `search_tiktok_ads` with the registered advertiser name. Exact and case-sensitive ("Anysphere", not "Cursor").
2. `get_tiktok_ad_details` with a result `id`.

## Competitors and briefs

- Unknown competitors → `search_competitors` with a domain or description, then run the platform steps per competitor.
- One-shot overview → `get_competitive_brief`.
- Tracking → re-run `get_meta_ads` / `get_google_ads` with the same settings a day or more later; the result reports what changed since the last fetch.

## Creatives

- `analyze_ad_image` on any image URL from results.
- `analyze_ad_video` for transcript and visual breakdown. For TikTok pass `tiktok_id`, not the expiring `video_url`.
- Transcript requests always go to `analyze_ad_video`.

## Reporting

- Lead with what the brand is pushing: offers, hooks, formats, landing pages.
- Cite `ad_url` / `page_id` so the user can follow up.
- Show most of what was found; do not truncate to three.
- Rate-limited or out of credits → `get_credit_balance`, share the upgrade link it returns.
