# Summary Attempts 001-010

Stand nach Attempt 010. Ziel bleibt 3 USDC pro Tag mit 100 USDC Kapitalrahmen auf ETHUSDC Spot.

## Attempts 004-010

- Attempt 004: -0.008791 USDC/Tag, Trades 14, PF 0.340083, Best break
- Attempt 005: -0.025176 USDC/Tag, Trades 31, PF 0.370586, Best vwap_proxy
- Attempt 006: -0.036007 USDC/Tag, Trades 70, PF 0.148974, Best break
- Attempt 007: 0.000000 USDC/Tag, Trades 0, PF 0.000000, Best panic
- Attempt 008: 0.013708 USDC/Tag, Trades 7, PF 6.523049, Best ethbtc
- Attempt 009: 0.013708 USDC/Tag, Trades 7, PF 6.523049, Best ethbtc
- Attempt 010: -0.017634 USDC/Tag, Trades 38, PF 0.642457, Best A5+A8

## Wichtigste Erkenntnis

Der erste positive Blindtest nach Fee und Slippage kam in Attempt 008/009 ueber hochselektive ETHBTC-Relative-Staerke. Er ist aber mit 0.013708 USDC/Tag und nur 7 Blindtest-Trades sehr weit vom Ziel 3 USDC/Tag entfernt.

Das ist ein Hinweis, dass ETHBTC-Kontext wertvoll sein kann, aber die Aktivitaet massiv zu niedrig ist.

## Ausschluss bis jetzt

- einfache globale Breakout-/Trend-Regeln
- reine Kline-Orderflow-Schwellen
- sehr kurze 1m-Scalps ohne starke Filter
- reine Uhrzeitfilter als Hauptsignal
- Panic-Dip-Reversal ohne ausreichende Blindtest-Aktivitaet
- Ensemble aus schwachen Einzelsignalen ohne neue Featureklasse

## Naechster sinnvoller Schritt

Attempt 011 sollte nicht einfach Parameter feintunen. Sinnvoller ist, die ETHBTC-Staerke-Familie aus Attempt 008 zu erweitern: mehr Aktivitaet suchen, aber PF und Drawdown kontrollieren.

Dafuer braucht es eine eigene Signalqualitaetsanalyse fuer ETHBTC-Staerke-Events auf 1m/5m/15m.
