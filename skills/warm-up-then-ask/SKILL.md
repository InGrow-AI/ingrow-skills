---
name: warm-up-then-ask
description: Read a prospect's recent posts and the posts they react to, then plan two or three genuine touches before the ask. Use when the user wants to reach a senior person who ignores cold messages.
---

# Warm up, then ask

Senior buyers answer people they recognise. A couple of useful comments on their posts turns a cold name into a familiar one.

## Before you start

Ask the user for anything below that they have not given you:

- The prospect's LinkedIn username.
- What the user wants to eventually ask for.

## Steps

1. Read the prospect's recent posts.  
   InGrow tool `linkedinGetProfilePosts` (`POST /public-api/linkedin/get-profile-posts`), $0.001 per call.
2. Read the posts they recently reacted to, to learn what they care about.  
   InGrow tool `linkedinGetProfileReactions` (`POST /public-api/linkedin/get-profile-reactions`), $0.001 per call.

## What to return

- The prospect's three main themes, with evidence.
- A plan of three touches over about two weeks: which post to comment on and a draft comment for each, then the ask.

## Cost

$0.002 per prospect.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Comments must add something: a fact, an experience, a question. No flattery-only comments.
