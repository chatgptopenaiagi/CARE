# Unknown model

**Status: CONCEPT.** These are proposed knowledge semantics, not an implemented enumeration or schema.

**ADOPTED PRINCIPLE:** Missing evidence must never silently become healthy, broken, true, or false.

## Several dimensions, not one overloaded flag

A file may be known present in a stale snapshot. A current observation may conflict with another observation. A probe can be unsupported while the target itself works normally. These conditions need separate dimensions.

| Dimension | Concepts | Interpretation |
| --- | --- | --- |
| Presence claim | `KNOWN_PRESENT`, `KNOWN_ABSENT`, `UNKNOWN` | What the bounded evidence establishes about presence. |
| Acquisition | Observed, `UNKNOWN`, `UNOBSERVABLE`, `PROBE_FAILED`, `UNSUPPORTED` | Whether evidence was acquired, why it was not, or whether this collector can assess it. |
| Freshness | Fresh for purpose, `STALE`, `UNKNOWN` | Whether observation timing is adequate for the current decision. |
| Consistency | Consistent, `CONFLICTING`, `UNKNOWN` | Whether relevant sources agree after scope differences are considered. |
| Applicability | Applicable, `NOT_APPLICABLE`, `UNKNOWN` | Whether a question or requirement applies to this subject and task. |

“Observed,” “fresh for purpose,” “consistent,” and “applicable” are descriptive concepts, not settled serialized token names. The uppercase states requested by the mission are preserved without forcing unlike dimensions into a contradictory flat list.

## State meanings

- `KNOWN_PRESENT`: a scoped observation establishes presence; it does not establish compatibility or health.
- `KNOWN_ABSENT`: an applicable, sufficiently complete observation establishes absence within declared coverage.
- `UNKNOWN`: available evidence cannot support a conclusion. Record the missing evidence where possible.
- `UNOBSERVABLE`: the fact cannot be observed in the current context, for example because required access is unavailable. This does not authorize privilege escalation.
- `PROBE_FAILED`: an attempted observation failed. Preserve the failure category without leaking secrets.
- `UNSUPPORTED`: the selected collector or assessment cannot evaluate this question. Do not equate this with the target being unsupported by its vendor.
- `STALE`: previously acquired evidence is too old or invalidated for this decision. Retain its historical value.
- `CONFLICTING`: relevant evidence supports incompatible conclusions that have not been reconciled.
- `NOT_APPLICABLE`: evidence establishes that this question does not apply. It is not a synonym for “not checked.”

## Combining knowledge

Use the underlying records and scope before deriving an aggregate. Two apparently conflicting executable versions may describe two installations. That is a discovery to model, not necessarily contradictory evidence.

Do not silently reduce unknown prerequisites to success or failure. A capability may be proven unavailable because one mandatory prerequisite fails while other prerequisites remain unknown. Report both the blocker and the unresolved requirements; do not label all dependencies broken.

When a consequential action depends on an unknown precondition, obtain suitable evidence or stop that action safely. A missing observation does not justify a repair, a package reinstall, or weakening security to make inspection easier.

## Knowledge changes versus system changes

`UNKNOWN` becoming `KNOWN_PRESENT` may mean that a new observation succeeded. It does not prove that the component was installed between snapshots. Similarly, a previously fresh observation becoming stale is a change in knowledge quality, not proof of machine degradation.

Reports must preserve this distinction through the [state model](STATE_MODEL.md), [delta model](DELTA_MODEL.md), [health model](HEALTH_MODEL.md), and [machine interface](MACHINE_INTERFACE.md).
