---
name: wake-up-repo
description: Turn any existing or new repository into an agent-ready control plane. Deep-scans the codebase to infer tech stack, patterns, anti-patterns, and governance gaps; interviews the owner only on ambiguities, external MCPs (Confluence, Linear, Jira), and key knowledge sources; and fills AGENTS.md, CONTRIBUTING.md, CODEOWNERS, SECURITY.md, inline docs on critical paths, and starter skills in one pass. Use when the user asks to wake up a repo, make a repository AI-ready or agent-ready, scaffold AGENTS.md, CONTRIBUTING.md, CODEOWNERS, or set up the AI-native playbook files on any codebase.
---

# Wake Up Repo

Turn any repository into an agent-ready control plane in one cohesive pass by inferring stack, patterns, and anti-patterns from code, resolving only real ambiguities (and optional MCP knowledge sources) with the owner, and filling all governance and inline-doc gaps without bloating `AGENTS.md`.

## When to Use

- The user asks to wake up a repository or make a repo ready for AI coding agents.
- The user wants to audit and fill gaps across `AGENTS.md`, `CONTRIBUTING.md`, `.github/CODEOWNERS`, `SECURITY.md`, `.github/PULL_REQUEST_TEMPLATE.md`, inline critical-path docs, or `.agents/skills/`.
- The user wants an agent to infer codebase patterns/anti-patterns and distill external docs or MCP sources into a lean control plane.

## Workflow

### Step 1: Deep Read-Only Scan & Inference (Before Asking Anything)

Inspect the repository thoroughly before speaking to the owner:

1. **Tech stack & tooling:** Read manifests (`package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, `Makefile`, `tsconfig.json`, `.github/workflows/*`) to infer languages, frameworks, package manager, build/test commands, and static-analysis tools (`tsc`, `cargo check`/`clippy`, `ruff`, `eslint`, `pyright`).
2. **Patterns & best practices:** Sample key source directories (`src/`, `packages/`, `apps/`, tests) to infer module boundaries, naming conventions, error-handling patterns, and test structure.
3. **Anti-patterns & critical paths:** Flag concrete hazards (disabled lint/typecheck rules, missing CI checks, inconsistent patterns, stale/conflicting docs) and identify high-blast-radius or undocumented critical paths (`auth/`, `billing/`, `infra/`, core pipelines, schemas).
4. **Governance gap audit:** Check `README.md`, `CONTRIBUTING.md`, `SECURITY.md`, `.github/CODEOWNERS`, `.github/PULL_REQUEST_TEMPLATE.md`, `AGENTS.md`, `CLAUDE.md`, `docs/adr/`, and `.agents/skills/`. Classify each as *present & solid*, *stale/incomplete*, or *missing*.

### Step 2: Surface Findings & Ask Only About Ambiguities + Knowledge Sources

Read `references/interview-questions.md`. Present a concise summary (4-6 bullets) of inferred stack, patterns, anti-patterns, critical paths, and governance gaps, then ask **only** what code cannot answer:

1. **Corrections & ambiguities:** Confirm or correct inferred patterns, legacy anti-patterns agents must not mimic, and non-obvious workarounds agents must not "clean up".
2. **Ownership & blast-radius (`CODEOWNERS`):** Confirm which high-risk paths require human sign-off and who owns them (GitHub handles/teams).
3. **Verification & branching gaps:** Only if missing or ambiguous in CI/manifests—confirm fast edit-time check, full pre-PR command, branch naming, and commit style.
4. **Docs & external MCP knowledge sources:** Ask for 1-5 high-signal docs/ADRs/runbooks, and **if the user has MCPs connected for external sources (Confluence, Linear, Jira, Notion, etc.)**, prompt them to include the specific spaces, projects, or tickets that hold key architecture decisions or invariants.

### Step 3: Ingest Knowledge Sources (Local Docs + External MCPs)

- Pull relevant context from any user-specified local docs or connected MCP sources (Confluence pages, Linear/Jira specs, incident runbooks).
- Distill architectural decisions and "why" context into short records under `docs/adr/`.
- Extract security/secret constraints into `SECURITY.md` and branching/PR rules into `CONTRIBUTING.md`.
- Never dump raw doc or ticket prose into root `AGENTS.md`.

### Step 4: Single-Pass Gap Fill (Control Plane Files + Critical-Path Inline Docs)

Read `references/control-plane-rubric.md` and `assets/AGENTS.template.md`. Show a concise file-by-file plan (create / update / leave untouched) and fill all gaps in one pass:

- **`AGENTS.md`** (strictly under 100-150 lines): fast scoped check + full pre-PR command, hard boundaries (including inferred anti-patterns to avoid), and pointers to native Git files and skills.
- **`CONTRIBUTING.md`**: fill missing or incomplete branching, commit, and verification contracts.
- **`.github/CODEOWNERS`**: create or patch ownership rules for inferred high-blast-radius paths.
- **`SECURITY.md` & `.github/PULL_REQUEST_TEMPLATE.md`**: add or update secret hygiene, banned patterns, and PR evidence checklists where missing.
- **Inline docs on critical paths:** Propose and add concise module-header comments, docstrings, or invariants directly in high-risk/non-obvious code paths (without cluttering trivial code), plus nested `AGENTS.md` where sub-stacks differ.
- **Starter `.agents/skills/`**: add repeatable workflow skills (`story-implementation`, `test-authoring`, `pr-readiness`) if helpful.

### Step 5: Dry-Run Verification

1. Verify every file path, handle, and CLI script referenced across `AGENTS.md`, `CONTRIBUTING.md`, and `CODEOWNERS` resolves cleanly.
2. Run the discovered fast static-analysis/typecheck/lint command (or confirm validity if dependencies are not installed) and report the exact result.

## Gotchas

- Never ask the owner for stack details, scripts, or directory layouts already visible in the repo.
- Never duplicate branching, commit, or security rules across `AGENTS.md`, `CONTRIBUTING.md`, and `SECURITY.md`; keep `AGENTS.md` as a pointer.
- Never overwrite existing governance files or source files silently—always present the plan first.
