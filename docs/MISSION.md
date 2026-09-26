# CARE mission

Status: **ADOPTED PRINCIPLE / PROJECT CHARTER**, established 2026-09-26. Runtime
mechanisms remain **CONCEPT** unless implementation and scoped verification are
recorded in [PROGRESS](PROGRESS.md).

**CARE — Compatibility, Adaptation & Recovery Engineering** extracts and
formalizes recovery architecture from real CWRE lessons. It may eventually apply
to operating systems, AI agents, development runtimes, compilers, package
managers, GPU stacks, containers, databases, IDEs, local AI, network services,
engineering applications, and future ecosystems. This scope is direction, not
a statement of implemented universal support.

## Purpose and origin

One visible failure can contain several independent causes. CWRE's Windows/Codex
migration exposed questions about executable precedence, PATH, privilege context,
daemon rules, companion binaries, package completeness, provisioning,
configuration, and workspace assumptions. These lessons motivate CARE; they do
not justify copying a concrete implementation or hardcoding a universal remedy.

> A symptom is not the root cause. A repair is not merely making the symptom disappear.

## Central recovery law

```text
PROBLEM
  → OBSERVATION
  → EVIDENCE
  → CLASSIFICATION
  → ROOT CAUSE
  → REPAIR PLAN
  → BACKUP
  → MINIMAL CHANGE
  → VERIFICATION
       ├─ failure → ROLLBACK / SAFE STOP → verify rollback when attempted → report
       └─ success → RECOVERED STATE → GENERALIZED KNOWLEDGE
```

The cause stage is an evidence gate, not a demand to invent certainty. Missing
understanding can lead to another bounded observation, an explicitly labeled
authorized workaround, or safe stop; it must not become an unearned root-repair
claim. Generalized knowledge requires a reviewed incident and synthetic
regression evidence before promotion into reusable detection or repair rules.

## Permanent constraints

- Diagnose before mutation. Distinguish observation, inference, hypothesis,
  possible cause, confirmed cause, unknown, and unsupported.
- Identify healthy components and preserve them. Investigate unknown components
  rather than repair them solely because their health is unknown.
- Keep workaround availability, root-cause identification/removal, partial repair,
  and recovery verification distinct and scoped.
- Preserve evidence provenance and limitations. Missing observations do not
  silently become healthy, broken, true, or false.
- Use minimal justified changes, appropriate backups, post-change verification,
  and repair-specific rollback or safe-stop plans. Never promise universal undo.
- Model multi-cause failures, task-specific dependencies, and capabilities.
  Presence, compatibility, health, and requirement are different questions.
- Compare state and migrations without equating temporal order to causation.
  Return with knowledge, preserving useful changes where justified.
- Expose the same meaning to humans and machine consumers. Risk, uncertainty,
  recovery limits, evidence, and verification must survive presentation.

See [PRINCIPLES](PRINCIPLES.md) for the adopted laws.

## Architectural direction

[ARCHITECTURE](ARCHITECTURE.md) defines candidate engine and adapter boundaries.
Observation and evidence inform pure rules, health and causal analysis, dependency
and capability graphs, and scoped repair planning. Backup, authorized execution,
verification, rollback, reporting, and case-study knowledge remain separate
responsibilities.

The [evidence](EVIDENCE_MODEL.md), [unknown](UNKNOWN_MODEL.md),
[health](HEALTH_MODEL.md), [root-cause](ROOT_CAUSE_MODEL.md),
[dependency](DEPENDENCY_GRAPH.md), and [capability](CAPABILITY_GRAPH.md) models
should grow through real incidents. [State](STATE_MODEL.md),
[snapshots](SNAPSHOT_MODEL.md), [delta](DELTA_MODEL.md), and
[migration](MIGRATION_MODEL.md) models should preserve contextual comparisons.

[Rule](RULE_CONTRACT.md), [repair](REPAIR_CONTRACT.md),
[verification](VERIFICATION_CONTRACT.md), and [rollback](ROLLBACK_MODEL.md)
contracts are proposed semantic boundaries. They do not select a programming
language, database, transport, wire schema, or universal plugin mechanism.

[Human explanations](HUMAN_EXPLANATION.md), a future recovery playground, and
the [machine interface](MACHINE_INTERFACE.md) must consume those same semantics.

## Independent projects

[CWRE](CWRE_RELATIONSHIP.md) remains the concrete Windows/Codex specialist and
initial case-study source. CARE does not absorb, rename, rewrite, or duplicate it.
[HAAEP](HAAEP_RELATIONSHIP.md) remains the broader Human-AI engineering platform
and may independently consume CARE recovery intelligence and CWRE specialization.
[ARX](ARX_RELATIONSHIP.md) may collect/reconcile evidence;
[Dragon-Hydra](DRAGON_HYDRA_RELATIONSHIP.md) may orchestrate bounded agents using
recovery constraints. Neither integration is implemented by Genesis.

## Risk and authority

GREEN covers read-only or low-risk work. YELLOW requires explicit human
authorization, including PATH/configuration changes, package reinstall, services,
launchers, runtime repair, registry changes, and narrow security exclusions.
RED is never automatic by default: global security weakening, authentication or
project-data destruction, database deletion, unknown configuration erasure,
runtime wipes, certificate removal, and broad privilege weakening.

A risk label is not authority. The illustrative missing-helper example must
follow these rules; a package restoration is not automatically low-risk or exempt
from rollback planning because it later verifies. See [SECURITY_MODEL](SECURITY_MODEL.md).

## Genesis deliverable and stopping condition

Create an observed local CARE workspace, Git on `main`, a private repository in
the authenticated GitHub account, and `origin`. Establish documentation,
contracts, [CASE-001](CASE_STUDIES.md), a two-year conceptual
[roadmap](ROADMAP_2_YEARS.md), [decisions](DECISIONS.md),
[progress](PROGRESS.md), [session instructions](../AGENTS.md), and a
[mission template](../missions/MISSION_TEMPLATE.md). Licensing remains pending.

Validate required files, relative Markdown links, secret exclusion, truthful
capability claims, independent project boundaries, and one current next action.
Commit, push, and verify origin, repository, visibility, default branch, commit
equality, remote files, rendered README, and clean local Git state.

Do not implement a daemon, scanner, GUI, installer, kernel components, OS
adapters, automatic repair, model, marketplace, or remote service. The initial
next block is a synthetic ATLAS multi-cause case and human-readable causal
decomposition; its exact acceptance criteria live only in progress.

Stop after this coherent Genesis foundation. Future additions follow real
incident → evidence → model → rule → test → repair capability, one bounded
development block at a time.
