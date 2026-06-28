# Projektziel

Dieses Repository dokumentiert die Forschung an einer eigenen ETHUSDC-Strategie fuer Binance Spot.

## Ziel

- Symbol: ETHUSDC
- Quote: USDC
- Markt: Binance Spot
- Kapitalrahmen: 100 USDC
- Zielwert: 3 USDC pro Tag oder mehr im Backtest und spaeter in der Live-Kontrolle

## Grundidee

Es soll keine beliebige Standardstrategie blind uebernommen werden. Die Strategie soll aus den vorhandenen ETHUSDC-Daten, Kontextdaten und Backtestergebnissen entwickelt werden.

## Arbeitskreislauf

1. Datenstand pruefen.
2. Bisherige Tests lesen.
3. Neue Strategieidee formulieren.
4. Backtest ausfuehren.
5. Ergebnis bewerten.
6. Erfolg oder Fehlschlag dokumentieren.
7. Naechsten Test aus den Erkenntnissen ableiten.

## Dokumentationsregel

Jeder Versuch bekommt einen eigenen Bericht:

- `tests/attempt_001.md`
- `tests/attempt_002.md`
- `tests/attempt_003.md`

Jeder Bericht muss festhalten:

- Strategieidee
- Datenstand
- verwendete Features
- Backtestzeitraum
- wichtigste Kennzahlen
- Ergebnis
- Grund fuer Erfolg oder Fehlschlag
- Erkenntnis fuer den naechsten Versuch

## Wichtige Projektregel

Rohdaten werden nicht in dieses Repository committed. Dieses Repository speichert nur Ziel, Code, Testberichte, Erkenntnisse und kleine Vorlagen.
