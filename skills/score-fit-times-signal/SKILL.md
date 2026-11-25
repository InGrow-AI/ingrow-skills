---
name: score-fit-times-signal
description: Rank a list of accounts by multiplying how well each fits the ICP by how fresh its strongest buying signal is (funding, hiring for the team you sell to, headcount growth). Use when the user has accounts and asks which to work first.
---

# Score fit times a fresh signal

Fit says who could buy; a fresh signal says who is likely to buy now. Ranking by the product of both puts the few accounts worth a call this week at the top.

## Before you start

Ask the user for anything below that they have not given you:

- The list of accounts (names or domains).
- The team or function they sell into, for example sales, engineering or finance.
- Industry, size and region that define a perfect fit.

## Steps

1. Read size, industry and headcount growth for each account, and the growth of the team they sell into.  
   InGrow tool `linkedinGetCompanyInsights` (`POST /public-api/linkedin/get-company-insights`), $0.005 per call.
2. Search open roles in that function at each account posted in the last month.  
   InGrow tool `linkedinSearchJobs` (`POST /public-api/linkedin/search-jobs`), $0.001 per call.
3. Check for a Form D filed in the last 6 months by each account.  
   InGrow tool `secSearchFormD` (`POST /public-api/sec/search-form-d`), $0.006 per call.

## What to return

- Fit score 0 to 5 from industry, size and region. Signal score 0 to 5 from the freshest signal: Form D in 90 days = 5, three or more open roles in the target function = 4, target team grew more than 20% in 6 months = 3.
- A table sorted by fit × signal, with the signal written out in plain words and its date.

## Cost

About $0.007 per account ($0.005 insights, $0.001 job search, $0.006 Form D search shared across accounts when you search by industry).

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Search Form D once by industry and date and match the results to the list, instead of one search per account.
- Never invent a signal. An account with none gets a signal score of 0.
