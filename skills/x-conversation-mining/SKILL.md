---
name: x-conversation-mining
description: Search X for people describing a problem the user solves, then qualify the accounts by bio and follower count. Use when the user wants prospects who are talking about a pain in public.
---

# X conversation mining

People complain about tools and ask for recommendations on X every day. A reply that helps, sent within a day, lands better than any cold email.

## Before you start

Ask the user for anything below that they have not given you:

- Phrases that describe the problem, for example 'looking for an alternative to' plus a competitor.
- Who counts as a buyer.

## Steps

1. Search the latest posts for each phrase.  
   InGrow tool `twitterSearch` (`POST /public-api/twitter/search`), $0.001 per call.
2. Read each author's bio, follower count and location.  
   InGrow tool `twitterGetUser` (`POST /public-api/twitter/get-user`), $0.001 per call.
3. For the strongest posts, read the replies to see which vendors already answered.  
   InGrow tool `twitterGetTweetReplies` (`POST /public-api/twitter/get-tweet-replies`), $0.001 per call.

## What to return

- A list: author, bio, followers, post text, link, posted time, whether a competitor already replied.
- A suggested helpful reply for each, without a pitch in the first message.

## Cost

$0.001 per call.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Leave out posts older than a week; the moment has passed.
