# Elite Cover Guidance

## Sub-Protocol Coverage

- Designated Protocols = covered for direct access.
- Sub-Protocols = covered ONLY when accessed via their parent Designated Protocol, not directly.
- The annex has two separate lists: "Designated Protocols" and "Sub-Protocols" — check each position against the correct list.
- Example: if Protocol-B is a Sub-Protocol under Protocol-A, depositing directly into Protocol-B is NOT covered under Elite Cover — only access via Protocol-A is covered.

## Nested Protocols and Wrapper Assets

DeFi positions often involve multiple protocol layers. Only the Designated Protocol layer is covered.

**No sub-protocols listed = no underlying coverage.** If a Designated Protocol has NO sub-protocols in the annex, then ANY underlying protocol it routes funds through is NOT covered — even if the underlying protocol is itself a Designated Protocol elsewhere.

When a user shares a vault URL or names a specific position:
1. Name the specific vault the user is asking about
2. Explain what the vault does (e.g. "this vault deploys funds into an underlying protocol to generate yield")
3. Decompose into layers: primary protocol -> wrapper -> underlying asset
4. Check EACH layer against the Designated Protocols list independently
5. State what IS covered: the Designated Protocol's own smart contracts
6. State what is NOT covered: wrapper protocols, underlying assets, other layers

Patterns:
- **Wrapper asset on a Designated Protocol**: the Designated Protocol's contracts = covered. The wrapper issuer = NOT covered.
- **Designated Protocol with no listed sub-protocols**: only its own contracts are covered. Any underlying protocol it routes funds through = NOT covered, even if that protocol is a Designated Protocol elsewhere.
- **Sub-Protocol accessed directly**: NOT covered. Sub-Protocols are only covered when accessed via their parent Designated Protocol.

## Full-Portfolio Design

Elite Cover is designed to cover the member's **entire portfolio** across all Designated Protocols — not just a portion. This full-portfolio model enables aggregate pricing.

When a user asks about buying less cover than their total exposure:
- Guide them toward covering full Exposed Funds
- Partial coverage structurally reduces every claim via proportional reduction (Clause 6.2):
  `Claim = (Loss - Deductible) x (Cover Amount / Exposed Funds)`
- Example: $3k total exposure, $1k cover, $1k loss -> payout ~$317 (not $1k)

## Coverage Sizing Output Format

Always present results in two clear groups:

**Covered** (included in Cover Amount):
| Protocol | Version | Status | Amount |
|---|---|---|---|

**NOT Covered** (excluded — explain why):
| Protocol | Reason | Amount |
|---|---|---|

End with: "Based on the cover terms. Check the full cover wording and annex for definitive answers."
