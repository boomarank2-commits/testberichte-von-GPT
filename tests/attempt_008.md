# Attempt 008 - Hochselektive ETHBTC Relative-Staerke

## Status

- Ergebnis: fehlgeschlagen
- Ziel: 3.000000 USDC pro Tag mit 100 USDC Kapitalrahmen
- Bester Blindtest-Wert: 0.013708 USDC/Tag
- Abstand zum Ziel: 2.986292 USDC/Tag

## Startregel

Dieser Versuch nutzt nur das hochgeladene Rohdatenpaket und die dokumentierten Erkenntnisse der vorherigen Attempts dieses Repositories. Keine alte Bot-Version ist Startpunkt.

## Idee

Sehr selektiver Test: ETH muss gegen BTC deutlich stark sein, BTC positiv, 1m-Orderflow und Volumen muessen bestaetigen.

## Bester Blindtest-Kandidat

```json
{
  "kind": "ethbtc",
  "session": "eu_us",
  "ethbtc": 0.01,
  "btc": 0.005,
  "ki": 0.35,
  "qvr": 4.0,
  "tp": 0.012,
  "sl": 0.007,
  "hold": 120,
  "raw_train_signals": 18
}
```

## Ergebnis Training

- USDC/Tag: 0.009756
- Gesamt-PnL: 7.150782
- Trades: 13
- Winrate: 0.769231
- Profit Factor: 3.623916
- Max Drawdown: 0.908411

## Ergebnis Blindtest

- USDC/Tag: 0.013708
- Gesamt-PnL: 5.017198
- Trades: 7
- Winrate: 0.857143
- Profit Factor: 6.523049
- Max Drawdown: 0.908411
- Worst Day: -0.908411
- Worst Month: 0.000000
- Exit TP: 6
- Exit SL: 1

## Bewertung

Das ist der erste positive Blindtest nach Fee und Slippage in dieser Schleife. Trotzdem ist er weit vom Ziel entfernt, weil die Aktivitaet extrem niedrig ist: nur 7 Trades im Blindtest und 0.013708 USDC/Tag statt 3 USDC/Tag.

## Erkenntnis

ETHBTC relative Staerke ist bisher die beste Spur. Sie darf nicht verworfen werden, muss aber deutlich mehr Aktivitaet liefern, ohne den Profit Factor komplett zu zerstoeren.

## Nicht erneut in dieser Form testen

- ETHBTC-Staerke so hart filtern, dass nur wenige Trades pro Jahr entstehen.

## Naechster sinnvoller Test

Attempt 009 waehlt aus 004 bis 008 nach Stabilitaet statt maximalem PnL.
