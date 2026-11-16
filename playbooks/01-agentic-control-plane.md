# Playbook 01: The Agentic Control Plane

*Distilled from "The Dead Files Wake Up: Turning Legacy Repo Docs into an Agentic Control Plane".*

Autonomous coding agents have zero institutional memory. When pointed at an existing codebase, root-level governance files become the primary ground truth loaded into the context window. Stale documentation doesn't just confuse new hires—it misdirects agentic execution loops at scale.

---

## 1. Wake Up Native Git Files First

Instead of inventing a parallel AI-only documentation system, turn standard Git/GitHub files into deterministic contracts read by both humans and agents:

| File | Agentic Control Plane Role | What Belongs Inside |
| :--- | :--- | :--- |
| `README.md` | **Topology & Entry-Point Map** | Directory tree, runtime prerequisites, service boundaries. |
| `CONTRIBUTING.md` | **Branching & Verification Contract** | Branch naming, commit format, exact CLI commands (`lint`, `typecheck`, `test`). |
| `.github/CODEOWNERS` | **Blast-Radius & Escalation Gate** | High-risk paths (`auth/`, `billing/`, `infra/`, schemas) requiring human sign-off. |
| `SECURITY.md` | **Hard Guardrails & Secret Hygiene** | Banned libraries, forbidden APIs, `.env` and secret handling rules. |
| `.github/PULL_REQUEST_TEMPLATE.md` | **Structured Handoff Schema** | Required evidence: test logs, typecheck output, linked ADRs. |
| `docs/adr/` | **Anti-Regression Memory** | Short Architecture Decision Records explaining *why* non-obvious patterns exist. |

---

## 2. Three Layers of Progressive Disclosure

Never treat `AGENTS.md` as an encyclopedia. Keep the root `AGENTS.md` under **100–150 lines** using three layers:

1. **Root `AGENTS.md` (Always loaded, ultra-lean router):** Exact verification commands, hard prohibitions, and pointers to where deeper rules live.
2. **Git standards + path-scoped rules (Loaded by location):** Repo-wide contracts in `CONTRIBUTING.md` and `SECURITY.md`; language or framework rules in nested `AGENTS.md` files (such as `packages/web-ui/AGENTS.md`) so frontend rules never pollute backend workers.
3. **Skills (Loaded on demand):** Repeatable multi-step workflows (`story-implementation`, `test-authoring`, `pr-readiness`, `schema-migration`) stored in `.agents/skills/<name>/SKILL.md`.

---

## 3. Six-Point Readiness Audit

1. Root `AGENTS.md` is under 150 lines and leads with exact CLI verification commands.
2. `CONTRIBUTING.md` specifies concrete branching and commit rules.
3. `.github/CODEOWNERS` protects high-blast-radius directories.
4. Nested `AGENTS.md` or path-scoped rules isolate frontend, backend, and infra conventions.
5. Core workflows live in `.agents/skills/` rather than the root prompt.
6. Stale docs are pruned or archived so agents never ingest conflicting legacy instructions.
