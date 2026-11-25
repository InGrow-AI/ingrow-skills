---
name: tiktok-ad-angles
description: Pull the top performing TikTok ads in an industry or for a keyword and break down their hooks, formats and calls to action. Use when the user is planning TikTok ads or creative.
---

# TikTok ad angles

TikTok's Creative Center ranks ads by real performance. Studying the top ones in your category shows which hooks hold attention in the first seconds.

## Before you start

Ask the user for anything below that they have not given you:

- The industry or keyword, the country and the objective (traffic, conversions, app installs).

## Steps

1. Get the top ads for the filters.  
   InGrow tool `tiktokGetTopAds` (`POST /public-api/tiktok/get-top-ads`), $0.003 per call.
2. Open the top ten for their metrics and details.  
   InGrow tool `tiktokGetAdDetails` (`POST /public-api/tiktok/get-ad-details`), $0.003 per call.

## What to return

- A table: ad, brand, hook in the first line, format, CTA, CTR or other metrics shown.
- Five hook patterns that repeat across the winners, each with an example.

## Cost

$0.003 per call.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.
