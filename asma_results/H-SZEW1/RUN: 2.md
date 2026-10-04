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
  - OpenHands SDK, pakiet openhands-sdk 1.51.0 (rejestr PyPI)
  - W3C PROV-Overview (Working Group Note, 2013-04-30)
  - W3C PROV-DM
  - Zep paper (arXiv 2501.13956 v1)
  - Graphiti, pakiet graphiti-core 0.30.2 (rejestr PyPI)
  - LangGraph Docs (docs.langchain.com)
RUN: 2
FOCUS: ochrona zdarzeń i wyzwalanie kondensacji w kodzie OpenHands, najmniejszy zestaw typów pochodzenia w PROV-DM, zapis unieważnienia faktu w Zep / Graphiti
INPUT_MODE: SOURCE_ONLY
DEPTH_BUDGET: TARGETED
DATE: 2026-10-04
ACCESS_LIMITATIONS:
  - kod OpenHands SDK i Graphiti odczytany z pakietów wheel pobranych z rejestru PyPI (openhands-sdk 1.51.0, graphiti-core 0.30.2), nie z repozytoriów GitHub (odrzucone przez narzędzie odczytu w Runie 1); kodu nie uruchamiano, zachowanie w czasie wykonania nie było obserwowane
  - PROV-DM oraz Zep paper (§2.1, §2.2.3) odczytane przez narzędzie zwracające streszczenie strony, nie surowy tekst; numery sekcji i cytaty pochodzą z odpowiedzi narzędzia i nie zostały sprawdzone na surowym tekście; bezpośredni dostęp z powłoki do w3.org i arxiv.org odrzucony przez proxy
  - PROV-CONSTRAINTS, PROV-O i PROV-N nieotwarte; sekcje oceny Zep paper nieotwarte
  - wersje pakietów (1.51.0, 0.30.2) mogą różnić się od wersji opisanych przez strony dokumentacji OpenHands (revision UNKNOWN) i przez pracę Zep (v1)
  - ograniczenia Runu 1 dotyczące Mem0 paper (odczyt urwany w §4.5), CLARION (tekst pierwotny nieotwarty) oraz abstraktów Self-Refine, Constitutional AI i Generative Agents pozostają w mocy dla materiału nieotwieranego w tym Runie
TARGET_PROFILE:
  id: SZEW-TECHNIKA-CZLOWIEK (wejście nie nadaje identyfikatora; nazwa z nagłówka pliku)
  version: UNKNOWN
  target: neuralcore jako interfejs dostrojony do człowieka (pole ZASADA; pole TARGET w wejściu nie występuje)

SOURCE MAP
REGION | LOCATOR | SIGNAL
OpenHands SDK, zdarzenia kondensacji | openhands-sdk 1.51.0, openhands/sdk/event/condenser.py | klasy `Condensation` (`forgotten_event_ids`, `summary`, `summary_offset`, `llm_response_id`), `CondensationRequest`, `CondensationSummaryEvent`
OpenHands SDK, widok i właściwości | openhands-sdk 1.51.0, openhands/sdk/context/view/view.py, manipulation_indices.py, properties/*.py | `View.from_events`, `ManipulationIndices.find_next`, cztery właściwości w `ALL_PROPERTIES`
OpenHands SDK, kondensatory | openhands-sdk 1.51.0, openhands/sdk/context/condenser/base.py, llm_summarizing_condenser.py, pipeline_condenser.py | `RollingCondenser.condense`, `CondensationRequirement`, `LLMSummarizingCondenser`, `hard_context_reset`
OpenHands SDK, magazyn zdarzeń i agent | openhands-sdk 1.51.0, openhands/sdk/conversation/event_store.py, event/types.py, event/base.py, agent/agent.py, conversation/impl/local_conversation.py | `EventStore.append`, `SourceType`, `Agent._step`, `LocalConversation.condense`
W3C PROV-DM | https://www.w3.org/TR/prov-dm/, §5.1–§5.3 | typy `Entity`, `Activity`, `Agent`; relacje `wasGeneratedBy`, `used`, `wasDerivedFrom`, `wasAttributedTo`, `wasAssociatedWith`, `actedOnBehalfOf`, `wasInformedBy`, `wasInvalidatedBy`, `wasRevisionOf`, `wasQuotedFrom`, `hadPrimarySource`
Zep paper | https://arxiv.org/html/2501.13956v1, §2.1, §2.2.3 | cztery znaczniki czasu krawędzi, porównanie nowych krawędzi z istniejącymi przez LLM, podgraf epizodów
Graphiti | graphiti-core 0.30.2, graphiti_core/edges.py, nodes.py, utils/maintenance/edge_operations.py, prompts/dedupe_edges.py, prompts/extract_edges.py, graphiti.py | `EntityEdge`, `EpisodicNode`, `resolve_edge_contradictions`, `resolve_extracted_edge`, parametr `store_raw_episode_content`
UNKNOWN_REGIONS:
  - grupa PRAKTYKA CZŁOWIEKA I JEJ MECHANIZACJA, leady nienazwane jako kandydaci: Zettelkasten systems, Memex, HippoRAG / HippoRAG 2, Personal Knowledge Graphs
  - grupa GDZIE SZEW PRZECIEKA, leady nienazwane jako kandydaci: DSPy, RAPTOR, AlphaEvolve, FunSearch, Darwin Gödel Machine
  - grupa CO TRZYMA SZEW, leady nienazwane jako kandydaci: EventStoreDB, Claude Code · autoryzacja i odwracalność, OpenHands · analizator i polityka potwierdzeń, OpenAI Model Spec, River, LangSmith, MemoryBank
  - grupa KLIMAT JAKO TRYB, leady nienazwane jako kandydaci: CAPS, Emotion Machine, MicroPsi / MicroPsi 2, Companions
  - pozostałe pliki pakietów openhands-sdk i graphiti-core, w tym krok wyszukiwania krawędzi-kandydatów w Graphiti
  - zgłoszenie #5149 w repozytorium OpenHands (widoczne tylko we fragmencie wyników wyszukiwania)
OUTSIDE_SCOPE:
  - pola i pytania z bloku PROBES_OUTSIDE_CORPUS
  - zachowanie systemów w czasie wykonania

DELTA
NEW
UNIT_ID: U-006
NAME: Reason-Derived Hard or Soft Condensation Requirement
LENS: LENS_ARTIFACT, LENS_SYSTEM
TYPE: mechanism
STATUS: SOURCE_SUPPORTED
FUNCTION: Kondensator wyznacza z widoku zbiór przyczyn kondensacji i przypisuje mu wymóg `HARD` albo `SOFT`; gdy kondensacji nie da się wygenerować, wymóg `SOFT` zostawia widok bez zmian, a `HARD` uruchamia `hard_context_reset`; zdarzenie `CondensationRequest` dopisuje agent po dwóch klasach błędów dostawcy LLM albo wywołanie `LocalConversation.condense`.
MINIMAL_FORM:
  - przyczyny (`Reason`): `REQUEST` = nieobsłużone `CondensationRequest` w widoku; `TOKENS` = liczba tokenów widoku większa niż mniejsza z wartości `max_tokens` i limitu wejścia LLM agenta; `EVENTS` = `len(view)` większe niż `max_size`
  - wymóg: `TOKENS` w zbiorze przyczyn → `HARD`; zbiór przyczyn zawarty w {`EVENTS`} → `SOFT`; w pozostałych przypadkach `REQUEST` → `HARD`; pusty zbiór → widok bez zmian
  - `NoCondensationAvailableException` przy `SOFT` → zwróć niezmieniony widok; przy `HARD` → `hard_context_reset`; wyjątek jest zgłaszany dalej, gdy `hard_context_reset` zwróci `None`
  - `hard_context_reset`: streszcza `view.events[preserve:]`, gdzie `preserve` = indeks wiodącego `SystemPromptEvent` + 1 (albo 0 bez niego), `summary_offset` = `preserve`; do `hard_context_reset_max_retries` (5) prób, po każdej porażce długość tekstu pojedynczego zdarzenia ograniczana do 0,8 poprzedniego limitu (`hard_context_reset_context_scaling`)
  - `Agent._step`: `LLMContextWindowExceedError` albo błąd błędnej struktury historii (po `state.rebuild_view()`) przy kondensatorze z `handles_condensation_requests()` = `True` → `on_event(CondensationRequest())`; bez takiego kondensatora błąd jest zgłaszany dalej
  - `Condensation` zwrócone z `condense` jest emitowane jako zdarzenie zamiast kroku agenta; kolejny krok liczy widok z dziennika (U-004)
SOURCE_ANCHOR:
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/context/condenser/llm_summarizing_condenser.py
    anchor: LLMSummarizingCondenser.get_condensation_reasons, condensation_requirement, hard_context_reset
    revision: 1.51.0
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/context/condenser/base.py
    anchor: CondensationRequirement, RollingCondenser.condense
    revision: 1.51.0
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/agent/agent.py
    anchor: Agent._step (obsługa LLMContextWindowExceedError i błędu struktury historii)
    revision: 1.51.0
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/conversation/impl/local_conversation.py
    anchor: LocalConversation.condense
    revision: 1.51.0
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: IMPLEMENTED_STRUCTURE
DEPENDENCIES:
  - LLM streszczający (`llm` kondensatora), niezależny od LLM agenta
  - kondensator z `handles_condensation_requests()` = `True` dla ścieżki `CondensationRequest`
MUST_BE_TRUE: kondensator z `handles_condensation_requests()` = `True` jest skonfigurowany w agencie; bez niego `LocalConversation.condense` zgłasza `ValueError`
ENFORCEMENT: RUNTIME_CONSTRAINED
EFFECT_STATUS: NOT_APPLICABLE
TRANSFER_FORM: PROCESS_RULE, WORKFLOW
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: `CondensationRequest` jest tworzone bez argumentów w `Agent._step` i w `LocalConversation.condense`, ze `source` = `environment`; w odczytanych plikach zdarzenie nie niesie informacji, czy wnioskodawcą był agent, czy użytkownik
UNKNOWN:
  - evidence: zachowanie `hard_context_reset` w czasie wykonania nie było obserwowane
  - dependency: ścieżka `Agent._astep` nieczytana; zakłada się jej zgodność z `_step` na podstawie dopasowanych wywołań `on_event(CondensationRequest())`
LIMITS:
  - wartości domyślne zależą od ścieżki: klasa `LLMSummarizingCondenser` ma `max_size` 240 i `keep_first` 2, a `default_condenser` ustawia 80 i 4
  - komentarz w kodzie uzasadnia `HARD` dla `TOKENS` stałym oknem kontekstu lokalnego modelu w uruchomieniach benchmarkowych; przyczyna `EVENTS` jest opisana jako heurystyka zarządzania historią
RELATES_TO:
  - U-004
  - U-007

NEW
UNIT_ID: U-007
NAME: Protected-Head Atomic-Boundary Forgetting Range
LENS: LENS_ARTIFACT, LENS_SYSTEM
TYPE: algorithm
STATUS: SOURCE_SUPPORTED
FUNCTION: Zakres zdarzeń do zapomnienia jest wybierany z widoku tak, że jego początek leży za chronioną głową (pierwsze `keep_first` zdarzeń i wiodący `SystemPromptEvent`), oba końce leżą na indeksach manipulacji wspólnych dla wszystkich właściwości widoku, a zakres mniejszy niż `minimum_progress` widoku jest odrzucany.
MINIMAL_FORM:
  - `protected_prefix` = max(`keep_first`, indeks wiodącego `SystemPromptEvent` + 1)
  - `forgetting_start` = `manipulation_indices.find_next(protected_prefix)`; `forgetting_end` = `manipulation_indices.find_next(len(view) − events_from_tail)`
  - `events_from_tail` = minimum po przyczynach: `REQUEST` → `len(view)//2 − keep_first − 1`; `EVENTS` → `max_size//2 − keep_first − 1`; `TOKENS` → długość sufiksu, który zmniejsza liczbę tokenów do połowy limitu
  - zapomniane zdarzenia = `view[forgetting_start:forgetting_end]`; `summary_offset` = `forgetting_start`
  - indeksy manipulacji = przecięcie zbiorów zwracanych przez każdą właściwość z `ALL_PROPERTIES`: `ObservationUniquenessProperty`, `BatchAtomicityProperty`, `ToolCallMatchingProperty`, `ToolLoopAtomicityProperty`
  - pusty zakres albo zakres mniejszy niż `minimum_progress` (0,1) długości widoku → `NoCondensationAvailableException`
  - `View.enforce_properties` usuwa z widoku zdarzenia naruszające właściwości jako ścieżka zapasowa i zapisuje ostrzeżenie w logu
SOURCE_ANCHOR:
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/context/condenser/llm_summarizing_condenser.py
    anchor: LLMSummarizingCondenser._get_forgotten_events, get_condensation, _leading_system_prompt_index
    revision: 1.51.0
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/context/view/view.py, manipulation_indices.py, properties/__init__.py
    anchor: View.manipulation_indices, View.enforce_properties, ManipulationIndices.find_next, ALL_PROPERTIES
    revision: 1.51.0
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: IMPLEMENTED_STRUCTURE
DEPENDENCIES:
  - zbiór właściwości widoku (`ALL_PROPERTIES`)
MUST_BE_TRUE: wiodący `SystemPromptEvent` znajduje się na początku widoku (komentarz w kodzie przypisuje tę gwarancję pętli agenta)
ENFORCEMENT: RUNTIME_CONSTRAINED
EFFECT_STATUS: NOT_APPLICABLE
TRANSFER_FORM: ALGORITHM, DESIGN_PRINCIPLE
ADOPTION_NOTES:
  - dotyczy ANTI-GOALS profilu: chronione są pozycje na początku widoku i spójność protokołu LLM; w otwartych plikach nie ma pola ani parametru, którym użytkownik wskazuje zdarzenie jako niepodlegające zapomnieniu
UNKNOWN:
  - evidence: zachowanie przy `keep_first` = 0 w czasie wykonania nie było obserwowane
  - evidence: zgłoszenie #5149 (widoczne tylko we fragmencie wyników wyszukiwania) nieotwarte; związek ze zmianą w kodzie nieustalony
LIMITS:
  - wybór zakresu nie odwołuje się do pola `source` zdarzeń: zdarzenie o `source` = `user` poza chronioną głową podlega zapomnieniu na równi z innymi
  - walidator wymaga `max_size // 2 − keep_first − 1` > 0
  - inne kondensatory z `pipeline_condenser.py` i `no_op_condenser.py` nie wybierają zakresu: `PipelineCondenser` wywołuje kolejne kondensatory do pierwszego `Condensation`, `NoOpCondenser` zwraca widok
RELATES_TO:
  - U-004
  - U-006

NEW
UNIT_ID: U-008
NAME: Minimal Provenance Types and Derivation Relations
LENS: LENS_KNOWLEDGE
TYPE: schema
STATUS: SOURCE_SUPPORTED
FUNCTION: PROV-DM definiuje trzy typy (`Entity`, `Activity`, `Agent`) i relacje, z których `wasAttributedTo` przypisuje encję agentowi, a `wasDerivedFrom` wiąże encję z encją, z której powstała; podzbiór tych elementów wyraża pytania „czyje to jest" i „z czego powstało".
MINIMAL_FORM:
  - `Entity` —`wasAttributedTo`→ `Agent`: przypisanie encji agentowi
  - `Entity` —`wasDerivedFrom`→ `Entity`: encja powstała jako transformacja, aktualizacja albo konstrukcja na podstawie encji istniejącej
  - `Entity` —`wasGeneratedBy`→ `Activity`; `Activity` —`wasAssociatedWith`→ `Agent`: czynność jako ogniwo między encją a odpowiedzialnym agentem
  - podtypy `wasDerivedFrom`: `wasRevisionOf` (wersja zmieniona), `wasQuotedFrom` (powtórzenie przez kogoś, kto nie musi być autorem), `hadPrimarySource` (od materiału wtórnego do pierwotnego)
  - `wasInvalidatedBy`: początek zniszczenia, zakończenia albo wygaśnięcia encji przez czynność
SOURCE_ANCHOR:
  - source: W3C PROV-DM
    locator: https://www.w3.org/TR/prov-dm/
    anchor: §5.1.1 Entity, §5.1.2 Activity, §5.1.3 wasGeneratedBy, §5.1.8 wasInvalidatedBy, §5.2.1–§5.2.4 derywacja i podtypy, §5.3.1–§5.3.4 Agent, wasAttributedTo, wasAssociatedWith, actedOnBehalfOf
    revision: UNKNOWN
EVIDENCE_TYPE: DIRECT_INFERENCE
EVIDENCE_LAYER: DOCUMENTED_DESIGN
ENFORCEMENT: UNKNOWN
EFFECT_STATUS: NOT_APPLICABLE
TRANSFER_FORM: SCHEMA, DESIGN_PRINCIPLE
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: pole `source` z U-004 wskazuje rodzaj nadawcy zdarzenia, a `wasDerivedFrom` wskazuje encję źródłową; to dwa różne pytania, a w U-004 odpowiada na nie tylko pierwsze
UNKNOWN:
  - evidence: czy PROV-DM wyznacza własny podzbiór minimalny; tekst nieczytany bezpośrednio
  - dependency: reguły spójności modelu (PROV-CONSTRAINTS) nieotwarte; kategoria `ENFORCEMENT` nieustalona
LIMITS:
  - definicje typów i relacji są faktem źródła; wybór podzbioru w `MINIMAL_FORM` jest wnioskiem z tych definicji
  - odczyt przez narzędzie zwracające streszczenie strony; numery sekcji niezweryfikowane na surowym tekście
RELATES_TO:
  - U-004
  - U-009

NEW
UNIT_ID: U-009
NAME: Bitemporal Fact Invalidation with Retained Source Episodes
LENS: LENS_KNOWLEDGE
TYPE: mechanism
STATUS: SOURCE_SUPPORTED
FUNCTION: LLM porównuje nowy fakt-krawędź z istniejącymi i wskazuje sprzeczne; dla starszej sprzecznej krawędzi kod ustawia `invalid_at` równe `valid_at` nowej krawędzi oraz `expired_at` równe czasowi przetwarzania, a krawędzie unieważnione są zapisywane razem z nowymi; surowa treść epizodu leży w osobnym węźle, do którego krawędź odsyła listą `episodes`.
MINIMAL_FORM:
  - `EntityEdge`: `fact` (według opisu pola „paraphrased from the source text"), `episodes`, `valid_at`, `invalid_at`, `expired_at`, `created_at`, `reference_time`
  - `EpisodicNode`: `source`∈{`message`, `json`, `text`, `fact_triple`}, `content` (surowe dane epizodu), `valid_at`, `entity_edges`; dla `message` format `content` to „actor: content"
  - nowa krawędź: dodatkowe wywołanie LLM (`_extract_edge_timestamps`) ustala `valid_at` i `invalid_at` względem `reference_time` epizodu
  - LLM (`dedupe_edges`) → `duplicate_facts`, `contradicted_facts` (indeksy); indeksy poza zakresem są pomijane z ostrzeżeniem
  - `resolve_edge_contradictions(nowa, kandydaci)`: pomiń kandydata, gdy okna `[valid_at, invalid_at]` nie nakładają się; gdy `valid_at` kandydata < `valid_at` nowej: `kandydat.invalid_at` = `nowa.valid_at`, `kandydat.expired_at` = istniejące albo bieżący czas
  - gdy kandydat ma późniejsze `valid_at` niż nowa krawędź, nowa dostaje `invalid_at` = `valid_at` kandydata i `expired_at` = bieżący czas
  - zapis: `resolved_edges + invalidated_edges`; krawędzie unieważnione nie są usuwane
SOURCE_ANCHOR:
  - source: Zep paper (arXiv 2501.13956 v1)
    locator: https://arxiv.org/html/2501.13956v1
    anchor: §2.1 Episodes, §2.2.3 Temporal Extraction and Edge Invalidation
    revision: v1
  - source: Graphiti, pakiet graphiti-core 0.30.2
    locator: graphiti_core/utils/maintenance/edge_operations.py
    anchor: resolve_edge_contradictions, resolve_extracted_edge, _extract_edge_timestamps
    revision: 0.30.2
  - source: Graphiti, pakiet graphiti-core 0.30.2
    locator: graphiti_core/edges.py, graphiti_core/nodes.py, graphiti_core/prompts/dedupe_edges.py, graphiti_core/prompts/extract_edges.py
    anchor: EntityEdge, EpisodicNode, EpisodeType, DedupeEdges (pola `duplicate_facts`, `contradicted_facts`)
    revision: 0.30.2
EVIDENCE_TYPE: SOURCE_FACT
EVIDENCE_LAYER: IMPLEMENTED_STRUCTURE
DEPENDENCIES:
  - LLM wykonujący porównanie i ekstrakcję znaczników czasu
  - zbiór krawędzi-kandydatów dostarczony przez wcześniejszy krok wyszukiwania
MUST_BE_TRUE: krawędzie mają `valid_at`; krawędź bez `valid_at` nie spełnia warunku unieważnienia w `resolve_edge_contradictions`
ENFORCEMENT: SCHEMA_CONSTRAINED
EFFECT_STATUS: UNKNOWN
TRANSFER_FORM: DATA_STRUCTURE, PROCESS_RULE
ADOPTION_NOTES:
  - dotyczy PROBLEMS profilu: unieważniona krawędź zostaje w bazie z `invalid_at`; surowy epizod jest osobnym węzłem, a `fact` jest parafrazą modelu
  - dotyczy ANTI-GOALS profilu: w `EntityEdge` brak pola z przyczyną unieważnienia, więc zapis nie odróżnia zmiany zdania użytkownika od korekty zapisu przez system
UNKNOWN:
  - evidence: czy którakolwiek ścieżka kodu zapisuje przyczynę unieważnienia; w otwartych plikach pola nie ma
  - evidence: wyniki oceny w pracy (sekcje po §2) nieotwarte
  - dependency: krok wyszukiwania krawędzi-kandydatów nieczytany
LIMITS:
  - decyzję o sprzeczności podejmuje LLM; część czasowa jest porównaniem znaczników w kodzie
  - znaczniki `valid_at` i `invalid_at` nowej krawędzi pochodzą z wywołania LLM
  - parametr `store_raw_episode_content` (domyślnie `True`): przy `False` kod ustawia `ep.content` na pusty ciąg przed zapisem
DISCREPANCY:
  DOCUMENTED: praca opisuje podgraf epizodów jako nieutracalny magazyn danych, z którego wyodrębniane są encje i relacje (§2.1)
  IMPLEMENTED: `Graphiti` przyjmuje parametr `store_raw_episode_content`; przy wartości `False` treść epizodu nie jest zapisywana
RELATES_TO:
  - U-002
  - U-008

EXTENDS
UNIT_ID: U-004
ADDED:
  - `Condensation.summary_event` jest generowane dynamicznie z deterministycznym `id` w postaci `<id Condensation>-summary` i według komentarza w kodzie nie jest zapisywane w magazynie zdarzeń
  - `Condensation.llm_response_id` wiąże zdarzenie z odpowiedzią LLM, która je wygenerowała
  - `EventStore.append` odrzuca zdarzenie o istniejącym `id` oraz zdarzenie z nieistniejącym `parent_id` (`ValueError`); interfejs `EventStore` w otwartym pliku nie ma metody usuwania zdarzenia
  - `Event` ma konfigurację `frozen=True` i `extra="forbid"`
SOURCE_ANCHOR:
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/event/condenser.py, openhands/sdk/event/base.py, openhands/sdk/conversation/event_store.py
    anchor: Condensation.summary_event, Condensation.llm_response_id, Event.model_config, EventStore.append
    revision: 1.51.0

CORRECTS
UNIT_ID: U-004
FIELD: MINIMAL_FORM
PREVIOUS: `source`∈{`user`, `agent`, `environment`}
CURRENT: `source`∈{`agent`, `user`, `environment`, `hook`} (`SourceType`); pozostałe linie bez zmian, w tym `CondensationSummaryEvent` ze `source` = `environment` i `role` = `user`
SOURCE_ANCHOR:
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/event/types.py, openhands/sdk/event/condenser.py
    anchor: SourceType, CondensationSummaryEvent.to_llm_message
    revision: 1.51.0
REASON: otwarto kod pakietu; strony dokumentacji z Runu 1 wymieniały trzy wartości `source`

CORRECTS
UNIT_ID: U-004
FIELD: EVIDENCE_LAYER
PREVIOUS: DOCUMENTED_DESIGN
CURRENT: IMPLEMENTED_STRUCTURE
SOURCE_ANCHOR:
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/event/condenser.py, openhands/sdk/context/view/view.py, openhands/sdk/conversation/event_store.py
    anchor: Condensation.apply, View.from_events, EventStore.append
    revision: 1.51.0
REASON: kod pakietu openhands-sdk 1.51.0 zawiera dziennik zdarzeń, zdarzenie `Condensation` i `View.from_events` w opisanej postaci

CORRECTS
UNIT_ID: U-004
FIELD: ENFORCEMENT
PREVIOUS: UNKNOWN
CURRENT: RUNTIME_CONSTRAINED
SOURCE_ANCHOR:
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/event/base.py, openhands/sdk/conversation/event_store.py
    anchor: Event.model_config (`frozen=True`), EventStore.append
    revision: 1.51.0
REASON: kod egzekwuje niemodyfikowalność obiektu zdarzenia i unikalność `id` w czasie wykonania; plików magazynu nie chroni przed zapisem spoza interfejsu żaden z otwartych plików

CORRECTS
UNIT_ID: U-004
FIELD: UNKNOWN
PREVIOUS: brak mechanizmu egzekwującego niemodyfikowalność dziennika w warstwie zapisu (nieotwarty); zgłoszenie #5149 (tylko fragment wyników wyszukiwania); kod `view.py` i `llm_summarizing_condenser.py` nieotwarty
CURRENT: zgłoszenie #5149 nieotwarte, związek ze zmianą w kodzie wiodącego `SystemPromptEvent` nieustalony; zachowanie w czasie wykonania nie było obserwowane
SOURCE_ANCHOR:
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/context/condenser/llm_summarizing_condenser.py
    anchor: _leading_system_prompt_index, _get_forgotten_events
    revision: 1.51.0
REASON: otwarto `view.py`, `llm_summarizing_condenser.py` i `event_store.py`; dwa z trzech braków zostały uzupełnione

CORRECTS
UNIT_ID: U-004
FIELD: LIMITS
PREVIOUS: w otwartych stronach dokumentacji nie opisano mechanizmu oznaczania zdarzeń jako niepodlegających zapomnieniu poza parametrem `keep_first` (domyślnie 4 pierwsze zdarzenia); wartości `max_size` (domyślnie 120) i `keep_first` są parametrami konfiguracji; strony opisują architekturę, zgodność z kodem nie została sprawdzona
CURRENT: w kodzie 1.51.0 chronione jest pierwsze `keep_first` zdarzeń i wiodący `SystemPromptEvent` (U-007); pola ani parametru do oznaczania dowolnych zdarzeń nie ma w otwartych plikach; domyślne `keep_first` i `max_size` zależą od ścieżki (U-006); zgodność stron dokumentacji z kodem opisuje DISCREPANCY
SOURCE_ANCHOR:
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/context/condenser/llm_summarizing_condenser.py
    anchor: LLMSummarizingCondenser (pola `max_size`, `keep_first`), default_condenser, _get_forgotten_events
    revision: 1.51.0
REASON: porównanie stron dokumentacji z kodem pakietu

CORRECTS
UNIT_ID: U-004
FIELD: DISCREPANCY
PREVIOUS: brak pola
CURRENT: DOCUMENTED: strony `events` i `condenser` (revision UNKNOWN) podają trzy wartości `source` oraz domyślne `keep_first` 4 i `max_size` 120; IMPLEMENTED: `SourceType` ma cztery wartości (`agent`, `user`, `environment`, `hook`), klasa `LLMSummarizingCondenser` ma domyślnie `keep_first` 2 i `max_size` 240, a `default_condenser` ustawia `max_size` 80 i `keep_first` 4
SOURCE_ANCHOR:
  - source: OpenHands SDK, pakiet openhands-sdk 1.51.0
    locator: openhands/sdk/event/types.py, openhands/sdk/context/condenser/llm_summarizing_condenser.py
    anchor: SourceType, LLMSummarizingCondenser, default_condenser
    revision: 1.51.0
REASON: rozbieżność między stronami dokumentacji z Runu 1 a kodem pakietu; wersja dokumentacji nieznana, więc rozbieżność może wynikać z różnicy wersji

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

CANDIDATE LEDGER
CANDIDATE_ID | STATE | UNIT_ID | LAST_CHANGE | REASON
C-001 | UNITIZED | U-001 | run 1 NEW | odrębny mechanizm zastępowania sąsiednich notatek z osobnym polem treści oryginalnej
C-002 | UNITIZED | U-002 | run 1 NEW | odrębny mechanizm wyboru operacji na pamięci dla faktu z ekstrakcji
C-003 | DEFER | - | run 1 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto tylko abstrakt arXiv 2303.17651, źródło kryterium w kroku sprzężenia zwrotnego nieodczytane
C-004 | UNITIZED | U-003 | run 1 NEW | odrębny mechanizm ograniczonego bufora refleksji dopisywanej po próbach
C-005 | DEFER | - | run 1 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto tylko abstrakt arXiv 2212.08073, miejsce wejścia i zmiany zasad nieodczytane
C-006 | DEFER | - | run 1 DEFER | BUDGET: limit pogłębień z §31 wyczerpany; otwarto tylko abstrakt arXiv 2304.03442, relacja refleksji do wpisów surowych nieodczytana
C-007 | UNITIZED | U-006 | run 2 NEW | odrębny mechanizm wyznaczania wymogu kondensacji i ścieżki awaryjnej; obejmuje leady „OpenHands · kondensacja kontekstu" i „OpenHands · ręczne żądanie kondensacji"
C-008 | UNITIZED | U-004 | run 2 CORRECTS | odrębny mechanizm dziennika tylko do dopisywania z widokiem pochodnym; po odczycie kodu Unit skorygowano i rozszerzono
C-009 | UNITIZED | U-008 | run 2 NEW | odrębny schemat najmniejszego zestawu typów i relacji pochodzenia
C-010 | UNITIZED | U-009 | run 2 NEW | odrębny mechanizm unieważniania faktu z zachowaniem epizodu źródłowego
C-011 | UNITIZED | U-005 | run 1 NEW | odrębny mechanizm przerwania z zapisem stanu i restartem węzła przy wznowieniu
C-012 | NOT_PROBED | - | run 1 NOT_PROBED | LEAD_UNRESOLVED: tekst pierwotny (Sun, Merrill, Peterson 2001, Cognitive Science) widoczny tylko we fragmencie wyników wyszukiwania, nie otwarty
C-013 | UNITIZED | U-007 | run 2 NEW | odrębny algorytm wyboru zakresu zapominania z chronioną głową i granicami jednostek atomowych; kandydat odnaleziony przy pogłębianiu C-007

REJECTED INFERENCES
- założenie z SEAM_QUESTION dla C-007, że pierwsza faza kondensacji wycina, a druga streszcza, nie ma oparcia w kodzie: `Condensation` powstaje z jednego wywołania LLM, które streszcza zapomniane zdarzenia; dwie fazy to wygenerowanie zdarzenia i zastosowanie go w `View.from_events`
- zachowanie zdarzenia w magazynie zdarzeń ≠ obecność zdarzenia w wejściu LLM; po `Condensation` wejście LLM zawiera streszczenie, a zapomniane zdarzenia są poza widokiem
- pole `source` zdarzenia w OpenHands ≠ kryterium wyboru zdarzeń do zapomnienia; `_get_forgotten_events` używa pozycji i indeksów manipulacji, nie wartości `source`
- relacja `wasQuotedFrom` w PROV-DM ≠ oznaczenie słów użytkownika; relacja opisuje powtórzenie przez kogoś, kto może nie być autorem, i nie wskazuje tożsamości autora
- domyślna wartość `store_raw_episode_content` = `True` ≠ gwarancja zachowania surowej treści epizodu; parametr pozwala ją pominąć przy zapisie
- unieważnienie krawędzi w Graphiti ≠ zapis przyczyny zmiany; w `EntityEdge` brak pola z przyczyną

AUDIT DELTA
- I1: każdy z 13 kandydatów ma wiersz w ledgerze
- limit z §31: w Runie 2 nazwano 4 kandydatów (C-007, C-009, C-010, C-013) i pogłębiono 4 z 5 dozwolonych; wybór wynika z OPEN_QUESTION Runu 1, a nie z profilu
- DISCREPANCY w U-004 (trzy wartości `source` wobec czterech; domyślne `keep_first` i `max_size`) i w U-009 (podgraf epizodów jako nieutracalny magazyn wobec parametru `store_raw_episode_content`)
- U-004: trzy pola wyliczeniowe i pola `UNKNOWN`, `LIMITS`, `DISCREPANCY` zmienione przez CORRECTS po otwarciu kodu; `EXTENDS` nie zmienia pól wyliczeniowych (§20)
- U-004, U-006, U-007: wartości domyślne `max_size` i `keep_first` różnią się między klasą (240, 2) a `default_condenser` (80, 4); wartości w przykładzie `LocalConversation.condense` (120, 4) są tekstem komunikatu błędu
- odczyt PROV-DM i Zep paper przez narzędzie zwracające streszczenie; tylko U-008 i warstwa dokumentowana U-009 zależą od tego odczytu
- kod pochodzi z pakietów PyPI w wersjach 1.51.0 i 0.30.2; zgodność z wersjami dokumentacji i prac nie została sprawdzona
- C-003, C-005 i C-006 nie były pogłębiane w tym Runie
- zgłoszenie #5149 (OpenHands) nadal tylko we fragmencie wyników wyszukiwania; nie weszło do pól SOURCE ani EXTRACT
- SEAM_QUESTION w wejściu zawierają hipotezy i oceny autora; nie weszły do pól SOURCE ani EXTRACT

SOURCE_GATE: CONTINUE
GATE_BASIS: kandydaci C-003, C-005 i C-006 mają stan DEFER, C-012 ma stan NOT_PROBED, a 20 leadów z wejścia nie przeszło PROBE.

SYNTHESIS
OBSERVATION: wybór zakresu zapominania w U-007 używa pozycji i granic jednostek atomowych protokołu LLM; w otwartych plikach brak pola, którym wskazuje się zdarzenie jako niepodlegające zapomnieniu.
OBSERVATION: `CondensationRequest` jest tworzone bez argumentów przez `Agent._step` i `LocalConversation.condense`, ze `source` = `environment`; zdarzenie nie niesie informacji o wnioskodawcy.
OBSERVATION: w U-009 unieważniona krawędź zostaje w bazie z `invalid_at` i `expired_at`, a `EntityEdge` nie ma pola z przyczyną unieważnienia.
OBSERVATION: w U-009 `fact` jest parafrazą tekstu źródłowego, a surowa treść leży w `EpisodicNode.content` i może być pominięta parametrem `store_raw_episode_content`.
INFERENCE: wzorzec „warstwa surowa i warstwa pochodna z odsyłaczem" występuje w U-004 (dziennik i `View`), U-009 (`EpisodicNode` i `EntityEdge.episodes`) oraz U-001 (`c_i` i pola pochodne); jawne pole nadawcy ma tylko U-004 (`source`), a w U-009 nadawca wynika z formatu `content` typu `message`.
INFERENCE: zbiór `Entity`, `Agent`, `wasAttributedTo` i `wasDerivedFrom` wystarcza formalnie do wyrażenia pytań „czyje" i „z czego"; `Activity` dodaje „czym wytworzono".
TRANSFER: SCHEMA z U-008 połączony z DATA_STRUCTURE z U-004: wpis w pliku tylko do dopisywania z polami nadawcy i wpisu źródłowego oraz osobny widok liczony z pliku.
OPEN_QUESTION: czy rozróżnienie „zmiana zdania użytkownika" i „korekta zapisu przez system" w Graphiti wynika z kolejności epizodów i typu `source` epizodu, bez osobnego pola.
OPEN_QUESTION: jak krok wyszukiwania krawędzi-kandydatów w Graphiti ogranicza zbiór krawędzi sprawdzanych pod kątem sprzeczności.
OPEN_QUESTION: czy czwarta wartość `hook` w `SourceType` OpenHands wpływa na wybór zdarzeń przez kondensator.
ASSESSMENT: kolejny Run: C-003, C-005 i C-006 wymagają pełnych tekstów prac (otwarto tylko abstrakty), a C-012 wymaga tekstu pierwotnego CLARION.
