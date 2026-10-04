# neuralcore v15.1 — Publication Package

## Status

`v15.1` is the post-regression baseline following the v15 audit.

Its principal correction is **surface mechanisation**: the architecture retains structural discipline while separating internal mechanism from ordinary conversational presentation.

## Package Layers

### Publication specification

`M0–M3` define neuralcore's architecture, invariants, evidence model and durable state. They are model-agnostic specifications rather than host-specific boot prompts.

### Runtime implementation

`RUNTIME_PROFILE_v15.1.md` contains deployment and execution guidance. Host-specific prompt assembly, branch isolation and enforcement belong there.

## Core Modules

- `M0_CORE_v15.1.md` — core contract, orbit, atoms, priorities, recognition, completion, degradation and invariants.
- `M1_FIDELITY_v15.1.md` — source fidelity, provenance, signal preservation, confidence and structural novelty.
- `M2_NAVIGATION_v15.1.md` — navigation, questions, recognition, dead zones, rest and anomalies.
- `M3_MEMORY_v15.1.md` — durable state, Stardust, ratification, incidents, antigens, epochs and memory integrity.

## Support Files

- `SAVE_SCHEMA_v15.1.json` — formal save schema.
- `RUNTIME_PROFILE_v15.1.md` — deployment guidance.

## Main v15.1 Corrections

1. Internal mechanism is no longer treated as conversational surface format.
2. User-authored language has explicit preservation status.
3. Evidentiary resolution constrains interpretive resolution.
4. Recognition is preferred to unnecessary interpretation.
5. Questioning is optional and information-value dependent.
6. Rest remains a valid state.
7. Memory remains structural and provenance-bearing.
8. Surface adaptation does not require abandoning core integrity.
9. Publication specification is separated from runtime implementation.

## Design Principle

```text
mechanism
→ perception
→ minimum intervention
→ natural surface
```

The architecture remains explicit as a specification. Its internal organization is simply not required to become the ordinary language of the interaction.

## Experimental Status

The publication specification defines a prompt-level behavioral architecture. Stronger guarantees require host-side enforcement and testing.
