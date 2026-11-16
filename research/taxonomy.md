# Taxonomy

Two separate classification axes (see CLAUDE.md, section 6).

---

## Axis 1 — Component types

What a component is **technically**. The definitions of Skill, Agent, Hook, and MCP were verified against the official documentation (batch 1).

| Value | Definition | Source | Status |
|---|---|---|---|
| `Skill` | A folder with `SKILL.md` (YAML frontmatter + Markdown instructions) and supporting files. The description is loaded into context every session; the full content loads only when the skill is invoked — by Claude, matching the description, or by the user via `/name`. Slash commands have been merged into skills | S-001, S-007 | Verified |
| `Agent` | A subagent: a Markdown file with frontmatter whose body is the system prompt. Runs in a separate context window, without the conversation history, with its own tools and permissions, and returns a summary | S-002, S-007 | Verified |
| `Hook` | A handler the harness runs automatically on a lifecycle event (e.g. `PreToolUse`, `Stop`). Five types: `command`, `http`, `mcp_tool`, `prompt`, `agent`. Deterministic — runs without Claude deciding | S-003, S-007 | Verified |
| `MCP` | A Model Context Protocol server that exposes tools and data of an external system to Claude (tools / prompts / resources) | S-005, S-007 | Verified |
| `CLI` | A command-line tool Claude invokes via Bash | Project definition | Defined |
| `Framework` | A system or collection combining several component types | Project definition | Defined |
| `Tool` | Software or a service outside Claude Code | Project definition | Defined |
| `Methodology` | A working method or engineering practice, with no required software implementation | Project definition | Defined |
| `Instructions` | A standing instruction file loaded into context without explicit invocation: CLAUDE.md, `.claude/rules/`, AGENTS.md, output styles, rule sets (e.g. Cursor rules) | S-006, S-007; decision 2026-11-16 (G-003) | Defined |

### Edge cases

| Case | What it is per the docs | Classification rule in this project |
|---|---|---|
| Plugin | "The packaging layer": a folder with a manifest that bundles Skills, Agents, Hooks, and MCP servers into one unit installed from a marketplace (S-004, S-007) | A plugin is not a component type. A plugin bundling several types is recorded as a `Framework`, and each component in it is recorded separately with `parent_component` |
| Slash command (`.claude/commands/`) | "Custom commands have been merged into skills" (S-001) | Recorded as `Skill` |
| Skill with `context: fork` | A skill that runs inside a subagent (S-001) | Recorded as `Skill`, noted in `how_it_works` |
| CLAUDE.md, `.claude/rules/`, AGENTS.md | Instruction files loaded at session start or by path (S-006) | Recorded as `Instructions` |
| Output style | Instructions for role, tone, and format for the whole session (S-007) | Recorded as `Instructions` |
| Built-in capabilities (Explore, Plan, `/code-review`, `/debug`, `/batch`, auto memory, dynamic workflows) | Part of Claude Code itself (S-002, S-007) | Not recorded as components. They are part of the baseline, documented in `references/documentation/claude-code-extension-mechanisms.md` |

---

## Axis 2 — Domains and categories

**Categories are derived from the research** (phase 4) and are not set in advance. Target: 8–12 top-level categories, without forcing the number.

The starting domains in `mission.md` (section 5) are only a search starting point.

### Recurring responsibilities identified

| Responsibility | Components | Batch |
|---|---|---|
| Developing and improving skills with evaluation against a baseline | C-001, C-005 | 1 |
| End-to-end testing of web apps | C-002 | 1 |
| Building MCP servers | C-003 | 1 |
| Encouraging the user to check answers before acting | C-004 | 1 |
| Whole development methodology bundles | C-006, C-016 | 2 |
| Forcing / bootstrapping skill usage | C-007, C-008 | 2 |
| Requirements discovery and decision interviews | C-009, C-025 | 2 |
| Planning (execution plans, decision maps) | C-010, C-026 | 2 |
| Plan execution via subagents, handoffs | C-011, C-021, C-024 | 2 |
| Test-driven development | C-012, C-017 | 2 |
| Debugging | C-013, C-018 | 2 |
| Verification before claiming completion | C-014 | 2 |
| Testing skills against a no-skill baseline | C-001, C-005, C-015 | 1–2 |
| Module and interface design | C-019 | 2 |
| Code review against standards and spec | C-020 | 2 |
| Primary-source research in background | C-022 | 2 |
| Session retrospective, improving the setup | C-023 | 2 |

### Top-level categories
<!-- Filled in during phase 4 -->

### Cross-domain components
<!-- Filled in during phase 4 -->
