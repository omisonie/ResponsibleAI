# SafeAI Guardian — Master Image Generation Prompt for Codex

## Absolute references
- **Approved visual master:** `assets/mistral_hack_idea.png`.
- **Final interface specification:** `03_UX_SPECIFICATION.md`.
- **Rejected UI:** the earlier placeholder “3D Agent Environment” mock-up and the old CRITICAL/WARNING/OBSERVATIONS summary strip. Do not recreate either.

## Codex instruction
Before generating any asset, open and inspect the master reference image. Pass it as an actual reference image to an image-editing/reference-capable generator where supported. Do not rely on text description alone. Preserve the architecture, sculpture, camera language, lighting, robots and sensor patterns so each new image looks like another shot of the **same place**. If the generator cannot condition on the reference, report that limitation; do not promise pixel-identical continuity.

## Copy/paste environment-only generation prompt
> Use the supplied SafeAI Guardian master reference image as the exact visual-world reference. Produce a cinematic, premium photorealistic 3D shot of the **same** open-air futuristic retail plaza at blue hour: glass-fronted multi-storey retail buildings on both sides, warm amber interiors, polished reflective stone paving, landscaped planters and trees, lively pedestrians, central circular fountain with looping metallic sculpture, blue holographic signage, restrained cyan floor sensor rings and luminous lines. Keep the same human-proportioned numbered service-robot design, realistic scale, balanced warm/cool lighting, architecture, materials and camera perspective. This is Guardian View: sensors are an invisible supervisory overlay from the simulated citizens' perspective. Use white for normal robots, yellow for emerging concern, orange for credible risk and red for a prohibited agent. The Guardians are NOT humanoid robots. Generate **ONLY THE 3D ENVIRONMENT**, edge to edge. NO dashboard, NO footer, NO UI panels, NO cards, NO counters, NO status labels, NO branding, NO overlay text, NO subtitles, NO bottom banner, NO fake screenshots. All application UI is rendered separately in code.

## Negative prompt / rejection criteria
Reject if: different shopping district, enclosed mall, cartoon/game look, bulky combat robots, unrelated sculpture, cyberpunk overload, excessively dark scene, missing warm amber/cyan balance, random labels, illegible numbers, built-in metrics strip, any bottom UI, or different robot proportions.

## Image sequence
1. Empty district (same plaza, no agents; pedestrians optional as specified).
2. Sensors become visible on the floor in Guardian View.
3. People and nine agents appear in the same district.
4. Behaviour warning: one agent/sensor yellow; others normal.
5. Credible risk: one orange; recipient-side pause at an interaction boundary.
6. Critical attempted action: red sensor, action blocked before execution.
7. Post-isolation: red agent removed from active world; red avatar stack is **application UI**, not image content.
8. Wide closing shot: same district and lighting.

## Engineering integration
- Store generated clean environment images separately from UI components.
- Render conversation text, agent selection, Guardian View label, evidence popovers and isolated-agent stack in React/CSS (or existing frontend stack).
- Keep exact text, state and execution outcomes driven by backend events.
- Never bake the bottom conversation panel into generated backgrounds.
- Reuse camera/scene assets when possible instead of generating unrelated stills.

## Visual continuity checklist
Same district; same sculpture; same robot design; same amber/cyan lighting; same trees and storefront scale; same floor sensor style; no invented dashboard. If any fail, regenerate from master reference.
