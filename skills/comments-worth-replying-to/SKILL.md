---
name: comments-worth-replying-to
description: Go through the comments on the user's own recent LinkedIn posts and surface the commenters who match the buyer profile, with a suggested reply. Use when the user posts on LinkedIn and wants to turn engagement into conversations.
---

# Comments worth replying to

The warmest leads are already in your comments. Replying with care and following up in a message converts better than any cold list.

## Before you start

Ask the user for anything below that they have not given you:

- The user's LinkedIn username.
- Buyer titles.

## Steps

1. Pull the user's posts from the last 30 days.  
   InGrow tool `linkedinGetProfilePosts` (`POST /public-api/linkedin/get-profile-posts`), $0.001 per call.
2. Get the comments on each post.  
   InGrow tool `linkedinGetProfilePostComments` (`POST /public-api/linkedin/get-profile-post-comments`), $0.001 per call.
3. Open profiles of commenters whose headline matches a buyer title.  
   InGrow tool `linkedinGetProfile` (`POST /public-api/linkedin/get-profile`), $0.001 per call.

## What to return

- Buyers who commented, with their comment, a suggested public reply and a suggested follow-up message.

## Cost

$0.001 per call.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.
