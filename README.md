# CARE

**Compatibility, Adaptation & Recovery Engineering** is a long-term recovery
architecture project derived from the engineering lessons of CWRE. CARE asks
what failed, what remains healthy, what evidence supports a cause, and what the
smallest justified recovery would be.

**Status: Genesis documentation foundation.** Principles are adopted; software
mechanisms and contracts are conceptual. No scanner, repair engine, daemon,
GUI, installer, OS adapter, AI model, or remote service exists in this repository.

> A symptom is not the root cause. A repair is not merely making the symptom disappear.

## Central recovery law

```text
PROBLEM → OBSERVATION → EVIDENCE → CLASSIFICATION → ROOT CAUSE
    → REPAIR PLAN → BACKUP → MINIMAL CHANGE → VERIFICATION
                                                 |
                      failure → ROLLBACK / SAFE STOP
                                                 |
                           success → RECOVERED STATE
                                        → GENERALIZED KNOWLEDGE
```

Insufficient evidence does not advance into a confirmed cause or automatic
repair. Failed verification enters a bounded recovery or safe-stop path; rollback
needs its own verification. A recovered state is scoped to an objective, and a
generalized rule requires reviewed evidence and regression cases.

## What CARE preserves

- **Diagnose first:** distinguish observations, inferences, hypotheses, possible
  causes, confirmed causes, unknowns, and unsupported questions.
- **Preserve healthy state:** repair the affected component, investigate unknown
  components, and protect components whose relevant health has been established.
- **Preserve uncertainty:** missing, inaccessible, failed, stale, conflicting,
  and unsupported evidence must not silently become Boolean health.
- **Separate workaround from repair:** restored workflow is not proof that the
  original cause was removed. Verification is a separate claim.
- **Change minimally and verify:** define the objective, backup, authority,
  effects, and verification before mutation.
- **Return with knowledge:** recovery may be exact, compensating, partial,
  impossible, or unknown. Retain the evidence and learning after a return.

See [principles](docs/PRINCIPLES.md) and the [mission](docs/MISSION.md).

## Architecture in brief

The proposed [architecture](docs/ARCHITECTURE.md) separates observation and
evidence from pure diagnostic rules, repair planning, authorized execution,
verification, and recovery. Human explanations and machine consumers use the
same authoritative meaning.

| Model | Purpose |
| --- | --- |
| [Evidence](docs/EVIDENCE_MODEL.md) and [unknown](docs/UNKNOWN_MODEL.md) | Retain provenance, scope, freshness, conflict, and limitations |
| [Health](docs/HEALTH_MODEL.md) | Identify what is healthy, broken, degraded, or unknown for a stated task |
| [Root cause](docs/ROOT_CAUSE_MODEL.md) | Represent multiple supported causal branches rather than assume one error means one cause |
| [Dependencies](docs/DEPENDENCY_GRAPH.md) and [capabilities](docs/CAPABILITY_GRAPH.md) | Separate presence, compatibility, health, and current-task necessity |
| [State](docs/STATE_MODEL.md), [snapshot](docs/SNAPSHOT_MODEL.md), [delta](docs/DELTA_MODEL.md), [migration](docs/MIGRATION_MODEL.md) | Compare scoped observations across changes without assuming temporal correlation proves cause |
| [Rules](docs/RULE_CONTRACT.md) | Stable, versioned, evidence-backed evaluation with no direct mutation |
| [Repair](docs/REPAIR_CONTRACT.md), [verification](docs/VERIFICATION_CONTRACT.md), [rollback](docs/ROLLBACK_MODEL.md) | Define bounded transactions and honest restoration limits |

These are proposed semantic contracts, not a frozen schema or implemented API.
No language, transport, database, GUI framework, or plugin loader is selected.

## People, machines, and independent projects

The [human explanation layer](docs/HUMAN_EXPLANATION.md) should show component,
status, effect, evidence, uncertainty, proposed action, risk, recovery limits,
and verification. A future recovery playground may expose health, dependencies,
incidents, evidence, state timelines, simulation, repairs, and before/after views.
The [machine interface](docs/MACHINE_INTERFACE.md) should expose the same facts
and outcomes without requiring tools to scrape prose.

| Project | Boundary |
| --- | --- |
| [CWRE](docs/CWRE_RELATIONSHIP.md) | Independent Windows/Codex implementation and initial case study; CARE learns from it without copying or replacing it |
| [HAAEP](docs/HAAEP_RELATIONSHIP.md) | Broader Human-AI platform that may consume CARE and specialized CWRE independently |
| [ARX](docs/ARX_RELATIONSHIP.md) | Possible evidence collection/reconciliation collaborator; CARE interprets recovery implications |
| [Dragon-Hydra](docs/DRAGON_HYDRA_RELATIONSHIP.md) | Possible orchestrator consuming CARE health/recovery constraints; no authority bypass |

## Risk and recovery

[Security policy](docs/SECURITY_MODEL.md) distinguishes **GREEN** read-only or
low-risk work, **YELLOW** changes requiring explicit human authorization, and
**RED** actions that are never automatic by default. Package reinstalls are
YELLOW. A color is not permission, and a successful repair cannot retroactively
justify skipping its prechecks or backup requirements.

## Growth through incidents

[CASE-001](docs/CASE_STUDIES.md) preserves sanitized architectural lessons from
CWRE's Windows/Codex migration. It is a historical documentation review, not a
new live reproduction or a universal compatibility claim.

The [two-year roadmap](docs/ROADMAP_2_YEARS.md) moves from foundation and synthetic
cases toward small evidenced diagnostic and recovery capabilities, then broader
adapters and integrations only where real incidents justify them. It is a
direction, not a delivery promise or permission to build every engine now.

## Continue one block at a time

Read [AGENTS.md](AGENTS.md), [MISSION](docs/MISSION.md), [PROGRESS](docs/PROGRESS.md),
relevant [decisions](docs/DECISIONS.md), and affected contracts. Follow the single
`NEXT_EXACT_ACTION`: a future synthetic ATLAS multi-cause case with a
human-readable causal decomposition, no live probes, and no repair engine.

Use the [mission template](missions/MISSION_TEMPLATE.md), preserve existing work,
validate the bounded result, document it, commit, push when appropriate, leave
one next action, and stop.

Genesis establishes documentation, catalogs, Git, and a private GitHub repository.
It does not establish runtime support, enforced permissions, or verified repairs.
Licensing remains [pending](LICENSE); private visibility is not permission to
store secrets or import private machine reports.
