# Summary Attempts 032-040

Ziel: 3 USDC pro Tag mit 100 USDC Kapitalrahmen auf ETHUSDC Spot.

Diese Runde nutzt eine schnelle 5m-Research-Ebene aus den Rohdaten. Sie ist kein finaler Live-Takeover, sondern dient dazu, neue Eventklassen schneller zu bewerten.

## Ergebnisse

| Attempt | Familie | Kind | USDC/Tag | Trades/Tag | Netto/Trade | Required Trades/Tag | Activity/Required | PF | Train USDC/Tag |
|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| 032 | multi_context_5m | hard_volctx_break6 | -0.239917 | 1.199454 | -0.200022 | 999999.000000 | 0.0000% | 0.559647 | -0.295927 |
| 033 | sweep_reclaim_5m | sweep_reclaim | 0.001353 | 0.024590 | 0.055008 | 54.537864 | 0.0451% | 1.248374 | -0.012419 |
| 034 | vwap_reversion_5m | vwap48_revert | 0.000739 | 0.035519 | 0.020812 | 144.145603 | 0.0246% | 1.046070 | -0.001958 |
| 035 | momentum_5m | momentum_burst | -0.017087 | 0.297814 | -0.057374 | 999999.000000 | 0.0000% | 0.843060 | -0.026137 |
| 036 | trend_pullback_5m | trend_pullback | -0.483081 | 2.363388 | -0.204402 | 999999.000000 | 0.0000% | 0.354556 | -0.423586 |
| 037 | atr_flow_5m | atr_flow | -1.233530 | 5.224044 | -0.236125 | 999999.000000 | 0.0000% | 0.275193 | -1.304833 |
| 038 | sell_exhaust_5m | sell_exhaust | 0.001495 | 0.013661 | 0.109448 | 27.410183 | 0.0498% | 1.301208 | -0.009278 |
| 039 | learned_hours_5m | mom | -0.139058 | 0.622951 | -0.223225 | 999999.000000 | 0.0000% | 0.291333 | -0.065381 |
| 040 | meta_5m | meta_pull | -0.327697 | 1.669399 | -0.196296 | 999999.000000 | 0.0000% | 0.466012 | -0.235214 |

## Bester Kandidat nach USDC/Tag

```json
{
  "attempt": 38,
  "family": "sell_exhaust_5m",
  "kind": "sell_exhaust",
  "blind_usdc_day": 0.001495,
  "gap_to_target": 2.998505,
  "blind_trades": 5,
  "blind_trades_day": 0.013661,
  "blind_avg_pnl_trade": 0.109448,
  "required_trades_day": 27.410183,
  "activity_to_required_ratio": 0.000498,
  "blind_pf": 1.301208,
  "train_usdc_day": -0.009278,
  "train_pf": 0.111449,
  "train_trades_day": 0.0191,
  "blind_max_dd": 0.908411,
  "blind_worst_month": -0.908411
}
```

## Bester Kandidat nach Zielmechanik

```json
{
  "attempt": 38,
  "family": "sell_exhaust_5m",
  "kind": "sell_exhaust",
  "blind_usdc_day": 0.001495,
  "gap_to_target": 2.998505,
  "blind_trades": 5,
  "blind_trades_day": 0.013661,
  "blind_avg_pnl_trade": 0.109448,
  "required_trades_day": 27.410183,
  "activity_to_required_ratio": 0.000498,
  "blind_pf": 1.301208,
  "train_usdc_day": -0.009278,
  "train_pf": 0.111449,
  "train_trades_day": 0.0191,
  "blind_max_dd": 0.908411,
  "blind_worst_month": -0.908411
}
```

## Kernerkenntnis

Auch die neuen Eventklassen loesen die Zielmechanik nicht. Die beste Richtung dieser Runde kann positive Blindtestwerte liefern, aber der Abstand zum Ziel bleibt extrem gross. Ein Kandidat mit viel Aktivitaet verliert Qualitaet; Kandidaten mit akzeptabler Qualitaet liefern zu wenige Trades.

## Folgerung

Attempt 041 sollte eine strukturelle Oracle-Pruefung machen: Wie viele reale Minuten-/5m-Fenster haben nach Kosten ueberhaupt genug MFE, um 3 USDC/Tag mit 100 USDC theoretisch erreichbar zu machen? Falls schon die Oracle-Naehe fehlt, ist das Ziel mit Spot/100 USDC wahrscheinlich nicht durch reine Long-only Regeln erreichbar.
