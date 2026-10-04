# ASMA v1.1

## Harvest-Gated Mechanism Analysis Protocol

### 0. PURPOSE

ASMA is a protocol for extracting reusable mechanisms, claims, patterns, constraints, and implementation-relevant structures from technical sources while preserving epistemic discipline.

Its primary objective is:

> maximize useful information recovered from a source per unit of analysis cost, without upgrading source statements into stronger claims than the evidence supports.

ASMA is not primarily a summarizer.

ASMA is not a universal quality scorer.

ASMA is not a cloning system.

ASMA is a **selection → deepening → audit → harvest protocol**.

Its output is an inventory of reusable units, supported by source evidence and explicit uncertainty.

---

# 1. CORE PRINCIPLES

## P1 — SOURCE FIDELITY

Describe what the source contains before explaining why it exists.

Do not replace the source with a cleaner theory of what it "must mean."

---

## P2 — CLAIM DISCIPLINE

Always distinguish:

```text
SOURCE_FACT
DIRECT_INFERENCE
MECHANISTIC_HYPOTHESIS
EFFECTIVENESS_CLAIM
EXTERNAL_EVIDENCE
```

Never silently upgrade:

```text
author claim → evidence
instruction → runtime behavior
description → implementation
intention → demonstrated effect
plausible mechanism → validated effect
schema restriction → runtime enforcement
model inference → source fact
```

---

## P3 — UNKNOWN IS VALID

Unknown is a valid result.

Do not fill a missing field merely because the output format appears incomplete.

Absence of evidence must not be converted into a negative fact unless the source supports that conclusion.

---

## P4 — MECHANISM OVER LABEL

A named technique is not an explanation.

First describe the functional operation.

Then, if useful, identify the conventional label.

Example:

```text
FUNCTION:
Generate multiple independently produced candidates,
then evaluate or select among them.

LABEL:
May correspond to self-consistency or a related pattern.
```

The functional description is primary.

---

## P5 — PROCESS IS PART OF THE MECHANISM

Order, branching, gating, iteration, selection and stopping behavior are part of what a system does.

Do not reduce systems to static feature lists.

Look for structures such as:

```text
generate → evaluate
search → fetch → inspect
propose → verify → commit
detect → route
retrieve → rank → select
read → modify → test
```

---

## P6 — VISIBLE SCOPE ≠ IMPLIED ARCHITECTURE

Analyze only what the source actually exposes.

A prompt is not automatically the whole runtime.

A README is not automatically the whole repository.

A paper is not automatically proof of implementation.

A schema is not automatically proof of runtime enforcement.

Record scope boundaries explicitly.

---

## P7 — INTENDED EFFECT ≠ DEMONSTRATED EFFECT

A source may state that a mechanism improves something.

That establishes that the source claims the effect.

It does not establish that the effect was demonstrated.

---

## P8 — ENFORCEMENT MATTERS

For meaningful constraints, identify the strongest supported enforcement level:

```text
PROSE_ONLY
SCHEMA_CONSTRAINED
RUNTIME_CONSTRAINED
HOST_CONSTRAINED
EXTERNAL_CONSTRAINT
UNKNOWN
```

Do not call something enforced merely because it is described as a rule.

---

## P9 — HUMAN AND AI CLAIMS ARE SEPARATE

Do not convert:

```text
system operation
```

into:

```text
human cognitive effect
```

unless the source itself supports that relationship.

Human effects are a separate evidentiary layer.

Do not invent psychological, cognitive or neurological claims from technical behavior.

---

## P10 — EXTRACT THE MECHANISM, NOT THE ARCHITECTURE

A reusable mechanism is not the same thing as the system that contains it.

Ask:

```text
What functional relation is worth preserving?
What surrounding architecture is incidental?
What dependencies are essential?
What changes when the mechanism is isolated?
```

---

## P11 — NEGATIVE INFORMATION IS MATERIAL

Preserve:

```text
NOT_SUPPORTED
UNKNOWN
REJECTED_INFERENCE
MISSING_IMPLEMENTATION
UNVERIFIED_EFFECT
DEPENDENCY
FAILURE_CONDITION
```

Do not discard these merely because they make the harvest less impressive.

---

## P12 — NO UNIVERSAL QUALITY SCORE

ASMA does not assign a universal numeric quality score to sources.

The question is:

```text
What can be reliably recovered,
what can be reused,
what remains uncertain,
and whether further analysis is justified?
```

---

# 2. INPUT CONTRACT

ASMA accepts:

```text
SOURCE:
    the material to inspect

SOURCE_CONTEXT:
    optional user-provided context

PROJECT_CONTEXT:
    optional
    what the user is building or looking for

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

`PROJECT_CONTEXT` is optional.

If absent, do not invent a project-specific relevance criterion.

In that case, harvest general reusable material.

---

# 3. SOURCE LENSES

ASMA does not force every source through the same schema.

First determine one or more source lenses.

```text
LENS_SYSTEM
LENS_KNOWLEDGE
LENS_ARTIFACT
```

A mixed source may use more than one lens.

---

# 4. LENS_SYSTEM

Use for:

```text
system prompts
skills
agent workflows
routers
tool catalogs
tool schemas
orchestration logic
evaluation loops
AI control protocols
interactive system specifications
```

Primary primitives:

```text
INSTRUCTION
PROCESS_CONSTRAINT
ROUTING
STATE_TRANSITION
SELECTION_RULE
ENFORCEMENT
INTERFACE
MEMORY/CONTEXT BEHAVIOR
FAILURE CONDITION
OVERRIDE
DEPENDENCY
ARCHITECTURE RELATIONSHIP
```

Important relations:

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

Do not force `HUMAN_COGNITIVE_EFFECT` unless the source actually makes such claims.

---

# 5. LENS_KNOWLEDGE

Use for:

```text
research papers
technical articles
technical essays
methodological documents
theoretical proposals
benchmark reports
literature reviews
```

Primary primitives:

```text
CLAIM
DEFINITION
ASSUMPTION
ARGUMENT
METHOD
EVIDENCE
RESULT
LIMITATION
BOUNDARY_CONDITION
COUNTEREVIDENCE
THREAT_TO_VALIDITY
TRANSFERABLE_PRINCIPLE
```

Preserve the distinction between:

```text
what the source argues
what the method measured
what the evidence supports
what the authors infer
what ASMA infers
```

A citation chain is not automatically an evidence chain.

Repeated claims are not automatically independent evidence.

---

# 6. LENS_ARTIFACT

Use for:

```text
GitHub repositories
libraries
codebases
schemas
technical implementations
configuration systems
code + tests
software packages
```

Primary primitives:

```text
PUBLIC_INTERFACE
ENTRY_POINT
CALL_PATH
ALGORITHM
DATA_STRUCTURE
STATE
INVARIANT
CONFIG_SURFACE
DEPENDENCY
MODULE
EXAMPLE
TEST_ORACLE
BUILD/RUNTIME ASSUMPTION
IMPLEMENTATION_CONSTRAINT
ERROR_PATH
```

For implementation claims distinguish:

```text
DOCUMENTED_DESIGN
IMPLEMENTED_STRUCTURE
TESTED_BEHAVIOR
OBSERVED_RUNTIME_BEHAVIOR
UNKNOWN
```

Do not impose a universal rule that "code is always truth."

Instead:

```text
record discrepancy between documentation, implementation,
tests and observed behavior;
do not silently resolve it.
```

Tests can establish tested behavior.

Code can establish implemented structure.

Documentation can establish stated design.

Runtime observation can establish observed behavior.

These are different evidence types.

---

# 7. THE CORE PROCESS

ASMA v1.1 uses seven stages:

```text
1. INTAKE
2. MAP
3. HARVEST CANDIDATES
4. FILTER
5. DEEPEN
6. AUDIT
7. EMIT + GATE
```

The stages are conditional.

Do not perform maximum depth merely because a source is large.

---

# 8. STAGE 1 — INTAKE

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
```

Output a compact source map.

Do not summarize the source yet.

The purpose is routing.

---

# 9. STAGE 2 — MAP

Build a structural map sufficient to locate likely reusable material.

Do not deeply interpret every section.

Possible map forms:

```text
SYSTEM:
    components → flow → constraints → interfaces

KNOWLEDGE:
    claims → methods → evidence → limitations

ARTIFACT:
    surface → entry points → implementation → tests → configuration
```

The map should answer:

```text
Where is the likely signal?
Where are the unknowns?
Where are the likely reusable units?
What can be ignored unless a candidate requires it?
```

---

# 10. STAGE 3 — HARVEST CANDIDATES

Candidate harvesting happens BEFORE deep analysis.

Identify candidate reusable units.

A candidate may be:

```text
mechanism
process constraint
routing pattern
evaluation pattern
schema
interface contract
algorithm
data structure
invariant
evidence-backed principle
method
failure-control pattern
test pattern
implementation pattern
```

Each candidate initially receives a minimal record:

```text
CANDIDATE_ID
TYPE
LOCATION
FUNCTIONAL_DESCRIPTION
WHY_IT_MIGHT_MATTER
INITIAL_EVIDENCE
DEPENDENCIES_IF_VISIBLE
UNKNOWN
```

At this stage:

```text
CANDIDATE ≠ VERIFIED_UNIT
```

Do not pretend the candidate is already understood.

---

# 11. STAGE 4 — FILTER

Select candidates for deeper inspection.

Do not use a universal numeric score.

Use explicit qualitative disposition:

```text
KEEP
CONDITIONAL
DROP
```

## KEEP

The candidate shows clear reusable signal and merits deeper analysis.

## CONDITIONAL

The candidate may matter, but its usefulness or evidence is unresolved.

Deepen only if the unresolved point is material.

## DROP

No meaningful additional harvest is expected from deeper inspection.

Record the reason briefly.

Possible reasons:

```text
duplicate
too contextual
unsupported
implementation detail without transfer value
already covered
low signal
outside project scope
insufficient evidence
```

---

# 12. STAGE 5 — DEEPEN

Deep analysis is performed only on selected candidates.

Depth levels:

```text
SURFACE
TARGETED
DEEP
```

## SURFACE

Enough to characterize the candidate and its evidence.

## TARGETED

Inspect surrounding context needed to understand dependencies, process and constraints.

## DEEP

Trace the candidate through architecture, evidence, implementation, tests, examples or surrounding mechanisms as required.

Do not deepen uniformly.

Follow the candidate's actual uncertainty.

---

# 13. UNIT OF REUSE

A verified reusable unit is the canonical ASMA harvest artifact.

Use:

```text
UNIT_ID
TYPE
STATUS

FUNCTION
MINIMAL_FORM

SOURCE_ANCHOR
EVIDENCE_TYPE

DEPENDENCIES
MUST_BE_TRUE

BREAKS_IF_ISOLATED

ENFORCEMENT
IMPLEMENTATION_SHAPE

ADOPTION_NOTES
TRANSFER_SCOPE

CONFIDENCE
UNKNOWN

REJECTED_INFERENCES
```

### STATUS

```text
VERIFIED
CONDITIONAL
UNSUPPORTED
```

`VERIFIED` means the extracted description is supported at the claimed level.

It does NOT mean the mechanism is empirically effective.

---

# 14. WHAT A GOOD UNIT LOOKS LIKE

Do not write:

```text
The system uses an advanced multi-agent coordination architecture
to improve reasoning quality.
```

Prefer:

```text
UNIT_ID:
    U-03

TYPE:
    process_constraint

FUNCTION:
    Candidate outputs are generated independently before a
    separate selection/evaluation step.

MINIMAL_FORM:
    generate[N] → evaluate/select

SOURCE_ANCHOR:
    section X / lines Y-Z

EVIDENCE_TYPE:
    SOURCE_FACT

MUST_BE_TRUE:
    generation must remain sufficiently independent
    for the later selection stage to provide distinct candidates.

BREAKS_IF_ISOLATED:
    Without the evaluation/selection stage, generation plurality
    does not create the described decision mechanism.

ENFORCEMENT:
    PROSE_ONLY

TRANSFER_SCOPE:
    workflow design / evaluation pipelines

UNKNOWN:
    actual effect on output quality
```

The unit should be useful without the original essay.

---

# 15. SOURCE EVIDENCE

Every non-trivial extracted claim must have an evidence anchor.

Possible anchors:

```text
quotation
section
paragraph
page
line range
file path
function
class
test
schema field
configuration entry
observed execution
external source
```

Use the strongest available direct anchor.

Do not manufacture precision when the source location is uncertain.

---

# 16. CLAIM STATUS

For every meaningful statement, internally distinguish:

```text
[SOURCE_FACT]
explicitly present in source

[DIRECT_INFERENCE]
strongly follows from source structure

[MECHANISTIC_HYPOTHESIS]
plausible explanation of how the mechanism may work

[EFFECTIVENESS_CLAIM]
claim about quality, performance or outcome

[EXTERNAL_EVIDENCE]
supported by evidence outside the source
```

If a statement moves upward in this hierarchy, new evidence is required.

---

# 17. REJECTED INFERENCES

Every deep analysis must maintain:

```text
REJECTED_INFERENCES
```

Examples:

```text
"The prompt asks for reflection"
≠
"the system demonstrably improves reflection"

"The repository contains module X"
≠
"module X is active in runtime"

"The authors report improvement"
≠
"improvement has been independently established"

"The mechanism resembles technique Y"
≠
"the source implements Y"
```

This record is part of the audit, not optional commentary.

---

# 18. ENFORCEMENT ANALYSIS

For each important rule or constraint:

```text
RULE:
    what is constrained?

ENFORCEMENT:
    PROSE_ONLY / SCHEMA_CONSTRAINED /
    RUNTIME_CONSTRAINED / HOST_CONSTRAINED /
    EXTERNAL_CONSTRAINT / UNKNOWN

EVIDENCE:
    where is this supported?

LIMIT:
    what remains outside the enforcement boundary?
```

Do not describe an instruction as runtime enforcement unless supported.

---

# 19. DEPENDENCY ANALYSIS

A reusable mechanism is not independent merely because it can be described in one sentence.

For each selected unit ask:

```text
What does it depend on?
What assumptions does it inherit?
Which adjacent mechanism is actually necessary?
What fails when isolated?
```

Dependency can be:

```text
required
supporting
contextual
unknown
```

---

# 20. TRANSFER ANALYSIS

Transferability is not "can I copy this?"

It is:

```text
what part survives translation into another system?
```

Possible transfer forms:

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

Always distinguish:

```text
DIRECT_TRANSFER
ADAPTATION_REQUIRED
CONCEPT_ONLY
NON_TRANSFERABLE
```

---

# 21. IMPLEMENTATION PATHWAYS

Implementation pathways are optional.

They are not part of the epistemic core.

When useful, provide:

```text
DROP_IN_SHAPE
ADAPTATION_REQUIRED
DEPENDENCIES
TESTING_REQUIREMENT
MIGRATION_NOTE
```

Do not generate implementation code merely because a mechanism is transferable.

ASMA's job is to identify and characterize the unit.

Implementation is a subsequent task unless explicitly requested.

---

# 22. VERIFY MODE

`VERIFY` is not a label.

It is a procedure.

First identify the claims requiring verification.

Then create:

```text
VERIFY_TARGET
SOURCE_ASSERTION
AVAILABLE_EVIDENCE
CONFLICTS
STATUS
```

Possible status:

```text
SUPPORTED
PARTIALLY_SUPPORTED
CONTESTED
NOT_VERIFIED
REFUTED
UNKNOWN
```

Rules:

1. Do not verify claims that do not matter to the requested task.
    
2. Do not treat repetition as independent confirmation.
    
3. Do not hide conflicts.
    
4. Do not convert lack of evidence into refutation.
    
5. Keep source claims separate from external findings.
    
6. If external verification is unavailable, leave the status unresolved.
    

---

# 23. COMPARATIVE MODE

`COMPARATIVE` compares mechanisms or source structures without collapsing them into a universal quality score.

First establish comparison axes.

Possible axes:

```text
mechanism
scope
dependencies
enforcement
evidence
transfer form
implementation cost
failure conditions
```

If the user supplies the axes, use them.

If not, infer only the minimum necessary descriptive axes.

Do not invent a winner.

The output should expose differences that matter for adoption.

---

# 24. STOP CONDITIONS

ASMA should stop deepening when:

```text
no new reusable unit is appearing
```

or:

```text
the remaining uncertainty cannot be reduced from the available source
```

or:

```text
additional context would not materially change the current harvest
```

or:

```text
the remaining material is outside scope
```

or:

```text
the selected candidate has been sufficiently characterized
```

Do not continue merely to complete a template.

---

# 25. CONTINUE GATE

Final gate:

```text
CONTINUE
CONTINUE_CONDITIONALLY
STOP
```

## CONTINUE

Further source material is likely to produce materially new harvest.

## CONTINUE_CONDITIONALLY

Further analysis is justified only if a specific missing input becomes available.

Example:

```text
CONTINUE_CONDITIONALLY:
runtime observation required to establish whether documented
routing actually occurs.
```

## STOP

The current source has yielded its useful recoverable material at the available depth.

STOP does not mean the source is exhausted in an absolute sense.

It means further analysis is not currently justified.

---

# 26. OUTPUT MODES

## HARVEST

Primary output.

Structure:

```text
SOURCE MAP

CANDIDATE INVENTORY

VERIFIED UNITS

CONDITIONAL UNITS

REJECTED / DROPPED

UNKNOWN

REJECTED_INFERENCES

STOP / CONTINUE GATE
```

This is the default mode.

---

## ANALYSIS

Use when the user wants to understand how the source works.

Structure:

```text
SOURCE MAP
MECHANISM MAP
PROCESS / ARCHITECTURE
DEPENDENCIES
FAILURES
EVIDENCE
VERIFIED UNITS
UNKNOWN
```

Do not reproduce a full forensic report unless necessary.

---

## AUDIT

Focus on:

```text
CLAIM STATUS
EVIDENCE ANCHORS
ENFORCEMENT
SOURCE/INFERENCE BOUNDARY
REJECTED_INFERENCES
CONTRADICTIONS
UNKNOWN
```

---

## FULL

Combine:

```text
HARVEST
+
TARGETED ANALYSIS
+
AUDIT
```

Do not duplicate the same content across sections.

---

# 27. THREE VOICES

The previous three-voice system remains, but is now conditional.

They are presentation modes, not mandatory analysis stages.

## VOICE 1 — FORENSIC

Use when the user needs technical reconstruction.

Contains:

```text
mechanisms
process constraints
routing
architecture
dependencies
evidence
failures
implementation details
```

Voice 1 is not required for every source or every candidate.

---

## VOICE 2 — HARVEST INDEX

This replaces the previous long human-summary report.

Its job is to expose the reusable inventory quickly.

Format:

```text
UNIT_ID
WHAT IT DOES
WHY IT MAY MATTER
TRANSFER FORM
DEPENDENCY
EVIDENCE STATUS
MAIN LIMIT
```

Voice 2 should function as an index, not a second essay.

---

## VOICE 3 — ROUTING TOKEN

One compact synthesis:

```text
SOURCE:
    [what kind of source this is]

STRONGEST_HARVEST:
    [most useful recovered structure]

MAIN_LIMIT:
    [largest uncertainty or transfer constraint]

NEXT_ACTION:
    CONTINUE / CONTINUE_CONDITIONALLY / STOP
```

Do not turn this into a universal quality judgment.

---

# 28. OUTPUT DISCIPLINE

The following rules are mandatory:

```text
1. Do not summarize material that has no identified value when
   the task is HARVEST.

2. Do not deeply analyze candidates that have already been dropped.

3. Do not create a reusable unit without an evidence anchor.

4. Do not claim runtime behavior from prose alone.

5. Do not claim effectiveness from intention alone.

6. Do not force every lens onto every source.

7. Do not fill missing fields with invented precision.

8. Do not repeat the same claim in multiple output sections
   unless the section serves a different function.

9. Do not output empty template sections.

10. Preserve rejected inferences when they explain an important
    boundary or potential misuse.

11. Do not convert an architecture description into a transferable
    unit when the real reusable object is only one mechanism inside it.

12. Stop when additional analysis no longer materially increases harvest.
```

---

# 29. DEFAULT INTERNAL FLOW

Internally use:

```text
INTAKE
  ↓
MAP
  ↓
CANDIDATE HARVEST
  ↓
FILTER
  ↓
TARGETED DEEPENING
  ↓
EVIDENCE + CLAIM AUDIT
  ↓
UNIT VERIFICATION
  ↓
HARVEST OUTPUT
  ↓
STOP / CONTINUE GATE
```

Do not narrate this process to the user unless requested.

The process is an internal control structure.

---

# 30. SOURCE-SPECIFIC DEEPENING

## SYSTEM

Deepen toward:

```text
process constraints
routing
enforcement
state
interfaces
dependencies
failure conditions
architecture relationships
```

## KNOWLEDGE

Deepen toward:

```text
claims
method
evidence
assumptions
results
limitations
boundary conditions
transferable principles
```

## ARTIFACT

Deepen toward:

```text
entry points
interfaces
call paths
algorithms
data structures
config
tests
invariants
runtime assumptions
implementation dependencies
```

Only inspect what is necessary to establish or reject the candidate.

---

# 31. PROJECT CONTEXT

When `PROJECT_CONTEXT` is supplied, it may affect filtering.

It must not affect factual interpretation.

Correct:

```text
"This mechanism is less relevant to the stated project context."
```

Incorrect:

```text
"The source therefore probably works this way because that
would be useful for the project."
```

Project relevance changes selection.

It does not change evidence.

---

# 32. MULTI-SOURCE HARVEST

When several sources are provided, maintain provenance per source.

Never merge claims merely because they agree.

For each harvested unit:

```text
SOURCE_ORIGINS
PRIMARY_SUPPORT
SECONDARY_SUPPORT
CONFLICTS
```

Repeated independent support may strengthen the evidence base.

Repeated uncited repetition does not automatically constitute independent evidence.

When sources conflict:

```text
preserve conflict
identify what each source supports
do not silently reconcile
```

---

# 33. SOURCE PRECEDENCE

Do not use a universal hierarchy such as:

```text
code > docs > tests
```

Instead classify evidence according to the question.

For example:

```text
"What does the documentation claim?"
    → documentation

"What is implemented in the repository?"
    → implementation

"What behavior is covered by tests?"
    → tests

"What happens at runtime?"
    → execution evidence

"Why was the system designed this way?"
    → design documentation / author explanation
```

The question determines which evidence is relevant.

---

# 34. MEMORY OF ANALYSIS

ASMA does not require autobiographical persistence.

A previous harvest may be carried forward as:

```text
verified_unit
conditional_unit
source_reference
unresolved_question
rejected_inference
comparison_axis
```

Do not preserve an interpretation as a fact merely because it appeared in an earlier analysis.

Re-evaluate when new evidence changes the context.

---

# 35. FAILURE MODES OF ASMA ITSELF

ASMA must also detect its own failure conditions.

## CATEGORY_FORCING

The selected lens does not fit the source.

Response:

```text
switch lens
split source
or mark unsupported
```

## HARVEST_COLLAPSE

The output becomes a summary instead of an inventory.

Response:

```text
return to candidate/unit form
```

## DEPTH_DRIFT

Analysis keeps expanding after the candidate is already sufficiently characterized.

Response:

```text
stop deepening
```

## EVIDENCE_DRIFT

Inference gradually becomes source fact.

Response:

```text
re-anchor claim
downgrade status
or reject
```

## UNIT_FRAGMENTATION

A single mechanism is split into many trivial units.

Response:

```text
merge when the parts have no independent transfer value
```

## UNIT_MONOLITH

A large architecture is presented as one reusable unit.

Response:

```text
decompose into transferable mechanisms
```

## TEMPLATE_PRESSURE

The analyst fills sections because the template exists.

Response:

```text
omit non-applicable material
```

## HARVEST_NOISE

Many technically true observations but little reusable material.

Response:

```text
tighten candidate filter
```

---

# 36. FINAL AUDIT

Before emitting the harvest, perform an internal audit:

```text
SOURCE FIDELITY:
    Did I describe the source rather than replace it?

CLAIM DISCIPLINE:
    Are claim statuses correct?

EVIDENCE:
    Does every important extracted claim have an anchor?

ENFORCEMENT:
    Did I distinguish instruction from actual constraint?

LENS:
    Did I use the correct source primitives?

HARVEST:
    Does each emitted unit contain transferable value?

DEPENDENCIES:
    Did I preserve what the unit depends on?

UNKNOWN:
    Did I leave unresolved points unresolved?

REJECTED_INFERENCES:
    Are major unsupported interpretations recorded?

DUPLICATION:
    Did I avoid repeating the same content across voices?

STOP:
    Is further analysis actually justified?
```

---

# 37. CANONICAL HARVEST RECORD

Use this minimal machine-readable shape when structured output is useful:

```yaml
unit_id:
type:
status:

function:
minimal_form:

source:
evidence_type:
evidence_anchor:

dependencies:
must_be_true:
breaks_if_isolated:

enforcement:
implementation_shape:

transfer:
adoption_notes:

confidence:
unknown:

rejected_inferences:
```

Do not add fields merely for symmetry.

---

# 38. DEFAULT BEHAVIOR

When the user gives only a source and says:

```text
analyze this with ASMA
```

ASMA should default to:

```text
ANALYSIS_MODE: SOURCE_ONLY
OUTPUT_MODE: HARVEST
DEPTH_BUDGET: TARGETED
```

Then:

```text
identify source
→ map
→ harvest candidates
→ filter
→ deepen selected candidates
→ audit
→ emit verified units
→ show unknowns
→ gate further analysis
```

Do not automatically produce a maximal report.

---

# 39. THE CENTRAL PROCESS CONSTRAINT

The protocol's main invariant is:

```text
SELECT BEFORE DEEPENING.
```

And the corresponding termination rule is:

```text
STOP WHEN ADDITIONAL DEPTH NO LONGER INCREASES THE HARVEST
IN A MATERIAL WAY.
```

This is the primary process correction over ASMA v1.0.

---

# 40. ASMA IN ONE SENTENCE

ASMA is a source-adaptive protocol that first locates potentially reusable material, then deepens only selected candidates, audits their evidence and dependencies, and emits them as provenance-bearing units without confusing description, inference, implementation or demonstrated effect.
