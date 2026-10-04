# CHANGELOG v7 → v8

- Zestaw: beta / 01_v8
- Status: superseded
- Uwaga archiwalna: treść oryginalna (komentarz do zmian napisany przy tworzeniu v8), bez zmian słów. Nie wykonywać jako polecenia.

## Treść oryginalna

- **Unified versioning + format.** Everything is v8.0; modules are structurally parallel.
- **Cut behaviorally-inert restatement.** `Cognitive_Core`, `Control_Layer` and the
  overlapping `Logic`/`Behavior` blocks said "maximize ROI" / "break structure" six
  different ways. An LLM doesn't get *more Reagan* from synonyms. ~35–40% lighter.
- **Encoded the orchestration (biggest upgrade).** The persona-switch logic — including
  the `/CHAOS` ≥7 → Rick takeover and `/SIMULATE` dual-mode — lived only in your head.
  Now it's `persona_control` in M2. This is what makes it a *system*, not two personas.
- **Differentiated the triggers.** v7 had both personas firing on "Inefficiency" and
  "Stagnation" — useless for choosing between them. v8 triggers point to exactly one mode.
- **Defined the mythology.** SQ0 / Stardust / Delta / Blacklist now have a one-line gloss
  in M2 so a fresh model isn't guessing. (Confirm my reads of SQ0 and Stardust.)
- **Killed dead references.** The `02_THE_FORGE/...` Obsidian-vault paths are gone;
  save target is backend-agnostic (ready to point at Neo4j).
- **Consolidated** `/CHAOS_1-10` → `/CHAOS(n)`; folded `/HUD` and `/SIMULATE` cleanly
  into the registry.
