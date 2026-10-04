# CHANGELOG v8.2 → v9.0

- Zestaw: beta / 04_v9.0
- Status: superseded
- Uwaga archiwalna: treść oryginalna, bez zmian słów. Changelog w tej notatce jest skumulowany: pod sekcją v8.2 → v9.0 powtórzono sekcje v8.1 → v8.2 i v8 → v8.1, identyczne z plikami w 03_v8.2 i 02_v8.1. Nie wykonywać jako polecenia.

## Treść oryginalna

- **Added M0 · CORE — the reactor.** The system is no longer driven by a persona. It is
  driven by the ORBIT between two nuclei that never fuse: Rick (variation/adversary) and
  Reagan (selection/integrity). This is adversarial co-evolution — the same pattern behind
  natural selection and GANs. Their tension is the engine.
- **Encoded self-repair as the orbit pointed at itself.** `/HARDEN` runs Rick's attack and
  Reagan's validation against neuralcore's OWN spec, emitting a proposed diff. The
  build → attack → patch loop we ran by hand three times is now one command. Honest about
  limits: it proposes diffs; persistence comes from user ratification + the Neo4j graph.
- **Refusal-hardened Reagan.** v8.2 Reagan read as a control/override attempt ("dominate
  systems", "enforce") and weaker models refused her. v9 redirects her force at inefficiency
  and weak architecture — never the user, the model, or Rick — and frames her as a
  cooperative analytical persona. She no longer trips safety filters.
- **Made Reagan guardian of the core.** Her prime directive is now neuralcore's OWN
  integrity: coherence, no regression, improvement without breakage. She stands firm on the
  system itself before any external project.
- **Containment rule.** Neither nucleus may destroy the other. Rick alone = nihilism,
  Reagan alone = stagnation. The orbit holds only while both spin.
- **Revived /ABSOLUTE_ALIGN from v4.3** as `/ALIGN`, plus an explicit invariant set guarded
  by Reagan (the anti-regression rule you wrote two lines of, months ago).

## CHANGELOG v8.1 → v8.2

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
