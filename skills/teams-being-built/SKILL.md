---
name: teams-being-built
description: Find companies hiring several people in the function the user sells to, a sign that a new team and budget exist. Use when the user wants hiring signals or asks which companies are building a sales, data, security or other team.
---

# Teams being built

One job post is noise. Three or more open roles in the same function means a team is being built, and a team being built needs tools.

## Before you start

Ask the user for anything below that they have not given you:

- The function and role titles to look for, for example SDR, account executive, data engineer.
- Locations and how recent the posts should be.

## Steps

1. Search LinkedIn jobs for each role title, posted in the last month.  
   InGrow tool `linkedinSearchJobs` (`POST /public-api/linkedin/search-jobs`), $0.001 per call.
2. Search the same titles across Indeed, Glassdoor and company career pages to catch roles not on LinkedIn.  
   InGrow tool `jobsSearchJobs` (`POST /public-api/jobs/search-jobs`), $0.003 per call.
3. For companies with three or more matching roles, read headcount growth of that function.  
   InGrow tool `linkedinGetCompanyInsights` (`POST /public-api/linkedin/get-company-insights`), $0.005 per call.

## What to return

- Companies ranked by open roles in the function, with the role titles, locations and posting dates.
- The current size of the team and its growth, so the user can see how early they are.

## Cost

$0.001 per LinkedIn search page, $0.003 per job board search, $0.005 per company insight.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Group roles by company name carefully: staffing agencies post on behalf of others. Leave agencies out unless the user wants them.
