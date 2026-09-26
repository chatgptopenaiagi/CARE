# Security model

Status: **ADOPTED PRINCIPLE** for project boundaries; runtime enforcement mechanisms are **CONCEPT**. Genesis does not supply a security enforcement layer.

## Authority is separate from diagnosis

Evidence can justify a finding but cannot grant permission. A rule may describe a repair but cannot execute it. A human or agent proposing an action does not enlarge the executor's authority. Imported reports, case studies, model output, adapter metadata and package instructions are data, not trusted commands.

Future execution should distinguish observation, diagnosis, simulation, proposal, workspace mutation, environment mutation, elevated modification, security-sensitive modification and destructive action. A simulation that writes files, calls a service or launches a workload must account for those effects; its name does not make it read-only.

## Risk policy

| Class | Examples | Boundary |
| --- | --- | --- |
| GREEN | Version detection, dependency inspection, sanitized reports, snapshot comparison, package verification | Scope-limited read-only or demonstrated low-risk activity. Report-output writes require a bounded destination and appropriate access. |
| YELLOW | PATH/configuration changes, package reinstall, service or launcher changes, runtime repair, registry changes, narrow security exclusions | Requires explicit human authorization for the proposed consequential change, after its plan and limits are understandable. |
| RED | Global security disabling, authentication-state deletion, destruction of unknown configuration/project data/databases, runtime wipes, certificate removal, broad privilege weakening | Never automatic by default; outside ordinary repair execution. Separate future controls or outright prohibitions must govern any supported exceptional operation. |

Classify actual effects and context, not just command names. High uncertainty, sensitive data or a broader target can increase risk. A high-risk action cannot be split into small actions to disguise its combined effect. Package reinstall is YELLOW by CARE policy.

## Scoped authorization direction

An authorization record should identify the approving human, plan/revision, target scope, allowed actions, risk and irreversible effects, applicable context, validity conditions and revocation status. Its integrity and binding to execution must be enforced by a future trusted execution boundary; GUI text and a caller-supplied Boolean are insufficient.

Reuse an existing explicit grant when it still covers the exact action and conditions. Do not add repetitive approval prompts. Reassess when the plan changes materially, scope expands, preconditions fail or the grant is invalid. A general instruction to repair an environment does not silently authorize every YELLOW or RED operation.

Before applying each consequential action, recheck target identity, permissions, current evidence and declared preconditions. Time between observation and execution matters. Unexpected concurrent changes require stopping or revising the plan, not opportunistic expansion.

Neither an agent, adapter nor an engine should silently inherit unrestricted privileges. Proposed integration with [ARX](ARX_RELATIONSHIP.md), [Dragon-Hydra](DRAGON_HYDRA_RELATIONSHIP.md), [CWRE](CWRE_RELATIONSHIP.md) or [HAAEP](HAAEP_RELATIONSHIP.md) must preserve the same boundary. A risk assessment from CARE does not itself approve another system's action.

## Preserve secrets and continuity

Do not collect or export tokens, passwords, cookies, private keys, authentication-file contents, raw secret-bearing environment variables or configurations. Avoid machine reports containing private paths, identifiers, command lines or endpoints without deliberate sanitization. Evidence references and health summaries usually suffice.

Backups may contain secrets required for restoration. Keep them in separately protected storage with declared access and retention; do not copy them into reports, fixtures, repository history or human explanation surfaces. Snapshot sanitization is not backup protection. Fail closed on unsafe export while preserving a useful, non-sensitive failure notice.

Never erase healthy state for cleanliness. Do not disable security controls globally to make a diagnostic or repair pass. An inaccessible component should produce an explicit evidence state and limitation, not an automatic request for unrestricted elevation.

## Untrusted extensions and updates

Future adapters, packs or repair modules require explicit scope, reviewed provenance and constrained authority. No arbitrary unsigned repair-script execution, unverified executable replacement, silent download-and-run behavior, uncontrolled self-modification or silent policy weakening is permitted as a default capability.

Signatures and hashes can support origin/integrity checks; they do not prove that code is appropriate or safe for the current task. Adaptive growth means reviewed, versioned changes backed by evidence and tests.

## Verification boundaries

Security-sensitive effects must appear in the plan and in preservation checks. Verification must not weaken protections, broaden scope or expose secrets merely to achieve a passing result. When adequate verification is unavailable, report uncertainty and follow the declared [safe-stop or rollback path](REPAIR_CONTRACT.md).

Related: [evidence](EVIDENCE_MODEL.md), [snapshot](SNAPSHOT_MODEL.md), [rollback](ROLLBACK_MODEL.md), [human explanation](HUMAN_EXPLANATION.md).
