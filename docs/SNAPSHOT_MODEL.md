# Snapshot model

Status: **CONCEPT**. Genesis defines a future observation artifact; it does not collect machine snapshots.

## Purpose and scope

A snapshot records what was observed, where, when and by which method. Possible categories include OS capabilities, runtimes, packages, PATH resolution, services, processes, configuration health, dependencies, hardware, security context, application health, workspace identity and network reachability.

Categories are optional and task-driven. An omitted category is not healthy, absent or irrelevant by default. Collection must preserve explicit unknown, unobservable, probe-failed, unsupported, stale, conflicting and not-applicable states according to the [unknown model](UNKNOWN_MODEL.md).

## Minimum semantic content

- Snapshot identity, contract version and intended diagnostic purpose.
- Environment identity and scope without unnecessary identifying information.
- Collection start/end times, per-observation times where available and clock limitations.
- Evidence provenance, observation method, adapter identity and version where relevant.
- Facts, units, source boundaries and redaction or omission indicators.
- Collection failures, partial coverage, known concurrent changes and freshness limits.
- References to applicable criteria and prior snapshots without implying comparability.

Capture may span time and observe an inconsistent combination of states. A future collector must report this limitation rather than claiming an atomic machine image. Content hashes can detect artifact changes; hashes alone do not establish trustworthy origin or factual correctness.

## Snapshot versus backup

**ADOPTED PRINCIPLE — observation artifacts do not imply restorability.** A sanitized report that says a configuration is valid cannot restore that configuration. A version inventory cannot restore a package, service state or database.

A repair's backup requirements are separate: required bytes or export format, consistency conditions, permissions, storage, integrity, availability, restoration method and retention. A backup may need sensitive data to restore a component; such data belongs in restricted recovery storage, never in a public snapshot or routine log. Diagnostic evidence may reference a sanitized backup identifier and verification outcome without exposing its contents.

If an artifact is intended to serve both purposes, it must independently satisfy the snapshot and backup contracts. Do not infer this from a filename or a successful copy operation.

## Sanitization boundary

Collect the minimum facts needed for the diagnostic question. Do not export credentials, authentication files, tokens, cookies, private keys, connection strings, raw secret-bearing configuration, full environment-variable dumps or raw database records. Prefer presence, validity and scoped capability results over contents.

Paths, usernames, project names, process arguments and network endpoints can also disclose private information. Redact or normalize them as appropriate while preserving stable aliases needed for comparisons. Record that redaction occurred; never substitute redacted values with false absence. Do not assume hashing a secret makes it safe to publish.

A failed sanitization step must prevent export. Retention, access and deletion requirements must be declared by a future collector. Sensitive raw observations must not leak through errors or auxiliary logs.

## Acceptance direction

Future synthetic tests should prove that omitted data remains unknown, redaction does not alter health conclusions, mixed-time captures are identified, provenance survives serialization and unsupported collection does not look healthy. Live collection is outside Genesis.

Related: [state](STATE_MODEL.md), [evidence](EVIDENCE_MODEL.md), [delta](DELTA_MODEL.md), [security](SECURITY_MODEL.md), [repair](REPAIR_CONTRACT.md).
