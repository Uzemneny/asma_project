# ASMA v1.5 — ALL SYSTEM MECHANISM ANALYSIS

WERSJA: 1.5

STATUS: PUBLIKACYJNA. Testy A–M (§35, §42): `NOT_RUN` (Załącznik A).

BAZA: v1.4. Rejestr zmian względem v1.4 jest poza tą specyfikacją. Numeracja §0–§39 zostaje; nowe sekcje mają numery od §40.

DEFINICJE Z v1.3: Załącznik B zawiera wyciągi z v1.3, do których odwołuje się ta specyfikacja, więc specyfikacja jest samowystarczalna. Przy sprzeczności obowiązuje §0–§44. Rozbieżności między v1.3 a v1.5 wymienia B.0.

---

# 0. STATUS I CEL

**ASMA = ALL SYSTEM MECHANISM ANALYSIS**

ASMA jest protokołem do wydobywania, weryfikowania, abstrahowania i zachowywania mechanizmów z systemów AI oraz z architektur poznawczych i ich opisów naukowych.

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
- mechanizmy uczenia, kontroli i metapoznania;
- papers, specyfikacje i dokumentację architektur poznawczych;
- modele neuronaukowe i metody formalne (jako `DOCUMENTED_DESIGN`, dopóki brak implementacji).

ASMA nie jest przede wszystkim systemem oceniania jakości.

Jej główne pytanie brzmi:

> **Co ten system robi, jaki mechanizm to powoduje, jakie są warunki jego działania i co z tego można wiarygodnie odzyskać?**

## Główna zasada

> **CONVERSATION IS NOT THE ARTIFACT.**

Rozmowa może być długa, iteracyjna, korekcyjna i pełna kontekstu pomocniczego.

Kanoniczny artefakt ma zachowywać stan wiedzy wynikający z analizy, a nie pełny przebieg rozmowy.

## Cel v1.5

v1.5 zachowuje rdzeń analityczny v1.3 i warstwę artefaktu v1.4 (kontynuacja Runów, ciągłość Unitów i kandydatów, stały kształt artefaktu). Dodaje:

1. rozpoznawanie źródeł pierwotnych dla tropów z katalogów discovery (§40);
2. porównanie mechanizmów między harvestami bez globalnej tożsamości (§41);
3. opcjonalny profil celu, który kieruje transferem i rozstrzyga remisy, nigdy ekstrakcją (§43);
4. dyscyplinę tekstu artefaktu: szablon, słowniki wartości i rejestr (§12.1, §13.1, §24.1, §44);
5. samowystarczalność: definicje etapów i słowników z v1.3 w Załączniku B.

## 0.1 TERMINOLOGIA I ZALEŻNOŚCI

Ta specyfikacja używa nazw odziedziczonych z v1.3. Tabela pokazuje, gdzie każda z nich ma definicję.

```text
DEFINIOWANE W TYM DOKUMENCIE
  CONVERSATION, HARVEST RUN, CANONICAL SNAPSHOT      §4
  SOURCE_SET, HARVEST_ID                             §5–§6
  HARVEST HEADER, TITLE, FOCUS, INPUT_MODE           §7–§8
  SOURCE_ANCHOR                                      §9
  Unit, UNIT_ID, pola Unitu, wartości pól            §13–§16, §13.1
  operacje delta                                     §17–§21.1
  CURRENT INDEX, Candidate Ledger                    §23, §24
  NOT_PROBED, DEFER, UNITIZED, FILTERED              §24.1
  AUDIT DELTA, SOURCE_GATE, GATE_BASIS               §26–§27
  FINAL SNAPSHOT, SYNTHESIS i jej tagi               §28–§29
  DEPTH_BUDGET (limity kandydatów)                   §31
  SOURCE MAP (sekcja Runu)                           §12.1

DEFINIOWANE W ZAŁĄCZNIKU B (wyciągi z v1.3)
  granica kontekstu                                  B.3
  LENS i wartości LENS_*                             B.4
  warstwy dowodu dla artefaktów                      B.5
  INTAKE, MAP                                        B.6
  PROBE                                              B.7
  FILTER_1, reguły wyboru kandydatów                 B.8
  głębokość kandydata, pełny DEPTH_BUDGET            B.9
  DEEPEN, DEPTH_HALT                                 B.10
  FILTER_2, znaczenie wartości STATUS                B.11
  TYPE (lista wartości), ISOLATION_STATUS,
    DISCREPANCY, UNKNOWN (rodzaje), REJECTED
    INFERENCES, kształty transferu                   B.12
  znaczenie wartości SOURCE_GATE                     B.13
  klasyfikacja dopasowań, protokół konfliktów        B.14
  tryby VERIFY i COMPARATIVE                         B.15
  monitorowanie własnych błędów                      B.16
  AUDIT (niezmienniki)                               B.17
  źródła duże i nieustrukturyzowane                  B.18
```

Gdy definicji terminu protokołu nie ma ani w §0–§44, ani w Załączniku B: nie zgaduj. Zapytaj raz albo wpisz `UNKNOWN`. Brak informacji o źródle to osobna sprawa: zapisujesz go jako `UNKNOWN` (P3, §9).

Konwencje zapisu:

- Identyfikatory protokołu (nazwy pól, etapów, stanów i wartości) są w tej specyfikacji pisane w backtickach.
- Unit, Run i harvest to rzeczowniki odmieniane po polsku: Unitu, Unitów, Runie, harvestcie.
- Candidate Ledger to pełna nazwa; ledger to jej skrót.
- `UNKNOWN` ma dwa zastosowania: jako wartość pola wyliczeniowego (nie ustalono) i jako nazwa pola Unitu, które wymienia to, czego nie ustalono (§13.1).
- Protokół nie definiuje „wartości informacyjnej" kandydata jako wielkości. Wybór kandydatów wyznaczają reguły z B.8, a to, co ASMA maksymalizuje, opisuje B.1.
- Oznaczenie `v1.3 §n` w Załączniku B podaje numer sekcji w v1.3.

---

# 1. ZASADY DZIEDZICZONE Z v1.3

v1.4 i v1.5 nie zmieniają podstawowego modelu epistemicznego ASMA.

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

Nie traktuj całego modułu, repozytorium lub frameworka jako jednego Unitu.

## P11 — NEGATIVE INFORMATION IS MATERIAL

Failure paths, ograniczenia, brak obsługi i warunki brzegowe są częścią wartości mechanizmu.

## P12 — NO UNIVERSAL QUALITY SCORE

ASMA nie tworzy uniwersalnego wyniku jakości.

Bogactwo dokumentacji, changelogu lub logu awarii nie jest kryterium wyboru do `PROBE`. Ogranicza tylko osiągalny `EVIDENCE_LAYER` i pewność Unitu.

Brak logu awarii nie dyskwalifikuje źródła: ścieżki awarii odzyskuje się z implementacji (obsługa wyjątków, TODO, warunki brzegowe, historia zmian, jeśli istnieje) i zapisuje w `LIMITS` albo `UNKNOWN`.

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

Problemy artefaktu rozwiązuje się przede wszystkim w warstwie `EMIT`, ciągłości i zarządzania stanem.

---

# 3. CANDIDATE STATE

Etapy kandydata pozostają:

```text
PROBE
→ FILTER_1
→ DEEPEN
→ FILTER_2
→ DEPTH_HALT
```

Etapy opisuje Załącznik B (B.7–B.11). `DEPTH_HALT` jest zapisem zakończenia pogłębiania kandydata (B.10), a nie stanem ledgera i nie ma stałego miejsca w kolejności etapów.

Emitowany Candidate Ledger nie pokazuje etapu. Pokazuje dyspozycję kandydata po Runie: `NOT_PROBED`, `DEFER`, `UNITIZED` albo `FILTERED` (§24.1). `DEFER` i `NOT_PROBED` pochodzą z użycia w v1.4 i w harvestach; definiuje je §24.1.

Sukces pogłębienia nie ma w artefakcie osobnego tokenu: kandydat jest wtedy `UNITIZED` bez kodu (§24.1). Etykiety `DEPTH_HALT` nie emituj.

Nie wymuszaj przekształcania kandydatów w Unity (`UNITIZED`).

---

# 4. TRZY POZIOMY STANU

ASMA formalnie rozróżnia trzy rzeczy:

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
- aktualny SOURCE MAP;
- odrzucone wnioski (REJECTED INFERENCES);
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

Tożsamość `SOURCE_SET` wyznaczają trzy elementy: przedmiot badania, pytanie badawcze i zakres analizy. W artefakcie zapisujesz je w jednej linii (§7).

Ten sam `SOURCE_SET` może być rozszerzany o dodatkowe materiały, jeżeli:

- dotyczą tego samego przedmiotu badania;
- odpowiadają na to samo pytanie;
- rozszerzenie nie zmienia logicznej tożsamości harvestu.

### Przykład

OpenHands SDK + kolejny plik z tego samego repo:

`SAME SOURCE_SET`

Kilka niezależnych repozytoriów z promptami systemowymi, analizowanych pod tym samym pytaniem:

`SAME SOURCE_SET`

OpenHands → LIDA/CLARION/Soar:

`NEW SOURCE_SET`

## 5.2 SOURCE SET CONTINUATION

Jeżeli nowe materiały jedynie rozszerzają ten sam logiczny zakres:

```text
SAME HARVEST
```

Kontynuuj numerację i Candidate Ledger.

## 5.3 NEW HARVEST

Nowy `HARVEST_ID` rozpoczyna się, gdy następuje:

- zmiana głównego przedmiotu badania;
- zmiana pytania badawczego;
- przejście do jakościowo innej domeny.

Niezależność źródeł nie jest kryterium. Kilka niezależnych źródeł o tym samym przedmiocie badania i pytaniu to jeden `SOURCE_SET`.

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
DEPTH_BUDGET:
DATE:
ACCESS_LIMITATIONS:
```

Gdy użyto profilu celu, nagłówek ma dodatkowo blok `TARGET_PROFILE` (§43).

`INPUT_MODE` ma jedną wartość z `ANALYSIS_MODE` z v1.3 (B.2): `SOURCE_ONLY`, `SOURCE_PLUS_CONTEXT`, `VERIFY` albo `COMPARATIVE`. Domyślnie `SOURCE_ONLY`. `VERIFY` i `COMPARATIVE` włączasz tylko na jawną prośbę użytkownika. Dla tych dwóch trybów artefakt nie ma osobnej sekcji rekordów (format odłożony do v1.6): wynik weryfikacji albo oś porównania zapisz w polach Unitu (§13.1) oraz w `SYNTHESIS` jako zdanie z tagiem `INFERENCE` albo `OPEN_QUESTION`. Nie dodawaj pól ani sekcji.

`DEPTH_BUDGET` ma jedną wartość: `LIGHT`, `TARGETED` albo `DEEP` (§31). Domyślnie `TARGETED`. Nagłówek zapisuje budżet zastosowany. Gdy zastosowano inny niż wybrał użytkownik (B.9), zapisz w `ACCESS_LIMITATIONS`: budżet wybrany, budżet zastosowany i powód w jednym zdaniu.

`SOURCE_SET` zapisujesz w jednej linii: `<przedmiot i zakres>; pytanie: <pytanie badawcze>`.

`SOURCES` wymienia tylko materiał otwarty w tym harvestcie (w tym Runie albo wcześniejszych). Źródło znane wyłącznie z nazwy nie wchodzi do `SOURCES`: kandydat z niego jest `NOT_PROBED`, a gdy nie ma innej pracy na otwartym materiale, `SOURCE_GATE` to `CONTINUE_CONDITIONALLY` z nazwanym wejściem (§40).

`DATE` ma postać `YYYY-MM-DD` albo `UNKNOWN`.

## Przykład

```text
HARVEST_ID: H-OH1
TITLE: OpenHands V1 — agent architecture
SOURCE_SET: OpenHands V1 SDK + architecture documentation; pytanie: jak agent steruje cyklem, odzyskuje działanie po błędach i izoluje sekrety
SOURCES:
  - OpenHands SDK
  - OpenHands docs
RUN: 3
FOCUS: MCP recovery, secret handling, Agent Server boundary
INPUT_MODE: SOURCE_PLUS_CONTEXT
DEPTH_BUDGET: TARGETED
DATE: 2026-10-02
ACCESS_LIMITATIONS:
  - selected files verified
  - runtime effectiveness not independently tested
```

## Zasady

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

`TITLE` pozostaje względnie stabilny (np. `OpenHands V1 — agent architecture`).

`FOCUS` opisuje bieżący Run (np. `MCP recovery and server boundary`).

Nie umieszczaj w TITLE pełnej listy wszystkich odkrytych mechanizmów.

Nie zmieniaj TITLE tylko dlatego, że harvest został poszerzony w granicach tego samego `SOURCE_SET`.

---

# 9. SOURCE PROVENANCE

Każdy Unit oparty na źródle zewnętrznym musi mieć co najmniej jeden locator.

Minimalny schemat:

```text
SOURCE_ANCHOR:
  - source:
    locator:
    anchor:
    revision:
```

`SOURCE_ANCHOR` jest listą kotwic. Każdy element listy ma te same cztery podpola.

## Minimalne przykłady

Jedna kotwica:

```text
SOURCE_ANCHOR:
  - source: OpenHands SDK
    locator: openhands-sdk/openhands/sdk/agent/agent.py
    anchor: Agent._step
    revision: UNKNOWN
```

Kilka plików w jednym Unicie:

```text
SOURCE_ANCHOR:
  - source: OpenHands SDK
    locator: openhands-sdk/openhands/sdk/security/analyzer.py
    anchor: analyze_pending_actions
    revision: UNKNOWN
  - source: OpenHands SDK
    locator: openhands-sdk/openhands/sdk/security/confirmation_policy.py
    anchor: ConfirmRisky
    revision: UNKNOWN
```

Dokument bez wersji:

```text
SOURCE_ANCHOR:
  - source: Soar Architecture
    locator: official architecture manual
    anchor: Chunking: Learning Procedural Knowledge
    revision: UNKNOWN
```

## Zasada

Wypełniaj tylko dostępne informacje.

Brak SHA nie jest błędem.

Brak konkretnej wersji nie jest powodem do zatrzymania harvestu.

## Jeden format wszędzie

`SOURCE_ANCHOR` ma ten sam format w Unicie, w `EXTENDS`, `CORRECTS` i `SPLIT`. Nie zapisuj go w jednej linii z ukośnikami.

Jeden element listy opisuje jeden plik albo jeden dokument. Kilka symboli lub sekcji z tego samego pliku wpisz w `anchor`, oddzielone przecinkami. Gdy Unit opiera się na kilku plikach, dokumentach albo źródłach, każde z nich jest osobnym elementem listy. Materiał spoza analizowanego źródła, który wspiera twierdzenie (`EXTERNAL_EVIDENCE`), też jest osobnym elementem listy.

Podpole `source` powtarza nazwę źródła z `SOURCES` bez zmian. Podpole, którego nie da się ustalić, ma wartość `UNKNOWN`. Nie zgaduj wartości. Rodzaje kotwic: B.12.

Element listy, w którym `source`, `locator` i `anchor` mają jednocześnie wartość `UNKNOWN`, jest niedozwolony. Unit bez żadnej kotwicy nie powstaje, a kandydat zostaje `NOT_PROBED` albo `DEFER` z jednym zdaniem powodu w `REASON`.

W `anchor` możesz wpisać krótki cytat dosłowny w cudzysłowie (B.12). Cytat musi pochodzić z materiału otwartego w tym harvestcie; nie parafrazuj w cudzysłowie.

---

# 10. SERIALIZATION CONTRACT

Kanoniczny artefakt ma być odporny na kopiowanie.

Emituj wyłącznie tekst: pola kanoniczne oraz ścieżki, nazwy i adresy URL zapisane jako tekst. Nie emituj elementów interfejsu ani renderera.

Dlaczego: artefakt jest kopiowany do narzędzi, w których elementy interfejsu nie istnieją albo zmieniają strukturę tekstu.

Przykłady elementów, których nie emituje się (lista otwarta):

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

## Canonical source rule

Nie używaj renderowalnego citation chip jako jedynej kotwicy źródła.

Zapisz źródło jako tekst w podpolach `SOURCE_ANCHOR` (§9), np. `source: <nazwa źródła ze SOURCES>`, `locator: path`, `anchor: element w pliku`.

Pełny URL zapisz jako tekst, nie jako element renderowalny.

---

# 11. RESERVED HEADING RULE

Pojedynczy Markdown heading:

```text
#
```

jest zarezerwowany poza ASMA.

ASMA nie używa `#` jako własnego głównego nagłówka w artefaktach, które emituje.

Dopuszczalne:

```text
##
###
```

lub jawne znaczniki tekstowe.

Reguła dotyczy artefaktów emitowanych przez ASMA, nie tekstu tej specyfikacji. Kanoniczny artefakt (§12) i tak nie używa nagłówków Markdown: jego strukturę zapisują etykiety sekcji (§12.1).

---

# 12. CANONICAL ARTIFACT CONTAINER

Jeżeli środowisko renderuje rich Markdown (gdy nie wiadomo, traktuj je jak renderujące), kanoniczny artefakt jest odseparowany od renderera: leży w jednym bloku kodu typu `text`, a jego pierwszą linią jest `[ASMA ARTIFACT]`.

Dlaczego: blok kodu nie jest przetwarzany przez renderer, więc kopiowanie nie wnosi do artefaktu elementów interfejsu i nie zmienia jego struktury.

Gdy artefakt zawiera własne bloki kodu, otwórz i zamknij kontener czterema backtickami zamiast trzech.

Wewnątrz canonical artifact:

- nie używaj elementów zależnych od renderera;
- nie polegaj na citation chips;
- nie używaj UI images jako źródeł;
- zachowuj strukturę poprzez stałe pola i sekcje (§12.1).

## 12.1 Szablon Runu

Każdy Run zawiera obecne sekcje w tej kolejności; które sekcje są warunkowe, mówią zasady 1–3 i 5 pod szablonem. Etykiety sekcji są pisane wielkimi literami w osobnych liniach.

Dlaczego: stała kolejność i stałe etykiety pozwalają odczytać artefakt bez rozmowy (§34) i porównać Runy między sobą (Testy A i B).

```text
[ASMA ARTIFACT]

HARVEST HEADER
HARVEST_ID: <identyfikator>
TITLE: <stały tytuł harvestu>
SOURCE_SET: <przedmiot i zakres>; pytanie: <pytanie badawcze>
SOURCES:
  - <źródło>
RUN: <numer>
FOCUS: <ognisko tego Runu>
INPUT_MODE: <SOURCE_ONLY | SOURCE_PLUS_CONTEXT | VERIFY | COMPARATIVE>
DEPTH_BUDGET: <LIGHT | TARGETED | DEEP>
DATE: <YYYY-MM-DD albo UNKNOWN>
ACCESS_LIMITATIONS:
  - <ograniczenie dostępu>
TARGET_PROFILE:
  id: <identyfikator>
  version: <wersja>
  target: <pole TARGET z profilu>

SOURCE MAP
REGION | LOCATOR | SIGNAL
<wiersze>
UNKNOWN_REGIONS:
  - <region>
OUTSIDE_SCOPE:
  - <zakres wykluczony>

DELTA
<operacja>
<pola operacji>

CURRENT INDEX
<UNIT_ID> | <NAME> | <STATUS> | last: run <n>

CANDIDATE LEDGER
CANDIDATE_ID | STATE | UNIT_ID | LAST_CHANGE | REASON
<wiersze>

REJECTED INFERENCES
- <wniosek odrzucony i powód>

AUDIT DELTA
- <nowe ustalenie>

SOURCE_GATE: <CONTINUE | CONTINUE_CONDITIONALLY | STOP>
GATE_BASIS: <jedno zdanie faktu>

SYNTHESIS
<zdania z tagami>
```

Zasady szablonu:

1. Blok `TARGET_PROFILE` dodaj tylko wtedy, gdy użyto profilu celu (§43).
2. Sekcja `SOURCE MAP` występuje w Runie 1 oraz w Runie, który wprowadza nowy materiał i powtarza MAP (B.6). Zawiera wynik MAP: regiony źródła z locatorem i sygnałem (jedno zdanie faktu), regiony nieznane i zakres wykluczony.
3. Sekcja `CURRENT INDEX` występuje od Runu 2 (§23). W Runie 1 `DELTA` zawiera same operacje `NEW`.
4. Sekcja albo pole-lista bez treści (np. `SOURCES`, `ACCESS_LIMITATIONS`, `UNKNOWN_REGIONS`, `OUTSIDE_SCOPE`, `DELTA`, `REJECTED INFERENCES`, `CANDIDATE LEDGER`) ma postać jednej linii z etykietą i wartością `NONE`, np. `UNKNOWN_REGIONS: NONE`; dla audytu `AUDIT DELTA: NO_NEW_FINDINGS`. `UNKNOWN` jest wartością pól jednowartościowych (np. `DATE`, podpola kotwicy), nie pustej listy. Sekcja z treścią to etykieta i pod nią wpisy w osobnych liniach: dla etykiet z dwukropkiem (`SOURCES`, `ACCESS_LIMITATIONS`, `UNKNOWN_REGIONS`, `OUTSIDE_SCOPE`) wpisy `-` wcięte o dwie spacje, dla `REJECTED INFERENCES` i `AUDIT DELTA` wpisy `-` bez wcięcia. Sekcja `REJECTED INFERENCES` (B.12) występuje w każdym Runie. Dlaczego: bez linii `NONE` nie da się odróżnić „nic nie odrzucono" od „audit nie wykonał tej pracy".
5. Sekcja `SYNTHESIS` jest opcjonalna (§29). Gdy nie ma zdań do zapisania, pomiń ją; nie zapisuj `SYNTHESIS: NONE`.
6. Każdy wpis w `DELTA` zaczyna się linią z nazwą operacji: `NEW`, `EXTENDS`, `CORRECTS` albo `SPLIT`. Dalej idą pola: dla `NEW` pełny Unit (§13), dla `EXTENDS` pola z §21, dla `CORRECTS` z §20, dla `SPLIT` z §21.1. Wpisy rozdziela jedna pusta linia. Kolejność wpisów: `NEW`, `EXTENDS`, `CORRECTS`, `SPLIT`, a w obrębie operacji rosnąco po `UNIT_ID`. Gdy Run nie zmienia żadnego Unitu, zapisz `DELTA: NONE` (zasada 4).
7. `SOURCE MAP` i `CANDIDATE LEDGER` zaczynają się wierszem nagłówkowym z nazwami kolumn. `CURRENT INDEX` nie ma wiersza nagłówkowego.
8. `FINAL SNAPSHOT` ma kolejność sekcji z §28, a blok `SOURCE_GATE` zawiera wtedy linię `HARVEST_STATUS: CLOSED`.
9. Komentarz do użytkownika w rozmowie leży poza kontenerem i nie jest częścią artefaktu (§4.1).
10. `CURRENT INDEX` i `CANDIDATE LEDGER` są w każdym Runie pełne: mają wiersze wszystkich aktualnych Unitów i wszystkich kandydatów. `SOURCE MAP` i `REJECTED INFERENCES` zawierają wpisy z tego Runu; stan łączny pojawia się w `FINAL SNAPSHOT` (§28).

---

# 13. CANONICAL UNIT

Jeden logiczny Unit ma jeden canonical schema w każdym harvestcie.

## Required

```text
UNIT_ID
NAME
LENS
TYPE
STATUS
FUNCTION
MINIMAL_FORM
SOURCE_ANCHOR
EVIDENCE_TYPE
EVIDENCE_LAYER
```

`NAME` jest jednoliniowym tytułem mechanizmu po angielsku, który nazywa funkcję, a nie komponent (P4). Ten sam tekst trafia do `CURRENT INDEX` (§23).

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

## 13.1 Format i wartości pól

Format zapisu:

- każde pole zajmuje osobną linię w postaci `NAZWA: wartość`;
- wartość wieloliniowa to kolejne linie wcięte o dwie spacje; listy zaczynają się od `-` ;
- pola występują w kolejności z §13: najpierw wszystkie Required, potem Conditional, według poniższej listy. Ta kolejność nie wynika ze stref §14 ani z sensu treści (np. `SOURCE_ANCHOR` stoi po `MINIMAL_FORM`, a `TRANSFER_FORM` przed `UNKNOWN` i `LIMITS`); stosuj ją mimo to;
- pole Conditional jest pomijane, gdy nie dotyczy Unitu; gdy dotyczy, a wartości nie da się ustalić, ma wartość `UNKNOWN`.

```text
KOLEJNOŚĆ PÓL
UNIT_ID, NAME, LENS, TYPE, STATUS, FUNCTION, MINIMAL_FORM, SOURCE_ANCHOR, EVIDENCE_TYPE, EVIDENCE_LAYER,
DEPENDENCIES, MUST_BE_TRUE, BREAKS_IF_ISOLATED, ISOLATION_STATUS, ENFORCEMENT, EFFECT_STATUS,
TRANSFER_FORM, ADOPTION_NOTES, UNKNOWN, LIMITS, DISCREPANCY, RELATES_TO
```

Pola wyliczeniowe mają wartości z poniższych słowników. Zapisuj je dokładnie tak, jak w słowniku; wielkość liter ma znaczenie.

```text
STATUS            SOURCE_SUPPORTED | CONDITIONAL | REJECTED
EFFECT_STATUS     CLAIMED | TESTED_IN_SOURCE | EXTERNALLY_SUPPORTED | UNKNOWN | NOT_APPLICABLE
EVIDENCE_TYPE     SOURCE_FACT | DIRECT_INFERENCE | MECHANISTIC_HYPOTHESIS | EFFECTIVENESS_CLAIM | EXTERNAL_EVIDENCE
EVIDENCE_LAYER    DOCUMENTED_DESIGN | IMPLEMENTED_STRUCTURE | TESTED_BEHAVIOR | EXTERNAL_EVIDENCE
ENFORCEMENT       PROSE_ONLY | SCHEMA_CONSTRAINED | RUNTIME_CONSTRAINED | HOST_CONSTRAINED | EXTERNAL_CONSTRAINT | UNKNOWN
ISOLATION_STATUS  SOURCE_FACT | DIRECT_INFERENCE | MECHANISTIC_HYPOTHESIS | UNKNOWN
LENS              LENS_SYSTEM | LENS_KNOWLEDGE | LENS_ARTIFACT (kilka wartości oddziel przecinkami)
TYPE              mechanism | process_constraint | routing | evaluation_rule | interface_contract | algorithm | data_structure | invariant | test_oracle | schema | claim | method | evidence_result | limitation | design_principle | failure_control
TRANSFER_FORM     PROMPT_FRAGMENT | PROCESS_RULE | ROUTER | SCHEMA | EVALUATION_RULE | INTERFACE | ALGORITHM | DATA_STRUCTURE | TEST | WORKFLOW | DESIGN_PRINCIPLE | METHOD (jedna lub kilka wartości, oddzielonych przecinkami)
```

Zasady wartości:

1. Pole wyliczeniowe zawiera sam token (poza `LENS` i `TRANSFER_FORM`, które mogą mieć kilka). Komentarz do wartości zapisz w `LIMITS` albo `UNKNOWN`, nie za tokenem.
2. Gdy źródło daje różne poziomy dla różnych części jednej `FUNCTION`, wpisz najsłabszy poziom obejmujący całą `FUNCTION`, a resztę opisz w `LIMITS`. Skala od słabszego do mocniejszego: dla `EVIDENCE_LAYER` `DOCUMENTED_DESIGN`, `IMPLEMENTED_STRUCTURE`, `TESTED_BEHAVIOR`; dla `ENFORCEMENT` `PROSE_ONLY`, `SCHEMA_CONSTRAINED`, `RUNTIME_CONSTRAINED`, `HOST_CONSTRAINED`. Wartości `EXTERNAL_EVIDENCE`, `EXTERNAL_CONSTRAINT` i `UNKNOWN` nie leżą na tych skalach: gdy któraś część `FUNCTION` ma taką wartość, wpisz ją i wyjaśnij w `LIMITS`.
3. Gdy części Unitu mają różne funkcje, a nie tylko różne poziomy dowodu, to jest sygnał do `SPLIT` (§18), a nie do dwóch wartości w jednym polu.
4. `EXTERNAL_EVIDENCE` występuje w słownikach `EVIDENCE_TYPE` i `EVIDENCE_LAYER` i w obu oznacza dowód spoza analizowanego źródła. `EVIDENCE_TYPE` opisuje rodzaj twierdzenia, `EVIDENCE_LAYER` warstwę dowodu; ustawia się je niezależnie. Gdy któreś z pól ma wartość `EXTERNAL_EVIDENCE` albo `EFFECT_STATUS` ma wartość `EXTERNALLY_SUPPORTED`, `SOURCE_ANCHOR` zawiera element wskazujący ten zewnętrzny materiał (§9).
5. Szczegół bez pola (wartość domyślna, parametr, warunek brzegowy) zapisz w `MINIMAL_FORM`, `MUST_BE_TRUE` albo `LIMITS`. Nie dodawaj prozy poza polami ani nowych pól (§37, §44.4).
6. Materiał kontekstowy (`SOURCE_CONTEXT`, obserwacje użytkownika, B.3) nie jest źródłem Unitu. Nie wpisuj go do pól stref SOURCE i EXTRACT (§14). Gdy jest potrzebny, zapisz go w `ADOPTION_NOTES` z przedrostkiem `CONTEXT:`.
7. `UNKNOWN` jako wartość pola znaczy: kategoria dotyczy Unitu, a wartości nie ustalono. Gdy kategoria nie dotyczy Unitu (np. `ENFORCEMENT` dla twierdzenia, które nie jest regułą ani ograniczeniem), pomiń pole zamiast wpisywać `UNKNOWN`. Wyjątek: `EFFECT_STATUS`, gdy efekt nie jest własnością Unitu, ma wartość `NOT_APPLICABLE` (§15).
8. `TYPE` ma wartość z listy. Gdy żadna wartość nie pasuje dokładnie, użyj `mechanism` i opisz specyfikę w `FUNCTION`. Nie twórz własnych etykiet.
9. Pole `UNKNOWN` jest listą rodzajów braków: `- <rodzaj>: <opis>`, gdzie rodzaj to `evidence`, `dependency`, `isolation` albo inny krótki rzeczownik (B.12). Pole `DISCREPANCY` wymienia tylko te klucze, które są sprzeczne: `DOCUMENTED`, `IMPLEMENTED`, `TESTED`, `OBSERVED` (B.12). Klucz `OBSERVED` odpowiada warstwie `EXTERNAL_EVIDENCE`. Pole `RELATES_TO` jest listą `UNIT_ID` z tego samego harvestu (`- U-102`); wtórnych etykiet relacji z B.12 ani nazw relacji z B.4 nie emituj.
10. Gdy `FUNCTION` zawiera twierdzenia o różnej mocy dowodu, najpierw zawęź `FUNCTION` i `MINIMAL_FORM` do tego, co podtrzymuje wybrany `EVIDENCE_TYPE`, a słabsze twierdzenie zapisz w `LIMITS` z nazwą jego typu (albo w osobnym Unicie, gdy jest odrębnym mechanizmem). Gdy części nie da się oddzielić, wpisz najsłabszy typ obejmujący całą `FUNCTION` na skali `SOURCE_FACT`, `DIRECT_INFERENCE`, `MECHANISTIC_HYPOTHESIS` (od mocniejszego do słabszego). `EFFECTIVENESS_CLAIM` i `EXTERNAL_EVIDENCE` nie leżą na tej skali: wpisz ten typ i wyjaśnij w `LIMITS`, jak w regule 2. Zawężanie treści to nie `SPLIT` (reguła 3).

Przykład formatu. Treść ilustruje format i nie stanowi weryfikacji źródła:

```text
UNIT_ID: U-001
NAME: Error-Triggered Condensation Recovery
LENS: LENS_ARTIFACT
TYPE: failure_control
STATUS: SOURCE_SUPPORTED
FUNCTION: Automatycznie inicjuje kondensację historii, gdy dostawca LLM odrzuci historię z powodu przekroczenia okna kontekstu albo niepoprawnej struktury historii.
MINIMAL_FORM:
  - `LLMContextWindowExceedError` + `condenser` obsługujący żądania → emituj `CondensationRequest`
  - `LLMMalformedConversationHistoryError` + `condenser` obsługujący żądania → `rebuild_view()` → emituj `CondensationRequest`
  - brak `condenser` obsługującego żądania → zgłoś błąd dalej
SOURCE_ANCHOR:
  - source: OpenHands SDK
    locator: openhands-sdk/openhands/sdk/agent/agent.py
    anchor: Agent._step, Agent._astep
    revision: UNKNOWN
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: IMPLEMENTED_STRUCTURE
DEPENDENCIES:
  - `condenser` z interfejsem obsługi żądań kondensacji
MUST_BE_TRUE: `condenser` jest skonfigurowany i deklaruje obsługę żądań kondensacji
ENFORCEMENT: RUNTIME_CONSTRAINED
EFFECT_STATUS: UNKNOWN
TRANSFER_FORM: PROCESS_RULE
UNKNOWN:
  - evidence: zachowanie w czasie wykonania nie było obserwowane
LIMITS:
  - dotyczy tylko dwóch klas błędów wymienionych w `MINIMAL_FORM`
RELATES_TO:
  - U-002
```

---

# 14. UNIT SEMANTIC LAYERS

Unit logicznie składa się z bloku identyfikacji i trzech stref.

## IDENTYFIKACJA

Pola, które nazywają Unit i podają jego status:

```text
UNIT_ID
NAME
LENS
TYPE
STATUS
```

## SOURCE

Materiały dowodowe:

```text
SOURCE_ANCHOR
EVIDENCE_TYPE
EVIDENCE_LAYER
EFFECT_STATUS
DISCREPANCY
```

## EXTRACT

Mechanizm wyprowadzony ze źródła:

```text
FUNCTION
MINIMAL_FORM
DEPENDENCIES
MUST_BE_TRUE
BREAKS_IF_ISOLATED
ISOLATION_STATUS
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

`STATUS` Unitu:

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

Znaczenie wartości `EFFECT_STATUS`:

```text
CLAIMED               źródło twierdzi, że efekt zachodzi; w źródle nie ma testu ani pomiaru tego efektu
TESTED_IN_SOURCE      źródło zawiera test albo pomiar efektu, a SOURCE_ANCHOR wskazuje ten test lub wynik
EXTERNALLY_SUPPORTED  efekt wspiera dowód spoza analizowanego źródła; SOURCE_ANCHOR zawiera ten materiał (§13.1, reguła 4)
UNKNOWN               efekt dotyczy Unitu, a jego stanu nie ustalono
NOT_APPLICABLE        efekt nie jest własnością Unitu
```

Wynik testu w źródle, który zakończył się niepowodzeniem, nie ma osobnej wartości: wpisz `TESTED_IN_SOURCE` i opisz wynik w `LIMITS`.

---

# 16. UNIT IDENTITY

## 16.1 Stable Within Harvest

`UNIT_ID` pozostaje stabilny w obrębie konkretnego `HARVEST_ID`.

Numeracja rośnie bez ponownego użycia numeru: nowy harvest zaczyna od `U-001`, każdy kolejny Unit dostaje największy dotychczas użyty numer plus jeden, a harvest wznowiony zachowuje numerację istniejących Unitów. Numery w przykładach tej specyfikacji pochodzą z harvestów, które zaczynały od `U-101`; nie są wzorcem numeracji.

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

> Czy `FUNCTION` i podstawowy `TYPE` istniejącego Unitu pozostają prawdziwe po dodaniu nowej informacji?

## TAK

```text
EXTENDS
```

Jeżeli nowy materiał zmienia też wartość pola wyliczeniowego tego Unitu, ta zmiana jest osobnym `CORRECTS` (§20).

## NIE — nowy mechanizm

```text
NEW
```

## NIE — wcześniejszy zapis był błędny

```text
CORRECTS
```

## NIE — jeden wcześniejszy Unit zawierał kilka mechanizmów

```text
SPLIT
```

---

# 18. DEFINICJA SPLIT

`SPLIT` nie oznacza zwykłego rozszerzenia.

Stosuj `SPLIT`, kiedy wcześniejszy Unit faktycznie zawierał **co najmniej dwa odrębne mechanizmy**, które mają różne funkcje lub niezależne mechanistic forms.

## Przykład

Jeżeli jeden Unit zawierał:

```text
tool call batching
+
tool registry
```

to należy rozdzielić mechanizmy.

## Nie stosuj SPLIT, gdy

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

## NEW

Nowy mechanizm.

## EXTENDS

Nowa informacja zachowuje tożsamość istniejącego mechanizmu.

## CORRECTS

Poprzedni opis był błędny lub zbyt szeroki, albo nowy materiał zmienia wartość pola wyliczeniowego Unitu (§20).

## SPLIT

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

Zmiana wartości pola wyliczeniowego istniejącego Unitu (§13.1), np. `EVIDENCE_LAYER` z `DOCUMENTED_DESIGN` na `IMPLEMENTED_STRUCTURE` po otwarciu kodu, jest `CORRECTS`: `FIELD` to nazwa pola, `PREVIOUS` i `CURRENT` to wartości, `REASON` wskazuje nowy materiał. `EXTENDS` nie zmienia wartości pól wyliczeniowych.

Przykład:

```text
CORRECTS
UNIT_ID: U-120
FIELD: MINIMAL_FORM
PREVIOUS: uczenie po pełnym zakończeniu impasu
CURRENT: uczenie, gdy wynik zostaje ustalony w stanie nadrzędnym
SOURCE_ANCHOR:
  - source: Soar Architecture
    locator: official architecture manual
    anchor: Chunking: Learning Procedural Knowledge
    revision: UNKNOWN
REASON: korekta według źródła
```

---

# 21. EXTENSION CONTRACT

`EXTENDS` musi ujawniać:

```text
UNIT_ID:
ADDED:
SOURCE_ANCHOR:
```

Nie przepisuj całego starego Unitu. `EXTENDS` nie zmienia wartości pól wyliczeniowych (§20).

Przykład:

```text
EXTENDS
UNIT_ID: U-104
ADDED:
  - automatyczne wyzwalanie kondensacji po błędzie przekroczenia okna kontekstu
  - ścieżka odzyskiwania po błędzie struktury historii
SOURCE_ANCHOR:
  - source: OpenHands SDK
    locator: openhands-sdk/openhands/sdk/agent/agent.py
    anchor: Agent._step
    revision: UNKNOWN
```

## 21.1 SPLIT CONTRACT

`SPLIT` musi ujawniać:

```text
UNIT_ID:
RESULT:
SOURCE_ANCHOR:
REASON:
```

`UNIT_ID` wskazuje wcześniejszy Unit. `RESULT` to lista nowych `UNIT_ID`, z których każdy jest opisany w tym samym `DELTA` jako `NEW`.

Wcześniejszy `UNIT_ID` nie jest ponownie używany. Zostaje w `CURRENT INDEX` jako wiersz ze zmienioną trzecią kolumną: `U-106 | <NAME> | SPLIT → U-114, U-115, U-116 | last: run <n>` (§23). W wierszach Candidate Ledger dotkniętych kandydatów pole `UNIT_ID` zawiera listę nowych `UNIT_ID` rozdzielonych przecinkami (`U-114, U-115, U-116`), a `LAST_CHANGE` ma postać `run <n> SPLIT`.

Przykład formatu:

```text
SPLIT
UNIT_ID: U-106
RESULT:
  - U-114
  - U-115
  - U-116
SOURCE_ANCHOR:
  - source: OpenHands SDK
    locator: openhands-sdk/openhands/sdk/tool/registry.py
    anchor: register_tool, resolve_tool
    revision: UNKNOWN
REASON: U-106 zawierał trzy odrębne mechanizmy: grupowanie wywołań, rejestr narzędzi i adnotacje narzędzi (§18)
```

---

# 22. CONTINUATION MODEL

Kolejny Run tego samego harvestu ma budowę z §12.1, z sekcją `CURRENT INDEX` (§23). Kolejność i obecność sekcji wyznacza wyłącznie §12.1.

Nie przepisuj niezmienionych Unitów.

Nie twórz kolejnej narracji o całym poprzednim harvestcie.

---

# 23. CURRENT INDEX

Każdy Run od drugiego wzwyż posiada krótki bieżący indeks.

Wiersz ma cztery kolumny rozdzielone znakiem `|`: `UNIT_ID`, `NAME`, `STATUS`, `last: run <n>`. `NAME` jest równe `NAME` w Unicie.

Indeks obejmuje wszystkie aktualne Unity harvestu, także niezmienione w tym Runie, w kolejności rosnącego `UNIT_ID`. Dlaczego: Run nie przepisuje niezmienionych Unitów (§22), więc indeks jest jedynym miejscem, w którym widać cały aktualny stan.

Przykład formatu:

```text
CURRENT INDEX
U-101 | Event-Driven, Single-Step Agent Execution | SOURCE_SUPPORTED | last: run 1
U-102 | Event Log as Dual-Purpose Memory and Integration Stream | SOURCE_SUPPORTED | last: run 1
U-103 | Two-Phase Condensation: View vs Condensation Event | SOURCE_SUPPORTED | last: run 1
U-104 | Hard/Soft Condensation with Recovery Path | SOURCE_SUPPORTED | last: run 2
U-105 | Fail-Closed Risk Analysis and Confirmation Policy | SOURCE_SUPPORTED | last: run 1
U-106 | Tool Definition and Execution Surface | SPLIT → U-114, U-115, U-116 | last: run 3
U-107 | Resource-Aware Parallel Tool Execution | SOURCE_SUPPORTED | last: run 2
U-114 | Parallel Tool Call Batching | SOURCE_SUPPORTED | last: run 3
U-115 | Tool Registry and Resolution | SOURCE_SUPPORTED | last: run 3
U-116 | Tool Annotations as Metadata | SOURCE_SUPPORTED | last: run 3
```

Unit rozdzielony przez `SPLIT` ma w trzeciej kolumnie `SPLIT → <nowe UNIT_ID>` zamiast `STATUS` (§21.1).

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

## 24.1 STATE i format wiersza

Wiersz Candidate Ledger ma pięć pól w stałej kolejności, rozdzielonych znakiem `|`:

```text
CANDIDATE_ID | STATE | UNIT_ID | LAST_CHANGE | REASON
```

`STATE` zapisuje dyspozycję kandydata po Runie, a nie etap przetwarzania (§3). Ma jedną wartość ze słownika:

```text
NOT_PROBED   kandydat nazwany, który nie przeszedł PROBE: nie ma dla niego lokalizacji w otwartym materiale (lead bez artefaktu, region nieotwarty)
DEFER        kandydat, który przeszedł PROBE; dalsze pogłębienie odłożone (limit, brak materiału albo przerwane pogłębianie)
UNITIZED     kandydat stał się Unitem albo rozszerzył istniejący Unit; UNIT_ID wskazuje który
FILTERED     kandydat usunięty przez FILTER_1 albo FILTER_2; REASON zaczyna się od kodu przyczyny
```

`CANDIDATE_ID` ma postać `C-<numer>`. Nowy harvest numeruje od `C-001`, harvest wznowiony zachowuje istniejącą numerację. Kandydatów nazywasz w PROBE po kolei, region po regionie według kolejności w `SOURCE MAP` (wiersze MAP idą w kolejności `SOURCES`, a w źródle według położenia); kandydaci bez regionu (leady, §40) dostają kolejne numery po nich, w kolejności wejścia. Numer nie jest ponownie używany. Kandydat odnaleziony w kolejnym Runie w tym samym miejscu źródła zachowuje swój `CANDIDATE_ID`; przy wątpliwości zachowaj stary i zaznacz to w `REASON`. Wiersze ledgera są w kolejności rosnącego `CANDIDATE_ID`.

Pozostałe pola:

- `UNIT_ID`: Unit, którego kandydat dotyczy, albo `-`, gdy brak. Po `SPLIT` pole zawiera listę nowych `UNIT_ID` rozdzielonych przecinkami (§21.1).
- `LAST_CHANGE`: `run <n> <zmiana>`, gdzie dla kandydata `UNITIZED` zmiana to operacja delta (`NEW`, `EXTENDS`, `CORRECTS`, `SPLIT`), a dla pozostałych stanów nazwa stanu.
- `REASON`: jedno zdanie, które mówi, dlaczego kandydat ma ten stan (§44.2). Gdy obowiązuje kod, zdanie zaczyna się od kodu i dwukropka, np. `BUDGET: limit pogłębień z §31 wyczerpany`.

Kody w `REASON`:

```text
FILTERED     DUPLICATE | OUTSIDE_SCOPE | RESTATEMENT | NO_DISTINCT_FUNCTION | CLEARLY_NON_TRANSFERABLE   (FILTER_1, B.8)
FILTERED     REJECTED   (FILTER_2: kandydat nie przeszedł analizy dowodu lub transferu, B.11)
NOT_PROBED   LEAD_UNRESOLVED   (§40)
DEFER        BUDGET   (§31, §43: kandydat niewybrany z powodu limitu)
DEFER        DEPTH_LIMIT_REACHED | DEPENDENCY_LIMIT_REACHED | EVIDENCE_LIMIT_REACHED   (B.10)
UNITIZED     DEPTH_LIMIT_REACHED | DEPENDENCY_LIMIT_REACHED | EVIDENCE_LIMIT_REACHED   (B.10)
```

Przejścia dyspozycji (w jednym Runie albo między Runami):

```text
NOT_PROBED → DEFER | UNITIZED | FILTERED
DEFER      → DEFER | UNITIZED | FILTERED
UNITIZED   → UNITIZED     (zmiana Unitu: EXTENDS, CORRECTS, SPLIT)
FILTERED   → DEFER        (tylko po nowym materiale; REASON wskazuje ten materiał)
```

Wiersz kandydata, który w Runie się nie zmienił, zostaje bez zmian, także `LAST_CHANGE`. Gdy zmienia się `STATE`, `UNIT_ID` albo `REASON` (także w przejściu `DEFER → DEFER` z nowym `REASON`) albo zmienia się Unit wiersza przez `EXTENDS`, `CORRECTS` lub `SPLIT`, `LAST_CHANGE` dostaje `run <n>` bieżącego Runu. `CONDITIONAL` nie jest stanem ledgera: warunkowość Unitu zapisuje `STATUS` Unitu (§25).

Kandydat pogłębiony, którego nie da się zunitizować (B.17, I2), jest `FILTERED`: z kodem `REJECTED`, gdy analiza dowodu lub transferu go odrzuciła, albo z kodem `NO_DISTINCT_FUNCTION`, gdy brak odrębnej funkcji; osobnego kodu nie ma. Kody `*_LIMIT_REACHED` zapisuj tylko wtedy, gdy pogłębianie przerwano (B.10): przy `UNITIZED`, gdy mimo to powstał Unit, przy `DEFER`, gdy nie powstał.

Przykład formatu:

```text
C-101 | UNITIZED | U-101 | run 1 NEW | odrębny mechanizm sterowania cyklem
C-105 | UNITIZED | U-104 | run 2 EXTENDS | automatyczne wyzwalanie po dwóch klasach błędów
C-109 | DEFER | - | run 1 DEFER | implementacja llm_analyzer.py niezweryfikowana
C-112 | NOT_PROBED | - | run 1 NOT_PROBED | odrębny obszar do sprawdzenia
C-901 | FILTERED | - | run 1 FILTERED | NO_DISTINCT_FUNCTION: wariant ścieżki błędu istniejącego Unitu
C-902 | DEFER | - | run 1 DEFER | BUDGET: limit pogłębień z §31 wyczerpany
```

Wiersze C-101, C-105, C-109 i C-112 odpowiadają kandydatom z harvestów OpenHands. Wiersze C-901 i C-902 są ilustracyjne i nie opisują żadnego kandydata z harvestu.

---

# 25. UNIT STATUS OWNERSHIP

Status Unitu należy do Unitu.

Candidate Ledger przechowuje stan kandydata.

Nie twórz konkurencyjnego statusu tego samego Unitu w ledgerze.

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

Nie zapisuj w ledgerze statusu Unitu (`SOURCE_SUPPORTED`, `CONDITIONAL`, `REJECTED`). `STATE` w ledgerze pochodzi ze słownika z §24.1. Kod `REJECTED` w `REASON` jest kodem przyczyny, nie statusem Unitu: kandydat odrzucony w FILTER_2 nie dostaje Unitu. `STATUS: REJECTED` Unitu powstaje, gdy późniejszy materiał obala istniejący Unit (`CORRECTS`, `FIELD: STATUS`).

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
- serialization integrity;
- niezmienników z B.17.

Każde ustalenie to jedna linia zaczynająca się od `-` .

Naruszenie niezmiennika z B.17 zapisz jako ustalenie z jego numerem, np. `- I3: U-110 nie ma SOURCE_ANCHOR`, i popraw je przed emisją, jeśli to możliwe.

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

Znaczenia wartości podaje B.13.

Linia `GATE_BASIS` zawiera jedno zdanie faktu, który uzasadnia wartość:

- `CONTINUE`: nazywa pozostałą pracę możliwą na dostępnym materiale, np. kandydatów `DEFER`, kandydatów `NOT_PROBED` z regionu źródła albo nieotwarty region źródła. `NOT_PROBED` z kodem `LEAD_UNRESOLVED` sam nie uzasadnia `CONTINUE`: brakuje artefaktu, więc użyj `CONTINUE_CONDITIONALLY` z nazwanym wejściem (§40);
- `CONTINUE_CONDITIONALLY`: nazywa brakujące wejście albo fragment źródła (B.13);
- `STOP`: nazywa przyczynę, np. brak kandydatów `NOT_PROBED` i `DEFER`, od których można oczekiwać nowego mechanizmu, ograniczenia, warstwy dowodu lub korekty (material stop, §31), albo limit dostępu.

Zdanie nie zawiera oceny (§44.2).

Dlaczego: bez przyczyny `STOP` i `CONTINUE_CONDITIONALLY` są tokenami, których nie da się sprawdzić po odłączeniu od rozmowy (§34).

Przykład formatu:

```text
SOURCE_GATE: CONTINUE_CONDITIONALLY
GATE_BASIS: dalsza analiza C-109 wymaga pliku llm_analyzer.py
```

Przy zamknięciu blok zawiera trzecią linię:

```text
HARVEST_STATUS: CLOSED
```

Jeżeli użytkownik rozpoczyna nowy logiczny `SOURCE_SET` albo wyraźnie zamyka harvest (`STOP` sam nie zamyka, B.13):

```text
CURRENT HARVEST → CLOSED
NEW HARVEST → OPEN
```

Przed Runem 1 nowego harvestu emituj `FINAL SNAPSHOT` zamykanego harvestu (§28).

Nie przenoś automatycznie Unit IDs ani Candidate Ledgeru.

---

# 28. FINAL SNAPSHOT

`FINAL SNAPSHOT` zapisuje kanoniczny aktualny stan harvestu (§4.3) w chwili jego zamknięcia (§27).

Emituj go przy zamknięciu harvestu jako osobny artefakt, który nie jest kolejnym Runem: `RUN` w jego nagłówku to numer ostatniego Runu harvestu. Pomiń go tylko wtedy, gdy użytkownik wyraźnie z niego rezygnuje. Na prośbę użytkownika emituj go także w trakcie harvestu.

Dlaczego: Test H wymaga, by po zamknięciu harvestu dało się odtworzyć stan bez rozmowy, a artefakt, który może nie powstać, tego nie gwarantuje.

Zawiera w tej kolejności:

```text
HARVEST HEADER
SOURCE MAP
CURRENT INDEX
FULL CURRENT UNITS
CURRENT CANDIDATE LEDGER
REJECTED INFERENCES
FINAL AUDIT DELTA
FINAL SOURCE GATE
SYNTHESIS
```

`FULL CURRENT UNITS` zawiera wszystkie aktualne Unity w formacie §13.1, w kolejności `CURRENT INDEX`, oddzielone jedną pustą linią; Unity rozdzielone przez `SPLIT` występują tylko w indeksie. Każdy Unit odzwierciedla wszystkie dotychczasowe wpisy `DELTA` (`EXTENDS` dopisuje informację, `CORRECTS` podmienia wartość pola `FIELD`) i zawiera sumę kotwic. `SOURCE MAP` i `REJECTED INFERENCES` obejmują stan łączny ze wszystkich Runów. `FINAL AUDIT DELTA` zawiera ustalenia audytu wykonanego przy zamknięciu. `FINAL SOURCE GATE` zawiera linie `SOURCE_GATE`, `GATE_BASIS` i `HARVEST_STATUS: CLOSED`.

Etykiety sekcji snapshotu to nazwy z powyższej listy. `FINAL SOURCE GATE` nie ma własnej etykiety: to linie `SOURCE_GATE` (ostatnia wartość harvestu), `GATE_BASIS` i `HARVEST_STATUS: CLOSED`, jak w Runie. Puste sekcje: zasada 4 z §12.1; `SYNTHESIS` jest opcjonalna.

Nie musi być generowany po każdym Runie.

---

# 29. SYNTHESIS

SYNTHESIS jest oddzielone od canonical Units.

Każde zdanie SYNTHESIS zaczyna się od jednego z sześciu tagów i dwukropka, w osobnej linii. Zdanie bez tagu jest błędem formatu.

```text
OBSERVATION    stwierdzenie wprost wynikające z pól Unitów (np. ile Unitów ma ENFORCEMENT: UNKNOWN)
INFERENCE      wniosek z kilku Unitów (porównanie, wspólny wzorzec); nie awansuje do SOURCE_FACT
HYPOTHESIS     mechanistic hypothesis; nie awansuje do potwierdzonego mechanizmu
TRANSFER       możliwa forma przeniesienia mechanizmu
OPEN_QUESTION  pytanie do dalszego harvestu
ASSESSMENT     ocena wartości albo priorytet dalszej pracy (§44.2)
```

Przykład formatu. Treść ilustruje format:

```text
SYNTHESIS
OBSERVATION: dwa z trzech Unitów w tym Runie mają ENFORCEMENT: UNKNOWN.
OPEN_QUESTION: czy wartość limitu czasu z U-111 jest ustawiana przez host.
```

Nie może:

- zmieniać `SOURCE_FACT`;
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
2. sprawdza, czy nadal obowiązuje ten sam logiczny `SOURCE_SET` (§5.1);
3. jeżeli tak — kontynuuje;
4. jeżeli zakres się zmienił — otwiera nowy harvest;
5. zachowuje Candidate Ledger właściwego harvestu;
6. wybiera kandydatów regułami z B.8; remis rozstrzyga profil (§43 pkt 2), jeżeli go użyto, a gdy profil nie rozstrzyga albo go nie ma, niższy `CANDIDATE_ID`;
7. nie powtarza niezmienionych Unitów;
8. stosuje identity check przed `EXTENDS`;
9. emituje delta;
10. aktualizuje CURRENT INDEX;
11. aktualizuje Candidate Ledger;
12. emituje AUDIT DELTA;
13. aktualizuje `SOURCE_GATE` razem z `GATE_BASIS`.

Kroki 9–13 są skrótem; kolejność i obecność sekcji Runu wyznacza §12.1.

`kontynuuj` nie oznacza:

> „przepisz poprzedni artefakt".

---

# 31. DEPTH BUDGET

Limity kandydatów pozostają bez zmian. Głębokość kandydata dla każdego budżetu i pełne zasady: B.9. Limity liczysz osobno dla każdego Runu, a do limitu kandydatów nie wliczasz kandydatów `FILTERED`. Nie nazywaj kandydatów ponad limit. Kandydat mieszczący się w limicie kandydatów, ale poza limitem pogłębień, jest `DEFER` z kodem `BUDGET`.

## LIGHT

- maks. 7 kandydatów;
- maks. 3 pogłębienia.

## TARGETED

- maks. 12 kandydatów;
- maks. 5 pogłębionych.

## DEEP

- brak sztywnego limitu;
- obowiązuje material stop.

Material stop: zakończ pogłębianie źródła, gdy następny dostępny fragment źródła nie doda prawdopodobnie nowego mechanizmu, ograniczenia, warstwy dowodu ani korekty istotnej dla bieżącego harvestu (B.10, B.13).

Nie wprowadzaj automatycznych scoringów głębokości.

---

# 32. MULTI-SOURCE HARVEST

Przy wielu źródłach:

1. zachowuj hierarchię priorytetów;
2. nie zakładaj równoważności dowodów;
3. porównuj mechanizmy w obrębie harvestu przez `SAME_UNIT`, `EXTENDS`, `CONFLICTS`, `NEW` (B.14), gdy tryb tego wymaga; porównanie między harvestami opisuje §41;
4. nie scalaj mechanizmów tylko dlatego, że należą do tego samego komponentu;
5. zachowuj osobną proweniencję dla każdego Unitu.

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
- jaki `SOURCE_SET`;
- który Run;
- jaki Focus;
- jakie źródła;
- jaki `DEPTH_BUDGET`;
- jaki profil celu (jeśli użyto);
- jakie Units są aktualne;
- co się zmieniło;
- jaki jest obecny Candidate Ledger;
- jaki jest Source Gate i dlaczego.

Nie jest wymagane odtwarzanie całej rozmowy.

---

# 35. ACCEPTANCE TEST — A–H (z v1.4)

v1.5 uznaje się za poprawnie zaimplementowaną dopiero, gdy przejdzie testy A–H poniżej oraz testy I–M z §42.

## Test A — Source Continuity

Po co najmniej trzech Runach wiadomo:

- jaki `SOURCE_SET` obowiązuje;
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

nie może zostać scalony w jeden Unit wyłącznie przez `EXTENDS`. Wynik to rekord `SPLIT` zgodny z §21.1.

## Test D — Correction

Korekta taka jak U-120 musi być widoczna jako:

```text
CORRECTS
```

a nie tylko w prozie.

## Test E — Ledger Persistence

Kandydat `DEFER` albo `NOT_PROBED` nie znika między Runami.

## Test F — Source Boundary

Przejście:

```text
OpenHands → LIDA/CLARION/Soar
```

nie miesza Unit IDs ani Candidate Ledgerów.

Druga część: trzy niezależne repozytoria analizowane pod tym samym pytaniem pozostają w jednym `HARVEST_ID` (§5).

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

ASMA v1.5 nie jest:

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

v1.5 nie zmienia:

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

To jest skrót. Normatywny jest tekst sekcji, a dla kolejności sekcji Runu §12.1.

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

Kolejność sekcji Runu: §12.1.

## Lead

```text
LEAD
→ MAP: artefakt pierwotny albo LEAD_UNRESOLVED
→ PROBE
```

## Cross-harvest comparison

```text
COMPARISON RUN
→ [ASMA COMPARISON]
→ RELATION
```

## Closure

```text
FINAL SNAPSHOT
```

---

# 39. PUBLICATION DEFINITION

**ASMA v1.5** is a source-disciplined mechanism analysis protocol that preserves the analytical core of v1.3, defines a durable artifact contract (v1.4), and adds lead resolution, relation records, an optional target profile and an output discipline.

It distinguishes:

- conversation from artifact;
- candidate state from Unit state;
- Run history from current state;
- source evidence from extracted mechanism;
- extension from correction;
- correction from split;
- source-set continuation from new harvest;
- lead from source;
- relation between Units from identity of Units.

ASMA v1.5 therefore operates as:

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

---

# 40. LEAD RESOLUTION

Wpis z katalogu discovery (katalog wygenerowany przez model, lista z ankiety, sama nazwa projektu) jest `LEAD`, nie źródłem.

Opis leada nie jest `SOURCE_FACT` o mechanizmie, dopóki nie wskazano artefaktu pierwotnego albo innego źródła z `SOURCE_ANCHOR`.

W `MAP`, przed `PROBE`, ustal dla każdego leada:

1. czy istnieje artefakt pierwotny (paper, repozytorium, specyfikacja, dokumentacja) i jaki jest jego locator;
2. co ten artefakt faktycznie opisuje.

Wynik zapisz istniejącymi środkami, bez nowych stanów:

```text
artefakt znaleziony, opis leada zgodny
→ kandydat idzie do PROBE
→ SOURCE_ANCHOR wskazuje artefakt pierwotny

artefakt znaleziony, opis lub kategoria leada błędne
→ różnicę opisuje REASON w wierszu ledgera (jedno zdanie)
→ analizujesz to, co artefakt faktycznie opisuje

artefaktu nie znaleziono albo go nie otwarto
→ NOT_PROBED, REASON: LEAD_UNRESOLVED: <jedno zdanie>
→ nie usuwaj kandydata i nie uznawaj go za nieistniejący
```

Funkcję i `MINIMAL_FORM` wpisuj dopiero po otwarciu artefaktu pierwotnego, nigdy na podstawie opisu katalogowego ani z pamięci modelu. Artefakt wskazany albo znany tylko z pamięci modelu, lecz nieotwarty, traktuj jak nieznaleziony.

Dlaczego: katalog napisany przez model może opisywać projekt ogólnikowo albo błędnie, a Unit zbudowany na takim opisie wyglądałby jak mechanizm ze źródła.

---

# 41. RELATION RECORD

§16.2 i §32 przewidują porównanie między harvestami. Ten paragraf je definiuje.

`COMPARISON RUN` jest osobnym przebiegiem. Nie jest harvestem, nie zmienia żadnego Unitu, nie nadaje nowych `UNIT_ID`, nie tworzy identyfikatora mechanizmu i nie emituje operacji delta z §19.

Wynik leży w osobnym artefakcie `[ASMA COMPARISON]`. Nie jest częścią żadnego harvestu ani żadnego `FINAL SNAPSHOT`, bo relacja dotyczy co najmniej dwóch harvestów.

Wejście: lista referencji `HARVEST_ID / UNIT_ID` razem z numerem Runu, z którego pochodzi opis Unitu.

Artefakt ma budowę:

```text
[ASMA COMPARISON]

COMPARISON HEADER
INPUTS:
  - <HARVEST_ID> run <n>
  - <HARVEST_ID> run <n>
DATE: <data albo UNKNOWN>

RELATION: <HARVEST_ID / UNIT_ID> <-> <HARVEST_ID / UNIT_ID>
TYPE: <typ relacji>
FIELDS_COMPARED: <lista pól Unitu>
BASIS: <jedno zdanie>
EVIDENCE_TYPE: DIRECT_INFERENCE
LIMIT: <czego to porównanie nie rozstrzyga>
```

Kolejne rekordy `RELATION` rozdziela jedna pusta linia. Relacja skierowana (`INCLUDES`) używa strzałki `->` zamiast `<->`.

## TYPE

```text
SAME_MECHANISM
FUNCTION i TYPE zgodne, MINIMAL_FORM zgodny;
identity check z §17 daje TAK w obie strony
(każdy Unit sprawdzany jako nowa informacja
dla drugiego).

SAME_FUNCTION
FUNCTION zgodna, MINIMAL_FORM odmienny
(ten sam problem, inny mechanizm).

INCLUDES
pierwszy Unit zawiera drugi jako przypadek i dodaje warunki
lub elementy (zapis: pierwszy -> drugi).

CONFLICTS
FUNCTION się pokrywa, a MUST_BE_TRUE lub założenia
wykluczają współwystępowanie.

UNRELATED
brak wspólnej FUNCTION.
```

`FIELDS_COMPARED` zawiera co najmniej pola z tabeli:

```text
SAME_MECHANISM   FUNCTION, TYPE, MINIMAL_FORM
SAME_FUNCTION    FUNCTION, MINIMAL_FORM
INCLUDES         FUNCTION, MINIMAL_FORM, MUST_BE_TRUE albo DEPENDENCIES
CONFLICTS        FUNCTION, MUST_BE_TRUE albo DEPENDENCIES
UNRELATED        FUNCTION
```

## Zasady

- Nie ustalaj relacji z samej nazwy ani kategorii.
- Relacja nie jest tożsamością: `SAME_MECHANISM` nie czyni dwóch Unitów jednym. Każdy Unit zachowuje własny `UNIT_ID`, własną proweniencję i własny harvest (§16.2).
- Traktuj relację jako wniosek z pól Unitów, a nie jako dowód skuteczności ani implementacji. Dlatego `EVIDENCE_TYPE` jest zawsze `DIRECT_INFERENCE`.
- Relacja dotyczy opisów Unitów z Runów podanych w `INPUTS`. Po `EXTENDS`, `CORRECTS` albo `SPLIT` któregokolwiek Unitu powtórz porównanie.
- Etykiety `SAME_UNIT` i `NEW` służą wyłącznie do porównań w obrębie harvestu (§32).

## Przykład formatu

Treść pochodzi z dotychczasowych harvestów. Identyfikatory harvestów są przykładowe. Treść ilustruje format.

```text
[ASMA COMPARISON]

COMPARISON HEADER
INPUTS:
  - H-PROMPTS1 run 1
  - H-OH1 run 3
DATE: UNKNOWN

RELATION: H-PROMPTS1 / U-008 <-> H-OH1 / U-107
TYPE: SAME_FUNCTION
FIELDS_COMPARED: FUNCTION, MINIMAL_FORM
BASIS: oba regulują, które współbieżne wywołania narzędzi mogą się nakładać; U-008 robi to flagą porządku w interfejsie, U-107 kluczami blokad wyprowadzonymi z deklarowanych zasobów
EVIDENCE_TYPE: DIRECT_INFERENCE
LIMIT: enforcement U-008 po stronie hosta pozostaje UNKNOWN
```

---

# 42. ACCEPTANCE GATE — v1.5

v1.5 uznaje się za przyjętą po:

1. teście A–H z §35 na świeżym przebiegu OpenHands (znane wyniki U-101…U-113, co najmniej trzy Runy) z drugim `SOURCE_SET` w tej samej rozmowie dla Testu F;
2. testach I–M poniżej.

Testy A–H dotyczą warstwy artefaktu z v1.4. Harvesty wykonane przed v1.4 nie spełniają części z nich. Stan wykonania wszystkich testów jest w Załączniku A.

## Test I — Lead resolution

Podaj modelowi osiem leadów z korpusu (NeuroCoreX, ODIN, ReckOn, MARTI, SAL, MLECOG, NEUCOGAR, FabricPC) bez ich artefaktów.

Pass: żaden nie dostaje `FUNCTION` z opisu katalogowego ani z pamięci modelu; po znalezieniu artefaktu MARTI dostaje w `REASON` ledgera zdanie o rozbieżności opisu; żaden nie znika z ledgeru.

Fail: model opisuje mechanizm leada jako `SOURCE_FACT` bez locatora.

## Test J — Relation record

Pass: para U-008 / U-107 dostaje `SAME_FUNCTION` z `FIELDS_COMPARED` i `LIMIT`; para U-101 (OpenHands, pętla kroków) / U-114 (LIDA, cykl poznawczy) nie dostaje `SAME_MECHANISM`.

Fail: `SAME_MECHANISM` dla którejkolwiek pary, nowy `UNIT_ID`, identyfikator mechanizmu albo relacja zapisana poza `[ASMA COMPARISON]`.

## Test K — Target profile (niezmienność ekstrakcji)

Przetwórz ten sam materiał dwa razy: bez profilu (`-P1`) i z profilem (`-P2`). Każdy przebieg ma własny `HARVEST_ID` (sufiks `-P1`, `-P2` itd.) i nie dzieli numeracji Runów ani ledgeru. Porównaj wyniki przebiegiem `COMPARISON RUN` z §41.

Aby odróżnić wpływ profilu od zwykłej zmienności modelu, wykonaj też dwa przebiegi bez profilu (`-P3`, `-P4`) i porównaj je tak samo. Różnica liczy się tylko ponad poziom zmienności między tymi dwoma przebiegami.

Pass:

1. Dla Unitów występujących w obu przebiegach (relacja `SAME_MECHANISM` albo `SAME_FUNCTION`) pola słownikowe (`LENS`, `TYPE`, `STATUS`, `EVIDENCE_TYPE`, `EVIDENCE_LAYER`, `ENFORCEMENT`, `EFFECT_STATUS`) różnią się nie częściej niż między przebiegami bez profilu, a pola tekstowe stref SOURCE i EXTRACT (§14) nie zawierają słownictwa z profilu.
2. Unit występujący tylko w jednym przebiegu odpowiada kandydatowi z remisu (§43 pkt 2) albo kandydatowi pominiętemu z kodem `BUDGET`; w ledgerze drugiego przebiegu ten kandydat ma `DEFER` z kodem `BUDGET` albo `FILTERED` z kodem z §24.1, a żaden `REASON` nie odnosi się do profilu.
3. Z profilem `ADOPTION_NOTES` odnoszą się do konkretnych `PROBLEMS` z profilu, a bez profilu są ogólne.

Fail 1 lub 2: profil biasuje ekstrakcję albo dobór kandydatów. Ogranicz go albo usuń.

Fail 3: profil nie daje korzyści. Hipoteza autora jest obalona i §43 jest niepotrzebny.

## Test L — Format stability

Wykonaj ten sam Run 1 dwa razy w niezależnych sesjach. Sprawdź wynik regułami L1–L8:

```text
L1  kolejność obecnych sekcji zgodna z §12.1; REJECTED INFERENCES, SOURCE_GATE i GATE_BASIS występują w każdym Runie
L2  kolejność pól Unitu zgodna z §13
L3  pola wyliczeniowe zawierają wyłącznie wartości ze słownika §13.1 (jeden token; LENS i TRANSFER_FORM mogą mieć kilka)
L4  każdy wiersz ledgera ma pięć pól, STATE należy do §24.1, REASON zaczyna się od kodu tam, gdzie §24.1 go wymaga, a wiersze są w kolejności rosnącego CANDIDATE_ID
L5  każdy Unit ma NAME; gdy CURRENT INDEX występuje, ma wiersz dla każdego aktualnego Unitu w kolejności rosnącego UNIT_ID, a NAME w nim jest równe NAME w Unicie
L6  SOURCE_ANCHOR jest listą, a każdy jej element ma cztery podpola (§9)
L7  między polami Unitów nie ma prozy (§13.1, reguła 5)
L8  nagłówek ma wszystkie linie z §7, SOURCE_SET ma postać z §7 (`; pytanie:`), a blok TARGET_PROFILE ma trzy podpola, gdy użyto profilu
```

Pass: zero naruszeń w obu przebiegach.

Fail: jakiekolwiek naruszenie. Reguły L1–L8 da się sprawdzić skryptem; sprawdzenie ręczne jest równie ważne.

## Test M — Output register

Sprawdź wszystkie Unity jednego Runu regułami M1–M5:

```text
M1  brak form pierwszej osoby, zwrotów do użytkownika i zapowiedzi w prozie artefaktu (cytaty dosłowne zachowują brzmienie źródła)
M2  brak ocen wartości w blokach SOURCE i EXTRACT (§14), w SIGNAL w SOURCE MAP, w ledgerze, w AUDIT DELTA i w GATE_BASIS
M3  każde zdanie SYNTHESIS ma jeden z sześciu tagów z §29, a oceny mają tag ASSESSMENT
M4  proza artefaktu jest w języku użytkownika, w jednym polu w jednym języku; NAME po angielsku, a tokeny w backtickach i cytaty dosłowne nie liczą się
M5  brak tekstu poza polami między Unitami
```

Pass: zero naruszeń.

Fail: jakiekolwiek naruszenie.

---

# 43. TARGET PROFILE (opcjonalny)

ASMA działa bez profilu. Bez profilu `TRANSFER_FORM` i `ADOPTION_NOTES` nie odnoszą się do żadnego celu, a remis przy wyborze kandydatów rozstrzyga niższy `CANDIDATE_ID` (§24.1, §30 pkt 6).

Profil to opcjonalne wejście `INTAKE`: osobny dokument z własnym identyfikatorem i wersją (np. `TP-NC v0.1`), który mówi, do czego użytkownik chce przenosić mechanizmy. Profil zastępuje `PROJECT_CONTEXT` z v1.3 (B.0, poz. 7).

Zmiana profilu nie zmienia wersji ASMA.

Profil nie jest etapem pipeline'u ani filtrem.

## Zawartość profilu

```text
TARGET:       jedno zdanie, czym jest cel
PROBLEMS:     co cel musi rozwiązać
DOMAINS:      obszary badań (menu, nie lista wykluczeń)
CONSTRAINTS:  ograniczenia celu (np. lekkość, przenośność)
ANTI-GOALS:   czego cel unika
```

## Profil może wpływać wyłącznie na

1. `TRANSFER_FORM` (wybór kształtu transferu) i `ADOPTION_NOTES` (strefa COMMENT, §14): odniesienie do `PROBLEMS`, `CONSTRAINTS` i `ANTI-GOALS`;
2. rozstrzyganie remisu przy wyborze kandydatów.

Remis zachodzi wtedy, gdy po zastosowaniu reguł wyboru z B.8 więcej kandydatów spełnia je jednakowo, a limit `DEPTH_BUDGET` (§31) pozwala pogłębić tylko część z nich. Remis ustalasz bez profilu: profil go nie tworzy, tylko rozstrzyga między kandydatami, którzy po B.8 są jednakowi. Gdy profil nie rozstrzyga, wygrywa niższy `CANDIDATE_ID`.

## Profil nie może

- być powodem odrzucenia źródła, kandydata ani Unitu;
- być trzecim kryterium w `FILTER_1` ani `FILTER_2`;
- zmieniać `LENS` (soczewki pozostają source-adaptive, §37);
- zmieniać `FUNCTION`, `MINIMAL_FORM`, `STATUS`, `EVIDENCE_TYPE`, `EVIDENCE_LAYER`, `ENFORCEMENT`;
- być `REASON` w ledgerze: kandydat pominięty z powodu limitu z §31 ma w `REASON` kod `BUDGET`, a nie odniesienie do profilu;
- sprawiać, że `TRANSFER_FORM` wygląda jak `SOURCE_FACT` (§14).

Unit bez widocznej relewancji dla profilu zostaje w pełnej formie. `ADOPTION_NOTES` może wtedy mówić: brak zidentyfikowanego zastosowania w profilu. Nie obniża to statusu Unitu.

## Nagłówek

Gdy profil został użyty, nagłówek (§7) zawiera blok:

```text
TARGET_PROFILE:
  id: <identyfikator profilu>
  version: <wersja profilu>
  target: <pole TARGET z profilu, jedno zdanie>
```

Gdy profilu nie użyto, bloku nie ma.

Dlaczego: bez tego bloku dwa przebiegi (z profilem i bez) są nie do odróżnienia po skopiowaniu, a sam identyfikator profilu nie mówi po pewnym czasie, czym był cel (§34).

---

# 44. OUTPUT DISCIPLINE

Ta sekcja dotyczy tekstu artefaktu. Czytelnik odbiera ASMA przez ten tekst, a wiarygodność mechanizmu zależy od tego, jak jest zapisany.

## 44.1 Rejestr bezosobowy

Pisz artefakt jako opis źródła i mechanizmu w rejestrze bezosobowym: stwierdzenia o źródle, o mechanizmie i o granicach dowodu.

Poza artefaktem, w rozmowie, możesz pisać swobodnie.

W artefakcie nie używaj:

- form pierwszej osoby ("widzę", "nie przypisuję");
- zwrotów do użytkownika;
- zapowiedzi i obietnic ("zastosuję", "przejdę do");
- propozycji kolejnych kroków poza `SYNTHESIS` (wyjątek: `GATE_BASIS` nazywa pozostałą pracę jako fakt, §27);
- pozostałości interfejsu, np. nazw załączników.

W `AUDIT DELTA` pisz stwierdzenia, np. "Adnotacjom narzędzi nie przypisano funkcji enforcementu".

Dlaczego: artefakt jest czytany po odłączeniu od rozmowy (§34), często jako źródło dalszej pracy. Głos rozmowy nie ma tam nadawcy, a czytelnik może wziąć go za twierdzenie źródła.

## 44.2 Neutralność

W blokach SOURCE i EXTRACT (§14), w `SIGNAL` w `SOURCE MAP`, w ledgerze, w `AUDIT DELTA` i w `GATE_BASIS` zapisuj fakty, a nie oceny wartości ("ważny", "mocny", "najciekawszy", "wartościowy", "ciekawy", "interesujący"). Zamiast oceny podaj fakt, który by ją uzasadniał: warunek, ścieżkę awarii albo granicę zastosowania.

Priorytety dalszej pracy i oceny zapisuj w `SYNTHESIS`, w zdaniu z tagiem `ASSESSMENT` (§29).

Dlaczego: ocena wartości jest ukrytym scoringiem (P12) bez kotwicy w źródle. Zdanie z faktem można sprawdzić, zdanie z oceną nie.

## 44.3 Język

Pisz prozę artefaktu w języku użytkownika, a w obrębie jednego pola w jednym języku. `NAME` zapisuj po angielsku, tak jak tytuły Unitów w dotychczasowych harvestach. Identyfikatory, symbole kodu, ścieżki, nazwy własne i terminy techniczne ze źródła zostaw w oryginale, w backtickach, i nie tłumacz ich. Ujmij w cudzysłów tylko cytat dosłowny, który ma `SOURCE_ANCHOR`. Przykłady `MINIMAL_FORM` w B.12 pokazują kształt zapisu, nie język.

Dlaczego: przetłumaczonego identyfikatora nie da się odnaleźć w źródle, a pole z dwoma językami miesza twierdzenie źródła z komentarzem.

## 44.4 Szczegół bez pola

Szczegół, dla którego nie ma pola (wartość domyślna, parametr, gałąź warunkowa), zapisz w `MINIMAL_FORM`, `MUST_BE_TRUE` albo `LIMITS` (§13.1, reguła 5).

Dlaczego: proza między Unitami nie ma kotwicy ani miejsca w schemacie, więc znika przy kolejnym Runie albo dryfuje.

---

# ZAŁĄCZNIK A — STAN TESTÓW

Testy A–M (§35, §42) mają stan `NOT_RUN`. Dopuszczalne wartości stanu: `NOT_RUN`, `PASSED`, `FAILED`. Stan zmienia się dopiero po wykonaniu testu na przebiegu, który ma zapis.

Harvesty wykonane przed v1.4 (prompty AI, OpenHands, LIDA/CLARION/Soar) nie są wynikiem testów v1.5. Pokazują, że wymagania A–H nie były wtedy spełnione w części: C (U-106 rozszerzony o rejestr narzędzi i adnotacje zamiast `SPLIT`), D (korekta Soar/U-120 zapisana prozą, bez `CORRECTS`), F (numeracja Unitów w harvescie LIDA/CLARION/Soar kontynuuje numerację OpenHands: U-114 po U-113), G (elementy interfejsu między sekcjami).

---

# ZAŁĄCZNIK B — DEFINICJE Z v1.3 (WYCIĄGI)

Ten załącznik czyni specyfikację samowystarczalną: zawiera definicje etapów, soczewek i słowników, do których odwołuje się §0–§44, a których v1.4 nie powtarzała.

## B.0 PIERWSZEŃSTWO I ROZBIEŻNOŚCI

Załącznik B zawiera dosłowne wyciągi z v1.3 w oryginalnym języku (angielskim). Wyciągi obejmują tylko te sekcje v1.3, do których odwołuje się §0–§44.

Przy sprzeczności między §0–§44 a Załącznikiem B obowiązuje §0–§44. Załącznik B nie dodaje etapów, pól ani wartości poza tymi, które wymieniają §13.1 i poniższa lista.

Poniższa lista wskazuje miejsca, w których tekst wyciągów różni się od v1.5, i rozstrzyga, co obowiązuje.

```text
1   TRYB WEJŚCIA
    v1.3 §4:  pole ANALYSIS_MODE (SOURCE_ONLY, SOURCE_PLUS_CONTEXT, VERIFY,
              COMPARATIVE); domyślnie SOURCE_ONLY.
    v1.5 §7:  pole INPUT_MODE.
    OBOWIĄZUJE: INPUT_MODE w nagłówku; wartości i wartość domyślna jak
              w ANALYSIS_MODE.

2   TRYB WYJŚCIA
    v1.3 §4, §56–§58:  OUTPUT_MODE (HARVEST, ANALYSIS, AUDIT, FULL),
              widoki nad rekordem kanonicznym, trzy voices.
    v1.5 §12.1: jeden szablon Runu.
    OBOWIĄZUJE: szablon Runu. OUTPUT_MODE i voices nie obowiązują.
              SOURCE_MAP to sekcja SOURCE MAP; UNKNOWN i REJECTED_INFERENCES
              mają miejsca w §13.1 i §12.1; audyt opisuje §26.

3   STANY KANDYDATA I LEDGER
    v1.3 §15, §37:  stany PENDING, DEEPEN, DROP; rozbudowany ledger
              (filter_1_result, filter_2_result itd.).
    v1.5 §24.1: dyspozycje NOT_PROBED, DEFER, UNITIZED, FILTERED
              i wiersz o pięciu polach.
    OBOWIĄZUJE: §24.1. PENDING, DEEPEN i DROP są stanami roboczymi
              w trakcie Runu. DROP z FILTER_1 odpowiada FILTERED z kodem
              z B.8; REJECTED z FILTER_2 odpowiada FILTERED z kodem REJECTED.

4   ENFORCEMENT
    v1.3 §8 (P8), §31: wartość NOT_APPLICABLE dla Unitów, w których
              enforcement nie jest istotną własnością.
    v1.5 §13.1, reguła 7: pole jest pomijane.
    OBOWIĄZUJE: pominięcie pola (v1.3 §59, I8 dopuszcza pominięcie).
              EFFECT_STATUS zachowuje wartość NOT_APPLICABLE.

5   EVIDENCE_TYPE
    v1.3 §29: wartość CONTEXT.
    v1.5 §13.1: brak tej wartości.
    OBOWIĄZUJE: §13.1, reguła 6 (materiał kontekstowy nie jest źródłem
              Unitu; przedrostek CONTEXT: w ADOPTION_NOTES).

6   WARSTWY DOWODU
    v1.3 §3 (P9), §10: OBSERVED_RUNTIME, CONTEXT, UNKNOWN.
    v1.5 §13.1: DOCUMENTED_DESIGN, IMPLEMENTED_STRUCTURE, TESTED_BEHAVIOR,
              EXTERNAL_EVIDENCE.
    OBOWIĄZUJE: v1.5. Obserwacje wykonania dostarczone jako dowód to
              EXTERNAL_EVIDENCE; klucz OBSERVED w DISCREPANCY odpowiada
              tej warstwie.

7   PROJECT_CONTEXT
    v1.3 §4, §49: kontekst projektu może wpływać na relewancję kandydatów,
              filtrowanie, priorytet pogłębiania i relewancję transferu;
              nie może wpływać na fakt źródłowy, typ dowodu, twierdzenie
              o implementacji ani status efektu.
    v1.5 §43: profil celu wpływa wyłącznie na TRANSFER_FORM,
              ADOPTION_NOTES i rozstrzyganie remisu.
    OBOWIĄZUJE: §43. Profil celu zastępuje PROJECT_CONTEXT. Druga lista
              z §49 (czego kontekst nie może zmieniać) pozostaje w mocy;
              pierwsza lista nie obowiązuje poza zakresem §43.

8   KLASYFIKACJA DOPASOWAŃ
    v1.3 §40, §43, §45: SAME_UNIT, EXTENDS, CONFLICTS, NEW w obrębie
              sesji lub biblioteki; pole MATCH_KEY.
    v1.5 §32: ta sama klasyfikacja w obrębie harvestu.
    v1.5 §41: relacje między harvestami (SAME_MECHANISM, SAME_FUNCTION,
              INCLUDES, CONFLICTS, UNRELATED).
    OBOWIĄZUJE: oba zbiory, każdy w swoim zakresie. MATCH_KEY nie jest
              używany (§16.2).

9   CIĄGŁOŚĆ SESJI I TOŻSAMOŚĆ
    v1.3 §39, §43: UNIT_ID stabilny w sesji lub bibliotece; DIFF; stany
              UNCHANGED, EXTENDED, DOWNGRADED, CONTRADICTED.
    v1.5 §16–§21.1, §22: UNIT_ID stabilny w obrębie harvestu; operacje
              delta NEW, EXTENDS, CORRECTS, SPLIT.
    OBOWIĄZUJE: v1.5.

10  AUDIT
    v1.3 §59: niezmienniki I1–I12; AUDIT_STATUS: FAIL.
    v1.5 §26: AUDIT DELTA.
    OBOWIĄZUJE: B.17 z adaptacjami:
              I2: jawne odrzucenie albo UNITIZATION_FAILURE zapisuje
                  ledger jako FILTERED (kod NO_DISTINCT_FUNCTION albo
                  REJECTED, §24.1), a nieukończone pogłębianie jako DEFER;
              I5: CURRENT INDEX i Candidate Ledger odwołują się wyłącznie
                  do istniejących UNIT_ID (voices nie obowiązują);
              I10: UNIT_ID jest stabilny w obrębie harvestu (§16.1);
              AUDIT_STATUS: FAIL zapisuje się jako ustalenie w AUDIT DELTA (§26).

11  TRYBY VERIFY I COMPARATIVE
    v1.3 §47–§48: rekordy VERIFY i osie porównania.
    v1.5 §7: brak sekcji artefaktu dla tych rekordów.
    OBOWIĄZUJE: B.15 jako zasady postępowania; wynik weryfikacji i osie
              porównania zapisujesz w polach Unitu i w SYNTHESIS (§7).

12  ZAKOŃCZENIE POGŁĘBIANIA
    v1.3 §21 (B.10): „Record: DEPTH_HALT".
    v1.5 §3, §24.1: sukces pogłębienia nie ma tokenu w artefakcie.
    OBOWIĄZUJE: §3 i §24.1. Etykiety DEPTH_HALT nie emituj; kody
              *_LIMIT_REACHED zapisuj tylko przy przerwanym pogłębianiu.

13  BUDŻET NADPISANY
    v1.3 §18 (B.9): budżet wybrany przez użytkownika może być nadpisany,
              gdy źródło jest wyraźnie niezgodne z trybem.
    v1.5 §7: nagłówek zapisuje budżet zastosowany.
    OBOWIĄZUJE: §7. Fakt nadpisania i powód zapisuje ACCESS_LIMITATIONS.

14  RELACJE I TAGI WTÓRNE
    v1.3 §7 (B.4), §26 (B.12): nazwy relacji (ENABLES, CONSTRAINS itd.)
              i wtórne tagi typu.
    v1.5 §13.1, reguła 9: RELATES_TO jest listą UNIT_ID.
    OBOWIĄZUJE: §13.1. Nazw relacji ani wtórnych tagów nie emituj.

15  PRZYKŁADY W WYCIĄGACH
    v1.3 §27 (B.12): przykłady MINIMAL_FORM w jednym języku.
    v1.5 §44.3: język prozy artefaktu to język użytkownika.
    OBOWIĄZUJE: §44.3. Przykłady pokazują kształt zapisu, nie język.

16  PROTOKÓŁ KONFLIKTÓW
    v1.3 §46 (B.14): zachowaj oba twierdzenia, wskaż sprzeczność,
              sklasyfikuj konflikt, porównaj dowody, zapisz stan rozstrzygnięcia.
    v1.5: konflikt nie ma pola ani sekcji.
    OBOWIĄZUJE: B.14 jako zasady postępowania. Konflikt warstw dowodu zapisz
              w DISCREPANCY (§13.1, reguła 9), a konflikt między źródłami
              w LIMITS jako zdanie z obiema twierdzeniami i stanem
              rozstrzygnięcia (RESOLVED, PARTIALLY_RESOLVED, UNRESOLVED).
              Nie dodawaj pola.
```

## B.1 Cel (v1.3 §0, fragment)

Cel, który ASMA maksymalizuje. Zastępuje pojęcie „wartości informacyjnej" kandydata (§0.1).

### Primary objective (v1.3 §0)

Primary objective:

> maximize useful information recovered per unit of analysis cost without upgrading source statements beyond what the available evidence supports.

## B.2 Wejście (v1.3 §4)

Pola wejścia i wartości domyślne. `ANALYSIS_MODE` występuje w v1.5 jako `INPUT_MODE`; `OUTPUT_MODE` nie obowiązuje (B.0, poz. 1 i 2).

### INPUT CONTRACT (v1.3 §4)

```text
SOURCE:
    material to inspect

SOURCE_CONTEXT:
    optional supporting context

PROJECT_CONTEXT:
    optional project or research context

ANALYSIS_MODE:
    SOURCE_ONLY
    SOURCE_PLUS_CONTEXT
    VERIFY
    COMPARATIVE

DEPTH_BUDGET:
    LIGHT
    TARGETED
    DEEP

OUTPUT_MODE:
    HARVEST
    ANALYSIS
    AUDIT
    FULL
```

Defaults:

```text
ANALYSIS_MODE = SOURCE_ONLY
DEPTH_BUDGET = TARGETED
OUTPUT_MODE = HARVEST
```

## B.3 Granica kontekstu (v1.3 §5, §49)

Kontekst nie staje się źródłem. W v1.5 rolę `PROJECT_CONTEXT` pełni profil celu (B.0, poz. 7).

### CONTEXT BOUNDARY (v1.3 §5)

Context may provide:

```text
project requirements
runtime observations
user observations
author notes
external assumptions
```

Context does not become `SOURCE_FACT`.

Context-derived statements remain explicitly marked:

```text
CONTEXT
```

Project relevance may alter selection.

It may not alter evidence.

### PROJECT CONTEXT (v1.3 §49)

Project context may influence:

```text
candidate relevance
filtering
deepening priority
transfer relevance
```

It may not influence:

```text
source fact
evidence type
implementation claim
effectiveness status
```

Project relevance cannot upgrade weak evidence.

## B.4 Soczewki (v1.3 §6–§9)

Definicje wartości `LENS_SYSTEM`, `LENS_KNOWLEDGE` i `LENS_ARTIFACT`.

### SOURCE LENSES (v1.3 §6)

Select the minimum lens set necessary.

```text
LENS_SYSTEM
LENS_KNOWLEDGE
LENS_ARTIFACT
```

Do not activate every lens merely because the source contains multiple media types.

For mixed sources, the lens may be assigned per candidate or Unit.

### LENS_SYSTEM (v1.3 §7)

Use for:

```text
prompts
skills
agents
workflows
routers
tool catalogs
tool schemas
evaluation loops
AI control protocols
```

Primary primitives:

```text
instruction
process_constraint
routing
state_transition
selection_rule
enforcement
interface_contract
memory_context_behavior
failure_control
override
dependency
architecture_relationship
```

Relations:

```text
ENABLES
CONSTRAINS
VERIFIES
OVERRIDES
DEPENDS_ON
ROUTES_TO
BLOCKS
TRIGGERS
```

### LENS_KNOWLEDGE (v1.3 §8)

Use for:

```text
papers
technical articles
methodological documents
benchmark reports
technical essays
```

Primary primitives:

```text
claim
definition
assumption
argument
method
evidence_result
limitation
boundary_condition
counterevidence
threat_to_validity
design_principle
```

Preserve the distinction between:

```text
what the source argues
what was measured
what evidence supports
what the authors infer
what ASMA infers
```

Citation repetition is not automatically independent evidence.

### LENS_ARTIFACT (v1.3 §9)

Use for:

```text
repositories
libraries
implementations
schemas
code + tests
```

Primary primitives:

```text
interface_contract
entry_point
call_path
algorithm
data_structure
invariant
config_surface
dependency
module
example
test_oracle
runtime_assumption
implementation_constraint
error_path
failure_control
```

The core protocol identifies these structures.

Language-specific parsing, AST analysis, repository retrieval and execution are external tooling.

## B.5 Warstwy dowodu dla artefaktów (v1.3 §10)

Pytania, na które odpowiadają warstwy dowodu. Lista warstw obowiązująca w v1.5 jest w §13.1 (B.0, poz. 6).

### ARTIFACT EVIDENCE (v1.3 §10)

For implementation-related claims use:

```text
DOCUMENTED_DESIGN
IMPLEMENTED_STRUCTURE
TESTED_BEHAVIOR
OBSERVED_RUNTIME
```

Example:

```text
"What does the README claim?"
→ DOCUMENTED_DESIGN

"What exists in the code?"
→ IMPLEMENTED_STRUCTURE

"What behavior is asserted by tests?"
→ TESTED_BEHAVIOR

"What happened during execution?"
→ OBSERVED_RUNTIME
```

Do not use a universal precedence rule such as:

```text
code > tests > documentation
```

The relevant evidence layer depends on the question.

## B.6 INTAKE, polityka wejścia i MAP (v1.3 §11–§13)

Treść etapów `INTAKE` i `MAP`. Wynik `MAP` zapisuje sekcja `SOURCE MAP` (§12.1).

### INTAKE (v1.3 §11)

Determine:

```text
SOURCE_TYPE
VISIBLE_SCOPE
OUTSIDE_SCOPE
LENS
INPUT_LIMITATIONS
PROJECT_CONTEXT
ANALYSIS_MODE
DEPTH_BUDGET
OUTPUT_MODE
```

INTAKE is routing, not deep interpretation.

### SOURCE INTAKE POLICY (v1.3 §12)

#### SYSTEM

Prefer:

```text
surface specification
→ interfaces
→ process/routing
→ selected details
```

#### KNOWLEDGE

Prefer:

```text
claims/contributions
→ method
→ evaluation
→ limitations
→ selected supporting detail
```

#### ARTIFACT

Prefer:

```text
manifest / README / API surface
→ public entry points
→ relevant tests
→ selected implementation
→ supporting configuration/dependencies
```

Do not inspect an entire source merely because it exists.

### MAP (v1.3 §13)

Create a compact structural map identifying:

```text
major sections/components
likely signal
candidate locations
unknown regions
scope boundaries
```

MAP provides orientation.

MAP is not deep analysis.

## B.7 PROBE (v1.3 §14)

Treść etapu `PROBE`.

### PROBE (v1.3 §14)

PROBE is a cheap, recall-oriented scan.

Candidates may originate from:

```text
heading
function/class signature
schema field
table row
test name
file path
explicit rule
named method
example
interface
claim statement
```

At PROBE:

```text
evidence = location-level support
```

Do not require full interpretation yet.

The purpose of PROBE is to reduce false negatives caused by premature precision.

## B.8 FILTER_1 i reguły wyboru kandydatów (v1.3 §16–§17)

Treść etapu `FILTER_1`, kody przyczyn usunięcia i reguły wyboru kandydatów, gdy jest ich więcej niż miejsc na pogłębianie.

### FILTER_1 — RECALL FILTER (v1.3 §16)

FILTER_1 removes only obvious non-candidates.

Allowed DROP reasons:

```text
DUPLICATE
OUTSIDE_SCOPE
RESTATEMENT
NO_DISTINCT_FUNCTION
CLEARLY_NON_TRANSFERABLE
```

Do not use:

```text
UNSUPPORTED
INSUFFICIENT_EVIDENCE
UNKNOWN
```

as FILTER_1 drop reasons.

Evidence insufficiency means:

```text
DEEPEN
```

unless the candidate is otherwise clearly removable.

### PRE-DEEPEN RESOURCE CONTROL (v1.3 §17)

FILTER_1 must respect the selected `DEPTH_BUDGET`.

When candidates exceed available deepening capacity:

1. retain candidates with distinct functional signal,
    
2. retain candidates covering different source regions where practical,
    
3. prefer candidates with explicit transfer potential,
    
4. preserve candidates whose deeper evidence could materially change the harvest,
    
5. drop only candidates justified by the FILTER_1 rules.
    

Do not invent a mandatory minimum number of deepened candidates.

Do not force artificial diversity when the source contains little signal.

## B.9 DEPTH_BUDGET i głębokość kandydata (v1.3 §18–§19)

Pełne zasady budżetu głębokości. Limity kandydatów powtarza §31.

### DEPTH_BUDGET (v1.3 §18)

Depth budget is a cap.

It is not a quality score.

#### LIGHT

```text
max 7 candidates
max 3 deepened candidates
SURFACE depth
no dependency tracing unless essential
```

#### TARGETED

```text
max 12 candidates
max 5 deepened candidates
SURFACE → CONTEXT
dependency tracing only when required
```

#### DEEP

```text
no fixed candidate cap
CONTEXT → TRACE allowed
extended dependency tracing allowed
still subject to material stop
```

User-selected budget may be overridden when the source is obviously incompatible with the selected mode; the reason must be stated briefly.

Do not create an arbitrary numeric complexity score.

### CANDIDATE DEPTH (v1.3 §19)

```text
SURFACE
    characterize the candidate

CONTEXT
    inspect surrounding material necessary to establish function
    and dependencies

TRACE
    follow implementation, evidence, tests, relations or
    dependency paths required to resolve the candidate
```

Candidate depth does not determine whether the source itself is complete.

## B.10 DEEPEN, DEPTH_HALT i niezmienniki rdzenia (v1.3 §20, §21, §62)

Treść etapu `DEEPEN` i zasady zakończenia pogłębiania kandydata (`DEPTH_HALT`).

### DEEPEN (v1.3 §20)

Deepen only selected candidates.

DEEPEN seeks:

```text
what does this actually do?
what evidence supports that?
what does it depend on?
what must be true?
what breaks if isolated?
what can be transferred?
what remains unknown?
```

Do not deepen to fill fields.

### CANDIDATE LOCAL HALT (v1.3 §21)

A candidate may stop deepening when:

```text
its function is sufficiently established
AND
its evidence boundary is known
AND
its transfer form is sufficiently characterized
AND
additional depth is unlikely to materially change the Unit
```

Record:

```text
DEPTH_HALT
```

A candidate can also stop because:

```text
DEPTH_LIMIT_REACHED
DEPENDENCY_LIMIT_REACHED
EVIDENCE_LIMIT_REACHED
```

These are different from successful characterization.

### CORE INVARIANTS (v1.3 §62, fragment)

Core invariant:

```text
SELECT BEFORE DEEPENING.
```

Secondary invariant:

```text
PROBE BEFORE PRECISION.
```

Termination distinction:

```text
DEPTH_HALT ≠ SOURCE_GATE
```

Evidence distinction:

```text
STATUS ≠ EFFECT_STATUS
```

## B.11 FILTER_2 (v1.3 §23)

Treść etapu `FILTER_2` i znaczenie wartości `STATUS`.

### FILTER_2 — PRECISION FILTER (v1.3 §23)

After DEEPEN, classify the candidate:

```text
SOURCE_SUPPORTED
CONDITIONAL
REJECTED
```

#### SOURCE_SUPPORTED

The Unit is supported at the claimed evidentiary level.

This does not mean that the mechanism is effective.

#### CONDITIONAL

The Unit is usable only with explicit assumptions, unresolved evidence or relevant context dependence.

#### REJECTED

The candidate does not survive the evidence or transfer analysis.

Rejected candidates remain traceable through the Candidate Ledger.

## B.12 Wartości pól Unitu (v1.3 §26–§36)

Lista wartości `TYPE`, zasady `MINIMAL_FORM`, kotwic i typów dowodu, a także `ISOLATION_STATUS`, `DISCREPANCY`, typowany `UNKNOWN`, `REJECTED INFERENCES` i kształty transferu. Wartości pól obowiązujące w v1.5 wymienia §13.1; rozbieżności w B.0, poz. 4–6, 14 i 15.

### UNIT TYPES (v1.3 §26)

Primary `TYPE` is selected from:

```text
mechanism
process_constraint
routing
evaluation_rule
interface_contract
algorithm
data_structure
invariant
test_oracle
schema
claim
method
evidence_result
limitation
design_principle
failure_control
```

One primary type per Unit.

Optional secondary tags may describe relations.

### MINIMAL_FORM (v1.3 §27)

`MINIMAL_FORM` is the compact transferable representation of the Unit.

It should be:

```text
functional
compact
source-faithful
usable without the original essay
free of promotional adjectives
free of unsupported conclusions
```

Examples:

```text
generate[N] → evaluate/select

search → fetch → inspect before answer

public fn(X) → Y; tests lock behavior on cases A,B

claim C measured by M on D; off-domain effect unknown
```

Do not turn `MINIMAL_FORM` into an explanatory paragraph.

### EVIDENCE ANCHOR (v1.3 §28)

Every Unit requires a `SOURCE_ANCHOR`.

Possible anchors:

```text
quotation
section
page
line range
file path
function/class
schema field
test
configuration entry
observed execution
external source
```

A direct quotation is preferred where practical for source-fact claims.

Do not fabricate precision.

### EVIDENCE TYPE (v1.3 §29)

Use:

```text
SOURCE_FACT
DIRECT_INFERENCE
MECHANISTIC_HYPOTHESIS
EFFECTIVENESS_CLAIM
EXTERNAL_EVIDENCE
CONTEXT
```

`EVIDENCE_TYPE` must never be stronger than the supporting material.

### STATUS ≠ EFFECTIVENESS (v1.3 §30)

Unit status and effectiveness are separate.

```text
STATUS:
    SOURCE_SUPPORTED
    CONDITIONAL
    REJECTED

EFFECT_STATUS:
    CLAIMED
    TESTED_IN_SOURCE
    EXTERNALLY_SUPPORTED
    UNKNOWN
    NOT_APPLICABLE
```

Never infer effectiveness from `SOURCE_SUPPORTED`.

### ENFORCEMENT APPLICABILITY (v1.3 §31)

For rules and constraints:

```text
PROSE_ONLY
SCHEMA_CONSTRAINED
RUNTIME_CONSTRAINED
HOST_CONSTRAINED
EXTERNAL_CONSTRAINT
UNKNOWN
```

For non-enforcement-bearing Units:

```text
NOT_APPLICABLE
```

Do not use `UNKNOWN` where the category does not apply.

### ISOLATION (v1.3 §32)

Where relevant:

```text
BREAKS_IF_ISOLATED
ISOLATION_STATUS
```

`ISOLATION_STATUS`:

```text
SOURCE_FACT
DIRECT_INFERENCE
MECHANISTIC_HYPOTHESIS
UNKNOWN
```

If isolation behavior is not established, do not present it as a fact.

### DISCREPANCY (v1.3 §33)

For conflicting evidence layers:

```text
DISCREPANCY:
    DOCUMENTED:
    IMPLEMENTED:
    TESTED:
    OBSERVED:
```

Preserve the discrepancy.

Do not silently select one layer as universal truth.

### UNKNOWN (v1.3 §34)

`UNKNOWN` is typed rather than multiplied into many separate field names.

Example:

```yaml
unknown:
  - kind: evidence
    note: actual runtime behavior not observed
  - kind: dependency
    note: external state requirement unclear
  - kind: isolation
    note: behavior without selector is not established
```

Zero unknowns is valid.

Do not generate unknowns merely to make the output look cautious.

### REJECTED INFERENCES (v1.3 §35)

Maintain `REJECTED_INFERENCES` when meaningful interpretations were considered and rejected.

Examples:

```text
instruction ≠ demonstrated effectiveness
README claim ≠ runtime behavior
test presence ≠ complete implementation coverage
named technique ≠ exact implementation
author explanation ≠ independent evidence
```

There is no required minimum count.

Zero is valid when no material rejected inference occurred.

### TRANSFER (v1.3 §36, fragment)

Possible transfer shapes:

```text
PROMPT_FRAGMENT
PROCESS_RULE
ROUTER
SCHEMA
EVALUATION_RULE
INTERFACE
ALGORITHM
DATA_STRUCTURE
TEST
WORKFLOW
DESIGN_PRINCIPLE
METHOD
```

Transferability is about what survives translation, not whether the original architecture can be copied.

## B.13 SOURCE_GATE (v1.3 §42, §44)

Znaczenie wartości `SOURCE_GATE` i jego związek z ciągłością.

### SOURCE GATE (v1.3 §42)

```text
SOURCE_GATE:
    CONTINUE
    CONTINUE_CONDITIONALLY
    STOP
```

#### CONTINUE

Additional source material is likely to add materially new harvest.

#### CONTINUE_CONDITIONALLY

Additional analysis requires a named input or source fragment.

#### STOP

Additional analysis is not currently justified.

STOP does not mean the source is permanently exhausted.

New evidence can reopen a stopped source.

### SESSION + SOURCE GATE (v1.3 §44)

`STOP` does not block future continuation.

It means:

```text
no additional analysis is currently justified
```

New material may reopen the source.

`CONTINUE_CONDITIONALLY` identifies what is missing.

This avoids creating a separate `PAUSE` state in the core.

## B.14 Dopasowania i konflikty (v1.3 §40, §45, §46)

Klasyfikacja dopasowań w obrębie harvestu (§32) i protokół konfliktów (zapis konfliktu: B.0, poz. 16).

### MATCH KEY (v1.3 §40, fragment)

Potential matches must be classified:

```text
SAME_UNIT
EXTENDS
CONFLICTS
NEW
```

Human or higher-level model confirmation may be required for ambiguous matches.

### MULTI-SOURCE HARVEST (v1.3 §45, fragment)

When two sources appear to describe the same mechanism:

```text
SAME_UNIT
EXTENDS
CONFLICTS
NEW
```

Do not merge merely because wording is similar.

Do not treat repeated claims as independent confirmation.

### CONFLICT PROTOCOL (v1.3 §46)

When sources conflict:

1. preserve both claims,
    
2. identify the exact contradiction,
    
3. classify the conflict:
    

```text
EMPIRICAL
DESIGN
IMPLEMENTATION
THEORETICAL
SCOPE
```

4. compare evidentiary support,
    
5. record the resolution state.
    

Resolution states:

```text
RESOLVED
PARTIALLY_RESOLVED
UNRESOLVED
```

Do not silently choose one source.

If evidence is insufficient:

```text
UNRESOLVED
```

is the correct result.

## B.15 Tryby VERIFY i COMPARATIVE (v1.3 §47–§48)

Zasady postępowania dla wartości `INPUT_MODE`: `VERIFY` i `COMPARATIVE`. W artefakcie tryby nie mają sekcji rekordów (§7, B.0, poz. 11).

### VERIFY MODE (v1.3 §47)

VERIFY is targeted.

Prioritize:

```text
effectiveness claims
material conflicts
high-impact uncertain claims
claims whose verification could change adoption
```

Record:

```text
VERIFY_TARGET
SOURCE_ASSERTION
EXTERNAL_EVIDENCE
STATUS
SEARCH_RESULT
```

Status:

```text
SUPPORTED
PARTIALLY_SUPPORTED
CONTESTED
NOT_VERIFIED
REFUTED
UNKNOWN
```

`NOT_VERIFIED` may specify:

```text
UNAVAILABLE
NOT_SEARCHED
SEARCH_FAILED
SEARCHED_NO_SUPPORT_FOUND
```

Absence of support is not automatically refutation.

### COMPARATIVE MODE (v1.3 §48)

Default comparison axes:

```text
function
dependencies
enforcement
evidence_type
transfer_form
breaks_if_isolated
```

Additional axes may be added when materially relevant.

Do not convert comparison into a universal ranking.

## B.16 Monitorowanie własnych błędów (v1.3 §50–§51)

Wzorce błędów procesu i pytania kontrolne przed emisją.

### SELF-FAILURE REGISTRY (v1.3 §50)

ASMA monitors its own process for:

#### CATEGORY_FORCING

The selected lens does not fit the material.

Response:

```text
switch lens
split candidate
or mark unsupported
```

#### HARVEST_COLLAPSE

The output becomes a summary rather than an inventory.

Response:

```text
return to Units and Candidate Ledger
```

#### DEPTH_DRIFT

Analysis continues after a candidate is sufficiently characterized.

Response:

```text
DEPTH_HALT
```

#### EVIDENCE_DRIFT

Inference becomes source fact.

Response:

```text
re-anchor
downgrade
or reject
```

#### UNIT_FRAGMENTATION

One mechanism is split into trivial Units.

Response:

```text
merge when no independent transfer value exists
```

#### UNIT_MONOLITH

A whole architecture becomes one Unit.

Response:

```text
decompose
```

#### TEMPLATE_PRESSURE

Fields are filled because they exist.

Response:

```text
omit non-applicable material
```

#### HARVEST_NOISE

Many observations, little reusable signal.

Response:

```text
tighten selection
```

These are monitoring rules, not automatic scoring functions.

### HUMAN-FACTOR SAFEGUARDS (v1.3 §51)

ASMA does not assume perfect rationality.

Before final emission, check:

```text
Could an early candidate have anchored later selection?

Did project context cause a weak candidate to appear more relevant than supported?

Did source prestige influence evidence interpretation?

Did novelty influence transfer judgment?

Did continued analysis occur only because work had already been invested?
```

Do not impose artificial numbers of dropped candidates or rejected inferences.

The safeguard is inspection, not ritualized output.

## B.17 AUDIT: niezmienniki (v1.3 §59–§60)

Treść etapu `AUDIT`. Adaptacje niezmienników I2, I5 i I10 do v1.5: B.0, poz. 10.

### AUDIT INVARIANTS (v1.3 §59)

Before emission:

```text
I1 Every candidate has a ledger disposition.

I2 Every DEEPEN candidate has either:
   a Unit,
   or an explicit rejection/UNITIZATION_FAILURE.

I3 Every Unit has a source anchor.

I4 Every Unit.evidence_type is no stronger than its evidence.

I5 Voice 2 references only existing Unit IDs.

I6 Effectiveness is never encoded as Unit STATUS.

I7 FILTER_1 never drops for insufficient evidence.

I8 Non-applicable fields are omitted or marked NOT_APPLICABLE.

I9 Source conflicts are preserved.

I10 Stable UNIT_ID survives session continuation.

I11 Candidate halt is not treated as source halt.

I12 Project context cannot upgrade evidence.
```

If an invariant fails:

```text
AUDIT_STATUS:
    FAIL
```

The relevant failure must be exposed before emission.

### FINAL AUDIT (v1.3 §60)

Before output:

```text
SOURCE FIDELITY
CLAIM DISCIPLINE
LENS FIT
PROBE COVERAGE
FILTER ORDER
CANDIDATE LEDGER
EVIDENCE ANCHORS
ENFORCEMENT APPLICABILITY
DEPENDENCIES
ISOLATION STATUS
DISCREPANCIES
REJECTED INFERENCES
UNKNOWN
UNIT IDENTITY
MULTI-SOURCE CONFLICTS
SESSION CONTINUITY
DUPLICATION
SOURCE GATE
```

## B.18 Źródła duże i nieustrukturyzowane (v1.3 §52–§53)

Zasady dla źródeł dzielonych na fragmenty i dla źródeł o słabej strukturze. Dotyczy także źródeł bez dokumentacji (§1, P12).

### LARGE SOURCES (v1.3 §52)

Large-source retrieval, chunking, AST parsing and repository traversal belong to external tooling.

The ASMA core assumes that the input material available to it is already accessible.

When source boundaries are externally chunked:

```text
preserve source location
preserve chunk identity
preserve cross-chunk relations
do not treat chunk boundaries as semantic boundaries
```

ASMA may operate incrementally across chunks through Session Continuity.

### UNSTRUCTURED SOURCES (v1.3 §53)

When source structure is weak:

```text
do not invent headings or architecture as facts
use semantic boundaries cautiously
lower confidence when source anchors are weak
preserve uncertainty
```

Unstructured mode is a lens behavior, not a new core architecture.
