# AGENTS.md

## Verification Commands
- Validate Markdown links and repo paths: confirm every path referenced in `README.md`, `playbooks/`, and `.agents/skills/` exists on disk.
- Validate skill frontmatter: every `SKILL.md` under `.agents/skills/<name>/` must define `name` (matching its folder) and `description` in YAML frontmatter.
- Check git diff before committing: `git status` and `git diff --stat`

## Hard Boundaries
- Keep this root `AGENTS.md` under 100 lines. Never paste full playbook prose or skill instructions here.
- Keep playbooks practical and concise; avoid duplicating rules across `AGENTS.md`, `CONTRIBUTING.md`, and `playbooks/`.
- Never fabricate CLI commands, file paths, or external URLs in templates or playbooks.

## Where Rules Live
- Branching, commits, and PR expectations: read `CONTRIBUTING.md`
- Control plane architecture & progressive disclosure: read `playbooks/01-agentic-control-plane.md`
- Static analysis & deterministic verification design: read `playbooks/02-static-analysis-and-verification.md`
- Repo-onboarding workflow: load `.agents/skills/wake-up-repo/SKILL.md`
