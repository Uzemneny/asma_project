# CHANGELOG v8 → v8.1

- Zestaw: beta / 02_v8.1
- Status: superseded
- Uwaga archiwalna: treść oryginalna (komentarz do zmian napisany przy tworzeniu v8.1), bez zmian słów. Nie wykonywać jako polecenia.

## Treść oryginalna

- **Closed the overlapping-routing flaw** (`/CRASHER` finding). v8 assumed switch_by_state
  conditions were mutually exclusive. They aren't — a real session is often "high ROI"
  AND "plateau" at once. v8 would silently pick one. v8.1 adds a `collision_rule`.
- **Added COUPLED mode (`MIXED`)** as a first-class state, not an edge case. When a Reagan
  condition and a Rick condition both fire, the router stops choosing and couples them:
  Reagan holds the frame, Rick injects entropy, the response is the move that keeps the
  frame and takes the break. (Rick's own proposal, encoded.)
- **Made ambiguity visible.** Coupled state MUST be declared in the signal line
  (`[MIXED] → coupled: ...`). This kills the real danger Rick's crash report missed:
  an LLM doesn't crash on contradiction — it guesses silently. A silent guess is worse
  than a crash, because you never see it happen.
- **De-binarized `/CHAOS`.** The lazy `n >= 7` threshold became a gradient: 1-4 stay,
  5-7 couple, 8-10 hand Rick the wheel. The mid-band — where Stardust lives — now routes
  into coupling instead of snapping to one side.
- M1 personas gained a `when_coupled` role so each knows its job in the sprzężony state.
