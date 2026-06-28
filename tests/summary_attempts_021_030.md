# Summary Attempts 021-030

Ziel: 3 USDC pro Tag mit 100 USDC Kapitalrahmen auf ETHUSDC Spot.

## Was neu war

Diese Runde bewertet Kandidaten nicht mehr nur nach PnL oder Profit Factor, sondern nach Zielmechanik: Trades/Tag mal Netto pro Trade. Ein Kandidat muss ausweisen, wie viele Trades/Tag er bei seinem Netto pro Trade brauchen wuerde, um 3 USDC/Tag zu erreichen.

## Ergebnisse

| Attempt | Familie | USDC/Tag | Trades/Tag | Netto/Trade | Required Trades/Tag | Activity/Required | PF |
|---:|---|---:|---:|---:|---:|---:|---:|
| 021 | pullback_target | -0.000385 | 0.030055 | -0.012822 | 999999.000 | 0.000% | 0.935567 |
| 022 | active_ethbtc | -0.054076 | 0.297814 | -0.181577 | 999999.000 | 0.000% | 0.436393 |
| 023 | flow_gate_eth | -0.036649 | 0.196721 | -0.186299 | 999999.000 | 0.000% | 0.364380 |
| 024 | target_mix | 0.054969 | 0.136612 | 0.402370 | 7.456 | 1.832% | 1.737322 |
| 025 | range_revert | 0.000212 | 0.002732 | 0.077684 | 38.618 | 0.007% | 9.990000 |
| 026 | volume_pop | 0.003812 | 0.158470 | 0.024055 | 124.713 | 0.127% | 1.088313 |
| 027 | day_bucket | -0.005437 | 0.087432 | -0.062190 | 999999.000 | 0.000% | 0.817035 |
| 028 | target_score | -0.021817 | 0.098361 | -0.221810 | 999999.000 | 0.000% | 0.420406 |
| 029 | target_mix | 0.014951 | 0.131148 | 0.114003 | 26.315 | 0.498% | 1.274361 |
| 030 | volume_pop | 0.055705 | 0.095628 | 0.582518 | 5.150 | 1.857% | 1.962953 |

## Bester USDC/Tag-Kandidat

```json
{
  "attempt": 30,
  "title": "Attempt 030 - Meta-Zielzonen Auswahl 1/2/4/8 Trades pro Tag",
  "family": "volume_pop",
  "blind_usdc_day": 0.055705,
  "gap_to_target": 2.944295,
  "blind_trades": 35,
  "blind_trades_day": 0.095628,
  "blind_avg_pnl_trade": 0.582518,
  "required_trades_day": 5.150057,
  "activity_to_required_ratio": 0.018568,
  "blind_pf": 1.962953,
  "blind_max_dd": 5.660626,
  "blind_worst_month": -1.228662
}
```

## Naechster an der Zielmechanik

```json
{
  "attempt": 30,
  "title": "Attempt 030 - Meta-Zielzonen Auswahl 1/2/4/8 Trades pro Tag",
  "family": "volume_pop",
  "blind_usdc_day": 0.055705,
  "gap_to_target": 2.944295,
  "blind_trades": 35,
  "blind_trades_day": 0.095628,
  "blind_avg_pnl_trade": 0.582518,
  "required_trades_day": 5.150057,
  "activity_to_required_ratio": 0.018568,
  "blind_pf": 1.962953,
  "blind_max_dd": 5.660626,
  "blind_worst_month": -1.228662
}
```

## Kernerkenntnis

Die Zielmechanik bestaetigt die Vermutung: Wir finden entweder seltene, hochwertige Trades oder mehr Aktivitaet mit sinkender Qualitaet. In dieser Runde kommt kein Kandidat auch nur in die Naehe der benoetigten Kombination aus Trades/Tag und Netto/Trade.

## Folgerung

Ab dem naechsten Zyklus sollte nicht noch breiter auf 15m gesucht werden. Falls weiter gesucht wird, dann nur mit der besten Zielmechanik-Familie und 1m-Lokalisierung, oder mit einer neuen Datenklasse.
