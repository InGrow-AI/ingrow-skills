---
name: find-work-emails
description: Find verified work emails for a list of LinkedIn profiles, with a cost check before running. Use when the user has people and asks for their emails.
---

# Find work emails

Email lookups cost more than data calls. Confirming the list and the total first avoids paying for people who should not be on it.

## Before you start

Ask the user for anything below that they have not given you:

- The LinkedIn profile URLs.
- Confirmation of the total cost before you start.

## Steps

1. Look up the work email for each profile URL, one call per person.  
   InGrow tool `contactsGetEmail` (`POST /public-api/contacts/get-email`), $0.01 per call.

## What to return

- A table: name, company, LinkedIn URL, email, or 'not found'.
- The number found and the total spent.

## Cost

$0.01 per person. Emails already on file come back without a new lookup.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Tell the user the total (people × $0.01) and wait for a yes before calling.
- Never guess an email pattern and present it as found.
