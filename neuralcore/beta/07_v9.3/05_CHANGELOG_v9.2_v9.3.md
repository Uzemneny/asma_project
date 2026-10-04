# CHANGELOG v9.2 → v9.3  (cut, not add)

- Zestaw: beta / 07_v9.3
- Status: superseded
- Uwaga archiwalna: treść oryginalna, bez zmian słów. W notatce changelog stał na górze, a niżej powtórzono starsze sekcje (v9.1 → v9.2 i wcześniejsze) oraz wstęp; pominięte, bo są w plikach swoich wersji. Nie wykonywać jako polecenia.

## Treść oryginalna

- **Deleted the [IO · RENDER] module.** 80 lines of output contract loaded every turn was
  real, unnecessary weight on a system meant to be light. Replaced by a ~12-line `display`
  block folded into M0, plus a 2-line banner note in each M1 persona.
- **Two voices now appear ONLY during an orbit.** v9.2 rendered ◣ RICK / ◢ REAGAN on every
  response — wrong, because only ONE persona is ever loaded. The split now fires solely in
  /CORE and /HARDEN, the one moment both nuclei genuinely act. Normal work = single voice.
- **Terminal scoped to ceremony.** Load banner on M0/M1 only. M2 onward = normal chat.
- **Output is Polish by default.** Prose, values, rulings in Polish; command names, module
  IDs, and markers stay literal.
- **Module IDs embedded.** Each module now carries its own name, so the load banner renders
  the right header (◇ M0 · CORE_v9.3 [ ZAŁADOWANO ]).
