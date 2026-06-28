# Attempt 073 - Trade-Level Capture fuer 053-Familie

## Status

Attempt 073 hat die fehlende Trade-Level-Datenebene erzeugt.

Wichtig: Der originale Attempt 053 speicherte nur Kandidatenkennzahlen, aber keine Entry-/Exit-Zeitpunkte. Deshalb kann man den originalen 053-Champion nicht nachtraeglich exakt auf MFE/MAE pruefen.

## Referenz 053

- Candidate-Level Blindtest: 0.560647 USDC pro Tag
- Train: 0.321810 USDC pro Tag
- PF Blind: 2.190311
- Problem: keine Trade-Zeitpunkte gespeichert

## Ergebnis Attempt 073

Eine 053-nahe Rekonstruktion wurde mit echter Trade-Level-Ausgabe erstellt. Diese Rekonstruktion ist aber nicht identisch mit dem originalen 053-Entry-Satz und ist deshalb nicht takeover-faehig.

Trade-Level-Rekonstruktion:
- Blind: -1.130052 USDC pro Tag
- Train: -0.847352 USDC pro Tag
- Blind Trades: 1846
- Train Trades: 2962
- Blind PF: 0.319188
- Train PF: 0.333799

Das ist kein Beweis gegen 053. Es ist der Beweis, dass der originale 053-Lauf zwingend mit Trade-Level-Capture wiederholt werden muss.

## Dateien lokal erzeugt

- trade_level_entries.csv
- trade_level_mfe_mae.csv
- entry_context_snapshots.csv
- exit_surface_with_capture.csv
- attempt073_reconstruction_candidates.csv
- codex_instruction_attempt073.md

## Entscheidung

Attempt 053 bleibt Kandidaten-Champion, ist aber noch nicht takeover-reif.

Attempt 073 beweist den technischen Datenpfad: Ab jetzt muss der Optimizer jeden Top-Kandidaten mit Trade-Level-Capture speichern. Erst danach kann man Partial-TP, Trail, MFE-Lock und echte Live-Umsetzbarkeit sauber pruefen.

## Codex-Kernaussage

Codex soll nicht versuchen, aus den alten 053-CSV-Dateien MFE/MAE zu erraten.

Codex muss den Replay/Optimizer so umbauen, dass der echte 053-Familienlauf mit `capture_trades=True` wiederholt wird und dabei Entry/Exit, MFE/MAE und Context-Snapshots schreibt.
