# Attempt 071a - Exit-Surface Diagnose auf Attempt-053-Kernspur

## Status

- Ergebnis: kein neuer Champion
- Referenz Attempt 053: 0.560647 USDC/Tag
- Beste Alternative auf gleicher gespeicherter 053-Entry-Surface: 0.550602 USDC/Tag
- Abstand zur Referenz: -0.010045 USDC/Tag

## Einschränkung

Attempt 053 hat Kennzahlen und Exit-Parameter gespeichert, aber keine einzelnen Entry-Zeitpunkte. Der direkte Rohdaten-Rekonstruktionslauf war zu schwer und brach ohne Ergebnis ab. Deshalb wurde 071a als Zwischenanalyse durchgeführt: alle gespeicherten 053-Kandidaten mit identischer Entry-Menge wurden als Exit-Surface ausgewertet.

## Referenz 053

```json
{
  "cid": 1929,
  "tp": 0.012,
  "sl": 0.008,
  "hold": 18,
  "gap": 15,
  "train_usdc_day": 0.321810,
  "train_trades_day": 3.714090,
  "train_avg_pnl_trade": 0.086646,
  "train_pf": 1.681599,
  "blind_usdc_day": 0.560647,
  "blind_trades_day": 4.292350,
  "blind_avg_pnl_trade": 0.130615,
  "blind_required_trades_day": 22.968196,
  "blind_target_ratio": 0.186882,
  "blind_pf": 2.190311,
  "blind_max_dd": 3.239916,
  "blind_worst_day": -1.960355,
  "blind_worst_month": 0.132363,
  "blind_active_share": 0.691257
}
```

## Beste Alternative gleicher Entry-Menge

```json
{
  "cid": 1705,
  "tp": 0.010,
  "sl": 0.008,
  "hold": 18,
  "gap": 15,
  "train_usdc_day": 0.300248,
  "blind_usdc_day": 0.550602,
  "blind_pf": 2.184932,
  "blind_max_dd": 2.538834,
  "blind_worst_month": -0.288624
}
```

## Diagnose

Die gespeicherte 053-Exit-Surface enthält 30 Kandidaten mit gleicher Entry-Menge. Der beste Satz bleibt TP 1.2 %, SL 0.8 %, Hold 18, Gap 15.

Sensitivität:
- bester Hold: 18 Minuten/Bars mit 0.560647 USDC/Tag
- bester TP: 1.2 % mit 0.560647 USDC/Tag
- bester SL: 0.8 % mit 0.560647 USDC/Tag

## Bewertung

Attempt 071a zeigt: Innerhalb der gespeicherten 053-Exit-Surface ist der Champion tatsächlich der beste Satz. Die Verbesserung kommt also nicht einfach durch kleinen TP/SL/Hold-Feinschliff.

Der nächste echte Hebel ist die fehlende Trade-Ebene:
- Entry-Timestamps speichern
- MFE/MAE pro Trade speichern
- MFE-Capture messen
- dann Partial-TP, Trail und MFE-Lock auf echten Trades optimieren

## Nächster Schritt

Attempt 072 muss den Research-Runner so umbauen, dass jeder Champion-Kandidat seine Entry-Timestamps und pro Trade MFE/MAE speichert. Erst danach kann die 053-Familie live-realistisch und sauber weiteroptimiert werden.
