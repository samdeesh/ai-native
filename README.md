# AI-Native Engineering Playbook

An operational playbook and installable skill kit for turning any repository into an **agent-ready control plane**, grounded in the engineering articles on Foundry.blog.

Instead of stuffing 500 lines of rules into a single prompt file, this repo pairs:
1. **Playbooks** (`playbooks/`) — concise, opinionated architecture for waking up native Git files, keeping `AGENTS.md` lean, and wiring fast static-analysis loops.
2. **Installable Skills** (`.agents/skills/`) — repeatable workflows any repo owner can run to interview themselves, ingest existing docs, and generate a verified control plane in minutes.

---

## Repository Topology

```text
.
├── AGENTS.md                                      # Lean control-plane router for this repo
├── CONTRIBUTING.md                                # Branching, commit, and verification contract
├── README.md                                      # You are here
├── playbooks/
│   ├── 01-agentic-control-plane.md                # Native Git files + 3-layer progressive disclosure
│   └── 02-static-analysis-and-verification.md     # Compiler, typecheck, and lint feedback loops
└── .agents/
    └── skills/
        └── wake-up-repo/                          # 5-step repo-onboarding skill
            ├── SKILL.md
            ├── references/
            │   ├── interview-questions.md
            │   └── control-plane-rubric.md
            └── assets/
                └── AGENTS.template.md
```

---

## Quickstart: Wake Up Any Repository

Copy `.agents/skills/wake-up-repo/` into your target repository (or install it with your agent CLI) and ask your coding agent:

> "Run `wake-up-repo` on this repository."

The skill will:
1. **Auto-scan** your codebase, package manifests, CI workflows, and existing docs.
2. **Ask 6 targeted questions** about invariants, blast-radius paths, and verification commands.
3. **Ingest supporting docs** (architecture notes, runbooks, ADRs) you provide.
4. **Generate/update** a lean `AGENTS.md` router, native Git contracts (`CONTRIBUTING.md`, `.github/CODEOWNERS`, `SECURITY.md`), and starter `.agents/skills/` after showing you a diff plan.
5. **Verify** that every referenced CLI command and path resolves cleanly.

---

## Contributing & License

Contributions are welcome! Whether it's a new playbook chapter, a sharper eval case, or an improvement to `wake-up-repo`, feel free to open an issue or pull request—see [CONTRIBUTING.md](CONTRIBUTING.md) for branch and verification guidelines.

Released under the [MIT License](LICENSE).
