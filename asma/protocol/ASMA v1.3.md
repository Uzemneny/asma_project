# ASMA v1.3

## AI SYSTEM MECHANISM ANALYSIS

---

# 0. PURPOSE

ASMA is a source-adaptive protocol for extracting reusable mechanisms, constraints, patterns, methods, claims and implementation-relevant structures from technical material while preserving epistemic discipline.

Primary objective:

> maximize useful information recovered per unit of analysis cost without upgrading source statements beyond what the available evidence supports.

ASMA is:

- a mechanism-analysis protocol,
    
- a harvest protocol,
    
- an epistemic-discipline layer,
    
- a source-adaptive analysis process.
    

ASMA is not:

- a universal quality scorer,
    
- a cloning system,
    
- an implementation generator,
    
- a repository parser,
    
- a runtime orchestrator,
    
- an external evidence service.
    

The central product is the **provenance-bearing reusable unit**.

---

# 1. NAME

**ASMA = AI SYSTEM MECHANISM ANALYSIS**

The name and meaning of the acronym are fixed.

---

# 2. CORE MODEL

ASMA separates two levels of state:

```text
CANDIDATE STATE
    PROBE
    → FILTER_1
    → DEEPEN
    → FILTER_2
    → DEPTH_HALT

SOURCE STATE
    INTAKE
    → MAP
    → CANDIDATE HARVEST
    → SOURCE_GATE
```

Candidate-level completion does not imply source-level completion.

Source-level continuation does not require reopening already completed candidates unless new evidence affects them.

---

# 3. CORE INVARIANTS

## P1 — SOURCE FIDELITY

Describe what the source contains before explaining why it exists.

Do not replace the source with a cleaner theory of what it "must mean".

---

## P2 — CLAIM DISCIPLINE

Distinguish:

```text
SOURCE_FACT
DIRECT_INFERENCE
MECHANISTIC_HYPOTHESIS
EFFECTIVENESS_CLAIM
EXTERNAL_EVIDENCE
CONTEXT
```

Never silently upgrade:

```text
author claim → evidence
instruction → runtime behavior
description → implementation
intention → demonstrated effect
plausible mechanism → validated effect
schema restriction → runtime enforcement
context → source fact
```

---

## P3 — UNKNOWN IS VALID

Unknown is a valid result.

Do not fill missing information because a field exists.

Do not manufacture precision.

---

## P4 — MECHANISM OVER LABEL

Describe the functional operation before assigning a named technique.

A label may identify similarity.

The functional mechanism remains primary.

---

## P5 — PROCESS IS PART OF THE MECHANISM

Ordering, branching, routing, iteration, state transition, selection and stopping are part of system behavior.

Preserve relations such as:

```text
generate → evaluate
search → fetch → inspect
propose → verify → commit
detect → route
read → modify → test
```

---

## P6 — VISIBLE SCOPE ≠ IMPLIED ARCHITECTURE

A prompt is not automatically the whole runtime.

A README is not automatically the whole repository.

A paper is not automatically proof of implementation.

A schema is not automatically proof of enforcement.

---

## P7 — INTENDED EFFECT ≠ DEMONSTRATED EFFECT

A source claim about effectiveness establishes that the source makes the claim.

It does not independently establish the effect.

---

## P8 — ENFORCEMENT MATTERS

For enforcement-bearing objects distinguish:

```text
PROSE_ONLY
SCHEMA_CONSTRAINED
RUNTIME_CONSTRAINED
HOST_CONSTRAINED
EXTERNAL_CONSTRAINT
UNKNOWN
NOT_APPLICABLE
```

`NOT_APPLICABLE` means enforcement is not the relevant property of the object.

---

## P9 — EVIDENCE LAYERS

For artifacts and mixed sources distinguish:

```text
DOCUMENTED_DESIGN
IMPLEMENTED_STRUCTURE
TESTED_BEHAVIOR
OBSERVED_RUNTIME
CONTEXT
UNKNOWN
```

Do not silently collapse these into one truth layer.

---

## P10 — EXTRACT THE MECHANISM, NOT THE ARCHITECTURE

Transfer the functional component that survives isolation.

Preserve:

```text
dependencies
assumptions
required context
failure conditions
```

---

## P11 — NEGATIVE INFORMATION IS MATERIAL

Preserve:

```text
UNKNOWN
REJECTED_INFERENCE
CONFLICT
MISSING_IMPLEMENTATION
UNVERIFIED_EFFECT
DEPENDENCY
FAILURE_CONDITION
```

---

## P12 — NO UNIVERSAL QUALITY SCORE

ASMA does not assign a universal numeric quality score.

Its output answers:

```text
what is recoverable
what is reusable
what is supported
what remains uncertain
whether further analysis is justified
```

---

# 4. INPUT CONTRACT

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

---

# 5. CONTEXT BOUNDARY

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

---

# 6. SOURCE LENSES

Select the minimum lens set necessary.

```text
LENS_SYSTEM
LENS_KNOWLEDGE
LENS_ARTIFACT
```

Do not activate every lens merely because the source contains multiple media types.

For mixed sources, the lens may be assigned per candidate or Unit.

---

# 7. LENS_SYSTEM

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

---

# 8. LENS_KNOWLEDGE

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

---

# 9. LENS_ARTIFACT

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

---

# 10. ARTIFACT EVIDENCE

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

---

# 11. INTAKE

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

---

# 12. SOURCE INTAKE POLICY

## SYSTEM

Prefer:

```text
surface specification
→ interfaces
→ process/routing
→ selected details
```

## KNOWLEDGE

Prefer:

```text
claims/contributions
→ method
→ evaluation
→ limitations
→ selected supporting detail
```

## ARTIFACT

Prefer:

```text
manifest / README / API surface
→ public entry points
→ relevant tests
→ selected implementation
→ supporting configuration/dependencies
```

Do not inspect an entire source merely because it exists.

---

# 13. MAP

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

---

# 14. PROBE

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

---

# 15. CANDIDATE RECORD

Each candidate receives:

```text
CANDIDATE_ID
LENS
TYPE
LOCATION
FUNCTIONAL_HINT
PROBE_EVIDENCE
INITIAL_RELEVANCE
DEPENDENCIES_IF_VISIBLE
STATE
```

Candidate state:

```text
PENDING
DEEPEN
DROP
```

A candidate is not yet a Unit.

---

# 16. FILTER_1 — RECALL FILTER

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

---

# 17. PRE-DEEPEN RESOURCE CONTROL

FILTER_1 must respect the selected `DEPTH_BUDGET`.

When candidates exceed available deepening capacity:

1. retain candidates with distinct functional signal,
    
2. retain candidates covering different source regions where practical,
    
3. prefer candidates with explicit transfer potential,
    
4. preserve candidates whose deeper evidence could materially change the harvest,
    
5. drop only candidates justified by the FILTER_1 rules.
    

Do not invent a mandatory minimum number of deepened candidates.

Do not force artificial diversity when the source contains little signal.

---

# 18. DEPTH_BUDGET

Depth budget is a cap.

It is not a quality score.

## LIGHT

```text
max 7 candidates
max 3 deepened candidates
SURFACE depth
no dependency tracing unless essential
```

## TARGETED

```text
max 12 candidates
max 5 deepened candidates
SURFACE → CONTEXT
dependency tracing only when required
```

## DEEP

```text
no fixed candidate cap
CONTEXT → TRACE allowed
extended dependency tracing allowed
still subject to material stop
```

User-selected budget may be overridden when the source is obviously incompatible with the selected mode; the reason must be stated briefly.

Do not create an arbitrary numeric complexity score.

---

# 19. CANDIDATE DEPTH

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

---

# 20. DEEPEN

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

---

# 21. CANDIDATE LOCAL HALT

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

---

# 22. OPTIONAL DEPTH SAFETY LIMITS

When needed, external execution can impose:

```text
MAX_DEEPEN_ROUNDS
MAX_DEPENDENCY_TRACE_DEPTH
MAX_EXTERNAL_LOOKUPS
MAX_RUNTIME_BUDGET
```

These are implementation controls, not epistemic facts.

The core ASMA prompt should not invent time guarantees it cannot enforce.

---

# 23. FILTER_2 — PRECISION FILTER

After DEEPEN, classify the candidate:

```text
SOURCE_SUPPORTED
CONDITIONAL
REJECTED
```

## SOURCE_SUPPORTED

The Unit is supported at the claimed evidentiary level.

This does not mean that the mechanism is effective.

## CONDITIONAL

The Unit is usable only with explicit assumptions, unresolved evidence or relevant context dependence.

## REJECTED

The candidate does not survive the evidence or transfer analysis.

Rejected candidates remain traceable through the Candidate Ledger.

---

# 24. CANONICAL UNIT — REQUIRED CORE

Every emitted Unit must contain:

```text
UNIT_ID
LENS
TYPE
STATUS
FUNCTION
MINIMAL_FORM
SOURCE_ANCHOR
EVIDENCE_TYPE
```

These are the **required fields**.

---

# 25. CANONICAL UNIT — CONDITIONAL FIELDS

Add only when applicable:

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
DISCREPANCY
RELATES_TO
```

Do not fill a conditional field because it exists.

Do not turn speculation into field completion.

---

# 26. UNIT TYPES

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

---

# 27. MINIMAL_FORM

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

---

# 28. EVIDENCE ANCHOR

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

---

# 29. EVIDENCE TYPE

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

---

# 30. STATUS ≠ EFFECTIVENESS

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

---

# 31. ENFORCEMENT APPLICABILITY

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

---

# 32. ISOLATION

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

---

# 33. DISCREPANCY

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

---

# 34. UNKNOWN

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

---

# 35. REJECTED INFERENCES

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

---

# 36. TRANSFER

Use:

```text
DIRECT_TRANSFER
ADAPTATION_REQUIRED
CONCEPT_ONLY
NON_TRANSFERABLE
```

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

---

# 37. CANDIDATE LEDGER

The Candidate Ledger is mandatory for every run containing candidate selection.

Canonical reference shape:

```yaml
candidate_id:
unit_id:
lens:
type:
location:

filter_1_result:
  DEEPEN
  DROP

drop_reason:

deepened:
depth_used:
local_halt_reason:

filter_2_result:
  SOURCE_SUPPORTED
  CONDITIONAL
  REJECTED

status_change:
notes:
```

`unit_id` may be null.

Do not require time tracking inside prompt-only ASMA.

Runtime systems may add it externally.

---

# 38. CANDIDATE LEDGER INVARIANT

The Ledger must make it possible to determine:

```text
what was found
what was dropped
what was deepened
how deeply it was inspected
what became a Unit
why a candidate did not become a Unit
```

If this trace cannot be reconstructed, the audit trail is incomplete.

---

# 39. UNIT IDENTITY

`UNIT_ID` represents identity.

Identity must remain stable once assigned within a persistent session or library.

Do not regenerate an existing Unit's identity because its description becomes more precise.

Example:

```text
U-017
```

remains `U-017` when its evidence or description is extended.

---

# 40. MATCH KEY

Deduplication is a separate problem from identity.

When external persistence exists, a Unit may additionally carry:

```text
MATCH_KEY
```

for similarity and candidate deduplication.

`MATCH_KEY` does not replace `UNIT_ID`.

Do not use raw hashing as the sole identity mechanism.

Potential matches must be classified:

```text
SAME_UNIT
EXTENDS
CONFLICTS
NEW
```

Human or higher-level model confirmation may be required for ambiguous matches.

---

# 41. SOURCE STATE

Source-level analysis state:

```text
MAPPED
HARVESTING
DIMINISHING
CONDITIONALLY_CONTINUABLE
STOPPED
```

Source state is not the sum of candidate states.

It is a judgment about whether additional source analysis is justified.

---

# 42. SOURCE GATE

```text
SOURCE_GATE:
    CONTINUE
    CONTINUE_CONDITIONALLY
    STOP
```

## CONTINUE

Additional source material is likely to add materially new harvest.

## CONTINUE_CONDITIONALLY

Additional analysis requires a named input or source fragment.

## STOP

Additional analysis is not currently justified.

STOP does not mean the source is permanently exhausted.

New evidence can reopen a stopped source.

---

# 43. SESSION CONTINUITY

When additional source material arrives:

```text
preserve existing UNIT_ID
preserve unchanged SOURCE_SUPPORTED Units
re-open CONDITIONAL / UNKNOWN candidates when relevant
PROBE newly added material
compare new candidates against existing Units
emit DIFF instead of rebuilding unchanged material
```

Candidate/Unit relations:

```text
NEW
SAME_UNIT
EXTENDS
CONFLICTS
```

Unit state changes may be:

```text
UNCHANGED
EXTENDED
DOWNGRADED
CONTRADICTED
```

A previous Unit is not immune to revision.

---

# 44. SESSION + SOURCE GATE

`STOP` does not block future continuation.

It means:

```text
no additional analysis is currently justified
```

New material may reopen the source.

`CONTINUE_CONDITIONALLY` identifies what is missing.

This avoids creating a separate `PAUSE` state in the core.

---

# 45. MULTI-SOURCE HARVEST

Each Unit retains:

```text
SOURCE_ORIGINS
PRIMARY_SUPPORT
SECONDARY_SUPPORT
CONFLICTS
```

When two sources appear to describe the same mechanism:

```text
SAME_UNIT
EXTENDS
CONFLICTS
NEW
```

Do not merge merely because wording is similar.

Do not treat repeated claims as independent confirmation.

---

# 46. CONFLICT PROTOCOL

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

---

# 47. VERIFY MODE

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

---

# 48. COMPARATIVE MODE

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

---

# 49. PROJECT CONTEXT

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

---

# 50. SELF-FAILURE REGISTRY

ASMA monitors its own process for:

## CATEGORY_FORCING

The selected lens does not fit the material.

Response:

```text
switch lens
split candidate
or mark unsupported
```

## HARVEST_COLLAPSE

The output becomes a summary rather than an inventory.

Response:

```text
return to Units and Candidate Ledger
```

## DEPTH_DRIFT

Analysis continues after a candidate is sufficiently characterized.

Response:

```text
DEPTH_HALT
```

## EVIDENCE_DRIFT

Inference becomes source fact.

Response:

```text
re-anchor
downgrade
or reject
```

## UNIT_FRAGMENTATION

One mechanism is split into trivial Units.

Response:

```text
merge when no independent transfer value exists
```

## UNIT_MONOLITH

A whole architecture becomes one Unit.

Response:

```text
decompose
```

## TEMPLATE_PRESSURE

Fields are filled because they exist.

Response:

```text
omit non-applicable material
```

## HARVEST_NOISE

Many observations, little reusable signal.

Response:

```text
tighten selection
```

These are monitoring rules, not automatic scoring functions.

---

# 51. HUMAN-FACTOR SAFEGUARDS

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

---

# 52. LARGE SOURCES

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

---

# 53. UNSTRUCTURED SOURCES

When source structure is weak:

```text
do not invent headings or architecture as facts
use semantic boundaries cautiously
lower confidence when source anchors are weak
preserve uncertainty
```

Unstructured mode is a lens behavior, not a new core architecture.

---

# 54. RUNTIME BOUNDARY

The following may exist outside core ASMA:

```text
repository retrieval
chunking
AST parsing
JSON/YAML validation
hash computation
persistent storage
time tracking
execution
external verification tooling
multi-call orchestration
```

ASMA may define the contract these tools support.

ASMA does not pretend that textual instructions execute those tools automatically.

---

# 55. PROMPT-ONLY LIMIT

ASMA v1.3 as a prompt has:

```text
text-level enforcement
model-dependent execution
no guaranteed schema enforcement
no guaranteed runtime state persistence
no guaranteed tool invocation
```

A runtime implementation may strengthen these with:

```text
structured output validation
separate calls
state persistence
retrieval
parsers
execution
external verification
```

Those are implementation layers around ASMA, not replacements for the protocol.

---

# 56. CANONICAL RECORD

ASMA has one canonical internal record:

```text
ASMA_RECORD
├── SOURCE_MAP
├── CANDIDATE_LEDGER
├── UNITS
├── UNKNOWN
├── REJECTED_INFERENCES
├── GLOBAL_DISCREPANCIES
├── AUDIT
└── SOURCE_GATE
```

Views such as HARVEST, ANALYSIS and AUDIT reference this record.

They do not create parallel truths.

---

# 57. OUTPUT MODES

## HARVEST

Primary default.

Emit:

```text
SOURCE_MAP
UNITS
UNKNOWN
REJECTED_INFERENCES
SOURCE_GATE
```

Add Candidate Ledger when auditability is materially relevant.

---

## ANALYSIS

Emit:

```text
SOURCE_MAP
mechanism/process relations
dependencies
architecture
failures
UNKNOWN
```

Reference Units by `UNIT_ID`.

---

## AUDIT

Emit:

```text
claim status
evidence
enforcement
discrepancies
rejected inferences
candidate trace
audit status
```

---

## FULL

Combine the above as views over the same canonical record.

Do not repeat the same Unit verbatim across sections.

---

# 58. THREE VOICES

Three voices are presentation views.

## VOICE 1 — FORENSIC

Detailed technical reconstruction when depth is required.

## VOICE 2 — HARVEST INDEX

```text
UNIT_ID
WHAT_IT_DOES
WHY_IT_MAY_MATTER
TRANSFER_FORM
DEPENDENCY
EVIDENCE_STATUS
MAIN_LIMIT
```

Voice 2 may only reference canonical Units.

## VOICE 3 — ROUTING TOKEN

```text
SOURCE
STRONGEST_HARVEST
MAIN_LIMIT
SOURCE_GATE
```

Voice 3 is not a separate evaluation system.

---

# 59. AUDIT INVARIANTS

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

---

# 60. FINAL AUDIT

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

---

# 61. DEFAULT EXECUTION

For:

```text
"analyze this with ASMA"
```

use:

```text
ANALYSIS_MODE = SOURCE_ONLY
DEPTH_BUDGET = TARGETED
OUTPUT_MODE = HARVEST
```

Process:

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

Do not automatically produce a maximal forensic report.

---

# 62. QUICK REFERENCE

```text
INTAKE
    identify source + lens + scope

MAP
    locate signal + candidate regions

PROBE
    find candidate signals cheaply

FILTER_1
    remove only obvious non-candidates

DEEPEN
    inspect selected candidates

FILTER_2
    SOURCE_SUPPORTED / CONDITIONAL / REJECTED

UNITIZE
    create provenance-bearing reusable Units

AUDIT
    verify evidence + invariants

EMIT
    output canonical views

SOURCE_GATE
    CONTINUE / CONTINUE_CONDITIONALLY / STOP
```

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

Identity distinction:

```text
UNIT_ID ≠ MATCH_KEY
```

---

# 63. REFERENCE UNIT SHAPE

```yaml
unit_id:
lens:
type:
status:

function:
minimal_form:

source_anchor:
evidence_type:

dependencies:
must_be_true:

breaks_if_isolated:
isolation_status:

enforcement:
effect_status:

transfer_form:
adoption_notes:

unknown:
discrepancy:
relates_to:
```

Only applicable fields are populated.

---

# 64. REFERENCE CANDIDATE LEDGER

```yaml
candidate_id:
unit_id:
lens:
type:
location:

filter_1_result:
deepened:
depth_used:
local_halt_reason:

filter_2_result:
drop_reason:

status_change:
notes:
```

---

# 65. FINAL DEFINITION

ASMA v1.3 is a source-adaptive protocol that probes technical material for candidate reusable units, filters obvious non-candidates without premature evidence requirements, selectively deepens surviving candidates, audits evidence and dependencies, preserves disagreement and uncertainty, maintains stable unit identity across sessions, and decides whether further source analysis is justified.

Its primary artifact is not the report.

It is the **provenance-bearing reusable Unit**.

---

# 66. VERSION CHANGE

### v1.3 finalization

The v1.3 hardening introduces:

```text
candidate state ≠ source state
PROBE → FILTER_1 → DEEPEN → FILTER_2
explicit local halt conditions
resource-aware selection without artificial minimum harvest
required vs conditional Unit fields
stable Unit identity separated from deduplication
typed UNKNOWN
explicit multi-source conflict handling
session continuation semantics
explicit runtime boundary
stronger audit invariants
self-failure monitoring
```

The following are intentionally NOT part of ASMA core:

```text
automatic complexity scoring
minimum number of Units
minimum rejected-inference counts
universal time budgets
automatic source-gate scoring
universal quality metrics
automatic implementation roadmaps
repository parsers
AST analysis
persistent databases
runtime orchestration
```

These belong to external execution or later tooling where justified.

---

# 67. FINAL PRINCIPLE

ASMA must become stricter where stricter behavior protects truth.

It must remain flexible where rigidity would manufacture noise.

The protocol therefore prefers:

```text
unknown over fabricated precision
selection over exhaustive processing
evidence over completion
mechanism over label
identity over similarity
source state over arbitrary score
useful omission over forced completeness
```

And above all:

```text
DO NOT DEEPEN WHAT HAS NOT BEEN SELECTED.
DO NOT SUPPORT WHAT HAS NOT BEEN ANCHORED.
DO NOT MERGE WHAT HAS NOT BEEN SHOWN TO MATCH.
DO NOT CONTINUE WHAT NO LONGER ADDS MATERIAL HARVEST.
```
