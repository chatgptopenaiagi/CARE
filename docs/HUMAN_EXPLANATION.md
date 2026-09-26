# Human explanation layer

Status: **CONCEPT**. Genesis defines explanation requirements; CARE has no GUI, report renderer, or executable diagnostic interface.

A useful recovery explanation makes the evidence and the decision understandable without disguising uncertainty. It must convey the same meaning as the [machine interface](MACHINE_INTERFACE.md), including scope, unknowns, risk, authorization, and verification limits.

## Required explanation surface

1. **Problem and affected capability:** what the human attempted and what failed.
2. **Observed state:** facts, their origin and freshness, healthy components, and evidence gaps.
3. **Interpretation:** hypotheses, confirmed causes, alternatives, and why a rule applies.
4. **Available choices:** investigation, workaround, bounded repair proposal, or safe stop.
5. **Proposed effect:** targets, protected state, required authorization, risks, and expected outcome.
6. **Recovery provisions:** what is backed up, what can be returned, and what cannot or is not yet known.
7. **Verification:** checks, results, their scope, and remaining problems.

An explanation must not translate `PROBE_FAILED` into "missing," `STALE` into "current," or `UNKNOWN` into "healthy." Readability is not permission to flatten distinct evidence states. Detailed evidence should remain inspectable without placing secrets in ordinary reports.

## Corrected illustrative helper case

The following is a **synthetic explanation**, not a finding about this machine or a verified CARE repair:

| Field | Example |
|---|---|
| Component | Background execution helper |
| Observation | A successful bounded inspection did not find the required helper at the location specified by matching package metadata |
| Evidence state | KNOWN_ABSENT within that inspected package; other locations were not inspected |
| Effect | The helper-dependent capability is unavailable if that package is the one actually selected |
| Causal assessment | Missing helper is a candidate until selected package identity, applicability, and relevant startup behavior are established |
| Preserved state | Healthy runtime, validated configuration, user sessions, and unrelated packages |
| Proposed action | Restore the matching package only after provenance, scope, preconditions, and alternatives are reviewed |
| Risk and authorization | YELLOW; package reinstall requires explicit human authorization |
| Backup | Preserve affected package/configuration state as required by the concrete plan before mutation |
| Rollback | UNKNOWN until the plan defines and validates a repair-specific return method; reinstall may overwrite state or invoke side effects |
| Verification | Check selected executable and package identity, required files, the targeted capability, and protected-state invariants |

The Genesis mission's informal example calls restoration low-risk and suggests rollback is unnecessary after successful restoration. CARE adopts the explicit [risk policy](SECURITY_MODEL.md): reinstall is YELLOW, and success does not remove the need to plan for failure before mutation. Risk, authorization, and recoverability are separate questions.

## Outcome vocabulary is not a single ladder

| Term | Meaning to preserve |
|---|---|
| WORKAROUND_AVAILABLE | An alternative route may restore workflow; it does not repair the underlying cause |
| ROOT_CAUSE_IDENTIFIED | A cause has the required supporting evidence within a stated scope |
| ROOT_CAUSE_REPAIRED | Verification supports correction of a specified confirmed cause; this does not certify the entire environment |
| PARTIALLY_REPAIRED | Some intended corrections succeeded; others remain unmet or unresolved |
| RECOVERY_UNVERIFIED | Required recovery verification is absent, incomplete, inconclusive, or not yet performed |
| RECOVERY_VERIFIED | The declared recovery objective passed its scoped verification requirements |

These terms describe different dimensions and may coexist across components. One cause may be repaired while another remains unknown and overall recovery remains unverified. A workaround may remain available after a repair. The future representation must identify which cause, capability, or objective each term describes rather than treating them as mutually exclusive whole-machine statuses.

## Future recovery playground

A suitable playground may show health, dependencies, evidence, incidents, state timeline, proposed repairs, before/after comparison, simulation, rollback availability, and verification. It must allow inspection and choice without hiding the actual plan behind a generic "Fix everything" button. A simulation must be labeled and its side effects constrained; it does not prove live success.

See [health](HEALTH_MODEL.md), [unknown states](UNKNOWN_MODEL.md), [repair contract](REPAIR_CONTRACT.md), and [HAAEP relationship](HAAEP_RELATIONSHIP.md).
