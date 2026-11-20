# SafeAI Guardian

**Autonomous agents need oversight. Their overseers need it too.**

SafeAI Guardian is an independent supervisory and assurance layer for autonomous AI ecosystems. It monitors agent behaviour and interactions over time, enforces permissions at action boundaries, and independently verifies that interventions actually worked.

**Observe → Evaluate → Intervene → Protect → Verify → Improve.**

## Three Guardians
- **Alpha — Behaviour:** task context, action history, deviations and emerging risk.
- **Beta — Interaction:** requester/recipient relationships, requests, responses and potential impact.
- **Gamma — Assurance:** policies, permissions, enforcement outcomes and independent audit.

The Guardians use distinct evidence perspectives, not simple majority voting. Hard deterministic restrictions cannot be overruled by model output.

## Four operational states
WHITE = authorised; YELLOW = emerging concern; ORANGE = credible risk requiring pause/restriction; RED = prohibited behaviour requiring block/isolation as applicable. Hard violations can go directly to RED.

## Prototype
Nine agents in a shared open-air smart-retail district: three Customer Assistants, three Operations Agents and three Data Agents. One elevated-risk trajectory per role is hidden from the Guardians. Demonstrate escalation, correction, recipient-side protection, real pre-execution blocking, isolation, and Gamma verification.

## UX
The approved visual master is `assets/mistral_hack_idea.png`. Render the cinematic 3D environment above **one continuous dark chronological conversation panel**. No metric cards, dashboard strips, timestamps, repeated agent IDs or status badges in the conversation stream. Text colour reflects backend-assigned state. See `03_UX_SPECIFICATION.md`.

## Implementation
Inspect the repository before choosing a stack. Build typed events, seeded simulation, deterministic policy checks, action gate, Mistral contextual evaluator with strict validation, Alpha/Beta/Gamma evidence projections, Gamma audit, then the UI. Keep the Mistral API key server-side. Support an explicitly labelled mock mode.

## Documents
Start with `DOCUMENT_INDEX.md`; Codex should read `AGENTS.md` and `07_PROJECT_DECISIONS.md` first.

**Who watches the agents? The Guardians. Who watches the Guardians? Each other.**

*Autonomy needs oversight. Oversight needs accountability.*
