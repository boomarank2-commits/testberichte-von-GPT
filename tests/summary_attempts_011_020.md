# Summary Attempts 011-020

Ziel: 3 USDC pro Tag mit 100 USDC Kapitalrahmen auf ETHUSDC Spot.

## Zielmechanik

- 3 USDC/Tag bedeuten 1095 USDC pro 365 Tage.
- Bei 100 USDC Einsatz braucht der Bot entweder viele Trades mit kleiner positiver Edge oder wenige Trades mit sehr hohem Netto pro Trade.
- Bei 10 bps Fee pro Seite plus 1 bp Slippage pro Seite muss jeder Trade zuerst ca. 0.22 Prozent Kostenzone ueberwinden.
- Viele bisherige Kandidaten sind schon rechnerisch zu selten: selbst positive Kandidaten brauchen oft 2.5 bis 7+ Trades pro Tag, liefern aber nur 0.01 bis 0.16 Trades pro Tag.

## Ergebnisse

| Attempt | Familie | USDC/Tag | Trades/Tag | Netto/Trade | Required Trades/Tag | PF |
|---:|---|---:|---:|---:|---:|---:|
| 011 | ethbtc_soft | 0.010279 | 0.010929 | 0.940486 | 3.190 | 9.990000 |
| 012 | flow_target | -0.023309 | 0.128415 | -0.181510 | 999999.000 | 0.510157 |
| 013 | ethbtc_score | 0.022614 | 0.021858 | 1.034601 | 2.900 | 6.881082 |
| 014 | swing_strength | 0.087832 | 0.073770 | 1.190617 | 2.520 | 2.540659 |
| 015 | dip_strength | 0.011972 | 0.021858 | 0.547736 | 5.477 | 3.726849 |
| 016 | accel | 0.011369 | 0.019126 | 0.594446 | 5.047 | 12.432048 |
| 017 | context_break | 0.008835 | 0.016393 | 0.538954 | 5.566 | 4.191255 |
| 018 | pullback | 0.010356 | 0.016393 | 0.631695 | 4.749 | 4.819886 |
| 019 | anti_btc_drag | 0.021083 | 0.051913 | 0.406130 | 7.387 | 1.765761 |
| 020 | late_confirm | 0.065408 | 0.155738 | 0.419988 | 7.143 | 1.878720 |

## Bester Attempt 011-020

```json
{
  "attempt": 14,
  "family": "swing_strength",
  "blind_usdc_day": 0.087832,
  "gap_to_target": 2.912168,
  "blind_trades": 27,
  "blind_trades_day": 0.07377,
  "blind_avg_pnl_trade": 1.190617,
  "required_trades_day": 2.519701,
  "blind_pf": 2.540659,
  "blind_max_dd": 6.47515,
  "blind_worst_month": -0.279513
}
```

## Kernerkenntnis

Der Nutzerhinweis war richtig. Die Zielmechanik ist das Kernproblem: 3 USDC/Tag sind nicht nur eine Strategiefrage, sondern eine Kombination aus Trades/Tag und Netto pro Trade.

Die besten Kandidaten bleiben weit weg vom Ziel. Attempt 020 ist in dieser Runde am naechsten, aber nur mit 0.065408 USDC/Tag, 0.155738 Trades/Tag und 0.419988 USDC Netto pro Trade. Bei diesem Netto pro Trade braeuchte er rechnerisch 7.143 Trades/Tag, liefert aber nur 0.156 Trades/Tag.

Wenn wir Aktivitaet hochziehen, sinkt die Qualitaet. Wenn die Qualitaet hoch bleibt, ist die Aktivitaet zu niedrig. Genau diese Balance muss ab Attempt 021 systematisch gesucht werden.

## Nicht mehr blind testen

- positive, aber extrem seltene ETHBTC-Signale als alleinige Strategie
- reine High-Throughput-Flow-Scalps ohne deutlich positives Netto pro Trade
- normale Breakout/Pullback/Trend-Varianten ohne Zielmechanik
- Aktivitaet durch schwache Zusatzsignale erzwingen

## Naechster sinnvoller Schritt

Attempt 021 sollte kein weiterer normaler Einzelstrategie-Test sein, sondern ein systematischer Research-Runner mit Zielmechanik. Ein Kandidat darf nur weiterkommen, wenn er gleichzeitig ausreichend Trades/Tag, positives Netto pro Trade, akzeptablen Drawdown und robuste Blindtest-Monate zeigt.
