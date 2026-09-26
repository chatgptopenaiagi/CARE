# CARE and CWRE

Status: **ADOPTED PRINCIPLE** for project independence; **RESEARCH DIRECTION** for future contract integration. No CARE/CWRE adapter exists.

CWRE remains the concrete Windows/Codex recovery implementation and originating case study. CARE extracts recovery lessons into proposed cross-domain contracts. Genesis does not rename, move, rewrite, merge, or duplicate CWRE. CARE's generalized vocabulary does not retroactively change CWRE's contracts.

## Responsibility boundary

| Concern | CARE direction | CWRE responsibility |
|---|---|---|
| Recovery reasoning | General evidence, health, cause, plan, verification, and return concepts | Concrete supported Windows/Codex behavior |
| Rules | Proposed reusable rule contract and promotion discipline | Own rule identities, applicability, implementation, and tests |
| Observation | Proposed adapter and evidence boundaries | Own collectors and supported environment probes |
| Repair | Proposed transaction and authorization semantics | Own implemented repair scope, refusals, backups, and verification |
| Case studies | Sanitized lessons with preserved provenance | Detailed implementation source and original incident evidence |

Neither project is required to adopt the other's internal data structures. Future interoperability should negotiate a versioned public surface and retain the original result's scope and limitations. A CARE recommendation must not bypass a CWRE precondition or authorize an operation CWRE does not support.

## Lessons reviewed during Genesis

CARE read CWRE's architecture documentation on 2026-09-26. This establishes the source of these lessons; it does not certify current runtime behavior or reproduce historical incidents.

- Separate observation, pure rule evaluation, repair planning, mutation, and verification.
- Preserve unknown evidence instead of manufacturing a positive or negative result.
- Distinguish command resolution, package completeness, helper identity, security context, and daemon health.
- Keep workarounds distinct from repaired causes and keep verified outcomes scoped.
- Preserve healthy state and require a repair-specific recovery plan.
- Prefer capability and context evidence over a brittle assumption based only on version.
- Test shared semantics across consumers: CWRE documents divergence between two implementations when required evidence was unknown.
- Distinguish matching bytes from trusted provenance, and a successful local build from a supported distribution.

These lessons motivate CARE's [evidence model](EVIDENCE_MODEL.md), [repair contract](REPAIR_CONTRACT.md), and [verification contract](VERIFICATION_CONTRACT.md). CARE has not copied code, machine snapshots, configuration, or authentication/session data.

## Policy differences remain explicit

CARE's [security model](SECURITY_MODEL.md) classifies package reinstall as **YELLOW**, requiring explicit human authorization. An older project's risk label or historical charter cannot silently override that policy. A future adapter must preserve the source label, explain any mapping, and enforce every applicable restriction; it must not downgrade a protected action because another system calls it low-risk.

Future integration research should begin with a small sanitized read-only result and its semantic mapping. A separate, explicitly scoped development block would be required for mutation integration. Installation of an adapter would grant no repair authority.

See [CASE-001](CASE_STUDIES.md), [architecture](ARCHITECTURE.md), and [HAAEP relationship](HAAEP_RELATIONSHIP.md).
