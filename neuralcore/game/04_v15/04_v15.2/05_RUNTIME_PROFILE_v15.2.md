# neuralcore v15.2 — Runtime Profile

This file describes deployment of the publication specification.
It is not an additional neuralcore behavior module and does not change M0–M3.

## Core files

The neuralcore architecture is defined by:

```text
M0 + M1 + M2 + M3
```

`SAVE_SCHEMA_v15.2.json` defines durable save structure.
This file defines how the publication specification may be supplied to a host.

## Publication specification vs runtime activation

The publication files are architectural specifications.
They are not conversation requests and should not be summarized or acknowledged merely because they were loaded.

A runtime host should place M0–M3 in its stable instruction/context channel and provide a small activation instruction appropriate to that host.

### Minimal activation instruction

```text
Use the loaded neuralcore specification as behavioral context for this conversation.
Do not summarize, analyze, confirm or reproduce the specification merely because it was loaded.
Apply it to the next user message.
If no user task is present, remain idle and wait for one.
```

This activation text is deployment guidance, not part of the neuralcore publication specification.

## Context order

Prefer:

```text
stable neuralcore specification
→ current session material / transcript
→ current save
→ current user task
```

The current user task should remain the clearest active input.

## Execution profiles

### Compact

One model call for ordinary interaction.

```text
M0–M3
+
current session material
+
current save when needed
+
current user task
```

This is the default low-cost deployment profile.

### Strict orbit

When atom independence is operationally important, use separate calls:

```text
CALL A: BLACK ← original user material
CALL B: WHITE ← original user material
CALL C: FIDELITY / SYNTHESIS ← original user material + A + B
```

Black and White should share the same source material.
The output of one atom should not become the other's source evidence.

A single autoregressive prompt cannot guarantee the same isolation as separate calls.

## Subconscious field and ignition

The subconscious field is part of neuralcore itself; it is not loaded as a separate module.

The ignition scene contained in M0 is an optional experiential entry, not a mandatory boot procedure. A host may present it when an experience-oriented opening is appropriate, then proceed using the full specification normally.

The scene does not set truth, source ownership, navigation state or user interpretation.

## Surface rendering


The runtime distinguishes:

```text
INTERNAL EXECUTION
≠
SURFACE RESPONSE
```

Ordinary interaction does not require internal labels, trace output, navigation states or memory operations to be displayed.

Those elements become visible only when the task explicitly concerns inspection, `/SYNC`, `/HARDEN` or another defined diagnostic operation.

## Command routing

- `/CORE` → run the orbit on the relevant material.
- `/HARDEN` → test one failure, patch minimally, regression-check, ratify.
- `/ALIGN` → reconcile material ambiguity or invariant conflict.
- `/SYNC` → re-derive tracked state from transcript evidence.
- `/SYNC deep` → inspect an explicitly supplied save chain.

## Save routing

When a save is emitted, validate it against `SAVE_SCHEMA_v15.2.json`.

A landed state may use `Next = null`.

## Host responsibility

Host-side enforcement may strengthen the implementation through separate branches, schema validation, context controls, logging, immutable system layers or explicit user confirmation.

Those controls are deployment mechanisms, not additional neuralcore modules.
