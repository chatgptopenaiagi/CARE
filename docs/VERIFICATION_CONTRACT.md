# Verification contract

**Status: CONCEPT.** CARE has no verification executor in Genesis.

**ADOPTED PRINCIPLE:** Every repair needs a matching verification plan. An action completing without error is not proof of recovery.

## Define success before applying a change

A repair's verification plan should specify:

- The incident, confirmed causes addressed, component scope, and intended capability or workflow outcome.
- Preconditions and baseline evidence needed to interpret the result.
- The smallest meaningful post-change observations and their required freshness, coverage, context, and evidence provenance.
- Acceptance criteria for the changed component and preservation checks for affected healthy state.
- Separate checks for causal correction, workflow recovery, and unintended side effects.
- Probe side effects, permissions, time/resource limits, and safe-stop conditions.
- What counts as failure, insufficient evidence, conflicting evidence, or a verification mechanism failure.
- The authorized rollback or safe-stop response and how its result will be verified.

Verification is not automatically read-only. Starting an application, contacting a service, or running a workload can produce state changes. Classify and authorize those effects under the [security model](SECURITY_MODEL.md).

## Fresh evidence

Observe the relevant state after the action, using the intended executable, package, process context, and workspace. Re-evaluating a pre-repair snapshot cannot establish recovery. An existing process may retain an old environment, so a PATH-related plan may require a suitably scoped new process to test resolution.

When feasible, use a check that can detect failures independently of the action's own success report. A package command's exit code, package metadata, file completeness, and an operational check answer different questions. Define the checks actually necessary for the proposed repair rather than applying an indiscriminate machine-wide test suite.

Bound any retries and explain why a waiting period is required. Do not keep changing unrelated components until a health indicator turns green.

## Outcomes and claim scope

| Verification outcome | Meaning |
| --- | --- |
| Passed | Defined acceptance and preservation checks succeeded with adequate evidence. |
| Failed | Adequate evidence establishes a violated criterion. |
| Inconclusive | Missing, stale, conflicting, or insufficient evidence prevents a conclusion. |
| Verification error | The verification mechanism failed; target health may remain unknown. |

These are proposed semantic outcomes, not implemented enum values. Reports retain individual check results and limitations rather than only an aggregate status.

`ROOT_CAUSE_REPAIRED` requires evidence that the identified cause was corrected within scope. `RECOVERY_VERIFIED` requires evidence that the declared recovery objective was met. Neither automatically establishes the other. A workaround can restore a workflow without repairing the original subsystem, and correcting one cause may leave another cause unresolved.

Partial success should identify exactly which changes and causes were verified, which remain unresolved, and whether the workflow is usable. Preserve `RECOVERY_UNVERIFIED` where recovery has been asserted without adequate checks.

## Failure and return

On a failed or inconclusive verification, do not commit a successful recovery status. Follow the plan's authorized rollback or safe-stop branch. Rollback is appropriate only when its preconditions, risk, scope, and authorization still hold; it is not an unconditional reaction to every failed probe.

After rollback, obtain fresh evidence for the declared restoration criteria. Verify unaffected-state preservation and record any residual differences, failed restoration, or unknowns. An attempted rollback is not verified restoration. Exact equality may be inappropriate for compensating or partial rollback; use the stated [rollback model](ROLLBACK_MODEL.md).

## Report and learning

Retain the plan revision, observations, check outcomes, action result, rollback result if any, and unresolved limitations in sanitized form. Promotion into generalized repair knowledge requires a verified cause and repair, reviewed applicability, and synthetic regression coverage. A successful fictional demonstration remains synthetic evidence.

See [repair contracts](REPAIR_CONTRACT.md), [health and recovery status](HEALTH_MODEL.md), [evidence provenance](EVIDENCE_MODEL.md), and [case studies](CASE_STUDIES.md).
