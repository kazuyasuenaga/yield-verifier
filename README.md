# Yield Verifier (Experimental)

This project automatically verifies yield-related numbers (APR/APY) and publishes reproducible receipts.

## Goals
1. **Recompute yield** from explicit assumptions (fees, compounding frequency, time window, etc.)
2. **Detect inconsistencies** between displayed values and recomputed values
3. **Guarantee reproducibility**: identical inputs must produce identical outputs
4. **Publish evidence**: every run outputs a structured receipt and logs

## How it works (high level)
- Fetch inputs from a defined target (page/API/on-chain data)
- Run deterministic calculations + validation checks
- Emit a receipt (`artifacts/receipt.json`) containing:
  - input/output digests (hashes)
  - spec version (rule set version)
  - check results (pass/fail + reasons)
  - computed APR/APY under stated assumptions
- Store receipts in git history for transparency

## Status
**Experimental / unstable.** Early versions may contain bugs or produce false positives/negatives.
Changes are tracked via commit history and receipts.

## What to trust
- Prefer runs marked `pass: true` with complete input evidence
- Always review the receipt assumptions and hashes
- Treat failures as “needs review”, not as definitive conclusions

## Disclaimer
This repository is for research and transparency. It is not financial advice.
