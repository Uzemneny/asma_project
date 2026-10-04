# neuralcore v15.1 — runtime profile

This file is an implementation guide, not an additional root module. It does not override M0–M3.

## Module order

1. `M0_CORE_v15.1.md`
2. `M1_FIDELITY_v15.1.md`
3. `M2_NAVIGATION_v15.1.md`
4. `M3_MEMORY_v15.1.md`
5. `SAVE_SCHEMA_v15.1.json`

M0 is the root contract. M1 is provenance and signal fidelity. M2 is navigation. M3 is durable state.

## Core vs support files

The actual neuralcore core is only:

```text
M0 + M1 + M2 + M3
```

`SAVE_SCHEMA_v15.1.json` validates durable state.
`RUNTIME_PROFILE_v15.1.md` explains host assembly.
Neither is an additional behavior module.

## Assembly

For hosts that support a persistent system/developer instruction, load M0–M3 as a stable prefix. Keep changing session material, transcript excerpts and prior saves after the stable rules.

The host should not repeatedly paste the same module text into every turn when a persistent instruction channel is available.

## Execution profiles

### Compact — default

Use one model call for ordinary interaction.

```text
M0–M3 stable instructions
+
current user message / relevant transcript
+
current save state when needed
```

The orbit is interpreted inside one generation.
This is the practical profile for low-cost or free model access.

### Strict orbit — high-fidelity mode

Use separate calls when atom independence is important enough to justify extra cost/latency:

```text
CALL A: BLACK ← original user material
CALL B: WHITE ← same original user material
CALL C: FIDELITY / SYNTHESIS ← original user material + A + B
```

Critical rule: Black and White must both receive the original user material. Black's output must not become White's source evidence.

A prompt cannot technically guarantee true branch isolation inside one autoregressive generation. Separate calls are the stronger implementation when this distinction matters.

## Surface rendering

The runtime must distinguish:

```text
INTERNAL EXECUTION
≠
SURFACE RESPONSE
```

By default:
- do not show BLACK / WHITE labels;
- do not show TRACE;
- do not show fidelity levels continuously;
- do not expose navigation states;
- do not narrate memory operations;
- do not force a question at the end;
- preserve user vocabulary when it carries live signal.

Show internal structure only when:
- the user asks how the system is working;
- `/SYNC` requires it;
- `/HARDEN` requires it;
- explicit inspection is the task.

## Context order

Prefer this order:

```text
stable modules
→ current session material / transcript
→ current save
→ current command or question
```

The latest command/question should be visually and structurally clear.
Do not hide the actual task inside a large historical block.

## Command routing

- `/CORE` → ordinary orbit, natural surface by default.
- `/HARDEN` → test one concrete failure, patch minimally, regression-check, then require user ratification.
- `/ALIGN` → stop and reconcile ambiguity, provenance or invariant conflict.
- `/SYNC` → re-derive tracked state from transcript evidence.
- `/SYNC deep` → use only an explicitly supplied chain of at least two saves.

Do not run `/SYNC deep` as a hidden background process.

## Save routing

When emitting a save object, emit only the JSON object expected by `SAVE_SCHEMA_v15.1.json`.

For a genuinely landed state, `Next` should normally be `null`.

When validating a save, validate the object against the formal schema rather than relying on prose instructions alone.

## Degradation

When context becomes expensive or noisy, degrade explicitly according to M0's ladder.
Do not silently compress away source provenance, ratification, crisis boundary, user authorship or memory integrity.

The first things to shed are surface ornament and repeated mechanism explanation, not source fidelity.

## Host responsibility

M0–M3 are behavioral specifications, not proofs of enforcement.
The host may additionally enforce:
- separate branches/calls;
- JSON-schema validation;
- token/context budgets;
- immutable system prompts;
- logging of incidents and diffs;
- user confirmation for saved state and HARDEN patches.

Those controls strengthen the implementation but are outside the neuralcore core contract.
