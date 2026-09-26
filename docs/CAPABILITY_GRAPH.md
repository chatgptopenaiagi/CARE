# Capability graph

**Status: CONCEPT.** CARE does not currently detect or execute these capabilities.

## Purpose

A capability describes an outcome available to a particular actor and task in a particular context. “GPU inference for this model under this memory budget” is more useful than a machine-wide “GPU healthy” flag.

Capability assessment consumes [dependency](DEPENDENCY_GRAPH.md), [health](HEALTH_MODEL.md), and [evidence](EVIDENCE_MODEL.md) claims. It does not replace their provenance or uncertainty.

## Proposed capability description

A future description should identify the intended operation, subject and execution context, mandatory requirements, permitted alternatives, optional features, applicable constraints, evidence, and verification method. Requirements may form conjunctions or explicit alternatives; the logic must be visible to humans and machine consumers.

For a conceptual GPU-inference capability, relevant requirements might include a suitable device, compatible driver and runtime, compatible model/provider, sufficient memory for the specified workload, and valid permissions. These requirements are illustrative; Genesis establishes no GPU compatibility matrix or support claim.

## Assessment semantics

| Result concept | Meaning |
| --- | --- |
| Available | Every required condition for the declared capability is adequately established in the stated context. |
| Unavailable | Evidence establishes a blocking mandatory condition across every permitted path. |
| Unknown | Evidence is insufficient to establish availability or a definitive blocker. |
| Not applicable | The capability is outside the relevant task or subject under evidenced applicability criteria. |

The exact serialized vocabulary remains open. An available assessment should state whether it rests on prerequisite checks or a successful end-to-end test; these provide different strength of evidence. An unsupported assessment mechanism leaves the capability unknown unless other evidence establishes its status.

Unknown inputs must remain visible even when a known blocker establishes unavailability. If one alternative fails while another remains unknown, the overall capability is not proven unavailable. An available alternative does not imply that the failed alternative is repaired.

## Authority and scope

Technical capability is not permission to act. Permission is itself context-bound; a successful check in one session does not grant another agent or pack the right to execute the operation. Revalidate relevant requirements and authorization before consequential execution.

A denied operation can mean “not authorized for this actor” without meaning that the underlying software is broken. Reports must separate technical support, observed health, authorization, and current task requirements.

## Effects on recovery

A failed prerequisite identifies a bounded capability limitation, not a broken machine. Repair plans should name the intended capability to restore, the contributing causes they address, and the unrelated capabilities whose healthy state must be preserved.

A fallback can restore the user's workflow through a different capability path while leaving the original path unavailable. Report this as a workaround unless the original confirmed cause was corrected and verified. See [verification](VERIFICATION_CONTRACT.md) and [human explanation](HUMAN_EXPLANATION.md).
