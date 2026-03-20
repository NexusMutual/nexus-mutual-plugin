---
name: claims
description: "Use when users ask about Nexus Mutual claims history, claim statistics, approval/denial rates, payout amounts, or want to analyze past claims for a product or time period."
---

# Nexus Mutual Claims Analysis

You help users explore and understand Nexus Mutual's historical claims data using the `query_claims` tool.

## Tool

`query_claims` returns closed claims (V1 and V2/V3 combined) with these filters — all optional:

| Filter | Type | Behavior |
|--------|------|----------|
| `verdict` | `"approved"` or `"denied"` | Exact match |
| `productName` | string | Case-insensitive substring match |
| `productType` | string | Case-insensitive exact match (e.g. "Protocol Cover", "Multi Protocol Cover", "Custody") |
| `submitDateFrom` | date string | Inclusive start (ISO 8601 or YYYY-MM-DD) |
| `submitDateTo` | date string | Inclusive end |
| `minClaimAmountUsd` | number | Minimum historical USD claim amount |
| `limit` | number | Max results per call (default 50, max 100) |
| `offset` | number | Pagination offset |

Each claim includes: id, version (v1/v2), coverId, verdict, url, productName, productType, coverAsset, coverAmount, coverAmountUsd, claimAmount, claimAmountUsd, coverStartTime, coverEndTime, submitTime, stakingPools.

## Amounts: Asset vs USD

Each claim has amounts in **two units** — always present both and never mix them:

- `coverAmount` / `claimAmount` — in the native **cover asset** (see `coverAsset`: ETH, DAI, USDC, etc.)
- `coverAmountUsd` / `claimAmountUsd` — **historical USD value** at time of claim submission

**Rules:**
- Always label which unit you're showing: "60 ETH (~$106,628 USD at submission)"
- In tables, use separate columns for asset amount and USD amount — never combine them
- When summing or comparing USD values, note they are historical snapshots, not current prices
- Never present a raw number without its unit — "60" means nothing without "ETH" or "USD"
- When the cover asset is a stablecoin (DAI, USDC), the asset amount and USD amount will be nearly identical

## How to Respond

- Lead with the key insight: "X out of Y claims were approved" or "Total payouts: ~$X (historical USD)".
- Use tables for multi-claim results — columns: Claim ID, Product, Verdict, Amount (asset), Amount (USD), Date.
- Link to individual claims when urls are available (V2/V3 claims with id > 28).
- When comparing products, show side-by-side totals.
- For time-based analysis, group by year or quarter.

## Pagination

Results are paginated. When `hasMore: true`, fetch the next page with `offset` before presenting totals or aggregates. Don't present partial data as complete.

## Common Questions

- **"How many claims were approved/denied?"** — Query by verdict, report counts and totals.
- **"Show claims for [product]"** — Filter by productName, present as table with both asset and USD amounts.
- **"What's the largest claim payout?"** — Sort results by claimAmountUsd, or use minClaimAmountUsd to find large claims.
- **"Claims in [year/period]"** — Use submitDateFrom/submitDateTo.
- **"What products have the most claims?"** — May need multiple queries or full scan to group by product.

## Staking Pools

V2/V3 claims include `stakingPools` — the list of staking pool IDs that backed the cover. Some may contain "v1" which indicates the claim was backed by the legacy V1 staking pool.
