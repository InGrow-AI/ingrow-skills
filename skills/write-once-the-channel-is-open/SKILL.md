---
name: write-once-the-channel-is-open
description: Check which prospects have an open LinkedIn profile (messageable without a connection) and route them to a direct message, and the rest to a connection request first. Use before any LinkedIn outreach to a list.
---

# Write only once the channel is open

A message to an open profile reaches the inbox today. Everyone else needs a connection first, and pitching in the request note lowers acceptance.

## Before you start

Ask the user for anything below that they have not given you:

- The prospects' LinkedIn profile URLs.

## Steps

1. Check each profile's open status.  
   InGrow tool `linkedinGetOpenProfileStatus` (`POST /public-api/linkedin/get-open-profile-status`), $0.015 per call.

## What to return

- Two lists: message now (open profiles) and connect first (everyone else).
- A short message draft for the first list and a short, pitch-free connection note for the second.

## Cost

$0.015 per profile.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Tell the user the total before checking a long list.
