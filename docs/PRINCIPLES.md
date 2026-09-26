# CARE principles

Status: **ADOPTED PRINCIPLE**. These are engineering obligations, not implemented
runtime enforcement. Genesis establishes the architecture in documentation.

## Central Recovery Law

**PROBLEM → OBSERVATION → EVIDENCE → CLASSIFICATION → ROOT CAUSE → REPAIR PLAN →
BACKUP → MINIMAL CHANGE → VERIFICATION → RECOVERED STATE → GENERALIZED KNOWLEDGE**

Failed verification branches to **ROLLBACK / SAFE STOP**, with verification of
any attempted rollback and an honest report. Unknown cause or authority prevents
advancement into a root-cause repair. The sequence is evidence-gated; it does not
force a cause, successful recovery, or generalized rule out of every incident.

## Diagnose First Law

Recognizing a symptom is a reason to investigate, not permission to apply a
remembered repair. Distinguish observed fact, inference, hypothesis, possible
cause, confirmed cause, unknown, and unsupported. Classify what the evidence
supports and the next observation that could confirm or disprove a candidate.
Several independent causes can coexist.

## Healthy State Preservation Law

Identify healthy components explicitly, with supporting checks and their scope.
If A, B, and E are healthy, C is broken, and D is unknown, the plan should protect
A/B/E, repair C if justified, and investigate D. Do not normalize, reinstall, or
delete healthy components for cosmetic consistency.

Health is task- and context-specific, not a permanent property of a machine.
Preservation constraints should become verification obligations after a repair.

## Workaround and root-repair distinction

| Claim | What it establishes |
| --- | --- |
| `WORKAROUND_AVAILABLE` | An alternative may restore the workflow within stated limits; the cause may remain |
| `ROOT_CAUSE_IDENTIFIED` | Evidence establishes a cause within a stated incident and scope |
| `ROOT_CAUSE_REPAIRED` | Verification establishes removal of that cause within the stated scope |
| `PARTIALLY_REPAIRED` | Some defined causes or effects were resolved; others remain |
| `RECOVERY_UNVERIFIED` | Available checks do not establish the claimed recovery |
| `RECOVERY_VERIFIED` | Named recovery criteria passed in the stated context and observation window |

These are proposed semantic claims, not one mutually exclusive implementation
enum or a mandatory linear progression. A verified fallback can restore a
workflow while the root cause remains. An execution can finish while verification
fails. Whole-system health cannot be inferred from one verified repair.

## Evidence and Unknown Laws

**OBSERVE → EVIDENCE → INTERPRET → ACT → VERIFY.** Preserve live observations,
fixtures, documentation, metadata, process/filesystem state, runtime tests,
user reports, and historical snapshots as distinguishable sources.

Absence, lack of access, probe failure, unsupported interpretation, stale evidence,
conflict, and non-applicability are different conditions. None silently becomes
healthy, broken, true, or false. Preserve a previous observation with its age;
do not silently promote it to current truth.

## Minimal Change and Verification Laws

Bind each proposed change to evidence, a diagnosed cause, the task objective,
targets, authority, backup, expected effects, and verification. Check the
smallest supported scope. Define success before mutation and verify it after.
A process exit, file presence, newer version, or disappeared symptom is not by
itself evidence of complete recovery.

Back up important affected state before modifying it. A snapshot of facts is not
necessarily a recoverable copy. If backup or verification prerequisites fail,
stop or replan; do not conceal them behind a success message.

## Repair-Specific Return Law

Classify rollback as **EXACT**, **COMPENSATING**, **PARTIAL**, **IMPOSSIBLE**, or
**UNKNOWN** for the particular targets and context. Verify the achieved return.
Do not overwrite another actor's unrelated changes or assume a compensating
action recreates the original state.

**Return with knowledge** means preserving sanitized observations, failed checks,
decisions, and useful changes when justified. It is not blind rollback, universal
undo, or permission to retain secrets indefinitely.

## Growth through verified incidents

**REAL INCIDENT → EVIDENCE → MODEL → RULE → TEST → REPAIR CAPABILITY.**

The knowledge-promotion path requires a verified cause and repair, reviewed
applicability, a stable rule identity/revision, and synthetic regression cases.
Anecdotes can become investigation candidates; they cannot directly become
automatic repair rules. Synthetic results establish their scenario, not live
cross-platform support.

## Shared meaning and bounded authority

Human-readable explanations and machine interfaces must express the same
evidence, uncertainty, scope, risk, outcomes, and recovery limits. Neither a
UI button, agent recommendation, rule match, nor package manifest grants repair
authority. Risk and permission remain separate.

CARE learns from independent CWRE and may cooperate with HAAEP, ARX, and
Dragon-Hydra through future contracts. It must not become a giant repair hammer
or absorb those projects simply because they share concepts.

Related: [architecture](ARCHITECTURE.md), [evidence](EVIDENCE_MODEL.md),
[unknown](UNKNOWN_MODEL.md), [health](HEALTH_MODEL.md),
[repair](REPAIR_CONTRACT.md), [security](SECURITY_MODEL.md), and
[decisions](DECISIONS.md).
