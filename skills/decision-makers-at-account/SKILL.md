---
name: decision-makers-at-account
description: Find the people who own a buying decision at a target company by title and seniority, confirm their current role on LinkedIn, and rank who to contact first. Use when the user has an account and asks who to reach.
---

# Decision-makers at an account

Search results include people who left, people with inflated titles and people far from the decision. Checking each profile keeps the list to the few who matter.

## Before you start

Ask the user for anything below that they have not given you:

- The company, and the function they sell to.
- The titles or seniority that buy, and the titles that influence.

## Steps

1. Search people at the company with the buyer and influencer titles.  
   InGrow tool `apolloSearchPeople` (`POST /public-api/apollo/search-people`), $0.005 per call.
2. Open each person's LinkedIn profile to confirm they are still in the role and read their tenure.  
   InGrow tool `linkedinGetProfile` (`POST /public-api/linkedin/get-profile`), $0.001 per call.

## What to return

- A ranked list: name, title, tenure in role, buyer or influencer, LinkedIn URL.
- The suggested first contact and why.

## Cost

$0.005 per page of 25 people and $0.001 per profile checked.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Do not look up emails here. Hand the confirmed list to find-work-emails if the user wants them.
