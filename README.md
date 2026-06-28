# ETHUSDC StrategyLab

Dieses Repository ist der Arbeitsbereich fuer die systematische Erforschung einer eigenen ETHUSDC-Binance-Spot-Strategie.

## Hauptziel

Aus den bereitgestellten historischen ETHUSDC-Rohdaten und zusaetzlichen Kontextdaten soll durch wiederholte Backtests, Auswertungen und dokumentierte Fehlschlaege eine realistische Strategie herausgefiltert oder neu entwickelt werden, die mit 100 USDC Kapitalrahmen langfristig mindestens 3 USDC pro Tag erreichen kann.

Das Ziel ist bewusst ambitioniert. Jeder Test muss ehrlich dokumentieren, ob er bestanden oder versagt hat. Fehlschlaege sind kein Abbruch, sondern werden als Wissen gespeichert, damit dieselben Sackgassen nicht wiederholt werden.

## Wichtige Klarstellung

Dieses Repository startet nicht bei einer alten Bot-Version und nicht bei einem alten V-Lauf. Fuer dieses Repo zaehlt nur:

1. das jeweils hochgeladene Rohdatenpaket,
2. der daraus abgeleitete eigene Attempt 001,
3. danach Attempt 002, Attempt 003 usw.

Alte Bot-Versionen, alte Reports oder fremde Annahmen duerfen nicht als fachlicher Startpunkt verwendet werden, ausser der Nutzer fordert das ausdruecklich an.

## Harte Projektregeln

- Handelspaar: ETHUSDC.
- Quote-Waehrung: USDC.
- Nur Binance Spot, kein Hebel.
- Keine beliebige Standardstrategie blind uebernehmen.
- Strategien muessen aus den vorhandenen ETHUSDC-Rohdaten und Kontextdaten heraus entwickelt werden.
- Rohdaten gehoeren nicht in dieses Repository.
- Code, Dokumentation, Testberichte und Erkenntnisse gehoeren in dieses Repository.
- Jeder fehlgeschlagene Versuch wird dokumentiert.
- Jeder neue Versuch muss pruefen, was vorher bereits ausgeschlossen wurde.
- Backtest-Regeln und spaetere Live-Regeln muessen identisch sein.

## Arbeitsweise

Der Forschungsprozess laeuft als Schleife:

1. Rohdatenpaket bereitstellen.
2. Datenqualitaet pruefen.
3. Strategieidee formulieren.
4. Backtest durchfuehren.
5. Ergebnis bewerten.
6. Fehlschlag oder Erfolg dokumentieren.
7. Erkenntnisse in GitHub speichern.
8. Naechsten Test aus den bisherigen Erkenntnissen ableiten.

Diese Schleife wird pro Chat-Durchlauf so weit wie moeglich fortgesetzt. Das Repo dient als Gedaechtnis, damit spaetere Durchlaeufe nicht wieder bei null anfangen.

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

Startpunkt ist das hochgeladene Rohdatenpaket `gpt_raw_market_dataset_20260628.zip`.

Darin enthaltene Datenquellen laut erster Pruefung:

- ETHUSDC 1m Candles inkl. Kline-Orderflow
- abgeleitete oder ableitbare HTF-Daten aus 1m
- Binance ETHUSDC exchange_info
- ETHUSDC aggTrade-Minutenfeatures
- BTCUSDC 1m
- ETHBTC 1m
- ETHUSDT 1m
- USDCUSDT 1m
- data_catalog.json

Noch nicht sauber backtestfaehig:

- ETHUSDC bookTicker / Spread
- ETHUSDC Top-20 Depth / Orderbook

Diese Microstructure-Daten sollen erst ab mindestens 30 validen Tagen Coverage als Backtestfeature verwendet werden.
