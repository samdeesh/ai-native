# Wake-Up-Repo: Owner Interview Questions

Ask only the questions below that were **not** already answered during Step 1 (Read-Only Discovery). Present them together in a single concise message.

1. **Repo purpose & primary audience:** In 1–2 sentences, what does this repo do and who owns/contributes to it?
2. **Fastest verification commands:** Which single CLI command should an agent run after every edit (typecheck/lint/scoped test), and which full command before opening a PR?
3. **High-blast-radius paths (`CODEOWNERS`):** Which directories or files (e.g., `auth/`, `billing/`, `infra/`, migrations, API schemas) should require explicit human approval before an agent modifies them?
4. **Hard boundaries & banned patterns (`SECURITY.md` / `AGENTS.md`):** Are there any forbidden libraries, legacy patterns not to mimic, or non-obvious workarounds agents must not "clean up"?
5. **Branching & PR contract (`CONTRIBUTING.md`):** What branch naming, commit style, and PR evidence (test output, screenshots, ADR links) do you expect?
6. **Supporting docs:** Do you have 1–5 existing docs, ADRs, or runbooks (paths, links, or pasted notes) we should distill into `docs/adr/` or path-scoped rules?
