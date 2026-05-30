# Review Report Format

This file defines the exact output schema for the Adversarial Reviewer agent.
The Orchestrator uses this schema to parse the review report and determine next steps.

---

## Report Structure

The review report has two blocks. They must be separated by a visible divider.
Each block has its own score, defect log, and recommended next steps.

---

```md
# Review Report — [scope: KAs / Roadmap]
Generated: [date]
Scope: [kas | roadmap]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
BLOCK 1 — INPUT QUALITY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Score: [1–10]
Summary: [1–2 sentences on overall input quality]

### Defect Log

| ID | Defect | Type | Artifact / Section | Attributable to | Severity | Next step |
|---|---|---|---|---|---|---|

### What the input covers well
[Bullet list — areas with good coverage and evidence]

### What the input is missing
[Bullet list — absent information that weakened artifacts]

### Open questions the input did not resolve
[Bullet list — gaps the human must address]

### Assumed claims that should be validated
[Bullet list — claims the system treated as fact without evidence]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
BLOCK 2 — PROCESS / AGENT QUALITY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Score: [1–10]
Summary: [1–2 sentences on overall execution quality]

### Defect Log

| ID | Defect | Type | Artifact / Section | Attributable to | Severity | Next step |
|---|---|---|---|---|---|---|

### What the agent did well
[Bullet list — areas of strong execution]

### Execution issues found
[Narrative or bullets — grouped by artifact if multiple KAs reviewed]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
HUMAN CHECKPOINT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

### Blocking issues (must resolve before proceeding)
[List of defect IDs with severity = blocking]

### Decisions needed from you
[List of items attributable to human_decision_needed]

### Items the Orchestrator will handle
[List of defect IDs the Orchestrator can resolve without human input]

Confirm to proceed, or indicate which items to address first.
```

---

## Field Definitions

### Defect ID
Format: `D-001`, `D-002`, etc. Sequential within the report. Unique across both blocks.

### Defect
One-sentence description of the specific problem. Must name the artifact, section, or claim. Must not be vague.

Good: `product-thesis.md assumes B2B segment as primary — no source document declares this`
Bad: `ICP section is weak`

### Type
Use only these values:

| Type | Use when |
|---|---|
| `input_gap` | Information absent from source material |
| `weak_evidence` | Claim accepted as fact but only assumed in Input |
| `source_conflict` | Contradiction between Input documents not surfaced |
| `tactical_drift` | Tactical item promoted to strategy without challenge |
| `missing_constraint` | Known constraint not reflected in artifact or roadmap |
| `decorative_kpi` | Numeric target invented without human input or source |
| `roadmap_overreach` | Roadmap generated before prerequisites were complete |
| `agent_invention` | Content with no traceable source in Input |
| `overcomplicated_text` | Output dense beyond what input complexity warrants |
| `hidden_contradiction` | Conflict present in Input ignored without flagging |
| `source_of_truth_conflict` | Two artifacts contain incompatible definitions |
| `versioning_error` | Artifact version or changelog not maintained correctly |
| `missing_nhr` | Content that warranted NHR marker but was not flagged |
| `needs_human_decision` | Gap requiring a decision only the human can make |

### Artifact / Section
Name the specific artifact and section where the defect appears.
Example: `product-thesis.md / Assumptions`, `strategic-roadmap.md / Phase 2`

### Attributable to
Use only these values:

| Value | Meaning |
|---|---|
| `input` | Source material did not provide what was needed |
| `agent` | Agent invented, hid, or ignored available information |
| `human_decision_needed` | Requires a decision only the human can make |
| `mixed` | Combination of weak input and poor synthesis — explain both |

Always include a one-sentence reasoning after the value.
Example: `input — no source document defines the GTM segment`
Example: `agent — diagnostic report flagged this claim as assumed; artifact presents it as fact`

### Severity
Use only these values:

| Value | Meaning |
|---|---|
| `low` | Minor issue, does not affect artifact usability |
| `medium` | Reduces artifact quality or reliability |
| `high` | Materially weakens artifact or roadmap |
| `blocking` | Orchestrator must not proceed without resolution |

### Next step
Use only these values:

| Value | Meaning |
|---|---|
| `orchestrator_revise` | Orchestrator corrects the artifact |
| `human_input_needed` | Human must provide missing information |
| `human_decision_needed` | Human must make a strategic decision |
| `open_question` | Register in open-questions.md and proceed |
| `accept_as_assumption` | Document as explicit assumption and continue |
| `flag_for_skill_review` | Pattern suggests a skill improvement opportunity |

---

## Scoring Guide

### Block 1 — Input Quality

| Score | Meaning |
|---|---|
| 9–10 | Input is complete, consistent, and well-evidenced. Minimal gaps. |
| 7–8 | Input covers most areas. Some gaps or assumed claims, but not blocking. |
| 5–6 | Input has meaningful gaps. Several areas required assumptions. |
| 3–4 | Input is significantly incomplete or contradictory. Artifacts are weakened. |
| 1–2 | Input does not support artifact generation reliably. Major decisions are missing. |

### Block 2 — Process / Agent Quality

| Score | Meaning |
|---|---|
| 9–10 | Execution was faithful to the skill. No inventions. NHR markers used correctly. |
| 7–8 | Mostly correct execution. Minor issues that do not affect artifact reliability. |
| 5–6 | Some execution problems. One or more artifacts have traceability issues. |
| 3–4 | Multiple execution failures. Artifacts contain invented or unattributed content. |
| 1–2 | Execution was significantly unfaithful to the skill. Artifacts are unreliable. |

---

## Human Checkpoint Rules

The Human Checkpoint section must appear after both blocks. It must:

1. List all defects with severity `blocking` — these cannot be skipped.
2. List all items attributable to `human_decision_needed` — these require human action.
3. List all defects the Orchestrator can handle without human input — for transparency.
4. End with a single confirmation prompt.

The Orchestrator presents this section to the human and waits for confirmation before proceeding.
