# 07 — Project Decisions (agreed baseline)

| ID | Decision | Reason |
|---|---|---|
| D01 | SafeAI Guardian: “Autonomous agents need oversight. Their overseers need it too.” | Oversight of both agents and supervisors |
| D02 | Observe → Evaluate → Intervene → Protect → Verify → Improve | Full protection lifecycle |
| D03 | Alpha = Behaviour, Beta = Interaction, Gamma = Assurance | Distinct evidence and responsibility |
| D04 | No majority voting; hard policy always prevails | Two permissive opinions cannot overrule security |
| D05 | WHITE/YELLOW/ORANGE/RED; direct WHITE→RED possible | Appropriate escalation without artificial stages |
| D06 | Monitor trajectories, not isolated text only | Risks emerge over sequences |
| D07 | Protect requester and recipient | Prevent proxy bypass and unsafe compliance |
| D08 | Enforce at protected action boundary | Alerts alone do not prevent execution |
| D09 | Gamma verifies actual enforcement | Supervisor must be accountable |
| D10 | Mistral reasons contextually; deterministic policy controls permissions | Avoid model-only security |
| D11 | No fine-tuning initially | Policy retrieval and structured validation first |
| D12 | Unknown behaviour flagged and reviewed before policy activation | Controlled catalogue evolution |
| D13 | Nine agents: 3 Customer, 3 Operations, 3 Data | Balanced demo |
| D14 | One hidden elevated-risk profile per role; fixed seed | Fair, repeatable test |
| D15 | One open-air smart retail district | Cross-agent interaction in a shared world |
| D16 | `assets/mistral_hack_idea.png` is approved visual master | Same city, robots, lighting, sensors |
| D17 | Guardian is invisible; floor sensors visible only in Guardian View | Supervisory rather than humanoid Guardian |
| D18 | Exactly two primary UI regions: 3D world above one black conversation panel | No extra dashboards |
| D19 | No summary metrics/cards/branding strip in bottom panel | Explicitly rejected old design |
| D20 | Conversation is text only; no timestamps, agent numbers or state badges | Colour tells the story |
| D21 | Backend controls white/yellow/orange/red text colours | Not frontend keyword inference |
| D22 | Auto-focus agent needing attention; click to select another | One conversation at a time |
| D23 | RED isolation removes agent from active scene; red avatar stack bottom-right | Logical isolation, retained audit |
| D24 | Generated background and application UI are separate layers | Exact interface control |
| D25 | Inspect repo and build core gate/audit before 3D polish | Technical credibility |
| D26 | Mock/live Mistral mode clearly labelled | Honest demonstration |

## Change control
When revising an agreed decision, record reason, impact and affected files; do not silently change the product or restore the rejected dashboard.
