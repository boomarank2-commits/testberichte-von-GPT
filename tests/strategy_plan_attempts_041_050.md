# Strategieplan Attempts 041-050

Stand: 2026-06-28
Symbol: ETHUSDC
Kapitalannahme: 100 USDC
Ziel: >= 3 USDC pro Tag im 365-Tage-Blindtest

## Grundsatzwechsel

Die Attempts 001-040 haben gezeigt: normale Strategiefamilien und grobe 15m-Bar-Close-Entries reichen nicht.

Die Deep-Research-Auswertung zeigt dagegen:

- ETHUSDC hat genug intraday Bewegung.
- Die theoretische nicht-ueberlappende 15m-Oracle-Kapazitaet liegt grob bei 5.25 bis 6.70 USDC/Tag.
- Das Ziel ist historisch nicht offensichtlich unmoeglich.
- Der Engpass ist nicht die Marktbewegung, sondern Extraction Fidelity.

Neue Regel:

15m ist nur noch Kontext. Entry und Exit muessen auf 1m lokalisiert werden.

## Verbot fuer die naechste Runde

Nicht mehr testen:

- Entry direkt auf 15m Bar-Close als fertige Strategie
- generische EMA/RSI/MACD-artige Templates
- reine Volume-Pop-Weiterfuehrung ohne 1m-Lokalisierung
- Kandidaten mit positiver Mini-Performance, aber ohne Zielmechanik
- Strategien, die zwar Profit Factor haben, aber viel zu wenige Trades liefern

## Gemeinsamer Bewertungsfilter fuer Attempts 041-050

Jeder Attempt muss neben USDC/Tag auch die Zielmechanik ausweisen:

```text
capital = 100 USDC
roundtrip_cost ~= 0.21 Prozent
net_usdc_trade = 100 * net_return_after_costs
required_trades_day = 3 / net_usdc_trade, falls net_usdc_trade > 0
target_ratio = trades_day / required_trades_day
```

Frueh verwerfen, wenn:

```text
net_usdc_trade <= 0
profit_factor < 1.20
max_drawdown > 20 USDC
target_ratio < 0.15
aktive Tage < 20 Prozent der Blindperiode
```

## Attempt 041: ETH Oracle-MFE Harvest Map

Zweck:
Vor dem naechsten Entry-Test exakt kartieren, wo die nutzbaren MFE-Fenster liegen.

Test:
- 1m und 15m Fenster mit 15/30/60/120m Forward-MFE
- Kostenhuerde 0.21 Prozent
- nach Stunde, Wochentag, ETHBTC-Regime, BTC-Schock, Volume-Z, Range-Z clustern

Erfolg:
- eine Rangliste der besten Rohpotenzial-Zellen
- Mindestziel: Zellen mit rechnerisch >= 3 USDC/Tag Oracle-Naehe

## Attempt 042: BTC-Shock + ETH-Resilience + 1m Reclaim

Hypothese:
Wenn BTC kurzfristig stark negativ schockt, ETHBTC aber relativ stark bleibt, entstehen ETH-spezifische Reclaim-Bewegungen.

Kontext:
- BTCUSDC 15m Return in unteren Quantilen q2-q10
- ETHBTC 15m/30m Relative Strength q70-q95
- ETHUSDC nicht unter eigener Katastrophen-Schwelle

1m Entry:
- nach BTC-Schock kein Sofortkauf
- warten auf 1m Reclaim ueber 5m-Mid oder lokales VWAP
- Pullback 0.05-0.18 Prozent
- Entry nur nach Rebreak

Exit:
- TP1 0.28-0.55 Prozent
- SL 0.18-0.35 Prozent
- Hold 12-45 Minuten
- Exit bei ETHBTC-Reversal

## Attempt 043: US-Overlap Expansion mit verzoegertem 1m Retest

Hypothese:
13-16 UTC liefert die meiste ETH-Bewegung, aber 15m-Schlusskurs ist zu spaet.

Kontext:
- UTC 13-16
- Volume-Z 1.0-2.5
- Range-Z 0.7-2.0
- Agg-Buy-Share 0.52-0.68

1m Entry:
- nicht auf Breakout-Bar kaufen
- erster Retest der Breakout-Zone
- Rebreak ueber 1m Trigger-Level
- maximal 1-3 Micro-Entries pro Kontext

Exit:
- TP1 schnell 0.20-0.35 Prozent
- Rest per Trail 1m Swing
- Time-Stop 8-30 Minuten

## Attempt 044: Exit-Engine-Only auf besten bisherigen Entry-Kontexten

Hypothese:
Die Entry-Kontexte sind nicht komplett falsch; der Hauptverlust liegt in schlechter MFE-Realisierung.

Test:
- identische Entries aus besten Kontexten nehmen
- nur Exit-Familien variieren

Exit-Familien:
1. Voll-TP fix
2. TP1 + Trail
3. TP1 + ETHBTC-Reversal-Exit
4. Time-Stop hart
5. MFE-Lock nach X Minuten

Erfolg:
- mindestens 30 Prozent bessere MFE-zu-PnL-Capture gegen bisherigen Exit

## Attempt 045: Asia Compression -> Europe/US Wake-Up

Hypothese:
Nach 02-07 UTC Kompression entsteht im Europe/US Hand-off ein handelbarer Wake-Up-Impuls, aber nur wenn ETHBTC bestaetigt.

Kontext:
- vorherige 60m Realized Vol unter q20-q40
- 11-14 UTC Startfenster
- 1m Volumenspike 2x-4x lokaler Median
- Break ueber 15m High
- ETHBTC positiv oder steigend

Exit:
- initialer SL unter Compression-Range
- TP1 0.25-0.45 Prozent
- Rest maximal 60m halten

## Attempt 046: ETHBTC Leadership Continuation

Hypothese:
ETHUSDC folgt besser, wenn ETHBTC bereits Fuehrung zeigt und BTC nicht dagegen laeuft.

Kontext:
- ETHBTC 15m/60m q80-q95
- BTCUSDC 15m nicht stark negativ
- ETHUSDC Pullback nicht tiefer als definierte ATR-Zone

1m Entry:
- 1m higher-low nach ETHBTC-Schub
- Reclaim ueber lokales 5m-Mid

Exit:
- Exit sofort bei ETHBTC Momentum-Bruch
- kein blindes Halten nur wegen ETHUSDC

## Attempt 047: USDC/USDT Basis als Gate fuer Stress-Vermeidung

Hypothese:
Basis ist kein Hauptsignal, aber ein guter Filter gegen falsche ETHUSDC-Signale.

Test:
- beste Attempt-042/043/046 Entries nochmal laufen lassen
- ETHUSDC vs synthetisch ETHUSDT*USDCUSDT Basis als Veto
- USDCUSDT Spread als Stressfilter

Ziel:
- weniger schlechte Trades
- PF und Drawdown verbessern, ohne Trades/Tag zu stark zu senken

## Attempt 048: Multi-Entry pro qualifiziertem ETH-Kontext

Hypothese:
Oracle zeigt genug Frequenz. Ein Trade pro Kontext laesst zu viel liegen.

Regel:
- nur in Kontexten aus 042/043/046
- maximal 2-4 Entries je Kontext
- Cooldown 3-10 Minuten
- jeder Entry braucht eigenen 1m Trigger
- Kill bei ETHBTC-Reversal oder fehlendem AggFlow

Bewertung:
- Zielmechanik muss steigen, nicht nur Tradezahl

## Attempt 049: AggTrade Flow Confirmation

Hypothese:
1m Reclaim funktioniert nur, wenn echter Taker-/AggTrade-Flow die Bewegung bestaetigt.

Features:
- aggTrade Count Z-Score
- taker buy/sell imbalance
- VWAP-Abstand
- max trade quote als Sweep-/Absorption-Hinweis

Test:
- 042/043/046 mit und ohne AggFlow-Gate vergleichen
- fehlende aggTrade-Minuten vorher auf 1m-Kalender reindizieren und Nullwerte fuellen

## Attempt 050: Kombinierter ETH-Regime-Router

Hypothese:
Eine Einzelstrategie reicht nicht. ETH braucht einen Router:

- BTC-Schock/ETH-Resilience
- US-Overlap Retest
- Asia Compression Wake-Up
- ETHBTC Leadership

Regel:
- pro Regime eigene Entry-/Exit-Parameter
- Kapital bleibt 100 USDC
- keine gleichzeitigen widerspruechlichen Positionen
- MaxOpen und Reentry streng begrenzen

Erfolg:
- bester kombinierter Jahresblindtest
- Zielmechanik, PF, DD, aktive Tage und Worst Month muessen zusammen passen

## Erwartung

Diese Runde ist deutlich sinnvoller als 001-040, weil sie nicht mehr fragt:

Welche bekannte Strategie funktioniert auf ETH?

Sondern:

Wo zeigt ETH laut Daten echte positive MFE, wie erkenne ich den 1m-Einstieg, und wie realisiere ich die Bewegung nach Kosten?

## Naechster operativer Schritt

Attempt 041 zuerst ausfuehren. Ohne Harvest Map werden 042-050 wieder blind.
Danach die Familien 042, 043 und 044 priorisieren, weil sie am direktesten auf den gefundenen Engpass zielen: 15m-Kontext war zu grob, 1m-Entry und Exit waren bisher zu schwach.
