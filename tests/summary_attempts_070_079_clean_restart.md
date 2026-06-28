# Clean Restart Attempts 070-079

Diese Runde startet nach der Bereinigung ab Attempt 070 neu.

Referenz bleibt Attempt 053: 0.560647 USDC/Tag auf Candidate-Level, aber ohne originale Entry-Zeitpunkte.

## Ergebnis

3 USDC/Tag wurden nicht erreicht.

Kein neuer Kandidat schlägt Attempt 053.

## Best per Attempt

| Attempt | Name | Train USDC/Tag | Blind USDC/Tag | PF Blind | Entscheidung |
|---:|---|---:|---:|---:|---|
| 70 | 053_fingerprint_strict | -0.692334 | -0.926008 | 0.264645 | rejected |
| 71 | high_ethbtc_low_chop | -0.223676 | -0.362995 | 0.250363 | rejected |
| 72 | fast_time_kill | -0.839310 | -1.239690 | 0.225287 | rejected |
| 73 | runner_wide_tp | -0.201957 | -0.261469 | 0.447964 | rejected |
| 74 | mae_filter_calm | -0.753819 | -0.879416 | 0.193724 | rejected |
| 75 | quality_low_freq | -0.055532 | -0.091329 | 0.335086 | best_new_but_rejected |
| 76 | btc_not_dragging | -0.487481 | -0.678592 | 0.303239 | rejected |
| 77 | pullback_reclaim_proxy | -0.462355 | -0.620092 | 0.236284 | rejected |
| 78 | strong_flow_only | -0.376695 | -0.476015 | 0.261104 | rejected |
| 79 | balanced_target | -0.246026 | -0.400802 | 0.202793 | rejected |

## Bester neuer Kandidat

Attempt 75 `quality_low_freq`:

- Train: -0.055532 USDC/Tag
- Blind: -0.091329 USDC/Tag
- PF Blind: 0.335086
- Drawdown Blind: 33.706120 USDC
- Ergebnis: rejected

## Entscheidung

Die neue saubere 070-079-Runde ist reproduzierbar, aber schlecht. Sie bestaetigt: einfache 5m-Filter um 053 herum sind nicht der Weg zu 3 USDC/Tag.

## Naechster sinnvoller Pfad

Nicht weiter 5m-Regeln lockern. Entweder:

1. Originalen 053-Lauf im echten Optimizer mit Trade-Capture erneut ausfuehren, oder
2. neue Datenklasse verwenden: aggTrades/Orderbuch statt nur Candles.
