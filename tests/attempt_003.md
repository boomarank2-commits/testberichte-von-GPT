# Attempt 003 - MFE/MAE-basierte Exit-Ableitung

## Status

- Ergebnis: fehlgeschlagen
- Ziel: 3.000000 USDC pro Tag mit 100 USDC Kapitalrahmen
- Bester Blindtest-Wert: -0.009342 USDC/Tag
- Abstand zum Ziel: 3.009342 USDC/Tag

## Startregel

Dieser Versuch nutzt nur das Rohdatenpaket und die Erkenntnisse aus Attempt 001 und Attempt 002. Keine alte Bot-Version ist Startpunkt.

## Datenstand

- ETHUSDC 1m: 2023-06-24 15:39:00+00:00 bis 2026-06-25 15:48:00+00:00, 1579690 Zeilen
- 15m-Bars: 105309
- Train-Bars: 70268
- Blind-Bars: 35041
- Split-Grenze: 2025-06-25 15:45:00+00:00

## Idee

Attempt 002 hat gezeigt: bessere Filter allein reichen nicht. Attempt 003 misst deshalb vor dem Backtest die Signalqualitaet:

- MFE = maximale positive Bewegung nach Signal
- MAE = maximale negative Bewegung nach Signal
- Horizonte: 4, 8, 16 und 32 Bars auf 15m
- TP und SL werden aus der MFE/MAE-Verteilung im Training abgeleitet
- Danach wird mit realistischen Entry-/Exit-Regeln auf Blind getestet

## Suchraum

- Signaldefinitionen: 252
- MFE/MAE-Vorkandidaten: 808
- tatsaechlich auf Training replayed: 150
- Blindtest auf Top-80 Train-Kandidaten
- Fee: 10 bps pro Seite
- Slippage: 1 bp pro Seite
- Entry: Signal auf geschlossener 15m-Bar, Einstieg naechste Bar Open
- Exit: TP/SL intrabar, bei TP+SL in gleicher Bar pessimistisch SL, sonst Hold-Exit

## Bester Blindtest-Kandidat

```json
{
  "session": "eu_us",
  "ai": 0.08,
  "av": 1.8,
  "btc": -0.003,
  "ethbtc": -0.002,
  "atr_min": 0.0004,
  "atr_max": 0.025,
  "kind": "quiet_expansion",
  "tp": 0.01516,
  "sl": 0.00772,
  "horizon": 32
}
```

## Signalqualitaet im Training

- Signal Count Train: 40
- MFE q60: 0.020778
- MFE q70: 0.023323
- MAE q40 abs: 0.008578
- Edge Probability MFE > Kostenzone: 0.925000
- Bad Probability MAE < -0.4%: 0.625000

## Ergebnis Training des Kandidaten

- USDC/Tag: -0.002554
- Gesamt-PnL: -1.872202
- Trades/Tag: 0.053206
- Trades: 39
- Winrate: 0.435897
- Profit Factor: 0.898274
- Max Drawdown: 7.420398
- Worst Day: -0.980260
- Worst Month: -1.960519

## Ergebnis Blindtest

- USDC/Tag: -0.009342
- Gesamt-PnL: -3.419082
- Trades/Tag: 0.054645
- Trades: 20
- Winrate: 0.300000
- Profit Factor: 0.671589
- Max Drawdown: 4.539360
- Worst Day: -1.960519
- Worst Month: -2.662376
- Active Share: 5.191257 %
- Exit TP: 5
- Exit SL: 9
- Exit Hold: 6

## Bewertung

Attempt 003 erreicht das Ziel nicht. Die MFE/MAE-Ableitung verbessert die Suchlogik fachlich, aber die besten Signale bleiben zu selten und nicht robust genug. Der beste Blindtest liegt weiterhin weit unter 3 USDC/Tag.

Wichtig: Der Versuch zeigt, dass das Problem nicht nur die Exit-Wahl ist. Selbst wenn TP/SL aus der tatsaechlichen Bewegungsverteilung abgeleitet werden, fehlt noch ein Signalcluster mit ausreichend hoher Trefferqualitaet und Aktivitaet.

## Nicht erneut in dieser Form testen

- MFE/MAE nur auf 15m-Signalen ohne feinere Entry-Lokalisierung.
- Ein Signalcluster allein mit einem festen TP/SL/Hold.
- Kandidaten mit sehr niedriger Aktivitaet als Hauptweg zum 3-USDC-Ziel.

## Naechster sinnvoller Test

Attempt 004 soll die Entry-Lokalisierung verfeinern:

1. Signal auf 15m/30m als Kontext,
2. Entry auf 1m innerhalb des folgenden Fensters suchen,
3. nur einsteigen, wenn 1m-Orderflow die Richtung bestaetigt,
4. MFE/MAE dann auf dem 1m-Entry messen,
5. danach Backtest mit 1m-genauem Entry/Exit.
