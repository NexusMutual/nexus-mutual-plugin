# Wallet Position Analysis and Cover Sizing

## Process

1. Use `get_wallet_positions` to fetch DeFi positions and balances.
2. Cross-reference DeBank protocol names with the exact Designated Protocols from the annex or product name.
3. DeBank names may differ from annex / product names — match carefully and verify versions.

## Protocol Version Matching

- DeBank may report positions under a generic name without a version suffix — verify which version the position belongs to before including it.
- When a user has positions in multiple versions of the same protocol, check each version individually against the annex.
- If a version is NOT in the Designated Protocols list, explicitly exclude it.

## Position Type Filtering

For each wallet position, match it against the Designated Protocols and Sub-Protocols lists in the cover annex:
- Check if the protocol is listed as a Designated Protocol or Sub-Protocol
- Check if the position type (deposit, lending, liquidity provision, staking, holdings, etc.) represents coverage under that protocol

**If a position type doesn't clearly map to coverage in the annex, flag it:**

- When unsure, link the user to the cover annex's Designated Protocols and Sub-Protocols sections
- Always defer to the annex as authoritative — don't assume position types are covered
## Sizing Rules

- **Elite Cover**: sum ONLY Designated Protocol positions where the position type is confirmed covered. Cover Amount should match this total.
- **Protocol Cover**: show per-protocol exposure for individual cover sizing.
- If DEBANK_API_KEY is not configured, ask the user for exposure amounts manually.
- Use `protocolFilter` parameter when you know which protocols matter.
- Present dollar values clearly and relate them to Cover Amount / Exposed Funds.

## Output Format

Always present results in two clear groups:

**Covered** (included in Cover Amount):
| Protocol | Version | Status | Amount |
|---|---|---|---|

**NOT Covered** (excluded — explain why):
| Protocol | Reason | Amount |
|---|---|---|

End with recommended Cover Amount and link to the annex for verification.
