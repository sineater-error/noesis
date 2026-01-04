# Noesis — Perception Model

This document defines how perception works in Noesis.
It formalizes how entities gain access to information about events
without altering world truth.

Perception is a constraint system, not a narrative device.

---

## Definition

**Perception** in Noesis is:

> A rule-based limitation on access to world events and state,
> evaluated per entity and per event.

Perception determines *what information may exist* for a given entity.
It does not determine what exists in the world.

---

## Core distinction

Noesis enforces a strict separation between:

- **Event** — what happened in the world
- **Perception** — whether an entity can access information about it
- **Information** — what the entity can know
- **Narrative** — how that knowledge is interpreted

Perception sits between events and information.

---

## Perception as data

Perception is explicit and enforceable.

It is never:
- inferred from narrative,
- assumed by convention,
- implied by co-location.

If perception allows access, information may be produced.
If perception denies access, information does not exist for that entity.

---

## Perception scope

Perception is evaluated:

- per entity,
- per event,
- per target object,
- at a specific point in world time.

There is no global perception state.

---

## Reference model (Rx / Tx)

The reference implementation uses two complementary sets of perception levels:

### Rx — Receive levels
Rx defines **what an entity is capable of perceiving**.

It answers the question:
> *Which layers of reality can this entity observe?*

Rx levels are cumulative.
An entity may perceive multiple layers simultaneously.

---

### Tx — Transmit levels
Tx defines **where an entity is perceptible to others**.

It answers the question:
> *In which layers of reality does this entity appear?*

Tx levels may be exclusive or cumulative,
depending on the nature of the entity’s state.

---

## Visibility rule

An entity **A** may perceive entity **B** if and only if:

Rx(A) ∧ Tx(B) ≠ 0

If the condition fails, **B does not exist** for **A**.

This affects:
- presence,
- interaction,
- emitted events,
- descriptions,
- command matching.

There is no intermediate “hidden but known” state.

---

## Self-perception invariant

An entity always perceives itself.

Self-perception is guaranteed even if:

Rx(self) ∧ Tx(self) = 0

This prevents accidental self-erasure.

---

## Perception and events

Perception does not affect whether an event occurs.

Instead, it determines:
- whether information derived from the event is available,
- which aspects of the event are accessible,
- how much context is exposed.

A single event may result in:
- full information,
- partial information,
- no information,
depending on perception.

---

## Perception and information

Information is produced only when perception allows it.

Information:
- is local to the perceiving entity,
- may omit cause, scope, or outcome,
- may differ between observers.

Absence of information is meaningful.
It must not be auto-filled.

---

## Perception and descriptions

Entities may expose different descriptions
depending on perception level.

Descriptions are:
- projections of the same entity,
- not separate entities,
- not separate events.

Multiple descriptions may be visible simultaneously
if perception allows access to multiple layers.

---

## Perception changes

Changes to perception capabilities
(e.g. gaining enhanced sight, becoming hidden)
are world events.

Perception does not change implicitly.
It is always the result of an event.

---

## Perception and narration

Narrative systems operate only on:
- information permitted by perception,
- contextual absence of information.

Narration may speculate,
but speculation has no authority.

Narrative systems must not:
- infer hidden state,
- reconstruct unseen events,
- assume shared perception.

---

## Failure modes (by design)

The following outcomes are intentional and valid:

- an entity acting on incomplete information,
- an entity being observed without awareness,
- an entity unaware of an event that affected it indirectly,
- contradictory narratives based on different perceptions.

These are not errors.
They are features.

---

## Architectural invariants

The following must always remain true:

- Perception never alters world truth
- Information never precedes perception
- No entity perceives more than it is allowed
- Ignorance is a supported state
- Co-location does not imply shared perception

Violation of any invariant constitutes a design failure.

---

## Summary

Perception in Noesis is a formal constraint system.

It exists to ensure that:
- the world remains objective,
- experience remains fragmented,
- knowledge remains partial.

A world is not defined by what is seen,
but by what remains unseen.

