# Repair contract

Status: **CONCEPT**. Genesis defines semantic obligations for future repair planning and execution. It contains no executable repair actions or permission enforcement.

## Separate diagnosis, proposal and authority

A rule finding is not a command. A proposed action is not authorization. Permission is not evidence that an action is correct. A repair must be justified by scoped evidence and causal reasoning, and must satisfy a separately checked authority boundary.

Do not mutate a system because its symptom resembles a known incident. If cause remains uncertain, propose further observation or a separately justified, explicitly described diagnostic experiment. Do not label that experiment a confirmed root-cause repair.

## Plan inputs and required content

A future repair plan should contain:

- Stable plan identity, revision, purpose, target capability and incident/rule references.
- Supporting and contradicting evidence, causal claims, uncertainty and applicability.
- Exact target components, intended changes, exclusions and healthy-state preservation conditions.
- Relevant dependency impact, execution context, required permissions and concurrency constraints.
- Risk class with reasons and unresolved risks, including data and security effects.
- Ordered, bounded actions; preconditions; stopping conditions; timeout/retry policy; and expected effects.
- Snapshot requirements and a separate backup plan covering consistency, restricted storage, integrity and restoration readiness.
- Verification criteria for the changed component, task capability and affected preservation conditions.
- Repair-specific [rollback model](ROLLBACK_MODEL.md), rollback triggers, restore verification and safe-stop procedure.
- A human explanation of expected benefits, possible losses, unknowns and irreversible effects.

Dependencies can determine repair order. For example, confirm that the intended package is complete before switching executable resolution to it. Do not encode a universal order without the incident's evidence.

## Risk and authorization

| Class | Contract obligation |
| --- | --- |
| GREEN | Read-only or demonstrably low-risk work such as diagnostics and package verification. Scope and sanitization still apply; the label does not authorize arbitrary writes. |
| YELLOW | Explicit human authorization is required for the specific plan and scope. Includes PATH/configuration changes, package reinstall, service changes, launcher replacement, runtime repair, registry changes and narrow security exclusions. |
| RED | Never automatic by default. Destructive or broad security-weakening operations are outside ordinary repair execution and need a separately designed control regime; a broad approval cannot make them ordinary repairs. |

Package reinstall is YELLOW in CARE even when a case study used a different local risk classification. A missing helper does not establish that reinstall has no risk or that backup and rollback analysis are unnecessary.

An existing explicit grant may satisfy authorization when it still covers the exact plan, scope, risk and context. Do not demand duplicate approvals. Changed targets, consequential plan changes, expired/revoked grants or invalid preconditions require reassessment. Unknown risk cannot be silently classified GREEN. See the [security model](SECURITY_MODEL.md).

## Transaction lifecycle

The normal conceptual path is `PRECHECK → SNAPSHOT → BACKUP → APPLY → VERIFY → COMMIT_RECOVERY → REPORT`.

1. **PRECHECK:** Validate evidence freshness, target identity, plan applicability, permissions, preservation conditions, dependencies, concurrency and recovery readiness. Stop if a required condition fails.
2. **SNAPSHOT:** Capture the scoped before-state and limitations without secrets. A snapshot alone is not a restore mechanism.
3. **BACKUP:** Preserve the state required by this repair and verify backup usability. If no backup is applicable, document why; never skip it silently. If required preservation cannot be achieved, stop before mutation.
4. **APPLY:** Perform only the approved bounded actions. Record attempted effects and resulting observations without secrets. Detect changed preconditions between steps; stop instead of widening scope.
5. **VERIFY:** Evaluate the predetermined success and preservation criteria using fresh evidence. An exit code or disappearance of the initial symptom alone is insufficient.
6. **COMMIT_RECOVERY:** Record an accepted, verified recovery outcome for the declared scope. This is a recovery lifecycle decision, not a Git commit or permission to delete backups.
7. **REPORT:** Explain changes, verification, remaining failures/unknowns, recovery limits and retained evidence.

If apply or verification fails, use the predeclared `ROLLBACK → VERIFY_ROLLBACK → REPORT` path when rollback remains safe and authorized, or enter `SAFE_STOP → REPORT`. Failed verification does not imply blind rollback is safe. Verify rollback independently and report residual damage or uncertainty.

If verification is unavailable, report `RECOVERY_UNVERIFIED`; do not advance to a successful recovery commit. A crash or lost connection may leave action completion unknown. Re-observe the target before any retry; repeat only actions whose retry semantics are justified.

**ADOPTED PRINCIPLE — transactional intent is not a universal atomicity promise.** External services, concurrent actors and irreversible effects can prevent exact restoration. Do not claim universal ACID transactions for heterogeneous systems.

## Outcome semantics

Keep workaround, cause, repair extent and verification distinguishable. `WORKAROUND_AVAILABLE` does not establish `ROOT_CAUSE_REPAIRED`. A confirmed causal branch may be repaired while another remains unknown, producing `PARTIALLY_REPAIRED`. `RECOVERY_VERIFIED` must identify the capability and scope verified; it does not declare the whole machine healthy.

Preserve original evidence, plan revisions, authorization references, apply observations, verification outcomes and rollback results. Sanitized reports should support both [human explanations](HUMAN_EXPLANATION.md) and [machine consumers](MACHINE_INTERFACE.md) without exposing credentials or private backup contents.

Related: [verification](VERIFICATION_CONTRACT.md), [health](HEALTH_MODEL.md), [root causes](ROOT_CAUSE_MODEL.md), [snapshot](SNAPSHOT_MODEL.md).
