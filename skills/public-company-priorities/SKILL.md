---
name: public-company-priorities
description: Read a public company's latest 10-K or 10-Q risk factors and management discussion to pull out its stated priorities and problems. Use when the user is planning an account or writing outreach to a listed company.
---

# Public company priorities

Executives tell investors what they are investing in and what worries them. Quoting their own words is the most credible way to open a conversation.

## Before you start

Ask the user for anything below that they have not given you:

- The company or ticker.
- What the user sells, so you can map priorities to it.

## Steps

1. Find the latest 10-K and 10-Q for the ticker.  
   InGrow tool `secSearchFilings` (`POST /public-api/sec/search-filings`), $0.006 per call.
2. Extract item 1A (risk factors) and item 7 (MD&A) from the 10-K, and part2item1a from the latest 10-Q.  
   InGrow tool `secExtractFilingItem` (`POST /public-api/sec/extract-filing-item`), $0.006 per call.

## What to return

- Five stated priorities and five stated risks, each with a short quote and the filing it came from.
- Two or three of them mapped to what the user sells, as conversation openers.

## Cost

$0.006 per search and $0.006 per section extracted. About $0.024 per company.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Quote exactly and name the filing and date. Do not paraphrase a risk factor as a fact about the company.
