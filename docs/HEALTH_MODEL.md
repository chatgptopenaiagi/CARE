# Health and preservation model

**Status: CONCEPT.** CARE has no live health evaluator in Genesis.

**ADOPTED PRINCIPLE:** Identify what is healthy, preserve it, and change only the smallest surface justified by a confirmed problem.

## Scoped health

Health is an assessment against explicit criteria for a component, capability, task, and observation period. It is not an eternal property of an installation or a single machine-wide Boolean.

Proposed assessment concepts include healthy, degraded, failed, unknown, and not applicable. Every assessment must reference its criteria, evidence, scope, and limitations. These health conclusions are separate from the [knowledge states](UNKNOWN_MODEL.md) of the supporting observations.

For example, a runtime can be present and able to execute a smoke test while being incompatible with a specific application's required architecture. A failed version probe may leave runtime health unknown. It does not, by itself, establish that the runtime is broken.

## Distinct questions

| Question | Example meaning |
| --- | --- |
| Presence | Is the inspected component there? |
| Compatibility | Does it satisfy the relevant interface, version, architecture, or environment constraints? |
| Health | Does it meet defined operational checks in this context? |
| Requirement | Is it needed for this task or an active dependency path? |
| Knowledge | How well can the previous answers be supported? |

Do not recommend installing or repairing a component solely because an inventory mentions it. A missing optional runtime may have no effect on the current task.

## Preservation obligations

A proposed repair needs an affected-component inventory with three explicit groups: components justified for change, components whose healthy state must be preserved, and unresolved components requiring further observation. The groups are scoped to the repair; they are not a claim of complete machine knowledge.

For every protected component, state the preservation assertion and how it will be checked. Examples include unchanged configuration bytes, continued runtime operation, retained project data, or unchanged executable selection. Checks should match the plausible impact of the proposed change rather than collect the entire machine.

Shared dependencies require particular care. Replacing one shared runtime or restarting one service can affect several otherwise healthy applications. Recalculate the affected scope and authorization before proceeding. A small command is not necessarily a small change.

Backups do not turn an unjustified rebuild into an acceptable repair. If the available repair mechanism cannot preserve required healthy state within authorized bounds, propose a narrower alternative or stop safely.

## Recovery status has several dimensions

`WORKAROUND_AVAILABLE` describes an alternate way to continue. `ROOT_CAUSE_IDENTIFIED` describes diagnostic knowledge. `ROOT_CAUSE_REPAIRED` describes correction of a confirmed cause within stated scope. `PARTIALLY_REPAIRED` records that only some intended corrections succeeded. `RECOVERY_UNVERIFIED` and `RECOVERY_VERIFIED` describe the verification status of a defined recovery objective.

These are not one exclusive status ladder. A workaround can restore a verified workflow while the original subsystem remains broken. A repair can correct one cause while another still blocks the application. A claimed repair remains unverified until fresh checks establish its result.

Reports should therefore state the affected causes, repair coverage, workflow outcome, and verification status separately. See [repair planning](REPAIR_CONTRACT.md), [verification](VERIFICATION_CONTRACT.md), and [human explanation](HUMAN_EXPLANATION.md).
