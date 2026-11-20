# 02 — Product Differentiation

## Positioning
**Do not merely detect unsafe agent behaviour: prevent unsafe execution and independently verify protection.** SafeAI Guardian complements prompt guardrails, observability and access control by linking behaviour, interaction and execution evidence.

## Comparison
| Capability | Typical standalone approach | SafeAI Guardian prototype |
|---|---|---|
| Prompt/output moderation | Individual text check | Includes contextual assessment but is not limited to text |
| Agent observability | Records traces | Uses traces to make protective decisions |
| Access control | Checks explicit permissions | Preserves hard controls and adds behavioural context |
| Tool-call filtering | Checks proposed call | Correlates call with prior trajectory and recipient |
| Post-hoc audit | Explains past events | Verifies that preventive enforcement actually worked |

These are category-level distinctions, not claims that every competing product lacks these capabilities.

## Six differentiators
1. **Trajectory over isolated events:** detect escalating data requests and deviation from task.
2. **Interaction-level protection:** check requester and recipient; prevent proxy bypass and unsafe compliance.
3. **Real pre-execution gate:** reject prohibited transfers before any external tool invocation.
4. **Distinct Guardian perspectives:** Alpha behaviour, Beta interaction, Gamma assurance; no majority override of hard policy.
5. **Supervisor assurance:** Gamma checks actual tool invocation and outcome, not just the intended decision.
6. **Evidence-first explainability:** full event history, policies, model output, validation, decision, gate result and audit.

## Demo proof points
| Claim | Proof |
|---|---|
| Early risk | Sequence shows WHITE→YELLOW→ORANGE based on evidence |
| Recipient protection | Data Agent receives unsafe request and does not comply |
| Prevention | Assert simulated transfer tool invocation count remains zero |
| Assurance | Gamma checks gate and tool result; failure injection exposes mismatch |
| Transparency | Click event to see evidence refs and policy version |

## What not to claim
Do not call three identical model calls independent; do not equate warnings with blocks; do not claim calibrated confidence, perfect detection or production compliance. Clearly label mocked versus live Mistral evaluation.
