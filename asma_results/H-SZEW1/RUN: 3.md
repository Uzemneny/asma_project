[ASMA ARTIFACT]

HARVEST HEADER
HARVEST_ID: H-SZEW1
TITLE: Szew technika / człowiek — mechanizmy pamięci, kompresji i przerwań w agentach
SOURCE_SET: korpus leadów discovery „SZEW: TECHNIKA / CZŁOWIEK" i ich źródła pierwotne; pytanie: jakie mechanizmy rozdzielają warstwę techniczną od ludzkiej albo opisują, jak ta granica przecieka
SOURCES:
  - Wejście ASMA INPUT SZEW: TECHNIKA / CZŁOWIEK
  - A-MEM paper (arXiv 2502.12110 v11)
  - Mem0 paper (arXiv 2504.19413 v1)
  - Reflexion paper (arXiv 2303.11366 v4)
  - Self-Refine paper (arXiv 2303.17651 v2)
  - Constitutional AI paper (arXiv 2212.08073 v1)
  - Generative Agents paper (arXiv 2304.03442 v2)
  - OpenHands Docs (docs.openhands.dev)
  - OpenHands SDK, pakiet openhands-sdk 1.51.0 (rejestr PyPI)
  - W3C PROV-Overview (Working Group Note, 2013-04-30)
  - W3C PROV-DM
  - Zep paper (arXiv 2501.13956 v1)
  - Graphiti, pakiet graphiti-core 0.30.2 (rejestr PyPI)
  - LangGraph Docs (docs.langchain.com)
  - Rozdział o implicit cognition (Purdue CCN, chap_3.pdf), opisujący CLARION skrótowo
RUN: 3
FOCUS: źródło kryterium i zasad w pętlach poprawiania (Self-Refine, Constitutional AI) oraz relacja refleksji do wpisów surowych (Generative Agents)
INPUT_MODE: SOURCE_ONLY
DEPTH_BUDGET: TARGETED
DATE: 2026-10-04
ACCESS_LIMITATIONS:
  - Self-Refine paper, Constitutional AI paper i Generative Agents paper odczytane przez narzędzie zwracające streszczenie wersji PDF, nie surowy tekst; numery sekcji, tabel i cytaty pochodzą z odpowiedzi narzędzia i nie zostały sprawdzone na surowym tekście; wartości liczbowe z tabel Self-Refine nie zostały przepisane do Unitu
  - kod referencyjny trzech prac nieotwarty (repozytoria GitHub odrzucone przez narzędzie odczytu w Runie 1); wszystkie nowe Unity mają warstwę DOCUMENTED_DESIGN
  - CLARION: PDF Sun, Merrill, Peterson 2001 pod adresem cogsci.rpi.edu odrzucony przez narzędzie odczytu (ROBOTS_DISALLOWED); rozdział Purdue CCN otwarty, ale opisuje CLARION skrótowo, bez mechanizmu ekstrakcji reguł
  - ograniczenia Runów 1 i 2 dotyczące materiału nieotwieranego w tym Runie pozostają w mocy
TARGET_PROFILE:
  id: SZEW-TECHNIKA-CZLOWIEK (wejście nie nadaje identyfikatora; nazwa z nagłówka pliku)
  version: UNKNOWN
  target: neuralcore jako interfejs dostrojony do człowieka (pole ZASADA; pole TARGET w wejściu nie występuje)

SOURCE MAP
REGION | LOCATOR | SIGNAL
Self-Refine paper | https://arxiv.org/pdf/2303.17651, §2 (Algorithm 1), §3.1, §4 (Tabela 2), Appendix C | ten sam model w trzech rolach, prompt informacji zwrotnej z przykładami, historia w prompcie poprawiania, limit iteracji i wskaźnik stopu
Constitutional AI paper | https://arxiv.org/pdf/2212.08073, §3.1, §3.2, §4.1, §4.3, przypis 2, Appendix C.1–C.2 | losowa zasada w każdym kroku rewizji, cztery pary krytyka–rewizja, 16 zasad napisanych przez autorów
Generative Agents paper | https://arxiv.org/pdf/2304.03442, §4.1, §4.2, §4.3 | rekord strumienia pamięci, wynik wyszukiwania z trzech składników, próg refleksji, wskaźniki do cytowanych rekordów
Rozdział o implicit cognition | https://ccn.psych.purdue.edu/papers/chap_3.pdf | CLARION wymieniony jako implementacja teorii EII; brak opisu mechanizmu ekstrakcji reguł
UNKNOWN_REGIONS:
  - grupa PRAKTYKA CZŁOWIEKA I JEJ MECHANIZACJA, leady nienazwane jako kandydaci: Zettelkasten systems, Memex, HippoRAG / HippoRAG 2, Personal Knowledge Graphs
  - grupa GDZIE SZEW PRZECIEKA, leady nienazwane jako kandydaci: DSPy, RAPTOR, AlphaEvolve, FunSearch, Darwin Gödel Machine
  - grupa CO TRZYMA SZEW, leady nienazwane jako kandydaci: EventStoreDB, Claude Code · autoryzacja i odwracalność, OpenHands · analizator i polityka potwierdzeń, OpenAI Model Spec, River, LangSmith, MemoryBank
  - grupa KLIMAT JAKO TRYB, leady nienazwane jako kandydaci: CAPS, Emotion Machine, MicroPsi / MicroPsi 2, Companions
  - etap uczenia z preferencji modelu (RLAIF) w Constitutional AI, §4, poza Unitem U-011
  - sekcje oceny Generative Agents i Self-Refine nieotwarte
  - kod implementacji (repozytoria) Self-Refine, Constitutional AI i Generative Agents
OUTSIDE_SCOPE:
  - pola i pytania z bloku PROBES_OUTSIDE_CORPUS
  - zachowanie systemów w czasie wykonania

DELTA
NEW
UNIT_ID: U-010
NAME: Same-Model Feedback Loop with Accumulating History
LENS: LENS_ARTIFACT
TYPE: algorithm
STATUS: SOURCE_SUPPORTED
FUNCTION: Ten sam LLM generuje wynik, wytwarza informację zwrotną na podstawie przykładów w prompcie i poprawia wynik; prompt poprawiania zawiera wszystkie wcześniejsze wyniki i informacje zwrotne; pętla kończy się po ustalonej liczbie iteracji albo po wskaźniku stopu wyodrębnionym z informacji zwrotnej.
MINIMAL_FORM:
  - `y0` = M(`p_gen` ∥ `x`); `fb_t` = M(`p_fb` ∥ `x` ∥ `y_t`); `y_{t+1}` = M(`p_refine` ∥ `x` ∥ `y0` ∥ `fb0` ∥ … ∥ `y_t` ∥ `fb_t`)
  - `p_fb` zawiera przykłady trójek wejście–wynik–informacja zwrotna (według odczytu: równanie 2)
  - zatrzymanie: limit iteracji (w eksperymentach do 4) albo `stop(fb_t, t)` wyodrębnione z informacji zwrotnej (Algorithm 1)
SOURCE_ANCHOR:
  - source: Self-Refine paper (arXiv 2303.17651 v2)
    locator: https://arxiv.org/pdf/2303.17651
    anchor: §2 Algorithm 1 i równania 2 oraz 4, §3.1, §4 Tabela 2, Appendix C Tabela 11
    revision: v2
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: DOCUMENTED_DESIGN
DEPENDENCIES:
  - jeden LLM występujący w trzech rolach (generacja, informacja zwrotna, poprawa)
  - przykłady w promptach dla ról informacji zwrotnej i poprawy
MUST_BE_TRUE: z tekstu informacji zwrotnej da się wyodrębnić wskaźnik stopu albo jest ustalony limit iteracji
ENFORCEMENT: UNKNOWN
EFFECT_STATUS: TESTED_IN_SOURCE
TRANSFER_FORM: ALGORITHM, WORKFLOW
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: kryterium w kroku informacji zwrotnej wyznacza ten sam model, który wytworzył wynik; jedynym warunkiem stopu niezależnym od modelu w odczytanym opisie jest limit iteracji
  - dotyczy ANTI-GOALS profilu: prompt poprawiania zawiera wyniki i informacje zwrotne z poprzednich iteracji; opis nie podaje znacznika rozróżniającego tekst użytkownika od tekstu modelu
UNKNOWN:
  - evidence: sposób wyodrębniania wskaźnika stopu w implementacji; kod nieotwarty
  - evidence: wartości liczbowe z Tabeli 2 i Tabeli 11 niezweryfikowane na surowym tekście
LIMITS:
  - w Tabeli 2 warianty z informacją zwrotną ogólną i bez informacji zwrotnej dają niższe wyniki niż wariant z informacją konkretną
  - Appendix C (Tabela 11) przypisuje większość niepowodzeń błędom w informacji zwrotnej
  - pytanie z wejścia, czy kolejna iteracja poprawia, a nie tylko wygładza, nie jest rozstrzygnięte przez Tabelę 2: tabela porównuje rodzaje informacji zwrotnej na wynikach zadań
RELATES_TO:
  - U-003
  - U-011

NEW
UNIT_ID: U-011
NAME: Randomly Sampled Principle Critique-Revision Loop
LENS: LENS_ARTIFACT
TYPE: algorithm
STATUS: SOURCE_SUPPORTED
FUNCTION: W etapie nadzorowanym model dla promptu generuje odpowiedź, a następnie wykonuje kolejne pary krytyka–rewizja; w każdym kroku do promptu wchodzi jedna zasada wylosowana z listy napisanej przez autorów pracy.
MINIMAL_FORM:
  - `r_0` = odpowiedź modelu na prompt red-team
  - krok `i` (do 4 par): `p_i` losowane z listy 16 zasad; krytyka(`r_{i−1}`, `p_i`) → rewizja `r_i`
  - lista zasad jest wejściem pętli; pętla nie zmienia listy
SOURCE_ANCHOR:
  - source: Constitutional AI paper (arXiv 2212.08073 v1)
    locator: https://arxiv.org/pdf/2212.08073
    anchor: §3.1, §3.2, przypis 2, Appendix C.1
    revision: v1
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: DOCUMENTED_DESIGN
DEPENDENCIES:
  - lista zasad w postaci tekstu
  - model wykonujący krytykę i rewizję w prompcie
MUST_BE_TRUE: lista zasad istnieje przed pętlą
ENFORCEMENT: PROSE_ONLY
EFFECT_STATUS: TESTED_IN_SOURCE
TRANSFER_FORM: ALGORITHM, WORKFLOW
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: zasady wchodzą do promptu jako tekst napisany przez autorów i są losowane; w odczytanej treści nie opisano mechanizmu nadpisania zasady przez użytkownika
  - dotyczy ANTI-GOALS profilu: rewizja `r_i` zastępuje `r_{i−1}` jako wejście kolejnego kroku
UNKNOWN:
  - evidence: mechanizm nadpisania zasady przez użytkownika nie jest opisany w odczytanej treści; brak opisu nie dowodzi braku mechanizmu w systemie wdrożonym
  - evidence: kod nieotwarty; zachowanie w czasie wykonania nie było obserwowane
LIMITS:
  - przypis 2 opisuje wybór zasad jako ad hoc i iteracyjny, do celów badawczych
  - ocena efektu opiera się na wykresie liczby rewizji (Figure 5 według odczytu); wartości niezweryfikowane na surowym tekście
  - Unit obejmuje pętlę nadzorowaną; etap uczenia z preferencji modelu (losowa zasada przy każdej etykiecie porównania, §4.1, §4.3) jest poza Unitem
RELATES_TO:
  - U-010

NEW
UNIT_ID: U-012
NAME: Reflection Records with Evidence Pointers in a Shared Memory Stream
LENS: LENS_KNOWLEDGE
TYPE: data_structure
STATUS: SOURCE_SUPPORTED
FUNCTION: Strumień pamięci przechowuje rekordy z opisem w języku naturalnym i dwoma znacznikami czasu; gdy suma ocen ważności ostatnich zdarzeń przekroczy próg, model generuje pytania i wnioski z cytowaniem rekordów, a wniosek jest zapisywany w tym samym strumieniu jako refleksja ze wskaźnikami do cytowanych rekordów; refleksje mogą cytować refleksje.
MINIMAL_FORM:
  - rekord: opis, znacznik utworzenia, znacznik ostatniego dostępu; ważność (skala 1–10) nadaje model przy utworzeniu
  - wynik wyszukiwania = suma ważona znormalizowanych składników: aktualność (zanik wykładniczy, współczynnik 0,995), ważność, trafność (cosinus wektorów)
  - wyzwalacz refleksji: suma ważności ostatnich zdarzeń większa niż 150
  - model → 3 najistotniejsze pytania → wnioski z numerami cytowanych rekordów → zapis refleksji w strumieniu razem ze wskaźnikami do cytowanych rekordów
  - drzewo refleksji: liście to obserwacje, węzły wyższe to refleksje o rosnącej abstrakcji
SOURCE_ANCHOR:
  - source: Generative Agents paper (arXiv 2304.03442 v2)
    locator: https://arxiv.org/pdf/2304.03442
    anchor: §4.1 Memory Stream, §4.2 Reflection, §4.3 Planning (zdanie o planach w wyszukiwaniu)
    revision: v2
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: DOCUMENTED_DESIGN
DEPENDENCIES:
  - LLM oceniający ważność rekordów i generujący pytania oraz wnioski
  - wektory osadzeń opisów rekordów
MUST_BE_TRUE: numeracja rekordów w prompcie refleksji pozwala modelowi cytować rekordy
ENFORCEMENT: UNKNOWN
EFFECT_STATUS: UNKNOWN
TRANSFER_FORM: DATA_STRUCTURE
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: refleksja jest zapisywana ze wskaźnikami do cytowanych rekordów, więc ścieżka od refleksji do rekordów surowych jest zapisana; warstwa pochodna leży w tym samym strumieniu co obserwacje
  - dotyczy ANTI-GOALS profilu: opis wyszukiwania podaje jeden wzór dla rekordów strumienia, a plany i refleksje wchodzą do wyszukiwania (§4.3); wzór nie zawiera składnika pochodzenia rekordu
UNKNOWN:
  - evidence: czy implementacja przechowuje pole typu rekordu; praca używa sformułowania „drugi typ pamięci" (§4.2)
  - evidence: skutki refleksji nad refleksją nie zostały odczytane; sekcje oceny nieotwarte
  - dependency: kod nieotwarty
LIMITS:
  - wartości progu (150), zaniku (0,995) i skali ważności (1–10) pochodzą z odpowiedzi narzędzia zwracającego streszczenie
  - wskaźniki do cytowanych rekordów opisują, z czego model wywiódł wniosek; nie wykazują, że treść refleksji zgadza się z cytowanymi rekordami
RELATES_TO:
  - U-003
  - U-004
  - U-008

CURRENT INDEX
U-001 | Neighbor Note Rewrite on Insert | SOURCE_SUPPORTED | last: run 1
U-002 | LLM-Selected Memory Operation per Extracted Fact | SOURCE_SUPPORTED | last: run 1
U-003 | Bounded Append-Only Verbal Reflection Buffer | SOURCE_SUPPORTED | last: run 1
U-004 | Append-Only Event Log with Condensation as Filter Event | SOURCE_SUPPORTED | last: run 2
U-005 | Checkpointed Interrupt with Node Restart on Resume | SOURCE_SUPPORTED | last: run 1
U-006 | Reason-Derived Hard or Soft Condensation Requirement | SOURCE_SUPPORTED | last: run 2
U-007 | Protected-Head Atomic-Boundary Forgetting Range | SOURCE_SUPPORTED | last: run 2
U-008 | Minimal Provenance Types and Derivation Relations | SOURCE_SUPPORTED | last: run 2
U-009 | Bitemporal Fact Invalidation with Retained Source Episodes | SOURCE_SUPPORTED | last: run 2
U-010 | Same-Model Feedback Loop with Accumulating History | SOURCE_SUPPORTED | last: run 3
U-011 | Randomly Sampled Principle Critique-Revision Loop | SOURCE_SUPPORTED | last: run 3
U-012 | Reflection Records with Evidence Pointers in a Shared Memory Stream | SOURCE_SUPPORTED | last: run 3

CANDIDATE LEDGER
CANDIDATE_ID | STATE | UNIT_ID | LAST_CHANGE | REASON
C-001 | UNITIZED | U-001 | run 1 NEW | odrębny mechanizm zastępowania sąsiednich notatek z osobnym polem treści oryginalnej
C-002 | UNITIZED | U-002 | run 1 NEW | odrębny mechanizm wyboru operacji na pamięci dla faktu z ekstrakcji
C-003 | UNITIZED | U-010 | run 3 NEW | odrębna pętla generacja–informacja zwrotna–rewizja z jednym modelem w trzech rolach i historią w prompcie
C-004 | UNITIZED | U-003 | run 1 NEW | odrębny mechanizm ograniczonego bufora refleksji dopisywanej po próbach
C-005 | UNITIZED | U-011 | run 3 NEW | odrębna pętla krytyka–rewizja z losowaną zasadą z listy autorów
C-006 | UNITIZED | U-012 | run 3 NEW | odrębna struktura rekordów refleksji ze wskaźnikami do rekordów cytowanych
C-007 | UNITIZED | U-006 | run 2 NEW | odrębny mechanizm wyznaczania wymogu kondensacji i ścieżki awaryjnej; obejmuje leady „OpenHands · kondensacja kontekstu" i „OpenHands · ręczne żądanie kondensacji"
C-008 | UNITIZED | U-004 | run 2 CORRECTS | odrębny mechanizm dziennika tylko do dopisywania z widokiem pochodnym; po odczycie kodu Unit skorygowano i rozszerzono
C-009 | UNITIZED | U-008 | run 2 NEW | odrębny schemat najmniejszego zestawu typów i relacji pochodzenia
C-010 | UNITIZED | U-009 | run 2 NEW | odrębny mechanizm unieważniania faktu z zachowaniem epizodu źródłowego
C-011 | UNITIZED | U-005 | run 1 NEW | odrębny mechanizm przerwania z zapisem stanu i restartem węzła przy wznowieniu
C-012 | NOT_PROBED | - | run 3 NOT_PROBED | LEAD_UNRESOLVED: tekst pierwotny (Sun, Merrill, Peterson 2001, Cognitive Science) nieotwarty; PDF autora odrzucony przez narzędzie odczytu, a rozdział Purdue CCN opisuje CLARION bez mechanizmu ekstrakcji reguł
C-013 | UNITIZED | U-007 | run 2 NEW | odrębny algorytm wyboru zakresu zapominania z chronioną głową i granicami jednostek atomowych; kandydat odnaleziony przy pogłębianiu C-007

REJECTED INFERENCES
- pytanie z wejścia, czy kolejna iteracja Self-Refine poprawia, a nie tylko wygładza, ≠ twierdzenie źródła; Tabela 2 porównuje rodzaje informacji zwrotnej na wynikach zadań i tego pytania nie rozstrzyga
- brak opisu nadpisania zasady przez użytkownika w odczytanej treści Constitutional AI ≠ brak takiego mechanizmu w systemie wdrożonym
- sformułowanie „drugi typ pamięci" w Generative Agents ≠ istnienie pola typu w zapisie rekordu
- obecność wskaźników do cytowanych rekordów w refleksji ≠ zgodność treści refleksji z tymi rekordami
- wzmianka o CLARION w rozdziale o implicit cognition ≠ opis mechanizmu CLARION; mechanizm nie został odczytany

AUDIT DELTA
- I1: każdy z 13 kandydatów ma wiersz w ledgerze; w Runie 3 nazwano 4 kandydatów (C-003, C-005, C-006, C-012) i pogłębiono 3 z 5 dozwolonych
- odczyt trzech prac przez narzędzie zwracające streszczenie; numery równań, sekcji i tabel niezweryfikowane na surowym tekście; wartości liczbowe tabel Self-Refine pominięte w Unicie
- C-012: dwie próby (PDF autora, rozdział Purdue CCN) nie dały lokalizacji mechanizmu w otwartym materiale; stan NOT_PROBED bez zmiany, zmieniony REASON
- Unity U-010, U-011, U-012 mają warstwę DOCUMENTED_DESIGN; żaden z nich nie ma warstwy IMPLEMENTED_STRUCTURE
- SEAM_QUESTION w wejściu zawierają hipotezy i oceny autora; nie weszły do pól SOURCE ani EXTRACT

SOURCE_GATE: CONTINUE
GATE_BASIS: 20 leadów z wejścia nie przeszło PROBE, a C-012 ma stan NOT_PROBED.

SYNTHESIS
OBSERVATION: w U-010 kryterium w kroku informacji zwrotnej wyznacza ten sam model, a jedynym warunkiem stopu niezależnym od modelu w odczytanym opisie jest limit iteracji.
OBSERVATION: w U-011 lista zasad jest tekstem napisanym przez autorów i losowanym w każdym kroku; odczytana treść nie wskazuje miejsca, w którym użytkownik zmienia zasadę.
OBSERVATION: w U-012 refleksja leży w tym samym strumieniu co obserwacje i zawiera wskaźniki do cytowanych rekordów.
INFERENCE: wskaźnik od rekordu pochodnego do źródła ma U-012 (wskaźniki do cytowanych rekordów), U-009 (`episodes`) i U-004 (`forgotten_event_ids` w `Condensation`); w opisach U-003 i U-010 takiego wskaźnika nie wymieniono.
HYPOTHESIS: lista cytowanych rekordów w U-012 mogłaby pełnić funkcję relacji `wasDerivedFrom` z U-008; zgodność nie została sprawdzona poza opisem pól.
TRANSFER: DATA_STRUCTURE z U-012: rekord pochodny z listą identyfikatorów cytowanych rekordów, zapisany w tym samym pliku co rekordy surowe.
OPEN_QUESTION: czy rekord refleksji w implementacji Generative Agents ma osobne pole typu.
OPEN_QUESTION: czy wskaźnik stopu w implementacji Self-Refine jest parsowany z tekstu informacji zwrotnej, czy ustalany stałą.
ASSESSMENT: kolejny Run: kod openhands-sdk 1.51.0 jest już otwarty, więc lead „OpenHands · analizator i polityka potwierdzeń" można sprawdzić bez nowego materiału; C-012 wymaga tekstu pierwotnego CLARION.
