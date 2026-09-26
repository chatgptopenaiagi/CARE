# Rollback model

Status: **CONCEPT**. Genesis defines recovery classifications and obligations; no restoration mechanism is implemented.

## Declare what return means

| Model | Meaning and limitation |
| --- | --- |
| EXACT | The declared target state can be restored within a precisely bounded scope and verified. This does not promise identical whole-machine state or reversal of external effects. |
| COMPENSATING | A separate action counteracts selected effects while leaving a different state. State the remaining differences. |
| PARTIAL | Only specified portions can be restored. Identify what remains changed, lost or uncertain. |
| IMPOSSIBLE | The relevant effects cannot be reversed by the available recovery method. Explain the consequence before mutation. |
| UNKNOWN | Restoration capability or adequacy has not been established. Do not advertise undo. |

Each classification is a claim requiring evidence and conditions. Availability of backup files alone does not establish EXACT recovery. If a component changed independently after backup, restoring old bytes may overwrite legitimate work rather than safely reverse the repair.

## Repair-specific rollback plan

A plan should specify trigger conditions, target identities, scope, preservation conditions, required backups, backup consistency, restoration method, permissions, prerequisites, dependencies, order, expected effects, verification criteria and safe-stop conditions.

Evaluate permissions for rollback as part of the repair plan. An authorized apply action does not automatically grant broader restore powers. Existing exact authorization can cover the declared rollback; no repetitive approval is needed while that grant and all relevant conditions remain valid.

Check target identity, concurrent changes, backup availability and restoration safety again immediately before rollback. Do not overwrite unexpected modifications. A plan must explain whether it can coordinate concurrent actors; where it cannot, state the limitation and stop safely when necessary.

## Verification and failure handling

Rollback has its own verification phase. Verify restored content or supported equivalent behavior, required permissions, relevant dependencies and protected healthy components. A copy operation succeeding does not prove usable service, configuration or task capability.

Report the restoration outcome independently from the original repair result. A failed repair followed by verified restoration is not a successful repair. A successful component restore may still leave the original symptom unresolved.

When restoration fails, becomes unsafe or cannot be observed, preserve available evidence and backups, stop further automatic mutation, and report the exact last known actions, remaining uncertainty and bounded recovery options. Do not continue through an unbounded sequence of speculative repairs.

## Return with knowledge

**ADOPTED PRINCIPLE — restore selected state without erasing the investigation.** Retain original observations, causal hypotheses, disproven explanations, failed plans and both verification results. Knowledge retained after return must remain sanitized and correctly qualified; failed experiments do not become verified repair rules.

`S0 → S1 → S2` can represent a useful recovery even when `S2` differs from `S0`. Healthy unrelated changes may remain. Explain those differences through the [state](STATE_MODEL.md) and [delta](DELTA_MODEL.md) models rather than claiming an exact rollback.

## Future proof obligations

Synthetic recovery tests should cover usable versus corrupt backups, independently changed targets, partial restoration, lost verification access, compensating effects and restore failure. Live destructive testing is forbidden by project policy. These tests are future requirements, not existing capabilities.

Related: [repair](REPAIR_CONTRACT.md), [verification](VERIFICATION_CONTRACT.md), [snapshot](SNAPSHOT_MODEL.md), [security](SECURITY_MODEL.md).
