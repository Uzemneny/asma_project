# NEURALCORE — RESEARCH CORPUS
## Discovery → Source Map → Project Taxonomy → ASMA-ready Corpus

**Version:** 1.0  ·  **Date:** 2026-10-02  ·  **Mode:** discovery / corpus consolidation

> **Purpose:** zachować wynik szerokiego rozpoznania projektów, architektur, mechanizmów i infrastruktur znalezionych w niezależnych materiałach modelowych, zanim rozpocznie się właściwa selekcja i rekonstrukcja ASMA.

---

## 0. Jak czytać ten dokument

To jest **korpus badawczy**, nie ranking projektów i nie audyt skuteczności. Projekt jest tutaj przede wszystkim **punktem wejścia do mechanizmu**. Opisy są krótkimi syntezami materiałów wejściowych; nie należy ich traktować jako niezależnie zweryfikowanych twierdzeń.

### Zasady
- **Projekt ≠ mechanizm.** Jeden projekt może zawierać dziesiątki mechanizmów.
- **Mechanizm ≠ implementacja.** Papier, kod, benchmark i dokumentacja są osobnymi warstwami dowodu.
- **Alias ≠ duplikat.** Powiązane generacje zachowują własną tożsamość źródłową.
- **Brak dowodu ≠ brak projektu.** Kandydat discovery pozostaje w korpusie, ale jego status wymaga późniejszego ASMA/verification.
- **Nie oceniam tu „najlepszości”.** Wyróżnik oznacza mechanizm lub charakter architektury, nie przewagę.

### Poziomy pochodzenia
| Kod | Znaczenie |
|---|---|
| `DIRECT` | materiał wklejony w bieżącej części rozmowy |
| `CONTEXT` | katalog zachowany wcześniej w kontekście tej rozmowy |
| `TECH` | osobny materiał techniczny analizowany jako artefakt źródłowy |

---

## 1. RESEARCH SOURCE REGISTRY

| ID | Źródło | Typ | Dostęp | Rola w korpusie |
|---|---|---|---|---|
| `S01` | **Mistral Vibe** | model-provided discovery catalog | `CONTEXT` | Source set emphasizing cognitive architectures, reasoning, memory, neuro/biological systems, research tooling and formal methods. |
| `S02` | **Perplexity** | model-provided discovery catalog | `CONTEXT` | Broad discovery pass across cognitive architectures, agents, memory, planning, RL, simulation, evals, protocols and infrastructure. |
| `S03` | **Qwen3.7-Plus** | model-provided discovery catalog | `CONTEXT` | Cognitive architectures, active inference, SNNs, agent frameworks, memory, protocols and neuro-symbolic systems. |
| `S04` | **Grok 4.20 — ArenaAI** | model-provided discovery catalog | `CONTEXT` | Large cognitive-architecture and agent-system survey with many historical and niche architectures. |
| `S05` | **GPT o3 Search — ArenaAI** | model-provided discovery catalog | `CONTEXT` | Broad search catalog spanning cognitive architectures, frameworks, memory, RL, robotics, safety, knowledge and evals. |
| `S06` | **Claude** | model-provided discovery catalog | `DIRECT` | Current-turn material: 40+ highly structured project records plus additional candidates; explicitly discovery-only. |
| `S07` | **ChatGPT Deep Research** | model-provided discovery catalog | `DIRECT` | Current-turn material covering cognitive architectures, agent frameworks, memory, AutoGPT/BabyAGI, HTM, DNC, Blue Brain and related systems. |
| `S08` | **LumoAI** | model-provided discovery catalog | `DIRECT` | Current-turn material with core projects plus newer framework/model/memory candidates. |
| `S09` | **ChatGPT** | model-provided discovery catalog | `DIRECT` | Current-turn large discovery corpus with 200+ named projects/families and explicit source/documentation fields. |

### Technical source sets

| ID | Źródło | Typ | Dostęp | Zakres |
|---|---|---|---|---|
| `T01` | **Anthropic / Claude Code** | technical artifact set | `DIRECT` | Detailed ASMA analysis of Task delegation, tool capabilities, authorization/reversibility, hooks, task progress and related mechanisms. |
| `T02` | **Cursor** | technical artifact set | `DIRECT` | Detailed source analysis of semantic-search refinement and code navigation/selective retrieval mechanisms. |
| `T03` | **Google Antigravity** | technical artifact set | `DIRECT` | Detailed source analysis of knowledge items, symbol-aware retrieval, scheduling and task tooling. |
| `T04` | **OpenHands** | technical artifact set | `DIRECT` | Code/documentation-level ASMA analysis: event loop, append-only log, condenser, security analyzer, tool registry and agent server. |

> **Ważne:** Grok 4.20 i GPT o3 Search są zachowane jako osobne źródła, ale oba mają pochodzenie `ArenaAI`. Nie są traktowane jako niezależne od siebie wyszukiwarki tylko dlatego, że są różnymi modelami.

> **Provenance rule:** gdy materiał mówi wyraźnie, że projekt pojawił się w wielu katalogach, zapisuję to jako `multiple supplied catalogs` zamiast udawać kompletną macierz wystąpień. Dokładne przecięcie wszystkich źródeł jest osobnym zadaniem, nie ukrytym za tym artefaktem.

---

## 2. KRYTERIUM GRUPOWANIA

Kategorie są **taksonomią funkcjonalną**, nie oceną. Ten sam projekt może być istotny w kilku wymiarach; w tym dokumencie otrzymuje jedno główne miejsce, a relacje między grupami są zachowane w aliasach i późniejszej warstwie mechanizmów.

### Główne rodziny
1. Cognitive Architectures
2. Memory, Knowledge & Retrieval
3. Reasoning, Reflection & Metacognition
4. Agents, Orchestration & Tool Use
5. Planning, Formal Reasoning & Search
6. Learning, RL & Adaptation
7. Neural Architectures, World Models & Open Models
8. Neural, Spiking & Brain-Inspired Systems
9. Active Inference, Predictive Processing & Adaptive Inference
10. Robotics & Embodied Cognition
11. Multi-Agent Systems & Social Simulation
12. Scientific AI, Discovery & Research Agents
13. Safety, Provenance, Observability & Evaluation
14. Protocols, Infrastructure & Durable Execution
15. Symbolic Systems, Logic & Neuro-Symbolic Methods
16. Brain Simulation, Connectomics & Biological Systems
17. Historical, Scientific & Meta-Research Systems

---

## 3. KORPUS — MAPA WIELKOŚCI

| Kategoria | Rekordy |
|---|---:|
| 01 — Cognitive Architectures | 49 |
| 02 — Memory, Knowledge & Retrieval | 39 |
| 03 — Reasoning, Reflection & Metacognition | 20 |
| 04 — Agents, Orchestration & Tool Use | 31 |
| 05 — Planning, Formal Reasoning & Search | 32 |
| 06 — Learning, RL & Adaptation | 18 |
| 07 — Neural Architectures, World Models & Open Models | 12 |
| 08 — Neural, Spiking & Brain-Inspired Systems | 17 |
| 09 — Active Inference, Predictive Processing & Adaptive Inference | 9 |
| 10 — Robotics & Embodied Cognition | 9 |
| 11 — Multi-Agent Systems & Social Simulation | 9 |
| 12 — Scientific AI, Discovery & Research Agents | 19 |
| 13 — Safety, Provenance, Observability & Evaluation | 22 |
| 14 — Protocols, Infrastructure & Durable Execution | 16 |
| 15 — Symbolic Systems, Logic & Neuro-Symbolic Methods | 11 |
| 16 — Brain Simulation, Connectomics & Biological Systems | 9 |
| 17 — Historical, Scientific & Meta-Research Systems | 10 |
| **Łącznie po scaleniu nazw w tym artefakcie** | **332** |

> Liczba oznacza rekordy projektowe/rodzinne w tym dokumencie, nie liczbę unikalnych mechanizmów, repozytoriów ani niezależnych dowodów.

---

## 01 — Cognitive Architectures

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **3APL** | agent programming / BDI | Beliefs, goals and plans in a formal agent-programming setting. | ChatGPT |
| **4CAPS** | cognitive architecture / distributed processing | Parallel constraint-satisfaction style cognitive processing. | Grok 4.20 — ArenaAI, ChatGPT |
| **ACT-R** | cognitive architecture / human cognition | Modules, buffers, production rules, declarative/procedural memory and activation-based retrieval. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **ACT-R/PM** | perception-motor extension | ACT-R extension linking cognitive modules with perceptual and motor systems. | ChatGPT |
| **AgentSpeak / Jason** | BDI / multi-agent systems | Beliefs, desires, intentions, plans and intention-stack execution. | Grok 4.20 — ArenaAI, Claude, ChatGPT Deep Research, ChatGPT |
| **AIXI** | theoretical AGI / decision theory | Universal sequence prediction plus reward optimization as a theoretical intelligence limit. | Grok 4.20 — ArenaAI |
| **ARCADIA** | cognitive architecture | Modular cognitive processing with attention, memory and executive control. | Grok 4.20 — ArenaAI |
| **ART** | adaptive resonance / neural cognition | Stability-plasticity trade-off through category learning and resonance. | Grok 4.20 — ArenaAI |
| **BECCA** | cognitive architecture / reinforcement | Experience-driven concept formation and action selection. | Grok 4.20 — ArenaAI |
| **CAPS** | cognitive architecture / personality | Constraint-based cognitive-affective processing rather than a single global controller. | Grok 4.20 — ArenaAI, Claude, ChatGPT |
| **CERA-CRANIUM** | cognitive architecture / robotics | Historical architecture for embodied cognition and action selection. | Grok 4.20 — ArenaAI |
| **CHREST** | cognitive modeling / chunk learning | Chunked knowledge structures and acquisition of expertise. | Grok 4.20 — ArenaAI |
| **CLARION** | cognitive architecture | Explicit/implicit learning layers plus motivational and metacognitive subsystems. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **Companions** | cognitive architecture / lifelong interaction | Long-term human-agent interaction, explanation, learning and experience. | Claude, ChatGPT Deep Research, ChatGPT |
| **Copycat** | analogy / cognitive architecture | Fluid analogy-making through distributed symbolic concepts and competing interpretations. | Grok 4.20 — ArenaAI, ChatGPT |
| **DAC** | cognitive architecture | Distributed cognition / action control research architecture. | Grok 4.20 — ArenaAI |
| **DIARC** | cognitive robotics | Distributed architecture for perception, dialogue, planning and robotic action. | Grok 4.20 — ArenaAI |
| **DUAL** | cognitive architecture | Interaction of symbolic and subsymbolic associative processing. | Grok 4.20 — ArenaAI, ChatGPT |
| **Emotion Machine** | cognitive theory / control | Emotion-like regulatory processes as architectural modes rather than a single emotion module. | Grok 4.20 — ArenaAI |
| **EPIC** | cognitive architecture / perception-action | Detailed modeling of perceptual, cognitive and motor concurrency. | Qwen3.7-Plus, Grok 4.20 — ArenaAI, Claude, ChatGPT |
| **EPIC / perceptual-motor architecture** | perception-action cognition | Concurrent human perceptual and motor processing. | Grok 4.20 — ArenaAI, ChatGPT |
| **Fluid Construction Grammar** | language / cognitive architecture | Construction-based language processing with interaction between grammar and semantics. | ChatGPT |
| **FORR** | decision architecture / learning | Multiple advice sources and learned heuristics arbitrated into decisions. | Grok 4.20 — ArenaAI, Claude, ChatGPT |
| **GLAIR** | cognitive architecture / embodied cognition | Layered architecture linking symbolic cognition with embodied control. | Grok 4.20 — ArenaAI, ChatGPT |
| **GOAL** | agent programming / goals | Goal-centric programming with beliefs, rules and actions. | ChatGPT |
| **Gödel Machine** | self-modification / theory | Formal proposal for utility-improving self-rewrites under proof conditions. | Grok 4.20 — ArenaAI, Claude |
| **H-CogAff / CogAff** | cognitive architecture | Hybrid architecture organizing perception, action, deliberation and reactive layers. | Grok 4.20 — ArenaAI |
| **ICARUS** | cognitive architecture / hierarchical skills | Concepts and hierarchical skills connected to perception, goals and execution. | Perplexity, Qwen3.7-Plus, Grok 4.20 — ArenaAI, Claude, ChatGPT |
| **Jadex** | BDI / agent programming | BDI agents with lifecycle, plans, goals and event handling. | ChatGPT |
| **Leabra / Emergent** | biologically inspired cognitive modeling | Error-driven plus Hebbian learning with working-memory/PFC-BG style gating. | Mistral Vibe, Perplexity, Qwen3.7-Plus, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT Deep Research, ChatGPT |
| **Letter Spirit** | analogy / concept formation | Programmatic analogy and concept discovery in letterform domains. | Grok 4.20 — ArenaAI, ChatGPT |
| **LIDA** | cognitive architecture / global workspace | Perception → attention → global broadcast → action cycles with episodic/semantic memory. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **MAMID** | cognitive architecture | Historical cognitive-architecture design focused on integrated control. | Grok 4.20 — ArenaAI |
| **Metacat** | metacognition / analogy | Metacognitive extension of Copycat-style analogy making and self-monitoring. | Grok 4.20 — ArenaAI, ChatGPT |
| **MicroPsi / MicroPsi 2** | cognitive architecture / motivation | Activation spreading combined with drives, emotion-like modulation and action selection. | Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **MLECOG** | cognitive architecture | Historical integrated cognitive architecture entry from survey catalog. | Grok 4.20 — ArenaAI |
| **NEUCOGAR** | cognitive architecture | Neural/cognitive architecture research entry from survey catalog. | Grok 4.20 — ArenaAI |
| **OpenCog Classic** | AGI / cognitive architecture | AtomSpace knowledge hypergraph, PLN, ECAN and heterogeneous cognitive components. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **OpenCog Hyperon / MeTTa** | AGI / cognitive architecture | Newer OpenCog direction centered on hypergraph knowledge and the MeTTa metagraph language. | Mistral Vibe, Perplexity, Qwen3.7-Plus, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, LumoAI, ChatGPT |
| **Pogamut** | embodied agents / games | Platform for agents acting in game environments with explicit perception and action. | Grok 4.20 — ArenaAI |
| **PolyScheme** | cognitive architecture / coordination | Scheme-based cognitive architecture research on distributed processing. | Grok 4.20 — ArenaAI |
| **PRIMs** | cognitive architecture / procedural knowledge | Hierarchical procedural primitives for action and cognition. | ChatGPT |
| **PRS — Procedural Reasoning System** | agent architecture / planning | Goals, beliefs and procedures assembled into explicit deliberative behavior. | ChatGPT |
| **SAL** | cognitive architecture | Survey-identified cognitive architecture entry for later source recovery. | Grok 4.20 — ArenaAI |
| **Sigma** | cognitive architecture / unified reasoning | Factor-graph-based attempt to unify symbolic and probabilistic reasoning. | Mistral Vibe, Perplexity, Qwen3.7-Plus, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **Soar** | cognitive architecture / problem solving | Decision cycle with working memory, impasses, subgoaling, chunking and multiple long-term memories. | multiple supplied catalogs |
| **Society of Mind** | cognitive theory | Many semi-autonomous agents cooperating to create higher-level behavior. | Grok 4.20 — ArenaAI, ChatGPT |
| **Subsumption Architecture** | robotic control | Layered reactive behaviors where higher layers suppress or subsume lower ones. | Grok 4.20 — ArenaAI, ChatGPT Deep Research, ChatGPT |
| **Ymir** | cognitive architecture / dialogue | Embodied conversational-agent research architecture. | Grok 4.20 — ArenaAI |


## 02 — Memory, Knowledge & Retrieval

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **A-MEM** | agent memory | Zettelkasten-like memory evolution and linking. | Perplexity, Grok 4.20 — ArenaAI, Claude, LumoAI |
| **Apache Jena** | semantic web / reasoning | RDF, SPARQL, rule-based inference and ontology tooling. | ChatGPT |
| **AtomSpace** | knowledge hypergraph | OpenCog’s structured graph substrate for concepts and relations. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **Compressive Transformer** | compressed long context | Compresses older activations into a secondary memory. | ChatGPT |
| **ConceptNet** | commonsense knowledge | Crowdsourced semantic network connecting concepts by relations. | GPT o3 Search — ArenaAI, ChatGPT |
| **Cyc / OpenCyc** | commonsense symbolic knowledge | Very large hand-authored knowledge base and inference system. | Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT Deep Research, ChatGPT |
| **Differentiable Neural Computer** | memory-augmented neural system | External dynamic memory with allocation, temporal links and multiple heads. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT Deep Research, ChatGPT |
| **End-to-End Memory Networks** | multi-hop memory | Learned multi-hop reads over external memory representations. | ChatGPT |
| **Freebase** | knowledge graph | Historical large-scale entity/relationship knowledge base. | GPT o3 Search — ArenaAI, ChatGPT |
| **GraphRAG** | knowledge graph retrieval | Entity/relation extraction, community detection and hierarchical summaries for local/global retrieval. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, LumoAI, ChatGPT |
| **HippoRAG / HippoRAG 2** | associative long-term retrieval | Knowledge graph + associative retrieval inspired by hippocampal indexing; Personalized PageRank in original line. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **KG-RAG** | knowledge graph RAG | Family of methods combining graph relations with retrieval-augmented generation. | ChatGPT |
| **KGTK** | knowledge graph tooling | Large-graph transformation, merge, filtering and validation workflows. | ChatGPT |
| **LazyGraphRAG** | selective graph retrieval | Defers expensive graph indexing and emphasizes on-demand structure. | ChatGPT |
| **LightRAG** | lightweight graph retrieval | Graph-based organization with retrieval designed to reduce indexing/lookup overhead. | ChatGPT |
| **LongMem** | long-term external memory for LLMs | Separate memory bank enables retrieval beyond active context. | ChatGPT |
| **Mem0** | LLM memory layer | Extract/update/deduplicate persistent user and agent memories across sessions. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, LumoAI, ChatGPT |
| **Memary** | agent memory / knowledge graph | Persistent memory mixing vector and graph representations. | ChatGPT |
| **Memex** | associative information management | Historical vision of linked personal knowledge and trail-based retrieval. | ChatGPT |
| **MemGPT / Letta** | long-term agent memory | Memory paging between working/context memory, recall and archival stores; agent controls memory through tools. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **Memorizing Transformers** | approximate memory retrieval | External ANN-style memory consulted during transformer processing. | ChatGPT |
| **Memory Networks** | external memory | Explicit read/write memory accessed through attention. | ChatGPT |
| **MemoryBank** | long-term conversational memory | Persistent user-memory extraction, retrieval, updating and forgetting heuristics. | Perplexity, LumoAI, ChatGPT |
| **MemoryOS** | hierarchical LLM memory | Structured memory hierarchy for long-running agents. | ChatGPT |
| **nano-graphrag** | minimal graph RAG | Compact implementation for graph-enhanced retrieval. | ChatGPT |
| **Neo4j** | graph database / knowledge system | Property graph storage and traversal with graph algorithms and vector search. | ChatGPT |
| **Neural Turing Machine** | differentiable external memory | Neural controller learns content/location-based read/write operations. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT Deep Research, ChatGPT |
| **OpenAlex** | scholarly knowledge graph | Entities for works, authors, venues and citations in a research graph. | ChatGPT |
| **ORKG** | research knowledge graph | Structured scientific contributions and comparison templates. | ChatGPT |
| **Personal Knowledge Graphs** | personal knowledge | Entity-centered persistent graph of a user/domain. | ChatGPT |
| **RAPTOR** | hierarchical memory / retrieval | Recursive clustering and abstraction to build a tree of summaries for retrieval. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **ReadAgent** | episodic reading memory | Compresses long documents into episode-like memory for later recall. | ChatGPT |
| **Recurrent Entity Networks** | entity-centric memory | Entity-specific recurrent memory slots for tracking facts. | ChatGPT |
| **RETRO** | retrieval-augmented model | Nearest-neighbor retrieval from external corpus interleaved with generation. | ChatGPT |
| **Semantic Scholar** | scientific retrieval graph | Semantic paper search, citation networks and research corpus tooling. | ChatGPT |
| **Transformer-XL** | persistent sequence context | Segment recurrence plus relative positional representation for longer context. | ChatGPT |
| **Wikidata** | open knowledge graph | Structured entities, properties, qualifiers and references with queryable graph semantics. | GPT o3 Search — ArenaAI, ChatGPT |
| **Zep / Graphiti** | temporal agent memory | Time-aware knowledge graph with episodes, relations and validity windows. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, LumoAI, ChatGPT |
| **Zettelkasten systems** | knowledge organization | Atomic notes plus links create associative, evolving knowledge networks. | ChatGPT |


## 03 — Reasoning, Reflection & Metacognition

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **AgentCoder** | multi-agent coding | Separates code generation, testing and refinement into cooperating roles. | Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI |
| **Anthropic circuit tracing** | interpretability | Maps internal features/circuits and attribution structures in language models. | Claude |
| **CoALA** | agent architecture taxonomy | Organizes language agents around working memory, long-term memory and action spaces. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, LumoAI, ChatGPT |
| **Constitutional AI** | principle-based control | Critique-and-revise against explicit principles, with RLAIF in the training pipeline. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **CRITIC** | tool-assisted self-correction | Critique is coupled to external tool interaction before revision. | Claude, ChatGPT |
| **Gorilla** | tool/API selection | Focuses language models on reliable API invocation from large tool collections. | Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, ChatGPT |
| **Graph of Thoughts (GoT)** | reasoning graph | Generalizes linear chains and trees to arbitrary thought graphs. | Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **Language Agent Tree Search (LATS)** | reasoning / planning / search | Language-agent MCTS-like search plus reflection and environment feedback. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **Language Models Mostly Know What They Know** | self-knowledge / calibration | Studies model confidence about whether internal knowledge is available. | Claude |
| **Llama Guard** | safety classifier / control | Model-based screening layer for unsafe inputs/outputs. | GPT o3 Search — ArenaAI |
| **OpenAI Model Spec** | instruction hierarchy / control | Public behavioral specification organized around instruction priority and constraints. | Claude, ChatGPT |
| **Quiet-STaR** | internal reasoning training | Trains models to generate internal rationales during language processing. | Grok 4.20 — ArenaAI |
| **ReAct** | reasoning + action | Interleaves reasoning steps and external actions/observations rather than separating them. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **Reflexion** | self-correction / memory | Actor–evaluator–reflection loop with verbal feedback retained in episodic memory. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **Self-Refine** | iterative refinement | Generation → self-feedback → revision loop with explicit iterations. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **STaR** | reasoning self-training | Bootstraps reasoning traces by generating rationales and retaining successful solutions. | Grok 4.20 — ArenaAI, Claude, ChatGPT |
| **STaR-GATE / self-verification family** | self-verification / self-training | Family of approaches using generated solutions plus verification or consistency signals for learning. | Claude |
| **Toolformer** | self-supervised tool use | Learns when and how to insert API calls during text generation. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **Tracr** | mechanistic interpretability / compilation | Compiles explicit algorithms into transformer models to study internal representations. | GPT o3 Search — ArenaAI |
| **Tree of Thoughts** | search over reasoning | Branches partial solution states, evaluates them and searches with BFS/DFS-style control. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, LumoAI, ChatGPT |


## 04 — Agents, Orchestration & Tool Use

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **AG2** | multi-agent framework | Community continuation of the AutoGen 0.2 lineage with conversational agents. | Qwen3.7-Plus, LumoAI |
| **AgentCoder** | coding agent ensemble | Separate generator/tester/refiner roles around software artifacts. | Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI |
| **AgentVerse** | multi-agent simulation framework | Reusable infrastructure for agent environments and collective behavior. | GPT o3 Search — ArenaAI, ChatGPT |
| **Agno** | agent framework | Lightweight agent framework appearing in 2026 production catalogs. | LumoAI |
| **AutoGPT** | autonomous agent framework | Classic task-creation → execution → prioritization loop with memory/tool integration. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT Deep Research, LumoAI, ChatGPT |
| **BabyAGI** | minimal autonomous task loop | Simple execute → create next tasks → prioritize loop with vector memory in the original popular prototype. | GPT o3 Search — ArenaAI, Claude, ChatGPT Deep Research, LumoAI, ChatGPT |
| **CAMEL** | multi-agent communication | Role-playing and task specification for collaborating language agents. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **ChatDev** | multi-agent software development | Company-like agent roles coordinated to produce software artifacts. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, ChatGPT |
| **Claude Agent SDK** | agent runtime / coding systems | Tool-driven agent framework derived from the Claude Code lineage. | LumoAI |
| **CrewAI** | role-based multi-agent orchestration | Agents, Crews and Flows organize role/task-based collaboration. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **DSPy** | declarative LM programming | Programs as modules/signatures with optimizers compiling behavior against metrics. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **Google ADK** | agent development framework | LLM agents plus deterministic sequential/parallel/loop workflow controllers. | Qwen3.7-Plus, LumoAI, ChatGPT |
| **GPT Researcher** | research workflow agent | Planner/searcher/writer style autonomous research workflow. | Claude, LumoAI, ChatGPT |
| **Haystack** | pipeline / agent framework | Component graphs, branching/loops, retrievers, agents and evaluation. | ChatGPT |
| **Jina DeepResearch** | research agent | Research-oriented long-running agent workflow. | ChatGPT |
| **LangChain** | LLM application framework | Composable tools, retrievers, chains and agent abstractions; large ecosystem. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **LangGraph** | stateful agent orchestration | Graph state, conditional routing, checkpoints, interrupts and durable execution. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **LlamaIndex** | data/agent framework | Ingestion, indexing, retrieval, knowledge graphs, memory and workflow tooling. | GPT o3 Search — ArenaAI, ChatGPT |
| **Manus** | commercial agent system | Long-running agent execution system; internal mechanisms largely undisclosed. | ChatGPT |
| **Mastra** | agent orchestration framework | Modern TypeScript-oriented agent/workflow framework in 2026 catalogs. | LumoAI |
| **MetaGPT** | multi-agent software engineering | Roles + SOPs + shared artifacts model a software-development organization. | Mistral Vibe, Perplexity, Qwen3.7-Plus, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **Microsoft Agent Framework** | agent orchestration | Converges AutoGen/Semantic Kernel ideas around agents and workflow execution. | Qwen3.7-Plus, LumoAI, ChatGPT |
| **Microsoft AutoGen** | multi-agent framework | Message/event-driven agent interaction and distributed runtime abstractions. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **Open Interpreter** | computer/tool agent | Language model generates and executes code through an interpreter with environment interaction. | Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT Deep Research, ChatGPT |
| **OpenAI Agents SDK** | agent runtime / handoffs | Minimal primitives around agent loops, tools, handoffs, sessions, guardrails and tracing. | LumoAI, ChatGPT |
| **OpenAI Swarm** | agent handoffs | Small experimental framework showing handoff-driven multi-agent control. | Grok 4.20 — ArenaAI, ChatGPT |
| **OpenHands / OpenDevin** | autonomous coding agent | Event-driven agent loop, tool registry, runtime, context condensation and safety controls. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT Deep Research, ChatGPT, technical deep dives |
| **PydanticAI** | typed agent framework | Typed validation/contracts around agent inputs, outputs and tools. | LumoAI |
| **Semantic Kernel** | agent / plugin framework | Plugins, functions, planners/processes and agent orchestration around application code. | Perplexity, Qwen3.7-Plus, GPT o3 Search — ArenaAI, LumoAI, ChatGPT |
| **Strands Agents** | agent framework | Framework family for building agent workflows and integrating observability. | LumoAI |
| **SWE-agent** | coding agent / ACI | Agent–computer interface optimized around repo navigation, edits, tests and issue resolution. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |


## 05 — Planning, Formal Reasoning & Search

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **Agent57** | RL exploration | Meta-controller blending multiple exploration and value mechanisms. | ChatGPT |
| **Alloy** | relational verification | Relational logic translated into bounded model-finding problems. | ChatGPT |
| **AlphaGeometry** | neuro-symbolic geometry | Neural language guidance paired with symbolic deduction/search in geometry. | Mistral Vibe, Perplexity, Qwen3.7-Plus, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, ChatGPT |
| **AlphaGeometry2** | neuro-symbolic geometry | Later AlphaGeometry system extending neural-symbolic theorem proving. | ChatGPT |
| **AlphaZero** | self-play planning | Policy/value networks plus MCTS and self-generated experience. | Mistral Vibe, Perplexity, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **Dreamer / DreamerV2 / DreamerV3** | world-model RL | Learns latent dynamics and improves policy using imagined trajectories. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, LumoAI, ChatGPT |
| **e-graphs / egg** | equational reasoning | Compactly represent many equivalent expressions and extract an optimized representative. | Mistral Vibe, Perplexity, ChatGPT |
| **Fast Downward** | classical automated planning | Translation to finite-domain representations plus heuristic state-space search. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **Go-Explore** | exploration / return | Archive promising states, explore from them, then robustify discovered trajectories. | ChatGPT |
| **HDDL** | HTN problem language | Standardized hierarchical planning problem description. | ChatGPT |
| **HTN planning family** | hierarchical decision making | Methods decompose abstract tasks into executable subtasks. | LumoAI, ChatGPT |
| **Lean 4** | theorem proving | Dependent type theory with programmable proof automation. | Mistral Vibe, Perplexity, Qwen3.7-Plus, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, ChatGPT |
| **LeanDojo** | formal theorem-proving environment | Data/tooling bridge between Lean proofs and machine-learning theorem provers. | Qwen3.7-Plus, ChatGPT |
| **Mathlib** | formal mathematics library | Large reusable corpus of definitions, theorems and proofs for Lean. | Mistral Vibe, Perplexity, Qwen3.7-Plus, GPT o3 Search — ArenaAI, ChatGPT |
| **MCTS** | planning/search mechanism | Selection → expansion → simulation → backup with exploration/exploitation control. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **MiniZinc** | constraint modeling | High-level constraint model compiled to multiple solver backends. | ChatGPT |
| **MuZero** | learned-model planning | Learns latent dynamics/value/policy and plans with MCTS without explicit environment rules. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **Never Give Up** | exploration | Intrinsic motivation designed to sustain exploration in complex environments. | ChatGPT |
| **NGU** | episodic/lifelong exploration | Combines episodic novelty with lifelong intrinsic motivation. | ChatGPT |
| **OR-Tools** | optimization / scheduling | Constraint programming, routing, linear/integer optimization and scheduling. | ChatGPT |
| **PDDL** | planning formalism | Declarative domain/problem description via predicates, actions, preconditions and effects. | Mistral Vibe, Perplexity, GPT o3 Search — ArenaAI, ChatGPT |
| **PDDLStream** | planning + external computation | Extends symbolic planning with streams that bind continuous/external computations. | GPT o3 Search — ArenaAI |
| **PlaNet** | world-model RL | Latent recurrent dynamics model used for model-based control. | ChatGPT |
| **PRISM** | probabilistic verification | Probabilistic model checking for stochastic systems. | ChatGPT |
| **RND** | novelty exploration | Random-network prediction error acts as intrinsic novelty signal. | ChatGPT |
| **SAT / CP solvers** | formal constraint reasoning | Discrete constraint propagation and search for satisfiable assignments. | Mistral Vibe, GPT o3 Search — ArenaAI, ChatGPT |
| **SHOP2** | HTN planning | Hierarchical task decomposition with methods and ordered subtasks. | Perplexity, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **SPIN** | model checking | Formal state exploration for concurrent systems. | ChatGPT |
| **TD-MPC2** | predictive control | Latent model-based RL / trajectory optimization mechanism. | ChatGPT |
| **TLA+** | formal system specification | State-transition specifications with model checking and invariant reasoning. | ChatGPT |
| **Unified Planning** | planning interoperability | Common problem representation and adapters for multiple planning engines. | ChatGPT |
| **Z3** | SMT solving | Constraint solving across theories through SMT search and propagation. | GPT o3 Search — ArenaAI, ChatGPT |


## 06 — Learning, RL & Adaptation

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **AlphaStar** | multi-agent game AI | Large-scale population training, league dynamics and strategic self-play. | GPT o3 Search — ArenaAI |
| **Avalanche** | continual learning | Unified streams, replay/regularization strategies and evaluation protocols for continual learning. | ChatGPT |
| **CleanRL** | transparent RL implementations | Readable single-file algorithm implementations optimized for inspection. | ChatGPT |
| **Decision Transformers** | offline RL | Treats trajectory return-to-go as conditioning for sequence-model-based action prediction. | LumoAI, ChatGPT |
| **DreamCoder** | program synthesis / abstraction learning | Synthesizes programs while learning reusable abstractions. | ChatGPT |
| **Enhanced POET** | open-ended evolution | Extensions of environment/agent coevolution from POET line. | ChatGPT |
| **Eureka** | LLM reward design | Language model generates and refines reward functions for RL. | ChatGPT |
| **EWC** | continual learning mechanism | Fisher-weighted regularization protects parameters important to previous tasks. | ChatGPT |
| **Gato** | generalist agent model | Single transformer policy trained across many tasks/modalities. | Perplexity, GPT o3 Search — ArenaAI |
| **Gato / generalist sequence models** | multi-task learning | Shared model across heterogeneous embodied and simulated tasks. | GPT o3 Search — ArenaAI |
| **Mava** | multi-agent RL | Distributed multi-agent learning with centralized/decentralized training patterns. | Qwen3.7-Plus, ChatGPT |
| **PBT** | population-based training | Optimizes training configurations by evolving a population during learning. | ChatGPT |
| **POET** | open-ended evolution | Coevolves agents and environments to create increasingly challenging tasks. | ChatGPT |
| **Progressive Neural Networks** | continual/transfer learning | Adds new network columns while preserving access to previous representations. | ChatGPT |
| **Ray / RLlib** | distributed AI/RL infrastructure | Scales reinforcement learning and multi-agent training across workers and environments. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **River** | online learning | Incremental model updates, streaming statistics, drift detection and anomaly detection. | Mistral Vibe, Perplexity, GPT o3 Search — ArenaAI, ChatGPT |
| **Tianshou** | RL framework | Modular policies, collectors, replay buffers and trainers. | ChatGPT |
| **TorchRL** | RL framework | TensorDict-based environment, collector, buffer and loss abstractions. | ChatGPT |


## 07 — Neural Architectures, World Models & Open Models

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **DeepSeek R1** | reasoning model | Open reasoning-model family emphasizing large-scale reinforcement/training for reasoning. | LumoAI, ChatGPT |
| **Falcon 180B** | open-weight LLM | Large open model from TII, useful as a historical open-model milestone. | LumoAI, ChatGPT |
| **HTM / NuPIC** | biologically inspired sequence learning | Sparse distributed representations, spatial pooling, temporal memory and anomaly detection. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **JEPA / I-JEPA / V-JEPA** | self-supervised world modeling | Predicts in latent representation space rather than reconstructing raw observations. | Qwen3.7-Plus, Grok 4.20 — ArenaAI, Claude, LumoAI |
| **Llama family** | open-weight language models | Large open-weight transformer ecosystem with extensive fine-tuning/tooling. | LumoAI, ChatGPT |
| **Mamba** | state-space sequence model | Selective state-space recurrence designed for linear-time sequence processing. | Qwen3.7-Plus, Grok 4.20 — ArenaAI, LumoAI, ChatGPT |
| **Mistral / Mixtral** | open-weight language models | Efficient transformer and MoE designs with strong multilingual/open-weight ecosystem. | LumoAI, ChatGPT |
| **NTM / DNC family** | memory-augmented neural systems | Neural controllers coupled to explicit differentiable memory. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **OLMo** | open LLM | AllenAI model line emphasizing transparent/open research artifacts. | LumoAI, ChatGPT |
| **Qwen family** | open model ecosystem | Broad multilingual, multimodal and reasoning model family. | Qwen3.7-Plus, LumoAI, ChatGPT |
| **Thousand Brains / Monty** | sensorimotor world model | Reference-frame-based sensory learning and predictive sensorimotor inference. | Mistral Vibe, Grok 4.20 — ArenaAI, ChatGPT |
| **Transformer** | neural architecture | Self-attention and feed-forward blocks as the dominant sequence modeling substrate. | LumoAI, ChatGPT |


## 08 — Neural, Spiking & Brain-Inspired Systems

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **Allen Brain Atlas** | neuroscience data | Cell types, connectivity and molecular/anatomical maps. | ChatGPT |
| **BindsNET** | SNN simulation | Python/PyTorch environment for spiking learning algorithms. | ChatGPT |
| **Brian2** | spiking neural simulator | Flexible Python-based spiking-network simulation with equation-level model definition. | Qwen3.7-Plus, GPT o3 Search — ArenaAI, ChatGPT |
| **FlyWire** | connectome reconstruction | Detailed connectome reconstruction and annotation for fly brains. | ChatGPT |
| **Lava / Loihi 2** | neuromorphic computing | Event-driven neural computation designed around Intel Loihi ecosystems. | Qwen3.7-Plus |
| **MICrONS** | connectomics | Large-scale functional + anatomical neural connectivity datasets. | ChatGPT |
| **Nengo / Semantic Pointer Architecture** | neural cognitive modeling | Neural Engineering Framework with vector symbolic binding and spiking implementations. | Mistral Vibe, Perplexity, Qwen3.7-Plus, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT Deep Research, ChatGPT |
| **NEST** | large-scale neural simulation | Simulator focused on large networks of spiking neurons. | ChatGPT |
| **NetPyNE** | neural network modeling | High-level construction, simulation and analysis of neuronal networks. | ChatGPT |
| **NeuroCoreX** | neuromorphic / SNN research | Source-lead candidate for neuromorphic/spiking computation. | Qwen3.7-Plus |
| **NeuroML** | formal neural model description | Standardized representation of neuronal and network models. | ChatGPT |
| **Norse** | SNN deep learning | PyTorch-based spiking neural network components. | ChatGPT |
| **ODIN** | spiking / neuromorphic research | Source-lead candidate for efficient spiking systems. | Qwen3.7-Plus |
| **ReckOn** | spiking / neuromorphic research | Source-lead candidate for neural event processing. | Qwen3.7-Plus |
| **Spaun** | neural cognitive model | Large-scale functional brain model executing perception, reasoning and motor tasks. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT Deep Research, ChatGPT |
| **SpikingJelly** | SNN toolkit | Deep-learning-style spiking neural network training and simulation toolkit. | Qwen3.7-Plus |
| **The Virtual Brain** | brain dynamics | Large-scale brain-network simulation and personalized dynamical modeling. | ChatGPT |


## 09 — Active Inference, Predictive Processing & Adaptive Inference

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **Active Inference ecosystem** | predictive processing / decision making | Family of agents built around generative models, belief updating and expected free energy. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **Complementary Learning Systems** | memory theory | Fast hippocampal learning coupled with slower cortical consolidation. | Claude, ChatGPT |
| **Dynamic Expectation Maximization (DEM)** | predictive processing / state estimation | Hierarchical dynamic Bayesian estimation and learning. | Claude, ChatGPT |
| **FabricPC** | predictive coding | Research implementation/candidate around predictive-coding architectures. | Qwen3.7-Plus |
| **Predictive coding** | foundational mechanism | Hierarchical prediction errors as a mechanism for perception/inference. | Qwen3.7-Plus, Claude, LumoAI, ChatGPT |
| **PyHGF / HGFX** | hierarchical Gaussian filtering | Bayesian belief updating for changing latent states and volatility. | Qwen3.7-Plus |
| **pymdp** | active inference implementation | Discrete-state active inference with beliefs, policies and expected free energy. | Mistral Vibe, Perplexity, Qwen3.7-Plus, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, LumoAI, ChatGPT |
| **RxInfer** | Bayesian state inference | Message-passing and probabilistic inference framework in Julia. | Qwen3.7-Plus, Claude, ChatGPT |
| **SPM** | computational neuroscience / Bayesian models | Variational Bayesian inference, DCM and generative models in neuroscience. | Claude, ChatGPT |


## 10 — Robotics & Embodied Cognition

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **AI2-THOR** | embodied environment | Interactive 3D environment for embodied navigation and manipulation agents. | Qwen3.7-Plus, GPT o3 Search — ArenaAI |
| **BabyAI** | symbolic/embodied learning | Small gridworlds with language-conditioned tasks and compositional instruction following. | Qwen3.7-Plus, GPT o3 Search — ArenaAI |
| **BehaviorTree.CPP** | control orchestration | Sequence/fallback/reactive nodes, blackboard, decorators and asynchronous actions. | Mistral Vibe, Perplexity, GPT o3 Search — ArenaAI, ChatGPT |
| **Isaac ROS** | robot perception/acceleration | GPU-accelerated perception and ROS 2 components. | ChatGPT |
| **MoveIt 2** | robot manipulation | Planning scene, collision checking, kinematics and trajectory execution. | ChatGPT |
| **Nav2** | robot navigation | Planner/controller/behavior servers, costmaps, lifecycle and recovery behavior. | Mistral Vibe, GPT o3 Search — ArenaAI, ChatGPT |
| **Open-RMF** | robot fleet coordination | Task allocation, traffic scheduling, fleet adapters and resource negotiation. | ChatGPT |
| **OpenCog Robotics** | cognitive robotics | Embodied perception, knowledge, planning and action integration. | Qwen3.7-Plus, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **ROS 2** | robotics infrastructure | Distributed nodes, topics, services, actions, lifecycle, QoS and executors. | Mistral Vibe, Perplexity, GPT o3 Search — ArenaAI, ChatGPT |


## 11 — Multi-Agent Systems & Social Simulation

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **Concordia** | social simulation / agent architecture | Framework for simulating interactive agents and social dynamics. | Perplexity, Grok 4.20 — ArenaAI |
| **Generative Agents / Smallville** | social simulation | Memory stream + reflection + planning in a multi-agent social world. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **Generative social agents** | multi-agent simulation family | Agent-based social simulation using memory, goals, roles and interaction histories. | Perplexity, Grok 4.20 — ArenaAI, Claude, LumoAI, ChatGPT |
| **MAgent2** | many-agent RL | Large populations of grid-based agents for collective behavior studies. | GPT o3 Search — ArenaAI, ChatGPT |
| **Mava** | multi-agent RL framework | Population training with centralized/decentralized execution patterns. | Qwen3.7-Plus, ChatGPT |
| **Melting Pot** | social intelligence benchmark | Large suite of social dilemmas, cooperation, competition and held-out evaluations. | Mistral Vibe, Perplexity, GPT o3 Search — ArenaAI, ChatGPT |
| **OpenSpiel** | game theory / MARL | Formal multi-agent game states, imperfect information and equilibrium/search algorithms. | GPT o3 Search — ArenaAI, ChatGPT |
| **PettingZoo** | multi-agent environment API | Standardized sequential/parallel APIs for diverse multi-agent environments. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **PettingZoo MPE** | multi-agent benchmark environments | Simple cooperative/competitive particle worlds with local observations and communication. | GPT o3 Search — ArenaAI, ChatGPT |


## 12 — Scientific AI, Discovery & Research Agents

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **AI Scientist** | automated scientific workflow | Idea generation → experiment code → execution → analysis → paper generation/review. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, LumoAI, ChatGPT |
| **AI2-THOR / ScienceWorld / ALFWorld** | interactive research environments | Formal environments for testing agents on embodied, scientific and household tasks. | Perplexity, Qwen3.7-Plus, GPT o3 Search — ArenaAI, ChatGPT |
| **AlphaEvolve** | evolutionary program discovery | LLM-guided program evolution around external evaluators. | Claude, LumoAI, ChatGPT |
| **AutoScholar** | scientific research automation | Research-agent candidate around literature and scientific workflow automation. | GPT o3 Search — ArenaAI, ChatGPT |
| **ChemCrow** | chemistry agent | Language-agent tools for chemical reasoning and experiment planning. | GPT o3 Search — ArenaAI, ChatGPT |
| **Coscientist** | automated chemistry / science | LLM-driven scientific planning and laboratory-action workflow. | Mistral Vibe, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude |
| **Darwin Gödel Machine** | self-improving code agent | Maintains archive of agent variants and searches for self-improvements via code changes. | Grok 4.20 — ArenaAI, Claude, LumoAI |
| **DENDRAL** | expert scientific system | Early automated hypothesis generation in chemistry using symbolic reasoning. | Claude, ChatGPT Deep Research, ChatGPT |
| **EURISKO** | heuristic discovery | System for exploring and evolving heuristics for problem solving. | Mistral Vibe, Grok 4.20 — ArenaAI, ChatGPT Deep Research |
| **FunSearch** | program search | Generate candidate programs and evaluate them externally, retaining strong variants. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, LumoAI, ChatGPT |
| **Google AI co-scientist** | scientific hypothesis generation | Multi-agent hypothesis proposal, critique/tournament and evidence gathering. | Mistral Vibe, Claude, LumoAI, ChatGPT |
| **GPT Researcher** | research workflow | Autonomous research task decomposition, web retrieval and synthesis. | Claude, LumoAI, ChatGPT |
| **Gödel Machine** | theoretical self-improvement | Utility-improving self-rewrite when a proof establishes improvement. | Grok 4.20 — ArenaAI, Claude, ChatGPT |
| **MARTI** | scientific/technical agent system | Research lead candidate in the source catalog for automated scientific reasoning. | Mistral Vibe, Grok 4.20 — ArenaAI |
| **MYCIN** | expert system / diagnosis | Rule-based medical reasoning with explicit confidence/knowledge structures. | Mistral Vibe, Claude, ChatGPT Deep Research |
| **PaperQA / PaperQA2** | scientific evidence retrieval | Literature ingestion, semantic retrieval, reranking, evidence extraction and citation-aware answers. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **Robot Scientist Adam** | automated scientific discovery | Robotized hypothesis generation, experiment execution and model comparison in biology. | Claude, ChatGPT Deep Research |
| **Robot Scientist Eve** | automated scientific discovery | Automated experimental screening and hypothesis testing in biology/medicine. | Claude, ChatGPT Deep Research |
| **STORM** | research synthesis | Perspective-guided questioning, source discovery, interviews and cited synthesis. | Mistral Vibe, Perplexity, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, LumoAI, ChatGPT |


## 13 — Safety, Provenance, Observability & Evaluation

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **AgentBench** | agent benchmark | Benchmark family for evaluating general agent capabilities across environments. | Mistral Vibe, Perplexity, GPT o3 Search — ArenaAI, ChatGPT |
| **Apache Airflow** | workflow orchestration | DAG scheduling, retries, dependencies, sensors and task-state management. | Mistral Vibe, GPT o3 Search — ArenaAI, ChatGPT |
| **BrowserGym** | browser agent environment | Unified browser interaction environment and benchmark interface. | ChatGPT |
| **Dagster** | data/workflow orchestration | Asset-aware orchestration, lineage and typed pipeline components. | GPT o3 Search — ArenaAI, LumoAI |
| **GAIA** | general assistant benchmark | Cross-domain assistant tasks requiring tools, browsing and multi-step reasoning. | GPT o3 Search — ArenaAI, ChatGPT |
| **in-toto** | software provenance | Signed supply-chain attestations linking artifacts to build steps and actors. | Mistral Vibe, GPT o3 Search — ArenaAI, ChatGPT |
| **Inspect AI** | agent evaluation framework | Solver/scorer abstraction, sandboxed tasks, trajectories and evaluation tooling. | Mistral Vibe, Perplexity, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **LangSmith** | LLM tracing/evaluation | Run trees, traces, datasets, evaluators and regression monitoring. | Perplexity, GPT o3 Search — ArenaAI, ChatGPT |
| **METR evals** | agent reliability evaluation | Task-based measurement of autonomous capabilities and risk-relevant behaviors. | Mistral Vibe, GPT o3 Search — ArenaAI |
| **MLflow** | experiment/model lineage | Tracks runs, artifacts, model versions and experiment lineage. | Perplexity, GPT o3 Search — ArenaAI, ChatGPT |
| **Model policy / guardrail frameworks** | AI safety/control | Guarding model I/O and tool actions through explicit policy layers. | Mistral Vibe, Qwen3.7-Plus, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, LumoAI, ChatGPT |
| **OPA** | policy enforcement | Externalized rule evaluation via Rego and structured decision inputs. | ChatGPT |
| **OpenTelemetry** | distributed observability | Traces, spans, context propagation, metrics and logs across systems. | Perplexity, GPT o3 Search — ArenaAI, ChatGPT |
| **ProvDB** | data provenance | Tracking derivations and provenance of experimental/data artifacts. | GPT o3 Search — ArenaAI |
| **Safety Gym / Safe-RL** | safe RL environment/evaluation | Benchmarks for learning policies under safety constraints. | GPT o3 Search — ArenaAI, ChatGPT |
| **SLSA** | software supply-chain security | Framework for verifiable build provenance and increasing assurance levels. | GPT o3 Search — ArenaAI, ChatGPT |
| **SWE-bench** | coding-agent benchmark | Real GitHub issues as executable tests of software engineering agents. | Mistral Vibe, Perplexity, GPT o3 Search — ArenaAI, Claude, ChatGPT Deep Research, LumoAI, ChatGPT |
| **Temporal** | durable execution | Event history + deterministic replay + durable workflows, retries and timers. | Mistral Vibe, Perplexity, Qwen3.7-Plus, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, ChatGPT |
| **W3C PROV** | provenance standard | Formal model of entities, activities, agents, derivations and attribution. | ChatGPT |
| **WebArena** | browser agent benchmark | Realistic web environments for task completion and browsing agents. | ChatGPT |
| **WebShop** | interactive web task environment | Shopping website environment for language agents. | ChatGPT |
| **yesWorkflow** | workflow/provenance extraction | Infers workflow structure from code annotations/comments. | GPT o3 Search — ArenaAI |


## 14 — Protocols, Infrastructure & Durable Execution

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **A2A / Agent2Agent** | agent interoperability protocol | Standardized agent-to-agent discovery, messaging and task handoff concepts. | Mistral Vibe, Perplexity, Qwen3.7-Plus, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI |
| **ACP** | agent communication protocol | Additional agent communication/protocol candidate in the source catalogs. | Qwen3.7-Plus |
| **Akka** | actor runtime | Actor model, supervision, messaging and distributed coordination. | ChatGPT |
| **Apache Flink** | stateful stream processing | Distributed stateful computations over event streams with checkpoints. | ChatGPT |
| **Apache Kafka** | event log infrastructure | Durable ordered partitions and consumer offsets as system memory substrate. | ChatGPT |
| **DataHub** | metadata / lineage | Central metadata catalog and lineage graph. | GPT o3 Search — ArenaAI |
| **Erlang/OTP** | fault-tolerant actor runtime | Supervision trees, processes, message passing and recovery. | ChatGPT |
| **EventStoreDB** | event sourcing | Append-only event streams as the source of truth for state reconstruction. | ChatGPT |
| **Kubernetes Controllers** | control loop infrastructure | Desired-state reconciliation loops with observed-state feedback. | ChatGPT |
| **Kubernetes Operators** | declarative automation | Domain-specific controllers extending reconciliation patterns. | ChatGPT |
| **Milvus** | vector database | Large-scale vector storage/retrieval infrastructure for memory and RAG. | GPT o3 Search — ArenaAI |
| **Model Context Protocol (MCP)** | tool/resource protocol | Standard primitives for tools, resources and prompts with capability negotiation. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **NATS JetStream** | persistent messaging | Durable event streams, consumers and message replay. | ChatGPT |
| **Orleans** | virtual actor runtime | Distributed virtual actors with activation, persistence and messaging. | ChatGPT |
| **Pachyderm** | data lineage / pipelines | Data versioning and reproducible data-processing pipelines. | GPT o3 Search — ArenaAI |
| **Ray** | distributed compute | Distributed tasks/actors and infrastructure for scaling agents/RL. | LumoAI, ChatGPT |


## 15 — Symbolic Systems, Logic & Neuro-Symbolic Methods

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **AlphaGeometry** | neuro-symbolic proving | Neural proposal mechanism combined with symbolic geometric deduction/search. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **BabyAI** | symbolic embodied tasks | Language-conditioned discrete environments emphasizing compositional instruction following. | Qwen3.7-Plus, GPT o3 Search — ArenaAI, ChatGPT |
| **CLIPS** | expert system | Classic production-rule engine with working memory and pattern matching. | ChatGPT |
| **Datalog / Soufflé** | logic programming | Rule-based recursive inference over relations. | ChatGPT |
| **Drools** | rule engine | Production rules, agenda/working-memory execution and rule evaluation. | ChatGPT |
| **e-graphs / egg** | equivalence reasoning | Many equivalent expressions represented compactly for rewrite-based optimization. | Mistral Vibe, Perplexity, ChatGPT |
| **Jess** | rule engine | Java-based production-rule reasoning in the CLIPS tradition. | ChatGPT |
| **Lean 4 / Mathlib** | formal mathematics | Proof-producing dependent type theory and large formal theorem library. | multiple supplied catalogs (exact overlap to be resolved in provenance audit) |
| **MRKL** | modular reasoning / tools | Routes questions to specialized symbolic or external expert modules. | Qwen3.7-Plus |
| **PDDLStream** | task-motion planning | Symbolic plans coupled to sampled/external computations. | GPT o3 Search — ArenaAI, ChatGPT |
| **Prolog / SWI-Prolog** | logic programming | Unification, backtracking, declarative rules and symbolic search. | ChatGPT |


## 16 — Brain Simulation, Connectomics & Biological Systems

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **Allen Brain Atlas** | neural cell/connectivity data | Cell-type, gene-expression and anatomical reference datasets. | ChatGPT |
| **Allen Cell Types** | neural cell taxonomy | Detailed classification of neuronal cell types. | ChatGPT |
| **Blue Brain Project** | multiscale brain simulation | Detailed cellular/synaptic reconstruction and large-scale simulation infrastructure. | Claude, ChatGPT Deep Research, ChatGPT |
| **C. elegans OpenWorm** | connectome / organism simulation | Connectome-driven simulation and modeling of C. elegans. | Mistral Vibe, Perplexity, Qwen3.7-Plus, Grok 4.20 — ArenaAI, GPT o3 Search — ArenaAI, Claude, ChatGPT |
| **EBRAINS** | neuroscience platform | Access layer for brain datasets, models, simulation and workflows. | ChatGPT |
| **FlyWire** | connectomics | Large-scale reconstruction and annotation of fly neural connectivity. | ChatGPT |
| **Human Brain Project** | brain simulation / data infrastructure | European-scale neuroscience infrastructure integrating models, data and simulation. | ChatGPT |
| **Human Connectome Project** | brain connectivity | Macroscale structural/functional connectivity maps. | ChatGPT |
| **MICrONS** | connectomics + functional data | Large-scale alignment of structure and function in cortical tissue. | ChatGPT |


## 17 — Historical, Scientific & Meta-Research Systems

| Projekt | Rola | Co go wyróżnia | Źródła wskazania (provenance lead) |
|---|---|---|---|
| **AlphaFold** | scientific prediction | Deep-learning system for protein structure prediction. | Perplexity, GPT o3 Search — ArenaAI |
| **AlphaStar** | game-playing / MARL | Population-based multi-agent training and strategic adaptation. | GPT o3 Search — ArenaAI |
| **Awesome-LLM collections** | curated research corpus | Community-maintained index of model families and implementations. | LumoAI, ChatGPT |
| **DENDRAL** | scientific expert system | Symbolic hypothesis generation for molecular structure elucidation. | Claude, ChatGPT Deep Research, ChatGPT |
| **EURISKO** | heuristic search/discovery | Self-evolving heuristic rules for problem solving and invention. | Mistral Vibe, Grok 4.20 — ArenaAI, ChatGPT Deep Research |
| **IBM Watson Discovery** | enterprise knowledge system | Document retrieval, ranking and knowledge extraction. | GPT o3 Search — ArenaAI |
| **MYCIN** | medical expert system | Rule-based diagnosis with explicit uncertainty/confidence handling. | Mistral Vibe, Claude, ChatGPT Deep Research, ChatGPT |
| **Papers with Code** | research metadata | Connects papers, code repositories, benchmarks and tasks. | Grok 4.20 — ArenaAI, Claude, ChatGPT |
| **Project Debater** | argumentation system | Large-scale argument retrieval, evidence and speech generation. | GPT o3 Search — ArenaAI |
| **Society of Mind** | cognitive theory | Multi-agent theory of mind built from interacting simple components. | Grok 4.20 — ArenaAI, ChatGPT |


---

## 4. RELACJE, ALIASY I GENERACJE

| Relacja | Jak ją czytać |
|---|---|
| **MemGPT → Letta** | Letta is the current project/runtime continuation of the MemGPT lineage; keep paper-era MemGPT and current Letta as related entities. |
| **OpenCog Classic → OpenCog Hyperon / MeTTa** | Related generations, not one immutable implementation. |
| **AutoGen → AG2** | AG2 is a community continuation/fork of the older AutoGen 0.2 lineage; preserve versions and provenance. |
| **AutoGen → Microsoft Agent Framework** | Related by Microsoft project lineage/convergence; not the same implementation. |
| **OpenDevin → OpenHands** | Renaming/project continuation relationship. |
| **Nengo → Spaun** | Spaun is a major cognitive/neural model built using the Nengo/NEF ecosystem. |
| **HTM → NuPIC** | HTM is the theory/family; NuPIC is an implementation ecosystem. |
| **Zep → Graphiti** | Graphiti is the open-source temporal graph memory substrate associated with Zep. |
| **Dreamer → DreamerV3** | Generational family; mechanisms evolve between versions. |
| **HippoRAG → HippoRAG 2** | Related versions/continuation; retain paper-specific claims. |
| **GraphRAG → LazyGraphRAG** | Related retrieval family; not interchangeable implementations. |
| **Generative Agents → Generative Memory** | The latter is a mechanism/family label extracted from the original architecture, not an independent project. |

### Typowe zjawiska duplikacyjne
- jedna nazwa opisuje **rodzinę mechanizmów**, a inna konkretną implementację;
- ten sam projekt zmienia nazwę lub organizację repozytorium;
- paper ma inną nazwę niż kod;
- framework zawiera mechanizm znany z osobnego paperu;
- wersja historyczna i współczesna mają wspólną genealogię, ale nieidentyczny runtime;

---

## 5. ŹRÓDŁOWA MAPA ROZBIEŻNOŚCI

Nie interpretujemy różnicy liczby wzmianek jako „lepszy/gorszy researcher”. Wartość tej warstwy polega na tym, że różne katalogi mają różne **pola widzenia**.

### Silny wspólny rdzeń
W wielu niezależnych katalogach powtarzają się m.in.: **ACT-R, Soar, CLARION, LIDA, OpenCog, Sigma, LangChain/LangGraph, AutoGen, CrewAI, MemGPT/Letta, Mem0, Zep/Graphiti, Reflexion, ReAct, Tree of Thoughts/LATS, Active Inference, HTM/NuPIC, Nengo/Spaun, Fast Downward, Dreamer/MuZero, MCP**. Taki powtarzalny rdzeń jest dobrym kandydatem do późniejszego porównania mechanizm-po-mechanizmie, ale sam w sobie nie jest dowodem jakości.

### Źródła o charakterystycznym profilu
- **Claude** wniósł obszerny materiał architektoniczny z mocnym rozróżnieniem implementacji, źródeł i ograniczeń oraz rozbudowany katalog z pamięci, agentów, neuronauki i provenance.
- **ChatGPT Deep Research** dostarczył szczegółowe karty klasycznych architektur oraz kilku dużych systemów pamięci/neuro/agent.
- **LumoAI** poszerzył korpus o współczesne frameworki, modele otwarte, pamięć, active inference i dodatkowe kandydaty z 2025–2026.
- **Zwykły ChatGPT** dostarczył najszerszy jawny katalog kategorii i dodatkowych rodzin, włącznie z formal methods, robotyką, neuroscience, control i knowledge systems.
- **Grok 4.20 / GPT o3 Search (ArenaAI)** wniosły bardzo szerokie pole historycznych architektur kognitywnych, systemów agentowych, RL, robotyki i infrastruktury.
- **Mistral Vibe / Perplexity / Qwen3.7-Plus** rozszerzały szczególnie rodziny cognitive architectures, agent frameworks, active inference, SNN, memory oraz formal/neuro-symbolic.

---

## 6. MATERIAŁ TECHNICZNY — ODDZIELNY OD KATALOGU PROJEKTÓW

Część wcześniejszej pracy nie była kolejnym „katalogiem modeli”, lecz wejściem do konkretnych artefaktów technicznych. To bardzo istotne, bo właśnie tam pojawiły się **kanoniczne jednostki ASMA**.

### Anthropic / Claude Code
- capability-bounded subagent delegation
- authorization + reversibility checks przed operacją
- hook feedback integration
- structured task progress / TodoWrite
- task-type → subagent-type routing.

### Cursor
- semantic search refinement loop:
`broad query → inspect → narrow → inspect again`
- symbol-aware/selective retrieval:
`discover structure → select symbol → read content`.

### Google Antigravity
- knowledge-item retrieval with provenance/history
- symbol-aware file retrieval
- scheduling / ordering controls
- structured task tooling.

### OpenHands
- event-driven reasoning–action loop
- append-only event log jako pamięć historii
- two-phase context condensation
- manual `CondensationRequest`,
- security analyzer + confirmation policy boundary
- tool registry + semantic annotations
- conversation state + replay
- local/remote backend separation.

Te rekordy są **materiałem pierwszego rzędu do ASMA**, ponieważ pochodzą z kodu i dokumentacji, a nie tylko z opisów projektowych.

---

## 7. META-MECHANIZMY, KTÓRE JUŻ WIDAĆ W CAŁYM KORPUSIE

Nie są to jeszcze wyniki ASMA. To mapa rodzin, które korpus wielokrotnie odsłania.

| Rodzina mechanizmu | Przykładowe realizacje |
|---|---|
| **memory paging / context management** | MemGPT/Letta, LongMem, OpenHands Condenser, Transformer-XL |
| **episodic memory + reflection** | Generative Agents, Reflexion, MemoryBank |
| **graph memory / relation retrieval** | GraphRAG, Zep/Graphiti, HippoRAG, AtomSpace |
| **search over partial states** | ToT, LATS, MCTS, Fast Downward |
| **generate → critique → revise** | Self-Refine, Reflexion, CRITIC, Constitutional AI |
| **task decomposition / subgoaling** | Soar, HTN/SHOP2, MetaGPT, AutoGPT |
| **specialized delegation** | BDI systems, AutoGen, Agents SDK, Claude Code Task |
| **state-machine / graph orchestration** | LangGraph, ADK, Temporal, Airflow |
| **tool-use protocols** | MCP, ReAct, Toolformer, Gorilla |
| **external verification** | Lean, Z3, CRITIC, SWE-bench, Inspect AI |
| **learned world models** | Dreamer, MuZero, JEPA |
| **replay / consolidation** | CLS, DNC/NTM family, continual-learning systems |
| **reconciliation / recovery loops** | Kubernetes controllers, Temporal, Nav2, Erlang/OTP |
| **provenance / lineage** | W3C PROV, in-toto, SLSA, MLflow |
| **attention allocation / resource control** | ACT-R, Soar, ECAN, HTM, active inference |
| **symbolic + neural coupling** | AlphaGeometry, OpenCog/Hyperon, Nengo/SPA, MRKL |

---

## 8. ASMA-READY TRANSITION MODEL

Ten zapis nie przeprowadza jeszcze ASMA. Przygotowuje do niej jednostki.

```text
SOURCE
  ↓
PROJECT
  ↓
IMPLEMENTATION / PAPER / SPEC
  ↓
MECHANISM CANDIDATE
  ↓
ASMA UNIT
  ├─ FUNCTION
  ├─ INPUT / OUTPUT
  ├─ STATE
  ├─ TRANSITION
  ├─ LEARNING
  ├─ DEPENDENCIES
  ├─ FAILURE MODES
  ├─ ENFORCEMENT
  ├─ EVIDENCE
  └─ TRANSFER FORM
  ↓
CROSS-PROJECT MECHANISM FAMILY
  ↓
NEURALCORE SYNTHESIS
```

### Minimalna karta przyszłego mechanizmu

```yaml
MECHANISM_ID:
NAME:
FAMILY:
FUNCTION:
INPUTS:
OUTPUTS:
STATE:
TRANSITIONS:
LEARNING:
DEPENDENCIES:
FAILURE_MODES:
ENFORCEMENT:
SOURCE_PROJECTS:
SOURCE_ANCHORS:
EVIDENCE_TYPE:
RECONSTRUCTABILITY:
TRANSFER_FORM:
UNKNOWN:
```

---

## 9. CZEGO TEN ARTEFAKT CELOWO NIE ROBI

- nie przyznaje rankingów;
- nie wyznacza „najlepszych” projektów;
- nie twierdzi, że deklarowana funkcja = potwierdzona skuteczność;
- nie rozstrzyga sporów mechanistycznych bez źródła pierwotnego;
- nie usuwa historycznych systemów tylko dlatego, że są stare;
- nie traktuje każdej biblioteki jako architektury poznawczej;
- nie traktuje każdego benchmarku jako implementacji agenta;
- nie traktuje paperu i repozytorium jako jednego dowodu.

---

## 10. OGRANICZENIA POCHODZENIA

Ten dokument został scalony z materiałów modelowych dostarczonych w rozmowie. Część wcześniejszych materiałów jest zachowana w pełnym brzmieniu, a część w postaci katalogów/ustaleń utrzymanych w kontekście rozmowy. Dlatego pole „Źródła wskazania” powinno być traktowane jako **provenance lead**, nie jako niezależny bibliograficzny audyt.

W szczególności nie należy wyciągać z tego dokumentu wniosku, że każdy URL, paper ID, stan repozytorium czy twierdzenie o skuteczności zostały zweryfikowane 2 października 2026. To będzie osobna warstwa pracy.

---

## 11. RESEARCH LOG — CO ZOSTAŁO OSIĄGNIĘTE

1. Zebrano wiele niezależnych perspektyw discovery.
2. Połączono powtarzające się projekty bez kasowania ich pochodzenia.
3. Rozdzielono projekt, rodzinę projektu, mechanizm i implementację.
4. Wyodrębniono osobny materiał techniczny, gdzie istnieją już bardziej konkretne jednostki ASMA.
5. Zachowano historyczne, akademickie i współczesne systemy w jednym korpusie.
6. Przygotowano strukturę, którą można później bezpośrednio przenieść do repozytorium publikacyjnego.

---

## 12. NASTĘPNA WARSTWA — NIE JEST CZĘŚCIĄ TEGO KORPUSU

Dalsza praca powinna rozpocząć się od **mechanizmów**, nie od kolejnego zbierania nazw:

```text
DISCOVERY CORPUS
      ↓
DEDUPLICATION
      ↓
MECHANISM CANDIDATE EXTRACTION
      ↓
ASMA LENS SELECTION
      ↓
SOURCE DEEPENING
      ↓
EVIDENCE + IMPLEMENTATION CHECK
      ↓
CROSS-PROJECT COMPARISON
      ↓
MECHANISM ATLAS / SYNTHESIS
      ↓
NEURALCORE
```

> **Rdzeń idei:** nie próbujemy skopiować projektów. Próbujemy odzyskać z nich mechanizmy, warunki ich działania, koszty, ograniczenia i zależności — a następnie sprawdzić, czy można je sensownie połączyć.

---

**END — NEURALCORE RESEARCH CORPUS v1.0**
