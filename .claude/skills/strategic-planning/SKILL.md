---
name: strategic-planning
description: "Use this skill to convert loose business intention and source documents into structured Strategic Artifacts and an actionable strategic-roadmap.md. Part of Phase 1 of the Deus Product Development Harness. ALWAYS use when the user: mentions roadmap, strategic plan, product strategy, or planning phase; shares loose docs and asks to structure or turn into a plan; asks about ICP, product thesis, user-architecture, product-architecture, or objectives in a planning context; wants to prepare for task planning, Linear issues, or initiative definition; says 'help me plan', 'build the roadmap', 'I need the strategy', 'give me the plan', 'define the ICP'; references Deus, Strategic Artifacts, strategic-change-log, strategy-brief, product-thesis, user-architecture, product-architecture, objectives-architecture, or strategic-roadmap. Do NOT skip this skill if loose strategic material exists and needs to become an actionable plan."
metadata:
  version: "6.0"
  last_updated: "2026-05-30"
  patches:
    - "v6.0 — verbose toggle (default silent, --verbose for incremental output)"
    - "v6.0 — ASCII format rule (markdown tables only, no box-drawing characters)"
    - "v6.0 — missing document soft signal (non-blocking, signals in _analysis.md and summary)"
    - "v6.0 — phase vs output rule (phases always execute; artifact is conditional on material)"
---


# Strategic Planning Skill

## Core Thesis

This skill preserves intention, criterion, and context across the production cycle.

The output should not be what AI happened to generate. It should be the product that was actually decided.

```text
Input/ (source documents)
  → Phase 0: Diagnostic (_analysis.md)        ← Diagnostic Analyst subagent
  → Phase 1: strategy-brief.md + product-thesis.md
  → Phase 2: user-architecture.md + product-architecture.md
  → Phase 3: objectives-architecture.md
  → Phase 4: features/ children (if applicable)
  → Phase 5: strategic-roadmap.md
  → Review Checkpoint (KAs)                   ← Adversarial Reviewer subagent
  → Review Checkpoint (Roadmap)               ← Adversarial Reviewer subagent
  → Phase 6: Handoff to Task Planning
  → _analysis.md deleted
```

**Prerequisite rule:** `strategic-roadmap.md` cannot be generated until all 5 Strategic Artifacts are complete. The roadmap is the output of the KA process, not a shortcut to it.

---

## Agent Architecture

This skill operates with three roles. The Orchestrator is this agent. The two subagents are defined in `.claude/agents/`.

| Role | File | Responsibility |
|---|---|---|
| Orchestrator | this skill | Coordinates, generates artifacts, versions, publishes, decides |
| Diagnostic Analyst | `.claude/agents/diagnostic-analyst.md` | Reads Input/, produces structured diagnostic report |
| Adversarial Reviewer | `.claude/agents/adversarial-reviewer.md` | Reviews KAs and roadmap, produces two-block review report |

**Core principle:** Subagents analyze and challenge. The Orchestrator decides, writes, versions, and publishes.

Subagents do not write files. Subagents do not publish artifacts. Subagents do not make strategic decisions.

### Invoking the Diagnostic Analyst

Invoke at the start of `/sp-start` or `/sp-diagnose`, before composing `_analysis.md`.

Parameters to pass:
- `scope`: `"strategic"`
- `project_path`: absolute path to the project folder
- `input_path`: absolute path to `Input/Strategic/`
- `artifact_questions_path`: absolute path to `.claude/skills/strategic-planning/references/artifact-questions.yaml`

Use the returned diagnostic report as the primary source for composing `_analysis.md`. Do not read `Input/` yourself before the agent has run — the agent does the heavy reading.

### Invoking the Adversarial Reviewer

Invoke twice per planning session.

**Invocation 1 — after all KAs are generated, before roadmap:**
- `review_scope`: `"strategic"`
- `artifacts_path`: absolute path to `Strategic Artifacts/`
- `input_path`: absolute path to `Input/Strategic/`
- `diagnostic_report_path`: absolute path to `Strategic Artifacts/_analysis.md`
- `artifact_questions_path`: absolute path to `.claude/skills/strategic-planning/references/artifact-questions.yaml`
- `review_format_path`: absolute path to `.claude/references/review-report-format.md`

**Invocation 2 — after roadmap is generated:**
- `review_scope`: `"roadmap"`
- Same paths as above

After each invocation, present the full review report to the human using the Review Checkpoint protocol below.

---

## Execution Commands

These commands control how the agent executes this skill. They can be used at any point in the session.

| Command | Action |
|---|---|
| `/sp-diagnose` | Executes Phase 0 only. Invokes Diagnostic Analyst, reads all Input/, produces full diagnostic. Does not generate any artifact. Usable at any moment, including mid-session. |
| `/sp-start` | Executes Phase 0 + presents Input Analysis Summary. Waits for human confirmation before any artifact is generated. |
| `/sp-next` | Executes the next pending phase. One phase at a time. Produces output, presents summary, waits for confirmation. |
| `/sp-run [artifact]` | Executes or recalibrates a specific KA. Creates a new version if the artifact already exists. Example: `/sp-run product-thesis` |
| `/sp-status` | Shows current state of all KA and the roadmap: complete, in progress, missing, or has NHR markers. |
| `/sp-roadmap` | Attempts to generate `strategic-roadmap.md`. If any KA is missing or incomplete, fails with an explicit message listing what is blocking. |
| `/sp-challenge [item]` | Applies Challenge Protocol to a specific claim, feature, or tactical item. |
| `/sp-conflict` | Shows all open conflicts from the Conflict Map in `_analysis.md`. |
| `/sp-questions [filter]` | Shows open questions from `open-questions.md`. Filters: no filter = all by priority · `high` = high priority only · `[artifact-name]` = filtered by origin artifact · `blocking` = only questions blocking a KA or the roadmap. |

**Default behavior (no command):** if the user provides Input without a command, the agent executes `/sp-start` automatically.

**Output mode flags (append to any command):**
`--verbose` — shows full incremental output during execution: thought process, intermediate steps, subagent returns, and diagnostic reasoning as it builds.
Default (no flag) — silent mode: all intermediate processing happens internally. A single clean summary is emitted once at the end of the command. No repeated blocks, no incremental rendering.

Use `--verbose` when debugging the skill, validating reasoning, or auditing a diagnostic. Use default (silent) for production runs.

---

## Output Format Rule

All output rendered to the user — summaries, tables, reports, checkpoints, review blocks — must use standard markdown only:

- `| col | col |` tables
- Prose paragraphs
- Markdown headers (`##`, `###`)

**No ASCII box-drawing characters.** No multi-column terminal layouts. No unicode drawing symbols (─ ┌ └ │ ╔ ═ etc.).

This rule applies in both default (silent) and `--verbose` mode. It applies to all commands and all output templates in this skill.

---

## Folder Structure

```
[Project]/
├── CLAUDE.md                          ← project context (not skill logic)
├── .claude/
│   ├── agents/
│   │   ├── diagnostic-analyst.md
│   │   └── adversarial-reviewer.md
│   └── references/
│       └── review-report-format.md
├── Strategic Artifacts/
│   ├── strategy-brief.md
│   ├── product-thesis.md
│   ├── user-architecture.md
│   ├── product-architecture.md       ← parent; references features/ children
│   ├── objectives-architecture.md    ← fifth KA: OKRs, KPIs, validation milestones
│   ├── strategic-roadmap.md
│   ├── strategic-change-log.md
│   ├── open-questions.md
│   └── features/
│       ├── [feature-name].md
│       └── transversales.md
└── Input/
    └── [source-file].md
```

**Rules:**
- `Input/` is read-only. The agent never writes to it.
- All agent-generated files live in `Strategic Artifacts/`.
- `_analysis.md` is temporary scaffolding. Lives in `Strategic Artifacts/` during the session. Deleted before final handoff.
- `strategic-change-log.md` is always maintained. No artifact is created or materially changed without a log entry.
- `open-questions.md` is created as soon as any artifact generates a gap or open question.

---

## Required Strategic Artifacts

| # | Artifact | Function |
|---|---|---|
| 1 | `strategy-brief.md` | Strategic direction: problem, ICP, value prop, differentiation, principles, priorities |
| 2 | `product-thesis.md` | Central product bet: falsifiable claim, assumptions, evidence, falsification risks |
| 3 | `user-architecture.md` | Users: ICP signals, jobs/frictions, exclusions, adoption logic |
| 4 | `product-architecture.md` | Product structure: modules, flows, core features, constraints, dependencies |
| 5 | `objectives-architecture.md` | Objectives: OKRs, KPIs, validation milestones, success signals per phase |

Full templates: `references/templates.md`
Evaluation criteria and failure signals: `references/artifact-questions.yaml`

---

## Versioning Rules

Every Knowledge Artifact includes frontmatter:

```md
---
artifact: [name]
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
---
```

**Version numbering:**
- `v0.x` — draft, not yet accepted as source of truth
- `v1.0` — accepted by the human as source of truth
- `v1.x` — meaningful update to an accepted artifact
- `v2.0+` — major revision when thesis, ICP, architecture, or roadmap changes materially

**Status values:** `draft` · `active` · `needs_human_review` · `superseded` · `archived`

**Revisit rule:** any KA can be revisited at any point using `/sp-run [artifact]`. A revisit always produces a new version. The previous version is not deleted — its status changes to `superseded`. Every version increment produces an entry in `strategic-change-log.md`.

**Cascade rule:** when a KA is revised, the agent evaluates whether downstream artifacts are affected. If they are, it marks them as `needs_human_review` and proposes what to update. It does not silently update downstream artifacts without presenting the impact.

**Only one version of each artifact should be marked `current: true`.**

---

## Phase 0 — Diagnostic (_analysis.md)

**Triggered by:** `/sp-diagnose`, `/sp-start`, or any first Input without a command.

**Step 1 — Invoke the Diagnostic Analyst subagent.**

Pass the project path and Input/ path. Wait for the diagnostic report to return. Do not read Input/ yourself before the agent has run.

**Step 2 — Compose _analysis.md from the diagnostic report.**

Use the diagnostic report as the primary source. Structure `_analysis.md` using the schema below. The Orchestrator authors the file — the subagent provides the raw material.

`_analysis.md` is working memory, not a deliverable. It is deleted before the final handoff.

### Structure of _analysis.md

```md
# Input Analysis (internal scaffolding — delete after session)

## Sources available
List of files in Input/ with a one-line description of each.

## Missing sources
Documents referenced in Input/ that are not present in Input/.
For each missing document:
- Name or description as referenced in the source
- Which document references it
- What it likely contains based on context
- Signal: "Uploading this document could improve precision of [artifact]. Not required to proceed."

This section does not block artifact generation. It is a signal, not a gate.

## Ontological map
Key entities found across documents and their relationships.

| Entity | Type | Appears in | Tension with |
|---|---|---|---|
| [concept] | User / Strategic / Tactical / Technical | doc1, doc3 | doc3 vs doc7 |

## Coverage map
For each KA, what is answered, partially answered, and absent in the Input.
Based on artifact-questions.yaml — evaluate each question against the Input.

| KA | Answered | Partial | Absent |
|---|---|---|---|
| strategy-brief | ... | ... | ... |
| product-thesis | ... | ... | ... |
| user-architecture | ... | ... | ... |
| product-architecture | ... | ... | ... |
| objectives-architecture | ... | ... | ... |

## Claims with evidence
Statements from Input that have direct support. These become artifact content.

## Assumed claims
Statements presented as fact but without supporting evidence.
Must be marked as hypotheses in artifacts, not facts.

## Source conflicts
Contradictions, overlaps, outdated assumptions, competing definitions.

| Conflict ID | Topic | Sources | Conflict | Strategic impact | Recommendation | NHR? |
|---|---|---|---|---|---|---|

## Tactical inputs found
Tactical requests, features, bugs, or roadmap fragments found in Input.

| Tactical item | Source | Strategic interpretation | Thesis link | Constraint | Recommendation |
|---|---|---|---|---|---|

## Candidates for open-questions.md
Gaps that no source answers and that block or weaken an artifact.

## Non-omittable questions
Questions that must be answered, assumed explicitly, or converted into validation objectives
before roadmap generation can proceed.

## Proposed generation order
Which artifacts to generate first and why.
```

### Input Analysis Summary (human checkpoint)

After composing `_analysis.md`, present this summary **once** at the end of `/sp-start`. Do not emit it incrementally during the diagnostic pass. In `--verbose` mode, incremental output is allowed throughout execution; in default (silent) mode, this is the single output rendered to the user.

```md
## Input Analysis Summary

### What the Input covers well
[Strategic questions answered with evidence]

### What the Input covers partially
[Areas with weak, incomplete, or assumed answers]

### What the Input does not cover
[Gaps that will require NHR markers or open questions]

### Source conflicts found
[Contradictions between documents — only meaningful ones]

### Tactical items found
[Feature ideas, issues, or roadmap fragments that imply strategy]

### Referenced documents not in Input/
[Only if any were found. Format: "[Document name] is referenced in [source doc] — uploading it could improve precision of [artifact]. Not required to proceed."]
[Omit this section if no missing documents were detected.]

### Non-omittable questions
[Questions that block or weaken the roadmap if unanswered]

### Proposed plan
Phase 1: [artifacts] — reason
Phase 2: [artifacts] — reason
Phase 3: [artifacts] — reason
Phase 4: features/ (if applicable)
Phase 5: strategic-roadmap.md

Confirm to proceed, or adjust before I begin.
```

This is the only mandatory human pause before artifact generation.

---

## Review Checkpoint Protocol

The Adversarial Reviewer is invoked twice: after all KAs are complete, and after the roadmap is generated.

### How to invoke

Invoke the Adversarial Reviewer subagent with the parameters listed in the Agent Architecture section. Wait for the full two-block report to return.

### How to present the report

Present the report to the human exactly as structured in `.claude/references/review-report-format.md`. Do not summarize or compress it. The human needs both blocks fully visible.

### How to handle the report

After the human reviews:

1. **`orchestrator_revise`** items — handle yourself. Revise and version the affected artifacts. Log in `strategic-change-log.md`.
2. **`human_input_needed`** or **`human_decision_needed`** items — present as a consolidated list. Wait for human response before proceeding.
3. **`open_question`** items — confirm with human before registering in `open-questions.md`.
4. **`accept_as_assumption`** items — mark explicitly in the artifact. Log in `strategic-change-log.md`.
5. **`flag_for_skill_review`** items — note in the handoff document for future skill iteration.

Wait for human confirmation before proceeding to the next phase.

---

## Source Reconciliation Protocol

When reading `Input/`, do not assume all documents are equally current, equally reliable, or mutually consistent.

**Never silently merge conflicting sources.**

### Conflict types

| Type | Meaning |
|---|---|
| Definition conflict | Two documents define the same concept differently |
| Priority conflict | Documents imply different priorities or sequencing |
| ICP conflict | Different users or segments are treated as primary |
| Product conflict | Features or modules imply different product direction |
| Technical conflict | Documents imply incompatible implementation paths |
| Evidence conflict | One document treats a claim as validated; another treats it as assumption |
| Time conflict | Older and newer documents disagree; source of truth is unclear |

### Conflict handling

For each meaningful conflict, produce a conflict record in `_analysis.md`:

| Conflict ID | Topic | Sources | Conflict | Strategic impact | Recommendation | NHR? |
|---|---|---|---|---|---|---|

### Resolution rules

1. If one source is clearly newer and consistent with current project direction → recommend it as source of truth.
2. If one source is tactical and another is strategic → do not let tactical override strategic without human review.
3. If both sources are plausible → mark `Needs Human Review`.
4. If the conflict does not block artifact generation → proceed with the safest assumption and record it in `open-questions.md`.
5. If the conflict affects ICP, thesis, product architecture, roadmap sequence, or validation objectives → pause and ask a Human Review Question.

**Rule: a clean artifact produced by hiding contradictions is a failure. A useful artifact preserves strategic tension until it is resolved or intentionally accepted.**

---

## Tactical-First Planning Guardrail

Strategic planning may begin from tactical issues, feature ideas, bugs, or execution requests. This is allowed.

However, **tactical input must not automatically become roadmap.**

When the user starts with tactical items, the agent translates each item into its strategic meaning before accepting it.

### Tactical item evaluation

For each tactical item, ask:
- What strategic objective does this serve?
- Which user or ICP does it benefit?
- Which product thesis does it support?
- Is it core, enabling, supporting, or distracting?
- Is it validated, assumed, or speculative?
- What constraint does it create?
- What does it displace if prioritized?
- Does it belong in the roadmap, backlog, validation queue, or archive?

### Tactical-to-strategic map

| Tactical item | Strategic objective | User/ICP | Thesis link | Evidence | Constraint | Recommendation | Disposition |
|---|---|---|---|---|---|---|---|

**Disposition values:** Roadmap candidate · Validation needed · Backlog · Defer · Reject · Needs Human Review

### Challenge triggers

Challenge a tactical item when:
- it sounds useful but does not support the thesis
- it benefits a non-primary user
- it adds complexity before validating the core loop
- it is a feature request disguised as strategy
- it requires resources the project does not have
- it solves a symptom instead of the strategic problem
- it belongs to a later phase

**Rule: do not convert tactical items into strategy. Translate, challenge, and align them.**

---

## Objectives Architecture (Fifth Knowledge Artifact)

`objectives-architecture.md` is the fifth required Knowledge Artifact.

It defines the measurable layer of the strategy: what the product must demonstrate at each phase, what signals validate the thesis, and what KPIs should guide roadmap decisions.

**Why it is a separate artifact:** roadmaps without objectives produce work that cannot be evaluated. If the roadmap does not define what success looks like per phase, there is no way to know if the product is working. This artifact closes that gap.

### Minimum viable structure

```md
---
artifact: objectives-architecture
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
---

# Objectives Architecture

## Phase [N]: [Name]

**What must be true at the end of this phase:**
[Free text. Defined by human or proposed and accepted. Not generated from template.]

**Signals that would indicate it is working (2–3 max):**
- [Signal 1 — defined by human or accepted proposal]
- [Signal 2]

**Signals that would indicate it is NOT working (falsification):**
- [Signal 1]

**KPIs and targets:**
[Only populated when the human defines or accepts an explicit agent proposal.
Leave as [TO BE DEFINED] → OQ-XXX until then.]

## Open Questions
[Questions that must be answered before this artifact can be completed.]
```

**Rules:**
- Sections are added only when the Input supports them. An empty section is not added structurally.
- Numeric targets are never agent-invented. They are human-defined, human-accepted proposals, or `[TO BE DEFINED]`.
- External benchmarks are allowed only when marked `[external reference — not a product decision]`.

Full expanded template (for when Input is sufficient): `references/templates.md`

### Prerequisite rule

`strategic-roadmap.md` cannot be generated until `objectives-architecture.md` is complete. Every roadmap phase must link to at least one KR or validation milestone from this artifact.

---

## Generation Principles

These two rules govern how the agent generates every Knowledge Artifact. They override structural ambition.

### Principle 1 — Do not generate what is not in the Input

The agent must not fill KA fields with its own inferences, benchmarks, or projections when the Input does not cover them.

**The three valid responses to a missing field:**

| Situation | Correct agent behavior |
|---|---|
| Field is missing but not blocking | Leave empty with an explicit question to the human → OQ-XXX |
| Field affects targets, metrics, or roadmap decisions | Ask the human before generating. Do not generate first and mark NHR after. |
| Human cannot answer and the agent must proceed | Propose options with explicit reasoning and wait for choice · or leave as `[TO BE DEFINED]` · or offer an external reference range marked `[external reference — not a product decision]` |

**NHR vs. empty field with question:**
- `[Needs Human Review]` — the agent generated something and the human reviews it.
- Empty field + explicit question — the human decides before the agent generates. For targets, metrics, and roadmap decisions, the second is correct.

**For `objectives-architecture.md` specifically:** non-omittable questions (GTM segment, pricing, runway, conversion assumptions) must be answered or explicitly deferred before the agent generates OKRs, KPIs, or numeric targets. Never fill targets with agent-invented numbers without marking them explicitly as proposals.

### Principle 2 — Complexity proportional to Input

The detail level of a KA must reflect the coverage of the Input, not the ambition of the template.

- If the Input covers a topic in 2 paragraphs, the KA should not produce 5 sections on that topic.
- Sections with no Input coverage are left with an explicit question, not filled structurally.
- A sparse but honest KA is more useful than a dense KA built on agent inference.

---

## Procedure

### Phase execution rule

Every phase always executes — phases are the evaluation mechanism, not conditional steps. What is conditional is the artifact output.

- If a phase has sufficient material → generate the artifact.
- If a phase has insufficient material → the phase delivers a **gap report** instead of the document. A gap report lists: what is missing, what assumptions would be required to proceed, and what the human needs to provide to unlock artifact generation.

A phase is never skipped to determine if it should be skipped. The evaluation is the phase.

---

### Phase 1 — strategy-brief.md + product-thesis.md

These define WHAT the product is and WHY it exists. Nothing else can be written without clear answers to these two questions.

For each: read coverage from `_analysis.md` → evaluate against `artifact-questions.yaml` → create or recalibrate → present summary + NHR markers → wait for confirmation.

### Phase 2 — user-architecture.md + product-architecture.md

These define FOR WHOM and HOW. Depend on Phase 1 to avoid reinterpreting the thesis.

Same process: read coverage → evaluate → create or recalibrate → present → confirm.

**Phase 4 activation decision:** when `product-architecture.md` is complete, evaluate whether it warrants a parent-child structure.
- Phase 4 is **required** if the artifact defines 5 or more modules with distinct behavior.
- Phase 4 is **optional** if modules are fewer or behavior is not sufficiently differentiated.
- Phase 4 is **skipped** if `product-architecture.md` is primarily principles and flows with no feature-level detail.

Record the decision (`required` / `optional` / `skipped`) and the rationale in `strategic-change-log.md` before proceeding to Phase 3.

### Phase 3 — objectives-architecture.md

Defines the measurable validation layer. Depends on Phase 1 and Phase 2 being stable.

**Before generating any OKR, KPI, or target, the agent must identify non-omittable questions** — inputs that cannot be inferred from the strategy alone (GTM segment, pricing model, runway, conversion assumptions). Present these to the human and wait for answers or explicit deferrals before proceeding.

Generation steps:
1. Identify non-omittable questions from `_analysis.md`. Present them. Wait.
2. With human answers (or explicit deferrals): generate the artifact at the level of detail the Input supports.
3. Numeric targets only appear if the human defined them or accepted an explicit agent proposal.
4. Fields with no Input coverage: leave as `[TO BE DEFINED]` with an `→ OQ-XXX` reference.
5. Do not use the full template structure if the Input does not warrant it. Use only the sections the Input can populate honestly.

### Phase 4 — features/ children

**Only executes if Phase 4 was declared required at end of Phase 2.**

If Phase 4 was declared omitted, skip to Phase 3. Do not revisit this decision silently.

When required:
1. For each module declared in `product-architecture.md` with differentiated behavior, create one file in `features/`.
2. Cross-cutting features (auth, notifications, search, permissions) go in `features/transversales.md`, not in individual files.
3. After generating each child, present a summary and wait for confirmation before the next.
4. When all children are complete, update the Feature Children Index in `product-architecture.md`.
5. Log completion in `strategic-change-log.md`.

**`/sp-next` behavior when Phase 4 is required:** after Phase 2 is confirmed, `/sp-next` executes Phase 4 before Phase 3. The sequence becomes: Phase 2 → Phase 4 → Phase 3 → Review Checkpoint → Phase 5.

Full template: `references/feature-child-template.md`

### Review Checkpoint — KAs

After Phase 3 is complete and before generating the roadmap:

**Phase 4 gate:** before invoking the Adversarial Reviewer, check the Phase 4 activation decision recorded in `strategic-change-log.md`.
- If Phase 4 was marked `required` and has not been executed → execute Phase 4 now before proceeding.
- If Phase 4 was marked `optional` → present the decision to the human and wait for confirmation before proceeding.
- If Phase 4 was marked `skipped` → proceed.

The Review Checkpoint does not proceed until the Phase 4 gate is resolved.

1. Invoke the Adversarial Reviewer with `review_scope: "strategic"`.
2. Present the full two-block report to the human.
3. Handle `orchestrator_revise` items. Present `human_decision_needed` items.
4. Wait for human confirmation before proceeding to `/sp-roadmap`.

### Phase 5 — strategic-roadmap.md

Only available when all 5 KA are in status `active` or `needs_human_review` with explicit human decision to proceed, and after the KA Review Checkpoint is resolved.

Every roadmap phase must link to at least one KR or validation milestone from `objectives-architecture.md`.

Full template: `references/templates.md`

### Review Checkpoint — Roadmap

After the roadmap is generated:

1. Invoke the Adversarial Reviewer with `review_scope: "roadmap"`.
2. Present the full two-block report to the human.
3. Handle `orchestrator_revise` items. Present `human_decision_needed` items.
4. Wait for human confirmation before proceeding to Phase 6.

### Phase 6 — Handoff

Delete `_analysis.md`. Produce:

```md
# Strategic Planning Handoff

## Current Roadmap Version
## Strategic Direction to Preserve
## Initiatives Ready for Task Planning
## Context Required by Task Planning
## Decisions That Must Not Be Reinterpreted
## Constraints and Trade-offs to Preserve
## Validation Objectives and KPIs
## Open Questions Requiring Human Review
## Risks to Watch During Task Planning
## Skill Review Flags
[Items flagged as flag_for_skill_review during review checkpoints]
```

---

## Challenge Protocol

Challenge when: claim sounds generic · differentiation is weak · ICP is too broad · priorities don't follow from thesis · evidence is thin · constraints ignored · strategy avoids a hard trade-off · roadmap phase has no validation objective.

```md
## Challenge

**Claim being challenged:** ...
**Why this may be weak:** ...
**What evidence exists:** ...
**What is still assumption:** ...
**Constraint or trade-off:** ...
**Recommended decision:** ...
**Needs Human Review:** Yes / No
```

---

## Human Interaction Protocol

One mandatory pause: Input Analysis Summary before artifact generation.
Two review checkpoints: after KAs, after roadmap.

All other interaction: extract first, ask only when missing answer blocks the roadmap.

```md
## Human Review Question

**Decision needed:** ...
**Why it matters:** ...
**Options:** 1. ... 2. ... 3. ...
**Agent recommendation:** ...
**Impact of decision:** ...
**Can proceed without answer?** Yes / No
```

---

## Open Questions Registry

`open-questions.md` is the single source of truth for all open questions, gaps, and unresolved decisions across all Strategic Artifacts. KAs are contextual views of this registry — not independent lists.

**A question is not resolved until `open-questions.md` marks it as such.**

### Structure of open-questions.md

```md
---
artifact: open-questions
version: [x.x]
status: active
last_updated: YYYY-MM-DD
---

# Open Questions

## Open Questions

| ID | Question / Gap | Artifact | Section | Current assumption | Blocks | Priority |
|---|---|---|---|---|---|---|
| OQ-001 | ... | strategy-brief | ICP | [assumption if any] | roadmap / KA / none | High |

## Resolved Decisions

| ID | Original question | Decision | Resolution date | Decided by |
|---|---|---|---|---|
```

**Columns:**
- **Current assumption** — if the agent proceeded with an assumption, state it explicitly. This is what `/sp-questions` shows so the human can confirm or replace it without opening the file.
- **Blocks** — `roadmap` if this question blocks `strategic-roadmap.md` generation · `[artifact-name]` if it blocks a specific KA · `none` if it is tracked but not blocking.

### Cross-reference protocol (GAP-01)

Every open question or NHR marker inside a KA must carry its OQ-ID:
```
[Needs Human Review] ICP lacks observable criteria → OQ-002
What is the GTM strategy? → OQ-001
```

When generating or revising a KA: check if the question exists in `open-questions.md` → if not, create it with the next available ID → write `→ OQ-XXX` in the KA. Never duplicate.

When the human resolves a question: (1) move to "Resolved Decisions" in `open-questions.md` · (2) replace NHR marker and `→ OQ-XXX` in the source KA with the decision, increment KA version · (3) log in `strategic-change-log.md`. All three in the same operation.

Full resolution flow and examples: `references/sp-questions-format.md`

### /sp-questions output format

Full output format and filter behavior: see `references/sp-questions-format.md`

**Filter behavior summary:**
- No filter → all open, ordered: blocking first, then High → Medium → Low
- `high` → High priority only
- `[artifact-name]` → questions from that artifact only
- `blocking` → only questions where Blocks = `roadmap` or a KA name

### Rules

- Every OQ-ID is unique and permanent. IDs are never reused, even after resolution.
- When a question is resolved, it moves to "Resolved Decisions" — it is never deleted.
- Increment version of `open-questions.md` whenever questions are added or resolved. Log in `strategic-change-log.md`.

---

## Memory Update Rules

Update `strategic-change-log.md` when the user says:
"update memory" · "log this change" · "this is now a decision" · "new version" · "mark this roadmap as current" · "update the history" · "this replaces the previous version"

Or when any trigger condition applies: artifact created or changed · roadmap created or changed · assumption becomes decision · human review resolved · constraint changes roadmap · open question resolved · review checkpoint completed.

---

## Loop Dimensions Check

| Dimension | Validation Question |
|---|---|
| D1 Intent | Does the roadmap preserve the product thesis, priorities, and anti-priorities? |
| D2 Context | Is the roadmap grounded in sufficient context and identifiable sources? |
| D3 Schema | Does the roadmap organize phases, initiatives, dependencies, risks, constraints, validation? |
| D4 Skills | Can the process be repeated using this skill? |
| D5 Tools | Were available sources considered, including conflicts and tactical items? |
| D6 Execution | Can the roadmap become initiatives and issues in Task Planning? |
| D7 Memory | Were meaningful changes and roadmap versions recorded? |
| D8 Objectives | Does every roadmap phase link to at least one KR or validation milestone? |
| D9 Scaffolding | Was `_analysis.md` deleted before the final handoff? |
| D10 Review | Were both Review Checkpoints completed and their outputs resolved before handoff? |

**Final exit question:** Can `strategic-roadmap.md` feed Task Planning without the next agent having to invent, reinterpret, or weaken the original strategic intention?
