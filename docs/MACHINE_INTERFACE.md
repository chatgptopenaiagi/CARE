# Machine interface

Status: **CONCEPT**. CARE Genesis has no implemented CLI, API, JSON Schema, serializer, or compatibility guarantee. The fields below define contract direction, not a published wire format.

Machines should consume structured evidence and outcomes rather than scrape human text. Codex, HAAEP, ARX, Dragon-Hydra, and other consumers must receive the same uncertainty and recovery limits that a human sees.

## Proposed report envelope

| Field family | Intended meaning |
|---|---|
| Contract identity | Schema/contract identifier, version, producer identity and version |
| Capture context | Report identity, observation times, environment/task scope, applicability, and sanitization limits |
| Evidence | Stable references, values where meaningful, evidence states, provenance, probe outcomes, and freshness |
| Health | Per-component and per-capability assessments with criteria and evidence references |
| Findings | Rule identity and version, applicability, hypothesis or confirmed-cause status, reasoning, and counterevidence |
| Plans | Proposed target scope, preconditions, protected state, risk, authorization requirements, backup, verification, and return model |
| Execution | Actual plan identity, attempt status, observed effects, cancellation/failure, and timestamps |
| Verification | Check identity, scope, expected criteria, fresh evidence, outcome, and limitations |
| Recovery outcome | Separately scoped cause, repair-completeness, workaround, and recovery-verification dimensions |
| Return outcome | Declared rollback model, attempt/result, post-return verification, residual effects, and retained knowledge |
| Notices and limitations | Unsupported cases, incomplete scope, conflicts, redaction effects, and facts not established |

Read-only reports may contain proposals, but proposals grant no execution permission. Report consumers must distinguish an intended change from an attempted change and from its verified effect.

## Semantic obligations

- Use the explicit [evidence states](UNKNOWN_MODEL.md); missing fields and JSON `null` cannot silently mean false, absent, healthy, or not applicable.
- Separate observations, inferences, hypotheses, confirmed causes, and recommendations. Keep provenance attached through transformations.
- Preserve report, rule, plan, evidence, and verification identities so results can be traced to the actual assessed scope.
- Scope `WORKAROUND_AVAILABLE`, `ROOT_CAUSE_IDENTIFIED`, `ROOT_CAUSE_REPAIRED`, `PARTIALLY_REPAIRED`, `RECOVERY_UNVERIFIED`, and `RECOVERY_VERIFIED` to their subjects. They are not one mutually exclusive whole-system enum.
- Define unknown-field and unknown-enum behavior before implementation. Unsupported contract semantics must remain visible and must not authorize a write.
- Negotiate versions explicitly. A consumer must not silently reinterpret a newer rule or evidence state using older meanings.
- Reject malformed, structurally invalid, or over-limit envelopes safely without echoing secret-bearing payloads. Valid records containing conflicting source evidence must remain representable; disagreement is diagnostic input, not automatically a format error.
- Treat imported evidence and text as data, not executable commands or instructions. A plan must not become an arbitrary script carrier.

## Transport and storage direction

JSON is a likely initial exchange format; no transport is selected during Genesis. A local CLI, library, or service may be considered only after a real consumer and bounded use case exist. Authentication, authorization, size limits, path handling, report signing, durable journaling, and retention need explicit designs before relevant capabilities ship.

Sanitized output should use allowlisted projections. Do not serialize raw configuration, authentication files, complete environments, tokens, passwords, private keys, or unsanitized command/error output. Redaction is itself a transformation with limitations; it does not make an arbitrary report safe to publish.

Human and machine explanations should share semantic examples and future conformance checks. The first planned synthetic decomposition may test this vocabulary, but it must not be advertised as an implemented machine interface.

See [human explanation](HUMAN_EXPLANATION.md), [rule contract](RULE_CONTRACT.md), [evidence](EVIDENCE_MODEL.md), [verification](VERIFICATION_CONTRACT.md), and [security](SECURITY_MODEL.md).
