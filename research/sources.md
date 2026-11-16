# Sources

Central registry of all inspected sources. Other files reference sources by ID (`S-###`).
Sources not yet inspected are listed in `mission.md`.

## Source types
- `official` — official documentation / Anthropic
- `primary` — source code or the component's authors
- `independent` — independent research / measurement
- `secondary` — summary, post, list

## Registry

| ID | Title | Link | Type | Author / Org | Accessed | Batch | Notes |
|---|---|---|---|---|---|---|---|
| S-001 | Claude Code Docs — Skills | https://code.claude.com/docs/en/skills | official | Anthropic | 2026-11-16 | 1 | First ~100K of ~120K characters read |
| S-002 | Claude Code Docs — Subagents | https://code.claude.com/docs/en/sub-agents | official | Anthropic | 2026-11-16 | 1 | First ~100K of ~117K characters read |
| S-003 | Claude Code Docs — Hooks reference | https://code.claude.com/docs/en/hooks | official | Anthropic | 2026-11-16 | 1 | First ~100K of ~294K characters read |
| S-004 | Claude Code Docs — Plugins overview | https://code.claude.com/docs/en/plugins | official | Anthropic | 2026-11-16 | 1 | Read in full |
| S-005 | Claude Code Docs — MCP | https://code.claude.com/docs/en/mcp | official | Anthropic | 2026-11-16 | 1 | First ~100K of ~157K characters read |
| S-006 | Claude Code Docs — Memory (CLAUDE.md, rules, AGENTS.md) | https://code.claude.com/docs/en/memory | official | Anthropic | 2026-11-16 | 1 | Partially read (targeted search) |
| S-007 | Claude Code Docs — Extend Claude Code | https://code.claude.com/docs/en/features-overview | official | Anthropic | 2026-11-16 | 1 | Read in full |
| S-008 | Skill authoring best practices | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices | official | Anthropic | 2026-11-16 | 1 | Read in full |
| S-009 | anthropics/skills — README and structure | https://github.com/anthropics/skills | primary | Anthropic | 2026-11-16 | 1 | Latest commit checked: 2026-11-14 |
| S-010 | anthropics/skills — skill-creator | https://github.com/anthropics/skills/tree/main/skills/skill-creator | primary | Anthropic | 2026-11-16 | 1 | SKILL.md and folder listing read |
| S-011 | anthropics/skills — webapp-testing | https://github.com/anthropics/skills/tree/main/skills/webapp-testing | primary | Anthropic | 2026-11-16 | 1 | SKILL.md read |
| S-012 | anthropics/skills — mcp-builder | https://github.com/anthropics/skills/tree/main/skills/mcp-builder | primary | Anthropic | 2026-11-16 | 1 | SKILL.md read |
| S-013 | anthropics/skills — discernment-nudge | https://github.com/anthropics/skills/tree/main/skills/discernment-nudge | primary | Anthropic | 2026-11-16 | 1 | SKILL.md read |
| S-014 | obra/superpowers — README and structure | https://github.com/obra/superpowers | primary | Jesse Vincent / Prime Radiant | 2026-11-16 | 2 | Latest release seen: v7.0.2 (2026-11-03) |
| S-015 | superpowers — test-driven-development | https://github.com/obra/superpowers/tree/main/skills/test-driven-development | primary | Jesse Vincent / Prime Radiant | 2026-11-16 | 2 | SKILL.md read |
| S-016 | superpowers — systematic-debugging | https://github.com/obra/superpowers/tree/main/skills/systematic-debugging | primary | Jesse Vincent / Prime Radiant | 2026-11-16 | 2 | SKILL.md read; 3 reference files not read |
| S-017 | superpowers — verification-before-completion | https://github.com/obra/superpowers/tree/main/skills/verification-before-completion | primary | Jesse Vincent / Prime Radiant | 2026-11-16 | 2 | SKILL.md read |
| S-018 | superpowers — subagent-driven-development | https://github.com/obra/superpowers/tree/main/skills/subagent-driven-development | primary | Jesse Vincent / Prime Radiant | 2026-11-16 | 2 | SKILL.md read; templates and reference files not read |
| S-019 | superpowers — brainstorming | https://github.com/obra/superpowers/tree/main/skills/brainstorming | primary | Jesse Vincent / Prime Radiant | 2026-11-16 | 2 | SKILL.md read |
| S-020 | superpowers — writing-plans | https://github.com/obra/superpowers/tree/main/skills/writing-plans | primary | Jesse Vincent / Prime Radiant | 2026-11-16 | 2 | SKILL.md read |
| S-021 | superpowers — writing-skills | https://github.com/obra/superpowers/tree/main/skills/writing-skills | primary | Jesse Vincent / Prime Radiant | 2026-11-16 | 2 | SKILL.md read; reference files not read |
| S-022 | superpowers — using-superpowers and hooks/session-start | https://github.com/obra/superpowers/tree/main/hooks | primary | Jesse Vincent / Prime Radiant | 2026-11-16 | 2 | Hook script and SKILL.md read |
| S-023 | mattpocock/skills — README and structure | https://github.com/mattpocock/skills | primary | Matt Pocock | 2026-11-16 | 2 | Latest commit seen: 2026-11-12 |
| S-024 | mattpocock/skills — tdd | https://github.com/mattpocock/skills/tree/main/skills/engineering/tdd | primary | Matt Pocock | 2026-11-16 | 2 | SKILL.md read; tests.md, mocking.md not read |
| S-025 | mattpocock/skills — diagnosing-bugs | https://github.com/mattpocock/skills/tree/main/skills/engineering/diagnosing-bugs | primary | Matt Pocock | 2026-11-16 | 2 | SKILL.md read |
| S-026 | mattpocock/skills — codebase-design | https://github.com/mattpocock/skills/tree/main/skills/engineering/codebase-design | primary | Matt Pocock | 2026-11-16 | 2 | SKILL.md read; DEEPENING.md, DESIGN-IT-TWICE.md not read |
| S-027 | mattpocock/skills — code-review | https://github.com/mattpocock/skills/tree/main/skills/engineering/code-review | primary | Matt Pocock | 2026-11-16 | 2 | SKILL.md read |
| S-028 | mattpocock/skills — implement | https://github.com/mattpocock/skills/tree/main/skills/engineering/implement | primary | Matt Pocock | 2026-11-16 | 2 | SKILL.md read |
| S-029 | mattpocock/skills — research | https://github.com/mattpocock/skills/tree/main/skills/engineering/research | primary | Matt Pocock | 2026-11-16 | 2 | SKILL.md read |
| S-030 | mattpocock/skills — retro | https://github.com/mattpocock/skills/tree/main/skills/engineering/retro | primary | Matt Pocock | 2026-11-16 | 2 | SKILL.md read |
| S-031 | mattpocock/skills — wayfinder | https://github.com/mattpocock/skills/tree/main/skills/engineering/wayfinder | primary | Matt Pocock | 2026-11-16 | 2 | SKILL.md read |
| S-032 | mattpocock/skills — handoff | https://github.com/mattpocock/skills/tree/main/skills/productivity/handoff | primary | Matt Pocock | 2026-11-16 | 2 | SKILL.md read |
| S-033 | mattpocock/skills — grilling | https://github.com/mattpocock/skills/tree/main/skills/productivity/grilling | primary | Matt Pocock | 2026-11-16 | 2 | SKILL.md read |
| S-034 | github/spec-kit — README | https://github.com/github/spec-kit | primary | GitHub | 2026-11-16 | 3 | Release version not shown on page; mentions "Spec Kit 1.0" |
| S-035 | spec-kit — spec-driven.md (philosophy) | https://github.com/github/spec-kit/blob/main/spec-driven.md | primary | GitHub | 2026-11-16 | 3 | Read in full |
| S-036 | spec-kit — templates/commands/analyze.md | https://github.com/github/spec-kit/blob/main/templates/commands/analyze.md | primary | GitHub | 2026-11-16 | 3 | Read in full |
| S-037 | spec-kit — templates/commands/clarify.md | https://github.com/github/spec-kit/blob/main/templates/commands/clarify.md | primary | GitHub | 2026-11-16 | 3 | Read in full |
| S-038 | spec-kit — templates/commands/converge.md | https://github.com/github/spec-kit/blob/main/templates/commands/converge.md | primary | GitHub | 2026-11-16 | 3 | Read in full |
| S-039 | spec-kit — integrations folder listing | https://github.com/github/spec-kit/tree/main/src/specify_cli/integrations | primary | GitHub | 2026-11-16 | 3 | Confirms a `claude` integration among ~44 agents |
| S-040 | bmad-code-org/BMAD-METHOD — README | https://github.com/bmad-code-org/BMAD-METHOD | primary | BMad Code, LLC | 2026-11-16 | 3 | Stable v6.12; v7 alpha on main |
| S-041 | BMAD-METHOD — skills/method listing | https://github.com/bmad-code-org/BMAD-METHOD/tree/main/skills/method | primary | BMad Code, LLC | 2026-11-16 | 3 | 16 skill folders listed |
| S-042 | BMAD-METHOD — bmad-project-context | https://github.com/bmad-code-org/BMAD-METHOD/tree/main/skills/method/bmad-project-context | primary | BMad Code, LLC | 2026-11-16 | 3 | SKILL.md read |
| S-043 | BMAD-METHOD — bmad-code-review | https://github.com/bmad-code-org/BMAD-METHOD/tree/main/skills/method/bmad-code-review | primary | BMad Code, LLC | 2026-11-16 | 3 | SKILL.md read; workflow is printed by a script at runtime (not readable) |
| S-044 | BMAD-METHOD — bmad-agent-architect | https://github.com/bmad-code-org/BMAD-METHOD/tree/main/skills/method/bmad-agent-architect | primary | BMad Code, LLC | 2026-11-16 | 3 | SKILL.md read |
| S-045 | gsd-build/get-shit-done (archived) | https://github.com/gsd-build/get-shit-done | primary | TÂCHES (per page) | 2026-11-16 | 3 | Archived 2026-06-26; moved to open-gsd/gsd-core |
| S-046 | open-gsd/gsd-core — README | https://github.com/open-gsd/gsd-core | primary | open-gsd | 2026-11-16 | 3 | Mentions version 1.7.0 |
| S-047 | gsd-core — docs/COMMANDS.md | https://github.com/open-gsd/gsd-core/blob/next/docs/COMMANDS.md | primary | open-gsd | 2026-11-16 | 3 | First ~100K of ~163K characters read |
