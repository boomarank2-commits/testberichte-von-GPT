# ETHUSDC StrategyLab

Dieses Repository ist der Arbeitsbereich fuer die systematische Erforschung einer eigenen ETHUSDC-Binance-Spot-Strategie.

## Hauptziel

Aus historischen ETHUSDC-Daten und zusaetzlichen Kontextdaten soll durch wiederholte Backtests, Auswertungen und dokumentierte Fehlschlaege eine realistische Strategie herausgefiltert oder neu entwickelt werden, die mit 100 USDC Einsatz langfristig mindestens 3 USDC pro Tag erreichen kann.

Das Ziel ist bewusst ambitioniert. Jeder Test muss ehrlich dokumentieren, ob er bestanden oder versagt hat. Fehlschlaege sind kein Abbruch, sondern werden als Wissen gespeichert, damit dieselben Sackgassen nicht wiederholt werden.

## Harte Projektregeln

- Handelspaar: ETHUSDC.
- Quote-Waehrung: USDC.
- Nur Binance Spot, kein Hebel.
- Keine beliebige 08/15-Strategie blind uebernehmen.
- Strategien muessen aus den vorhandenen ETHUSDC-Daten, Kontextdaten und Backtests heraus entwickelt werden.
- Rohdaten gehoeren nicht in dieses Repository.
- Code, Dokumentation, Testberichte und Erkenntnisse gehoeren in dieses Repository.
- Jeder fehlgeschlagene Versuch wird dokumentiert.
- Jeder neue Versuch muss pruefen, was vorher bereits ausgeschlossen wurde.
- Backtest-Regeln und spaetere Live-Regeln muessen identisch sein.

## Arbeitsweise

Der Forschungsprozess laeuft als Schleife:

1. Datenpaket bereitstellen.
2. Datenqualitaet pruefen.
3. Strategieidee formulieren.
4. Backtest durchfuehren.
5. Ergebnis bewerten.
6. Fehlschlag oder Erfolg dokumentieren.
7. Erkenntnisse in GitHub speichern.
8. Naechsten Test aus den bisherigen Erkenntnissen ableiten.

Diese Schleife wird so lange fortgesetzt, bis ein Kandidat gefunden wird, der das Ziel realistisch erfuellt oder klar gezeigt wird, welche Marktgrenzen das Ziel verhindern.

## Repository-Zweck

Dieses Repo ist nicht der Ort fuer grosse Rohdaten. Es ist der Ort fuer:

- Projektziel
- Strategieideen
- Testberichte
- Fehlschlagsdatenbank
- Backtest-Zusammenfassungen
- Regeln fuer weitere Versuche
- Dokumentation des aktuellen Erkenntnisstands

## Aktueller Startpunkt

V20 ist laut Kontext vollstaendig durchgelaufen. Verwendete Datenquellen sind unter anderem:

- ETHUSDC 1m Candles inkl. Kline-Orderflow
- ETHUSDC HTF 5m/15m/30m/1h/4h/1d, aus 1m abgeleitet
- Binance ETHUSDC exchange_info
- ETHUSDC aggTrade-Minutenfeatures
- BTCUSDC 1m
- ETHBTC 1m
- ETHUSDT 1m
- USDCUSDT 1m
- data_catalog.json
- Backtest-Run `run_20260628_101554`

Noch nicht sauber backtestfaehig:

- ETHUSDC bookTicker / Spread
- ETHUSDC Top-20 Depth / Orderbook

Diese Microstructure-Daten sollen erst ab mindestens 30 validen Tagen Coverage als Backtestfeature verwendet werden.
