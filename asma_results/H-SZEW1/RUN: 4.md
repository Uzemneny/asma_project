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
  - RAPTOR paper (arXiv 2401.18059)
  - HippoRAG paper, abstrakt (arXiv 2405.14831)
  - DSPy paper, abstrakt (arXiv 2310.03714)
  - OpenHands Docs (docs.openhands.dev)
  - OpenHands SDK, pakiet openhands-sdk 1.51.0 (rejestr PyPI)
  - W3C PROV-Overview (Working Group Note, 2013-04-30)
  - W3C PROV-DM
  - Zep paper (arXiv 2501.13956 v1)
  - Graphiti, pakiet graphiti-core 0.30.2 (rejestr PyPI)
  - LangGraph Docs (docs.langchain.com)
  - Claude Code Docs (code.claude.com): permissions, checkpointing
  - OpenAI Model Spec, wersja 2026-08-18
  - KurrentDB Docs (docs.kurrent.io): strona główna, concepts
  - River Docs (riverml.xyz): przegląd modułu drift
  - LangSmith Docs (docs.langchain.com): evaluation concepts
  - Rozdział o implicit cognition (Purdue CCN, chap_3.pdf), opisujący CLARION skrótowo
RUN: 4
FOCUS: kto ustala próg zatrzymania i jak człowiek może go przesunąć (Claude Code, OpenHands, OpenAI Model Spec) oraz droga od streszczenia do źródła (RAPTOR)
INPUT_MODE: SOURCE_ONLY
DEPTH_BUDGET: TARGETED
DATE: 2026-10-04
ACCESS_LIMITATIONS:
  - strony Claude Code Docs (permissions, checkpointing) odczytane jako tekst strony; RAPTOR paper, OpenAI Model Spec, KurrentDB Docs, River Docs, LangSmith Docs oraz abstrakty HippoRAG i DSPy odczytane przez narzędzie zwracające streszczenie; numery sekcji i cytaty z tych odczytów nie zostały sprawdzone na surowym tekście
  - kod OpenHands SDK odczytany z pakietu openhands-sdk 1.51.0 (rejestr PyPI), jak w Runie 2; moduły `ensemble.py`, `defense_in_depth`, `grayswan` i `toolshield_*` nieczytane
  - adres https://model-spec.openai.com/ zwraca przekierowanie; odczytano wersję 2026-08-18
  - KurrentDB Docs: odczytano stronę główną i `getting-started/concepts.html`; strony o projekcjach, usuwaniu strumieni i scavengingu nieotwarte
  - HippoRAG i DSPy: otwarto tylko strony abstraktów arXiv
  - ograniczenia Runów 1–3 dotyczące materiału nieotwieranego w tym Runie pozostają w mocy
TARGET_PROFILE:
  id: SZEW-TECHNIKA-CZLOWIEK (wejście nie nadaje identyfikatora; nazwa z nagłówka pliku)
  version: UNKNOWN
  target: neuralcore jako interfejs dostrojony do człowieka (pole ZASADA; pole TARGET w wejściu nie występuje)

SOURCE MAP
REGION | LOCATOR | SIGNAL
RAPTOR paper | https://arxiv.org/pdf/2401.18059, §3 | fragmenty jako liście, streszczenia klastrów jako węzły nadrzędne, indeksy dzieci w węzłach, dwie strategie wyszukiwania
HippoRAG paper, abstrakt | https://arxiv.org/abs/2405.14831 | triple z LLM w grafie wiedzy, Personalized PageRank
DSPy paper, abstrakt | https://arxiv.org/abs/2310.03714 | sygnatury, moduły i optymalizatory kompilujące program względem metryki
KurrentDB Docs | https://docs.kurrent.io/getting-started/concepts.html | dziennik zdarzeń tylko do dopisywania, niezmienność zdarzeń, strumienie, kontrola współbieżności optymistycznej
Claude Code Docs, permissions | https://code.claude.com/docs/en/permissions, sekcje Permission system, Manage permissions, Permission modes, Settings precedence, Managed settings, Extend permissions with hooks | reguły deny, ask, allow, tryby uprawnień, zakresy ustawień
Claude Code Docs, checkpointing | https://code.claude.com/docs/en/checkpointing, sekcje How checkpoints work, Limitations | checkpoint przed każdą turą, `/rewind`, wyłączenia
OpenHands SDK, bezpieczeństwo | openhands-sdk 1.51.0, openhands/sdk/security/analyzer.py, llm_analyzer.py, confirmation_policy.py, risk.py; agent/agent.py; settings/model.py; conversation/impl/local_conversation.py | `SecurityAnalyzerBase`, `LLMSecurityAnalyzer`, `ConfirmRisky`, `_requires_user_confirmation`
OpenAI Model Spec | https://model-spec.openai.com/2026-08-18.html, sekcje The chain of command, Respect the letter and spirit of instructions | poziomy władzy, wytyczne nadpisywalne niejawnie
River Docs | https://riverml.xyz/latest/api/overview/ | moduł drift z detektorami ADWIN, KSWIN, PageHinkley
LangSmith Docs | https://docs.langchain.com/langsmith/evaluation-concepts | zbiory przykładów, ewaluatory, ocena offline i online, kolejki anotacji
UNKNOWN_REGIONS:
  - grupa PRAKTYKA CZŁOWIEKA I JEJ MECHANIZACJA, leady nienazwane jako kandydaci: Zettelkasten systems, Memex, Personal Knowledge Graphs
  - grupa GDZIE SZEW PRZECIEKA, leady nienazwane jako kandydaci: AlphaEvolve, FunSearch, Darwin Gödel Machine
  - grupa CO TRZYMA SZEW, lead nienazwany jako kandydat: MemoryBank
  - grupa KLIMAT JAKO TRYB, leady nienazwane jako kandydaci: CAPS, Emotion Machine, MicroPsi / MicroPsi 2, Companions
  - pozostałe moduły analizatorów w openhands-sdk (`ensemble.py`, `defense_in_depth`, `grayswan`, `toolshield_*`)
  - strony KurrentDB o projekcjach, usuwaniu strumieni i scavengingu
  - etap uczenia z preferencji modelu (RLAIF) w Constitutional AI, §4
OUTSIDE_SCOPE:
  - pola i pytania z bloku PROBES_OUTSIDE_CORPUS
  - zachowanie systemów w czasie wykonania

DELTA
NEW
UNIT_ID: U-013
NAME: Summary Tree with Child Pointers to Source Chunks
LENS: LENS_KNOWLEDGE
TYPE: data_structure
STATUS: SOURCE_SUPPORTED
FUNCTION: Fragmenty tekstu są liśćmi drzewa; klastry węzłów są streszczane przez LLM w węzły nadrzędne, a każdy węzeł nadrzędny przechowuje indeksy swoich dzieci, więc od każdego poziomu abstrakcji istnieje droga do liści; rekurencja trwa do niemożności dalszego klastrowania.
MINIMAL_FORM:
  - węzeł: tekst (fragment albo streszczenie), osadzenie SBERT, indeksy dzieci
  - budowa: fragmenty (około 100 tokenów, granice zdań zachowane) → osadzenia → klastrowanie GMM z redukcją UMAP, dwustopniowe (globalne, potem lokalne) → streszczenie klastra przez LLM → węzły nadrzędne → powtórzenie
  - wyszukiwanie: przejście po drzewie (od korzenia, top-`k` na warstwie) albo spłaszczone drzewo (jedna warstwa, wybór do progu około 2000 tokenów)
SOURCE_ANCHOR:
  - source: RAPTOR paper (arXiv 2401.18059)
    locator: https://arxiv.org/pdf/2401.18059
    anchor: §3 (budowa drzewa, przechowywane pola węzła, strategie wyszukiwania)
    revision: UNKNOWN
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: DOCUMENTED_DESIGN
DEPENDENCIES:
  - enkoder SBERT
  - LLM streszczający klastry (według odczytu gpt-3.5-turbo)
EFFECT_STATUS: UNKNOWN
TRANSFER_FORM: DATA_STRUCTURE, DESIGN_PRINCIPLE
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: od węzła streszczenia da się zejść do liści po indeksach dzieci; to odpowiedź na pytanie wejścia o drogę z powrotem do oryginalnych zdań
  - dotyczy ANTI-GOALS profilu: w wariancie spłaszczonego drzewa węzły streszczeń i fragmenty oryginalne konkurują w jednej warstwie wyszukiwania; według odczytu kontekst dla modelu jest konkatenacją tekstów wybranych węzłów
UNKNOWN:
  - evidence: czy węzeł ma pole oznaczające warstwę albo typ (liść, streszczenie); odczytano trzy pola (tekst, osadzenie, indeksy dzieci)
  - evidence: czy kontekst przekazany modelowi zawiera oznaczenie, które węzły są streszczeniami; według odczytu bez jawnego pokazania relacji dzieci
  - dependency: kod nieotwarty
LIMITS:
  - odczyt przez narzędzie zwracające streszczenie; wartości (100 tokenów, 2000 tokenów, współczynnik klastrowania) niezweryfikowane na surowym tekście
  - praca podaje przewagę wyszukiwania spłaszczonego drzewa; efekt samej drogi do źródła nie był odczytany
RELATES_TO:
  - U-004
  - U-012

NEW
UNIT_ID: U-014
NAME: Ordered Deny-Ask-Allow Rules with Scope Precedence
LENS: LENS_ARTIFACT, LENS_SYSTEM
TYPE: process_constraint
STATUS: SOURCE_SUPPORTED
FUNCTION: Każde wywołanie narzędzia jest rozstrzygane regułami w kolejności `deny`, `ask`, `allow`, a pierwsze dopasowanie decyduje; reguły pochodzą z wielu zakresów ustawień, `deny` z dowolnego zakresu wygrywa z `allow`, a tryb uprawnień zmienia, które wywołania pytają użytkownika.
MINIMAL_FORM:
  - reguły `Allow` (bez zatwierdzania), `Ask` (pytanie przy każdym użyciu), `Deny` (zakaz); kolejność oceny `Deny` → `Ask` → `Allow`; swoistość reguły nie zmienia kolejności
  - zakresy: ustawienia użytkownika, projektu i zarządzane (najwyższe); `Deny` z dowolnego zakresu przeważa nad `Allow`; żaden poziom, w tym argument wiersza poleceń, nie nadpisuje zarządzanej reguły
  - tryby (`defaultMode`): `default`, `acceptEdits`, `plan`, `auto` (klasyfikator w tle), `dontAsk`, `bypassPermissions`; `permissions.disableBypassPermissionsMode` i `permissions.disableAutoMode` blokują dwa tryby
  - domyślne zatwierdzanie według typu narzędzia: odczyt w katalogu roboczym bez pytania; Bash z wyjątkiem wbudowanego zbioru poleceń tylko do odczytu, edycja plików i wyszukiwanie w sieci z pytaniem
  - hook `PreToolUse`: jego decyzja nie omija reguł `deny` i `ask`; hook kończący się kodem 2 przeważa nad regułą `allow`
  - `/permissions` zmienia regułę od następnego wywołania narzędzia w tej samej turze
SOURCE_ANCHOR:
  - source: Claude Code Docs (code.claude.com)
    locator: https://code.claude.com/docs/en/permissions
    anchor: Permission system, Manage permissions, Permission modes, Settings precedence, Managed settings, Extend permissions with hooks
    revision: UNKNOWN
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: DOCUMENTED_DESIGN
DEPENDENCIES:
  - pliki ustawień w zakresach użytkownika, projektu i zarządzanym
MUST_BE_TRUE: reguły są dopasowywane do wywołania przed wykonaniem narzędzia
ENFORCEMENT: RUNTIME_CONSTRAINED
EFFECT_STATUS: NOT_APPLICABLE
TRANSFER_FORM: PROCESS_RULE, WORKFLOW
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: o tym, czy system pyta, decydują typ narzędzia, reguła i tryb; człowiek przesuwa próg przez `/permissions` i `defaultMode`, a poziom zarządzany jest nadrzędny wobec użytkownika
  - dotyczy ANTI-GOALS profilu: w dokumentacji decyzja o pytaniu nie zależy od odwracalności operacji
UNKNOWN:
  - evidence: zachowanie w czasie wykonania nie było obserwowane
  - evidence: sposób działania klasyfikatora w trybie `auto` poza stroną permissions nieotwarty
LIMITS:
  - reguły `Read` i `Edit` typu `deny` nie obejmują polecenia, które czyta pliki bez ich nazwania, ani procesów pośrednich; według dokumentacji ochronę na poziomie systemu daje piaskownica
  - reguła `Deny` dla Bash nie dopasowuje tego samego programu wywołanego przez ścieżkę ani wewnątrz `sh -c`
  - reguły dopasowują wzorce; dokumentacja nie opisuje sprawdzania skutków operacji
RELATES_TO:
  - U-015
  - U-016

NEW
UNIT_ID: U-015
NAME: Per-Prompt File-Edit Checkpoints with Selective Rewind
LENS: LENS_ARTIFACT, LENS_SYSTEM
TYPE: mechanism
STATUS: SOURCE_SUPPORTED
FUNCTION: Przed każdą turą rozpoczętą promptem zapisywany jest checkpoint stanu plików edytowanych narzędziami edycji; `/rewind` przywraca kod, rozmowę albo oba, a opcje streszczania kompresują rozmowę bez zmiany plików i bez usuwania oryginalnych wiadomości z transkryptu sesji.
MINIMAL_FORM:
  - checkpoint = stan plików przed promptem rozpoczynającym turę; zapisywany razem z rozmową
  - migawki plików dla 100 ostatnich checkpointów; sprzątanie po około 30 dniach (`cleanupPeriodDays`)
  - menu `/rewind`: przywróć kod i rozmowę; przywróć rozmowę; przywróć kod; streść od tego miejsca; streść do tego miejsca
  - poza zakresem: zmiany plików z poleceń Bash, edycje większości subagentów, zmiany zewnętrzne, dowiązania symboliczne i twarde, wiadomości dołączone w trakcie tury
SOURCE_ANCHOR:
  - source: Claude Code Docs (code.claude.com)
    locator: https://code.claude.com/docs/en/checkpointing
    anchor: How checkpoints work, Rewind and summarize, Limitations
    revision: UNKNOWN
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: DOCUMENTED_DESIGN
EFFECT_STATUS: NOT_APPLICABLE
TRANSFER_FORM: WORKFLOW, PROCESS_RULE
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: odwracalność jest tu mechanizmem po fakcie, odrębnym od decyzji o pytaniu (U-014), i obejmuje pliki edytowane narzędziami edycji; zmiana pliku wykonana poleceniem Bash nie ma checkpointu
  - dotyczy ANTI-GOALS profilu: opcja streszczenia zostawia pliki bez zmian, a oryginalne wiadomości w transkrypcie; to ten sam podział surowa warstwa i widok pochodny co w U-004
UNKNOWN:
  - evidence: zachowanie w czasie wykonania nie było obserwowane
LIMITS:
  - dokumentacja nazywa checkpointy ochroną na poziomie sesji, a nie zamiennikiem kontroli wersji
  - przywrócenie checkpointu, którego migawki zostały usunięte, może się nie powieść
RELATES_TO:
  - U-004
  - U-014

NEW
UNIT_ID: U-016
NAME: Risk-Threshold Confirmation Policy Separated from Risk Analyzer
LENS: LENS_ARTIFACT, LENS_SYSTEM
TYPE: mechanism
STATUS: SOURCE_SUPPORTED
FUNCTION: Analizator przypisuje akcji poziom ryzyka (`LOW`, `MEDIUM`, `HIGH`, `UNKNOWN`), a odrębna polityka potwierdzeń (`AlwaysConfirm`, `NeverConfirm`, `ConfirmRisky`) decyduje, czy wykonanie zatrzymuje się w stanie `WAITING_FOR_CONFIRMATION`; w `LLMSecurityAnalyzer` poziom ryzyka jest wartością zadeklarowaną przez LLM agenta w argumencie wywołania narzędzia.
MINIMAL_FORM:
  - `risk` = `analyzer.security_risk(action)`; brak analizatora → `UNKNOWN`; błąd analizy → `HIGH`
  - `LLMSecurityAnalyzer.security_risk(action)` = `action.security_risk`; pole `security_risk` wypełnia LLM w argumentach wywołania i jest uwzględniane tylko przy skonfigurowanym analizatorze; pominięcie albo narzędzie tylko do odczytu → `UNKNOWN`
  - `ConfirmRisky(threshold=HIGH, confirm_unknown=True)`: `UNKNOWN` → `confirm_unknown`; w innym wypadku `risk.is_riskier(threshold)` (relacja zwrotna, więc poziom równy progowi też wymaga potwierdzenia); próg `UNKNOWN` odrzucany walidatorem
  - `_requires_user_confirmation`: pojedyncze `FinishAction` albo `ThinkAction` nigdy nie wymaga potwierdzenia; gdy `should_confirm` zwróci `True` dla którejkolwiek akcji z partii → `execution_status` = `WAITING_FOR_CONFIRMATION`
  - polityka stanu rozmowy domyślnie `NeverConfirm`; zmiana przez `set_confirmation_policy` (rozmowa lokalna i zdalna, ścieżka `confirmation_policy`); `reject_pending_actions(reason)` odrzuca oczekujące akcje
  - mapowanie ustawień: bez `confirmation_mode` → `NeverConfirm`; z analizatorem `llm` → `ConfirmRisky`; w pozostałych przypadkach `AlwaysConfirm`
SOURCE_ANCHOR:
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/security/confirmation_policy.py, analyzer.py, llm_analyzer.py, risk.py
    anchor: ConfirmationPolicyBase, ConfirmRisky, SecurityAnalyzerBase.analyze_pending_actions, LLMSecurityAnalyzer.security_risk, SecurityRisk.is_riskier
    revision: 1.51.0
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/agent/agent.py, settings/model.py, conversation/impl/local_conversation.py
    anchor: Agent._requires_user_confirmation, Agent._extract_security_risk, ConversationSettings._build_confirmation_policy, set_confirmation_policy, reject_pending_actions
    revision: 1.51.0
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: IMPLEMENTED_STRUCTURE
DEPENDENCIES:
  - analizator bezpieczeństwa skonfigurowany w stanie rozmowy
  - LLM agenta wypełniający `security_risk` (dla `LLMSecurityAnalyzer`)
MUST_BE_TRUE: polityka potwierdzeń jest ustawiona w stanie rozmowy
ENFORCEMENT: RUNTIME_CONSTRAINED
EFFECT_STATUS: NOT_APPLICABLE
TRANSFER_FORM: PROCESS_RULE, DESIGN_PRINCIPLE
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: próg decyzji leży w obiekcie polityki ustawianym przez wywołującego, a ocena ryzyka jest osobnym krokiem; odpowiedź na pytanie wejścia, kto ustala próg: wywołujący przez `ConfirmRisky.threshold` i `set_confirmation_policy`
  - dotyczy ANTI-GOALS profilu: w `LLMSecurityAnalyzer` ocenę ryzyka wyznacza ten sam model, który proponuje akcję
UNKNOWN:
  - evidence: czy końcowy użytkownik aplikacji może przesunąć próg; kod SDK udostępnia `set_confirmation_policy`, a warstwa interfejsu użytkownika nie była czytana
  - evidence: sposób wyznaczania ryzyka w analizatorach z `ensemble.py`, `defense_in_depth`, `grayswan` i `toolshield_*` nieczytany
LIMITS:
  - metoda `SecurityAnalyzerBase.should_require_confirmation` zawiera osobną logikę progu (HIGH zawsze, UNKNOWN bez trybu potwierdzeń); w przeszukanym kodzie SDK nie ma jej wywołań
  - zachowanie w czasie wykonania nie było obserwowane
RELATES_TO:
  - U-014
  - U-006

NEW
UNIT_ID: U-017
NAME: Authority-Ordered Instruction Hierarchy with Implicitly Overridable Guidelines
LENS: LENS_ARTIFACT
TYPE: design_principle
STATUS: SOURCE_SUPPORTED
FUNCTION: Instrukcje mają poziomy władzy (`Root`, `System`, `Developer`, `User`, `Guideline`, `No Authority`); instrukcja wyższego poziomu przeważa nad niższą, zasady poziomu `Root` nie są nadpisywalne, a wytyczne domyślne (w tym ton i styl) mogą być nadpisane niejawnie; wiadomości asystenta, wyniki narzędzi i tekst cytowany nie mają władzy z samej treści.
MINIMAL_FORM:
  - poziomy od najwyższego: `Root`, `System`, `Developer`, `User`; poniżej `Guideline` (nadpisywalny niejawnie) i `No Authority`
  - konflikt dwóch zasad `Root` → model domyślnie nie działa
  - wytyczne („Be warm", „Be conversational", „Use appropriate style") są domyślnymi wytycznymi poziomu `Guideline`
  - zasada „respect the letter and spirit of instructions": litera i duch instrukcji, nie samo dosłowne brzmienie
SOURCE_ANCHOR:
  - source: OpenAI Model Spec, wersja 2026-08-18
    locator: https://model-spec.openai.com/2026-08-18.html
    anchor: The chain of command, Respect the letter and spirit of instructions
    revision: 2026-08-18
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: DOCUMENTED_DESIGN
ENFORCEMENT: UNKNOWN
EFFECT_STATUS: UNKNOWN
TRANSFER_FORM: DESIGN_PRINCIPLE, SCHEMA
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: odpowiedź na pytanie wejścia, czy spec oddziela zasady od tonu: według odczytu oddziela poziomami władzy (reguły w `Root` i `System`, ton w `Guideline`)
  - dotyczy ANTI-GOALS profilu: w odczytanych sekcjach brak opisu mechanizmu, który chroniłby sformułowanie użytkownika przed przepisaniem; wytyczne tonu są nadpisywalne niejawnie przez kontekst
UNKNOWN:
  - evidence: dokładny tekst sekcji o dopasowaniu stylu do rozmówcy i granica takiego dopasowania
  - evidence: sposób egzekwowania hierarchii w modelu; spec opisuje zachowanie, a nie mechanizm
LIMITS:
  - odczyt przez narzędzie zwracające streszczenie; nazwy poziomów i cytaty niezweryfikowane na surowym tekście
  - według odczytu spec nie podaje jawnej listy rzeczy, które użytkownik może zmienić w wytycznych
RELATES_TO:
  - U-014
  - U-016

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
U-013 | Summary Tree with Child Pointers to Source Chunks | SOURCE_SUPPORTED | last: run 4
U-014 | Ordered Deny-Ask-Allow Rules with Scope Precedence | SOURCE_SUPPORTED | last: run 4
U-015 | Per-Prompt File-Edit Checkpoints with Selective Rewind | SOURCE_SUPPORTED | last: run 4
U-016 | Risk-Threshold Confirmation Policy Separated from Risk Analyzer | SOURCE_SUPPORTED | last: run 4
U-017 | Authority-Ordered Instruction Hierarchy with Implicitly Overridable Guidelines | SOURCE_SUPPORTED | last: run 4

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
C-014 | DEFER | - | run 4 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto tylko abstrakt arXiv 2405.14831, sposób tworzenia i oznaczania połączeń w grafie nieodczytany
C-015 | DEFER | - | run 4 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto tylko abstrakt arXiv 2310.03714, sposób definiowania metryki i jej weta nieodczytany
C-016 | UNITIZED | U-013 | run 4 NEW | odrębna struktura drzewa streszczeń z indeksami dzieci w węzłach
C-017 | DEFER | - | run 4 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto stronę główną i `concepts.html` KurrentDB, odtwarzanie stanu i usuwanie strumieni nieodczytane
C-018 | UNITIZED | U-014 | run 4 NEW | odrębny mechanizm kolejności reguł deny, ask, allow z pierwszeństwem zakresów
C-019 | UNITIZED | U-016 | run 4 NEW | odrębny mechanizm rozdzielenia oceny ryzyka od polityki potwierdzeń
C-020 | UNITIZED | U-017 | run 4 NEW | odrębna hierarchia poziomów władzy instrukcji z nadpisywalnymi wytycznymi
C-021 | DEFER | - | run 4 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto tylko stronę przeglądu modułu drift, sposób zasilania detektora i okno odniesienia nieodczytane
C-022 | DEFER | - | run 4 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto tylko stronę evaluation concepts, kolejki anotacji i porównanie eksperymentów nieodczytane
C-023 | UNITIZED | U-015 | run 4 NEW | odrębny mechanizm checkpointów plików i rewind; kandydat odnaleziony przy pogłębianiu C-018

REJECTED INFERENCES
- opis FUNCTION_PRIOR dla C-018 („authorization + reversibility checks przed operacją") ≠ opis w dokumentacji: o pytaniu decydują typ narzędzia, reguła i tryb, a checkpointy są osobnym mechanizmem po fakcie, bez zmian z poleceń Bash
- nazwa `LLMSecurityAnalyzer` ≠ niezależna ocena ryzyka: metoda zwraca wartość `security_risk` zadeklarowaną przez LLM agenta w wywołaniu narzędzia
- istnienie indeksów dzieci w węzłach RAPTOR ≠ widoczność relacji dzieci dla modelu przy odpowiedzi; według odczytu kontekst jest konkatenacją tekstów wybranych węzłów
- poziom `Guideline` dla tonu w Model Spec ≠ ochrona sformułowań użytkownika; odczytane sekcje takiej ochrony nie opisują
- sformułowania „append-only" i „immutable" na stronie concepts KurrentDB ≠ rozstrzygnięcie pytania o wersję bez bazy; strony o odtwarzaniu stanu i usuwaniu strumieni nieotwarte
- abstrakty HippoRAG i DSPy ≠ odpowiedź na pytania z wejścia o autora połączeń i o definiującego metrykę; pytania pozostają otwarte

AUDIT DELTA
- I1: każdy z 23 kandydatów ma wiersz w ledgerze; w Runie 4 nazwano 10 kandydatów (C-014–C-023) z limitu 12 i pogłębiono 5 (C-016, C-018, C-019, C-020, C-023)
- wybór pogłębień według B.8: reguła 3 (jawny potencjał transferu w leadzie) dla C-016, C-017, C-018; C-017 pogłębiono mniej niż pozostałych z reguły 4, bo wzorzec dziennika tylko do dopisywania jest już w U-004; remis między C-014, C-015, C-019, C-020, C-021 i C-022 rozstrzygnięto profilem (§43 pkt 2) na rzecz C-019 i C-020; w ledgerze pominięci mają kod BUDGET
- C-023 (checkpointy) odnaleziony przy pogłębianiu C-018 jako odrębny mechanizm
- Claude Code Docs odczytane jako tekst strony; pozostałe źródła nowe w tym Runie odczytane przez narzędzie zwracające streszczenie
- w kodzie 1.51.0 `LLMSecurityAnalyzer.security_risk` zwraca `action.security_risk`; `SecurityAnalyzerBase.should_require_confirmation` nie ma wywołań w przeszukanym kodzie SDK
- adres Model Spec zwrócił przekierowanie do wersji 2026-08-18; odczytano tę wersję
- w wejściu SEAM_QUESTION zawierają hipotezy i oceny autora; nie weszły do pól SOURCE ani EXTRACT

SOURCE_GATE: CONTINUE
GATE_BASIS: 11 leadów z wejścia nie przeszło PROBE, C-012 ma stan NOT_PROBED, a C-014, C-015, C-017, C-021 i C-022 mają stan DEFER.

SYNTHESIS
OBSERVATION: w U-016 poziom ryzyka dla `LLMSecurityAnalyzer` pochodzi z pola `security_risk` wypełnianego przez LLM agenta, a próg decyzji leży w obiekcie polityki (`ConfirmRisky.threshold`, domyślnie `HIGH`) ustawianym przez wywołującego.
OBSERVATION: w U-014 reguły są oceniane w kolejności `deny`, `ask`, `allow`; `deny` z dowolnego zakresu wygrywa z `allow`, a zakres zarządzany jest najwyższy.
OBSERVATION: w U-015 checkpointy obejmują edycje plików narzędziami edycji, zmiany z poleceń Bash nie są objęte, a streszczenie rozmowy zostawia oryginalne wiadomości w transkrypcie.
OBSERVATION: w U-017 ton i styl są domyślnymi wytycznymi poziomu `Guideline`, nadpisywalnymi niejawnie, a wiadomości asystenta, wyniki narzędzi i tekst cytowany nie mają władzy z samej treści.
OBSERVATION: w U-013 węzeł nadrzędny przechowuje indeksy dzieci.
INFERENCE: w odczytanym opisie U-014 i w kodzie U-016 odwracalność operacji nie jest kryterium decyzji o pytaniu: w U-014 kryterium to typ narzędzia, reguła i tryb, w U-016 poziom ryzyka deklarowany przez LLM.
INFERENCE: wzorzec „warstwa surowa zostaje, widok pochodny prowadzi do źródła" występuje w U-004 (zdarzenia), U-009 (`episodes`), U-012 (wskaźniki do cytowanych rekordów), U-013 (indeksy dzieci) i U-015 (transkrypt przy streszczeniu).
TRANSFER: PROCESS_RULE z U-014: kolejność deny → ask → allow z pierwszym dopasowaniem, reguły z wielu zakresów, w których deny wygrywa.
OPEN_QUESTION: czy analizatory z `ensemble.py`, `defense_in_depth`, `grayswan` i `toolshield_*` w openhands-sdk przypisują ryzyko niezależnie od wartości zadeklarowanej przez LLM.
OPEN_QUESTION: czy węzeł RAPTOR ma pole warstwy lub typu odróżniające liść od streszczenia.
ASSESSMENT: kolejny Run: C-014, C-015, C-017, C-021 i C-022 wymagają tekstów poza abstraktami i stronami przeglądowymi; 11 leadów bez nazwy (Zettelkasten systems, Memex, Personal Knowledge Graphs, AlphaEvolve, FunSearch, Darwin Gödel Machine, MemoryBank, CAPS, Emotion Machine, MicroPsi / MicroPsi 2, Companions) czeka na PROBE.
