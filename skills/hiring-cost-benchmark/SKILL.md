---
name: hiring-cost-benchmark
description: Estimate what a company is paying to hire the roles it has open, using salary data for those titles and locations. Use when the user sells something that replaces, speeds up or supports a hire.
---

# Hiring cost benchmark

Putting a real number on the cost of the roles a company is hiring makes the case for a tool or service in the buyer's own terms.

## Before you start

Ask the user for anything below that they have not given you:

- The company and its open role titles and locations.

## Steps

1. Get the salary range for each title at the company.  
   InGrow tool `jobsGetCompanySalary` (`POST /public-api/jobs/get-company-salary`), $0.002 per call.
2. Get the market range for each title in its location, to compare.  
   InGrow tool `jobsGetEstimatedSalary` (`POST /public-api/jobs/get-estimated-salary`), $0.002 per call.

## What to return

- A table: role, location, company range, market range, number of open roles, total annual cost.

## Cost

$0.002 per call.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Present salary data as estimates with the range, not as exact pay.
