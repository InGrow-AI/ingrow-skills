---
name: leadership-change-alerts
description: Find public companies that just appointed or lost an executive, using 8-K item 5.02 filings, and identify the new leader. Use when the user wants to reach new executives in their first 90 days.
---

# Leadership change alerts

New leaders review vendors and set priorities in their first months. An 8-K item 5.02 filing is the official record of the change.

## Before you start

Ask the user for anything below that they have not given you:

- Industries or tickers to watch, and the date range (default the last 30 days).
- The roles that matter, for example CFO, CRO, CTO.

## Steps

1. Search 8-K filings with item 5.02 in the date range, filtered by industry or ticker.  
   InGrow tool `secSearchFilings` (`POST /public-api/sec/search-filings`), $0.006 per call.
2. Extract item 5.02 from each filing to read who joined or left, and in what role.  
   InGrow tool `secExtractFilingItem` (`POST /public-api/sec/extract-filing-item`), $0.006 per call.
3. Find the new leader's LinkedIn profile to read their background.  
   InGrow tool `linkedinGetProfile` (`POST /public-api/linkedin/get-profile`), $0.001 per call.

## What to return

- A list: company, ticker, filing date, person, role, joined or left, previous company.
- One sentence on what the new leader is likely to prioritize, based on their background.

## Cost

$0.006 per filing search and $0.006 per item extracted, plus $0.001 per profile.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Item 5.02 also covers board changes and compensation. Keep only the roles the user asked for.
