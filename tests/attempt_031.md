# Attempt 031 - 15m Volume-Pop Kontext mit 1m Entry-Lokalisierung

## Status

- Ergebnis: fehlgeschlagen
- Ziel: 3.000000 USDC pro Tag mit 100 USDC Kapitalrahmen
- Bester Blindtest-Wert: 0.046579 USDC/Tag
- Abstand zum Ziel: 2.953421 USDC/Tag

## Startregel

Dieser Versuch nutzt nur das hochgeladene Rohdatenpaket und die dokumentierten Erkenntnisse bis Attempt 030. Keine alte Bot-Version ist Startpunkt.

## Idee

Attempt 030 war die beste Zielmechanik-Spur: 15m `volume_pop`, aber zu wenig Trades. Attempt 031 nutzt 15m-Volume-Pop nur noch als Kontextfenster. Der eigentliche Einstieg wird auf 1m gesucht: Flow, 1m-Breakout, Pullback-Reclaim, Momentum oder Absorption-Reclaim.

## Zielmechanik

- Ziel pro Tag: 3.000000 USDC
- Blindtest Trades/Tag: 0.128415
- Blindtest Netto pro Trade: 0.362724 USDC
- Rechnerisch benoetigte Trades/Tag bei diesem Netto pro Trade: 8.270755
- Aktivitaet zu benoetigter Aktivitaet: 1.5526 %
- Zielerfuellung: 1.5526 %

## Bester Kandidat

```json
{
  "cid": 68,
  "ctx_window_min": 120,
  "ctx_raw_train": 124,
  "ctx_raw_blind": 41,
  "active_minutes_train": 13050,
  "ctx_fthr": 1.9341005428489904,
  "ctx_ai15": 0.3,
  "ctx_av15": 3.0,
  "ctx_eb4": -0.002,
  "ctx_btc4": 0.003,
  "ctx_session": "avoid_dead",
  "entry_ckind": "flow_pos",
  "entry_kimb": 0.0,
  "entry_qvr": 1.0,
  "entry_tvr": 0.8,
  "entry_ret1": -0.0005,
  "entry_ret3": -0.0005,
  "entry_ret5": 0.0,
  "entry_eb5": -0.001,
  "entry_btc5": -0.002,
  "tp": 0.02,
  "sl": 0.012,
  "hold_min": 240,
  "raw_1m_signals_train": 2118,
  "raw_1m_signals_blind": 836
}
```

## Ergebnis Training

- USDC/Tag: -0.064381
- Gesamt-PnL: -47.191476
- Trades/Tag: 0.175989
- Trades: 129
- Netto pro Trade: -0.365825 USDC
- Benoetigte Trades/Tag fuer Ziel: 999999.000000
- Profit Factor: 0.435826
- Max Drawdown: 51.076858
- Worst Month: -9.087939

## Ergebnis Blindtest

- USDC/Tag: 0.046579
- Gesamt-PnL: 17.048021
- Trades/Tag: 0.128415
- Trades: 47
- Netto pro Trade: 0.362724 USDC
- Benoetigte Trades/Tag fuer Ziel: 8.270755
- Winrate: 0.595745
- Profit Factor: 2.065508
- Max Drawdown: 3.628952
- Worst Day: -1.407361
- Worst Month: -1.078770
- Active Share: 9.289617 %

## Bewertung

Attempt 031 erreicht das Ziel nicht. Die 1m-Lokalisierung verbessert die Entry-Idee fachlich, aber sie loest das Kernproblem nicht: Die beste Kombination aus Aktivitaet und Netto pro Trade bleibt weit unter der Zielmechanik von 3 USDC/Tag.

Wichtig: Wenn die 15m-Volume-Pop-Kontexte weich genug werden, steigt die Aktivitaet, aber die Qualitaet bricht. Wenn die Kontexte hart bleiben, gibt es zu wenige Trades.

Zusaetzlich ist der beste Kandidat nicht uebernehmbar, weil Training deutlich negativ war und der positive Blindtest dadurch eher wie ein Glueckstreffer aussieht.

## Nicht erneut in dieser Form testen

- 15m-Volume-Pop plus einfache 1m-Flow-/Breakout-Trigger als Hauptstrategie.
- Mehr Aktivitaet nur durch laengere Kontextfenster erzwingen.
- Kandidaten akzeptieren, wenn Train negativ und Blind nur gluecklich positiv ist.

## Naechster sinnvoller Test

Attempt 032 sollte entweder eine neue Datenklasse nutzen oder explizit eine Multi-Trade-pro-Kontext-Logik pruefen. Ohne mehr unabhaengige Entry-Ereignisse bleibt die Trades/Tag-Mechanik zu weit weg.
