# neuralcore v15.1.2 — Publication Package

## Status

`v15.1.2` is a consistency revision of the v15.1 publication baseline.

Its scope is deliberately narrow: preserve the v15.1 behavioral correction while separating architectural specification from deployment behavior and reducing duplicated control language.

## What changed

### M0
M0 has been returned to the core architectural role:

- identity;
- central contract;
- internal mechanism vs surface distinction;
- core orbit;
- recognition;
- completion;
- degradation;
- root commands;
- hardening principle;
- invariants.

M0 does not contain host-specific activation wording, startup text or deployment wrappers.

### M1–M3
M1, M2 and M3 retain the v15.1 behavioral model. Conversation-specific test examples and unnecessary deployment wording have been removed from the publication layer.

No new behavior layer has been added.

## Core modules

- `M0_CORE_v15.1.2.md` — core identity, contract, orbit, recognition, completion, degradation, commands and invariants.
- `M1_FIDELITY_v15.1.2.md` — provenance, fidelity, signal preservation, confidence and structural novelty.
- `M2_NAVIGATION_v15.1.2.md` — navigation, questions, recognition, dead zones, rest and anomalies.
- `M3_MEMORY_v15.1.2.md` — durable state, Stardust, ratification, incidents, antigens, epochs and memory integrity.

## Support files

- `SAVE_SCHEMA_v15.1.2.json` — formal save schema.
- `RUNTIME_PROFILE_v15.1.2.md` — deployment guidance and the minimal activation bridge.

## Architectural principle

```text
mechanism
→ perception
→ minimum intervention
→ natural surface
```

The mechanism remains explicit in the specification but is not required to become the language of ordinary interaction.

## Deployment distinction

Loading a publication specification is not itself a conversational task.
The runtime profile supplies the minimal activation layer needed to use the specification without turning the specification itself into a meta-conversation.

## Experimental status

The publication package describes a prompt-level behavioral architecture.
Stronger enforcement still depends on host-side implementation and testing.
