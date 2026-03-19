# Custody Cover (Part A of Crypto Cover)

## Two Covered Events

**1. Crime-Related Loss**:
- Designated Custodian is victim of a crime (hack, theft, fraud) AND
- Custodian announces all users must incur a loss of >=10% of holdings.
- Earliest filing: 14 days after announcement.

**2. Extended Withdrawal Restriction**:
- Custodian imposes a COMPLETE withdrawal halt WITHOUT prior notice AND
- Restriction remains continuously for >=100 days.
- Earliest filing: 100 days after restriction starts.
- Partial restrictions or user-specific halts are NOT covered.

**Key requirements**:
- **$1,000,000 minimum** purchase per Designated Custodian.
- **API keys required**: read-only API keys for all CEX accounts must be provided within 5 days of purchase. Failure may result in claim denial.
- Grace period: 120 days (much longer than protocol cover's 35 days).
- The covered member cannot be the custodian itself or a related entity.

---

# Slashing Cover (Part D of Crypto Cover)

## Covered Events

- Aggregate Penalties and Slashing across all Covered Validators exceed the Deductible within any continuous **40-day period**.
- Applies to both direct validators AND liquid staking/restaking protocol stakers.

## Claim Calculation

- Claim = 100% of Penalties/Slashing - remaining Deductible.
- If Covered Validators Exposure exceeds the Covered Validator Limit (in annex), claim is reduced proportionally.
- Subject to per-network Sublimits in the annex.

## Exclusions

- Penalties for offenses committed BEFORE Cover Period started.
- Missed rewards of any kind (offline penalties, MEV).
- Earliest filing: 7 days. Deadline: 35 days after cover ends.

Always check the annex for: Deductible amount, Covered Validator Limit, and network-specific Sublimits.
