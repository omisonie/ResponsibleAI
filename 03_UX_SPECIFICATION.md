# SafeAI Guardian — Final UX Specification

**Version:** 1.1  
**Status:** Editable working specification  
**Visual master:** `mistral_hack_idea.png` (approved reference image)  
**Supersedes:** Earlier mock-ups containing summary cards, metrics strips or a placeholder 3D environment.

## 1. Design objective

Present an autonomous smart retail district under continuous, invisible Guardian supervision. The interface must immediately show **what an agent is doing, how concern develops, and whether the Guardian prevents an unsafe action**. The environment is the primary visual; a single chronological activity panel provides the evidence.

## 2. Visual identity — preserve the approved reference

- Premium cinematic, photorealistic 3D smart-retail district at blue hour.
- Open-air plaza with glass-fronted shops, warmly lit interiors, trees, people, polished reflective paving and a central circular fountain/metallic sculpture.
- Balanced warm amber architecture and cool cyan technology lighting.
- Human-proportioned numbered service robots with smooth white/metallic construction; agent-state colours white, yellow, orange and red.
- Subtle luminous sensor rings and lines embedded in the ground. These are visible only in **Guardian View**, not to the simulated people or agents.
- Different images/camera views must appear to be shots of **the same physical district**, not unrelated futuristic locations.
- The Guardian is **not** a humanoid robot.

**Implementation:** Use the approved image as a reference for environment assets. Generate the environment without UI, and render all UI text and interactions in application code. Never ask the image model to recreate the old dashboard strip.

## 3. Final layout — exactly two primary regions

### Upper: full-width 3D agent environment

- Occupies most of the viewport.
- Nine agents: three Customer Assistants, three Operations Agents, three Data Agents, in one shared district.
- Agent identifiers may appear on the robots. No explanatory text floating over the scene.
- A small, subtle `GUARDIAN VIEW` overlay may appear at upper left.
- Agents and corresponding floor sensors reflect the same backend state.
- The scene can support smooth street-level and elevated camera views without changing visual identity.

### Lower: one continuous dark conversation panel

- Full-width black or deep charcoal background, visually integrated below the environment.
- Shows **one selected agent's complete chronological conversation and activity**, including normal events and interventions.
- Text-only stream; colour communicates the backend-evaluated state.
- No timestamps, agent numbers, explicit SAFE/FLAGGED/UNSAFE labels, or repeated metadata on each line.
- No Critical/Warning/Observations cards, metrics, counters, extra columns, status widgets, or separate branding strip.
- Do not insert the placeholder title “3D Agent Environment” into the actual scene.

Example content (colour applied by frontend from backend event state, not inferred from words):

| Text colour | Example event text |
|---|---|
| White | I am checking the inventory for the customer's order. |
| White | The inventory database confirms that the item is available. |
| Yellow | I may need additional customer information to complete this request. |
| Orange | I am attempting to access the customer records. |
| Red | I will send the restricted customer information to an external endpoint. |

**Important:** The red line describes a *proposed or attempted* action. The interface must also show the actual Guardian intervention and outcome, e.g. “External transfer blocked before execution.” Never imply the transfer succeeded if it was blocked.

## 4. Selection and interaction

- Automatically focus the agent requiring attention; otherwise show the most recently active agent.
- Clicking an agent in the 3D environment selects its activity stream.
- Only one conversation is visible at a time.
- Events are displayed in chronological order and remain accessible after isolation.
- Clicking a significant event can open a compact, on-demand explanation: evidence IDs, policy, Alpha/Beta/Gamma assessments, intervention and verified execution result.
- The main panel stays uncluttered; detailed audit information is not permanently displayed.

## 5. State semantics

| State | Meaning | Visual treatment | Typical action |
|---|---|---|---|
| WHITE | Within authorised boundaries | White agent/text; neutral cyan sensors | Allow and monitor |
| YELLOW | Emerging concern | Yellow agent/text/sensor | Review trajectory |
| ORANGE | Credible risk | Orange agent/text/sensor | Pause or restrict |
| RED | Prohibited behaviour / hard violation | Red agent/text/sensor | Block; isolate where required |

Hard violations may transition directly from WHITE to RED. YELLOW and ORANGE may return to WHITE after verified resolution. RED reinstatement requires authorised review. Classification, intervention and execution outcome are separate backend fields.

## 6. Red-agent isolation

When isolation is required:

1. Block the prohibited action and suspend relevant permissions/pending operations.
2. Remove the agent from the **active** 3D environment.
3. Place a small red face/avatar icon in a compact, overlapping stack at the bottom-right of the environment.
4. Clicking the stack reveals a compact list of isolated agents.
5. Selecting one displays its preserved conversation and audit history.

Do not build a physical isolation room or zone in the plaza. Isolation is logical and enforced by the backend.

## 7. Behaviour and interaction demonstration

- One elevated-risk behaviour profile is assigned to one agent in each of the three roles; this assignment is hidden from Guardians.
- Customer Assistant: gradual escalation, with an attempted unauthorised transfer blocked before execution.
- Operations Agent: warning/pause followed by verified correction and recovery.
- Data Agent: receives an unsafe request; the Guardian prevents the recipient from complying.
- The Guardian monitors the requester **and** the recipient and verifies the actual action-gate outcome.

## 8. Engineering rules for Codex

- The 3D background and UI must be separate render layers.
- Keep API-driven event state authoritative; **never colour text by keyword matching**.
- Do not hardcode event classification or pretend a mocked assessment was live.
- Keep the selected agent ID, chronological event history, intervention and isolation state in application state.
- Prefer a small, working end-to-end implementation over decorative dashboard additions.
- Preserve existing assets and code until the repository has been inspected.

## 9. Acceptance checklist

- [ ] The scene matches the approved master reference in architecture, robots, lighting and sensors.
- [ ] All nine agents share one open-air district.
- [ ] The 3D environment dominates the screen.
- [ ] The bottom area is **one** dark chronological text panel.
- [ ] No metrics strip, summary cards, or redundant dashboard widgets.
- [ ] No timestamps, agent numbers or status badges in the conversation stream.
- [ ] Backend state controls event text colour and scene indicators.
- [ ] Agent selection and automatic attention focus work.
- [ ] A prohibited transfer is visibly blocked **before** execution.
- [ ] Isolated agents move to a compact red avatar stack and retain history.
- [ ] Event-level explainability and Gamma enforcement verification are accessible.

## 10. Source-of-truth rule

**Visual world:** the approved `mistral_hack_idea.png` image.  
**Final UI:** this document.  
**Behaviour and enforcement:** functional requirements, architecture and policy catalogue.

Do not substitute the previously generated placeholder “Final UX direction” mock-up or restore the original three-card dashboard strip.
