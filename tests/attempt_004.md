# Attempt 004 - 15m Kontext mit 1m Entry-Lokalisierung

## Status

- Ergebnis: fehlgeschlagen
- Ziel: 3.000000 USDC pro Tag mit 100 USDC Kapitalrahmen
- Bester Blindtest-Wert: -0.008791 USDC/Tag
- Abstand zum Ziel: 3.008791 USDC/Tag

## Startregel

Dieser Versuch nutzt nur das hochgeladene Rohdatenpaket und die dokumentierten Erkenntnisse der vorherigen Attempts dieses Repositories. Keine alte Bot-Version ist Startpunkt.

## Idee

15m-Kontext oeffnet nur ein Entry-Fenster; Einstieg erfolgt auf 1m per Reclaim oder Micro-Breakout.

## Bester Blindtest-Kandidat

```json
{
  "ctx": ["quiet", "eu_us"],
  "kind": "break",
  "session": "all",
  "ki": 0.12,
  "qvr": 1.0,
  "tp": 0.007,
  "sl": 0.0045,
  "hold": 45
}
```

## Ergebnis Training

- USDC/Tag: -0.011313
- Trades: 34
- Profit Factor: 0.305651

## Ergebnis Blindtest

- USDC/Tag: -0.008791
- Trades: 14
- Profit Factor: 0.340083
- Max Drawdown: 3.217555
- Worst Month: -1.343944

## Bewertung

15m-Kontext plus 1m-Entry-Lokalisierung verbessert die Kontrolle, erzeugt aber keine positive Edge. Der Einstieg ist genauer als bei Attempt 003, aber weiterhin nicht gut genug.

## Nicht erneut in dieser Form testen

- 15m-Kontextfenster plus simpler 1m-Breakout/Reclaim als Hauptsignal.
- Quiet-Expansion-Kontext ohne staerkeren ETHBTC/BTC-Filter.

## Naechster sinnvoller Test

Attempt 005 isoliert Tageszeit und Wochentag, weil Kontext plus 1m-Trigger noch nicht reicht.
