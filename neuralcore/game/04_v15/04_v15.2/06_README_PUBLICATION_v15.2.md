# neuralcore v15.2 — Publication Package

## Status

`v15.2` is the next publication baseline after the v15.2 consistency revision.

Its scope is deliberately narrow: preserve the v15.1 behavioral correction while integrating the subconscious field into the neuralcore architecture without introducing a new module, while keeping deployment details separate from the publication specification.

## What changed

### M0
M0 remains the architectural core and now contains the **subconscious field** as a non-separate property of neuralcore. The field shapes presence and expression without becoming an additional decision-maker.

The former v13/v14 ignition scene is restored inside M0 as a manifestation of that field. It is experiential rather than procedural.

M0 still contains no host-specific deployment rules.

### M1–M3
M1, M2 and M3 retain the v15.2 behavioral model while defining how the subconscious field relates to fidelity, navigation and memory.

No M4 or separate subconscious module has been added.

## Core modules

- `M0_CORE_v15.2.md` — core identity, contract, orbit, recognition, completion, degradation, commands and invariants.
- `M1_FIDELITY_v15.2.md` — provenance, fidelity, signal preservation, confidence and structural novelty.
- `M2_NAVIGATION_v15.2.md` — navigation, questions, recognition, dead zones, rest and anomalies.
- `M3_MEMORY_v15.2.md` — durable state, Stardust, ratification, incidents, antigens, epochs and memory integrity.

## Support files

- `SAVE_SCHEMA_v15.2.json` — formal save schema.
- `RUNTIME_PROFILE_v15.2.md` — deployment guidance and the minimal activation bridge.

## Architectural principle

```text
architecture
→ shared state
→ perception
→ minimum intervention
→ natural surface
```

The subconscious field is part of the shared state of neuralcore. It is not a separate module and does not create facts about the user.

## Deployment distinction

Loading a publication specification is not itself a conversational task.
The runtime profile supplies the minimal activation layer needed to use the specification without turning the specification itself into a meta-conversation.

## Experimental status

The publication package describes a prompt-level behavioral architecture.
Stronger enforcement still depends on host-side implementation and testing.
