# Spec Kit, BMAD Method, GSD — Batch 3 Findings

- Sources: S-034 to S-047 (see `research/sources.md`)
- Accessed: 2026-11-16
- Licenses: all three are MIT (per their repository pages). Only summaries and short quotes are kept here.

Each finding is marked **Fact** (stated in the source) or **Inference** (mine).

---

## 1. Overview

| | Spec Kit (C-027) | BMAD Method (C-033) | GSD Core (C-037) |
|---|---|---|---|
| Owner | GitHub | BMad Code, LLC | open-gsd (originally gsd-build / TÂCHES) |
| Core idea | Specs are the source of truth; "code serves specifications" (S-035) | Role-based agile process with durable decisions (S-040) | Fight context rot with fresh-context subagents (S-046) |
| Install | Python CLI via uv | npx installer | npx installer |
| State in repo | `.specify/`, `specs/`-style feature folders, `memory/constitution.md` | initiative / epic / story files, `_bmad/` | `.planning/` (PROJECT, ROADMAP, STATE, config) |
| Claude Code | **Fact:** `claude` integration exists (S-039) | **Fact:** not named; "any tool that supports skills" (S-040) | **Fact:** named first (S-046) |
| Stability | Active | **Fact:** v6.12 stable, v7 alpha with breaking changes (S-040) | **Fact:** original archived 2026-06-26, moved to GSD Core (S-045) |
| Evidence | **Fact:** anecdotal only (12 h vs 15 min example, S-035) | **Fact:** none (S-040) | **Fact:** none; CI badge only (S-046) |

- **Inference:** None of the three frameworks publishes measured evidence. Together with batch 2, that makes 0 of 5 methodology frameworks with evidence.

## 2. The most reusable parts

### Spec Kit — consistency checks (strongest in this batch)
- **Fact:** `clarify` scans 10 ambiguity categories, asks **at most 5 questions, one at a time**, each with a recommended option, and writes each answer back into the spec (S-037).
- **Fact:** `analyze` is "STRICTLY READ-ONLY", runs 6 detection passes (duplication, ambiguity, underspecification, constitution alignment, coverage gaps, inconsistency), assigns severities, and reports coverage % (S-036).
- **Fact:** `converge` compares the spec with the current code and classifies gaps as **missing / partial / contradicts / unrequested**, appending tasks until it reports "converged" (S-038).
- **Fact:** templates require `[NEEDS CLARIFICATION: ...]` markers instead of guesses (S-035).
- **Inference:** `converge` turns "does the code match the spec" into a repeatable loop with typed gaps — the clearest spec-compliance verification found so far.

### BMAD — keeping instructions small and true
- **Fact:** `bmad-project-context` verifies every instruction against the code, records each existing instruction as retain / rewrite / relocate / automate / delete, turns observed agent mistakes into pitfalls and proposes hooks or CI checks, and requires audits to "end with the same size or smaller" (S-042).
- **Fact:** much of BMAD's workflow logic is printed by scripts at runtime (S-043), so it cannot be inspected by reading alone.

### GSD — session continuity and context hygiene
- **Fact:** heavy research, planning, and execution run in fresh-context subagents; plans are checked to fit a fresh context window (S-046).
- **Fact:** `/gsd-pause-work` writes `.planning/continue-here.md`; `/gsd-resume-work` restores it; `/gsd-health --context` checks context-window usage (S-047).
- **Fact:** model profiles `quality` / `balanced` / `budget` (S-047).

## 3. Patterns confirmed across batches 2 and 3

| Pattern | Seen in |
|---|---|
| Specs / plans / decisions persisted as files in the repo | Superpowers, Pocock, Spec Kit, BMAD, GSD |
| Fresh-context subagents for heavy work, with file-based handoffs | Superpowers (C-011), GSD (C-037), Pocock (C-022) |
| Few batched questions with a recommended answer | Pocock (C-025), Spec Kit (C-029) |
| Verification against the spec, not just "tests pass" | Superpowers (C-011 reviewer), Pocock (C-020), Spec Kit (C-031) |
| Turning repeated mistakes into deterministic checks | Pocock (C-023), BMAD (C-035), Anthropic docs (batch 1) |
| Explicit model tiers per task | Superpowers (C-011), GSD (C-037) |

- **Inference:** These six patterns appear independently in several sources. They are strong candidates for the harness's core, to be validated in the evaluation phase.

## 4. Concerns

- **Fact:** Matt Pocock's README criticizes GSD, BMAD, and Spec Kit for taking away "your control" (S-023).
- **Inference:** All three are large (Spec Kit ~9 core commands plus extensions; GSD ~40 commands; BMAD 16 method skills plus modules). Adopting any of them whole conflicts with the minimal-harness goal. Extracting specific parts (C-029–C-031, C-035, C-038) is more consistent with the mission.

## 5. Not inspected in this batch

- Spec Kit: `specify`, `plan`, `tasks`, `implement`, `checklist`, `constitution` command templates; bug and assess extensions.
- BMAD: all other method skills; runtime workflow scripts; Test Architect and BMad Loop modules.
- GSD Core: `agents/`, `hooks/`, command implementations, remaining 60% of COMMANDS.md.
- See G-013 to G-015.
