# Delta model

Status: **CONCEPT**. Genesis specifies comparison semantics only.

## Compare only what can be compared

A delta compares two scoped [snapshots](SNAPSHOT_MODEL.md) using declared criteria. Establish component identity, observation scope, fact meaning, units, relevant context and schema compatibility before calculating a difference. Path equality is not always component identity, and a moved path alone does not prove replacement.

Comparability may hold for only part of a snapshot. Report comparable portions and explicit gaps rather than rejecting everything or manufacturing a complete comparison.

## Change vocabulary

| Comparison result | Required interpretation |
| --- | --- |
| Appeared or disappeared | Comparable evidence establishes known absence/presence across captures. |
| Version or location changed | The same scoped component is identified and both values are observed. |
| Became unreachable | Comparable reachability tests differ; disappearance or destruction is not established. |
| Health changed | Relevant health criteria and context are comparable; evidence supports each judgment. |
| Knowledge-only change | Observability or knowledge changed without evidence of an environment transition. |
| Incomparable | Identity, scope, meaning or context cannot support the requested comparison. |
| Insufficient evidence | Comparison could be meaningful, but required observations are missing or uncertain. |
| No observed difference | Comparable observed facts match; unobserved state is not thereby unchanged. |

For example, `UNKNOWN` followed by `KNOWN_PRESENT` does not prove that an installation occurred. `KNOWN_PRESENT` followed by `PROBE_FAILED` does not prove removal. Conflicting evidence must remain visible rather than collapsing into a single apparent transition.

## Meaning of a difference

Expected and unexpected changes depend on a declared plan or expectation. Improvement and regression depend on the intended task, objective and [verification](VERIFICATION_CONTRACT.md) criteria. A newer package can be irrelevant to the task or introduce a regression.

**ADOPTED PRINCIPLE — a delta is evidence of difference, not proof of cause.** Record candidate explanations separately with supporting and contradicting evidence. An update followed by failure is a reason to investigate the [migration](MIGRATION_MODEL.md), not sufficient evidence to attribute every failure to that update.

## Output direction

A future delta result should reference both snapshots, comparison criteria, identity mappings, supported changes, uncertainty, preservation-relevant unchanged observations and limitations. It should identify expected changes from a repair plan separately from unplanned differences.

The delta evaluator observes and classifies. It does not mutate components, select a rollback automatically or convert a regression judgment into authorization. A [repair plan](REPAIR_CONTRACT.md) must independently justify its target and evaluate dependencies, preservation constraints and recovery options.

## Selective reconciliation

Comparison may support keeping a beneficial configuration change while restoring a defective package. This produces a new state, not necessarily an exact historical replay. Preserve the comparison and what was learned after return. Unknown neighboring components require investigation or an explicit plan boundary; their uncertainty is not permission to reset them.

Future fixtures should cover partial comparability, identity changes, transient reachability failures, knowledge-only changes and unrelated concurrent modifications. No comparator is implemented in Genesis.

Related: [state](STATE_MODEL.md), [root causes](ROOT_CAUSE_MODEL.md), [rollback](ROLLBACK_MODEL.md), [machine interface](MACHINE_INTERFACE.md).
