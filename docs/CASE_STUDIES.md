# Case studies

Status: **CONCEPT** for the case-study model; **historical documentation review** for CASE-001. CARE has not reproduced the incident or implemented a recovery system.

Cases connect a reported problem to evidence, competing explanations, a bounded intervention, and its verification. They are not collections of repair recipes to execute on similar-looking machines.

## Proposed case record

| Field | Purpose |
|---|---|
| Case identity and revision | Stable reference with an explicit correction history |
| Origin and scope | Environment family, affected capability, transition, and limits of applicability |
| User symptom | Observable loss of function, separate from its explanation |
| Evidence ledger | Sanitized observations, provenance, time, probe scope, and evidence states |
| Component assessment | Healthy, affected, unknown, and out-of-scope components |
| Causal decomposition | Supported candidates, confirmed causes, counterevidence, and unresolved alternatives |
| Intervention history | Workarounds, proposed repairs, actual authorized changes, and ordering |
| Preservation and recovery | Protected state, backup scope, and actual rollback feasibility |
| Verification | Tests performed, fresh results, scope, failures, and remaining uncertainty |
| Knowledge disposition | Lessons retained, proposed generalization, and regression-test references |

Identifiers, timestamps, paths, command output, environment values, and even hashes may reveal private information. A publishable case must undergo a deliberate sanitization review. Preserve enough scope and provenance to assess a claim without copying private reports, authentication state, sessions, or machine-specific identifiers.

## CASE-001: Codex CLI Windows migration

**Case status:** historical, documentation-derived case outline. The originating transition was the Codex CLI 0.156.x to 0.157.1 migration described by CWRE. CARE reviewed CWRE's architecture documentation during Genesis on 2026-09-26. This is not a fresh live-machine reproduction, a vendor compatibility statement, or proof that every installation at these versions has the same failures.

**Symptom family:** expected Codex workflows became unavailable or behaved differently after migration. The case demonstrates that a single visible symptom can span independent layers.

| Reported layer or lesson | General engineering implication | What remains to be established in another incident |
|---|---|---|
| PATH precedence and multiple installations | Resolve the executable actually used before interpreting its version | Effective command resolution in the affected process and workspace |
| Package layout and missing companion executable | A CLI version response does not prove package completeness | Authoritative package expectations and scoped filesystem observations |
| Windows privilege and token context | User identity alone does not describe execution capability | Relevant token properties and the application's actual requirements |
| Daemon provisioning, lifecycle, and version parity | A foreground executable can work while a background capability fails | Process identity, release state, supported control path, and compatible versions |
| Configuration and workspace assumptions | Valid syntax and existing paths do not prove effective behavior | Loaded configuration, overrides, target identity, and task applicability |
| Healthy runtime or state alongside a failed layer | Recovery should target the affected surface and preserve continuity | Scoped health evidence and protected-state invariants |

These are candidates and lessons for investigation, not a claim that each reported issue caused every observed failure. A case revision may promote a specific causal claim only when its supporting evidence and verification are available and reviewed. CARE does not import CWRE's code, reports, rule IDs, or machine data, and does not claim that every CWRE recommendation has an implemented repair.

## Promotion into reusable knowledge

The required path is:

```text
incident evidence
  -> verified root cause within a stated scope
  -> verified repair within a stated scope
  -> reviewed, versioned rule proposal
  -> synthetic regression cases, including counterexamples and unknown evidence
  -> eligible future detection or explicitly authorized repair capability
```

A diagnostic observation may inform a detection-only experiment before the repair is known. It must remain labeled as such and cannot qualify an automatic repair. Historical success, anecdote, version coincidence, or a disappearing symptom is insufficient to promote a repair rule. Generalization must preserve applicability limits, evidence requirements, contraindications, and verification obligations.

Synthetic cases need their own provenance and must never be reported as live incidents. The planned first experiment is governed by the single current action in [progress](PROGRESS.md); it does not create a repair engine.

See [evidence](EVIDENCE_MODEL.md), [root causes](ROOT_CAUSE_MODEL.md), [rule contract](RULE_CONTRACT.md), and [CWRE relationship](CWRE_RELATIONSHIP.md).
