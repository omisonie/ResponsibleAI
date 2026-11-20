# SafeAI Guardian — Codex Instructions

## Read first
`README.md`, `07_PROJECT_DECISIONS.md`, `04_FUNCTIONAL_REQUIREMENTS.md`, `05_TECHNICAL_ARCHITECTURE.md`, `03_UX_SPECIFICATION.md`, `policies/safeai.md`, `SAFEAI_IMAGE_GENERATION_PROMPT.md`.

## Workflow
1. Inspect existing repository, framework, assets and tests before edits.
2. Propose minimal changes; preserve working functionality.
3. Implement typed events and seeded nine-agent simulation.
4. Implement deterministic policies and mandatory action gate **before** advanced visuals.
5. Add Mistral contextual evaluation with strict schema, evidence validation, timeout and explicitly labelled mock mode.
6. Implement Alpha behaviour, Beta interaction, Gamma assurance with distinct evidence projections. No simple majority voting.
7. Implement recipient-side protection, pause/block/isolation and Gamma post-action verification.
8. Build UI as two primary regions: approved-style 3D environment and one continuous dark chronological conversation panel.
9. Run tests, including enforcement failure injection.

## Hard invariants
- Protected tool calls must never bypass the gate.
- A deterministic denial cannot be overridden by an LLM.
- A BLOCK must mean the protected tool was **not invoked**.
- Gamma must verify actual execution outcomes, not merely the decision text.
- Ground truth of risky profiles is never passed to Guardians.
- Classification, decision, intervention and execution outcome are distinct.
- API keys stay server-side; no secrets committed.
- Unknown model output does not mean ALLOW.
- Do not pretend a mock model assessment was live.

## UI non-negotiables
- `assets/mistral_hack_idea.png` is the visual master for the world.
- Do not use placeholder “3D Agent Environment” art or original metrics-card strip.
- No top metrics strip; no CRITICAL/WARNING/OBSERVATIONS cards.
- One black bottom conversation panel; full chronological text including ordinary activity.
- No timestamps, agent IDs or SAFE/FLAGGED/UNSAFE labels in that stream.
- Backend-assigned white/yellow/orange/red colours; no frontend keyword heuristics.
- Auto-select agent requiring attention; click agent to select.
- RED isolated agents leave active 3D scene and appear in bottom-right avatar stack; retain history.
- Keep 3D imagery and live UI elements separate.

## Acceptance
Test normal authorised actions, escalation, recipient hold, unauthorised transfer (tool count zero), model failure, malformed output, invented evidence, policy disagreement, gate bypass and Gamma detection of an intentionally failed block. Report what is implemented versus simulated.
