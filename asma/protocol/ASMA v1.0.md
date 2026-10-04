```text
ASMA v1.0
AI SYSTEMS MECHANISM ANALYSIS

PURPOSE
ASMA is an information-compression and mechanism-extraction protocol for analyzing AI systems.

It is designed to analyze:
- prompts
- system prompts
- skills
- tool catalogs
- tool schemas
- agent workflows
- multi-agent systems
- routing systems
- pipelines
- evaluation loops
- context/memory systems
- hybrid AI architectures
- documentation describing how an AI system operates

ASMA does not primarily ask:
"Is this system good?"

ASMA asks:
"What does this system make the AI do,
how does it control that process,
what mechanisms produce that behavior,
what assumptions does it encode,
what does it cost,
where can it fail,
what is actually supported,
and what can be extracted and reused?"

================================================================
CORE PRINCIPLES
================================================================

PRINCIPLE 1 — SOURCE FIDELITY

Describe what the source explicitly contains before interpreting why it exists.

Never silently replace source terminology with a more convenient theory.

If the source does not provide enough information:
write "unknown", "not specified", or "outside analyzed scope".

Never fill an information gap with imagination.

---------------------------------------------------------------

PRINCIPLE 2 — CLAIM DISCIPLINE

Always distinguish:

SOURCE FACT
What the source explicitly states or structurally enforces.

DIRECT INFERENCE
A conclusion that follows closely from the source structure.

MECHANISTIC HYPOTHESIS
A plausible explanation for why a mechanism may work.

EFFECTIVENESS CLAIM
A claim that a mechanism improves some outcome.

EXTERNAL EVIDENCE
Evidence independent from the analyzed source.

Never transform:

author claim → evidence
instruction → effectiveness
description → runtime enforcement
model judgment → validation
schema restriction → host-level restriction
plausible mechanism → demonstrated effect

---------------------------------------------------------------

PRINCIPLE 3 — UNKNOWN IS VALID INFORMATION

Do not hide uncertainty.

"Unknown" is preferable to fabricated precision.

---------------------------------------------------------------

PRINCIPLE 4 — HUMAN EFFECTS ARE A SEPARATE LAYER

Do not infer neural, psychological, cognitive or behavioral effects merely from an AI system's instructions.

Separate:

AI / MODEL OPERATIONS
from
HUMAN COGNITIVE CLAIMS
from
SYSTEM / INFRASTRUCTURE EFFECTS

---------------------------------------------------------------

PRINCIPLE 5 — MECHANISMS OVER LABELS

Do not merely identify names such as:
"few-shot", "ReAct", "Tree of Thoughts", "role prompting".

Describe the functional mechanism first.

Example:

MECHANISM:
Generate multiple isolated candidates before evaluation.

TECHNIQUE LABEL:
multi-path / self-consistency / branching

Functional mechanism is primary.

---------------------------------------------------------------

PRINCIPLE 6 — ARCHITECTURE MATTERS

A prompt can be one component of a much larger system.

Do not analyze:
- a tool catalog as if it were only prose
- a routing file as if it were a complete agent
- a skill as if its external framework files were visible
- an agent workflow as if it were a single prompt

Always determine what layer of the system is actually visible.

---------------------------------------------------------------

PRINCIPLE 7 — PROCESS IS PART OF THE MECHANISM

Analyze not only WHAT the AI must do, but WHEN it may do it.

Examples:
- generate before evaluate
- search before fetch
- read before edit
- ask user before continuing
- branch before selecting
- select before deepening
- summarize before continuing
- stop when sufficient evidence exists

These are PROCESS CONSTRAINTS.

---------------------------------------------------------------

PRINCIPLE 8 — ENFORCEMENT MATTERS

A rule written in prose is not automatically enforced.

Distinguish:

TEXT_ONLY
Schema / contract only
Runtime-enforced
Host-enforced
Externally verified
Unknown

---------------------------------------------------------------

PRINCIPLE 9 — NO UNIVERSAL QUALITY SCORE

Do not produce:
- "8/10"
- "best"
- "worst"
- "high quality"
as the main result.

ASMA extracts information.

Its final gate is:
CONTINUE
CONTINUE_CONDITIONALLY
STOP

This is an information-value gate, not a quality ranking.

================================================================
INPUT
================================================================

SOURCE:
[full prompt / file content / tool catalog / workflow / system description]

SOURCE LOCATION:
[URL, file, repository path, or unknown]

OPTIONAL CONTEXT:
[intended use, model, platform, author notes, runtime conditions]

ANALYSIS MODE:
- SOURCE_ONLY
- SOURCE_PLUS_CONTEXT
- VERIFY
- COMPARATIVE

DEFAULT:
SOURCE_ONLY unless the user explicitly asks for external verification.

If VERIFY mode is used and web access is available:
verify important effectiveness claims and clearly separate external evidence from source-derived analysis.

================================================================
INTERNAL EXECUTION MODEL
================================================================

ASMA runs three internal passes before producing the final report.

PASS A — PARSE
Extract observable source structure.

PASS B — MODEL
Infer mechanisms, architecture, constraints, costs and failure modes.

PASS C — AUDIT
Challenge every important inference:
"Did the source actually justify this statement?"

Only after PASS C may the final three voices be produced.

================================================================
VOICE 1 — TECHNICAL ANALYSIS
================================================================

STEP 0 — OBJECT IDENTIFICATION
---------------------------------------------------------------

OBJECT_TYPE:
Choose all applicable:

- single_prompt
- system_prompt
- user_prompt
- interactive_protocol
- skill
- routing_rule
- tool_catalog
- tool_schema
- agent_workflow
- multi_agent_system
- pipeline
- evaluation_system
- memory_context_system
- hybrid
- unknown

SYSTEM_LAYER:
- instruction
- orchestration
- tool
- data
- evaluation
- interface
- safety
- infrastructure
- hybrid
- unknown

PRIMARY_FUNCTION:
[what the object fundamentally exists to do]

VISIBLE_SCOPE:
[what is actually present]

OUTSIDE_SCOPE:
[required components not present or externally referenced]

INTERACTION_MODEL:
- one_shot
- iterative
- user_in_the_loop
- autonomous
- tool_mediated
- multi_agent
- mixed
- unknown

INPUT:
[what enters]

OUTPUT:
[what leaves]

SIDE_EFFECTS:
[files, state, tools, integrations, UI, external actions]

---------------------------------------------------------------
STEP 1 — SYSTEM MAP
---------------------------------------------------------------

Before listing mechanisms, construct the highest-level map.

SYSTEM_FLOW:

[input]
→ [routing / classification]
→ [operation]
→ [evaluation / gating]
→ [action]
→ [output]

LAYER MAP:

L1:
[meta / identity / global rules]

L2:
[interaction / routing]

L3:
[reasoning / generation]

L4:
[tools / retrieval / execution]

L5:
[evaluation / verification]

L6:
[output / interface]

L7:
[external dependencies]

Do not force all layers if they are absent.

---------------------------------------------------------------
STEP 2 — SOURCE PRIMITIVES
---------------------------------------------------------------

Classify important constraints by their actual source form.

For each relevant item:

SP[n]:

CONTENT:
[rule or structure]

SOURCE_PRIMITIVE:
- prose_instruction
- schema_constraint
- required_field
- enum
- default
- example
- routing_instruction
- negative_routing
- tool_description
- external_dependency
- implementation_detail
- other

ENFORCEMENT_LEVEL:
- text_only
- schema_constrained
- runtime_enforced
- host_enforced
- externally_verified
- unknown

Do not infer enforcement from wording alone.

---------------------------------------------------------------
STEP 3 — INSTRUCTION INVENTORY
---------------------------------------------------------------

List major explicit instructions.

I[n]:

CONTENT:
[short faithful description]

FUNCTION:
- task
- role
- constraint
- format
- sequencing
- evaluation
- prohibition
- routing
- branching
- tool_use
- safety
- state_control
- other

SOURCE_INTENT:
[only when explicitly stated]

Do not infer benefits here.

---------------------------------------------------------------
STEP 4 — MECHANISM EXTRACTION
---------------------------------------------------------------

Extract functional mechanisms.

For each:

M[n]

NAME:
[short functional name]

TYPE:
- generation
- selection
- routing
- decomposition
- verification
- retrieval
- memory/context
- interaction
- tool_use
- safety
- planning
- evaluation
- state_management
- other

DESCRIPTION:
[what structurally happens]

TRIGGER:
[what causes it]

OPERATION:
[what the system does]

EXPECTED_EFFECT:
[what it is intended or plausibly expected to change]

DEPENDENCIES:
[what must exist for it to work]

STATUS:
- explicit_mechanism
- direct_inference
- mechanistic_hypothesis
- uncertain

---------------------------------------------------------------
STEP 5 — MECHANISM GRANULARITY
---------------------------------------------------------------

For each important mechanism determine:

GRANULARITY:
- atomic
- composite
- architectural

ATOMIC:
A mechanism performing one recognizable function.

COMPOSITE:
Several atomic mechanisms combined.

ARCHITECTURAL:
A structure in which multiple mechanisms interact.

If a named technique contains several mechanisms,
decompose it.

Example:

"Self-consistency"

may contain:
- candidate generation
- path independence
- answer aggregation
- selection

---------------------------------------------------------------
STEP 6 — PROCESS CONSTRAINTS
---------------------------------------------------------------

Detect ordering, timing and state rules.

PC[n]:

RULE:
[what must happen before/after what]

PREVENTS:
[what bad sequence it prevents]

ENFORCES:
[what sequence it creates]

ENFORCEMENT:
[text / schema / runtime / host / unknown]

IMPORTANCE:
- low
- medium
- high

Look especially for:
- generate before evaluate
- search before fetch
- read before edit
- ask before continuing
- branch before selection
- selection before deepening
- stop conditions
- retry limits
- isolated contexts
- context compression
- mandatory ordering
- skip conditions

---------------------------------------------------------------
STEP 7 — ROUTING / DECISION LOGIC
---------------------------------------------------------------

Determine whether the system chooses different behavior based on conditions.

ROUTING_RULES:

R[n]

CONDITION:
[what triggers branch]

IF_TRUE:
[action/path]

IF_FALSE:
[action/path]

ROUTING_TYPE:
- positive
- negative
- fallback
- escalation
- skip
- halt
- retry
- reroute

RISK:
- low
- medium
- high
- unknown

Also detect:
- category forcing
- hidden routing assumptions
- ambiguous classification boundaries
- first-choice anchoring

---------------------------------------------------------------
STEP 8 — ARCHITECTURE
---------------------------------------------------------------

Describe the runtime structure.

ARCHITECTURAL_PATTERN:
- single_step
- chain
- loop
- branching
- search
- pipeline
- multi_agent
- tool_loop
- router
- evaluator_loop
- hybrid
- unknown

FLOW:
[input]
→ component
→ component
→ component
→ output

COMPONENTS:

C[n]:
ROLE:
INPUT:
OUTPUT:
DEPENDENCIES:

RELATIONSHIPS:
- enables
- constrains
- depends_on
- selects
- feeds
- verifies
- overrides
- conflicts_with
- duplicates

BOTTLENECKS:
[components with disproportionate importance]

---------------------------------------------------------------
STEP 9 — EXTERNAL DEPENDENCIES
---------------------------------------------------------------

Detect everything that is outside the analyzed object.

DEPENDENCY[n]:

NAME:
TYPE:
- prompt
- file
- repository
- tool
- API
- model
- runtime
- database
- integration
- human_input
- hidden_context
- external_framework
- unknown

REQUIRED_FOR:
[what part depends on it]

VISIBLE:
yes / partial / no

IMPACT_IF_MISSING:
[what breaks]

IMPORTANT:
Never claim to have analyzed an external dependency that was not actually provided.

---------------------------------------------------------------
STEP 10 — OBJECTIVE / FUNCTION OF SELECTION
---------------------------------------------------------------

Determine what the system treats as "better".

CRITERIA:
- accuracy
- novelty
- viability
- fit
- consistency
- safety
- completeness
- speed
- cost
- user preference
- compliance
- visual fidelity
- context preservation
- other

WEIGHTS:
[only if explicit]

SOURCE:
- user
- author
- system
- model_generated
- implicit
- unknown

ENFORCEMENT:
[how the criterion influences the result]

CRITICAL:
A numerical criterion is not automatically an objective truth.
It is a design choice unless externally validated.

---------------------------------------------------------------
STEP 11 — OPERATIONAL MAP
---------------------------------------------------------------

Describe what happens at the AI/system level.

MODEL_OPERATIONS:
- classification
- generation
- decomposition
- retrieval
- ranking
- verification
- self_critique
- branching
- summarization
- tool_use
- memory access
- context compression
- planning
- state transition
- other

SYSTEM_EFFECTS:
- latency
- token cost
- call count
- context usage
- infrastructure load
- reproducibility
- automation
- statefulness
- user blocking
- integration dependence
- other

---------------------------------------------------------------
STEP 12 — HUMAN COGNITIVE LAYER
---------------------------------------------------------------

Only include if supported or clearly framed as a hypothesis.

For each claim:

H[n]:

PROCESS:
- attention
- working_memory
- metacognition
- cognitive_flexibility
- abstraction
- reflection
- agency
- decision_support
- cognitive_load
- other

CLAIM:
[what effect is proposed]

SOURCE_STATUS:
- source_claim
- direct_inference
- hypothesis
- evidence_supported
- unknown

DO NOT:
infer neural activation, brain regions, neurotransmitters, or training effects from prompt structure alone.

---------------------------------------------------------------
STEP 13 — COST / TRADE-OFF MAP
---------------------------------------------------------------

For each major mechanism:

T[n]

MECHANISM:
[reference]

INCREASES:
[what becomes stronger / more explicit]

COST:
[time / tokens / latency / complexity / attention / infrastructure]

POSSIBLE_WEAKENING:
[what may become harder]

EVIDENCE_STATUS:
- supported
- plausible
- unknown

Never state a speculative trade-off as measured fact.

---------------------------------------------------------------
STEP 14 — FAILURE MODES
---------------------------------------------------------------

For each significant risk:

F[n]

FAILURE:
[what can go wrong]

TRIGGER:
[condition]

CONSEQUENCE:
[effect]

DETECTION:
[how it could be noticed]

MITIGATION:
[only if source provides one]

Also test explicitly:

CATEGORY_FORCING
Does the system force problems into a fixed conceptual structure?

ANCHORING
Can an early answer/example/branch constrain later generation?

SELF_CONFIRMATION
Can the same model generate a claim and validate its own claim?

CRITERIA_BIAS
Can arbitrary weighting or hidden preferences determine the outcome?

FALSE_DIVERSITY
Are outputs only superficially different?

COMPLEXITY_OVERHEAD
Can the procedure cost more than the problem warrants?

INFORMATION_BOTTLENECK
Can caps, summaries, isolated agents or schemas hide relevant information?

DEPENDENCY_FAILURE
Can missing external components invalidate the process?

ENFORCEMENT_GAP
Can the system instruct behavior without actually enforcing it?

---------------------------------------------------------------
STEP 15 — EPISTEMIC STATUS
---------------------------------------------------------------

For each important non-trivial claim:

CLAIM[n]:

TEXT:
[claim]

TYPE:
- instruction
- mechanism
- heuristic
- hypothesis
- empirical_claim
- theoretical_claim
- rhetorical_claim
- implementation_detail
- architecture_fact
- unknown

CONFIDENCE:
- high
- medium
- low

SOURCE:
[exact section / field / component]

DO NOT UPGRADE:
- author anecdote → evidence
- design intention → measured outcome
- tool description → runtime proof
- schema → host behavior
- model judgment → independent validation

---------------------------------------------------------------
STEP 16 — EVIDENCE
---------------------------------------------------------------

For every effectiveness claim:

E[n]:

CLAIM:
[claim]

EVIDENCE_TYPE:
- none
- author_anecdote
- example
- benchmark
- experiment
- peer_reviewed_study
- external_evaluation
- runtime_trace
- implementation_observation
- unknown

POPULATION_OR_TASK:
[what was tested]

MODEL_OR_SYSTEM:
[if known]

LIMITATIONS:
[important limits]

STATUS:
- demonstrated_in_context
- suggestive
- unsupported
- unknown

If VERIFY mode was used:
separate source evidence from external evidence.

---------------------------------------------------------------
STEP 17 — TRANSFERABILITY
---------------------------------------------------------------

For each important reusable mechanism:

T[n]:

TRANSFER_LEVEL:
- high
- medium
- low
- unknown

CAN_BE_EXTRACTED:
yes / no

TRANSFERABLE_UNIT:
[what exactly can be reused]

POTENTIAL_DOMAINS:
[where it may work]

TRANSFER_RISK:
[what may invalidate the transfer]

IMPORTANT:
Transfer the mechanism, not necessarily the entire architecture.

---------------------------------------------------------------
STEP 18 — INFORMATION HARVEST
---------------------------------------------------------------

Extract only the most valuable reusable information.

REUSABLE_MECHANISMS:
1.
2.
3.
...

REUSABLE_PROCESS_CONSTRAINTS:
1.
2.
3.
...

REUSABLE_ROUTING_PATTERNS:
1.
2.
3.
...

REUSABLE_ARCHITECTURAL_PATTERNS:
1.
2.
3.
...

REUSABLE_EVALUATION_PATTERNS:
1.
2.
3.
...

INTERESTING_BUT_UNVERIFIED:
1.
2.
3.
...

DO_NOT_COPY_BLINDLY:
1.
2.
3.
...

---------------------------------------------------------------
STEP 19 — ANALYSIS GATE
---------------------------------------------------------------

DECISION:
- CONTINUE
- CONTINUE_CONDITIONALLY
- STOP

RATIONALE:
[one factual reason]

CONTINUE:
The source contains mechanisms worth extracting.

CONTINUE_CONDITIONALLY:
The source is valuable but depends on missing components, weak evidence or unclear scope.

STOP:
The source contains little reusable information beyond repetition or presentation.

This is NOT a quality score.

================================================================
VOICE 2 — CLEAN HUMAN SUMMARY
================================================================

Produce a concise, high-density explanation.

Use exactly these headings:

WHAT IT IS

WHAT IT ACTUALLY DOES

MOST VALUABLE MECHANISMS

PROCESS CONTROLS

WHAT IT MAY STRENGTHEN

WHAT IT MAY COST OR WEAKEN

WHAT IS ACTUALLY SUPPORTED

WHAT I WOULD EXTRACT

WHAT I WOULD NOT COPY BLINDLY

WHAT IS OUTSIDE THE ANALYZED SCOPE

FURTHER_ANALYSIS

Rules:
- shorter than Voice 1
- no new claims
- preserve uncertainty
- focus on reusable information
- make complex systems readable without flattening them

================================================================
VOICE 3 — ONE-SENTENCE AI JUDGMENT
================================================================

Write exactly one sentence.

It must contain:
1. what the system fundamentally is,
2. the strongest reusable mechanism,
3. the main limitation or uncertainty.

Template:

"[OBJECT] is primarily a [mechanism/architecture] whose main reusable value comes from [strength], while its main limitation is [limitation/evidence gap]."

Do not use a score.
Do not call it "best" or "worst".

================================================================
FINAL AUDIT — THREE PASSES
================================================================

PASS 1 — SOURCE FIDELITY

Ask:
"Did I say anything that the source does not support?"

Correct:
- overclaiming
- invented intent
- invented runtime behavior
- invented dependencies
- invented effectiveness

---------------------------------------------------------------

PASS 2 — MECHANISM QUALITY

Ask:
"Did I extract actual mechanisms rather than merely repeat labels?"

Correct:
- technique-name dumping
- shallow summaries
- duplicated mechanisms
- architecture described as a list without relationships

---------------------------------------------------------------

PASS 3 — INFORMATION VALUE

Ask:
"Would deleting this information make the system harder to understand or reuse?"

If no:
remove it.

The final report should maximize:
INFORMATION DENSITY / WORD COUNT

not:
WORD COUNT / INFORMATION DENSITY

================================================================
ASMA OUTPUT RULES
================================================================

1. Prefer precise language over impressive language.
2. Prefer "unknown" over fabricated certainty.
3. Prefer functional descriptions over fashionable labels.
4. Distinguish mechanism from intended effect.
5. Distinguish intended effect from demonstrated effect.
6. Distinguish instruction from enforcement.
7. Distinguish architecture from implementation.
8. Distinguish AI effects from human effects.
9. Distinguish external dependency from analyzed content.
10. Never use neural language without appropriate evidence.
11. Do not silently compare the object to another system.
12. Do not reference neuralcore unless comparison mode explicitly requests it.
13. Do not optimize or rewrite the analyzed system unless explicitly requested.
14. Do not turn the report into an essay.
15. Preserve useful negative information:
   - what is missing
   - what is unverified
   - what may fail
   - what should not be copied blindly

================================================================
ASMA CORE QUESTION
================================================================

Do not ask:

"Is this prompt good?"

Ask:

"What mechanisms control the AI system,
what process do they create,
what architecture connects them,
what assumptions and selection criteria are encoded,
what do they cost,
where can they fail,
what is actually supported,
and what can be extracted as a reusable mechanism?"
```
