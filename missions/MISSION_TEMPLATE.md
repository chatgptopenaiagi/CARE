# Mission: [one bounded recovery-engineering block]

Status: **DRAFT — this template does not grant action authority**.

## MISSION_ID

[Stable identifier and date.]

## PROJECT_AND_WORKSPACE

[Confirmed repository, root, branch, owner, and affected boundary.]

## OBJECTIVE_AND_STOP_CONDITION

[Concrete human problem or architectural question, success criteria, exclusions,
and exactly when to stop.]

## FILES_TO_READ

[MISSION, PROGRESS, relevant DECISIONS, affected contracts, and narrowly scoped
evidence. Do not collect authentication or unrelated private state.]

## EVIDENCE_AND_DIAGNOSIS

[Symptom; observed facts with provenance/scope/time; inference; hypotheses;
confirmed causes; conflicting or missing evidence. Mark synthetic inputs.]

## HEALTH_AND_PRESERVATION

[Affected, healthy, and unknown components; applicable task requirements;
preservation assertions and plausible shared-dependency impact.]

## AUTHORIZED_CHANGES

[Actual human authorization, plan/scope, risk, limits, and validity. Distinguish
observe, propose, simulate, apply, and return. A finding is not permission.]

## FORBIDDEN_CHANGES

[Protected targets, external projects, state, secrets, and unapproved operations.]

## PLAN_AND_BACKUP

[Smallest justified actions and ordering, preconditions, expected effects,
timeouts, snapshot versus backup requirements, backup protection and readiness,
safe-stop triggers. Use not applicable with a reason for documentation-only work.]

## VERIFICATION_AND_RETURN

[Predetermined fresh checks, causal correction versus workflow recovery,
healthy-state preservation, and independent results. Rollback: EXACT,
COMPENSATING, PARTIAL, IMPOSSIBLE, or UNKNOWN; scope, conditions, authority,
concurrent-change protection, verification of return, and retained learning.]

## TESTS_REQUIRED

[Focused checks appropriate to this block, synthetic cases before live mutation,
expected results, limitations, and criteria for reporting inconclusive evidence.]

## REPORT_FORMAT

[Actual outcome, evidence, changes, tests run, verification scope, workaround
versus repair status, unresolved causes, return outcome, Git/publication status,
and known limitations. Never substitute a planned result for an observed one.]

## NEXT_EXACT_ACTION

[At handoff, update docs/PROGRESS.md with exactly one bounded subsequent action.
Historical mission handoffs do not become competing current task queues.]
