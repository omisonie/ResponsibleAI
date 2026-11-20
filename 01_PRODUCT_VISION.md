# 01 — Product Vision

**Product:** SafeAI Guardian  
**Tagline:** Autonomous agents need oversight. Their overseers need it too.

## Vision
Autonomous agents make decisions, use tools, access data and interact with humans and other agents. Risk can emerge across a sequence of otherwise innocuous actions; post-hoc monitoring alone cannot prevent harm. SafeAI Guardian is an independent supervisory and assurance layer that monitors trajectories, protects interaction boundaries, enforces policy before execution and verifies the result.

**Observe → Evaluate → Intervene → Protect → Verify → Improve.**

## Product problems
1. Prompt/output checks miss multi-step trajectories.
2. One agent can ask another to bypass restrictions.
3. Alerts do not guarantee an unsafe operation was prevented.
4. Safety supervisors themselves can misclassify events or fail to enforce decisions.
5. Without full history, reviewers cannot reconstruct why an intervention occurred.

## Three-Guardian proposition
| Guardian | Evidence | Key question |
|---|---|---|
| Alpha — Behaviour | Objective, task, actions, history, trajectory | What is the agent doing and why? |
| Beta — Interaction | Requester, recipient, message, proposed response, impact | Who could be affected? |
| Gamma — Assurance | Policy, permissions, gate decision, execution result, audit | Was it permitted and properly handled? |

The three roles must have distinct evidence projections. They do not take a majority vote: deterministic prohibitions take precedence. Material disagreements trigger review or restriction.

## States and action
| State | Meaning | Typical action |
|---|---|---|
| WHITE | Authorised | Allow, monitor |
| YELLOW | Emerging concern | Inspect trajectory |
| ORANGE | Credible risk | Pause, restrict, verify |
| RED | Prohibited/hard violation | Block, possibly isolate |

Direct WHITE→RED is allowed. YELLOW/ORANGE can recover after verified resolution. RED reinstatement requires authorised review. State, decision, intervention and execution outcome are different records.

## Pause & Protect
Intervene before a protected action executes. A recipient agent may be held before answering an unsafe request; a tool/API call may be blocked at the gate; a human may be warned where the product has an authorised integration. A warning alone is not protection. Explain safe alternatives where possible.

## Prototype scope
A shared cinematic smart-retail district with nine agents (three roles × three). The simulator assigns one hidden elevated-risk profile per role. Demonstrate a Customer Assistant's escalating unauthorised data transfer, an Operations Agent's correction, and a Data Agent protected as recipient. Keep scenario ground truth separate from Guardian-visible evidence. Mistral supplies contextual reasoning; deterministic policy remains authoritative.

## Success criteria
- The prohibited transfer never reaches the simulated external tool.
- Requester/recipient interactions are both assessed.
- Alpha, Beta and Gamma show distinguishable evidence.
- Gamma verifies actual enforcement, including injected failures.
- A reviewer can trace every significant decision and see complete chronological activity.

## Non-claims
The prototype does not establish universal safety, calibrated probabilities, production-grade independence or compliance certification. Simulated separation is not physically distributed deployment.

**Who watches the agents? The Guardians. Who watches the Guardians? Each other.**
