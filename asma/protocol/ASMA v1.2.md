# ASMA v1.2

## Final Mechanism Harvest Protocol

---

# 0. PURPOSE

ASMA is a source-adaptive protocol for extracting reusable mechanisms, claims, constraints, patterns, methods and implementation-relevant structures from technical material while preserving epistemic discipline.

Primary objective:

> maximize useful information recovered per unit of analysis cost without upgrading source statements beyond what the available evidence supports.

ASMA is not primarily a summarizer.

ASMA is not a universal quality scorer.

ASMA is not a cloning system.

ASMA is a **harvest-gated analysis protocol**.

Its primary product is a provenance-bearing inventory of reusable units.

---

# 1. SCOPE

ASMA can analyze:

```text
SYSTEM
    prompts
    skills
    workflows
    routers
    tool catalogs
    schemas
    evaluation loops
    AI control protocols

KNOWLEDGE
    papers
    technical articles
    methodological documents
    benchmark reports
    technical essays

ARTIFACT
    repositories
    libraries
    codebases
    schemas
    implementations
    code + tests
```

ASMA itself is a **prompt-level analytical protocol**.

It does not claim runtime enforcement by itself.

External orchestration, JSON validation, repository retrieval, parsers, execution environments and other infrastructure are outside the core protocol.

---

# 2. CORE INVARIANTS

## P1 — SOURCE FIDELITY

Describe what the source contains before explaining why it exists.

Do not replace the source with a cleaner theory of what it "must mean."

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

Unknown is a legitimate result.

Do not fill missing information because a template contains a field.

---

## P4 — MECHANISM OVER LABEL

Describe the functional operation before assigning a technique label.

A label is secondary evidence about similarity, not the mechanism itself.

---

## P5 — PROCESS IS PART OF THE MECHANISM

Ordering, routing, branching, iteration, selection and stopping are part of system behavior.

Preserve process relations such as:

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

A source may claim that a mechanism improves something.

That does not establish that the effect was demonstrated.

---

## P8 — ENFORCEMENT MATTERS

For objects where enforcement is applicable, distinguish:

```text
PROSE_ONLY
SCHEMA_CONSTRAINED
RUNTIME_CONSTRAINED
HOST_CONSTRAINED
EXTERNAL_CONSTRAINT
UNKNOWN
NOT_APPLICABLE
```

`NOT_APPLICABLE` means the object is not an enforcement-bearing rule or constraint.

---

## P9 — PRESERVE EVIDENCE LAYERS

For artifacts and mixed sources distinguish:

```text
DOCUMENTED_DESIGN
IMPLEMENTED_STRUCTURE
TESTED_BEHAVIOR
OBSERVED_RUNTIME
CONTEXT
UNKNOWN
```

Do not silently collapse them.

---

## P10 — EXTRACT THE MECHANISM, NOT THE ARCHITECTURE

Transfer only the functional part that survives isolation.

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
UNSUPPORTED
CONFLICT
MISSING_IMPLEMENTATION
UNVERIFIED_EFFECT
DEPENDENCY
FAILURE_CONDITION
```

---

## P12 — NO UNIVERSAL QUALITY SCORE

ASMA does not assign a universal numeric quality score.

It determines:

```text
what is recoverable
what is reusable
what is supported
what remains uncertain
whether further analysis is justified
```

---

# 3. INPUT CONTRACT

```text
SOURCE:
    material to inspect

SOURCE_CONTEXT:
    optional supporting context supplied by the user

PROJECT_CONTEXT:
    optional description of what the user is building or looking for

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

---

# 4. SOURCE_PLUS_CONTEXT

Context may add:

```text
PROJECT_CONTEXT
runtime notes
author notes
user observations
external assumptions
```

Context does not become `SOURCE_FACT`.

Any statement supported only by context must remain:

```text
[CONTEXT]
```

Do not use context to strengthen source evidence.

---

# 5. SOURCE LENSES

Select the minimum set of lenses required by the source.

```text
LENS_SYSTEM
LENS_KNOWLEDGE
LENS_ARTIFACT
```

Do not activate all lenses merely because a source contains multiple media types.

For mixed sources, assign the lens at the **candidate/unit level** when necessary.

---

# 6. LENS_SYSTEM

Use for prompts, agents, workflows, routers, tools and control protocols.

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

Useful relations:

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

# 7. LENS_KNOWLEDGE

Use for papers, articles and technical knowledge sources.

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

Preserve:

```text
what the source argues
what was measured
what evidence supports
what the authors infer
what ASMA infers
```

Citation repetition is not automatically independent evidence.

---

# 8. LENS_ARTIFACT

Use for repositories, libraries, implementations and code + tests.

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

Evidence layers:

```text
DOCUMENTED_DESIGN
IMPLEMENTED_STRUCTURE
TESTED_BEHAVIOR
OBSERVED_RUNTIME
```

When documentation, code and tests disagree:

```text
record discrepancy
do not silently resolve it
```

---

# 9. INTAKE

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

Do not deeply interpret the source at intake.

The purpose of INTAKE is routing.

---

# 10. INTAKE POLICY

For large or context-limited sources, use source-specific intake order.

## SYSTEM

Prefer:

```text
surface specification
→ interfaces
→ routing/process
→ selected details
```

## KNOWLEDGE

Prefer:

```text
abstract/claims
→ method
→ results/evaluation
→ limitations
→ selected supporting detail
```

## ARTIFACT

Prefer:

```text
manifest / README / API surface
→ public entry points
→ tests tied to public behavior
→ selected implementation
→ supporting configuration/dependencies
```

Do not walk the entire source merely because material exists.

---

# 11. MAP

Create a compact structural map sufficient to locate likely reusable material.

The map should identify:

```text
major sections/components
likely signal
unknown areas
candidate locations
scope boundaries
```

MAP is orientation, not deep analysis.

---

# 12. PROBE

Before filtering, perform a cheap, recall-oriented probe.

Candidates may be detected from:

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

At PROBE stage:

```text
evidence = location-level evidence
```

Do not require full interpretation yet.

The purpose is to avoid false negatives caused by insufficient early context.

---

# 13. CANDIDATE RECORD

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
STATUS
```

Candidate status:

```text
PENDING
DEEPEN
DROP
```

A candidate is not yet a reusable unit.

---

# 14. FILTER 1 — RECALL FILTER

FILTER 1 is performed before deepening.

Its purpose is to remove obvious non-candidates without requiring full evidence.

Allowed DROP reasons:

```text
DUPLICATE
OUTSIDE_SCOPE
RESTATEMENT
NO_DISTINCT_FUNCTION
CLEARLY_NON_TRANSFERABLE
```

Do **not** use:

```text
UNSUPPORTED
INSUFFICIENT_EVIDENCE
UNKNOWN
```

as FILTER 1 drop reasons.

If more evidence is required, the candidate remains:

```text
DEEPEN
```

This preserves recall.

---

# 15. DEPTH BUDGET

Depth budget is a cap, not a score.

## LIGHT

```text
max 7 candidates
max 3 deepened candidates
SURFACE depth only
no dependency tracing
```

## TARGETED

```text
max 12 candidates
max 5 deepened candidates
SURFACE → CONTEXT
dependency tracing only when required for unitization
```

## DEEP

```text
no fixed candidate cap
CONTEXT → TRACE allowed
full relevant dependency tracing
still subject to material stop
```

Do not treat these limits as quality scores.

---

# 16. CANDIDATE DEPTH

Candidate inspection depth:

```text
SURFACE
    enough to characterize the candidate

CONTEXT
    surrounding material required to establish function/dependencies

TRACE
    implementation, evidence, tests, relations or dependency paths
    required to resolve the candidate
```

`DEPTH_BUDGET` limits how many candidates and how much work may be spent.

Candidate depth describes how far one selected candidate is inspected.

---

# 17. DEEPEN

Deepen only candidates marked `DEEPEN`.

Deepening must answer:

```text
What does this actually do?
What evidence supports that?
What does it depend on?
What happens if isolated?
What form can be transferred?
What remains unknown?
```

Do not deepen a candidate merely to fill a template.

---

# 18. FILTER 2 — PRECISION FILTER

After deepening, each selected candidate becomes:

```text
SOURCE_SUPPORTED
CONDITIONAL
REJECTED
```

## SOURCE_SUPPORTED

The extracted unit is supported at the claimed evidentiary level.

This does not mean demonstrated effectiveness.

## CONDITIONAL

The unit may be valid, but important assumptions or evidence gaps remain.

## REJECTED

The candidate does not survive evidence or transfer analysis.

Rejected candidates remain in the ledger.

---

# 19. CANONICAL UNIT

Only `SOURCE_SUPPORTED` or `CONDITIONAL` candidates may become Units.

Canonical record:

```text
UNIT_ID
LENS
TYPE
STATUS

FUNCTION
MINIMAL_FORM

SOURCE_ANCHOR
EVIDENCE_TYPE

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

REJECTED_INFERENCES
RELATES_TO
```

Fields are lens-dependent.

Do not fabricate non-applicable fields.

---

# 20. UNIT TYPES

Primary `TYPE` must come from this closed set:

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

One primary type per unit.

Optional secondary tags may describe additional relations.

---

# 21. MINIMAL_FORM

`MINIMAL_FORM` is the compact transferable form of the unit.

It must be:

```text
one line where possible
functional rather than promotional
usable without the original essay
free of quality adjectives
free of unsupported conclusions
```

Good:

```text
generate[N] → evaluate/select
search → fetch → inspect before answer
public fn(X) → Y; tests lock behavior on cases A,B
claim C measured by M on D; off-domain effect unknown
```

Bad:

```text
advanced reasoning architecture that significantly improves quality
```

A `MINIMAL_FORM` is a representation of the unit, not a summary paragraph.

---

# 22. EVIDENCE

Every Unit requires a source anchor.

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

For `SOURCE_FACT`, use a direct source anchor.

A precise quotation is preferred when practical, but location is acceptable when the source is structured and the claim is directly recoverable there.

Do not fabricate precision.

---

# 23. EVIDENCE TYPE

Use:

```text
SOURCE_FACT
DIRECT_INFERENCE
MECHANISTIC_HYPOTHESIS
EFFECTIVENESS_CLAIM
EXTERNAL_EVIDENCE
CONTEXT
```

Evidence type must never be stronger than the evidence anchor supports.

---

# 24. BREAKS_IF_ISOLATED

`BREAKS_IF_ISOLATED` describes what depends on surrounding architecture.

Also record:

```text
ISOLATION_STATUS:
    SOURCE_FACT
    DIRECT_INFERENCE
    MECHANISTIC_HYPOTHESIS
    UNKNOWN
```

Do not present a mechanistic hypothesis as a source-established fact.

---

# 25. ENFORCEMENT

Enforcement is applicable to rules, constraints, schemas and control structures.

Use:

```text
PROSE_ONLY
SCHEMA_CONSTRAINED
RUNTIME_CONSTRAINED
HOST_CONSTRAINED
EXTERNAL_CONSTRAINT
UNKNOWN
NOT_APPLICABLE
```

For objects such as:

```text
claim
method
algorithm
design_principle
```

use:

```text
NOT_APPLICABLE
```

when enforcement is not the relevant property.

---

# 26. EFFECT STATUS

Effectiveness is a separate dimension.

Use:

```text
CLAIMED
TESTED_IN_SOURCE
EXTERNALLY_SUPPORTED
UNKNOWN
NOT_APPLICABLE
```

Never encode effectiveness into `STATUS`.

---

# 27. DISCREPANCY

For conflicting evidence layers, use:

```text
DISCREPANCY:
    DOCUMENTED:
    IMPLEMENTED:
    TESTED:
    OBSERVED:
```

Do not choose one layer as universally authoritative.

The relevant evidence layer depends on the question being asked.

---

# 28. TRANSFER FORM

Use:

```text
DIRECT_TRANSFER
ADAPTATION_REQUIRED
CONCEPT_ONLY
NON_TRANSFERABLE
```

Possible output shapes:

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

---

# 29. PROJECT CONTEXT

`PROJECT_CONTEXT` may influence selection and relevance.

It may not alter factual interpretation.

Correct:

```text
LESS_RELEVANT_TO_PROJECT
```

Incorrect:

```text
SOURCE_MUST_HAVE_THIS_BECAUSE_PROJECT_NEEDS_IT
```

Project context may not create evidence.

It may also not upgrade a weak candidate into `SOURCE_SUPPORTED`.

---

# 30. REJECTED INFERENCES

Maintain:

```text
REJECTED_INFERENCES
```

Record important interpretations that were considered and rejected.

Example:

```text
instruction ≠ demonstrated effectiveness
README claim ≠ runtime behavior
test presence ≠ full implementation coverage
named technique ≠ exact implementation
```

This record protects the source/inference boundary.

---

# 31. CANDIDATE LEDGER

The Candidate Ledger is mandatory in every non-trivial run.

```text
CANDIDATE_ID
UNIT_ID
LENS
LOCATION
FILTER_1_RESULT
DEEPENED
DEPTH_USED
FILTER_2_RESULT
DROP_REASON
STATUS_CHANGE
```

The ledger is the evidence that:

```text
PROBE → FILTER → DEEPEN
```

actually occurred.

A candidate may have no Unit if it is dropped or rejected.

---

# 32. CANONICAL RECORD

ASMA has one canonical internal output:

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

This record is the source of truth.

All presentation modes are views over this record.

Do not create separate competing representations of the same Unit.

---

# 33. OUTPUT MODES

## HARVEST

Emit:

```text
SOURCE_MAP
UNITS
UNKNOWN
REJECTED_INFERENCES
SOURCE_GATE
```

Candidate Ledger may be shown when auditability matters.

## ANALYSIS

Emit:

```text
SOURCE_MAP
relations among Units
dependencies
process/architecture
failures
UNKNOWN
```

Reference Units by `UNIT_ID`.

Do not restate their entire contents.

## AUDIT

Emit:

```text
evidence
claim status
enforcement
discrepancies
rejected inferences
audit state
```

## FULL

Emit the views above from the same canonical record.

Never duplicate a Unit merely because multiple views mention it.

---

# 34. THREE VOICES

Three voices are optional presentation views.

## VOICE 1 — FORENSIC

Detailed technical reconstruction.

Use only when technical depth is needed.

## VOICE 2 — HARVEST INDEX

Compact index:

```text
UNIT_ID
WHAT_IT_DOES
WHY_IT_MAY_MATTER
TRANSFER_FORM
DEPENDENCY
EVIDENCE_STATUS
MAIN_LIMIT
```

Voice 2 may only reference Units present in the canonical record.

## VOICE 3 — ROUTING TOKEN

```text
SOURCE
STRONGEST_HARVEST
MAIN_LIMIT
SOURCE_GATE
```

Voice 3 is not a separate judgment system.

---

# 35. LOCAL HALT

At candidate level:

```text
DEPTH_HALT
```

means:

> this candidate is sufficiently characterized.

It does not mean the source is exhausted.

---

# 36. SOURCE GATE

At source level:

```text
SOURCE_GATE:
    CONTINUE
    CONTINUE_CONDITIONALLY
    STOP
```

## CONTINUE

Additional material is likely to add materially new harvest.

## CONTINUE_CONDITIONALLY

Additional analysis requires a named missing input.

Example:

```text
CONTINUE_CONDITIONALLY:
    inspect src/router.py and its corresponding tests
```

## STOP

Additional analysis is not currently justified.

STOP does not mean the source is absolutely exhausted.

---

# 37. SESSION CONTINUITY

When additional source material arrives:

```text
preserve existing UNIT_ID
preserve SOURCE_SUPPORTED units unless contradicted
re-open CONDITIONAL / UNKNOWN candidates
probe newly added material
emit DIFF rather than rebuilding unchanged material
```

New candidate relation:

```text
NEW
SAME_UNIT
EXTENDS
CONFLICTS
```

Existing Units may be:

```text
UNCHANGED
EXTENDED
DOWNGRADED
CONTRADICTED
```

A previous Unit does not become permanent truth merely because it was previously emitted.

---

# 38. MULTI-SOURCE HARVEST

For multiple sources:

```text
SOURCE_ORIGIN
PRIMARY_SUPPORT
SECONDARY_SUPPORT
CONFLICTS
```

When a new candidate overlaps an existing Unit:

```text
SAME_UNIT
EXTENDS
CONFLICTS
NEW
```

Do not merge merely because two sources use similar language.

Do not treat repetition as independent confirmation.

---

# 39. VERIFY MODE

VERIFY is a targeted mode.

Select verification targets only when they matter to the task.

Priority:

```text
effectiveness claims
material conflicts
high-impact uncertain claims
claims whose verification could change adoption
```

Each target:

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

`NOT_VERIFIED` must distinguish:

```text
UNAVAILABLE
NOT_SEARCHED
SEARCH_FAILED
SEARCHED_NO_SUPPORT_FOUND
```

Absence of support is not automatically refutation.

---

# 40. COMPARATIVE MODE

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

Do not use universal quality ranking.

Do not force unrelated sources onto identical structures.

---

# 41. SELF-FAILURE MODES

ASMA must monitor for:

## CATEGORY_FORCING

The lens does not fit the source.

Response:

```text
switch lens
split candidate
or mark unsupported
```

## HARVEST_COLLAPSE

The output becomes summary rather than inventory.

Response:

```text
return to candidate/unit representation
```

## DEPTH_DRIFT

Analysis continues after sufficient characterization.

Response:

```text
DEPTH_HALT
```

## EVIDENCE_DRIFT

Inference becomes source fact.

Response:

```text
downgrade claim
re-anchor
or reject
```

## UNIT_FRAGMENTATION

One transferable mechanism is split into trivial units.

Response:

```text
merge where no independent transfer value exists
```

## UNIT_MONOLITH

An entire architecture is emitted as one Unit.

Response:

```text
decompose into transferable mechanisms
```

## TEMPLATE_PRESSURE

Fields are filled because they exist.

Response:

```text
omit non-applicable material
```

## HARVEST_NOISE

Large amount of technically true material, little reusable signal.

Response:

```text
tighten FILTER_1
tighten MATERIAL_TEST
```

---

# 42. MATERIAL TEST

A candidate should normally reach DEEPEN when:

```text
it has a distinct function
AND
it has a plausible transfer form or represents a load-bearing
constraint/failure
AND
it is not merely a restatement
```

Evidence sufficiency is **not** required at FILTER_1.

After DEEPEN, a candidate may become:

```text
SOURCE_SUPPORTED
CONDITIONAL
REJECTED
```

---

# 43. AUDIT INVARIANTS

Before emission:

```text
I1 Every candidate has a ledger disposition.

I2 Every DEEPEN candidate has either:
   a Unit,
   or an explicit rejection/UNITIZATION_FAILURE.

I3 Every Unit has a source anchor.

I4 Every Unit.evidence_type is no stronger than its anchor.

I5 Voice 2 references only existing Unit IDs.

I6 Effectiveness is never encoded as Unit STATUS.

I7 FILTER_1 never uses "insufficient evidence" as DROP reason.

I8 Non-applicable fields are omitted or marked NOT_APPLICABLE.

I9 Source conflicts are preserved rather than silently reconciled.

I10 Existing stable Unit IDs are preserved across session continuation.
```

If an invariant fails:

```text
AUDIT_STATUS:
    FAIL
```

and the output must expose the relevant failure.

---

# 44. DEFAULT EXECUTION

For:

```text
"analyze this with ASMA"
```

default to:

```text
ANALYSIS_MODE: SOURCE_ONLY
OUTPUT_MODE: HARVEST
DEPTH_BUDGET: TARGETED
```

Execution:

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

Do not automatically produce maximal analysis.

---

# 45. FINAL AUDIT

Before emission check:

```text
SOURCE FIDELITY
CLAIM DISCIPLINE
LENS FIT
CANDIDATE LEDGER
FILTER ORDER
EVIDENCE ANCHORS
ENFORCEMENT APPLICABILITY
DEPENDENCIES
ISOLATION STATUS
DISCREPANCIES
REJECTED INFERENCES
UNKNOWN
DUPLICATION
UNIT STABILITY
SOURCE GATE
```

---

# 46. CANONICAL UNIT — REFERENCE SHAPE

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
rejected_inferences:
```

Fields are conditional by lens.

No empty decorative fields.

---

# 47. CANONICAL ASMA RECORD — REFERENCE SHAPE

```yaml
source_map:
candidate_ledger: []

units: []

unknown: []

rejected_inferences: []

global_discrepancies: []

audit:
  status:
  invariant_results: []

source_gate:
  status:
  condition:
```

---

# 48. CENTRAL PROCESS CONSTRAINT

The primary invariant of ASMA v1.2 is:

```text
SELECT BEFORE DEEPENING.
```

Operationally:

```text
PROBE BEFORE PRECISION FILTER
PRECISION FILTER AFTER EVIDENCE
DEPTH_HALT BEFORE SOURCE_GATE
```

ASMA must not:

```text
deep-analyze everything
then select
```

and must not:

```text
reject unseen material merely because evidence is incomplete
```

---

# 49. FINAL DEFINITION

ASMA v1.2 is a source-adaptive protocol that probes material for candidate reusable units, filters without requiring premature evidence, selectively deepens only surviving candidates, audits their evidence and dependencies, emits them through one canonical record, preserves uncertainty and disagreement, and determines whether further source analysis is justified.

Its central product is not the report.

It is the **provenance-bearing reusable unit**.
