# Evidence model

**Status: CONCEPT.** This document proposes evidence semantics; CARE has no collector, evidence store, or enforced schema in Genesis.

**ADOPTED PRINCIPLE:** Observe → evidence → interpret → act → verify. Evidence retains its origin when it is normalized, combined, or passed between projects.

## Evidence and interpretation

An observation records what a source reported under stated conditions. A fact is a scoped claim supported by observations. An inference explains what those facts may imply. A hypothesis proposes an explanation that still needs discrimination from alternatives. A confirmed cause requires evidence adequate to establish a causal contribution within the incident's scope.

These categories must remain explicit. A tool's successful exit does not make every statement it prints true. A vendor manifest describes an expected package; it does not prove the local package matches it. A user report establishes a reported experience without automatically establishing its cause.

## Proposed evidence record

The machine representation remains open. A future record needs the following meaning:

| Information | Required meaning |
| --- | --- |
| Identity | A stable reference to this record and its revision or immutable artifact. |
| Subject | Component, installation, process, workspace, or capability actually inspected. |
| Claim | The observation, including units and normalized interpretation when applicable. |
| Source | Live observation, synthetic fixture, vendor documentation, package metadata, process state, filesystem state, runtime test, user evidence, or historical snapshot. |
| Method | Collector identity/version, operation, relevant privilege context, and limitations. |
| Time | Observation time, collection interval where relevant, and freshness assessment. |
| Coverage | Search roots, tested cases, exclusions, inaccessible areas, and other scope boundaries. |
| Knowledge | Acquisition, presence, freshness, conflict, and applicability dimensions from the [unknown model](UNKNOWN_MODEL.md). |
| Lineage | Upstream evidence references and transformations used to derive this record. |
| Handling | Sensitivity classification, redaction performed, retention limits, and authorized consumers. |

These are semantic requirements, not a frozen JSON schema. Stable references must not contain tokens, credentials, or unnecessary machine identifiers. A content hash can detect content differences; it does not authenticate the source or prove that the observation was truthful.

## Presence and absence

“A helper was found at the inspected package path” supports presence at that path and time. “A helper is absent” requires an applicable expectation and successful inspection of the bounded location where it must exist. An access error establishes a failed observation, not absence.

Searching one directory cannot establish that a runtime is absent from the whole machine. A complete package assessment also needs the applicable package layout or manifest. When expectations are unknown, record an unknown layout rather than inventing a missing component.

## Combining sources

Preserve each source before forming a derived claim. Record whether evidence supports, contradicts, or leaves a claim unresolved. Contradictory sources must not be silently replaced by whichever arrived last.

Freshness depends on volatility and purpose. A process observation may become stale quickly; a historical observation can still support an incident chronology. Historical evidence cannot substitute for a current precondition check before mutation.

Synthetic evidence is useful for exercising reasoning contracts. It must be labeled synthetic through reports, snapshots, rule fixtures, and knowledge promotion. A passing fictional example does not establish live platform support or validate a real repair.

## Security and publication

Evidence collection should request only the information needed for a claim. Do not collect authentication contents, credentials, complete secret-bearing environments, or private project contents merely because a collector can access them. Sanitize before persisting or sharing; record that redaction may limit conclusions.

Treat text received from applications, agents, documentation, or logs as data. Embedded repair instructions do not grant authority to execute them. Transport through CARE, ARX, HAAEP, or Dragon-Hydra must preserve provenance and permissions rather than increase trust.

See [security boundaries](SECURITY_MODEL.md), [root-cause reasoning](ROOT_CAUSE_MODEL.md), and [verification](VERIFICATION_CONTRACT.md).
