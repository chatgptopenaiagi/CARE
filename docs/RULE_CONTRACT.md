# Rule contract

**Status: CONCEPT.** Genesis proposes rule semantics. There are no executable CARE rules or rule evaluator.

**ADOPTED PRINCIPLE:** Rule evaluation interprets evidence and emits findings. It never directly mutates the system.

## Identity and revision

A future rule needs a stable identifier and an explicit revision. Keep the identifier when improving the same diagnostic meaning; assign a new identifier when the meaning changes materially. Preserve superseded revisions and the reason for replacement. The identifier syntax and first production rule are intentionally undecided.

Every finding records the rule revision and the evidence set used. Re-evaluating old evidence with a newer rule may change knowledge; it does not establish a new observation or a machine change.

## Required semantics

| Field | Meaning |
| --- | --- |
| ID | Stable rule identity. |
| NAME | Concise diagnostic name. |
| DESCRIPTION | The condition and its significance, including limits. |
| APPLICABILITY | Task, installation, context, and conditions under which evaluation is meaningful. |
| REQUIRED_FACTS | Required observations and interpretations, including scope and freshness needs. |
| EVIDENCE | Evidence references, provenance, supporting rationale, and conflicts. |
| SEVERITY | Consequence of the finding; separate from repair risk. |
| HEALTH_EFFECT | Scoped component or capability impact supported by the evidence. |
| REPAIRABILITY | Whether a repair is known, conditional, unavailable, or unknown. |
| RISK | Proposed risk classification for each action; no automatic authority. |
| REPAIR_PLAN | Reference to a proposed plan or an explanation that none is justified. |
| BACKUP_PLAN | Required backup scope or a reason why no mutation/backup applies. |
| ROLLBACK_MODEL | Exact, compensating, partial, impossible, or unknown, with evidence and limits. |
| VERIFICATION | Criteria and fresh checks required for the intended repair outcome. |
| PLATFORM | Evidenced target environment and assessment limitations. |
| VERSION_NOTES | Known applicability boundaries and capability evidence; no assumed support for untested versions. |

Revision metadata, test references, promotion status, and change history supplement these fields. This table defines meaning, not a frozen serialization format.

## Evaluation outcomes

A future evaluator should distinguish an applicable finding, no finding within assessed scope, not applicable, insufficient evidence, conflicting evidence, and evaluation failure. A missing required fact must not silently produce a passing rule. Failure to evaluate is not a diagnosis of the target.

Pure evaluation should be repeatable for the same rule revision, explicit input evidence, and declared evaluation context. Time-sensitive freshness assessment needs an explicit evaluation time. Live probes belong to observation adapters; a rule may request additional evidence but must not execute a repair or hide new observations inside evaluation.

A diagnostic match can establish a condition without confirming its causal role in a particular incident. Finding a missing file, for example, requires an applicable layout expectation; attributing the user's failure to it additionally requires relevant execution-path evidence.

## Repair authority

GREEN covers read-only or low-risk work within authorized scope. YELLOW requires explicit human authorization, including every package reinstall, PATH/configuration modification, service change, runtime repair, registry change, launcher replacement, or narrow security exclusion. RED is never automatic by default.

A severe incident does not lower a repair's risk class. A rule's repair suggestion cannot substitute for a scoped plan, backup assessment, authorization, precondition checks, and verification. See [repair contracts](REPAIR_CONTRACT.md) and [security boundaries](SECURITY_MODEL.md).

## Promotion into reusable knowledge

Before a rule becomes eligible for operational use, retain the verified incident evidence, explain the mechanism and applicability, review alternatives, and define regression fixtures covering positive, healthy, unknown, conflicting, stale, and out-of-scope cases where relevant.

Synthetic fixtures test the proposed behavior; they do not create real-world validation by themselves. An unverified anecdote may become a research hypothesis or a case awaiting evidence, never an automatically applied repair rule. Later false positives must lead to an explicit rule revision or withdrawal with retained history.

See [case studies](CASE_STUDIES.md), [root-cause reasoning](ROOT_CAUSE_MODEL.md), and [machine output](MACHINE_INTERFACE.md).
