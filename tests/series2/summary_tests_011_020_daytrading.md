# Testreihe 2 - Tests 011-020: Bekannte Daytrading-Strategien ETH-only

## Ergebnis kurz
- Bester neuer Kandidat: Test 017 `range_support_bounce_eth`
- Blind USDC/Tag: `-0.014087`
- Train USDC/Tag: `-0.031790`
- Blind PF: `0.530617`
- Rejection: `train_nonpositive;blind_nonpositive;pf_low;below_attempt053;target_ratio_low`

## Datenbasis
- Bars: 315,841 x 5m
- First: 2023-06-24 23:35:00+00:00
- Last: 2026-06-25 15:45:00+00:00
- Split: 2025-06-25 15:48:00+00:00
- Fokus: ETHUSDC Spot long-only, 100 USDC je Trade
- ETH-only Rohdaten: ETHUSDC Candles mit Quote Volume, Trade Count und Taker-Buy-Quote
- Kosten: 0.22 USDC pro 100-USDC-Roundtrip

## Ranking
| Test | Strategie | Train USDC/Tag | Blind USDC/Tag | Blind Trades/Tag | Avg/Trade Blind | PF Blind | Entscheidung |
|---:|---|---:|---:|---:|---:|---:|---|
| 017 | range_support_bounce_eth | -0.031790 | -0.014087 | 0.109590 | -0.128540 | 0.530617 | rejected |
| 012 | rsi_bollinger_reversion_eth | -0.069196 | -0.077884 | 0.304111 | -0.256104 | 0.399535 | rejected |
| 016 | macd_rsi_momentum_scalp_eth | -0.153048 | -0.113394 | 0.638360 | -0.177634 | 0.473152 | rejected |
| 018 | liquidity_sweep_reclaim_eth | -0.123266 | -0.124987 | 0.591784 | -0.211204 | 0.536463 | rejected |
| 015 | session_open_range_breakout_eth | -0.150701 | -0.244221 | 0.865758 | -0.282089 | 0.455642 | rejected |
| 020 | volatility_squeeze_breakout_eth | -0.101688 | -0.250378 | 0.830142 | -0.301609 | 0.335128 | rejected |
| 014 | vwap_bounce_eth | -0.431285 | -0.446462 | 1.975354 | -0.226016 | 0.383365 | rejected |
| 013 | donchian_breakout_eth | -0.284208 | -0.495863 | 1.813709 | -0.273397 | 0.416435 | rejected |
| 011 | ema_trend_pullback_eth | -0.709763 | -0.835028 | 3.704131 | -0.225432 | 0.417516 | rejected |
| 019 | supertrend_atr_continuation_eth | -0.958538 | -1.158328 | 4.983590 | -0.232428 | 0.449266 | rejected |

## Getestete Strategieklassen
- Test 011 `ema_trend_pullback_eth`: EMA trend-following pullback, ETH-only with flow and trend filter.
- Test 012 `rsi_bollinger_reversion_eth`: RSI/Bollinger mean reversion with lower-wick absorption.
- Test 013 `donchian_breakout_eth`: Donchian/range breakout with volume and taker-buy confirmation.
- Test 014 `vwap_bounce_eth`: Intraday VWAP bounce during active hours.
- Test 015 `session_open_range_breakout_eth`: US-overlap opening/range breakout proxy.
- Test 016 `macd_rsi_momentum_scalp_eth`: MACD/RSI momentum scalping, volume-confirmed.
- Test 017 `range_support_bounce_eth`: Range/support bounce with low trend strength.
- Test 018 `liquidity_sweep_reclaim_eth`: Liquidity sweep/fakeout reclaim with large lower wick.
- Test 019 `supertrend_atr_continuation_eth`: ATR trend-continuation proxy after pullback.
- Test 020 `volatility_squeeze_breakout_eth`: Bollinger squeeze breakout with volume/flow expansion.

## Entscheidung
Kein Kandidat erreicht 3 USDC/Tag. Kein Kandidat schlägt Attempt 053 (0.560647 USDC/Tag). Nicht implementieren.

## Ethereum-Anpassung
Ja: Es stimmt teilweise, dass vorher nicht jede Strategie wirklich ETH-only angepasst war. Diese Runde testet bekannte Daytrading-Strategien direkt auf ETHUSDC mit ETH-eigenem Volumen, Taker-Buy-Flow, Wick-Verhalten, Volatilitaet und Session-Struktur.

## Reproduzierbarkeit
Jeder Test hat Kandidaten-CSV und Trade-Level-CSV mit Entry/Exit/PnL/MFE/MAE.