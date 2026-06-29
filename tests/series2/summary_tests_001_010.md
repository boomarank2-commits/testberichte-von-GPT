# Testreihe 2 - Tests 001-010

## Ziel
Neustart aus Rohdaten mit zehn neuen ETH-spezifischen Ideen. Erkenntnisse aus Testreihe 1 wurden nur als Ausschluss-Leitplanken verwendet.

## Datenbasis
- Rows 3m joined: 526,507
- First: 2023-06-24 18:30:00+00:00
- Last: 2026-06-25 15:48:00+00:00
- Split: 2025-06-25 15:48:00+00:00
- Training: vor Split, ca. 2 Jahre
- Blindtest: nach Split, ca. 1 Jahr
- Rohdaten: ETHUSDC, BTCUSDC, ETHBTC, ETHUSDT, USDCUSDT Candles
- Flow: Taker-buy Quote aus Roh-Candles als Orderflow-Proxy
- Stake: 100 USDC
- Kosten: 0.22% Roundtrip

## Ergebnis kurz
- Bester neuer Kandidat: Test 002 `raw_cross_basis_reversion`
- Blind USDC/Tag: -0.002795
- Train USDC/Tag: -0.207588
- Blind PF: 0.000000
- Blind Trades/Tag: 0.002740
- Rejection: train_nonpositive;blind_nonpositive;pf_low;target_ratio_low

## Best per Test

| Test | Name | Train USDC/Tag | Blind USDC/Tag | Blind Trades/Tag | Blind Avg/Trade | PF Blind | Entscheidung |
|---:|---|---:|---:|---:|---:|---:|---|
| 002 | raw_cross_basis_reversion | -0.207588 | -0.002795 | 0.002740 | -1.020000 | 0.000000 | rejected |
| 005 | range_low_sweep_reclaim_3m | -0.157529 | -0.064858 | 0.273973 | -0.236733 | 0.444170 | rejected |
| 001 | raw_price_sweep_absorption | -0.225882 | -0.137688 | 0.561644 | -0.245152 | 0.192658 | rejected |
| 004 | compression_expansion_3m | -0.455163 | -0.397655 | 1.778082 | -0.223642 | 0.216473 | rejected |
| 008 | train_only_phase_cells_3m | -0.324416 | -0.440093 | 1.978082 | -0.222485 | 0.448667 | rejected |
| 009 | eu_us_session_drive_3m | -0.362248 | -0.486388 | 1.983562 | -0.245210 | 0.451799 | rejected |
| 003 | ethbtc_lead_pullback_reclaim_3m | -1.017087 | -1.150424 | 5.060274 | -0.227344 | 0.395599 | rejected |
| 007 | sell_exhaustion_absorption_3m | -0.952241 | -1.459970 | 5.824658 | -0.250653 | 0.364911 | rejected |
| 006 | relative_strength_decouple_3m | -1.316006 | -1.466438 | 6.860274 | -0.213758 | 0.432240 | rejected |
| 010 | raw_consensus_ensemble_3m | -3.476655 | -3.570848 | 15.838356 | -0.225456 | 0.400597 | rejected |

## Was wurde getestet und warum?

- 001 Raw Price Sweep Absorption: neue Price-Action-Idee; Range-Low-Sweep + Reclaim + Taker-Buy-Flow.
- 002 Cross-Basis Reversion: neue Cross-Market-Idee; ETHUSDC gegen synthetisches ETHUSDT/USDCUSDT.
- 003 ETHBTC Lead Pullback Reclaim: 053-Erkenntnis ETHBTC-Führung, aber andere 3m-Reclaim-Logik.
- 004 Compression Expansion: Volatilitäts-Kompression und anschließender Ausbruch.
- 005 Range Low Sweep Reclaim: Liquidity Sweep gegen größere Range.
- 006 Relative Strength Decouple: ETH soll stärker als BTC laufen, BTC darf nicht bremsen.
- 007 Sell Exhaustion Absorption: starker Sellflow, aber Preis hält und recovered.
- 008 Train-only Phase Cells: Marktphasen-Zellen nur aus Training gewählt.
- 009 EU/US Session Drive: Session-Impuls mit ETHBTC-Momentum.
- 010 Raw Consensus Ensemble: mehrere neue Rohbedingungen gleichzeitig.

## Entscheidung
Kein Kandidat schlägt Attempt 053. Nicht implementieren; Erkenntnisse in Testreihe 2.2 verwenden.

## Reproduzierbarkeit
Jeder Test hat Kandidaten-CSV und Trade-Level-CSV mit Entry/Exit/PnL/MFE/MAE. Codex darf nur Kandidaten übernehmen, die Train und Blind positiv sind und Attempt 053 schlagen.
