Only the **World** and **Perception** layers are authoritative.
The **Narrative** layer has no authority over world state.

---

## World layer

### Responsibility

The World layer defines and enforces:

- entities (players, NPCs, objects),
- locations and spatial relations,
- rules, constraints, and state transitions,
- objective facts about the world.

It answers the question:

> *What exists, and what is allowed to happen?*

### Characteristics

- Single source of truth
- Deterministic state transitions
- No interpretation or narration
- No assumptions about who perceives the world

### Reference implementation

In the current reference stack, this layer is implemented using **TinyMUX**:
- object database
- rooms, exits, things
- state flags and attributes
- hard constraints

---

## Perception layer

### Responsibility

The Perception layer governs:

- visibility and audibility,
- awareness and detectability,
- partial or asymmetric access to world state.

It answers the question:

> *What does a given entity have access to right now?*

### Key concept: perception as data

Perception is treated as explicit, enforceable data — not as narrative convention.

In the reference implementation, this is achieved through:
- Rx (receive) levels — what an entity can perceive
- Tx (transmit) levels — where an entity is perceivable
- reality levels and visibility rules

Perception does not alter world state.
It constrains access to it.

### Failure mode by design

If an entity cannot perceive another entity, the latter does not exist
from the former’s point of view.

There is no “hidden but known” state.

---

## Narrative layer

### Responsibility

The Narrative layer is responsible for:

- describing experience,
- interpreting events,
- contextualizing partial knowledge,
- producing meaning.

It answers the question:

> *What does this experience feel like, and what might it mean?*

### Non-authoritative by design

The Narrative layer:
- cannot create or alter world facts,
- cannot override perception rules,
- cannot assume omniscience.

It operates exclusively on *derived inputs*.

### Implementations

Narrative can be provided by:
- human moderators or game masters,
- AI systems (e.g. LLMs),
- scripted or hybrid approaches.

Noesis treats all narrative sources as interchangeable observers.

---

## Data flow

### Event-driven model

All meaningful interaction follows this flow:
Action
↓
World validation and state update
↓
Perception filtering
↓
Narrative interpretation
↓
Presentation to participant

### Important constraint

Narrative systems receive only:
- world events that occurred,
- perception-filtered snapshots,
- no hidden or global state.

This prevents narrative hallucination from corrupting world truth.

---

## Interfaces and boundaries

### World ↔ Perception

- Tight coupling
- Perception rules are evaluated directly against world state
- No external system may bypass this boundary

### Perception ↔ Narrative

- Read-only
- Snapshot-based
- Explicitly scoped to the observing entity

### Narrative ↔ World

- No direct write access
- Any proposed action must re-enter through the World layer

---

## Integration layer (out of scope)

Transport, orchestration, and user interfaces
(e.g. Discord, web clients, external services)
are considered *integration concerns*.

They must not:
- encode world rules,
- infer hidden state,
- bypass perception constraints.

---

## Architectural invariants

The following statements must always remain true:

- World truth is centralized and authoritative
- Perception is explicit and enforceable
- Narrative is derived, never primary
- No participant has full knowledge by default
- Ignorance is a valid and supported state

If any of these are violated, the architecture has failed.

---

## Design intent

Noesis is not designed to simulate a complete world.
It is designed to simulate **incomplete access to a complete world**.

This asymmetry is intentional.

---

## Summary

Noesis is an engine where:
- the world exists independently,
- perception fragments experience,
- meaning emerges without omniscience.

Architecture exists to protect this separation.
