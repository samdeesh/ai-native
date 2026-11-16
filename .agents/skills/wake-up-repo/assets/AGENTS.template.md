# AGENTS.md

## Verification Commands
- Install: `<install-command>`
- Fast check (run after edits): `<typecheck-or-lint-command>`
- Scoped tests: `<scoped-test-command>`
- Full pre-PR suite: `<full-test-and-build-command>`

## Hard Boundaries
- Never modify `<protected-paths-from-CODEOWNERS>` without explicit human approval.
- Never weaken assertions, skip tests, or disable linter/typecheck rules to get a green build.
- Never commit secrets, tokens, or `.env` files.
- Do not refactor `<non-obvious-workarounds>` without checking `docs/adr/` first.

## Where Rules Live
- Project topology & setup: read `README.md`
- Branching, commit conventions, and PR workflow: read `CONTRIBUTING.md`
- Security rules & banned patterns: read `SECURITY.md`
- Architectural trade-offs: check `docs/adr/`
- Repeatable workflows: load matching skills in `.agents/skills/`
