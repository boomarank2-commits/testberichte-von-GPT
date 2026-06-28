# Combined Report Attempts 041-060

# Summary Attempts 041-050

## Meta
```json
{
  "rows": 1579690,
  "first": "2023-06-24 15:39:00+00:00",
  "last": "2026-06-25 15:48:00+00:00",
  "split": "2025-06-25 15:48:00+00:00",
  "cost_roundtrip_pct": 0.22
}
```

## Attempt 041 Oracle Capacity
| horizon   |   trades_day |   avg_net_trade |   oracle_usdc_day |   positive_windows |   window_count |
|:----------|-------------:|----------------:|------------------:|-------------------:|---------------:|
| 15m       |      34.4344 |        0.2365   |           8.14375 |              12603 |          35040 |
| 30m       |      31.9699 |        0.259352 |           8.29147 |              18783 |          35040 |
| 60m       |      20.2678 |        0.351075 |           7.11551 |              23730 |          35040 |
| 120m      |      11.1967 |        0.515273 |           5.76937 |              27259 |          35040 |

## Best per Attempt 042-050
| attempt_no | family | kind | blind_usdc_day | blind_trades_day | blind_avg_pnl_trade | blind_required_trades_day | blind_target_ratio | blind_pf | blind_max_dd | blind_worst_day | blind_worst_month | blind_active_share | train_usdc_day | train_trades_day | train_avg_pnl_trade | train_pf | rejection_reason |
|---:|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 42 | btc_shock_resilience | break5 | 0.001585 | 0.002732 | 0.58 | 5.172414 | 0.000528 | 9.99 | -0.58 | 0.0 | 0.0 | 0.002732 | -0.013379 | 0.025992 | -0.514737 | 0.151042 | target_ratio_low;active_days_low |
| 43 | us_overlap_retest | delayed_retest | -0.227481 | 0.877049 | -0.25937 | 999999.0 | 0.0 | 0.431032 | 84.612893 | -3.28 | -13.273672 | 0.546448 | -0.20431 | 0.640219 | -0.319126 | 0.316344 | negative_net_trade;pf_low;drawdown_high;target_ratio_low |
| 44 | exit_engine | ethbtc_leadership::swing | 0.336353 | 1.628415 | 0.206552 | 14.524169 | 0.112118 | 1.928796 | 8.017159 | -2.61 | 3.498402 | 0.581967 | 0.240249 | 1.399453 | 0.171674 | 1.755318 | target_ratio_low |
| 45 | asia_compression_wakeup | break15 | -0.017694 | 0.125683 | -0.140783 | 999999.0 | 0.0 | 0.524902 | 7.016028 | -0.946817 | -3.015729 | 0.103825 | -0.054548 | 0.229822 | -0.237347 | 0.185487 | negative_net_trade;pf_low;target_ratio_low;active_days_low |
| 46 | ethbtc_leadership | reclaim5 | 0.364549 | 1.551913 | 0.234903 | 12.771217 | 0.121516 | 2.003297 | 7.659739 | -2.8 | 2.877628 | 0.579235 | 0.252532 | 1.340629 | 0.188368 | 1.756963 | target_ratio_low |
| 47 | basis_gate | ethbtc_leadership::calm35 | 0.369577 | 1.546448 | 0.238984 | 12.553133 | 0.123192 | 2.031404 | 5.819739 | -2.8 | 2.877628 | 0.579235 | 0.249781 | 1.333789 | 0.187272 | 1.750332 | target_ratio_low |
| 48 | multi_entry_context | ethbtc_leadership::gap20 | 0.445131 | 2.120219 | 0.209946 | 14.28941 | 0.148377 | 1.83664 | 7.751876 | -4.6 | 4.335518 | 0.581967 | 0.312505 | 1.871409 | 0.166989 | 1.619071 | target_ratio_low |
| 49 | aggflow_gate | ethbtc_leadership::ai0.02_aq0.8 | 0.310413 | 1.535519 | 0.202155 | 14.840114 | 0.103471 | 1.795498 | 7.713339 | -2.8 | 2.029648 | 0.579235 | 0.203128 | 1.295486 | 0.156797 | 1.594498 | target_ratio_low |
| 50 | regime_router | btc_shock_resilience+btc_shock_resilience+btc_shock_resilience+btc_shock_resilience | -0.19177 | 0.636612 | -0.301235 | 999999.0 | 0.0 | 0.512906 | 70.207912 | -2.24 | -12.475863 | 0.543716 | -0.203577 | 0.504788 | -0.403293 | 0.353654 | negative_net_trade;pf_low;drawdown_high;target_ratio_low |

## Best Overall 041-050
```json
{
  "attempt_no": 48,
  "family": "multi_entry_context",
  "kind": "ethbtc_leadership::gap20",
  "blind_usdc_day": 0.445131,
  "blind_trades_day": 2.120219,
  "blind_avg_pnl_trade": 0.209946,
  "blind_required_trades_day": 14.28941,
  "blind_target_ratio": 0.148377,
  "blind_pf": 1.83664,
  "blind_max_dd": 7.751876,
  "blind_worst_day": -4.6,
  "blind_worst_month": 4.335518,
  "blind_active_share": 0.581967,
  "train_usdc_day": 0.312505,
  "train_trades_day": 1.871409,
  "train_avg_pnl_trade": 0.166989,
  "train_pf": 1.619071,
  "rejection_reason": "target_ratio_low"
}
```

## Interpretation 041-050
Diese Runde ist eine Research-Ebene: ETH-Regime werden nur als Kontext genutzt, Entry/Exit wird 1m-basiert approximiert und jeder Kandidat wird an der Zielmechanik gemessen.

---

# Summary Attempts 051-060

## Best per Attempt
| attempt_no | family | kind | blind_usdc_day | blind_trades_day | blind_avg_pnl_trade | blind_required_trades_day | blind_target_ratio | blind_pf | blind_max_dd | blind_worst_day | blind_worst_month | blind_active_share | train_usdc_day | train_trades_day | train_avg_pnl_trade | train_pf | rejection_reason |
|---:|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 51 | ethbtc_target_runner | reclaim5 | 0.43811 | 3.062842 | 0.143041 | 20.973078 | 0.146037 | 1.628604 | 5.987109 | -3.849174 | 0.361569 | 0.691257 | 0.309973 | 2.388509 | 0.129777 | 1.562193 | target_ratio_low |
| 52 | ethbtc_multi_gap | reclaim5 | 0.254154 | 5.114754 | 0.04969 | 60.373768 | 0.084718 | 1.24507 | 10.724777 | -2.568412 | -2.284041 | 0.699454 | 0.155445 | 4.599179 | 0.033798 | 1.167256 | target_ratio_low |
| 53 | exit_surface_ethbtc | reclaim5 | 0.560647 | 4.29235 | 0.130615 | 22.968196 | 0.186882 | 2.190311 | 3.239916 | -1.960355 | 0.132363 | 0.691257 | 0.32181 | 3.71409 | 0.086646 | 1.681599 | passes_filters |
| 54 | ethbtc_flow_surface | reclaim5 | 0.118493 | 4.095628 | 0.028932 | 103.692812 | 0.039498 | 1.131589 | 12.469556 | -4.389803 | -5.299788 | 0.696721 | 0.022715 | 3.508892 | 0.006474 | 1.029018 | pf_low;target_ratio_low |
| 55 | ethbtc_time_specialist | reclaim5 | 0.207713 | 3.663934 | 0.056691 | 52.918164 | 0.069238 | 1.282632 | 7.622998 | -2.44 | -4.151668 | 0.696721 | 0.098194 | 3.124487 | 0.031427 | 1.153437 | target_ratio_low |
| 56 | ethbtc_persistence_exitproxy | reclaim5 | 0.110174 | 4.229508 | 0.026049 | 115.168201 | 0.036725 | 1.168415 | 6.195607 | -1.489545 | -1.851547 | 0.688525 | -0.03716 | 3.636115 | -0.01022 | 0.940194 | pf_low;target_ratio_low |
| 57 | loose_ethbtc_strong_1m | reclaim_strong | 0.050724 | 1.781421 | 0.028474 | 105.358749 | 0.016908 | 1.158713 | 9.77276 | -2.72 | -7.470098 | 0.546448 | 0.039611 | 1.357045 | 0.02919 | 1.167023 | pf_low;target_ratio_low |
| 58 | target_zone_frequency | pull_vol_flow | -0.361854 | 1.972678 | -0.183433 | 999999.0 | 0.0 | 0.281046 | 132.71974 | -3.08476 | -14.576321 | 0.650273 | -0.351741 | 1.797538 | -0.195679 | 0.242454 | negative_net_trade;pf_low;drawdown_high;target_ratio_low |
| 59 | positive_ethbtc_router | 4mask_union | -2.021465 | 13.311475 | -0.151859 | 999999.0 | 0.0 | 0.480529 | 739.898629 | -10.18969 | -77.74178 | 0.751366 | -1.847587 | 11.829001 | -0.156191 | 0.45374 | negative_net_trade;pf_low;drawdown_high;target_ratio_low |
| 60 | final_ethbtc_target_mix | pull | -0.219163 | 1.286885 | -0.170305 | 999999.0 | 0.0 | 0.414672 | 81.653724 | -3.240216 | -10.642846 | 0.560109 | -0.23988 | 1.221614 | -0.196363 | 0.328252 | negative_net_trade;pf_low;drawdown_high;target_ratio_low |

## Best Overall 051-060
```json
{
  "attempt_no": 53,
  "family": "exit_surface_ethbtc",
  "kind": "reclaim5",
  "blind_usdc_day": 0.560647,
  "blind_trades_day": 4.29235,
  "blind_avg_pnl_trade": 0.130615,
  "blind_required_trades_day": 22.968196,
  "blind_target_ratio": 0.186882,
  "blind_pf": 2.190311,
  "blind_max_dd": 3.239916,
  "blind_worst_day": -1.960355,
  "blind_worst_month": 0.132363,
  "blind_active_share": 0.691257,
  "train_usdc_day": 0.32181,
  "train_trades_day": 3.71409,
  "train_avg_pnl_trade": 0.086646,
  "train_pf": 1.681599,
  "rejection_reason": "passes_filters"
}
```

## Interpretation 051-060
Fokussierte Fortsetzung der 041-050-Erkenntnis: ETHBTC-Leadership + 1m-Trigger + Multi-Entry/Zielmechanik.
