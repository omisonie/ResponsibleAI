# 05 — Technical Architecture

## System path
```text
Agent simulation (9 agents, 3 roles)
    ↓
Typed event collector → event store
    ↓
Context builder + versioned policy retrieval
    ├── Deterministic permissions / destination checks
    ├── Alpha: behavioural evidence
    ├── Beta: interaction evidence
    └── Gamma: policy / assurance evidence
             ↓
Mistral contextual assessment (where relevant)
             ↓
Strict schema + evidence-reference validator
             ↓
Decision engine (hard restrictions always prevail)
             ↓
ACTION GATE: allow / warn / restrict / pause / block / isolate
             ↓ (only authorised operations execute)
Tool result / non-invocation proof
             ↓
Gamma post-action audit → persisted trace → Guardian View
```

## Component contracts
- **Simulator:** emits proposed actions and dialogue; never calls protected tools directly. Hidden risk assignment lives in evaluation-only storage.
- **Collector:** assigns event ID, agent/task/interaction IDs, timestamp, context, proposed/completed status.
- **Policy engine:** checks resource permissions, sensitivity, tool allowlists, destinations, approvals and explicit prohibitions. Hard deny is authoritative.
- **Context builder:** selects relevant prior events and applicable policy excerpts, minimising data passed to Mistral.
- **Alpha:** sees objective, history and trajectory; returns findings with event references.
- **Beta:** sees requester/recipient, proposed interaction and impact; can recommend recipient hold.
- **Gamma:** sees policy, permission, gate and tool-result evidence; independently checks compliance and actual enforcement.
- **Mistral evaluator:** contextual reasoning only; structured output; never grants denied permission.
- **Validator:** rejects malformed output, invalid enums, invented event/policy refs, unsupported claims.
- **Decision engine:** hard deny > mandatory approval > contextual risk; disagreement triggers review/restriction, never majority override.
- **Action gate:** sole protected tool execution path. A BLOCK outcome must not invoke the tool.
- **Audit store:** records original event, context refs, policy version, model/version, Guardian assessments, decision, intervention, actual tool result and Gamma verification.

## Example proposed action
```json
{
  "event_id":"evt-100",
  "agent_id":"customer-02",
  "event_type":"external_data_transfer",
  "task_context":"inventory_support",
  "action":"send_customer_record",
  "resource_sensitivity":"restricted",
  "destination":"external_endpoint",
  "destination_authorised":false,
  "requester_agent_id":"customer-02",
  "recipient_agent_id":"data-03",
  "related_event_ids":["evt-097","evt-099"],
  "execution_status":"pending"
}
```

## Example contextual assessment
```json
{
  "classification":"UNSAFE",
  "severity":"critical",
  "policy_ids":["P01-003","P09-002"],
  "reason":"Restricted customer data requested for an unauthorised destination",
  "evidence_refs":["evt-100","evt-099"],
  "recommended_intervention":"BLOCK",
  "uncertainty":"low"
}
```
Model-reported uncertainty is not a calibrated probability.

## Enforcement invariants
1. Protected tool execution requires a positive gate decision.
2. Denied destination or permission cannot be overridden by an LLM.
3. PAUSE means the operation has not executed.
4. BLOCK records a non-invocation result; Gamma checks it.
5. Isolation suspends relevant permissions and pending operations while retaining history.
6. On model failure, deterministic restrictions remain active; unresolved protected operations use restrictive fallback.

## Implementation stack
Inspect the repository first. Candidate: React/TypeScript + existing 3D renderer/Three.js, FastAPI or Node backend, Pydantic/Zod validation, SQLite, Mistral API. Avoid framework rewrites. API keys server-side. Explicitly label mock mode.

## Suggested tables
`agents`, `events`, `policies`, `assessments`, `decisions`, `tool_results`, `audits`, `scenarios`. Scenario ground truth must not be in Guardian-facing payloads.

## Key failure tests
Malformed model JSON; model ALLOW on denied transfer; missing evidence; timeout; conflicting Guardian findings; tool executes despite BLOCK; audit log missing. The last two must produce Gamma assurance failures.
