---
name: glassdoor-team-pains
description: Read a company's Glassdoor reviews filtered to the team the user sells to and pull out recurring complaints about tools, process and workload. Use for account research or personalized outreach.
---

# Team pains from Glassdoor

Employees write plainly about broken tools and processes. A complaint repeated across reviews is a problem the team's leader already knows about.

## Before you start

Ask the user for anything below that they have not given you:

- The company name, and the team or role the user sells to.

## Steps

1. Find the company's Glassdoor id.  
   InGrow tool `glassdoorSearchCompanies` (`POST /public-api/glassdoor/search-companies`), $0.001 per call.
2. Read size, ratings and CEO approval.  
   InGrow tool `glassdoorGetCompanyOverview` (`POST /public-api/glassdoor/get-company-overview`), $0.001 per call.
3. Read the most recent reviews and keep the ones from the target team.  
   InGrow tool `glassdoorGetCompanyReviews` (`POST /public-api/glassdoor/get-company-reviews`), $0.001 per call.

## What to return

- Recurring themes with counts and short quotes, and the ratings trend.
- One outreach angle grounded in a theme, written without quoting a reviewer by name.

## Cost

$0.001 per call.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Reviews are anonymous. Never try to identify a reviewer.
