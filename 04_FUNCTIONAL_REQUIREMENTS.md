# 04 — Functional Requirements

**Priority:** P0 = core hackathon proof; P1 = important UX; P2 = optional polish.

| ID | Priority | Requirement | Acceptance evidence |
|---|---|---|---|
| FR-01 | P0 | Create nine agents: 3 Customer, 3 Operations, 3 Data | Typed roster contains nine unique IDs |
| FR-02 | P0 | Seeded scenario with one elevated-risk profile per role | Same seed repeats assignments; Guardians cannot access truth |
| FR-03 | P0 | Emit structured messages, actions, tool calls, permissions, interactions and results | Events validate against schema |
| FR-04 | P0 | Correlate events by agent, task and requester/recipient | Trace IDs link related activity |
| FR-05 | P0 | Preserve complete normal and suspicious history | Chronological audit available |
| FR-06 | P0 | Evaluate hard permissions, sensitivity, destinations and approvals | Denied transfer rejected without model |
| FR-07 | P0 | Retrieve versioned policy entries | Decisions include policy IDs/version |
| FR-08 | P0 | Alpha evaluates task and behaviour trajectory | Evidence-backed Alpha result |
| FR-09 | P0 | Beta evaluates requester, recipient and pending response | Evidence-backed Beta result |
| FR-10 | P0 | Gamma checks policy, gate and execution evidence | Pre-check and post-audit records |
| FR-11 | P0 | Mistral contextual evaluation with structured schema | Validated output, errors handled |
| FR-12 | P0 | Reject malformed or unsupported model evidence | No unvalidated model ALLOW |
| FR-13 | P0 | Support WHITE/YELLOW/ORANGE/RED and direct WHITE→RED | State transition tests |
| FR-14 | P0 | Separate state, decision, intervention and outcome | Distinct fields in trace |
| FR-15 | P0 | Gate every protected operation before execution | No direct tool bypass path |
| FR-16 | P0 | Support ALLOW/WARN/RESTRICT/PAUSE/BLOCK/ISOLATE | Decision tests |
| FR-17 | P0 | Protect recipient from unsafe request | Recipient tool call not executed |
| FR-18 | P0 | Isolate prohibited agent logically | Permissions suspended; history retained |
| FR-19 | P0 | Gamma verifies enforcement, flags mismatches | Failure-injection test |
| FR-20 | P0 | Deterministic restrictions remain on API failure | Timeout fail-closed test |
| FR-21 | P0 | Mock and live Mistral modes visibly distinguished | UI/test evidence |
| FR-22 | P1 | Full-width approved-style district and nine agents | Visual review |
| FR-23 | P1 | One dark bottom chronological conversation panel | No cards, counters or timestamps |
| FR-24 | P1 | Backend-derived colour for activity and sensor | No keyword colour inference |
| FR-25 | P1 | Auto-focus attention; click agent to select | Interaction test |
| FR-26 | P1 | Red isolated-agent avatar stack at bottom-right | Click reveals history |
| FR-27 | P1 | On-demand event evidence and Guardian assessments | Click event opens trace |
| FR-28 | P2 | Smooth camera movement and scene polish | Visual review |

## State rules
- WHITE authorised; YELLOW early concern; ORANGE credible risk requiring pause/restriction; RED prohibited/hard violation.
- Hard policy violations can move directly to RED.
- YELLOW/ORANGE recovery requires verified resolution; RED reinstatement requires authorised review.
- Do not average away a current critical violation.

## Non-functional requirements
- No API keys in browser or repository.
- Schema-validate all external/model inputs.
- Preserve policy/model versions, event IDs and gate outcomes.
- Avoid unnecessary sensitive context in LLM requests.
- Fixed-seed demo must be reproducible; different seeds used in tests.
- A failed audit must not be reported as successful enforcement.

## Out of scope
Production multitenancy, physically distributed Guardians, full enterprise IAM, fine-tuning, compliance certification, universal threat coverage.
