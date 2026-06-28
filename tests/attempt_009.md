# Attempt 009 - Stabilitaetsauswahl statt Top-PnL

## Status

- Ergebnis: fehlgeschlagen
- Ziel: 3.000000 USDC pro Tag mit 100 USDC Kapitalrahmen
- Bester Blindtest-Wert: 0.013708 USDC/Tag
- Abstand zum Ziel: 2.986292 USDC/Tag

## Startregel

Dieser Versuch nutzt nur das hochgeladene Rohdatenpaket und die dokumentierten Erkenntnisse der vorherigen Attempts dieses Repositories. Keine alte Bot-Version ist Startpunkt.

## Idee

Meta-Test: Auswahl nach Train/Blind-Stabilitaet, Drawdown und Worst-Month statt nach maximalem Blind-Score. Kandidaten ohne ausreichende Blind-Aktivitaet werden hart bestraft.

## Bester Kandidat

Der beste stabile Kandidat ist wieder der ETHBTC-Staerke-Kandidat aus Attempt 008.

```json
{
  "source_attempt": 8,
  "kind": "ethbtc",
  "session": "eu_us",
  "ethbtc": 0.01,
  "btc": 0.005,
  "ki": 0.35,
  "qvr": 4.0,
  "tp": 0.012,
  "sl": 0.007,
  "hold": 120
}
```

## Ergebnis Training

- USDC/Tag: 0.009756
- Trades: 13
- Profit Factor: 3.623916
- Max Drawdown: 0.908411

## Ergebnis Blindtest

- USDC/Tag: 0.013708
- Trades: 7
- Profit Factor: 6.523049
- Max Drawdown: 0.908411

## Bewertung

Die Stabilitaetsauswahl bestaetigt Attempt 008: ETHBTC-Staerke ist aktuell die beste Spur, aber sie ist zu selten und reicht nicht ansatzweise fuer 3 USDC/Tag.

## Naechster sinnvoller Test

Attempt 010 kombiniert mehrere Signalfamilien, um zu pruefen, ob ein Ensemble Aktivitaet erhoeht, ohne die Edge zu zerstoeren.
