# Research Log

One entry per session or batch, newest first.

## Template
```
## YYYY-MM-DD — Batch N: Title
- Sources inspected:
- Key findings:
- Decisions:
- New gaps:
- Remaining work:
```

---

## 2026-11-16 — Language change
- Decisions: Everything is in English — project files and chat. All project files were translated from Hebrew to English (user decision).

## 2026-11-16 — Batch 1: Claude Code official docs and anthropics/skills
- Sources inspected: S-001 to S-013.
- Key findings (details in `references/documentation/claude-code-extension-mechanisms.md`):
  - Verified the definitions of Skill, Agent, Hook, and MCP. A plugin is a packaging layer, not a component type. Slash commands have been merged into skills.
  - Instructions (CLAUDE.md, skills) are requests; hooks and permissions are enforcement. A failing hook does not block by default.
  - Every component has a fixed context cost (its description) even when unused.
  - The baseline already has built-in capabilities (Explore, Plan, `/code-review`, `/debug`, auto memory, dynamic workflows). An external component must prove improvement beyond them.
  - Anthropic recommends evaluation-driven development against a baseline (C-005), and skill-creator implements it (C-001).
  - anthropics/skills has 19 skills; most are unrelated to software engineering. 4 relevant ones were recorded (C-001 to C-004).
- Decisions: Added a classification rule for plugins to the taxonomy. Added a ninth component type, `Instructions`, for standing instruction files (user decision, closes G-003). Repository published at https://github.com/maayan-a/claude-code-harness
- New gaps: G-003 to G-008 (G-003 closed).
- Remaining work: Batch 2 — Superpowers and Matt Pocock Skills.

## 2026-11-16 — Phase 0: Setup and alignment with the mission document
- Done:
  - Created the folder structure, README.md, CLAUDE.md, and research file templates.
  - Saved the mission document as `research/mission.md`, reorganized and updated.
  - Aligned the project with the document: renamed `domains/` to `domain-analysis/` with a template; `components.csv` columns follow the document's 20 fields plus tracking fields; separated component type from domain; added `Tool` and `Methodology` as component types.
  - Created a git repository.
- Decisions:
  - Web reading only, no cloning repositories; save only relevant excerpts.
  - Single agent working sequentially, in batches.
  - The repository is public on GitHub.
  - Added domain H: agent-managed methodology, memory, and human-in-the-loop (an explicit user goal).
- New gaps: G-001, G-002.
- Next step: Batch 1 — Claude Code official docs and `anthropics/skills`.
