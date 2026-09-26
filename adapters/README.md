# Adapters

Status: **CONCEPT catalog; no adapter implementations or supported platforms**.

Future adapters may cover operating systems, runtimes, compilers, packages,
GPU stacks, containers, Git, databases, services, and AI providers. The
[architecture](../docs/ARCHITECTURE.md) explains their boundaries.

An adapter translates concrete evidence and bounded operations while preserving
scope, provenance, context, unknowns, side effects, and permissions. Unsupported
probe output must not become a healthy result. Installation presence is not
compatibility, health, or task requirement.

Future entries need a real incident, supported/tested contexts, applicable
contracts, probe effects, sanitized fixtures, failure behavior, and limitations.
Do not invent a universal OS abstraction or generate empty platform modules.
