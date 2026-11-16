# Contributing to AI-Native Playbook

## Branching & Commits
- Branch naming: `feat/<topic>` for new skills or playbooks, `fix/<topic>` for corrections, `docs/<topic>` for editorial updates.
- Commit style: concise imperative subject line (e.g., `feat(skills): add wake-up-repo onboarding skill`).

## Verification Before Opening a PR
1. Verify all file paths referenced in `AGENTS.md`, `README.md`, and `SKILL.md` exist.
2. Verify any new skill under `.agents/skills/<skill-name>/SKILL.md` has valid YAML frontmatter (`name` and `description`) and keeps detailed checklists in `references/` or `assets/` rather than bloating `SKILL.md`.
3. Keep root `AGENTS.md` under 100 lines.
