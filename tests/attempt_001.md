# Attempt 001 - ETHUSDC Kline-Orderflow Baseline

## Status

- Ergebnis: fehlgeschlagen
- Ziel: 3.000000 USDC pro Tag mit 100 USDC Kapitalrahmen
- Erreichter Blindtest-Wert: -0.188234 USDC/Tag
- Abstand zum Ziel: 3.188234 USDC/Tag

## Datenstand

- ETHUSDC 1m: 2023-06-24T15:39:00Z bis 2026-06-25T15:48:00Z, 1579690 Zeilen
- Kontextdateien vorhanden: BTCUSDC, ETHBTC, ETHUSDT, USDCUSDT
- ETHUSDC aggTrade-Dateien vorhanden: 92
- Live-Microstructure-Dateien vorhanden: 4

Attempt 001 nutzt bewusst nur ETHUSDC-Candles inklusive Kline-Orderflow. Kontext- und aggTrade-Daten werden in Attempt 002/003 gezielt eingebaut, damit die Fehlschlaege sauber trennbar bleiben.

## Split

- Training/Suche: 2023-06-24T15:39:00Z bis 2025-06-25T15:47:00Z
- Blindtest: 2025-06-25T15:48:00Z bis 2026-06-25T15:48:00Z

## Strategieidee

Baseline fuer ETHUSDC selbst:

- Long-only Binance Spot
- Timeframe in diesem Minimaltest: 15m aus 1m gebaut
- Varianten in diesem Minimaltest: Trend-Reclaim und Breakout
- Kline-Orderflow: Taker-Buy-Quote-Imbalance und relatives Quote-Volume
- Sessionfilter in diesem Minimaltest: alle Stunden und EU/US
- Entry nach geschlossenem Signal auf der naechsten Kerze
- Exit per TP, SL, optional Trail und Max-Hold
- Kosten: 10 bps Fee pro Seite plus 1 bps Slippage

## Bester gefundener Kandidat

```json
{
  "tf": 15,
  "variant": "breakout",
  "session": "eu_us",
  "tp": 0.007,
  "sl": 0.004,
  "hold": 18,
  "trail": 0.003,
  "ema_fast": 12,
  "ema_slow": 48,
  "pull_atr": 0.8,
  "breakout_len": 24,
  "imb_min": 0.04,
  "vol_ratio_min": 0.8
}
```

## Ergebnis Training

- USDC/Tag: -0.123878
- Gesamt-PnL: -90.80238
- Trades/Tag: 1.004093
- Trades: 736
- Winrate: 0.19837
- Profit Factor: 0.18105
- Max Drawdown: 90.824511
- Worst Day: -1.439563
- Worst Month: -10.367059
- Active Share: 50.068213 %

## Ergebnis Blindtest

- USDC/Tag: -0.188234
- Gesamt-PnL: -68.893762
- Trades/Tag: 1.0
- Trades: 366
- Winrate: 0.188525
- Profit Factor: 0.177921
- Max Drawdown: 68.981985
- Worst Day: -2.20556
- Worst Month: -11.957347
- Active Share: 47.540984 %

## Warum fehlgeschlagen?

Das Ziel von 3 USDC/Tag wurde nicht erreicht. Der beste Blindtest-Kandidat liegt bei -0.188234 USDC/Tag und ist damit kein brauchbarer Takeover-Kandidat.

Die wichtigste Erkenntnis: Einfache ETHUSDC-Signale plus Kline-Orderflow-Schwellen reichen nicht. Der Markt produziert zwar viele Signale, aber nach Fee und Slippage bleibt keine Edge in der Groessenordnung von 3 Prozent pro Tag.

## Nicht erneut in dieser einfachen Form testen

- Trend-Reclaim, Breakout oder VWAP-Reclaim nur mit Kline-Taker-Imbalance.
- Globale Parameter fuer alle Marktphasen.
- Sessionfilter ohne vorherige Marktphasen-Erkennung.

## Naechster sinnvoller Test

Attempt 002 soll die vorhandenen Kontextdaten und die aggTrade-Minutenfeatures gezielt nutzen und zuerst Marktphasen bilden:

- Trend Up
- Trend Down
- Volatile Chop
- Quiet Range
- Liquidity Burst
- ETHBTC relative Staerke
- BTC-getriebene Bewegung

Danach soll pro Cluster eine eigene Entry-/Exit-Logik gesucht werden, statt eine globale Strategie auf alle ETHUSDC-Zustaende zu pressen.
