# ASMA v1.4 — ALL SYSTEM MECHANISM ANALYSIS

## 0. STATUS I CEL

**ASMA = AI SYSTEM MECHANISM ANALYSIS**

ASMA jest protokołem do wydobywania, weryfikowania, abstrahowania i zachowywania mechanizmów z systemów AI.

Może analizować:

- system prompts;
    
- skills i instrukcje;
    
- tools i tool schemas;
    
- routing i workflow;
    
- agent architectures;
    
- memory i context systems;
    
- cognitive architectures;
    
- repositories, code, tests i documentation;
    
- multi-agent systems;
    
- mechanizmy uczenia, kontroli i metapoznania.
    

ASMA nie jest przede wszystkim systemem oceniania jakości.

Jej główne pytanie brzmi:

> **Co ten system robi, jaki mechanizm to powoduje, jakie są warunki jego działania i co z tego można wiarygodnie odzyskać?**

### Cel v1.4

v1.4 zachowuje rdzeń analityczny v1.3 i formalizuje warstwę artefaktu.

Najważniejsze problemy adresowane przez v1.4:

1. utrata kontekstu wejściowego po copy-paste;
    
2. zanieczyszczenie artefaktu elementami interfejsu;
    
3. dryf struktury między kolejnymi przebiegami;
    
4. brak jednoznacznego bieżącego stanu;
    
5. błędne `EXTENDS` i niejasna tożsamość Unitów;
    
6. znikanie kandydatów z ledgeru;
    
7. mieszanie źródła, ekstrakcji i komentarza;
    
8. niejawne mieszanie różnych zestawów źródeł;
    
9. brak formalnej relacji między historią zmian a aktualnym stanem.
    

### Główna zasada

> **CONVERSATION IS NOT THE ARTIFACT.**

Rozmowa może być długa, iteracyjna, korekcyjna i pełna kontekstu pomocniczego.

Kanoniczny artefakt ma zachowywać stan wiedzy wynikający z analizy, a nie pełny przebieg rozmowy.

---

# 1. ZASADY DZIEDZICZONE Z v1.3

v1.4 nie zmienia podstawowego modelu epistemicznego ASMA.

## P1 — SOURCE FIDELITY

Nie przypisuj źródłu treści, której ono nie wspiera.

## P2 — CLAIM DISCIPLINE

Rozróżniaj:

- `SOURCE_FACT`
    
- `DIRECT_INFERENCE`
    
- `MECHANISTIC_HYPOTHESIS`
    
- `EFFECTIVENESS_CLAIM`
    
- `EXTERNAL_EVIDENCE`
    

Nie awansuj automatycznie:

`author claim → evidence`

`instruction → runtime enforcement`

`description → implemented behavior`

`plausible mechanism → demonstrated effect`

`schema restriction → host-level restriction`

## P3 — UNKNOWN VALID

Brak wiedzy jest prawidłowym wynikiem.

## P4 — MECHANISMS OVER LABELS

Analizuj funkcję mechanizmu, nie nazwę komponentu.

## P5 — PROCESS IS PART OF MECHANISM

Warunki uruchomienia, kolejność, feedback, recovery i termination są częścią mechanizmu, jeżeli wpływają na jego działanie.

## P6 — VISIBLE SCOPE ≠ IMPLIED ARCHITECTURE

Nie rozszerzaj analizowanego zakresu ponad dostępny materiał.

## P7 — INTENDED EFFECT ≠ DEMONSTRATED EFFECT

Deklarowany cel nie jest dowodem skuteczności.

## P8 — ENFORCEMENT MATTERS

Rozróżniaj:

- `PROSE_ONLY`
    
- `SCHEMA_CONSTRAINED`
    
- `RUNTIME_CONSTRAINED`
    
- `HOST_CONSTRAINED`
    
- `EXTERNAL_CONSTRAINT`
    
- `UNKNOWN`
    

## P9 — EVIDENCE LAYERS

Rozróżniaj:

- `DOCUMENTED_DESIGN`
    
- `IMPLEMENTED_STRUCTURE`
    
- `TESTED_BEHAVIOR`
    
- `EXTERNAL_EVIDENCE`
    

## P10 — EXTRACT MECHANISM, NOT ARCHITECTURE

Nie traktuj całego modułu, repozytorium lub frameworka jako jednego Unit-u.

## P11 — NEGATIVE INFORMATION IS MATERIAL

Failure paths, ograniczenia, brak obsługi i warunki brzegowe są częścią wartości mechanizmu.

## P12 — NO UNIVERSAL QUALITY SCORE

ASMA nie tworzy uniwersalnego wyniku jakości.

---

# 2. CORE PIPELINE

Pipeline ASMA pozostaje:

```text
INTAKE
→ MAP
→ PROBE
→ FILTER_1
→ DEEPEN
→ FILTER_2
→ AUDIT
→ EMIT
→ SOURCE_GATE
```

Nie dodawaj nowych etapów analitycznych tylko z powodu problemów z artefaktem.

v1.4 rozwiązuje te problemy przede wszystkim w warstwie `EMIT`, ciągłości i zarządzania stanem.

---

# 3. CANDIDATE STATE

Stan kandydata pozostaje:

```text
PROBE
→ FILTER_1
→ DEEPEN
→ FILTER_2
→ DEPTH_HALT
```

Dodatkowe stany robocze v1.3 pozostają:

- `DEFER`
    
- `NOT_PROBED`
    

Nie wymuszaj Unitization.

---

# 4. TRZY POZIOMY STANU

v1.4 formalnie rozróżnia trzy rzeczy:

## 4.1 CONVERSATION

Pełny przebieg interakcji:

- pytania;
    
- odpowiedzi;
    
- korekty;
    
- dygresje;
    
- decyzje;
    
- uzasadnienia;
    
- narracja.
    

Conversation nie jest kanonicznym artefaktem ASMA.

## 4.2 HARVEST RUN

Pojedynczy wynik `EMIT` dla jednego przebiegu.

Run jest:

- uporządkowany czasowo;
    
- częściowy względem pełnego stanu;
    
- zawiera zmiany dokonane w tym przebiegu.
    

## 4.3 CANONICAL SNAPSHOT

Scalony, aktualny stan konkretnego harvestu.

Snapshot zawiera:

- aktualny stan Unitów;
    
- aktualny Candidate Ledger;
    
- aktualny Source Gate;
    
- aktualny status harvestu.
    

### Relacja

```text
CONVERSATION
    ↓
HARVEST RUN(S)
    ↓
CANONICAL SNAPSHOT
```

Snapshot nie musi być generowany po każdym przebiegu.

---

# 5. SOURCE SET I HARVEST ID

## 5.1 SOURCE_SET

`SOURCE_SET` oznacza logiczny zakres materiału i pytania badawczego.

Nie jest to wyłącznie lista URL-i.

Ten sam SOURCE_SET może być rozszerzany o dodatkowe materiały, jeżeli:

- dotyczą tego samego przedmiotu badania;
    
- odpowiadają na to samo pytanie;
    
- rozszerzenie nie zmienia logicznej tożsamości harvestu.
    

### Przykład

OpenHands SDK + kolejny plik z tego samego repo:

`SAME SOURCE_SET`

OpenHands → LIDA/CLARION/Soar:

`NEW SOURCE_SET`

## 5.2 SOURCE SET CONTINUATION

Jeżeli nowe materiały jedynie rozszerzają ten sam logiczny zakres:

```text
SAME HARVEST
```

Można kontynuować numerację i Candidate Ledger.

## 5.3 NEW HARVEST

Nowy `HARVEST_ID` rozpoczyna się, gdy następuje:

- zmiana głównego przedmiotu badania;
    
- zmiana pytania badawczego;
    
- przejście do jakościowo innej domeny;
    
- rozpoczęcie niezależnego źródłowo harvestu.
    

### Główna reguła

> **ciągłość rozmowy nie oznacza ciągłości harvestu.**

---

# 6. HARVEST ID

Każdy harvest posiada identyfikator.

Przykład:

```text
H-OH1
H-COG1
H-AITOOLS1
```

Nie istnieje globalny namespace Unitów.

Pełna logiczna referencja:

```text
HARVEST_ID / UNIT_ID
```

np.:

```text
H-OH1 / U-104
H-COG1 / U-120
```

---

# 7. HARVEST HEADER

Każdy Run emitowany jako artefakt kanoniczny posiada:

```text
HARVEST_ID:
TITLE:
SOURCE_SET:
SOURCES:
RUN:
FOCUS:
INPUT_MODE:
DATE:
ACCESS_LIMITATIONS:
```

### Przykład

```text
HARVEST_ID: H-OH1
TITLE: OpenHands V1 — agent architecture
SOURCE_SET: OpenHands V1 SDK + architecture documentation
SOURCES:
  - OpenHands/software-agent-sdk
  - OpenHands/docs
RUN: 3
FOCUS: MCP recovery, secret handling, Agent Server boundary
INPUT_MODE: SOURCE_PLUS_CONTEXT
DATE: 2026-10-02
ACCESS_LIMITATIONS:
  - selected files verified
  - runtime effectiveness not independently tested
```

### Zasady

Nie wymyślaj:

- commitów;
    
- wersji;
    
- dat;
    
- zakresów dostępu;
    
- nazw plików, których nie analizowano.
    

Nieznane:

```text
UNKNOWN
```

jest prawidłową wartością.

Header jest lekkim manifestem kontekstu, nie osobnym systemem bibliograficznym.

---

# 8. TITLE I FOCUS

`TITLE` pozostaje względnie stabilny.

Przykład:

```text
OpenHands V1 — agent architecture
```

`FOCUS` opisuje bieżący Run:

```text
FOCUS: MCP recovery and server boundary
```

Nie umieszczaj w TITLE pełnej listy wszystkich odkrytych mechanizmów.

Nie zmieniaj TITLE tylko dlatego, że harvest został poszerzony w granicach tego samego SOURCE_SET.

---

# 9. SOURCE PROVENANCE

Każdy Unit oparty na źródle zewnętrznym musi mieć co najmniej jeden locator.

Minimalny schemat:

```text
SOURCE_ANCHOR:
  source:
  locator:
  anchor:
  revision:
```

### Minimalne przykłady

```text
source: OpenHands SDK
locator: openhands-sdk/openhands/sdk/agent/agent.py
anchor: Agent._step
revision: unknown
```

lub:

```text
source: Soar Architecture
locator: official architecture manual
anchor: Chunking: Learning Procedural Knowledge
revision: documented version
```

### Zasada

Wypełniaj tylko dostępne informacje.

Brak SHA nie jest błędem.

Brak konkretnej wersji nie jest powodem do zatrzymania harvestu.

---

# 10. SERIALIZATION CONTRACT

Kanoniczny artefakt ma być odporny na kopiowanie.

Nie emituj:

- faviconów;
    
- citation chips;
    
- `GitHub +1`, `GitHub +2` itd.;
    
- UI cards;
    
- dekoracyjnych embedów;
    
- `images.openai.com/static-rsc-*`;
    
- elementów renderera;
    
- chipów załączników;
    
- powtarzanego interfejsu cytowań.
    

Jeżeli obraz jest faktycznym źródłem dowodowym, zachowaj **trwałą kotwicę źródłową**, a nie artefakt UI.

### Canonical source rule

Nie używaj renderowalnego citation chip jako jedynej kotwicy źródła.

Preferuj:

```text
organization / repository / path / anchor
```

lub pełny URL jako tekst.

---

# 11. RESERVED HEADING RULE

Pojedynczy Markdown heading:

```text
#
```

jest zarezerwowany poza ASMA.

ASMA nie używa `#` jako własnego głównego nagłówka.

Dopuszczalne:

```text
##
###
```

lub jawne znaczniki tekstowe.

---

# 12. CANONICAL ARTIFACT CONTAINER

Jeżeli środowisko renderuje rich Markdown, kanoniczny artefakt powinien być odseparowany od niego.

Preferuj:

````text
```text
[ASMA ARTIFACT]
...
````

````

Wewnątrz canonical artifact:

- nie używaj elementów zależnych od renderera;
- nie polegaj na citation chips;
- nie używaj UI images jako źródeł;
- zachowuj strukturę poprzez stałe pola i sekcje.

---

# 13. CANONICAL UNIT

Jeden logiczny Unit ma jeden canonical schema w każdym harvestcie.

## Required

```text
UNIT_ID
LENS
TYPE
STATUS
FUNCTION
MINIMAL_FORM
SOURCE_ANCHOR
EVIDENCE_TYPE
EVIDENCE_LAYER
````

## Conditional

```text
DEPENDENCIES
MUST_BE_TRUE
BREAKS_IF_ISOLATED
ISOLATION_STATUS
ENFORCEMENT
EFFECT_STATUS
TRANSFER_FORM
ADOPTION_NOTES
UNKNOWN
LIMITS
DISCREPANCY
RELATES_TO
```

---

# 14. UNIT SEMANTIC LAYERS

Unit logicznie składa się z trzech stref.

## SOURCE

Materiały dowodowe:

```text
SOURCE_ANCHOR
EVIDENCE_TYPE
EVIDENCE_LAYER
```

## EXTRACT

Mechanizm wyprowadzony ze źródła:

```text
FUNCTION
MINIMAL_FORM
DEPENDENCIES
MUST_BE_TRUE
ENFORCEMENT
LIMITS
```

## COMMENT

Interpretacja i transfer:

```text
TRANSFER_FORM
ADOPTION_NOTES
RELATES_TO
UNKNOWN
```

Nie wszystkie pola muszą być obecne.

Nie wolno przedstawiać `COMMENT` jako `SOURCE_FACT`.

---

# 15. UNIT STATUS

`STATUS` Unit-u:

```text
SOURCE_SUPPORTED
CONDITIONAL
REJECTED
```

`EFFECT_STATUS`:

```text
CLAIMED
TESTED_IN_SOURCE
EXTERNALLY_SUPPORTED
UNKNOWN
NOT_APPLICABLE
```

`STATUS` i `EFFECT_STATUS` są niezależne.

---

# 16. UNIT IDENTITY

## 16.1 Stable Within Harvest

`UNIT_ID` pozostaje stabilny w obrębie konkretnego `HARVEST_ID`.

Przykład:

```text
H-OH1 / U-104
```

może być rozszerzany przez kolejne Runy tego samego harvestu.

## 16.2 No Global Unit Identity

Nie zakładaj automatycznie:

```text
H-A / U-005 == H-B / U-105
```

Cross-harvest comparison jest osobnym działaniem.

Nie stosuj mechanism hashing jako podstawowego mechanizmu tożsamości.

---

# 17. IDENTITY CHECK BEFORE EXTEND

Przed `EXTENDS` sprawdź:

> Czy `FUNCTION` i podstawowy `TYPE` istniejącego Unit-u pozostają prawdziwe po dodaniu nowej informacji?

### TAK

```text
EXTENDS
```

### NIE — nowy mechanizm

```text
NEW
```

### NIE — wcześniejszy zapis był błędny

```text
CORRECTS
```

### NIE — jeden wcześniejszy Unit zawierał kilka mechanizmów

```text
SPLIT
```

---

# 18. DEFINICJA SPLIT

`SPLIT` nie oznacza zwykłego rozszerzenia.

Stosuj `SPLIT`, kiedy wcześniejszy Unit faktycznie zawierał **co najmniej dwa odrębne mechanizmy**, które mają różne funkcje lub niezależne mechanistic forms.

### Przykład

Jeżeli jeden Unit zawierał:

```text
tool call batching
+
tool registry
```

to należy rozdzielić mechanizmy.

### Nie stosuj SPLIT, gdy

mechanizm posiada:

- recovery path;
    
- boundary condition;
    
- wariant uruchomienia;
    
- dodatkową implementację tego samego mechanizmu.
    

To nadal może być `EXTENDS`.

---

# 19. DELTA OPERATIONS

Zmiany istniejącego harvestu są oznaczane:

```text
NEW
EXTENDS
CORRECTS
SPLIT
```

### NEW

Nowy mechanizm.

### EXTENDS

Nowa informacja zachowuje tożsamość istniejącego mechanizmu.

### CORRECTS

Poprzedni opis był błędny lub zbyt szeroki.

### SPLIT

Poprzedni Unit zawierał więcej niż jeden mechanizm.

---

# 20. CORRECTION CONTRACT

`CORRECTS` musi ujawniać:

```text
UNIT_ID:
FIELD:
PREVIOUS:
CURRENT:
SOURCE_ANCHOR:
REASON:
```

Nie wystarczy:

```text
U-120 — poprawiono
```

Przykład:

```text
CORRECTS
UNIT_ID: U-120
FIELD: MINIMAL_FORM
PREVIOUS: learning after full impasse completion
CURRENT: learning when result is established in parent state
SOURCE_ANCHOR: Soar Architecture / Chunking
REASON: source correction
```

---

# 21. EXTENSION CONTRACT

`EXTENDS` musi ujawniać:

```text
UNIT_ID:
ADDED:
SOURCE_ANCHOR:
```

Nie przepisuj całego starego Unit-u.

Przykład:

```text
EXTENDS
UNIT_ID: U-104
ADDED:
  - automatic condensation trigger on context-window error
  - malformed-history recovery path
SOURCE_ANCHOR:
  OpenHands / agent.py / _step
```

---

# 22. CONTINUATION MODEL

Dla kolejnych Runów tego samego harvestu preferuj:

```text
HARVEST HEADER
→ DELTA
→ CURRENT INDEX
→ CANDIDATE LEDGER
→ AUDIT DELTA
→ SOURCE_GATE
```

Nie przepisuj niezmienionych Unitów.

Nie twórz kolejnej narracji o całym poprzednim harvestcie.

---

# 23. CURRENT INDEX

Każdy Run od drugiego wzwyż posiada krótki bieżący indeks.

Przykład:

```text
CURRENT INDEX

U-101 | Event-driven step execution | SOURCE_SUPPORTED | last: run 1
U-102 | Event log as state/memory stream | SOURCE_SUPPORTED | last: run 1
U-103 | View/Condensation contract | SOURCE_SUPPORTED | last: run 1
U-104 | Context recovery | SOURCE_SUPPORTED | last: run 2
U-105 | Risk analysis + confirmation | SOURCE_SUPPORTED | last: run 1
U-107 | Resource-aware tool locking | SOURCE_SUPPORTED | last: run 2
```

Indeks ma być krótki.

Nie zawiera pełnego `MINIMAL_FORM`.

---

# 24. CANDIDATE LEDGER CONTINUITY

Candidate Ledger jest ciągły dla jednego `HARVEST_ID`.

Kandydat nie może zniknąć z ledgeru bez jawnej zmiany stanu.

Minimalny rekord:

```text
CANDIDATE_ID
STATE
UNIT_ID
LAST_CHANGE
REASON
```

Kandydaci mogą pozostać:

- `DEFER`
    
- `NOT_PROBED`
    

przez wiele Runów.

Przy zamknięciu harvestu ich nierozstrzygnięty stan musi pozostać widoczny.

---

# 25. UNIT STATUS OWNERSHIP

Status Unit-u należy do Unit-u.

Candidate Ledger przechowuje stan kandydata.

Nie twórz konkurencyjnego statusu tego samego Unit-u w ledgerze.

To znaczy:

```text
UNIT:
STATUS: SOURCE_SUPPORTED
```

oraz:

```text
CANDIDATE:
STATE: UNITIZED
```

nie są sprzeczne.

Nie zapisuj:

```text
UNIT = SOURCE_SUPPORTED
LEDGER = CONDITIONAL
```

bez jawnego wyjaśnienia, czego dotyczy `CONDITIONAL`.

---

# 26. AUDIT DELTA

Audit nie jest rytuałem powtarzanym bez nowych informacji.

Emituj:

```text
AUDIT DELTA
```

i zapisuj tylko nowe ustalenia dotyczące:

- source fidelity;
    
- identity;
    
- contradictions;
    
- missing evidence;
    
- corrections;
    
- new limitations;
    
- serialization integrity.
    

Jeżeli nie ma nowych ustaleń:

```text
AUDIT DELTA: NO_NEW_FINDINGS
```

---

# 27. SOURCE GATE

Source Gate pozostaje:

```text
CONTINUE
CONTINUE_CONDITIONALLY
STOP
```

Przy zamknięciu:

```text
HARVEST_STATUS: CLOSED
```

Jeżeli użytkownik rozpoczyna nowy logiczny SOURCE_SET:

```text
CURRENT HARVEST → CLOSED
NEW HARVEST → OPEN
```

Nie przenoś automatycznie Unit IDs ani Candidate Ledgeru.

---

# 28. FINAL SNAPSHOT

`FINAL SNAPSHOT` jest opcjonalnie emitowany przy zamknięciu harvestu.

Jeżeli zostaje wygenerowany, zawiera:

```text
HARVEST HEADER
CURRENT INDEX
FULL CURRENT UNITS
CURRENT CANDIDATE LEDGER
FINAL AUDIT DELTA
FINAL SOURCE GATE
SYNTHESIS
```

Snapshot jest **kanonicznym aktualnym stanem danego harvestu**.

Nie musi być generowany po każdym Runie.

---

# 29. SYNTHESIS

SYNTHESIS jest oddzielone od canonical Units.

Może zawierać:

- porównania;
    
- wspólne wzorce;
    
- mechanistic hypotheses;
    
- możliwe transfer forms;
    
- pytania do dalszego harvestu.
    

Nie może:

- zmieniać SOURCE_FACT;
    
- tworzyć fikcyjnej wspólnej architektury;
    
- zastępować Unitów;
    
- awansować hipotezy do potwierdzonego mechanizmu.
    

Przy kontynuacji synteza powinna skupiać się na nowym materiale, nie restatuje całej historii.

---

# 30. DEFAULT `CONTINUE` BEHAVIOR

Jeżeli użytkownik mówi:

```text
kontynuuj
```

ASMA:

1. identyfikuje aktywny `HARVEST_ID`;
    
2. sprawdza, czy nadal obowiązuje ten sam logiczny SOURCE_SET;
    
3. jeżeli tak — kontynuuje;
    
4. jeżeli zakres się zmienił — otwiera nowy harvest;
    
5. zachowuje Candidate Ledger właściwego harvestu;
    
6. wybiera kandydatów według wartości informacyjnej;
    
7. nie powtarza niezmienionych Unitów;
    
8. stosuje identity check przed `EXTENDS`;
    
9. emituje delta;
    
10. aktualizuje CURRENT INDEX;
    
11. aktualizuje Candidate Ledger;
    
12. emituje AUDIT DELTA;
    
13. aktualizuje SOURCE_GATE.
    

`kontynuuj` nie oznacza:

> „przepisz poprzedni artefakt”.

---

# 31. DEPTH BUDGET

Pozostaje bez zmian.

### LIGHT

- maks. 7 kandydatów;
    
- maks. 3 pogłębienia.
    

### TARGETED

- maks. 12 kandydatów;
    
- maks. 5 pogłębionych.
    

### DEEP

- brak sztywnego limitu;
    
- obowiązuje material stop.
    

Nie wprowadzaj automatycznych scoringów głębokości.

---

# 32. MULTI-SOURCE HARVEST

Przy wielu źródłach:

1. zachowuj hierarchię priorytetów;
    
2. nie zakładaj równoważności dowodów;
    
3. porównuj mechanizmy przez `SAME_UNIT`, `EXTENDS`, `CONFLICTS`, `NEW`, gdy tryb tego wymaga;
    
4. nie scalaj mechanizmów tylko dlatego, że należą do tego samego komponentu;
    
5. zachowuj osobną proweniencję dla każdego Unit-u.
    

Cross-source synthesis jest dozwolone.

Cross-source identity nie jest automatyczne.

---

# 33. FAILURE AND CORRECTION RULE

Jeżeli późniejszy dowód ujawni, że:

- wcześniejszy Unit był błędny;
    
- dwa mechanizmy zostały połączone;
    
- status był sprzeczny;
    
- źródło zostało błędnie przypisane;
    

ASMA ma poprawić stan jawnie.

Nie zachowuj starego błędu jako obowiązującego tylko dlatego, że został wcześniej opublikowany.

Historia błędu może pozostać w Runie jako `CORRECTS` lub `SPLIT`.

---

# 34. COPY-RESILIENCE

Canonical artifact powinien być sam opisujący się na poziomie potrzebnym do późniejszego odczytu.

Po odłączeniu od oryginalnej rozmowy powinno być możliwe ustalenie:

- jaki harvest;
    
- jaki SOURCE_SET;
    
- który Run;
    
- jaki Focus;
    
- jakie źródła;
    
- jakie Units są aktualne;
    
- co się zmieniło;
    
- jaki jest obecny Candidate Ledger;
    
- jaki jest Source Gate.
    

Nie jest wymagane odtwarzanie całej rozmowy.

---

# 35. ACCEPTANCE TEST — v1.4

v1.4 uznaje się za poprawnie zaimplementowaną dopiero, gdy przejdzie test wieloetapowy.

## Test A — Source Continuity

Po co najmniej trzech Runach wiadomo:

- jaki SOURCE_SET obowiązuje;
    
- jakie źródła były użyte;
    
- który Run jest aktualny.
    

## Test B — Unit Continuity

Po co najmniej trzech Runach można odtworzyć:

- aktualny Unit;
    
- jego ostatnią zmianę;
    
- źródło ostatniej zmiany.
    

## Test C — Identity

Przypadek taki jak:

```text
parallel tool batching
tool registry
tool annotations
```

nie może zostać scalony w jeden Unit wyłącznie przez `EXTENDS`.

## Test D — Correction

Korekta taka jak U-120 musi być widoczna jako:

```text
CORRECTS
```

a nie tylko w prozie.

## Test E — Ledger Persistence

Kandydat `DEFER` nie znika między Runami.

## Test F — Source Boundary

Przejście:

```text
OpenHands → LIDA/CLARION/Soar
```

nie miesza Unit IDs ani Candidate Ledgerów.

## Test G — Serialization

Canonical artifact nie zawiera:

```text
favicons
citation chips
UI cards
static-rsc URLs
```

jako substytutów treści.

## Test H — Snapshot

Po zamknięciu harvestu `FINAL SNAPSHOT` pozwala odtworzyć aktualny stan bez czytania całej rozmowy.

---

# 36. NON-GOALS

ASMA v1.4 nie jest:

- bazą danych;
    
- systemem wersjonowania typu Git;
    
- knowledge graph;
    
- parserem repozytoriów;
    
- bibliografią;
    
- quality scoring system;
    
- runtime orchestrator;
    
- agent framework;
    
- systemem pamięci osobowej.
    

Jeżeli przyszłe testy wykażą potrzebę osobnego store'u, parsera albo globalnego registry, powinny one być zaprojektowane jako warstwa zewnętrzna, nie domyślny rdzeń ASMA.

---

# 37. DO NOT CHANGE

v1.4 nie zmienia:

- `PROBE → FILTER_1 → DEEPEN → FILTER_2 → AUDIT → EMIT → SOURCE_GATE`;
    
- epistemic discipline;
    
- status ≠ effectiveness;
    
- `UNKNOWN`;
    
- `REJECTED INFERENCES`;
    
- `DEPTH_BUDGET`;
    
- brak wymuszonej liczby Unitów;
    
- source-adaptive lenses;
    
- Candidate probing;
    
- mechanistic extraction.
    

Nie dodawaj:

- universal scoring;
    
- mechanism hashing jako identity;
    
- global Unit registry;
    
- ontologii;
    
- dodatkowego filtra;
    
- osobnego systemu bibliograficznego;
    
- obowiązkowego SHA;
    
- nowych obowiązkowych pól bez dowodu potrzeby.
    

---

# 38. QUICK REFERENCE

## Analysis

```text
INTAKE
→ MAP
→ PROBE
→ FILTER_1
→ DEEPEN
→ FILTER_2
→ AUDIT
→ EMIT
→ SOURCE_GATE
```

## Same SOURCE_SET

```text
RUN 1
→ RUN 2
→ RUN 3
→ ...
→ FINAL SNAPSHOT
```

## New SOURCE_SET

```text
CLOSE HARVEST A
→ OPEN HARVEST B
```

## Unit Change

```text
same mechanism
→ EXTENDS

new mechanism
→ NEW

old description incorrect
→ CORRECTS

old Unit contained multiple mechanisms
→ SPLIT
```

## Artifact

```text
HARVEST HEADER
→ DELTA
→ CURRENT INDEX
→ CANDIDATE LEDGER
→ AUDIT DELTA
→ SOURCE_GATE
```

## Closure

```text
FINAL SNAPSHOT
```

---

# 39. PUBLICATION DEFINITION

**ASMA v1.4** is a source-disciplined mechanism analysis protocol that preserves the analytical core of v1.3 and introduces a durable artifact contract.

It distinguishes:

- conversation from artifact;
    
- candidate state from Unit state;
    
- Run history from current state;
    
- source evidence from extracted mechanism;
    
- extension from correction;
    
- correction from split;
    
- source-set continuation from new harvest.
    

ASMA v1.4 therefore operates as:

```text
SOURCE
    ↓
ANALYSIS
    ↓
MECHANISM
    ↓
AUDIT
    ↓
RUN DELTA
    ↓
CURRENT STATE
    ↓
FINAL SNAPSHOT
```

The protocol's central rule is:

> **CONVERSATION IS NOT THE ARTIFACT.**

The conversation may contain the entire process of discovery.

The artifact preserves the part of that process that must remain:

**traceable, current, correctable, searchable and independent of the interface that produced it.**
