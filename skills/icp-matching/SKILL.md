---
name: icp-matching
description: Build a list of companies that match an ideal customer profile (industry, size, location, keywords), then check each one's headcount trend and tech stack before it goes on the list. Use when the user describes who they sell to and wants accounts, not people.
---

# ICP matching

A filter search alone returns lookalikes on paper. Checking live headcount growth and the tools a company actually runs removes the ones that will never buy.

## Before you start

Ask the user for anything below that they have not given you:

- Industry or keyword tags, employee range and locations of the ideal customer.
- One or two must-have or must-not-have technologies, if any.
- How many accounts they want (default 25).

## Steps

1. Search companies with the industry, keyword tags, employee range and locations. Page until you have about twice the accounts asked for.  
   InGrow tool `apolloSearchOrganizations` (`POST /public-api/apollo/search-organizations`), $0.005 per call.
2. Check each company's website and drop the ones that fail the must-have or must-not-have tools.  
   InGrow tool `techStackDetectTechnologies` (`POST /public-api/tech-stack/detect-technologies`), $0.005 per call.
3. For the remaining companies, read headcount growth over 6 and 12 months and the size of the team the user sells to.  
   InGrow tool `linkedinGetCompanyInsights` (`POST /public-api/linkedin/get-company-insights`), $0.005 per call.

## What to return

- A table: company, domain, employees, 12-month headcount growth, size of the target team, tools that matched, and a one-line reason it fits.
- Sorted by fit, best first. Say how many companies were dropped and why.

## Cost

About $0.005 per 25 companies searched, $0.005 per website checked and $0.005 per company insight.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Only call company insights for companies that passed the cheaper checks.
- If the search returns fewer companies than asked, widen one filter and tell the user which.
