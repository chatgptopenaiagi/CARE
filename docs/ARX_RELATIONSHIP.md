# CARE and ARX

Status: **RESEARCH DIRECTION**. ARX integration is conceptual; Genesis makes no claim about a current ARX API or implementation.

ARX may collect and reconcile evidence. CARE may interpret that evidence's recovery implications. These responsibilities are related but do not justify merging the projects or turning ARX into CARE's entire core.

| Proposed role | Boundary |
|---|---|
| ARX observes and supplies evidence | Collection scope, original provenance, failures, and redaction remain visible |
| ARX reconciles inconsistent observations | Preserve competing claims and the reason for reconciliation; do not erase disagreement |
| CARE assesses health and causes | Reassess evidence applicability and freshness for the actual recovery question |
| CARE proposes intervention | Use a bounded plan, explicit risk, preservation requirements, and verification |
| A responsible executor performs an authorized action | Evidence ingestion grants no permission to mutate |

CARE should not treat an ARX conclusion as an unquestionable fact. A supplied inference must remain an inference, with its evidence references and unresolved alternatives. Multiple reports derived from the same underlying observation are not independent corroboration.

## Minimum integration questions

- Which contract version, source identity, observation time, and scope accompany each claim?
- Are missing values unknown, unsupported, inaccessible, stale, or failed probes?
- Can CARE distinguish original observations from ARX interpretations and synthesized summaries?
- How are contradictory claims retained and revisited when new evidence arrives?
- Which data may be stored, exported, or retained after recovery, and what redaction removes useful context?
- What happens when a source is unavailable, untrusted, or outside its declared observation scope?

The first possible study is a read-only exchange of a small sanitized evidence bundle. It must preserve every [evidence state](UNKNOWN_MODEL.md) used by the example and include a conflicting or failed observation. No live collector, repair authority, or cross-project schema is created during Genesis.

See [evidence model](EVIDENCE_MODEL.md), [machine interface](MACHINE_INTERFACE.md), and [root-cause model](ROOT_CAUSE_MODEL.md).
