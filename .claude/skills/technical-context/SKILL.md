---
name: technical-context
description: "Convert raw implementation documents in Input/ into structured, agent-executable implementation artifacts: stack.md, schema.md, architecture.md, and feature specs. Use when preparing implementation context before creating Linear issues, when legacy implementation docs exist and need to be formalized, or when checking whether existing artifacts are complete and up to date."
metadata:
  version: "1.0"
  last_updated: "2026-06-01"
---

# Implementation Context Skill

## Core Thesis

An implementation artifact is not complete because it is detailed. It is complete when
BUILD can implement any issue that touches it without asking a single question.

```
Input/Implementation/ (raw docs, legacy files, any format)
  → Phase 0: Diagnostic (_technical_analysis.md)     ← Diagnostic Analyst subagent
  → Phase 1: stack.md
  → Phase 2: schema.md
  → Phase 3: architecture.md
  → Phase 4: features/ children                 ← one file per feature with material
  → Review Checkpoint                           ← Adversarial Reviewer subagent
  → Phase 5: Handoff to PM agent
  → _technical_analysis.md deleted
```

**Prerequisite rule:** Linear issues cannot be created for a phase until the implementation
artifacts that phase depends on are complete and in `active` status.

---

## Agent Architecture

| Role | File | Responsibility |
|---|---|---|
| Orchestrator | this skill | Coordinates, generates artifacts, versions, publishes, decides |
| Diagnostic Analyst | `.claude/agents/diagnostic-analyst.md` | Reads Input/, produces structured diagnostic report against implementation-questions.yaml |
| Adversarial Reviewer | `.claude/agents/adversarial-reviewer.md` | Reviews generated artifacts, produces two-block review report |

**Core principle:** Subagents analyze and challenge. The Orchestrator decides, writes, versions, and publishes.

Subagents do not write files. Subagents do not publish artifacts. Subagents do not make implementation decisions.

### Invoking the Diagnostic Analyst

Pass these parameters:
- `scope`: `"implementation"`
- `project_path`: absolute path to the project folder
- `input_path`: absolute path to `Input/Implementation/`
- `strategic_artifacts_path`: absolute path to `Strategic Artifacts/`
- `artifact_questions_path`: absolute path to `.claude/skills/technical-context/reference/implementation-questions.yaml`

The agent reads both `Input/Implementation/` and `Strategic Artifacts/` as input — technical
source documents plus the strategic context (product thesis, user architecture, product
architecture, objectives architecture). It evaluates every question in
`implementation-questions.yaml` against the combined material and returns a structured
diagnostic report.

Do not read `Input/` or `Strategic Artifacts/` yourself before the agent has run.

### Invoking the Adversarial Reviewer

Invoked once, after all artifacts are generated.

Pass these parameters:
- `review_scope`: `"implementation"`
- `artifacts_path`: absolute path to `Technical Artifacts/`
- `input_path`: absolute path to `Input/Implementation/`
- `diagnostic_report_path`: absolute path to `Technical Artifacts/_technical_analysis.md`
- `artifact_questions_path`: absolute path to `.claude/skills/technical-context/reference/implementation-questions.yaml`

---

## Execution Commands

| Command | Action |
|---|---|
| `/impl-start` | Executes Phase 0. Invokes Diagnostic Analyst, produces diagnostic. Presents Input Analysis Summary. Waits for human confirmation before generating any artifact. |
| `/impl-next` | Executes the next pending phase. One phase at a time. Produces output, presents summary, waits for confirmation. |
| `/impl-run [artifact]` | Generates or regenerates a specific artifact. Creates a new version if it already exists. Examples: `/impl-run stack`, `/impl-run schema`, `/impl-run feature:editor` |
| `/impl-status` | Shows current state of all artifacts: complete, in progress, missing, or has NHR markers. |
| `/impl-diagnose` | Executes Phase 0 only. Does not generate any artifact. |
| `/impl-check` | Compares existing artifacts in `Technical Artifacts/` against current `Input/Implementation/`. Reports what is outdated, incomplete, or missing. Does not regenerate — only reports. |

**Default behavior (no command):** if the user provides Input without a command,
the agent executes `/impl-start` automatically.

**Output mode:**
Default — silent: all intermediate processing happens internally. A single clean
summary is emitted at the end of the command.
`--verbose` — shows full incremental output. Use when debugging or auditing.

---

## Output Format Rule

All output rendered to the user must use standard markdown only:
- `| col | col |` tables
- Prose paragraphs
- Markdown headers (`##`, `###`)

No ASCII box-drawing characters. No unicode drawing symbols.

---

## Folder Structure

```
[Project]/
├── Input/
│   ├── Strategic/                      ← KAs and strategic context (read-only for Phase 2)
│   └── Implementation/                 ← raw technical docs, legacy files, stack docs
│
├── Strategic Artifacts/                ← output of Phase 1 (readable for strategic context)
│
├── Technical Artifacts/                ← all generated artifacts live here
│   ├── stack.md
│   ├── schema.md
│   ├── architecture.md
│   ├── features/
│   │   └── feature-[name].md
│   ├── _technical_analysis.md          ← temporary; deleted after handoff
│   ├── technical-change-log.md
│   └── technical-open-questions.md
│
└── .claude/
    └── skills/
        └── technical-context/
            └── reference/
                └── implementation-questions.yaml
```

**Rules:**
- `Input/Implementation/` is the drop zone for technical source documents. Read-only.
- `Strategic Artifacts/` is readable for strategic context (product thesis, user architecture, product architecture). Do not modify.
- All agent-generated files live in `Technical Artifacts/`.
- `_technical_analysis.md` is temporary scaffolding. Deleted before handoff.
- `technical-change-log.md` is always maintained. No artifact is created or materially changed without a log entry.
- `technical-open-questions.md` is created as soon as any artifact generates a gap.

---

## Required Artifacts

| # | Artifact | Function |
|---|---|---|
| 1 | `stack.md` | Technologies, performance contract, environments, agent conventions |
| 2 | `schema.md` | Data model, entities, RLS, business rules, sync behavior, indices |
| 3 | `architecture.md` | Application modes, navigation, page inventory, decisions, invariants |
| 4 | `features/feature-[name].md` | Per-feature flows, UI states, error conditions, acceptance criteria |

Evaluation criteria: `.claude/skills/technical-context/reference/implementation-questions.yaml`

---

## Versioning Rules

Every artifact includes frontmatter:

```md
---
artifact: [stack | schema | architecture | feature-[name]]
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: false
---
```

**Version numbering:**
- `v0.x` — draft, not yet accepted
- `v1.0` — accepted by the human as source of truth
- `v1.x` — meaningful update to an accepted artifact
- `v2.0+` — major revision (new tables, stack change, architectural rethink)

**Status values:** `draft` · `active` · `needs_human_review` · `superseded`

**Cascade rule:** when `schema.md` changes materially, evaluate whether `architecture.md`
and affected `features/` are still accurate. Mark them `needs_human_review` if affected.
Do not silently update downstream artifacts.

---

## Phase 0 — Diagnostic (_technical_analysis.md)

**Triggered by:** `/impl-diagnose`, `/impl-start`, or first Input without a command.

**Step 1 — Invoke the Diagnostic Analyst subagent.**

Pass the project path, Input/ path, and `implementation-questions.yaml` path.
Wait for the diagnostic report. Do not read Input/ yourself first.

**Step 2 — Compose _technical_analysis.md.**

Use the diagnostic report as the primary source. Structure the file:

```md
# Implementation Input Analysis (internal scaffolding — delete after session)

## Sources available
List of files in Input/Implementation/ and Strategic Artifacts/ with a one-line description of each.

## Missing sources
Documents referenced in Input/ that are not present.
For each: name, which doc references it, what it likely contains.
Signal only — does not block artifact generation.

## Coverage map
For each artifact, what is answered, partially answered, and absent.
Based on implementation-questions.yaml — evaluate each question against Input.

| Artifact | Answered | Partial | Absent |
|---|---|---|---|
| stack | ... | ... | ... |
| schema | ... | ... | ... |
| architecture | ... | ... | ... |
| feature specs | ... | ... | ... |
| cross-artifact coherence | ... | ... | ... |
| strategic alignment | ... | ... | ... |

## Decisions buried in prose
Statements that function as rules but are written as explanations.
These must be extracted and formalized in the artifact.

## Assumed behaviors
Behaviors presented as implemented but without confirmation in the source.
Must be marked as NHR in artifacts until verified.

## Source conflicts
Contradictions between Input/ documents.

| Conflict ID | Topic | Sources | Conflict | Impact | Recommendation |
|---|---|---|---|---|---|

## Feature inventory
List of features found in Input/ with enough material to generate a feature spec.
For each: name, source docs, completeness estimate.

## Non-omittable questions
Questions that must be answered before artifacts can be marked active.
These block the PM agent from creating issues.

## Proposed generation order
Which artifacts to generate first and why.
```

### Input Analysis Summary (human checkpoint)

Present this summary once at the end of `/impl-start`:

```md
## Input Analysis Summary

### What Input covers well
[Sections with strong, specific, agent-executable answers]

### What Input covers partially
[Sections with weak, implicit, or prose-buried answers]

### What Input does not cover
[Gaps that will require NHR markers or open questions]

### Decisions buried in prose
[Rules found in explanation form — will be extracted in artifacts]

### Source conflicts found
[Contradictions between documents]

### Features with enough material for specs
[List of feature names found in Input/]

### Non-omittable questions
[Questions that block artifact completion]

### Proposed plan
Phase 1: stack.md — reason
Phase 2: schema.md — reason
Phase 3: architecture.md — reason
Phase 4: features/ — [list of features]

Confirm to proceed, or adjust before I begin.
```

This is the only mandatory human pause before artifact generation.

---

## Generation Principles

### Principle 1 — Do not generate what is not in Input

The agent must not fill artifact sections with its own inferences when Input does not cover them.

| Situation | Correct agent behavior |
|---|---|
| Section is missing but not blocking | Leave empty with an explicit question → OQ-XXX |
| Section affects BUILD decisions or constraints | Ask before generating. Do not generate first and mark NHR after. |
| Human cannot answer and agent must proceed | Propose options with reasoning and wait for choice, or leave as `[TO BE DEFINED]` |

**For schema specifically:** never invent field types, constraints, or RLS policies.
If a field exists in a flow but not in the schema, surface it as a gap — do not add it speculatively.

**For stack specifically:** never invent performance thresholds. If thresholds exist in Input
as principles ('must be fast'), extract them as-is and mark them as requiring formalization → OQ-XXX.

### Principle 2 — Complexity proportional to Input

The detail level of an artifact must reflect the coverage of Input, not the ambition of the template.

- If Input covers a topic briefly, the artifact does not produce 5 sections on that topic.
- A sparse but honest artifact is more useful than a dense artifact built on agent inference.
- Sections with no Input coverage are left with an explicit question, not filled structurally.

### Principle 3 — Extract, do not restate

The value of this skill is not copying Input into a different format. It is:
- Extracting decisions buried in prose and making them explicit rules
- Surfacing conflicts between documents that would cause inconsistent implementation
- Identifying gaps that would force BUILD to make assumptions mid-implementation

An artifact that only reorganizes what was already in Input is not complete.

---

## Procedure

### Phase execution rule

Every phase always executes — phases are the evaluation mechanism, not conditional steps.

- If a phase has sufficient material → generate the artifact.
- If a phase has insufficient material → the phase delivers a **gap report**: what is missing,
  what assumptions would be required, what the human needs to provide.

A phase is never skipped to determine if it should be skipped.

---

### Phase 1 — stack.md

Reads `_technical_analysis.md` → evaluates against SK-01 through SK-19 →
extracts technology decisions, performance thresholds, conventions, environment configs.

**Critical extraction steps:**
1. For each technology: name, role, what it does NOT do in this system.
2. For performance: extract all measurable thresholds. If thresholds are in prose, formalize them.
   If they are missing, mark as → OQ-XXX.
3. For conventions: restate as enforced rules, not preferences.
4. For environments: produce one configuration table per environment.

Present summary + NHR markers. Wait for confirmation.

---

### Phase 2 — schema.md

Reads `_technical_analysis.md` + `stack.md` → evaluates against DB-01 through DB-15.

**Critical extraction steps:**
1. For each table: produce field-level documentation with type, constraints, purpose note.
2. For RLS: produce a policy table for every table × every operation.
3. For business rules: extract every automatic operation from prose into an explicit rule block.
4. For sync behavior: document per-field which layer is authoritative.
5. For schema transition: document objective vs. effective schema if they differ.

If a flow in Input references a field or table not found in the schema documentation,
surface it as a gap — do not add it to the schema speculatively.

Present summary + NHR markers. Wait for confirmation.

---

### Phase 3 — architecture.md

Reads `_technical_analysis.md` + `stack.md` + `schema.md` → evaluates against AR-01 through AR-12.

**Critical extraction steps:**
1. For each mode: purpose, primary behavior, explicit exclusions.
2. For navigation: exact dimensions, coordination rules, transition specs.
3. For routes: auth requirement, redirect on auth failure, mobile behavior.
4. For decisions: extract from prose into explicit rule format with rationale.
5. For invariants: extract boundary rules from incident references, notes, and constraints.

Present summary + NHR markers. Wait for confirmation.

---

### Phase 4 — features/

**Triggered by:** feature inventory in `_technical_analysis.md` listing features with sufficient material.

For each feature with sufficient material:
1. Create `Technical Artifacts/features/feature-[name].md`.
2. Evaluate against FN-01 through FN-12.
3. Document all flows as numbered steps.
4. Document all error, loading, and empty states.
5. Document data operations per step.
6. State acceptance criteria as binary, verifiable conditions.
7. For gaps: leave as `[TO BE DEFINED]` → OQ-XXX. Do not invent behavior.

After generating each feature spec, present a summary and wait for confirmation before the next.

Features with insufficient material → gap report listing what is missing, not a partial spec.

---

### Review Checkpoint

After all artifacts are generated:

1. Invoke the Adversarial Reviewer with `review_scope: "implementation"`.
2. Present the full two-block report.
3. Handle `orchestrator_revise` items — revise and version affected artifacts.
4. Present `human_decision_needed` items — wait for response.
5. Register `open_question` items in `technical-open-questions.md`.
6. Wait for human confirmation before proceeding to handoff.

---

### Phase 5 — Handoff

Delete `_technical_analysis.md`. Produce:

```md
# Implementation Context Handoff

## Artifacts Ready
[List of artifacts in active status with version]

## Artifacts with Open Questions
[List of artifacts with NHR markers or open questions — what is still unresolved]

## What PM Agent Can Use Now
[Which artifacts are complete enough to generate issues for which phases]

## Decisions Extracted from Input
[Rules that were formalized from prose — confirm these are correct before BUILD uses them]

## Conflicts Resolved
[How source conflicts were resolved — the human must confirm these decisions hold]

## Constraints BUILD Must Not Override
[Non-negotiable rules extracted from the artifacts — these apply to every issue]

## Open Questions Blocking Issue Creation
[Questions that must be resolved before issues can be written for affected features]

## Skill Review Flags
[Items that suggest this skill or its questions need updating]
```

---

## Source Reconciliation Protocol

When multiple Input/ documents cover the same topic, do not assume they are consistent.

| Conflict type | Meaning |
|---|---|
| Definition conflict | Two documents define the same entity, field, or behavior differently |
| State conflict | One document shows a feature as complete; another shows it as planned |
| Constraint conflict | Documents imply different performance, RLS, or architectural constraints |
| Runtime conflict | Web runtime and desktop runtime have different behaviors, undistinguished |
| Time conflict | Older document describes a design that a newer document supersedes |

**Rule:** a clean artifact produced by hiding contradictions is a failure.
A useful artifact preserves the conflict until it is resolved or intentionally accepted.

---

## Open Questions Registry

`technical-open-questions.md` tracks all gaps and unresolved decisions.

```md
---
artifact: technical-open-questions
version: 0.1
status: active
last_updated: YYYY-MM-DD
---

# Implementation Open Questions

## Open Questions

| ID | Question / Gap | Artifact | Section | Current assumption | Blocks | Priority |
|---|---|---|---|---|---|---|

## Resolved Decisions

| ID | Original question | Decision | Resolution date | Decided by |
|---|---|---|---|---|
```

**Cross-reference protocol:** every NHR marker inside an artifact must carry its OQ-ID:
```
[Needs Human Review] RLS policy for margins table on update not defined → OQ-003
```

When a question is resolved: (1) move to Resolved in `technical-open-questions.md`,
(2) replace NHR marker in the artifact with the decision, increment version,
(3) log in `technical-change-log.md`. All three in the same operation.

---

## Loop Dimensions Check

| Dimension | Validation Question |
|---|---|
| D1 Completeness | Can BUILD implement any issue touching these artifacts without asking a question? |
| D2 Traceability | Is every rule in the artifact traceable to a source in Input/ or a human decision? |
| D3 Conflict-free | Are all source conflicts resolved or explicitly preserved as open questions? |
| D4 Agent-executable | Are acceptance criteria binary and testable without human judgment? |
| D5 Constraints | Are all hard constraints extracted as explicit rules, not embedded in prose? |
| D6 Gaps surfaced | Are all gaps marked as NHR or open questions — not silently filled? |
| D7 Memory | Were all changes and decisions logged in `technical-change-log.md`? |
| D8 Handoff-ready | Can `Technical Artifacts/` feed the PM agent without reinterpretation? |

**Final exit question:** Can the PM agent create a Linear issue for any feature in these artifacts
and have BUILD implement it correctly — without the PM agent, BUILD, or the human
having to invent, assume, or discover missing context mid-implementation?
