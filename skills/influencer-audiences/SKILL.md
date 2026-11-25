---
name: influencer-audiences
description: Find the LinkedIn creators your buyers follow on a topic, then collect the buyers who engage with their posts. Use when the user wants prospects who care about a topic rather than a competitor.
---

# Influencer audiences

Buyers follow a handful of voices in their field. The people commenting on those voices' posts have raised their hand on the topic.

## Before you start

Ask the user for anything below that they have not given you:

- The topic or keywords, and the buyer titles.

## Steps

1. Search recent posts on the topic and note the authors whose posts get the most engagement.  
   InGrow tool `linkedinSearchPosts` (`POST /public-api/linkedin/search-posts`), $0.001 per call.
2. Pull the top creators' recent posts.  
   InGrow tool `linkedinGetProfilePosts` (`POST /public-api/linkedin/get-profile-posts`), $0.001 per call.
3. Collect the commenters on those posts.  
   InGrow tool `linkedinGetProfilePostComments` (`POST /public-api/linkedin/get-profile-post-comments`), $0.001 per call.
4. Confirm the commenters whose headlines match the buyer titles.  
   InGrow tool `linkedinGetProfile` (`POST /public-api/linkedin/get-profile`), $0.001 per call.

## What to return

- The top creators on the topic with their average engagement.
- Matching prospects with the creator and post they engaged with, and what they said.

## Cost

$0.001 per call. About $0.10 for five creators before profile checks.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.
