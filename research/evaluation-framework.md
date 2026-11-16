# Evaluation Framework

## 1. Component record fields (`components.csv`)

| Column | Description | Values |
|---|---|---|
| `id` | Component ID | `C-001`... |
| `component_name` | Exact name | |
| `original_source` | Repository / source URL | |
| `original_author` | Verified creator or organization | `unknown` if not verified |
| `component_type` | Component type (axis 1) | `Skill` / `Agent` / `Hook` / `MCP` / `CLI` / `Framework` / `Tool` / `Methodology` / `Instructions` |
| `domain` | Relevant domain (axis 2) | |
| `subcategory` | Specific responsibility | |
| `problem_solved` | What problem it addresses | |
| `how_it_works` | Actual implementation or workflow | |
| `inputs` | What information it needs | |
| `outputs` | What it produces | |
| `dependencies` | Required tools or components | |
| `claude_code_compatibility` | Compatibility with Claude Code | `direct` / `adaptable` / `incompatible` |
| `token_overhead` | Token cost | Estimate or measurement — state which |
| `runtime_overhead` | Runtime cost | Estimate or measurement — state which |
| `evidence` | Evidence of effectiveness | Tests, benchmarks, real-world use, documentation |
| `maintenance` | Recent releases and activity | |
| `license` | Verified license | |
| `limitations` | Known weaknesses | |
| `overlap` | Similar components (C-### IDs) | |
| `potential_value` | Why it might improve the harness | |
| `maturity` | Maturity level (section 3) | `proven` / `experimental` / `inspiration` / `not-relevant` / `unsuitable` |
| `parent_component` | Framework the component belongs to | C-### ID |
| `source_ids` | Sources supporting the record | S-### IDs |
| `date_researched` | Research date | YYYY-MM-DD |
| `notes` | Notes | |

Unknown information is marked `unknown`. Do not leave a field empty when the information was checked and not found.

## 2. Evaluation criteria

1. Engineering quality
2. Originality
3. Practical usefulness
4. Maintenance activity
5. Documentation quality
6. Evidence of effectiveness
7. Compatibility with Claude Code
8. Ease of integration
9. Token efficiency
10. Runtime and financial cost
11. Security implications
12. License and reuse restrictions
13. Duplication with other components

### Scoring scale
<!-- To be defined once enough components have been collected for comparison -->

## 3. Maturity levels

| Value | Meaning |
|---|---|
| `proven` | Proven and mature — strong evidence and wide use |
| `experimental` | Promising but experimental |
| `inspiration` | Useful inspiration only — a good idea, not for direct use |
| `not-relevant` | Not relevant |
| `unsuitable` | Potentially dangerous or unsuitable |

## 4. Evaluating the harness as a whole (baseline vs. harness)

### Principle
Claude Code baseline and Claude Code with the harness solve **the same tasks** under **comparable conditions**.

### Metrics
Correctness · test coverage · security · maintainability · token usage · time · cost.

### Test tasks
<!-- To be defined in the evaluation and benchmarking batch -->

### Methodology
<!-- Comparison conditions, repetitions, statistical reliability, control of variables -->

## 5. Known limitations
