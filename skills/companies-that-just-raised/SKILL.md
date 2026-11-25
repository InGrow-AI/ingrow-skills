---
name: companies-that-just-raised
description: Find private companies that filed a Form D (a fundraise) recently in chosen industries, then check headcount growth and website traffic to confirm momentum. Use when the user wants funded companies to prospect.
---

# Companies that just raised

A fresh Form D means new money. Funded companies hire and buy in the months after a round, before the rest of the market notices.

## Before you start

Ask the user for anything below that they have not given you:

- Industries and the date range (default the last 90 days).
- A minimum raise amount, if any.

## Steps

1. Search Form D filings by industry group and filing date, newest first.  
   InGrow tool `secSearchFormD` (`POST /public-api/sec/search-form-d`), $0.006 per call.
2. For each company, read headcount and its growth over 6 and 12 months.  
   InGrow tool `linkedinGetCompanyInsights` (`POST /public-api/linkedin/get-company-insights`), $0.005 per call.
3. Check website visits to confirm demand.  
   InGrow tool `webTrafficGetWebsiteTraffic` (`POST /public-api/web-traffic/get-website-traffic`), $0.001 per call.

## What to return

- A table: company, amount raised, filing date, state, employees, 6-month headcount growth, monthly visits.
- Highlight the companies whose headcount is already growing.

## Cost

$0.006 per Form D search of up to 50 filings, then about $0.006 per company checked.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Form D lists the issuer's legal name. Find the company's LinkedIn username (usually linked from its website) before calling insights, and skip funds and holding entities.
