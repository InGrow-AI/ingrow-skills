---
name: account-research-brief
description: Produce a one-page brief on a company before a call: headcount and growth, recent LinkedIn posts, open roles, website traffic, tech stack and review ratings. Use when the user says they have a meeting or wants to research an account.
---

# Account research brief

Five minutes of reading the right sources beats an hour of browsing. The brief shows what changed recently, which is what to talk about.

## Before you start

Ask the user for anything below that they have not given you:

- The company name, LinkedIn username and domain.
- What the user sells.

## Steps

1. Headcount, growth and function breakdown.  
   InGrow tool `linkedinGetCompanyInsights` (`POST /public-api/linkedin/get-company-insights`), $0.005 per call.
2. What the company posted in the last 30 days.  
   InGrow tool `linkedinGetCompanyPosts` (`POST /public-api/linkedin/get-company-posts`), $0.001 per call.
3. Open roles at the company.  
   InGrow tool `linkedinSearchJobs` (`POST /public-api/linkedin/search-jobs`), $0.001 per call.
4. Website visits and traffic sources.  
   InGrow tool `webTrafficGetWebsiteTraffic` (`POST /public-api/web-traffic/get-website-traffic`), $0.001 per call.
5. Tools on the website.  
   InGrow tool `techStackDetectTechnologies` (`POST /public-api/tech-stack/detect-technologies`), $0.005 per call.
6. If they sell software, their G2 rating and pros and cons.  
   InGrow tool `reviewsGetG2Product` (`POST /public-api/reviews/get-g2-product`), $0.004 per call.

## What to return

- A one-page brief: snapshot, what changed recently, hiring, digital presence, tools, and three questions to ask on the call.

## Cost

About $0.02 per company.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Say which sources returned nothing rather than leaving gaps unexplained.
