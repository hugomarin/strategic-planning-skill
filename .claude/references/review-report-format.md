# Review Report Format

This file defines the exact output schema for the Adversarial Reviewer agent.
The Orchestrator uses this schema to parse the review report and determine next steps.
Applies to all three scopes: `strategic`, `roadmap`, and `implementation`.

---

## Report Structure

The review report has three sections: Block 1 (Input Quality), Block 2 (Process / Agent Quality),
and Human Checkpoint. They must appear in this order, clearly separated.

---

```md
# Adversarial Review — [Strategic | Roadmap | Implementation]
Generated: [YYYY-MM-DD]
Scope: [strategic | roadmap | implementation]

## Block 1 — Input Quality

**Score:** [1–10]
**Summary:** [2–3 sentences on the overall quality of Input/ for this scope]

**Defect log:**

| D-ID | Defect | Type | Artifact / Section | YAML ID | Severity | Attribution | Next step |
|---|---|---|---|---|---|---|---|

**What the input covers well:**
[Bullet list — areas with good coverage and evidence]

**What the input is missing:**
[Bullet list — absent information that weakened artifacts]

**Open questions the input did not resolve:**
[Bullet list — gaps the human must address]

**Assumed claims that should be validated:**
[Bullet list — claims the system treated as fact without evidence]

---

## Block 2 — Process / Agent Quality

**Score:** [1–10]
**Summary:** [2–3 sentences on how well the Orchestrator executed the skill]

**Defect log:**

| D-ID | Defect | Type | Artifact / Section | YAML ID | Severity | Attribution | Next step |
|---|---|---|---|---|---|---|---|

**What the agent did well:**
[Bullet list — areas of strong execution]

**Execution issues found:**
[Narrative or bullets grouped by artifact]

---

## Human Checkpoint

**Blocking issues (must resolve before proceeding):**
[List D-IDs with severity = blocking]

**Decisions needed from you:**
[List D-IDs attributable to human_decision_needed]

**Items the Orchestrator will handle:**
[List D-IDs the Orchestrator can resolve without human input]

Confirm to proceed, or indicate which items to address first.
```

---

## Field Definitions

### D-ID
Format: `D-001`, `D-002`, etc. Sequential within the report. Unique across both blocks.

### Defect
One-sentence description of the specific problem. Must name the artifact, section, or claim.
Include the key evidence inline. Must not be vague.

Good: `product-thesis.md assumes B2B segment as primary — no source document declares this`
Bad: `ICP section is weak`

### Type
Use only the values in the applicable table below. Type values differ by scope.

**Shared defect types — all scopes:**

| Type | Use when |
|---|---|
| `agent_invention` | Content in artifact not traceable to any Input source |
| `hidden_contradiction` | Conflict present in Input ignored or smoothed over without flagging |
| `missing_nhr` | Content that warranted NHR marker but was not flagged |
| `weak_evidence` | Claim accepted as fact but marked as assumed in diagnostic |
| `missing_constraint` | Known constraint from Input not reflected in artifacts |
| `source_of_truth_conflict` | Two artifacts contain incompatible definitions without flagging |
| `versioning_error` | Artifact versioning or changelog not maintained correctly |
| `overcomplicated_text` | Output unnecessarily dense relative to input complexity |
| `input_gap` | Absent information that weakened an artifact (attribution: input) |
| `needs_human_decision` | Gap requiring a decision only the human can make |

**Strategic and roadmap scope — additional types:**

| Type | Use when |
|---|---|
| `decorative_kpi` | Numeric target generated without human input or explicit source |
| `tactical_drift` | Tactical item converted to strategy without challenge or translation |
| `roadmap_overreach` | Roadmap generated before all required KAs were complete |
| `icp_vagueness` | ICP defined by mindset or aspiration, not observable criteria |
| `unfalsifiable_thesis` | Thesis cannot be proven wrong — it is a vision statement |
| `missing_anti_priorities` | No explicitly deferred items — prioritization without trade-offs |
| `unlinked_phase` | Roadmap phase has no link to a KR or validation milestone |

**Implementation scope — additional types:**

| Type | Use when |
|---|---|
| `missing_error_state` | Flow or feature documents the happy path but no failure conditions |
| `ambiguous_flow_step` | Step described at intention level, not execution level |
| `untestable_acceptance_criteria` | Criterion requires human judgment to verify |
| `missing_rls` | Feature or flow touches a table whose RLS policies are not documented |
| `boundary_violation_risk` | Rule from invariants section not reflected in feature spec touching that boundary |
| `undocumented_empty_state` | View or list has no documented empty state |
| `undocumented_loading_state` | Async operation has no documented loading state |
| `buried_decision` | Rule governing BUILD behavior written as explanation, not explicit rule |
| `runtime_ambiguity` | Behavior documented without specifying which runtime it applies to |
| `schema_mismatch` | Feature spec references field, table, or operation not in schema.md |
| `assumed_behavior` | Flow step assumes a behavior not documented as triggered by that step |
| `permission_gap` | User action documented without specifying who is authorized to perform it |
| `strategic_misalignment` | Technical artifact contradicts or ignores a decision in Strategic Artifacts |

### Artifact / Section
Name the specific artifact and section where the defect appears.
Example: `product-thesis.md / Assumptions` · `stack.md / Performance Contract` · `feature-editor.md / Flow 1`

### YAML ID
The question ID from the questions file that this defect maps to, if applicable.
Example: `SK-03` · `DB-08` · `FN-09` · `SA-02`
Leave blank (`—`) if the defect does not map to a specific question.

### Severity

| Value | Meaning |
|---|---|
| `blocking` | Orchestrator must not proceed without resolution |
| `high` | Materially weakens artifact or roadmap |
| `medium` | Reduces artifact quality or reliability |
| `low` | Minor issue, does not affect artifact usability |

### Attribution
Use only these values. Always include a one-sentence reason after the value.

| Value | Meaning |
|---|---|
| `input` | Source material did not provide what was needed |
| `agent` | Agent invented, hid, or ignored available information |
| `human_decision_needed` | Requires a decision only the human can make |
| `mixed` | Combination of weak input and poor synthesis — explain both |

Example: `input — no source document defines the GTM segment`
Example: `agent — diagnostic report flagged this claim as assumed; artifact presents it as fact`

When unsure: lean toward `mixed` rather than defaulting to `agent`.

### Next step
Use only these values:

| Value | Meaning |
|---|---|
| `orchestrator_revise` | Orchestrator corrects the artifact |
| `human_input_needed` | Human must provide missing information |
| `human_decision_needed` | Human must make a decision |
| `open_question` | Register in open-questions file and proceed |
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
