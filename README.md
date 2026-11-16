# Claude Code Harness — Research Project

## Goal
Research the ecosystem around Claude Code and later build a high-quality **AI Software Engineering Harness**: a controlled combination of Skills, Agents, Hooks, MCP servers, tools, and workflows that measurably improves software engineering quality compared to Claude Code without a harness.

Additional goal: an agent-managed development methodology — agents manage the process, store and update knowledge, and do the work, while the human only makes decisions and reviews.

The goal is not the biggest harness, but the most effective one.

## Core documents
- [research/mission.md](research/mission.md) — the full research mission: sources, domains, deliverables, and questions.
- [CLAUDE.md](CLAUDE.md) — the binding working rules.

## Methodology in brief
- Discover broadly before classifying; the taxonomy emerges from the findings.
- Extract individual components from repositories, not just evaluate whole repositories.
- Original sources, verified claims, and explicit marking of unknown information.
- Web reading only — no cloning repositories and no installations.
- Work in batches, logged in [research-log.md](research/research-log.md).

## Project phases

| # | Phase | Main output | Status |
|---|---|---|---|
| 0 | Set up the research environment | Structure, rules, mission document | Done |
| 1 | Initial sources | `sources.md` | In progress |
| 2 | Component extraction | `components.csv` | Not started |
| 3 | Discovery expansion | `sources.md`, `people-and-organizations.md` | Not started |
| 4 | Classification | `taxonomy.md` | Not started |
| 5 | Domain analysis | `domain-analysis/` | Not started |
| 6 | Coverage analysis | `research-gaps.md` | Not started |
| 7 | Preliminary recommendations | `integration-candidates.md` | Not started |
| 8 | Baseline measurement | `benchmarks/baseline/` | Not started |
| 9 | Build and measure the harness | `benchmarks/harness/` | Not started |

Phases 1–7 are research only. Phases 8–9 start only after an explicit decision.

## Batch plan (phases 1–2)

| Batch | Content | Status |
|---|---|---|
| 1 | Claude Code official docs and `anthropics/skills` — verify component type definitions | Done (2026-11-16) |
| 2 | Superpowers, Matt Pocock Skills | Done (2026-11-16) |
| 3 | Spec Kit, BMAD Method, GSD | Not started |
| 4 | Aider, Cline, Roo Code, AGENTS.md | Not started |
| 5 | Catalogs: Awesome Cursor Rules, Awesome Claude Skills, Awesome Context Engineering | Not started |
| 6 | Evaluation and benchmarking | Not started |
| 7 | Security | Not started |
| 8 | Testing and quality engineering | Not started |
| 9 | Architecture and design quality | Not started |
| 10 | Observability, performance, and agent tracing | Not started |

## Navigation

```text
claude-code-harness/
├── README.md                     # This file
├── CLAUDE.md                     # Working rules
├── research/
│   ├── mission.md                # Research mission
│   ├── sources.md                # Registry of inspected sources
│   ├── components.csv            # Component inventory
│   ├── taxonomy.md               # Component types and categories
│   ├── people-and-organizations.md
│   ├── evaluation-framework.md   # Fields, criteria, comparison methodology
│   ├── integration-candidates.md
│   ├── research-gaps.md
│   ├── research-log.md
│   └── domain-analysis/          # One analysis per domain
├── references/                   # Relevant excerpts from sources
│   ├── repositories/
│   ├── articles/
│   └── documentation/
└── benchmarks/
    ├── baseline/                 # Claude Code without the harness
    └── harness/                  # Claude Code with the harness
```
