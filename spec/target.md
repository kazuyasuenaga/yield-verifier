# Target: Arcadia Farm (Base) strategyId=405

## Target name
Arcadia Farm (Base 8453) - v2 strategyId=405

## Target URL
https://arcadia.finance/farm/8453/v2?strategyId=405

## Target identifiers
- chain_id: 8453 (Base)
- strategy_id: 405

## Primary data sources (preferred order)
1) Arcadia Strategies API: GET /v1/api/strategies/{strategy_id}
2) On-chain reads for the underlying pool/position (if API lacks fields)
3) UI scraping (last resort)

## What we fetch (inputs) - minimum set
- timestamp_utc
- strategy_id
- displayed_yield (apr/apy) + unit (if available from API)
- fee assumptions (management/performance/compound costs) if available
- underlying pool identifiers (pair symbols + pool address) if available
- tvl / liquidity (if available)
- reward emissions info (if applicable, from API)
- any leverage/multiplier field (if strategy is leveraged)

## What we compute (outputs)
- effective_apr_estimate (net of known fees; if fees unknown, mark as "unknown_fee_assumptions")
- effective_apy_estimate (from apr + compounding assumption)
- deviation_vs_displayed (if displayed_yield is available)
- reproducibility_hashes (input_digest/output_digest)

## Checks (v0.1 — start small, expand later)
1) input_present: required fields exist for this run
2) unit_unambiguous: percent/day vs percent/year etc is clear
3) deterministic_output: normalized input -> stable output hash
