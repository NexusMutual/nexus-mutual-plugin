# Depeg Cover Guidance (Part C of Crypto Cover)

## Key Rules

- Annex lists specific "Approved Covered Token Derivatives" (e.g. tokenized yield derivatives, wrapped staking tokens).
- **Derivatives prove exposure, not claim trigger**: Approved derivatives count as proof you hold exposure to the Covered Token. But the claim trigger is still the Covered Token itself depegging. If the derivative loses value (e.g. the derivative protocol is hacked) but the Covered Token stays pegged, there's no valid claim.
- **3-day holding requirement**: the member must hold the Covered Token (or approved derivative) for at least 3 days before the depeg begins. This rules out reactive purchases — the cover protects existing holdings, not tokens bought in anticipation of or during a depeg.
- Example: a user wants to buy a stablecoin during a depeg to arbitrage, then claim. Answer: "That would not work — the 3-day holding requirement excludes reactive purchases."

## Claims Process

- To claim: transfer tokens to Nexus Mutual. Approved -> swapped for Unit of Claim value. Denied -> tokens returned.
- Depeg threshold and observation time (Depeg Time) defined in the annex, NOT the cover wording.
- Earliest filing: after Depeg Time ends.
- Filing deadline: 30 days after Depeg Time ends (per Clause 8 of the cover wording).
- **WARNING**: The on-chain `gracePeriodDays` (e.g. 120 days) is NOT the depeg filing window. It reflects the max grace period across ALL Crypto Cover product types (driven by Custody Cover). For depeg, always use the 30-day window from the cover wording.
- Claim amounts subject to Sublimit per Covered Token (in annex) AND overall Cover Amount.

## Exclusions

- Smart contract bugs don't count UNLESS they specifically cause the depeg.
- Depeg of any asset OTHER than the Covered Token is not covered.

Always fetch annex (`get_product_annex`) for token eligibility questions.
