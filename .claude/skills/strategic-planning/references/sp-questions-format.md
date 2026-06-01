# /sp-questions — Output Format

## Output template

```md
## Open Questions [filter: {active filter or "all"}]

### Blocking the roadmap
| ID | Question | Artifact | Current assumption |
|---|---|---|---|
| OQ-005 | What is the entry segment? | objectives-architecture | Seg A + C as co-entry |

### High Priority
| ID | Question | Artifact | Current assumption |
|---|---|---|---|

### Medium Priority
| ID | Question | Artifact | Current assumption |
|---|---|---|---|

### Low Priority
| ID | Question | Artifact | Current assumption |
|---|---|---|---|

---
To resolve a question: answer it in conversation.
The agent updates open-questions.md, the source KA, and strategic-change-log in the same step.
```

## Filter behavior

| Filter | What it shows |
|---|---|
| (none) | All open questions. Order: blocking first, then High → Medium → Low. |
| `high` | Only questions with Priority = High. |
| `[artifact-name]` | Only questions where Artifact = that name. Example: `/sp-questions objectives-architecture` |
| `blocking` | Only questions where Blocks = `roadmap` or a specific KA name. |

## Column: Current assumption

This column is the critical output of `/sp-questions`.

Many blocking questions already have an explicit assumption that the agent used to proceed.
The command must show it so the human can decide:
- confirm the assumption as-is (it becomes a decision in "Resolved Decisions")
- replace it with a real answer (the agent updates the KA, open-questions.md, and change-log)
- defer it explicitly (the assumption stays, marked as intentionally deferred)

If no assumption was made, show `—`.

## Resolution flow

When the human answers a question shown by `/sp-questions`:

1. `open-questions.md` — move the row to "Resolved Decisions" with the decision and date.
2. Source KA — replace the NHR marker and `→ OQ-XXX` with the decision. Increment KA version.
3. `strategic-change-log.md` — log the change.

All three steps in the same operation. A question is not resolved until all three are complete.
