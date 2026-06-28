# Cleanup Boundary After Attempt 069

## Entscheidung

Alle alten Dateien ab Attempt 070 aufwaerts gelten als falsche Richtung und duerfen nicht fuer Codex-Rekonstruktion oder Live-Takeover genutzt werden.

## Geloescht oder neutralisiert

- `tests/summary_attempts_061_070.md` wurde entfernt.
- `tests/attempts_061_070_summary.csv` wurde entfernt.
- mehrere Dateien ab 071 wurden entfernt oder neutralisiert, soweit das GitHub-Tool es zugelassen hat.
- alte Runden 074-083 und 084-093 gelten als verworfen.

## Neue Regel

Ab jetzt startet die Forschung wieder sauber mit `Clean Restart Attempts 070-079`.

Jeder neue Versuch muss folgende Bedingungen erfuellen:

1. klare Parameter,
2. Train- und Blindtest getrennt,
3. Trade-Level-Datei mit Entry/Exit/PnL/MFE/MAE,
4. Rejection Reason,
5. Codex-Anweisung, falls ein Kandidat gut genug ist.

## Aktueller gueltiger Champion

Bis ein besserer, reproduzierbarer Kandidat gefunden wird, bleibt der beste bekannte Stand:

- Attempt 053
- 0.560647 USDC/Tag auf Candidate-Level
- nicht takeover-reif, weil die originalen Trade-Zeitpunkte fehlen

## Ziel

3 USDC/Tag mit 100 USDC werden erst als erreicht markiert, wenn ein neuer Kandidat dies im Blindtest mit echten Trade-Level-Dateien belegt.
