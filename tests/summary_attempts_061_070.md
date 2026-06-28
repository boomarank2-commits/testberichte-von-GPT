# Summary Attempts 061-070

## Zweck

Diese Runde hat den Attempt-053-Radius nach oben, unten und in die Breite variiert: weichere/härtere ETHBTC-Schwellen, mehr Aktivität, höhere Qualität, Partial/Trail-Exit, Session-Spezialisierung, Volatilitätsband, Flow-Gate und Break/Retest. Attempt 070 ist der Kontrollpunkt: der bisherige Champion 053 bleibt als Referenz stehen.

## Best per Attempt

|   attempt_no | family           | kind                                |   blind_usdc_day |   blind_trades_day |   blind_avg_pnl_trade |   blind_required_trades_day |   blind_target_ratio |   blind_pf |   blind_max_dd |   blind_worst_day |   blind_worst_month |   blind_active_share |   train_usdc_day |   train_trades_day |   train_avg_pnl_trade |   train_pf | rejection_reason                                                           |
|-------------:|:-----------------|:------------------------------------|-----------------:|-------------------:|----------------------:|----------------------------:|---------------------:|-----------:|---------------:|------------------:|--------------------:|---------------------:|-----------------:|-------------------:|----------------------:|-----------:|:---------------------------------------------------------------------------|
|           61 | core             | reclaim5_core                       |        -2.60877  |           11.8251  |             -0.220612 |                 999999      |             0        |   0.197031 |      954.808   |          -6.60745 |         -104.828    |             1        |        -2.22483  |           10.2333  |             -0.217411 |   0.186235 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           62 | core             | activity_soft_flow                  |        -3.38154  |           15.0738  |             -0.224333 |                 999999      |             0        |   0.16636  |     1237.7     |          -9.2772  |         -116.645    |             1        |        -2.86276  |           13.0027  |             -0.220166 |   0.154684 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           63 | quality          | quality_leadership                  |        -0.660273 |            3.03279 |             -0.217712 |                 999999      |             0        |   0.311354 |      243.048   |          -4.31086 |          -34.88     |             0.909836 |        -0.501357 |            2.41337 |             -0.207741 |   0.324046 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           64 | partial          | partial_trail_surface               |        -3.36803  |           17.7404  |             -0.189851 |                 999999      |             0        |   0.405936 |     1232.7     |         -10.5132  |         -136.679    |             1        |        -3.1023   |           16.2592  |             -0.190803 |   0.381632 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           65 | core             | multi_gap_frequency                 |        -5.77494  |           26.4344  |             -0.218463 |                 999999      |             0        |   0.100338 |     2113.63    |         -10.7458  |         -230.055    |             1        |        -5.29547  |           24.2101  |             -0.21873  |   0.086332 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           66 | time             | session_specialist                  |        -1.05228  |            4.80328 |             -0.219077 |                 999999      |             0        |   0.263875 |      385.136   |          -4.70502 |          -42.3106   |             0.994536 |        -0.909972 |            3.99318 |             -0.227882 |   0.198454 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           67 | volband          | anti_chop_band                      |        -2.55297  |           11.5027  |             -0.221945 |                 999999      |             0        |   0.168244 |      934.387   |          -6.41212 |          -95.6942   |             1        |        -1.88753  |            8.92497 |             -0.211489 |   0.174333 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           68 | flow             | flow_confirm_reclaim                |        -2.74928  |           11.7596  |             -0.233791 |                 999999      |             0        |   0.198687 |     1006.3     |          -7.03436 |          -95.4804   |             1        |        -2.31103  |           10.3738  |             -0.222775 |   0.188894 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           69 | break            | break_retest_leadership             |        -1.76924  |            7.79508 |             -0.226969 |                 999999      |             0        |   0.245092 |      647.842   |          -6.58886 |          -75.3292   |             0.991803 |        -1.44666  |            6.63984 |             -0.217876 |   0.254851 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           70 | champion_control | attempt053_reclaim5_exact_reference |         0.560647 |            4.29235 |              0.130615 |                     22.9682 |             0.186882 |   2.19031  |        3.23992 |          -1.96036 |            0.132363 |             0.691257 |         0.32181  |            3.71409 |              0.086646 |   1.6816   | champion_kept_best;passes_filters                                          |

## Best Overall 061-070

```json
{
  "attempt_no": 70,
  "family": "champion_control",
  "kind": "attempt053_reclaim5_exact_reference",
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
  "rejection_reason": "champion_kept_best;passes_filters",
  "params": "{\"source\":\"Attempt 053 exact reference\"}"
}
```

## Kernerkenntnis

Die breite Suche um Attempt 053 herum hat den Champion nicht geschlagen. Besonders die aggressiveren Aktivitäts-Varianten kippen schnell ins Negative, weil sie zu viele schwache Reclaim-Situationen aufnehmen. Der beste Satz bleibt Attempt 053. Das ist keine Niederlage, sondern eine wichtige Eingrenzung: Die nächste Optimierung darf nicht einfach lockern, sondern muss die bestehende 053-Regel live-realistischer nachbauen und dann MFE-Capture/Exit verbessern.

## Nicht weiterverfolgen

- weiche ETHBTC-Schwellen nur für mehr Trades
- Flow-Gate ohne starke ETHBTC-Führung
- Session-Spezialisierung als alleinige Verbesserung
- Break/Retest statt Reclaim als Ersatz für 053
- aggressive Multi-Frequency ohne Qualitätssperre

## Nächster sinnvoller Schritt

Attempt 071 sollte nicht breiter suchen, sondern Attempt 053 exakt rekonstruieren: Entry-Snapshots, MFE/MAE pro Trade, Exit-Capture und danach nur Exit/Partial/Trail auf dieser festen Entry-Menge optimieren.
