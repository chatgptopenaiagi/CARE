# Migration model

Status: **CONCEPT**. A migration is a transition to investigate, not an implemented migration service or a promise of version compatibility.

## Observe transitions

Software, runtimes, operating systems, package managers, drivers, configuration formats and directory locations can change together. Understanding only the destination version can miss which prerequisite, execution context or resolution rule changed.

A future migration record should describe:

- Source and target states, their observation coverage and relevant versions/capabilities.
- Intended objective, expected differences and preservation constraints.
- Changed components, dependencies, installation provenance and execution context.
- Transition actions known to have occurred, their source and timing uncertainty.
- Before/after verification criteria, observations and unexpected differences.
- Candidate causal paths, alternative explanations, unknowns and concurrent changes.
- Recovery options, verified results and knowledge that can safely generalize.

When there is no trustworthy source snapshot, record the gap. Historical recollection, vendor documentation and a live destination observation have different provenance. Do not reconstruct an allegedly certain baseline by combining them silently.

## Capability-aware analysis

Version identifiers can constrain applicability, but a version string alone does not establish package completeness, companion-binary presence, supported launch modes or task health. Prefer direct capability observations when safe and available; retain version and documentation evidence with their scope.

Multiple changes can contribute independently. An older executable resolving first and an incomplete newer package can coexist. Repairing PATH may expose the package failure rather than create it. Re-evaluate remaining causal branches after every verified change.

## Initial case-study direction

CWRE's reported Codex CLI Windows migration from the 0.156 series to the 0.157 series motivates [CASE-001](CASE_STUDIES.md). Its lessons concern executable resolution, privilege context, companion binaries, package integrity and daemon lifecycle.

These are case-study lessons, not universal claims that every installation or release in those series has the same behavior. Detailed implementation and evidence remain in independent CWRE. CARE must preserve each claim's provenance, conditions and verification limits before using it in a reusable rule.

## From incident to knowledge

A transition profile should be promoted only from verified incident evidence: establish applicable conditions, confirmed causes, verified repair and recovery limits, then add a synthetic regression case. Unverified narratives remain hypotheses or research material.

Profiles require stable identity, revision history, evidence references, supported scope and invalidation conditions. New contrary evidence can narrow or supersede a profile; it must not silently rewrite historical findings. A profile can recommend investigation without permitting mutation.

## Recovery direction

Migration recovery may restore one component, compensate for a change or safely stop. It need not downgrade everything. [Repair planning](REPAIR_CONTRACT.md) preserves healthy state, checks dependencies and states whether useful destination changes can remain. [Rollback](ROLLBACK_MODEL.md) must be evaluated for this transition; a version downgrade is not automatically a valid restore.

Related: [state](STATE_MODEL.md), [delta](DELTA_MODEL.md), [rules](RULE_CONTRACT.md), [CWRE relationship](CWRE_RELATIONSHIP.md).
