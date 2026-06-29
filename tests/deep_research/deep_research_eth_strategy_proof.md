# Deep Research ETH Strategy Proof

## Setup
- Joined rows: 1,579,604
- First: 2023-06-24T17:05:00Z
- Last: 2026-06-25T15:48:00Z
- Split: 2025-06-25T15:48:00Z
- Train days: 731.95
- Blind days: 365.00
- Data used in this fast proof: ETHUSDC 1m + BTCUSDC 1m + ETHBTC 1m + ETHUSDC taker-buy quote flow from Binance candle fields
- Stake: 100 USDC, Spot long-only
- Costs: 0.22 USDC per roundtrip

## Ergebnis
- Best test: DR08 `DR08_sweep_reclaim`
- Train USDC/day: `-0.014622`
- Blind USDC/day: `-0.010789`
- Blind PF: `0.194169`
- Blind trades/day: `0.060274`
- Blind avg/trade: `-0.178998`
- Decision: `train_nonpositive;blind_nonpositive;below_attempt053;below_3_usdc_day;pf_low`

## Ranking

| Test | Name | Train USDC/day | Blind USDC/day | Blind trades/day | Avg/trade | PF | Decision |
|---:|---|---:|---:|---:|---:|---:|---|
| 08 | DR08_sweep_reclaim | -0.014622 | -0.010789 | 0.060274 | -0.178998 | 0.194169 | train_nonpositive;blind_nonpositive;below_attempt053;below_3_usdc_day;pf_low |
| 05 | DR05_flow_strict | -0.106565 | -0.169302 | 0.758904 | -0.223087 | 0.111358 | train_nonpositive;blind_nonpositive;below_attempt053;below_3_usdc_day;pf_low |
| 09 | DR09_full_tp_cap | -0.185924 | -0.264500 | 1.194521 | -0.221427 | 0.117913 | train_nonpositive;blind_nonpositive;below_attempt053;below_3_usdc_day;pf_low |
| 02 | DR02_core_strict | -0.207479 | -0.285175 | 1.252055 | -0.227766 | 0.101811 | train_nonpositive;blind_nonpositive;below_attempt053;below_3_usdc_day;pf_low |
| 06 | DR06_flow_volbounded | -0.237705 | -0.324323 | 1.465753 | -0.221267 | 0.106931 | train_nonpositive;blind_nonpositive;below_attempt053;below_3_usdc_day;pf_low |
| 04 | DR04_flow_loose | -0.302928 | -0.373572 | 1.717808 | -0.217470 | 0.105593 | train_nonpositive;blind_nonpositive;below_attempt053;below_3_usdc_day;pf_low |
| 10 | DR10_full_loose_secondary | -0.504303 | -0.613401 | 2.797260 | -0.219287 | 0.080795 | train_nonpositive;blind_nonpositive;below_attempt053;below_3_usdc_day;pf_low |
| 01 | DR01_core_reclaim | -0.538010 | -0.636571 | 2.819178 | -0.225800 | 0.105588 | train_nonpositive;blind_nonpositive;below_attempt053;below_3_usdc_day;pf_low |
| 07 | DR07_continuation_flow | -0.743799 | -1.085384 | 4.945205 | -0.219482 | 0.124589 | train_nonpositive;blind_nonpositive;below_attempt053;below_3_usdc_day;pf_low |
| 03 | DR03_loose_secondary | -1.020450 | -1.093268 | 5.063014 | -0.215932 | 0.090895 | train_nonpositive;blind_nonpositive;below_attempt053;below_3_usdc_day;pf_low |

## Exit-Erkenntnis
Aggregiert ueber die 10 Blindtest-Varianten:

- 8,057 Trades
- Summe: -1,772.544401 USDC
- Durchschnitt: -0.220001 USDC/Trade
- Zeit-/Reversal-Exits sind das Hauptproblem: `time_kill_2m`, `leadership_reversal`, `time_kill_4m` verlieren zusammen stark.
- `mfe_lock` ist positiv, aber viel zu klein, um die negativen Fruehexits auszugleichen.

## Schlussfolgerung
Die Deep-Research-These ist fachlich plausibel, aber diese konkrete regelbasierte Umsetzung ist auf den gelieferten Daten nicht bewiesen profitabel.

Kein Test erreicht 3 USDC/Tag und keiner schlaegt Attempt 053 mit 0.560647 USDC/Tag.

Wichtig: Dieser Proof nutzt den in den Binance-Kerzen vorhandenen Taker-Buy-Quote-Flow. Der ZIP enthaelt zusaetzlich separate aggTrade-Dateien; ein Teilgegenlauf mit separaten aggTrade-Dateien zeigte fuer die ersten Varianten praktisch identische Werte, wurde aber wegen Laufzeit nicht vollstaendig fertig. Fuer die Entscheidung reicht dieser Proof: nicht implementieren.

## Codex-Entscheidung
Nicht implementieren.

Naechster sinnvoller Schritt:
1. exakten Attempt 053 Runner mit Trade-Capture rekonstruieren, oder
2. echte historische Orderbuch-/Depth-Daten sammeln und danach Book-Support/Spread-Gates testen.
