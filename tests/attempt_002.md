# Attempt 002 - Marktphasen plus aggTrade-/Kontextfilter

## Status

- Ergebnis: fehlgeschlagen
- Ziel: 3.000000 USDC pro Tag mit 100 USDC Kapitalrahmen
- Bester Blindtest-Wert: -0.007750 USDC/Tag
- Abstand zum Ziel: 3.007750 USDC/Tag

## Startregel

Dieser Versuch nutzt nur das bereitgestellte Rohdatenpaket und die Erkenntnis aus Attempt 001. Es wird keine alte Bot-Version als Startpunkt verwendet.

## Datenstand

- ETHUSDC 1m: 2023-06-24 15:39:00+00:00 bis 2026-06-25 15:48:00+00:00, 1579690 Zeilen
- 15m-Bars: 105309
- Train-Bars: 70268
- Blind-Bars: 35041
- Split-Grenze: 2025-06-25 15:45:00+00:00
- aggTrade 15m-Bars: 107712

## Idee

Attempt 001 hat gezeigt, dass eine einfache globale Breakout-/Trend-Reclaim-Regel mit Kline-Orderflow nicht reicht.

Attempt 002 testet deshalb vier Richtungen:

1. `phase_breakout`: Breakout nur in Trend-Up-Regime mit BTC-/ETHBTC-Unterstuetzung und Orderflow-Bestaetigung.
2. `pullback_reclaim`: Pullback zur EMA in Trend-Up-Regime, danach Reclaim mit positivem Orderflow.
3. `liquidity_reversal`: Reversal nach lokalem Dump, wenn aggTrade-Kaeufer absorbieren und BTC/ETHBTC nicht stark dagegen laufen.
4. `quiet_expansion`: Ausbruch aus ruhiger Phase bei Volumen-/aggTrade-Expansion.

## Verwendete Features

- ETHUSDC OHLCV 15m aus 1m
- Kline Taker-Buy-Imbalance
- Kline Quote-Volume-Ratio
- aggTrade Imbalance
- aggTrade Volume-Ratio
- Max-AggTrade-Quote-Ratio
- BTCUSDC Kontext
- ETHBTC relative Staerke
- ETHUSDT Basis gegen ETHUSDC
- USDCUSDT Stablecoin-Abweichung
- UTC-Sessionfilter

## Suchraum

- Kandidaten erzeugt: 540
- Train-Kandidaten nach Mindestaktivitaet: 435
- Blindtest auf Top-80 Train-Kandidaten
- Fee: 10 bps pro Seite
- Slippage: 1 bp pro Seite
- Entry: Signal auf geschlossener 15m-Bar, Einstieg naechste Bar Open
- Exit: TP/SL intrabar, bei TP+SL in gleicher Bar pessimistisch SL, sonst Hold-Exit
- Kapital: 100 USDC, maximal eine Position gleichzeitig

## Bester Blindtest-Kandidat

```json
{
  "ai": 0.16,
  "atr_min": 0.0004,
  "atr_max": 0.02,
  "tp": 0.01,
  "ethbtc": -0.001,
  "sl": 0.006,
  "session": "eu_us",
  "av": 1.2,
  "hold": 24,
  "btc": -0.002,
  "kind": "quiet_expansion"
}
```

## Ergebnis Training des Kandidaten

- USDC/Tag: -0.007888
- Gesamt-PnL: -5.781708
- Trades/Tag: 0.058663
- Trades: 43
- Winrate: 0.395349
- Profit Factor: 0.665792
- Max Drawdown: 6.569729
- Worst Day: -0.808621
- Worst Month: -1.617241

## Ergebnis Blindtest

- USDC/Tag: -0.007750
- Gesamt-PnL: -2.836665
- Trades/Tag: 0.057377
- Trades: 21
- Winrate: 0.380952
- Profit Factor: 0.642872
- Max Drawdown: 2.868116
- Worst Day: -1.617241
- Worst Month: -2.425862
- Active Share: 5.464481 %
- Exit TP: 5
- Exit SL: 8
- Exit Hold: 8

## Bewertung

Attempt 002 erreicht das Ziel nicht. Gegenueber Attempt 001 ist die Richtung besser, weil der beste Kandidat im Blindtest nicht mehr deutlich negativ ist. Trotzdem liegt er sehr weit unter 3 USDC/Tag.

Die zentrale Erkenntnis: Marktphasen und aggTrade-/Kontextfilter reduzieren schlechte Trades, erzeugen aber noch keine ausreichend grosse Edge. Mit 100 USDC Kapitalrahmen ist 3 USDC/Tag nur erreichbar, wenn entweder sehr viele kleine Trades mit klar positiver Erwartung oder wenige sehr starke Bewegungen mit hoher Trefferqualitaet gefunden werden. Dieser Versuch findet beides noch nicht.

## Nicht erneut in dieser Form testen

- Ein statischer Long-only Kandidat pro Marktphase ohne adaptive Exit-Logik.
- AggTrade-Imbalance nur als einfacher Schwellenwert.
- Top-Train-Kandidaten direkt nach Blind-PnL waehlen, ohne Monats-/Walk-Forward-Stabilitaet.

## Naechster sinnvoller Test

Attempt 003 soll nicht zuerst Entry-Regeln optimieren, sondern Signalqualitaet ueber MFE/MAE messen:

1. Signale sammeln,
2. nach 4/8/16/32 Bars MFE und MAE berechnen,
3. profitable Signalcluster finden,
4. TP/SL/Hold aus der tatsaechlichen Verteilung ableiten,
5. dann erst vollstaendiger Backtest.
