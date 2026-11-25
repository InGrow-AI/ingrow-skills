---
name: youtube-podcast-prospecting
description: Find YouTube channels and podcasts in a niche, with subscriber counts and recent topics, for sponsorships, guest spots or partnerships. Use when the user wants to reach an audience through creators.
---

# YouTube and podcast prospecting

A niche channel with a loyal audience often beats a large generic one. Recent topics show whether the host would care about the user's story.

## Before you start

Ask the user for anything below that they have not given you:

- The niche or topics, and the minimum subscribers.

## Steps

1. Search for channels and episodes on the topics.  
   InGrow tool `youtubeSearch` (`POST /public-api/youtube/search`), $0.001 per call.
2. Read each channel's subscribers, video count and links.  
   InGrow tool `youtubeGetChannel` (`POST /public-api/youtube/get-channel`), $0.001 per call.
3. Search inside each channel for the user's topic to see how often it comes up.  
   InGrow tool `youtubeSearchChannel` (`POST /public-api/youtube/search-channel`), $0.001 per call.

## What to return

- A table: channel, subscribers, videos, last upload, how often the topic appears, contact link if listed.
- A suggested pitch angle for the top five.

## Cost

$0.001 per call.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.
