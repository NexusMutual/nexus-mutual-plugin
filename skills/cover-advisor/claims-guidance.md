# Claims Guidance

## Filing Windows

After a Covered Event there is a waiting period before you can file, and a deadline after which you can no longer file.

**WARNING**: Do NOT rely on on-chain `gracePeriodDays` from `get_product_details` for filing deadlines. The on-chain value may reflect the max grace period across all product types bundled under the same cover wording, not the actual deadline for the specific product.

**Always read the cover wording** (`get_cover_wording`) to find the actual filing deadline for the specific product type.

`get_product_details` **claimTiming** is still useful for:
- **coolDownPeriodDays** — waiting period after the event before you can file
- **payoutRedemptionPeriodDays** — days to redeem after approval

Missing the filing deadline = right to claim is permanently lost.

## Loss Measurement

- For economic events (oracle failure, liquidation failure, governance takeover): loss measured over any 2-hour window.
- For code bug exploits: actual amount lost at the time it occurred.

## Claim Formulas

- **Elite Cover**: `Claim = (Loss - Deductible) x (Cover Amount / Exposed Funds)` — proportional reduction when cover < total exposure.
- **Protocol Cover**: `Claim = min(Loss - Deductible, Cover Amount)` — no proportional reduction, paid up to cover amount.
- **Leveraged Liquidation**: `Claim = (Loss - Deductible) x (Cover Amount / Principal Funds)` — uses pre-leverage collateral.

## After Approval

- Payout available to redeem within **30 days** of approval — failure to redeem forfeits the claim.
- Member must assign recovery rights to the Foundation within 20 days.
- Forward any third-party recoveries within 5 days. Double recovery prohibited.

## Common Exclusions

**Your own security**: Phishing, private key breaches, malware — if the protocol acted as intended, no claim.

**Market risks**: Price movements (EXCEPT oracle failure/manipulation). De-peg of assets the protocol generates.

**Governance risks**: Rug pulls, admin key actions using existing permissions.

**Pre-existing issues**: Events before Cover Period. Public bug disclosures before cover started.

**Structural**: Non-EVM chain losses (unless annex includes them). Bridge failures.

Always fetch the full cover wording (`get_cover_wording`) for the definitive exclusion list.
