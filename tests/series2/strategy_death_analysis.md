# Strategy Death Analysis - Testreihen bis Series2 011-020

## Kurzfazit
Die meisten Strategien sterben nicht an einem einzigen Fehler, sondern an einer Kombination aus Kostenlinie, falschem Exit und zu breiter Aktivitaet in Chop-Phasen.

Hauptmuster: Die Rohbewegung ist oft vorhanden, aber sie wird nicht sauber gefangen. Viele Trades haben MFE ueber Kosten, enden aber per Hold oder SL negativ.

## Gesamtbild Blindtest
- Aggregierte Blind-Trades in dieser Analyse: 43716
- Aggregierter Net-PnL: -7358.490 USDC
- Kostenmodell: 0.22 USDC pro 100-USDC-Roundtrip

## Gruppenvergleich Blindtest
| Gruppe | Strategien | Trades | Sum PnL | Avg Net/Trade | Avg Gross vor Kosten | Gross positive Share | Avg MFE | Avg MAE | MFE > Kosten |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| attempt073 | 1 | 1846 | -413.599 | -0.224052 | -0.004052 | 0.441 | nan | nan | nan |
| clean070_079 | 10 | 9567 | -2166.789 | -0.226409 | -0.006409 | 0.460 | 0.132 | -0.561 | 0.264 |
| posdna080_089 | 9 | 228 | -55.818 | -0.210110 | 0.009890 | 0.524 | nan | nan | nan |
| series2_001_010 | 10 | 14659 | -3349.662 | -0.311043 | -0.091043 | 0.421 | 0.513 | -0.828 | 0.657 |
| series2_011_020 | 10 | 5773 | -1372.623 | -0.231445 | -0.011445 | 0.467 | 0.546 | -0.491 | 0.655 |

## Exit-Reason Todeszone
| Exit Reason | Count | Sum PnL | Avg PnL | Interpretation |
|---|---:|---:|---:|---|
| sl | 4323 | -4824.725 | -1.064540 | Stop-Loss frisst den kompletten Vorteil. |
| hold | 25883 | -4713.370 | -0.170846 | Zeit-Ausgang ist zu spaet oder Entry hat keinen Follow-through. |
| sl_both | 9 | -10.056 | -1.117331 | Intrabar-Ambiguitaet, konservativ negativ. |
| sl_both_pessimistic | 4 | -4.280 | -1.070000 | Intrabar-Ambiguitaet, konservativ negativ. |
| mfelock | 19 | -3.285 | -0.130839 | Spezialexit, kleiner Einfluss. |
| be_stop | 7 | 0.385 | 0.055000 | Spezialexit, kleiner Einfluss. |
| tp | 1828 | 2196.841 | 1.171386 | Einziger klar positiver Exit-Typ, aber zu selten. |

## Die Verbindung / der gemeinsame Grund
1. Nach Kosten fehlt fast immer Edge. Viele Gruppen liegen vor Kosten nur knapp um Null; nach 0.22 USDC Roundtrip werden sie negativ.
2. Die Signale erzeugen zwar Bewegung, aber nicht ausreichend gerichtete Bewegung. MFE ist oft vorhanden, MAE und Ruecklauf sind aber zu gross.
3. Der Hold-Exit verliert in Summe stark. Das bedeutet: Viele Entries bekommen keinen schnellen Follow-through oder geben MFE wieder ab.
4. Stop-Loss-Treffer sind weniger haeufig als Hold-Exits, zerstoeren aber mit grossen Einzelschaden den gesamten PnL.
5. Standard-Daytrading-Indikatoren sterben besonders an ETH-Chop und Kosten. Mehr Frequenz verschlechtert den Netto pro Trade.
6. Attempt 053 bleibt anders, weil er ETHBTC-Leadership/Reclaim/Exit-Surface nutzt und im Blindtest +0.130615 USDC netto pro Trade schafft.

## Konsequenz fuer naechste Tests
- Nicht mehr neue Standardstrategien testen.
- Kein Hold-Exit als Hauptausgang ohne fruehen Follow-through-Test.
- Entry muss nach 1-3 Minuten beweisen, dass MFE entsteht; sonst Time-Kill.
- Bei MFE > Kosten muss ein MFE-Lock/BE-Stop greifen, sonst verschenkt der Bot Bewegung.
- Stop-Loss muss kontextabhaengig werden; feste SLs treffen zu oft in ETH-Wicks.
- Naechste sinnvolle Richtung: 053 exakt mit Trade-Capture oder 1m/aggTrade/Orderbook Microstructure.
