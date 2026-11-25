---
name: competitor-post-engagers
description: Collect the people who reacted to and commented on a competitor's recent LinkedIn posts, then keep the ones who match the buyer profile. Use when the user names competitors and wants warm prospects.
---

# People engaging with competitors

People who engage with a competitor's posts are already in market. Commenters show more intent than reactors, and new ones appear every week.

## Before you start

Ask the user for anything below that they have not given you:

- Competitor LinkedIn company usernames.
- Buyer titles and seniority, and how far back to look (default 30 days).

## Steps

1. Pull each competitor's recent posts.  
   InGrow tool `linkedinGetCompanyPosts` (`POST /public-api/linkedin/get-company-posts`), $0.001 per call.
2. Get the comments on each post in the window.  
   InGrow tool `linkedinGetCompanyPostComments` (`POST /public-api/linkedin/get-company-post-comments`), $0.001 per call.
3. Get the people who reacted to the posts with the most engagement.  
   InGrow tool `linkedinGetPostReactions` (`POST /public-api/linkedin/get-post-reactions`), $0.001 per call.
4. Open the profiles whose headline matches the buyer titles to confirm role and company.  
   InGrow tool `linkedinGetProfile` (`POST /public-api/linkedin/get-profile`), $0.001 per call.

## What to return

- Prospects grouped by commenters and reactors: name, title, company, which competitor post, what they said if they commented.
- Remove the competitor's own employees.

## Cost

$0.001 per call. A competitor with 10 posts costs about $0.05 before profile checks.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Filter by headline before opening profiles to keep cost down.
