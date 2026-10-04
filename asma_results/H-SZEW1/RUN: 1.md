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
  - Self-Refine paper, abstrakt (arXiv 2303.17651 v2)
  - Constitutional AI paper, abstrakt (arXiv 2212.08073 v1)
  - Generative Agents paper, abstrakt (arXiv 2304.03442 v2)
  - OpenHands Docs (docs.openhands.dev)
  - W3C PROV-Overview (Working Group Note, 2013-04-30)
  - Zep paper, abstrakt (arXiv 2501.13956 v1)
  - LangGraph Docs (docs.langchain.com)
RUN: 1
FOCUS: rozdział warstwy surowej od pochodnej w pamięci agentów: zapis, przepisywanie, kompresja i przerwanie przez człowieka
INPUT_MODE: SOURCE_ONLY
DEPTH_BUDGET: TARGETED
DATE: 2026-10-04
ACCESS_LIMITATIONS:
  - kod w repozytoriach nieotwarty; strony GitHub odrzucone przez narzędzie odczytu (ROBOTS_DISALLOWED); wszystkie Unity mają warstwę DOCUMENTED_DESIGN
  - dla Self-Refine, Constitutional AI, Generative Agents i Zep odczytano wyłącznie strony abstraktów arXiv
  - Mem0 paper: odczyt urwany w §4.5; Appendix B (Algorithm 1) nieodczytany
  - CLARION: tekst pierwotny nieotwarty; widoczne tylko fragmenty wyników wyszukiwania
  - 20 leadów z wejścia nie nazwano kandydatami w Runie 1 (limit 12 kandydatów dla TARGETED, §31); lista w UNKNOWN_REGIONS
  - zachowanie w czasie wykonania nie było obserwowane dla żadnego systemu
TARGET_PROFILE:
  id: SZEW-TECHNIKA-CZLOWIEK (wejście nie nadaje identyfikatora; nazwa z nagłówka pliku)
  version: UNKNOWN
  target: neuralcore jako interfejs dostrojony do człowieka (pole ZASADA; pole TARGET w wejściu nie występuje)

SOURCE MAP
REGION | LOCATOR | SIGNAL
TARGET_PROFILE | Wejście ASMA INPUT SZEW: TECHNIKA / CZŁOWIEK, blok TARGET_PROFILE | pola PROBLEM, ZASADA, CO MA WYJŚĆ, CZEGO NIE SZUKAĆ, ZASADA CZYTANIA; brak pól TARGET, id i version
PRAKTYKA CZŁOWIEKA I JEJ MECHANIZACJA | Wejście, grupa 1 | 6 leadów w 3 blokach SEAM_QUESTION; opisy FUNCTION_PRIOR jednolinijkowe
GDZIE SZEW PRZECIEKA | Wejście, grupa 2 | 11 leadów w 8 blokach SEAM_QUESTION
CO TRZYMA SZEW | Wejście, grupa 3 | 12 leadów, każdy z własnym blokiem SEAM_QUESTION
KLIMAT JAKO TRYB | Wejście, grupa 4 | 4 leady w 1 bloku SEAM_QUESTION
PROBES_OUTSIDE_CORPUS | Wejście, ostatni blok | 5 pytań i lista 5 pól; wejście opisuje pola jako nazwy do przeszukania, nie jako źródła
A-MEM paper | https://arxiv.org/html/2502.12110v11, §3.1–§3.3, Appendix B.1–B.3, Tabela 3, §6 | równania (1)–(7), trzy szablony promptów, ablacja `LG` i `ME`
Mem0 paper | https://arxiv.org/html/2504.19413v1, §2.1, §2.2, Tabela 1 | faza ekstrakcji i aktualizacji, cztery operacje, wariant `Mem0g`
Reflexion paper | https://arxiv.org/html/2303.11366v4, §3, §4.1–§4.3, §5, Appendix B.1 | Algorithm 1, trzy modele, pamięć ograniczona do `Ω` wpisów
Self-Refine paper, abstrakt | https://arxiv.org/abs/2303.17651 | pętla generacja, sprzężenie zwrotne, rewizja; jeden model w trzech rolach
Constitutional AI paper, abstrakt | https://arxiv.org/abs/2212.08073 | faza nadzorowana (krytyka i rewizja) oraz faza RL z preferencji modelu
Generative Agents paper, abstrakt | https://arxiv.org/abs/2304.03442 | strumień obserwacji, refleksja, planowanie
OpenHands Docs | https://docs.openhands.dev/sdk/arch/events, https://docs.openhands.dev/sdk/arch/condenser | dziennik zdarzeń tylko do dopisywania, zdarzenie `Condensation`, `View.from_events()`
W3C PROV-Overview | https://www.w3.org/TR/prov-overview/ | lista 12 dokumentów rodziny PROV; typy i relacje definiuje PROV-DM, nieotwarty
Zep paper, abstrakt | https://arxiv.org/abs/2501.13956 | graf wiedzy z uwzględnieniem czasu (Graphiti), zachowane relacje historyczne
LangGraph Docs | https://docs.langchain.com/oss/python/langgraph/interrupts | `interrupt()`, checkpointer, `Command(resume=...)`, reguły interrupts
UNKNOWN_REGIONS:
  - grupa PRAKTYKA CZŁOWIEKA I JEJ MECHANIZACJA, leady nienazwane jako kandydaci: Zettelkasten systems, Memex, HippoRAG / HippoRAG 2, Personal Knowledge Graphs
  - grupa GDZIE SZEW PRZECIEKA, leady nienazwane jako kandydaci: DSPy, RAPTOR, AlphaEvolve, FunSearch, Darwin Gödel Machine
  - grupa CO TRZYMA SZEW, leady nienazwane jako kandydaci: EventStoreDB, Claude Code · autoryzacja i odwracalność, OpenHands · analizator i polityka potwierdzeń, OpenAI Model Spec, River, LangSmith, MemoryBank
  - grupa KLIMAT JAKO TRYB, leady nienazwane jako kandydaci: CAPS, Emotion Machine, MicroPsi / MicroPsi 2, Companions
  - kod implementacji (repozytoria) wszystkich pięciu Unitów
OUTSIDE_SCOPE:
  - pola i pytania z bloku PROBES_OUTSIDE_CORPUS
  - zachowanie systemów w czasie wykonania

DELTA
NEW
UNIT_ID: U-001
NAME: Neighbor Note Rewrite on Insert
LENS: LENS_KNOWLEDGE
TYPE: mechanism
STATUS: SOURCE_SUPPORTED
FUNCTION: Przy dodaniu nowej notatki LLM wyznacza linki do najbliższych notatek i dla każdej z nich tworzy nową wersję kontekstu, słów kluczowych i tagów, która zastępuje wersję poprzednią; oryginalna treść interakcji `c_i` jest odrębnym polem notatki.
MINIMAL_FORM:
  - nowa interakcja `c_n` → LLM(`P_s1`) → `K_n`, `G_n`, `X_n`; `e_n` = `f_enc`(`c_n`, `K_n`, `G_n`, `X_n`)
  - top-`k` sąsiadów po cosinusie `e_n`·`e_j` (`k`=10 domyślnie) → LLM(`P_s2`) → zbiór linków `L_n`
  - dla każdego sąsiada `m_j`: LLM(`P_s3`) → `m_j*`; `m_j*` zastępuje `m_j` w `M`
  - schemat JSON wyjścia `P_s3`: `should_evolve`, `actions`, `suggested_connections`, `tags_to_update`, `new_context_neighborhood`, `new_tags_neighborhood`
SOURCE_ANCHOR:
  - source: A-MEM paper (arXiv 2502.12110 v11)
    locator: https://arxiv.org/html/2502.12110v11
    anchor: §3.1 Note Construction, §3.2 Link Generation, §3.3 Memory Evolution, równania (1)–(7), Appendix B.1–B.3, Tabela 3, §6 Limitations
    revision: v11 (2025-10-08)
  - source: Mem0 paper (arXiv 2504.19413 v1)
    locator: https://arxiv.org/html/2504.19413v1
    anchor: Tabela 1, wiersze A-Mem i A-Mem*
    revision: v1
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: DOCUMENTED_DESIGN
DEPENDENCIES:
  - enkoder tekstu `f_enc` (w eksperymentach all-minilm-l6-v2)
  - LLM wykonujący szablony `P_s1`, `P_s2`, `P_s3`
MUST_BE_TRUE: `M` zawiera notatki z polami `c_i`, `t_i`, `K_i`, `G_i`, `X_i`, `e_i`, `L_i`
BREAKS_IF_ISOLATED: ewolucja używa zbioru `M_near` z kroku wyszukiwania sąsiadów (równania 4–5); bez tego kroku równanie (7) nie ma zbioru wejściowego
ISOLATION_STATUS: DIRECT_INFERENCE
ENFORCEMENT: SCHEMA_CONSTRAINED
EFFECT_STATUS: TESTED_IN_SOURCE
TRANSFER_FORM: DATA_STRUCTURE, PROCESS_RULE
ADOPTION_NOTES:
  - dotyczy PROBLEMS i CONSTRAINTS profilu: pole `c_i` przechowuje oryginalną treść interakcji obok pól `K_i`, `G_i`, `X_i` generowanych przez LLM
  - dotyczy ANTI-GOALS profilu: zastąpienie `m_j` przez `m_j*` oznacza, że wartości `X`, `K`, `G` neutralnej notatki stają się słowami modelu; tekst nie opisuje losu poprzedniej wersji
UNKNOWN:
  - evidence: czy poprzednia wersja `m_j` jest zachowana po zastąpieniu
  - evidence: czy `e_j` jest przeliczane po ewolucji
  - dependency: kod A-mem-sys nieotwarty
LIMITS:
  - §3.3 podaje do aktualizacji kontekst, słowa kluczowe i tagi; §2.2 używa sformułowania o ewolucji „treści i relacji"; schemat JSON w `P_s3` nie ma pola treści
  - szablon `P_s3` w treści wymienia akcje `strengthen` i `update_neighbor`, a schemat JSON w tym samym szablonie wymienia `strengthen`, `merge`, `prune`
  - ablacja w Tabeli 3 obejmuje warianty „bez `LG` i `ME`" oraz „bez `ME`"; wariant z `ME` bez `LG` nie był testowany
  - wyniki Tabeli 3 dotyczą F1 i BLEU-1 na LoCoMo, nie zachowania brzmienia oryginału
  - zewnętrznie: Mem0 (Tabela 1) podaje ponowne uruchomienie A-Mem z niższym F1 niż w pracy A-MEM (single hop 20,76 wobec 27,02); przyczyny różnicy nie podano
  - §6: jakość organizacji zależy od możliwości modelu bazowego
RELATES_TO:
  - U-002

NEW
UNIT_ID: U-002
NAME: LLM-Selected Memory Operation per Extracted Fact
LENS: LENS_KNOWLEDGE
TYPE: mechanism
STATUS: SOURCE_SUPPORTED
FUNCTION: Dla każdego kandydata-faktu wyekstrahowanego przez LLM z pary wiadomości system wyszukuje podobne wpisy, a LLM wybiera przez wywołanie narzędzia jedną z operacji `ADD`, `UPDATE`, `DELETE`, `NOOP`; `DELETE` dotyczy wpisów sprzecznych z nowym faktem.
MINIMAL_FORM:
  - `P` = (`S`, ostatnie `m`=10 wiadomości, `m_{t-1}`, `m_t`) → LLM `φ` → zbiór kandydatów `Ω`; `S` odświeżane asynchronicznie
  - dla `ω_i`∈`Ω`: top `s`=10 podobnych wpisów (wektory) + `ω_i` → wywołanie narzędzia → `ADD` | `UPDATE` | `DELETE` | `NOOP`
  - `Mem0g`: wpis sprzeczny jest oznaczany jako nieważny, bez fizycznego usunięcia
SOURCE_ANCHOR:
  - source: Mem0 paper (arXiv 2504.19413 v1)
    locator: https://arxiv.org/html/2504.19413v1
    anchor: §2 Proposed Methods, §2.1 Mem0, §2.2 Mem0g
    revision: v1
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: DOCUMENTED_DESIGN
DEPENDENCIES:
  - baza wektorowa z wyszukiwaniem podobieństwa
  - LLM z interfejsem wywołań narzędzi (w pracy GPT-4o-mini)
MUST_BE_TRUE: istnieje podsumowanie rozmowy `S` pobierane z bazy
ENFORCEMENT: SCHEMA_CONSTRAINED
EFFECT_STATUS: CLAIMED
TRANSFER_FORM: PROCESS_RULE
ADOPTION_NOTES:
  - dotyczy ANTI-GOALS profilu: kandydaci są faktami wyekstrahowanymi przez LLM, a operacja `UPDATE` rozszerza istniejący wpis, co zmienia jego treść
  - dotyczy PROBLEMS profilu: w podstawowym Mem0 sprzeczność jest rozstrzygana operacją `DELETE`, a zachowanie obu wersji opisano tylko dla `Mem0g`
UNKNOWN:
  - evidence: czy wpis przechowuje oryginalne sformułowanie wypowiedzi użytkownika
  - evidence: wyniki per operacja (ablacja `ADD`/`UPDATE`/`DELETE`/`NOOP`)
  - dependency: Appendix B (Algorithm 1) i implementacja nieodczytane
LIMITS:
  - wyniki w pracy dotyczą całego potoku na LOCOMO bez kategorii adversarial; ablacji operacji w odczytanej części nie ma
  - wybór operacji należy do LLM; zbiór operacji ogranicza interfejs wywołania narzędzia
  - odczyt pracy urwany w §4.5
RELATES_TO:
  - U-001

NEW
UNIT_ID: U-003
NAME: Bounded Append-Only Verbal Reflection Buffer
LENS: LENS_KNOWLEDGE
TYPE: mechanism
STATUS: SOURCE_SUPPORTED
FUNCTION: Po każdej próbie model refleksji tworzy tekstowe podsumowanie z trajektorii, sygnału ewaluatora i bieżącej pamięci; wpis jest dopisywany do pamięci długoterminowej ograniczonej do `Ω` wpisów, a aktor w kolejnej próbie otrzymuje te wpisy w kontekście.
MINIMAL_FORM:
  - `τ_t` = trajektoria aktora `M_a`; `r_t` = `M_e`(`τ_t`); `sr_t` = `M_sr`(`τ_t`, `r_t`, `mem`)
  - `mem` ← [`sr_0`] po próbie 0; po każdej kolejnej próbie dopisz `sr_t` do `mem`; `|mem|` ≤ `Ω` (zwykle 1–3)
  - pętla trwa do uznania `τ_t` przez `M_e` za poprawną albo do limitu prób
  - warianty `M_e`: dopasowanie dokładne (HotPotQA), heurystyka (ALFWorld: ponad 3 powtórzenia tej samej akcji i odpowiedzi albo ponad 30 akcji), testy jednostkowe generowane przez model (kod, do 6 testów, filtr AST)
SOURCE_ANCHOR:
  - source: Reflexion paper (arXiv 2303.11366 v4)
    locator: https://arxiv.org/html/2303.11366v4
    anchor: §3 (Actor, Evaluator, Self-reflection, Memory, The Reflexion process), Algorithm 1, §4.1, §4.2, §4.3, §5 Limitations, Appendix B.1
    revision: v4 (2023-10-10)
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: DOCUMENTED_DESIGN
DEPENDENCIES:
  - ewaluator `M_e` (wariant zależny od zadania)
  - model refleksji `M_sr`
MUST_BE_TRUE: sygnał ewaluatora jest dostępny po każdej próbie
ENFORCEMENT: UNKNOWN
EFFECT_STATUS: TESTED_IN_SOURCE
TRANSFER_FORM: DATA_STRUCTURE, PROCESS_RULE
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: jedynym zapisem do `mem` w Algorithm 1 jest `sr_t` wygenerowane przez `M_sr`, czyli wpis jest warstwą modelu
  - dotyczy ANTI-GOALS profilu: opis pamięci nie podaje pola pochodzenia wpisu ani rozróżnienia od słów użytkownika
UNKNOWN:
  - evidence: czy implementacja oznacza pochodzenie wpisów w `mem`
  - dependency: repozytorium reflexion nieotwarte
LIMITS:
  - §5: pamięć długoterminowa jest oknem przesuwnym o maksymalnej pojemności
  - §1: skuteczność zależy od samoewaluacji LLM albo heurystyk, bez formalnej gwarancji
  - §4.3: fałszywie pozytywne wyniki testów generowanych przez model skracają pętlę; MBPP Python pozostaje poniżej bazowego pass@1 (Tabela 1)
  - Appendix B.1: brak poprawy na WebShop po czterech próbach
  - Appendix A: starchat-beta bez poprawy względem bazowego (0,26 i 0,26)
RELATES_TO:
  - U-004

NEW
UNIT_ID: U-004
NAME: Append-Only Event Log with Condensation as Filter Event
LENS: LENS_ARTIFACT, LENS_SYSTEM
TYPE: data_structure
STATUS: SOURCE_SUPPORTED
FUNCTION: Historia agenta jest dziennikiem zdarzeń tylko do dopisywania; kompresja kontekstu nie usuwa zdarzeń z dziennika, tylko dopisuje zdarzenie `Condensation` z `forgotten_event_ids`, streszczeniem i `summary_offset`, a widok dla LLM (`View`) jest liczony z dziennika przez `View.from_events()`.
MINIMAL_FORM:
  - `Event`: niemodyfikowalny model (id, timestamp, `source`∈{`user`, `agent`, `environment`}) → dopisywany do dziennika
  - `condense(view)` → `View` albo `Condensation`; `Condensation` (`forgotten_event_ids`, `summary`, `summary_offset`) → dopisane do dziennika
  - `View.from_events(events)`: odfiltruj `forgotten_event_ids`, wstaw streszczenie na `summary_offset` → wejście LLM
  - `source` (pochodzenie zdarzenia) i LLM `role` (reprezentacja dla modelu) są niezależne; `CondensationSummaryEvent` ma `source`=`environment` i `role`=`user`
SOURCE_ANCHOR:
  - source: OpenHands Docs (docs.openhands.dev)
    locator: https://docs.openhands.dev/sdk/arch/events
    anchor: Core Responsibilities, Event Types, `source` vs LLM `role`
    revision: UNKNOWN
  - source: OpenHands Docs (docs.openhands.dev)
    locator: https://docs.openhands.dev/sdk/arch/condenser
    anchor: LLMSummarizingCondenser (Process, Configuration), View and Condensation, Condensation Event
    revision: UNKNOWN
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: DOCUMENTED_DESIGN
DEPENDENCIES:
  - agent dopisujący `Condensation` do dziennika i wychodzący z kroku
  - LLM generujący streszczenie (w dokumentacji często tańszy model)
MUST_BE_TRUE: widok jest liczony z dziennika przy następnym kroku agenta
ENFORCEMENT: UNKNOWN
EFFECT_STATUS: NOT_APPLICABLE
TRANSFER_FORM: DATA_STRUCTURE, DESIGN_PRINCIPLE
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: dziennik jest warstwą surową, `View` warstwą pochodną, a pole `source` odróżnia zdarzenia pochodzące od użytkownika od komunikatów środowiska
  - dotyczy CONSTRAINTS profilu: wzorzec opisano bez bazy danych; stan wynika z dziennika zdarzeń
UNKNOWN:
  - evidence: mechanizm egzekwujący brak modyfikacji dziennika w warstwie zapisu nie został otwarty
  - evidence: zgłoszenie #5149 w repozytorium (widoczne tylko we fragmencie wyników wyszukiwania) wskazuje, że ścieżka `hard_context_reset` może streszczać także zdarzenie promptu systemowego; nieotwarte i niezweryfikowane
  - dependency: kod `view.py` i `llm_summarizing_condenser.py` nieotwarty
LIMITS:
  - w otwartych stronach dokumentacji nie opisano mechanizmu oznaczania zdarzeń jako niepodlegających zapomnieniu poza parametrem `keep_first` (domyślnie 4 pierwsze zdarzenia)
  - `CondensationRequest` jest zdarzeniem wewnętrznym niewidocznym dla LLM; wyzwala je agent po błędzie okna kontekstu albo kod aplikacji
  - streszczenie generuje LLM; wartości `max_size` (domyślnie 120) i `keep_first` są parametrami konfiguracji
  - strony opisują architekturę; zgodność z kodem nie została sprawdzona
RELATES_TO:
  - U-003

NEW
UNIT_ID: U-005
NAME: Checkpointed Interrupt with Node Restart on Resume
LENS: LENS_ARTIFACT, LENS_SYSTEM
TYPE: process_constraint
STATUS: SOURCE_SUPPORTED
FUNCTION: `interrupt()` zawiesza wykonanie grafu, checkpointer zapisuje stan pod `thread_id`, wartość z `interrupt()` trafia do wywołującego, a wznowienie przez `Command(resume=...)` uruchamia węzeł od początku; wartość wznowienia staje się wynikiem wywołania `interrupt()`.
MINIMAL_FORM:
  - wymagane: checkpointer, `thread_id` w konfiguracji, wywołanie `interrupt(payload)` z wartością serializowalną do JSON
  - `interrupt(v)` → zapis stanu → `v` do wywołującego → oczekiwanie bez limitu czasu
  - `Command(resume=x)` z tym samym `thread_id` → węzeł startuje od początku → `interrupt()` zwraca `x`
  - kilka `interrupt()` w jednym węźle: wartości wznowienia dopasowywane po indeksie wywołania
SOURCE_ANCHOR:
  - source: LangGraph Docs (docs.langchain.com)
    locator: https://docs.langchain.com/oss/python/langgraph/interrupts
    anchor: Pause using interrupt, Resuming interrupts, Rules of interrupts
    revision: UNKNOWN
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: DOCUMENTED_DESIGN
DEPENDENCIES:
  - checkpointer (w produkcji trwały)
  - stały `thread_id`
MUST_BE_TRUE: kolejność i liczba wywołań `interrupt()` w węźle jest taka sama przy każdym wykonaniu
BREAKS_IF_ISOLATED: bez checkpointera i `thread_id` wznowienie z zapisanego stanu nie jest możliwe
ISOLATION_STATUS: SOURCE_FACT
ENFORCEMENT: RUNTIME_CONSTRAINED
EFFECT_STATUS: NOT_APPLICABLE
TRANSFER_FORM: WORKFLOW, PROCESS_RULE
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: punkt przekazania kontroli człowiekowi z zapisem stanu i powrotem wartości człowieka jako wyniku wywołania
  - dotyczy ANTI-GOALS profilu: strona nie opisuje znacznika pochodzenia wartości wznowienia w zapisanym stanie
UNKNOWN:
  - evidence: czy stan po wznowieniu odróżnia wartość podaną przez człowieka od wartości wyliczonej
  - dependency: kod biblioteki nieotwarty
LIMITS:
  - kod przed `interrupt()` w węźle wykonuje się ponownie przy wznowieniu; efekty uboczne przed `interrupt()` powinny być idempotentne (zasada z dokumentacji)
  - dokumentacja zaleca: nie owijać `interrupt()` w gołe `try/except`, nie zmieniać kolejności wywołań; egzekwowanie tych zasad nie jest opisane
  - pętla `while True` z `interrupt()` odtwarza poprzednie iteracje przy każdym wznowieniu; dokumentacja zaleca krawędź warunkową
  - statyczne punkty przerwania (`interrupt_before`, `interrupt_after`) dokumentacja opisuje jako niezalecane dla przepływów z człowiekiem
RELATES_TO:
  - U-004

CANDIDATE LEDGER
CANDIDATE_ID | STATE | UNIT_ID | LAST_CHANGE | REASON
C-001 | UNITIZED | U-001 | run 1 NEW | odrębny mechanizm zastępowania sąsiednich notatek z osobnym polem treści oryginalnej
C-002 | UNITIZED | U-002 | run 1 NEW | odrębny mechanizm wyboru operacji na pamięci dla faktu z ekstrakcji
C-003 | DEFER | - | run 1 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto tylko abstrakt arXiv 2303.17651, źródło kryterium w kroku sprzężenia zwrotnego nieodczytane
C-004 | UNITIZED | U-003 | run 1 NEW | odrębny mechanizm ograniczonego bufora refleksji dopisywanej po próbach
C-005 | DEFER | - | run 1 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto tylko abstrakt arXiv 2212.08073, miejsce wejścia i zmiany zasad nieodczytane
C-006 | DEFER | - | run 1 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto tylko abstrakt arXiv 2304.03442, relacja refleksji do wpisów surowych nieodczytana
C-007 | DEFER | - | run 1 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; obejmuje leady „OpenHands · kondensacja kontekstu" i „OpenHands · ręczne żądanie kondensacji"; zdarzenie `Condensation` opisuje U-004, progi i wyzwalanie w kodzie nieopracowane
C-008 | UNITIZED | U-004 | run 1 NEW | odrębny mechanizm dziennika tylko do dopisywania z widokiem pochodnym
C-009 | DEFER | - | run 1 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto W3C PROV-Overview, typy i relacje z PROV-DM nieodczytane z tekstu normatywnego
C-010 | DEFER | - | run 1 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto tylko abstrakt arXiv 2501.13956, zapis unieważnienia relacji nieodczytany
C-011 | UNITIZED | U-005 | run 1 NEW | odrębny mechanizm przerwania z zapisem stanu i restartem węzła przy wznowieniu
C-012 | NOT_PROBED | - | run 1 NOT_PROBED | LEAD_UNRESOLVED: tekst pierwotny (Sun, Merrill, Peterson 2001, Cognitive Science) widoczny tylko we fragmencie wyników wyszukiwania, nie otwarty

REJECTED INFERENCES
- opis FUNCTION_PRIOR i pytanie SEAM_QUESTION z wejścia ≠ twierdzenie o źródle pierwotnym; pytania potraktowano jako wskazanie miejsca w źródle
- założenie z wejścia, że ewolucja w A-MEM przepisuje pierwotne brzmienie notatki, nie ma oparcia w odczytanym tekście; obecność osobnego pola `c_i` również nie dowodzi, że `c_i` pozostaje bez zmian po zastąpieniu `m_j` przez `m_j*`
- brak opisu pola pochodzenia wpisu w pamięci Reflexion ≠ brak tego pola w implementacji
- dokumentacja pola `source` w OpenHands ≠ egzekwowanie rozróżnienia pochodzenia w kodzie
- rola `user` zdarzenia `CondensationSummaryEvent` ≠ pochodzenie streszczenia od użytkownika; pole `source` ma wartość `environment`

AUDIT DELTA
- I1: każdy z 12 kandydatów ma wiersz w ledgerze
- I3: każdy Unit ma co najmniej jedną kotwicę z pełnym `locator`; revision `UNKNOWN` dla stron dokumentacji
- wejście nie zawiera pól `TARGET`, `id` i `version` profilu celu; w nagłówku `version: UNKNOWN`, `target` z pola ZASADA
- w A-MEM szablon `P_s3` ma dwie różne listy akcji (tekst i schemat JSON); zapisano w LIMITS U-001
- odczyt Mem0 paper urwany w §4.5, Appendix B nieodczytany; zapisano w ACCESS_LIMITATIONS i UNKNOWN U-002
- pięć Unitów ma warstwę DOCUMENTED_DESIGN; żaden nie ma warstwy IMPLEMENTED_STRUCTURE
- zgłoszenie #5149 (OpenHands) widoczne tylko w fragmencie wyników wyszukiwania; nie weszło do pól SOURCE ani EXTRACT, tylko do UNKNOWN U-004
- SEAM_QUESTION w wejściu zawierają hipotezy i oceny autora; nie weszły do pól SOURCE ani EXTRACT

SOURCE_GATE: CONTINUE
GATE_BASIS: kandydaci C-003, C-005, C-006, C-007, C-009 i C-010 mają otwarte strony źródeł i stan DEFER, a 20 leadów z wejścia nie przeszło PROBE.

SYNTHESIS
OBSERVATION: U-004 ma pole `source` o trzech wartościach, niezależne od roli LLM; w opisach U-001, U-002, U-003 i U-005 pola pochodzenia wpisu lub wartości brak.
OBSERVATION: U-001 przechowuje oryginalną treść w osobnym polu `c_i`; w odczytanych opisach U-002 i U-003 takiego pola nie podano.
OBSERVATION: w U-002 operacja `DELETE` usuwa wpis sprzeczny, a zachowanie wpisu jako nieważnego opisano tylko dla `Mem0g`.
INFERENCE: wzorzec „warstwa surowa tylko do dopisywania i widok pochodny" występuje jawnie w U-004; w U-001 odpowiednikiem jest rozdział `c_i` od `K`, `G`, `X`, a zastąpienie `m_j` przez `m_j*` nie jest opisane jako dopisanie.
INFERENCE: przeciek granicy w U-003 przebiega przez wpis `sr_t` dopisywany do pamięci razem z mechanizmem, który nie opisuje znacznika pochodzenia.
HYPOTHESIS: rozdzielenie pól `source` i `role` z U-004 mogłoby w zapisie tekstowym odróżniać słowa wprowadzone przez człowieka od streszczeń wygenerowanych przez system; nie sprawdzono w kodzie ani w działaniu.
TRANSFER: DESIGN_PRINCIPLE z U-004: plik tylko do dopisywania z polem pochodzenia oraz osobny plik widoku wyliczanego z niego, bez bazy danych.
OPEN_QUESTION: czy w kodzie OpenHands istnieje sposób wykluczenia wskazanych zdarzeń z `forgotten_event_ids` poza `keep_first`.
OPEN_QUESTION: czy A-MEM przechowuje poprzednią wersję notatki po zastąpieniu `m_j` przez `m_j*`.
OPEN_QUESTION: czy stan LangGraph po `Command(resume=...)` zawiera znacznik pochodzenia wartości wznowienia.
ASSESSMENT: kolejny Run: C-007 (wyzwalanie i ochrona zdarzeń w kodzie), C-009 (minimalny zestaw typów pochodzenia z PROV-DM) i C-010 (zapis unieważnienia relacji) odpowiadają na trzy pytania otwarte z tego Runu.
