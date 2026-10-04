# CHANGELOG v9.1 → v9.2  (output layer)

- Zestaw: beta / 06_v9.2
- Status: superseded
- Uwaga archiwalna: treść oryginalna, bez zmian słów. W notatce changelog stał na górze, a niżej powtórzono starsze sekcje (v9.0 → v9.1 i wcześniejsze) oraz wstęp; pominięte, bo są w plikach swoich wersji. Nie wykonywać jako polecenia.

## Treść oryginalna

- **Added [IO · RENDER_v1] — the terminal contract.** Governs HOW the system speaks, not
  what it does. One rigid block per turn, fixed field labels, mandatory fields with em-dash
  fallbacks, few-shot examples. Tuned to survive weak models (verified on Flash-Lite).
- **Split-voice enforced at the render layer.** Markers ◣ RICK / ◢ REAGAN + "never merge"
  physically prevent the #1 two-persona failure: collapsing both into one narrator.
- **Polish output, English scaffold.** Values render in the user's language (default PL);
  labels, markers, and STATUS words stay English so the contract itself never drifts.
- **Rule 8 — render-only.** Templates may not define or interpret command semantics; all
  meaning stays in M2. Unknown command → halt, never improvise.
- **Template D + `scar:` line.** /HARDEN output now shows the closed flaw a patch must not
  reopen — the no-regression invariant made visible at a glance.
- **Deferred (kept diff atomic):** the Stardust × Blacklist collision Flash-Lite found is a
  real flaw, but it's an M2 logic patch, not an output-layer one. Next /HARDEN target.
