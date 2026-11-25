---
name: competitor-ad-watch
description: Pull a competitor's live ads from the Meta Ad Library and summarize their offers, hooks and how long each ad has run. Use when the user asks what a competitor is advertising or wants ad ideas.
---

# Competitor ad watch

An ad that keeps running is an ad that works. Long-running ads show which message a competitor has proven with its own budget.

## Before you start

Ask the user for anything below that they have not given you:

- Competitor names and the country (default US).

## Steps

1. Find each competitor's advertiser page id.  
   InGrow tool `facebookSearchAdvertisers` (`POST /public-api/facebook/search-advertisers`), $0.003 per call.
2. Pull their active ads for the country.  
   InGrow tool `facebookGetAdvertiserAds` (`POST /public-api/facebook/get-advertiser-ads`), $0.003 per call.

## What to return

- Each competitor's ads grouped by offer or angle, with the hook, start date and how long it has run.
- The three longest-running messages and what they suggest about what converts.

## Cost

$0.003 per call.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.
