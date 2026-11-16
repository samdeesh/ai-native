# Playbook 02: Static Analysis & Deterministic Verification

*Distilled from "Why Static Analysis, Rust, and TypeScript Win With AI Agents".*

AI coding agents rarely fail because they type too slowly. They fail when their environment lacks fast, deterministic feedback to reject bad assumptions before runtime.

---

## 1. Make the Compiler & Linter Your Enforcement Engine

Static analysis (type checkers, compilers, linters) inspects the AST and type graph without executing a single line of code, giving agents exact `file:line` diagnostics they can self-correct in seconds.

- **TypeScript (`strict: true`):** Connects database queries, API handlers, and UI components in one type graph. Wire `tsc --noEmit` (or fast native checkers) into `AGENTS.md` so agents run it after every edit.
- **Rust (`rustc` + `clippy`):** Enforces ownership, lifetimes, and exhaustive `Option`/`Result` handling at compile time. Treat `clippy` warnings as errors in CI.
- **Dynamic stacks (Python / plain JS):** Compensate with strict type checking (`pyright` / `mypy`), schema validators (`pydantic` / `zod`) at API and content boundaries, and fast linters (`ruff` / `eslint`).

---

## 2. Wire Fast Loops Into `AGENTS.md`

Always distinguish **fast edit-time checks** from **full CI suites** in `AGENTS.md` so agents don't skip verification due to slow feedback:

1. **Single-file / scoped check** (seconds): typecheck + targeted unit test command (`pnpm test -- <path>`).
2. **Full verification gate** (before PR): full typecheck, linter, and test suite.
3. **Hard rule:** Never weaken assertions, skip tests (`it.skip`), or disable linter rules to achieve a green build.

---

## 3. Where Static Analysis Stops

A green `tsc` or `cargo clippy` run proves types align and memory is safe—not that pricing math or authorization checks match business intent. Reserve unit/integration tests and human review (`.github/CODEOWNERS`) for business logic and architectural boundaries.
