---
name: tech-stack-targeting
description: Find which companies in a list run a competitor's tool or a tool that pairs with the user's product, using live website detection. Use when the user sells a replacement, an integration or a service for a specific technology.
---

# Target by tech stack

A company already paying for a tool in your category understands the problem. Companies running a tool you integrate with get value on day one.

## Before you start

Ask the user for anything below that they have not given you:

- The list of company domains (up to a few hundred).
- The technologies to look for: competitors, complements, or both.

## Steps

1. Analyze the websites in batches of up to 10 URLs per call.  
   InGrow tool `techStackAnalyzeWebsite` (`POST /public-api/tech-stack/analyze-website`), $0.008 per call.
2. For any site the batch analysis could not read, try the single-site detector.  
   InGrow tool `techStackDetectTechnologies` (`POST /public-api/tech-stack/detect-technologies`), $0.005 per call.

## What to return

- Three groups: runs a competitor, runs a complement, runs neither. For each company list the matching tools.
- A one-line opener for each group, for example the switch angle or the integration angle.

## Cost

$0.008 per batch of up to 10 sites, and $0.005 per single-site retry.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Website detection only sees what loads in the browser. Back-office tools like a CRM may not show. Say so when the user asks about one.
