---
name: website-traffic-qualification
description: Pull monthly website visits, traffic sources and top countries for a list of domains and keep the ones above a size or growth threshold. Use when the user wants to filter accounts by online demand, for example ecommerce or SaaS brands.
---

# Qualify accounts by website traffic

Headcount lags; traffic shows demand now. A brand whose visits are growing and whose paid share is rising is spending on growth.

## Before you start

Ask the user for anything below that they have not given you:

- The list of domains.
- A minimum monthly visits threshold, and whether growth or a specific country matters.

## Steps

1. Get visits, engagement, traffic sources and top countries for each domain.  
   InGrow tool `webTrafficGetWebsiteTraffic` (`POST /public-api/web-traffic/get-website-traffic`), $0.001 per call.

## What to return

- A table: domain, monthly visits, change over the period, top country and its share, paid search and social share.
- Mark each domain as keep or drop against the threshold and say why.

## Cost

$0.001 per domain.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Small sites often return no data. List them separately instead of dropping them silently.
