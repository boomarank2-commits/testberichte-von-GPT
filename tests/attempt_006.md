# Attempt 006 - Stark gefilterter 1m-Scalp

## Status

- Ergebnis: fehlgeschlagen
- Ziel: 3.000000 USDC pro Tag mit 100 USDC Kapitalrahmen
- Bester Blindtest-Wert: -0.036007 USDC/Tag
- Abstand zum Ziel: 3.036007 USDC/Tag

## Startregel

Dieser Versuch nutzt nur das hochgeladene Rohdatenpaket und die dokumentierten Erkenntnisse der vorherigen Attempts dieses Repositories. Keine alte Bot-Version ist Startpunkt.

## Idee

Kurzer 1m-Scalp mit hohen Orderflow- und Volumenschwellen, um Gebuehrenfresser aus Attempt 005 zu vermeiden.

## Bester Blindtest-Kandidat

```json
{
  "kind": "break",
  "session": "high_overlap",
  "ki": 0.65,
  "qvr": 8.0,
  "tp": 0.004,
  "sl": 0.003,
  "hold": 15
}
```

## Ergebnis Training

- USDC/Tag: -0.182156
- Trades: 583
- Profit Factor: 0.083840

## Ergebnis Blindtest

- USDC/Tag: -0.036007
- Trades: 70
- Profit Factor: 0.148974
- Max Drawdown: 13.178741
- Worst Month: -2.608919

## Bewertung

Viele kurze 1m-Trades bleiben nach Fee und Slippage stark negativ. Der Versuch schliesst reines 1m-Scalping ohne deutlich staerkere Edge als Hauptweg aus.

## Nicht erneut in dieser Form testen

- 1m-Scalp mit reinem Breakout/Orderflow.
- Kleine TP/SL-Struktur, die hauptsaechlich Gebuehren produziert.

## Naechster sinnvoller Test

Attempt 007 testet Panic-Reversal nach schnellen Dumps.
