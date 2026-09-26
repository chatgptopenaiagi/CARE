# CARE and Dragon-Hydra

Status: **RESEARCH DIRECTION**. No agent swarm, orchestration runtime, or integration is implemented.

Dragon-Hydra may orchestrate agents. CARE may supply environment health findings, recovery implications, preservation constraints, and proposed verification requirements. CARE does not become the orchestrator, and Dragon-Hydra does not gain authorization by requesting an assessment.

## Proposed interaction

```text
orchestrator proposes a scoped action
  -> CARE assesses available evidence and recovery constraints
  -> result: eligible to seek authorization, revise, simulate, investigate, or refuse
  -> human authorization and applicable policy checks
  -> responsible executor rechecks preconditions
  -> scoped execution and fresh verification
  -> original findings, actual effects, and unresolved uncertainty retained
```

"Eligible" means the proposal may proceed to the required authorization and execution gates. It is not an approval token. CARE's advice does not itself execute a change, and no diagnostic result can override security policy.

## Coordination boundaries

- Delegated work needs a bounded scope, target identity, time/resource limits, and explicit stop conditions.
- Agents must preserve original evidence references and distinguish observations from their interpretations.
- Proposed plans need stable identity and preconditions so concurrent agents cannot silently substitute targets or act on stale state.
- Conflicting proposals require reconciliation before mutation; more votes are not stronger causal evidence.
- An unknown health prerequisite must remain visible. Whether it blocks execution depends on the action's declared evidence requirements, not an orchestrator's desire to finish.
- Delegation cannot expand a human grant. A sub-agent receives only the authority deliberately assigned within applicable limits.
- Failure, cancellation, partial execution, and failed rollback must be reported explicitly; the system must not retry consequential changes indefinitely.

These are architectural requirements, not existing enforcement. Future research should exercise a synthetic proposal and a synthetic conflict before connecting any agent to live repair execution.

See [repair contract](REPAIR_CONTRACT.md), [security model](SECURITY_MODEL.md), [verification](VERIFICATION_CONTRACT.md), and [machine interface](MACHINE_INTERFACE.md).
