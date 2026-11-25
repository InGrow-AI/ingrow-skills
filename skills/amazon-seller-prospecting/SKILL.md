---
name: amazon-seller-prospecting
description: Find brands and sellers that are growing on Amazon in a category, with their ratings and product counts, to prospect for ecommerce services or software. Use when the user sells to Amazon brands or ecommerce teams.
---

# Amazon seller prospecting

Best sellers and movers lists show who is winning a category this month. A seller with strong sales but weak ratings or few products has a clear problem to solve.

## Before you start

Ask the user for anything below that they have not given you:

- The Amazon category or product keywords, and the marketplace country (default US).
- What the user sells, so you can pick the right gap to point out.

## Steps

1. Get best sellers or movers and shakers for the category.  
   InGrow tool `amazonGetBestSellers` (`POST /public-api/amazon/get-best-sellers`), $0.002 per call.
2. Open the top products to read the brand, rating, review count and seller.  
   InGrow tool `amazonGetProduct` (`POST /public-api/amazon/get-product`), $0.002 per call.
3. Read each seller's profile: name, rating, feedback count and business details.  
   InGrow tool `amazonGetSeller` (`POST /public-api/amazon/get-seller`), $0.002 per call.
4. Count each seller's products to size the brand.  
   InGrow tool `amazonGetSellerProducts` (`POST /public-api/amazon/get-seller-products`), $0.002 per call.

## What to return

- A table: brand, seller, best seller rank, rating, reviews, product count, business name and location from the seller profile.
- One observed gap per seller, such as a low rating, few products or missing variations.

## Cost

$0.002 per call. About $0.008 per seller researched.

Every InGrow response carries `x-cost-usd` and `x-balance-usd` headers. Report the total spent at the end.

## Guardrails

- Amazon itself sells many best sellers. Skip products where the seller is Amazon.
