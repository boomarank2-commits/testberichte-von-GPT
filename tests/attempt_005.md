# Attempt 005 - Tageszeit- und Wochentag-Spezialisierung

## Status

- Ergebnis: fehlgeschlagen
- Ziel: 3.000000 USDC pro Tag mit 100 USDC Kapitalrahmen
- Bester Blindtest-Wert: -0.025176 USDC/Tag
- Abstand zum Ziel: 3.025176 USDC/Tag

## Startregel

Dieser Versuch nutzt nur das hochgeladene Rohdatenpaket und die dokumentierten Erkenntnisse der vorherigen Attempts dieses Repositories. Keine alte Bot-Version ist Startpunkt.

## Idee

ETHUSDC wird nach UTC-Session und Werktag gefiltert, ohne 15m-Kontext. Ziel war zu pruefen, ob bestimmte Handelszeiten allein eine Edge liefern.

## Bester Blindtest-Kandidat

```json
{
  "kind": "vwap_proxy",
  "session": "high_overlap",
  "weekdays": true,
  "ki": 0.4,
  "qvr": 6.0,
  "tp": 0.011,
  "sl": 0.007,
  "hold": 90
}
```

## Ergebnis Training

- USDC/Tag: -0.070115
- Trades: 199
- Profit Factor: 0.336843

## Ergebnis Blindtest

- USDC/Tag: -0.025176
- Trades: 31
- Profit Factor: 0.370586
- Max Drawdown: 9.214348
- Worst Month: -2.637542

## Bewertung

Reine Tageszeit- und Wochentagfilter reichen nicht. Auch das US/EU-Overlap-Fenster mit hohen Volumenschwellen bleibt negativ.

## Nicht erneut in dieser Form testen

- Uhrzeitfilter als Hauptsignal.
- VWAP-/EMA-Reclaim ohne staerkeren Marktphasen- oder ETHBTC-Kontext.

## Naechster sinnvoller Test

Attempt 006 testet stark gefilterte 1m-Scalps gegen Gebuehren.
