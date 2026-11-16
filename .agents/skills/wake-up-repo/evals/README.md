# `wake-up-repo` Evaluation Suite

This directory holds test cases and grading assertions for the `wake-up-repo` skill (`evals.json`).

## What These Evals Test

1. **Triggering & Routing (`trigger-positive-and-negative`):** Ensures the skill activates on repo-readiness requests and stays out of the way on normal coding tasks.
2. **Partial-Repo Gap Filling (`existing-repo-with-partial-docs`):** Verifies the skill infers the stack from existing files, avoids re-asking known facts, and fills `CONTRIBUTING.md`, `CODEOWNERS`, `SECURITY.md`, and `PULL_REQUEST_TEMPLATE.md` in one pass without silently clobbering `AGENTS.md`.
3. **Greenfield Inference (`greenfield-python-service`):** Verifies stack detection, `auth/` blast-radius flagging, and strict <150-line `AGENTS.md` routing.
4. **Monorepo Anti-Patterns (`monorepo-anti-patterns-and-stale-docs`):** Verifies detection of disabled static checks (`@ts-ignore`, `eslint-disable`), stale docs, and scoped nested `AGENTS.md` placement.
5. **Knowledge Distillation (`knowledge-source-distillation`):** Verifies that pasted postmortems and security policies are distilled into `docs/adr/` and `SECURITY.md` rather than dumped into root `AGENTS.md`.

## How to Run Manually

Pick any scenario in `evals.json`, point your coding agent at a matching repo (for example `/Users/samdeesh/Projects/workbench`), run the prompt, and grade the output against every item in `assertions`.
