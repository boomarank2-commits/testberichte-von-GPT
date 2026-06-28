# Attempt 072 - Trade-Level Capture Diagnose für Attempt 053

## Status

- Ergebnis: kein neuer Backtest-Wert, sondern harte Datenqualitäts-Diagnose.
- Attempt 053 bleibt Champion: 0.560647 USDC/Tag.
- Beste Exit-Alternative gleicher Oberfläche bleibt darunter: 0.550602 USDC/Tag.

## Geprüfte vorhandene Dateien

- `attempts_051_060_fast_out/attempt_053_candidates.csv`
  - 45 Zeilen
  - enthält Kandidatenkennzahlen
  - enthält keine Entry-Zeitpunkte
  - enthält keine Exit-Zeitpunkte
- `attempt071_out/attempt071_fixed_entry_exit_surface.csv`
  - 30 Zeilen
  - enthält Exit-Surface-Kennzahlen
  - enthält keine Entry-Zeitpunkte
  - enthält keine Exit-Zeitpunkte

## Ergebnis der Prüfung

Die vorhandenen 053-Dateien enthalten nur Kandidatenkennzahlen, aber keine einzelnen Trade-Zeitpunkte.

Damit gibt es aktuell keine ehrliche Möglichkeit, aus den gespeicherten Dateien echte MFE/MAE pro Trade zu berechnen. Alles andere wäre geraten oder synthetisch und wäre für eine spätere Live-Übernahme gefährlich.

## Entscheidung

Attempt 053 bleibt gültiger Champion, aber er ist noch nicht takeover-reif, weil die Trade-Level-Prüfung fehlt.

## Verbindliches Trade-Level-Schema für den nächsten Runner

Pflichtspalten:

- `trade_id`
- `split`
- `entry_utc`
- `entry_i`
- `entry_price`
- `exit_utc`
- `exit_i`
- `exit_price`
- `exit_reason`
- `net_pnl_usdc`
- `gross_return_pct`
- `net_return_pct`
- `tp`
- `sl`
- `hold`
- `gap`
- `mfe_6m`, `mae_6m`
- `mfe_12m`, `mae_12m`
- `mfe_18m`, `mae_18m`
- `mfe_25m`, `mae_25m`
- `mfe_35m`, `mae_35m`
- `mfe_45m`, `mae_45m`
- `mfe_60m`, `mae_60m`
- `mfe_80m`, `mae_80m`
- `mfe_best_horizon`
- `mae_worst_horizon`
- `capture_ratio`
- `ethbtc_5m`
- `ethbtc_15m`
- `ethbtc_60m`
- `btc_15m`
- `btc_60m`
- `qvr_1m`
- `taker_imb_1m`
- `range_ratio_1m`
- `session_bucket`

## Nächster Schritt

Attempt 073 muss den 053-Runner neu ausführen und echte Trade-Level-Dateien erzeugen:

1. echte Entry-Timestamps,
2. echte Trade-Liste,
3. MFE/MAE je Trade,
4. Monatsstabilität aus echten Trades,
5. danach erst Partial-TP, Trail und MFE-Lock testen.

## Fazit

Der nächste Engpass ist nicht mehr TP/SL/Hold, sondern fehlende Trade-Level-Datenerfassung. Erst wenn diese Daten gespeichert sind, können wir den 053-Champion live-realistisch härten.