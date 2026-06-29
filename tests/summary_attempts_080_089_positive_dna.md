# Clean Attempts 080-089: Positive-DNA Strategy Search

This round tested strategies developed from all positive links: ETHBTC leadership, BTC not dragging, reclaim/pullback confirmation, volume/orderflow confirmation, train-only cell selection, and MFE-aware exits.

## Result

Best new candidate: Attempt 87 `cell_broad_timekill`

- Train USDC/day: `0.000000`
- Blind USDC/day: `0.000000`
- Blind PF: `0.000000`
- Blind trades/day: `0.000000`
- Blind avg/trade: `0.000000`
- Blind maxDD: `0.000000`
- Rejection: `train_nonpositive;blind_nonpositive;pf_low;target_ratio_low`

## Best per attempt

| Attempt | Name | Method | Train USDC/day | Blind USDC/day | PF Blind | Trades/day Blind | Avg/trade Blind | Decision |
|---:|---|---|---:|---:|---:|---:|---:|---|
| 87 | cell_broad_timekill | train_cells | 0.000000 | 0.000000 | 0.000000 | 0.000000 | 0.000000 | rejected |
| 88 | cell_score_combo | cell_plus_score | -0.000973 | -0.001306 | 0.881354 | 0.024658 | -0.052950 | rejected |
| 80 | lead_flow_tight | manual_score | -0.007753 | -0.003326 | 0.906666 | 0.101370 | -0.032811 | rejected |
| 89 | consensus_high_precision | cell_plus_score | -0.001629 | -0.004547 | 0.522610 | 0.024658 | -0.184404 | rejected |
| 82 | shock_resilience | manual_score | -0.012256 | -0.006604 | 0.561754 | 0.043836 | -0.150661 | rejected |
| 81 | swing_runner | manual_score | -0.007399 | -0.009159 | 0.518047 | 0.041096 | -0.222872 | rejected |
| 83 | active_reclaim | manual_score | -0.010729 | -0.011090 | 0.516984 | 0.046575 | -0.238107 | rejected |
| 84 | cell_high_goodrate | train_cells | -0.003273 | -0.017318 | 0.196713 | 0.057534 | -0.301003 | rejected |
| 86 | cell_rare_strong_runner | train_cells | -0.000610 | -0.047888 | 0.234009 | 0.123288 | -0.388426 | rejected |
| 85 | cell_balanced_mae | train_cells | -0.008422 | -0.051687 | 0.269782 | 0.161644 | -0.319759 | rejected |

## Decision

No candidate beats Attempt 053. 3 USDC/day not reached. Do not implement as live candidate.

## Reproducibility

- 5m bars from 1m ETHUSDC/BTCUSDC/ETHBTC candles.
- ETHUSDC aggTrade orderflow included.
- All thresholds are selected from train only.
- Last 365 days are blind.
- Each attempt has trade-level CSV with Entry/Exit/PnL/MFE/MAE.

## Interpretation

The positive-DNA idea is directionally logical, but the tested 5m/cell versions are too weak. The best non-zero candidates remain slightly negative. This confirms that the next real improvement must come from either exact Attempt 053 reconstruction with trade capture, or a lower-level 1m/aggTrade/orderbook trigger rather than coarse 5m cells.
