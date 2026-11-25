---
name: comment-first
description: Find this week's posts from a list of prospects and draft a thoughtful comment for each, ranked by how much engagement the post is getting. Use for a daily or weekly LinkedIn engagement routine.
---

# Comment first

Commenting on a post while it is still being read puts your name in front of the author and their audience, at no cost to the relationship.

## Before you start

Ask the user for anything below that they have not given you:

- The prospects' LinkedIn usernames.
- The user's point of view or expertise, so comments sound like them.

## Steps

1. Pull each prospect's posts from the last 7 days.  
   InGrow tool `linkedinGetProfilePosts` (`POST /public-api/linkedin/get-profile-posts`), $0.001 per call.
2. For the posts worth a comment, read the full text and engagement counts.  
   InGrow tool `linkedinGetPost` (`POST /public-api/linkedin/get-post`), $0.001 per call.

## What to return

- Posts ranked by recency and engagement, each with a link and a draft comment of two or three sentences.

## Cost

$0.001 per prospect plus $0.001 per post opened.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Skip posts that are announcements of loss, layoffs or personal news unless a short supportive note fits.
