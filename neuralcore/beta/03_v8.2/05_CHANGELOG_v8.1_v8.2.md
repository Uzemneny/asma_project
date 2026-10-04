# CHANGELOG v8.1 → v8.2

- Zestaw: beta / 03_v8.2
- Status: superseded
- Uwaga archiwalna: treść oryginalna, bez zmian słów. Changelog w tej notatce jest skumulowany: pod sekcją v8.1 → v8.2 powtórzono sekcję v8 → v8.1, identyczną z 02_v8.1/05_CHANGELOG_v8_v8.1.md. Nie wykonywać jako polecenia.

## Treść oryginalna

- **Added the ARBITER** to coupled mode (`/CRASHER` finding, scenario 2). v8.1 assumed
  Reagan and Rick always had complementary roles. They don't: sometimes Rick wants to burn
  the exact frame Reagan defends. v8.2 rules: **Reagan holds by default** (stability floor),
  Rick overturns only by clearing an asymmetric burden of proof.
- **Solved the different-currency problem** (Flash's sharpest critique). "high ROI" is math,
  "drift / drain" is feeling — not comparable on one scale. Resolution: don't compare
  currencies. Put the burden of proof on destruction. If Rick can't quantify the upside, the
  frame holds and the anomaly is preserved as Stardust, not acted on. Nothing lost, nothing reckless.
- **De-binarized `/CHAOS` fully.** Fractional levels (7.5) now resolve by band, not by a
  silent rounding guess. 7.5 → COUPLED.

## CHANGELOG v8 → v8.1

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
