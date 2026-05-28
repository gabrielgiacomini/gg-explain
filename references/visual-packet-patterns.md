# Visual Packet Patterns

## Packet Shape Selection

| Question Shape | Primary Visual | Use When | Avoid When |
| --- | --- | --- | --- |
| What happens step by step? | Mermaid `flowchart TD` | the explanation is about process flow, staged orchestration, or handoffs | the real question is timing between actors rather than step order |
| Who talks to whom and in what order? | Mermaid `sequenceDiagram` | actor-to-actor exchanges or request/response order matters | the explanation is mostly branching logic or state |
| How does this thing change over time? | Mermaid `stateDiagram-v2` | the subject is lifecycle, mode changes, or transition guards | the explanation is linear and does not involve true state |
| How do options differ? | comparison matrix table | the question is tradeoff-heavy and the user must compare paths quickly | the question is causal flow rather than side-by-side comparison |
| What does the user experience? | ASCII user journey | terminal readability matters more than rendered diagrams | system internals are the real focus |
| Which files or contracts matter? | key-files table plus optional mini-flowchart | the user needs concrete starting points in the repo | the explanation is conceptual and not yet tied to code |

## Scan-Speed Rules

1. Lead with one direct answer sentence before the visual.
2. Prefer one primary visual. Add a second one only when it removes real ambiguity.
3. Default to vertical diagrams when the medium is narrow or scan speed matters.
4. Use `LR` only when horizontal causality is materially clearer than top-down flow.
5. Quote Mermaid labels when they contain punctuation or multiple words:
   - `A["Question or label"]`
6. Split wide diagrams into stacked subgraphs or multiple mini-diagrams instead of shrinking one
   large diagram.
7. Prefer tables when the user is choosing among options, responsibilities, or phases.
8. Keep the usual visual payload small enough to inspect quickly:
   - roughly one diagram with up to about 9 nodes, or
   - one compact matrix with 3-6 rows.

## File and Contract Inclusion Heuristics

Include `Key Files / Contracts` when any of these are true:

- the user is likely to act on the explanation immediately,
- the explanation depends on a specific source file, route, or contract boundary,
- the next downstream skill needs exact starting points.

Skip file tables when the explanation is purely conceptual and code pointers would distract from the
main idea.

## Suggested Packet Order

1. `What This Is`
2. `Short Explanation`
3. `Visual Explanation`
4. `Key Files / Contracts`
5. `What To Do Next`
