---
name: review-battlecard
description: Build a battlecard against a competitor from its G2 page and its lowest-rated G2 and Trustpilot reviews. Use when the user asks how to win against a named competitor.
---

# Review battlecard

Unhappy customers describe a competitor's weak spots in their own words. Those words make the strongest objection handling.

## Before you start

Ask the user for anything below that they have not given you:

- The competitor's G2 product slug and domain.
- The user's product strengths.

## Steps

1. Read the competitor's rating, pros and cons, pricing and alternatives.  
   InGrow tool `reviewsGetG2Product` (`POST /public-api/reviews/get-g2-product`), $0.004 per call.
2. Pull the 1 to 3 star reviews, filtered to the user's segment.  
   InGrow tool `reviewsGetG2ProductReviews` (`POST /public-api/reviews/get-g2-product-reviews`), $0.004 per call.
3. Pull low-rated Trustpilot reviews for the competitor's domain, if any.  
   InGrow tool `reviewsGetTrustpilotReviews` (`POST /public-api/reviews/get-trustpilot-reviews`), $0.003 per call.

## What to return

- A battlecard: where they win, where they lose with quotes, the questions that expose the weak spots, and how the user's product answers each.

## Cost

$0.004 per G2 call and $0.003 per Trustpilot call. About $0.02 per competitor.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Use quotes as written and say where they came from. Do not make claims about the competitor that the reviews do not support.
