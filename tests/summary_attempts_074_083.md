# Summary Attempts 074-083

## Zweck

074-083 ist die erste Runde nach 073 mit reproduzierbarer Trade-Level-Ausgabe je Bestversuch. Es wurden target-encoded Feature-Scores aus Trainingsdaten gebaut und im Blindtest mit echter Entry-/Exit-Liste geprüft.

## Ergebnis kurz

Alle neuen reproduzierbaren Tests 074-083 waren schlechter als der alte Candidate-Level-Champion 053.

- Bester alter Champion: Attempt 053 = 0.560647 USDC/Tag, aber ohne Trade-Level-Zeitpunkte.
- Bester neuer reproduzierbarer Kandidat aus 074-083: Attempt 083 = -0.001328 USDC/Tag.
- 3 USDC/Tag wurden nicht erreicht.

## Best per Attempt

| Attempt | Score | Gate | Blind USDC/Tag | Blind Trades/Tag | Blind Avg/Trade | Blind PF | Train USDC/Tag | Entscheidung |
|---:|---|---|---:|---:|---:|---:|---:|---|
| 074 | clean18 | ethlead | -0.027482 | 0.103825 | -0.264691 | 0.480716 | -0.017782 | rejected |
| 075 | swing35 | ethlead_strong | -0.007364 | 0.049180 | -0.149726 | 0.709488 | -0.012582 | rejected |
| 076 | any18 | flow | -0.040604 | 0.166667 | -0.243623 | 0.427819 | -0.020963 | rejected |
| 077 | capture18 | ethlead | -0.032811 | 0.117486 | -0.279276 | 0.386200 | -0.016604 | rejected |
| 078 | ensemble | overlap | -0.046244 | 0.243169 | -0.190170 | 0.513897 | -0.030666 | rejected |
| 079 | swing35 | low_chop | -0.009615 | 0.133880 | -0.071821 | 0.798473 | -0.029453 | rejected |
| 080 | any18 | week_eu_us | -0.100755 | 0.357923 | -0.281499 | 0.329488 | -0.044647 | rejected |
| 081 | lead_combo | ethlead | -0.006890 | 0.051913 | -0.132723 | 0.720520 | -0.027262 | rejected |
| 082 | ensemble | ethlead | -0.028112 | 0.106557 | -0.263819 | 0.416637 | -0.027069 | rejected |
| 083 | lead_combo | all_lead | -0.001328 | 0.177596 | -0.007475 | 0.976572 | -0.045008 | rejected |

## Champion 074-083

```json
{
  "attempt_no": 83,
  "score_name": "lead_combo",
  "gate": "all_lead",
  "q": 0.002,
  "threshold": 47.6715731,
  "raw_train_signals": 345,
  "raw_blind_signals": 234,
  "tp": 0.01,
  "sl": 0.008,
  "hold": 18,
  "gap": 10,
  "mode": "fixed",
  "train_usdc_day": -0.045008,
  "blind_usdc_day": -0.001328,
  "blind_pf": 0.976572,
  "rejection_reason": "train_nonpositive;negative_net_trade;pf_low;target_ratio_low;active_days_low"
}
```

## Entscheidung

074-083 haben das 3-USDC-Ziel nicht erreicht und schlagen Attempt 053 nicht. Damit bleibt Attempt 053 der beste Candidate-Level-Champion.

Wichtig: Diese Runde war trotzdem notwendig, weil sie zeigt, dass einfache ML-/Score-Signale mit echter Trade-Level-Replay-Logik keinen besseren robusten Kandidaten liefern.

## Nächster Schritt

Nicht weiter allgemeine ML-Scores testen. Der nächste sinnvolle Pfad ist weiterhin:

1. Originale 053-Familie im echten Optimizer erneut laufen lassen.
2. `capture_trades=True` erzwingen.
3. Jeden Top-Kandidaten mit Entry/Exit/MFE/MAE speichern.
4. Danach erst Partial-TP, Trail, MFE-Lock und Codex-Implementierung prüfen.
