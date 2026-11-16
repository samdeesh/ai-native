# Control Plane Placement Rubric

Use this rubric to keep root `AGENTS.md` under 100–150 lines and avoid duplicating rules across files.

## Where Each Rule Belongs

- **Root `AGENTS.md`** — Always loaded. Keep it to:
  1. Exact CLI verification commands (fast scoped check + full pre-PR check).
  2. Hard boundaries ("never" rules: protected paths, never skip tests/linters, no secrets).
  3. Pointers to `CONTRIBUTING.md`, `SECURITY.md`, `.github/CODEOWNERS`, `docs/adr/`, and `.agents/skills/`.
- **`README.md`** — High-level system topology, runtime prerequisites, and local setup.
- **`CONTRIBUTING.md`** — Branch naming, commit format, and PR verification expectations.
- **`.github/CODEOWNERS`** — Ownership and mandatory human-review gates for high-blast-radius paths.
- **`SECURITY.md`** — Secret hygiene, banned APIs/libraries, and vulnerability reporting.
- **`docs/adr/`** — Short Architecture Decision Records explaining *why* non-obvious patterns or workarounds exist (anti-regression memory).
- **Nested `AGENTS.md`** — Stack-specific rules scoped to a subdirectory (e.g. `frontend/AGENTS.md` vs. `services/api/AGENTS.md`).
- **`.agents/skills/<name>/SKILL.md`** — Step-by-step repeatable workflows (`story-implementation`, `test-authoring`, `pr-readiness`, `schema-migration`).

## 6-Point Readiness Check

Before finishing Step 5, confirm:
1. Root `AGENTS.md` is under 150 lines and leads with exact CLI commands.
2. `CONTRIBUTING.md` has concrete branching/commit/test rules.
3. `.github/CODEOWNERS` covers high-blast-radius paths (if any exist).
4. Stack-specific rules are scoped to subdirectories rather than polluting the root.
5. Repeatable multi-step workflows live in `.agents/skills/`, not `AGENTS.md`.
6. Every file path and command mentioned in `AGENTS.md` actually exists.
