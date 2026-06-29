# Codex Instruction - Testreihe 2 Tests 011-020

Nicht implementieren.

Bester Kandidat:
- Test 017 `range_support_bounce_eth`
- Blind USDC/Tag: -0.014087
- Train USDC/Tag: -0.031790
- Blind PF: 0.530617
- Ergebnis: rejected

Kein Kandidat schlägt Attempt 053. Die getesteten bekannten Daytrading-Strategien sind als ETH-only Varianten dokumentiert, aber nicht live-tauglich.

Wichtig für weitere Arbeit: Nicht weiter generische Standardindikator-Strategien testen. Nächste sinnvolle Richtung ist echte ETH-Microstructure, aggTrades/Orderbook oder exakte 053-Rekonstruktion mit Trade-Capture.
