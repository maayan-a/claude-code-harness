# Superpowers vs. Matt Pocock Skills — Batch 2 Findings

- Sources: S-014 to S-033 (see `research/sources.md`)
- Accessed: 2026-11-16
- Licenses: both repositories are MIT (per their repository pages). Only summaries and short quotes are kept here.

Each finding is marked **Fact** (stated in the source) or **Inference** (mine).

---

## 1. Two opposite philosophies

| Aspect | Superpowers (C-006) | Matt Pocock Skills (C-016) |
|---|---|---|
| Stance | **Fact:** "Mandatory workflows, not suggestions" (S-014) | **Fact:** "small, easy to adapt, and composable" (S-023) |
| Activation | **Fact:** SessionStart hook injects a bootstrap skill every session; "even a 1% chance" a skill applies means it must be invoked (S-022) | **Fact:** many skills are user-invoked only (`disable-model-invocation`), e.g. `implement` (S-028) |
| Human checkpoints | Design-doc approval gate; execution method choice; stop only for irreversible / security / external side effects (S-018, S-019) | Seams agreed before TDD; hypotheses shown before testing; decisions always go to the user (S-024, S-025, S-033) |
| Persistent artifacts | `docs/superpowers/specs/`, `docs/superpowers/plans/`, a ledger file (S-018–S-020) | `GLOSSARY.md`, ADRs, issue-tracker tickets (S-023, S-031) |
| Evidence | **Fact:** no quantitative results on the page; mentions a "drill" eval harness in `superpowers-evals` (S-014) — not reachable (G-010) | **Fact:** no quantitative results; based on cited books and experience (S-023) |

- **Inference:** Superpowers optimizes for discipline; Pocock optimizes for control and low overhead. The harness principle "smallest high-impact version" fits the Pocock approach better, but several Superpowers skills are stronger individually.
- **Inference:** Neither repository offers evidence of effectiveness. Both are candidates for the baseline-vs-harness evaluation, not proven components.

## 2. Overlapping skills — direct comparison candidates

| Responsibility | Superpowers | Pocock | Built-in (batch 1) | Key difference |
|---|---|---|---|---|
| TDD | C-012 — strict Iron Law; delete code written before tests | C-017 — agreed seams, vertical slices, anti-tautology rule | — | Rigidity vs. test quality focus |
| Debugging | C-013 — root cause first; 3 failed fixes → question architecture | C-018 — build a red feedback loop first; redact secrets; 3–5 ranked hypotheses | `/debug` | Single vs. multiple hypotheses; secret redaction only in C-018 |
| Code review | Task reviewer inside C-011 (spec + quality verdicts) | C-020 — two parallel subagents, Standards and Spec kept separate | `/code-review` | Both add a spec-compliance axis |
| Requirements | C-009 — one question at a time, design doc, approval gate | C-025 — rounds over a decision frontier, recommended answers | — | C-025 batches decisions; C-009 produces a written design |
| Planning | C-010 — detailed plan per task with exact files and tests | C-026 — decision map of tickets in the issue tracker | Plan subagent | Execution plan vs. decision map |
| Skill writing | C-015 — pressure scenarios without the skill first | — | C-001 skill-creator | All three agree: test against a no-skill baseline first (also C-005) |

## 3. Practices with high relevance to the user's goal (agent-managed, human decides and reviews)

- **Fact:** C-011 keeps progress in a **ledger file** because "conversation memory does not survive compaction"; briefs, reports, and diffs are passed as **files**, not pasted text; reviews diff from a **recorded BASE commit** (S-018).
- **Fact:** C-011 lists only four reasons to stop and ask the human: irreversible/destructive operation, security-sensitive action, external side effect (merge, push, publish), or a plan too broken to proceed (S-018).
- **Fact:** C-011 requires an explicit model for every subagent dispatch, with tiers by task type, and warns that cheap models can take 2–3× more turns (S-018).
- **Fact:** C-025 asks numbered questions each with a recommended answer "worded so that 'yes' accepts it", and sends fact lookups to a subagent instead of the user (S-033).
- **Fact:** C-026 stores decisions as tickets with types HITL (human in the loop) and AFK (agent alone) (S-031).
- **Fact:** C-023 recommends turning mechanical rules into deterministic checks (lint, pre-commit, CI) instead of prose, and only proposes changes (S-030).
- **Inference:** Combined, these describe a workable pattern: agents work autonomously from files (plan, ledger, tickets), and the human is asked only at defined decision points, with batched questions and recommended answers.

## 4. Context and token cost observations

- **Fact:** Superpowers injects ~450–500 words (`using-superpowers`) into every session via a hook that always exits 0 (S-022).
- **Fact:** Loaded skill sizes vary widely: e.g. brainstorming ~3,500 words, subagent-driven-development ~2,500, TDD ~1,400 (Superpowers); implement ~200, tdd ~600 (Pocock) — estimates from page length, not measured.
- **Fact:** C-024 handoff references artifacts by path instead of copying them (S-032).
- **Inference:** Token cost per skill should be measured in the evaluation; skill size alone differs by an order of magnitude between equivalent skills.

## 5. Not inspected in this batch

- Superpowers: `executing-plans`, `dispatching-parallel-agents`, `requesting-code-review`, `receiving-code-review`, `using-git-worktrees`, `finishing-a-development-branch`, `diagnosing-superpowers`, all reference/template files, `tests/`.
- Pocock: `ask-matt`, `grill-with-docs`, `triage`, `improve-codebase-architecture`, `setup-matt-pocock-skills`, `to-spec`, `to-tickets`, `implement-spec`, `prototype`, `domain-modeling`, `pr`, `wizard`, `grill-me`, `teach`, `to-questionnaire`, `wait-what`, `writing-for-agents`, reference files.
- See G-009.
