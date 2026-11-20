# SafeAI Guardian — Document Index

## Files
| File | Purpose |
|---|---|
| `README.md` | Project overview and tagline |
| `01_PRODUCT_VISION.md` | Why the product exists; principles and scope |
| `02_DIFFERENTIATION.md` | Novelty, comparisons and honest claims |
| `03_UX_SPECIFICATION.md` | **Final agreed UI**, superseding earlier mock-ups |
| `04_FUNCTIONAL_REQUIREMENTS.md` | Functional acceptance criteria |
| `05_TECHNICAL_ARCHITECTURE.md` | Components, gate, Mistral and assurance |
| `06_IMPLEMENTATION_AND_TESTING.md` | Build sequence, tests, demo and definition of done |
| `07_PROJECT_DECISIONS.md` | Explicitly agreed decisions |
| `AGENTS.md` | Codex project instructions |
| `policies/safeai.md` | Initial versioned policy catalogue |
| `SAFEAI_IMAGE_GENERATION_PROMPT.md` | Master visual reference prompt for Codex |
| `assets/mistral_hack_idea.png` | Approved visual master image |

## Source-of-truth order
Approved decisions → functional requirements and safety constraints → technical architecture/policy catalogue → **final UX specification** → implementation guidance. For visual identity, the master image is authoritative; for UI composition, `03_UX_SPECIFICATION.md` is authoritative. Flag contradictions instead of silently changing decisions.

## Codex reading order
`AGENTS.md` → `07_PROJECT_DECISIONS.md` → `04_FUNCTIONAL_REQUIREMENTS.md` → `05_TECHNICAL_ARCHITECTURE.md` → `policies/safeai.md` → `03_UX_SPECIFICATION.md` → `SAFEAI_IMAGE_GENERATION_PROMPT.md` → `06_IMPLEMENTATION_AND_TESTING.md`.

## Key prohibitions
No old three-card metrics strip. No placeholder 3D environment. No LLM override of deterministic denials. No ungated protected actions. No claim of live model use when mocked. No majority voting of identical Guardian calls.
