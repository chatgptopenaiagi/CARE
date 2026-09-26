# State model

Status: **CONCEPT**. These are semantic requirements for future implementations; Genesis has no state store or state engine.

## What a state describes

A state is a scoped, time-bound description of an environment, not a claim that CARE knows the whole machine. A future state record should identify:

- The environment and component identities, using sanitized identifiers where possible.
- The task or capability being evaluated and the observation scope.
- Capture times, observation methods, evidence references and relevant contract versions.
- Facts with their explicit [evidence states](UNKNOWN_MODEL.md), including unobserved areas.
- Health judgments, their criteria and the evidence that supports them.
- Known concurrent changes, collection gaps and comparability limits.

An observation can become stale while an investigation is in progress. A later observation must not silently overwrite earlier evidence or its original meaning.

## State and knowledge are different

**ADOPTED PRINCIPLE — distinguish environment change from knowledge change.** Discovering that a helper was already absent changes CARE's knowledge; it does not prove that the helper disappeared during the investigation. A probe failure changes observability; it does not prove a component failed.

Keep the observed environment, the evidence available about it, and interpretations of that evidence distinguishable. A state can contain conflicting observations without resolving them by majority vote or silently selecting the newest source.

## Baselines and transitions

`S0` is a selected baseline with stated criteria and limitations. Calling it a baseline does not make every component healthy. `S1` is another scoped observation, possibly after an update. `Delta(S0, S1)` requires compatible identities, scopes and fact meanings; otherwise its affected portions are incomparable.

Classify differences as expected change, unexpected change, improvement, regression, knowledge-only change, incomparable state or insufficient evidence. More than one classification can apply to different components. Improvement and regression require an intended objective and verification criteria, not merely a version increase.

The [delta model](DELTA_MODEL.md) records differences. The [root-cause model](ROOT_CAUSE_MODEL.md) separately evaluates causal explanations. Temporal order alone does not connect those two claims.

## Selective return with knowledge

A degraded `S1` may lead to selective restoration and then `S2`. `S2` need not equal `S0`: useful changes may remain while a proven harmful change is reversed. Preserve healthy components and investigate unknown components instead of treating them as disposable.

Before a proposed return, identify its exact target, dependency impact, known concurrent changes and preservation conditions. Afterward, verify the restored surface and relevant dependencies. Preserve incident evidence, failed attempts, comparison results and recovery outcomes even when component state returns to an earlier version.

Returning safely is a [repair-specific recovery operation](ROLLBACK_MODEL.md), not a property automatically provided by retaining state descriptions. A [snapshot](SNAPSHOT_MODEL.md) is not necessarily a backup.

## Future validation obligations

Synthetic scenarios should demonstrate knowledge-only changes, partly comparable states, stale evidence, conflicting observations, healthy components that remain unchanged, and a selective return that preserves useful changes. These obligations are conceptual; no such executable tests exist in Genesis.

Related: [health](HEALTH_MODEL.md), [migration](MIGRATION_MODEL.md), [repair](REPAIR_CONTRACT.md), [HAAEP relationship](HAAEP_RELATIONSHIP.md).
