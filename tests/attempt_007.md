# Attempt 007 - Selektives Panic-Reversal nach schnellen ETH-Dumps

## Status

- Ergebnis: fehlgeschlagen
- Ziel: 3.000000 USDC pro Tag mit 100 USDC Kapitalrahmen
- Bester Blindtest-Wert: 0.000000 USDC/Tag
- Abstand zum Ziel: 3.000000 USDC/Tag

## Startregel

Dieser Versuch nutzt nur das hochgeladene Rohdatenpaket und die dokumentierten Erkenntnisse der vorherigen Attempts dieses Repositories. Keine alte Bot-Version ist Startpunkt.

## Idee

Sehr selektiver Dip-Reversal-Test nach starken 5m-Dumps mit hohem Volumen und Kaeuferdruck. Ziel war: weniger Trades, dafuer groessere Bewegung.

## Bester Trainingskandidat

```json
{
  "kind": "panic",
  "session": "us",
  "drop": 0.012,
  "ki": 0.25,
  "qvr": 4.0,
  "tp": 0.012,
  "sl": 0.0075,
  "hold": 90,
  "raw_train_signals": 9
}
```

## Ergebnis Training

- USDC/Tag: 0.002048
- Trades: 8
- Profit Factor: 1.522276

## Ergebnis Blindtest

- USDC/Tag: 0.000000
- Trades: 0
- Profit Factor: 0.000000

## Bewertung

Der Ansatz war im Training leicht positiv, hatte im Blindtest aber keine Aktivitaet. Damit ist er als Bot-Strategie unbrauchbar. Zu seltene Signale koennen das Tagesziel nicht erreichen.

## Nicht erneut in dieser Form testen

- Panic-Reversal mit so harten Schwellen als Hauptstrategie.
- Kandidaten akzeptieren, die im Blindtest keine Trades liefern.

## Naechster sinnvoller Test

Attempt 008 nutzt ETHBTC relative Staerke als Hauptfilter.
