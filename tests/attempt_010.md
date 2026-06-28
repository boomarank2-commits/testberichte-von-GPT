# Attempt 010 - Kombination orthogonaler Signale

## Status

- Ergebnis: fehlgeschlagen
- Ziel: 3.000000 USDC pro Tag mit 100 USDC Kapitalrahmen
- Bester Blindtest-Wert: -0.017634 USDC/Tag
- Abstand zum Ziel: 3.017634 USDC/Tag

## Startregel

Dieser Versuch nutzt nur das hochgeladene Rohdatenpaket und die dokumentierten Erkenntnisse der vorherigen Attempts dieses Repositories. Keine alte Bot-Version ist Startpunkt.

## Idee

OR-Ensemble aus den besten Signalfamilien der Attempts 005, 006 und 008. Ziel war zu pruefen, ob mehrere schwache, unterschiedliche Signale zusammen mehr Aktivitaet liefern und trotzdem stabil bleiben.

## Bester Blindtest-Kandidat

```json
{
  "ensemble": "A5+A8",
  "members": 2,
  "raw_train_signals": 326,
  "tp": 0.0115,
  "sl": 0.007,
  "hold": 105
}
```

## Ergebnis Training

- USDC/Tag: -0.058270
- Trades: 207
- Profit Factor: 0.471936
- Max Drawdown: 46.782181

## Ergebnis Blindtest

- USDC/Tag: -0.017634
- Trades: 38
- Profit Factor: 0.642457
- Max Drawdown: 6.987775
- Worst Month: -2.481416

## Bewertung

Das Ensemble erhoeht die Aktivitaet, zerstoert aber die Edge. Die positive ETHBTC-Spur aus Attempt 008 wird durch schwache Signale aus anderen Familien verwässert.

## Nicht erneut in dieser Form testen

- Schwache Signalfamilien per OR kombinieren.
- Aktivitaet durch Hinzufuegen negativer Signale erhoehen.

## Naechster sinnvoller Test

Naechster Zyklus braucht neue Featureklassen oder einen reproduzierbaren Research-Runner, nicht nur weitere Parameterfeinsuche. Die ETHBTC-Staerke-Familie ist die beste Spur und sollte gezielt erweitert werden.
