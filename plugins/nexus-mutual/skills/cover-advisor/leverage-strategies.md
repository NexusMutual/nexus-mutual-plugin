# Leverage Strategies Guidance

## Looping Strategies (Elite Cover)

- **Elite Cover protects initial capital only** — not the total leveraged exposure.
- In a looping strategy (deposit -> collateralize -> borrow -> reinvest), borrowed funds and collateral effectively cancel out. Net exposure = initial capital.
- Purchase cover based on **initial capital invested**, not the gross leveraged position.
- Example: $10k initial capital, 2x loop to $20k total position -> purchase $10k Elite Cover (not $20k).
- Recommend contacting Nexus Mutual (nexusmutual.io/contact) for complex leveraged scenarios before purchasing.

## Leveraged Liquidation Cover (specific product type)

This is a dedicated cover type for liquidation risk on leveraged positions:

**Two covered events**:
1. **Depeg Liquidation** — Covered Token depegs beyond the threshold causing liquidation.
2. **Oracle Failure/Manipulation Liquidation** — external price feed corruption triggers liquidation.

**Key rules**:
- **Like-Kind Assets only**: covered positions must borrow the same asset class as collateral. ETH collateral -> borrow ETH-based only. Borrowing non-Like-Kind Assets = excluded.
- **Acceptable Leverage Limit**: defined in the annex. Exceeding it voids the claim.
- **Proportional reduction**: uses Principal Funds (pre-leverage collateral), not Exposed Funds: `Claim = (Loss - Deductible) x (Cover Amount / Principal Funds)`.
- **Fixed-rate oracle edge case**: if a depeg occurs but no liquidation happens because the oracle uses a fixed rate, a liquidation is "deemed" to have occurred IF: (a) a market-based oracle would have triggered it, AND (b) the Covered Token team publicly announces material losses with no viable recovery path.

Earliest filing: 7 days after event. Always check the annex for specific Covered Tokens, Designated Protocols, and leverage limits.
