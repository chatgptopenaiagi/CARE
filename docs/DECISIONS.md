# Architectural decisions

Append-only log. Genesis decisions below were accepted on **2026-09-26**.
Accepted principles constrain future work; runtime mechanisms remain **CONCEPT**.
Supersede a decision in a new entry, retaining the original rationale and history.

## CARE-ADR-001 — Diagnose before repair

**Status: ADOPTED PRINCIPLE.** Follow the Central Recovery Law from observation
and evidence through diagnosis, plan, backup, minimal change, verification,
recovery, and reviewed knowledge. Inadequate evidence permits investigation or
safe stop, not invented certainty.

**Reason:** A familiar symptom can have several different causes. Symptom relief
does not prove causal correction.

**Consequence:** Every proposed repair needs evidence and scoped causal reasoning.
See [PRINCIPLES](PRINCIPLES.md) and [ROOT_CAUSE_MODEL](ROOT_CAUSE_MODEL.md).

## CARE-ADR-002 — Healthy state is an explicit preservation obligation

**Status: ADOPTED PRINCIPLE.** Identify healthy, affected, and unresolved
components. Protect healthy state and verify preservation after justified changes.

**Reason:** Rebuilding an environment can damage working components and erase
evidence. Unknown state must not be treated as disposable.

**Consequence:** Plans describe exclusions, shared-dependency impact, and
preservation checks. Backups cannot justify an unnecessary rebuild.
See [HEALTH_MODEL](HEALTH_MODEL.md).

## CARE-ADR-003 — Uncertainty has distinct dimensions

**Status: ADOPTED PRINCIPLE; representation CONCEPT.** Keep presence, acquisition,
freshness, consistency, and applicability distinct. Preserve all requested states,
including known absence, unknown, unobservable, probe failed, unsupported, stale,
conflicting, and not applicable.

**Reason:** A known-present component can have stale evidence; a failed probe
does not prove target failure. A flat Boolean or overloaded enum loses meaning.

**Consequence:** Human and machine views must retain those distinctions. No wire
schema is fixed by Genesis. See [UNKNOWN_MODEL](UNKNOWN_MODEL.md).

## CARE-ADR-004 — Workflow recovery and root repair are separate claims

**Status: ADOPTED PRINCIPLE.** Workaround availability, cause identification,
cause removal, repair coverage, and verification are separate scoped dimensions.

**Reason:** A verified fallback can restore a workflow while the original
subsystem remains broken. One corrected branch need not resolve all causes.

**Consequence:** Preserve all six mission outcome terms without forcing a single
success ladder. Report residual failures and unknowns.
See [VERIFICATION_CONTRACT](VERIFICATION_CONTRACT.md).

## CARE-ADR-005 — Graphs preserve multiple causes and task requirements

**Status: ADOPTED PRINCIPLE; graph mechanisms CONCEPT.** Distinguish dependency,
capability, and causal relationships with evidence and typed meaning.

**Reason:** Presence, compatibility, health, and task necessity differ. Several
independent or interacting causes can produce one symptom.

**Consequence:** Do not infer causes from dependency edges, temporal order, or
agent agreement alone. Graph storage technology remains undecided.
See [DEPENDENCY_GRAPH](DEPENDENCY_GRAPH.md) and [CAPABILITY_GRAPH](CAPABILITY_GRAPH.md).

## CARE-ADR-006 — Rules remain pure and versioned

**Status: ADOPTED PRINCIPLE.** Rule evaluation consumes explicit evidence and
context and produces findings. It neither observes implicitly nor mutates.

**Reason:** Diagnostic reproducibility and review require separation from live
collection and execution authority.

**Consequence:** Findings retain stable rule identity/revision, applicability,
evidence, and limitations. A recommendation is not permission.
See [RULE_CONTRACT](RULE_CONTRACT.md).

## CARE-ADR-007 — Recovery transactions are bounded, not universally atomic

**Status: ADOPTED PRINCIPLE; transaction execution CONCEPT.** Define backup,
apply, verification, return, and safe-stop behavior per repair. Rollback classes
are EXACT, COMPENSATING, PARTIAL, IMPOSSIBLE, and UNKNOWN.

**Reason:** External effects, concurrent changes, and missing restoration
mechanisms can prevent exact return. A snapshot is not automatically a backup.

**Consequence:** Verify fresh post-change evidence and any attempted rollback;
protect unrelated changes and retain learning. `COMMIT_RECOVERY` records scoped
verified recovery, not a Git commit, universal ACID guarantee, or backup deletion.
See [REPAIR_CONTRACT](REPAIR_CONTRACT.md) and [ROLLBACK_MODEL](ROLLBACK_MODEL.md).

## CARE-ADR-008 — Specialist projects remain independent

**Status: ADOPTED PRINCIPLE.** CARE learns theory and contracts from CWRE without
copying or replacing its concrete implementation. HAAEP, ARX, and Dragon-Hydra
remain separate collaborators with prospective contracts.

**Reason:** Shared vocabulary does not justify merging ownership, source, state,
permissions, or runtime responsibilities.

**Consequence:** Genesis reads architectural lessons only, imports no code or
private machine reports, and modifies none of those projects. No existing project
is claimed to implement a CARE contract. See [CWRE_RELATIONSHIP](CWRE_RELATIONSHIP.md),
[HAAEP_RELATIONSHIP](HAAEP_RELATIONSHIP.md), [ARX_RELATIONSHIP](ARX_RELATIONSHIP.md),
and [DRAGON_HYDRA_RELATIONSHIP](DRAGON_HYDRA_RELATIONSHIP.md).

## CARE-ADR-009 — Private Genesis and pending licensing

**Status: ADOPTED PRINCIPLE / repository policy.** Genesis uses the authenticated
account `chatgptopenaiagi` and private repository name `CARE`. Licensing remains
pending; [LICENSE](../LICENSE) grants no project-wide license.

**Reason:** The mission explicitly requests private publication and does not
establish a commercial or open-source license preference.

**Consequence:** A later visibility or licensing change requires an explicit
owner decision recorded here. Private visibility does not make secrets,
machine reports, or external source suitable repository contents.

## CARE-ADR-010 — Explicit risk policy outranks the illustrative helper example

**Status: ADOPTED PRINCIPLE.** GREEN is read-only or justified low-risk work;
YELLOW requires explicit human authorization; RED is never automatic by default.
In CARE, every package reinstall is YELLOW.

**Reason:** The mission's risk section classifies reinstall as YELLOW, while its
informal human-explanation example labels matching-package restoration low risk
and implies rollback is unnecessary after verification. The explicit risk and
repair-specific rollback laws govern the example.

**Consequence:** Human explanations must use the plan's actual risk and state
backup/recovery requirements before mutation. CARE does not silently inherit
CWRE's case-specific GREEN reinstall example. Existing exact authorization may
be reused, but a blanket grant cannot erase material scope or risk changes.
See [SECURITY_MODEL](SECURITY_MODEL.md) and [HUMAN_EXPLANATION](HUMAN_EXPLANATION.md).

## CARE-ADR-011 — Genesis is prose contracts, not executable architecture

**Status: ADOPTED PRINCIPLE.** Create documentation and repository discipline;
select no implementation language, serialization schema, GUI framework, scanner,
universal adapter, plugin loader, or repair service.

**Reason:** The architecture should grow from incidents rather than speculative
module generation. Synthetic conceptual cases can reveal unclear semantics first.

**Consequence:** Catalog READMEs contain no fake implementations. The sole next
block is the fictional ATLAS causal-decomposition experiment defined in
[PROGRESS](PROGRESS.md), not a repair engine or live probe.

## CARE-ADR-012 — Knowledge promotion retains evidence and scope

**Status: ADOPTED PRINCIPLE.** Preserve source lineage and distinguish incident
lessons from operationally eligible rules. Promotion requires verified cause and
repair, reviewed applicability, and synthetic regression cases.

**Reason:** Unverified anecdotes and repeated assertions cannot establish a
safe reusable repair. Historical evidence cannot silently become a current probe.

**Consequence:** CASE-001 is a sanitized documentation-level case, with original
verification limits retained. Failed attempts can teach without becoming verified
repair rules. Synthetic cases remain synthetic after publication.
See [CASE_STUDIES](CASE_STUDIES.md) and [EVIDENCE_MODEL](EVIDENCE_MODEL.md).
