# Dependency graph

**Status: CONCEPT.** Genesis defines dependency semantics; there is no dependency scanner or resolver.

## Purpose

A dependency graph records which components and environmental conditions a defined task requires. It helps CARE localize a problem and preserve unrelated healthy state.

Presence is not compatibility. Compatibility is not health. Health is not proof that a component is required for the current task.

## Proposed nodes and edges

Nodes may represent an application installation, runtime, library, helper process, configuration, OS capability, external service, or workspace. Distinguish concrete installations and execution contexts; two binaries with the same product name need not be the same node.

An edge should identify:

- The dependent and prerequisite, including the applicable task or execution mode.
- Whether the requirement is mandatory, optional, conditional, or one alternative among several.
- Compatibility constraints such as interface behavior, architecture, supported versions, or configuration requirements.
- Evidence for the dependency itself, with source and freshness.
- Evidence about whether the prerequisite is satisfied in the observed context.
- Scope, unresolved assumptions, and consequences when the dependency is unavailable.

This is a semantic contract, not a prescribed graph database or schema.

## Evaluation boundaries

Do not infer a dependency merely because a package is installed on the same machine. An npm-based application and a standalone distribution may have different prerequisites; observe the actual installation and relevant metadata.

Unknown constraints remain unknown. A package version string may support identity while leaving interface compatibility, package completeness, or operational health unresolved. Prefer evidenced capabilities over brittle assumptions based only on version ranges.

If several alternatives are valid, preserve them explicitly. A failed optional edge does not make the application unhealthy. A dependency cycle should be reported with its scope; a future evaluator must not recurse indefinitely or silently discard an edge to make the graph appear valid.

## Impact and preservation

Incoming edges reveal other consumers of a proposed change. Before replacing a shared runtime or altering a service, examine affected consumers and preservation obligations. Incomplete discovery limits the strength of any “no other impact” claim.

External dependencies deserve explicit boundaries. An unreachable network service may reflect local connectivity, remote availability, authorization, or insufficient observation. Do not convert one failed connection into a confirmed remote-service failure.

Dependency graphs support [capability assessment](CAPABILITY_GRAPH.md), [causal investigation](ROOT_CAUSE_MODEL.md), and [repair planning](REPAIR_CONTRACT.md). They do not authorize automatic installation, deletion, or reconfiguration.
