# CARE and HAAEP

Status: **ADOPTED PRINCIPLE** for project independence; **RESEARCH DIRECTION** for integration. No integration exists.

HAAEP is the broader Human-AI Adaptive Engineering Platform direction. CARE focuses on diagnosis, compatibility, recovery, verification, and state preservation. CARE does not take ownership of HAAEP's desktop, general agent orchestration, runtime management, or wider engineering vision.

## Complementary roles

```text
HAAEP human and AI planes
  -> may consume CARE recovery intelligence
  -> may independently consume CWRE's specialized Windows/Codex results
```

This diagram represents optional future dependencies. It is not a current deployment or a requirement to route every CWRE interaction through CARE.

| Concern | Proposed responsibility |
|---|---|
| Explain a recovery problem in a broader engineering mission | HAAEP, retaining CARE's uncertainty and scope |
| Classify recovery evidence and propose bounded repair plans | CARE, within its supported capabilities |
| Perform a supported Windows/Codex operation | CWRE through its own contract, where deliberately integrated |
| Present comparison, choice, approval, and progress | HAAEP Human Plane or another CARE consumer |
| Authorize consequential changes | Human under applicable policy; not an inferred grant from a UI click elsewhere |
| Enforce execution preconditions | The responsible execution boundary, including all applicable project restrictions |

HAAEP should consume CARE's [machine interface](MACHINE_INTERFACE.md) and render the same semantics described by its [human explanation layer](HUMAN_EXPLANATION.md). It should not reproduce hidden diagnosis or repair logic in a playground.

## Come-and-Go recovery

CARE shares the idea that returning can preserve knowledge. Its recovery-specific form is selective: after comparing baseline S0 and degraded S1, an authorized repair may produce S2 that retains useful changes and reverses only a proven harmful change. S2 need not equal S0.

The [state model](STATE_MODEL.md), [delta model](DELTA_MODEL.md), and [rollback model](ROLLBACK_MODEL.md) define the limits of that direction. A snapshot is not automatically a restorable backup. A difference is not automatically a cause. A return request is not authorization to erase everything created since a baseline.

## Future recovery playground

A suitable human surface could expose system health, dependency graphs, incident evidence, state timelines, proposed repairs, before/after comparison, simulation, rollback availability, and verification results. It must show unknowns, the targeted scope, protected healthy components, authorization requirements, and irreversible effects.

The playground would control underlying contracts; it would not invent diagnoses or promise universal undo. CARE Genesis provides no GUI, executable API, simulation engine, or HAAEP plug-in. A first integration study must prove semantic fidelity on a small sanitized example before live recovery is considered.

See [security](SECURITY_MODEL.md), [CWRE](CWRE_RELATIONSHIP.md), and [roadmap](ROADMAP_2_YEARS.md).
