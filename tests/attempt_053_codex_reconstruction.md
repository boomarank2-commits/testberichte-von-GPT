# Attempt 053 - Codex Reconstruction Note

## Zweck

Diese Datei beschreibt, wie der bisher beste bekannte Kandidat `Attempt 053` entstanden ist und was Codex spaeter rekonstruieren muss.

## Datenbasis

- Symbol: ETHUSDC Spot, long-only.
- Kapital je Trade: 100 USDC.
- Daten: 1m Candles mit Kontext ETHBTC und BTCUSDC.
- Zeitraum laut Combined Report:
  - First: 2023-06-24 15:39:00 UTC
  - Last: 2026-06-25 15:48:00 UTC
  - Split: 2025-06-25 15:48:00 UTC
- Training: alle Daten vor dem Split, ca. 2 Jahre.
- Blindtest: alle Daten nach dem Split, ca. 1 Jahr.
- Kostenmodell: 0.22 Prozent Roundtrip, also Fee plus Slippage je Seite.

## Strategiefamilie

- Attempt: 053
- Family: exit_surface_ethbtc
- Kind: reclaim5
- Idee: ETHBTC-Leadership als Regime, danach 1m/Reclaim-nahe Entry-Lokalisierung und Exit-Surface ueber TP/SL/Hold/Gap.

## Champion Parameter

Top Candidate aus `attempt_053_candidates.csv`:

- cid: 1929
- gap: 15
- tp: 0.012
- sl: 0.008
- hold: 18
- raw_train_signals: 12345
- train_trades: 2715
- blind_trades: 1571

Interpretation:

- `tp=0.012` bedeutet ca. +1.2 Prozent Bruttoziel.
- `sl=0.008` bedeutet ca. -0.8 Prozent Brutto-Stop.
- `hold=18` bedeutet maximale Haltedauer in der verwendeten Runner-Einheit.
- `gap=15` ist die Signal-/Reentry-Abstandslogik der 053-Surface.

## Ergebnis Training

- Train PnL: 235.243154 USDC
- Train USDC/Tag: 0.321810
- Train Trades: 2715
- Train Trades/Tag: 3.714090
- Train Avg PnL/Trade: 0.086646 USDC
- Train PF: 1.681599
- Train Max DD: 6.720156 USDC
- Train Worst Day: -5.167099 USDC
- Train Worst Month: -1.179287 USDC
- Train Active Share: 0.653899

## Ergebnis Blindtest

- Blind PnL: 205.196782 USDC
- Blind USDC/Tag: 0.560647
- Blind Trades: 1571
- Blind Trades/Tag: 4.292350
- Blind Avg PnL/Trade: 0.130615 USDC
- Blind PF: 2.190311
- Blind Max DD: 3.239916 USDC
- Blind Worst Day: -1.960355 USDC
- Blind Worst Month: 0.132363 USDC
- Blind Active Share: 0.691257
- Required Trades/Day for 3 USDC at this avg trade: 22.968196
- Target Ratio: 0.186882
- Rejection Reason: passes_filters

## Warum 053 wichtig ist

Attempt 053 war der erste Kandidat, der die internen Filter bestanden hat. Er hat nicht das Ziel von 3 USDC/Tag erreicht, aber er war bis jetzt der beste stabile Kandidat mit positivem Train und positivem Blindtest.

## Wie der Runner es geschafft hat

1. ETHUSDC 1m Candles laden.
2. BTCUSDC und ETHBTC als Kontext dazuladen.
3. Train/Blind nach Split trennen.
4. ETHBTC-Leadership/Reclaim5-Signalmenge erzeugen.
5. Nur auf Training Exit-Surface ueber Gap, TP, SL und Hold suchen.
6. Kandidaten nach Train-Qualitaet, PF, Drawdown, Aktivitaet und Target-Ratio bewerten.
7. Beste Parameter unveraendert auf den Blindtest anwenden.
8. Candidate 1929 war die beste Surface-Kombination.

## Wichtige Einschraenkung

Der alte 053-Lauf speicherte keine echten Entry-/Exit-Zeitpunkte je Trade. Deshalb darf Codex nicht behaupten, MFE/MAE oder Live-Ausfuehrung exakt aus 053 rekonstruieren zu koennen.

Codex muss den 053-Runner mit denselben Signalen und Parametern erneut laufen lassen und dabei `capture_trades=True` erzwingen.

Pflichtausgaben fuer eine echte Rekonstruktion:

- trade_level_entries.csv
- trade_level_mfe_mae.csv
- entry_context_snapshots.csv
- exit_surface_with_capture.csv

Pflichtfelder:

- entry_utc
- entry_price
- exit_utc
- exit_price
- exit_reason
- net_pnl_usdc
- MFE/MAE je Trade
- ETHBTC/BTC/Flow-Kontext beim Entry

## Codex darf implementieren, wenn

- der rekonstruierte Lauf wieder nahe an 0.560647 USDC/Tag im Blindtest kommt,
- die Trade-Anzahl nahe 1571 im Blindtest liegt,
- Train und Blind positiv bleiben,
- PF und Drawdown stabil bleiben,
- Trade-Level-Dateien vorhanden sind.

## Codex darf nicht implementieren, wenn

- nur eine approximierte 053-Variante negativ laeuft,
- Entry-Zeitpunkte fehlen,
- der Kandidat nur im Training positiv ist,
- 3 USDC/Tag behauptet wird, ohne Blindtest und Trade-Level-Dateien.
