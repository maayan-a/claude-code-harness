# Claude Code Extension Mechanisms — Batch 1 Findings

- Sources: S-001 to S-008 (see `research/sources.md`)
- Accessed: 2026-11-16
- License: Anthropic documentation. Only summaries and short quotes are kept here, with links to the source.

Findings that directly affect harness design. Each finding is marked **Fact** (documented in the source) or **Inference** (mine).

---

## 1. Instructions are requests; hooks are enforcement

- **Fact:** "An instruction like 'never edit `.env`' in CLAUDE.md or a skill is a request, not a guarantee. A `PreToolUse` hook that blocks the edit is enforcement." (S-007)
- **Fact:** CLAUDE.md and auto memory are loaded as context, "not enforced configuration" (S-006).
- **Fact:** A failing hook does not block by default — "a policy hook with a wrong path or a crashing script then lets everything through". To block on failure: `"onFailure": "block"` (S-003).
- **Fact:** "use the permission system rather than a hook to enforce a hard allow or deny" (S-003).
- **Inference:** Critical harness rules (security, preventing destructive actions) must live in permissions or in hooks that fail closed — not only in instructions.

## 2. Context cost by mechanism

| Mechanism | When it loads | Cost | Source |
|---|---|---|---|
| CLAUDE.md | Session start, full content | Every request. Target: under 200 lines per file | S-006, S-007 |
| `.claude/rules/` with `paths` | When a matching file is touched | Only when relevant | S-006 |
| Skill | Description at session start; full content when invoked | Low. `description` + `when_to_use` truncated at 1,536 characters | S-001, S-007 |
| Skill with `disable-model-invocation: true` | Only when the user invokes it | Zero until invoked | S-001, S-007 |
| Subagent | When spawned | Separate context; warning when total descriptions exceed 15,000 tokens | S-002, S-007 |
| MCP | Tool names at session start; schemas on demand (tool search) | Low until used. Warning above 10,000 tokens of tool output | S-005, S-007 |
| Hook | On its event | Zero, unless it returns output | S-007 |
| Enabled plugin | Every session | Names and descriptions of all its skills and agents are in context every turn | S-004 |

- **Fact:** After compaction, invoked skills keep "the first 5,000 tokens of each", within a combined budget of 25,000 tokens (S-001).
- **Fact:** `/context all` shows how many tokens each MCP tool uses (S-007).
- **Inference:** Every harness component has a fixed cost (its description) even when unused. This cost must be measured as part of the evaluation.

## 3. Built-in capabilities already in the baseline

- **Fact:** Built-in subagents: `Explore` (read-only), `Plan` (research in plan mode), `general-purpose` (S-002).
- **Fact:** Bundled skills: `/code-review`, `/batch`, `/debug` (S-007).
- **Fact:** Auto memory — notes Claude writes itself, loaded every session (first 200 lines or 25KB) (S-006).
- **Fact:** Dynamic workflows — a script Claude writes that runs many subagents, with optional cross-checking of findings (S-007).
- **Inference:** An external component that duplicates a built-in capability must prove improvement **beyond** it. The comparison baseline is Claude Code with these built-ins.

## 4. Subagents — isolation and delegation

- **Fact:** "Each subagent starts with a fresh, isolated context window. It doesn't see your conversation history, the skills you've already invoked, or the files Claude has already read." (S-002)
- **Fact:** A subagent can spawn subagents up to three layers below the main conversation; up to 20 concurrently by default (S-002).
- **Fact:** Relevant frontmatter fields: `tools`, `model`, `permissionMode`, `isolation: worktree`, `memory`, `skills`, `hooks` (S-002).
- **Fact:** Plugin subagents don't support `hooks`, `mcpServers`, `permissionMode` (S-002).
- **Inference:** Handing a task to a subagent requires a self-contained prompt. This is a risk point for information loss (domains A and H).

## 5. Unknown fields fail silently

- **Fact:** In both skills and subagents, unrecognized frontmatter fields are ignored without an error — "misspelled field names fail silently" (S-001, S-002).
- **Inference:** The harness needs an automated check that validates its components' frontmatter.

## 6. AGENTS.md

- **Fact:** Claude Code reads `AGENTS.md` only when there is no `CLAUDE.md` in the working directory or above it. To use both: import `AGENTS.md` from `CLAUDE.md` (S-006).

## 7. Recommended order for building a setup

- **Fact:** The docs recommend adding mechanisms in response to triggers, e.g.: "Claude gets a convention or command wrong twice → Add it to CLAUDE.md"; "You want something to happen every time without asking → Write a hook" (S-007).
- **Inference:** This matches the "smallest high-impact version" principle (question 10 in mission.md): add a component only when there is an observed problem.

## 8. Skill authoring principles (S-008)

- Conciseness: "Default assumption: Claude is already very smart"; `SKILL.md` body under 500 lines.
- Degrees of freedom matched to task fragility: general instructions for open work, exact scripts for fragile operations.
- References only one level deep from `SKILL.md`.
- Descriptions in third person, covering both "what" and "when".
- Feedback loops: validator → fix → repeat.
- **"Create evaluations BEFORE writing extensive documentation."** → C-005
