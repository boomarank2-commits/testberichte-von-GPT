# Summary Attempts 084-093 Fast 5m

Diese Runde ist eine schnelle 5m-Research-Schicht mit reproduzierbarer Trade-Level-Ausgabe fuer die fertig gelaufenen Bestversuche. Sie dient als Fortsetzungssuche, nicht als finaler Live-Takeover.

Referenz 053 bleibt 0.560647 USDC/Tag auf Candidate-Level.

## Best per Attempt

|   attempt_no | name                    |    tp |    sl |   hold_5m |   gap_5m |   blind_usdc_day |   blind_trades_day |   blind_avg_pnl_trade |   blind_pf |   blind_max_dd |   blind_worst_month |   train_usdc_day |   train_pf | rejection_reason                                                           |
|-------------:|:------------------------|------:|------:|----------:|---------:|-----------------:|-------------------:|----------------------:|-----------:|---------------:|--------------------:|-----------------:|-----------:|:---------------------------------------------------------------------------|
|           85 | vstrong_avoid_dead      | 0.016 | 0.01  |         7 |        4 |        -0.50154  |            2.51093 |             -0.199743 |   0.475985 |        183.95  |            -26.892  |        -0.385997 |   0.529548 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           88 | us_overlap_qvr08        | 0.012 | 0.008 |         4 |        3 |        -0.611466 |            2.78962 |             -0.219193 |   0.340588 |        223.796 |            -27.0856 |        -0.472241 |   0.32409  | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           86 | flow_strong_avoid_dead  | 0.014 | 0.008 |         5 |        3 |        -0.973216 |            4.10929 |             -0.236833 |   0.336647 |        356.394 |            -59.147  |        -0.593943 |   0.422507 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           91 | swing_avoid_dead        | 0.016 | 0.01  |        12 |        4 |        -1.02729  |            4.77596 |             -0.215096 |   0.435747 |        375.988 |            -48.2351 |        -0.811196 |   0.446481 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           89 | pull_reclaim_avoid_dead | 0.012 | 0.008 |         4 |        3 |        -1.16204  |            5.4235  |             -0.21426  |   0.220702 |        425.69  |            -67.7639 |        -1.08828  |   0.244942 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           90 | btc_strict_avoid_dead   | 0.014 | 0.008 |         5 |        3 |        -1.23456  |            5.51366 |             -0.223909 |   0.323429 |        452.804 |            -63.6385 |        -0.900673 |   0.352133 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           84 | 053_5m_core_avoid_dead  | 0.012 | 0.008 |         4 |        3 |        -1.43797  |            6.56011 |             -0.219199 |   0.295598 |        527.341 |            -68.03   |        -1.05467  |   0.315374 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           87 | anti_chop_avoid_dead    | 0.012 | 0.008 |         4 |        3 |        -1.61606  |            7.5     |             -0.215475 |   0.284866 |        592.57  |            -76.3417 |        -1.35067  |   0.308528 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           92 | freq_soft_avoid_dead    | 0.01  | 0.006 |         3 |        2 |        -2.68883  |           12.3634  |             -0.217483 |   0.216454 |        984.11  |           -107.665  |        -2.17976  |   0.230181 | train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low |
|           93 | combo_not_completed     | 0     | 0     |         0 |        0 |         0        |            0       |              0        |   0        |          0     |              0      |         0        |   0        | not_completed_timeout_before_tradelevel                                    |

## Bester fertig gelaufener Kandidat 084-093

```json
{
  "attempt_no": 85,
  "name": "vstrong_avoid_dead",
  "tp": 0.016,
  "sl": 0.01,
  "hold_5m": 7,
  "gap_5m": 4,
  "raw_train_signals": 3472,
  "raw_blind_signals": 1877,
  "score": -11.791915,
  "rejection_reason": "train_nonpositive;negative_net_trade;pf_low;drawdown_high;target_ratio_low",
  "train_pnl": -282.935757,
  "train_usdc_day": -0.385997,
  "train_trades": 1607,
  "train_trades_day": 2.19236,
  "train_avg_pnl_trade": -0.176065,
  "train_pf": 0.529548,
  "blind_pnl": -183.563595,
  "blind_usdc_day": -0.50154,
  "blind_trades": 919,
  "blind_trades_day": 2.510929,
  "blind_avg_pnl_trade": -0.199743,
  "blind_pf": 0.475985,
  "blind_max_dd": 183.950383
}
```

## Entscheidung

3 USDC/Tag nicht erreicht. Alle fertig gelaufenen Varianten 084-092 sind negativ; Attempt 093 wurde nicht mehr voll trade-level fertig, weil die Frequenzvarianten zu gross/langsam wurden. 053 bleibt besser.

## Wichtigste Erkenntnis

Mehr Aktivitaet ueber weichere 5m-Regeln zerstoert den Edge sofort. Der beste Weg bleibt: den originalen 053-Lauf im echten Optimizer mit Trade-Capture wiederholen, nicht approximieren.
