# Codex Instruction - Attempt 073

## Do not claim 3 USDC/day yet

The current champion is still Attempt 053 at candidate-metric level: 0.560647 USDC/day. However, Attempt 053 did not persist entry/exit timestamps.

Attempt 073 created real trade-level capture files for a 053-near ETHBTC leadership + 1m reclaim reconstruction. The reconstructed mask is only 053-near, not exact. Its live-like replay is negative, so it must not be used as a takeover.

## Mandatory optimizer change

Add `capture_trades=True` to the optimizer replay for every champion/top candidate. Persist one row per closed trade with:

- entry_utc, entry_i, entry_price
- exit_utc, exit_i, exit_price, exit_reason
- net_pnl_usdc
- MFE/MAE horizons 6/12/18/25/35/45/60/80m
- capture_ratio
- ETHBTC/BTC/orderflow snapshot

## Next path toward 3 USDC/day

Do not loosen 053 entries blindly. Attempts 061-070 showed quality collapses.

The next real step is to rerun the actual 053 optimizer family with `capture_trades=True`, then improve exits only from real MFE/MAE clusters.
