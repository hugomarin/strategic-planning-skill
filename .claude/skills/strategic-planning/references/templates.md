# Strategic Planning Templates

## Table of Contents

1. `strategy-brief.md`
2. `product-thesis.md`
3. `user-architecture.md`
4. `product-architecture.md`
5. `strategic-roadmap.md`
6. `strategic-change-log.md`

---

## 1. strategy-brief.md

```md
---
artifact: strategy-brief
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
---

# Strategy Brief

## Purpose
Define the strategic direction that must be preserved during planning, execution, and review.

## Current Understanding
Summarize the current strategic direction of the product in 5–10 lines.

## Problem
Define the specific problem being solved and why it matters.

## Target User / ICP
Define who the product is for and what signals make this user relevant.

## Value Proposition
Define the value the product creates for the target user.

## Strategic Direction
Define what the product must preserve as it evolves.

## Differentiation
Explain what makes this product different from alternatives or generic solutions.

## Strategic Principles
List principles that should guide product, roadmap, design, and execution decisions.

## Priorities
Define what should move first and why.

## Anti-priorities
Define what should not be built yet, or should not be built at all.

## Success Criteria
Define what signals would indicate that the strategy is working.

## Open Questions
List what remains uncertain and requires decision or research.
```

---

## 2. product-thesis.md

```md
---
artifact: product-thesis
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
---

# Product Thesis

## Purpose
Capture the central product bet and its implications.

## Central Thesis
State the main product conviction in one clear sentence.

## Why This Thesis Matters
Explain why this thesis matters for users, the market, or the way work is done.

## Non-obvious Belief
Explain what this product believes that others do not see, underestimate, or solve poorly.

## Assumptions
List the assumptions that must be true for the thesis to work.

## Evidence
List available evidence: conversations, user signals, market signals, usage, strong intuitions, or prior learnings.

## Challenge / Counterargument
Explain the strongest argument against this thesis.

## Falsification Risks
Explain what would have to happen to prove the thesis weak or false.

## Product Implications
Explain what this thesis requires from the product.

## Roadmap Implications
Explain what this thesis requires from the build sequence.

## Validation Needs
Define what evidence would strengthen or weaken the thesis.
```

---

## 3. user-architecture.md

```md
---
artifact: user-architecture
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
---

# User Architecture

## Purpose
Define who the product is built for and what signals should guide product decisions.

## Primary User / ICP
Describe the primary user.

## Observable Signals
List concrete signals that help identify this user.

## Jobs / Needs / Frictions
Explain what the user is trying to accomplish, what hurts, and what frictions exist.

## User Roles or Segments
Define secondary roles or segments, if relevant.

## Exclusions
Define users or cases that should not guide the product in this phase.

## Adoption Logic
Explain why this user would adopt, use, or pay.

## Product Implications
Define what features, flows, or product decisions derive from this user architecture.

## Risks / Open Questions
List what is still unknown about the user.
```

---

## 4. product-architecture.md

```md
---
artifact: product-architecture
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
---

# Product Architecture

## Purpose
Translate strategy and user understanding into product structure.

## Product Principles
Define principles that should guide product decisions.

## Core Modules
Define the main modules or capabilities.

## Critical Flows
Define the flows that must work for the product to express its thesis.

## Core Features
Define indispensable features.

## Secondary Features
Define useful but non-core features.

## Dependencies
List dependencies between modules, features, data, technology, or design.

## Product Constraints
Define limits that should not be broken.

## Risks
List product, complexity, or adoption risks.

## Roadmap Implications
Define what should be built first, later, or not yet.
```

---

## 5. strategic-roadmap.md

```md
---
artifact: strategic-roadmap
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
---

# Strategic Roadmap

## Purpose
Convert strategic direction into an actionable roadmap that can feed Task Planning.

## Source Artifacts
List the Knowledge Artifacts used to generate this roadmap.

## Strategic Summary
Briefly summarize the strategic direction this roadmap must preserve.

## Roadmap Phases

### Phase [N]: [Name]

- **Strategic objective:**
- **Initiatives:**
- **Expected product outcome:**
- **Dependencies:**
- **Risks:**
- **Validation objective:**
- **Success criteria:**
- **What should not be included yet:**

## Prioritization Criteria
Define the criteria used to decide sequence and importance.

## Anti-priorities
Define attractive but intentionally excluded work.

## Candidate Initiatives
List initiatives that may later become tasks or Linear issues.

## Strategic Dependencies
List dependencies between product, design, technology, users, or business constraints.

## Constraints and Trade-offs
Identify constraints that shape this roadmap and the trade-offs they force.

## Validation Objectives
Define what this roadmap is trying to validate, learn, or de-risk.

## Rules of Intention Preservation
Define what must not be lost when this roadmap becomes tasks.

## Open Decisions
List unresolved decisions that require human review.

## Handoff to Task Planning
Explain what the next moment should use from this roadmap to generate initiatives, issues, DoD, acceptance criteria, and distributed context.
```

---

## 6. strategic-change-log.md

```md
# Strategic Change Log

## Purpose
Track meaningful changes to strategic artifacts and roadmap versions.

| Date | Artifact | Version | Change | Reason | Decision / User Input | Current? |
|---|---|---|---|---|---|---|
```

---

## 7. open-questions.md

```md
---
artifact: open-questions
version: 0.1
status: active
last_updated: YYYY-MM-DD
---

# Open Questions

## Open Questions

| ID | Question / Gap | Artifact | Section | Current assumption | Blocks | Priority |
|---|---|---|---|---|---|---|
| OQ-001 | [question or gap] | [artifact name] | [section name] | [assumption if agent proceeded with one, or —] | roadmap / [artifact-name] / none | High / Medium / Low |

## Resolved Decisions

| ID | Original question | Decision | Resolution date | Decided by |
|---|---|---|---|---|
| OQ-000 | [original question text] | [decision taken] | YYYY-MM-DD | [human / agent assumption / inferred] |
```

**Column notes:**
- `Current assumption` — if the agent proceeded without a human answer, the assumption must be stated explicitly here. This is the column shown by `/sp-questions` so the human can confirm or replace without opening the file.
- `Blocks` — use `roadmap` if this question blocks `strategic-roadmap.md` · use `[artifact-name]` if it blocks a specific KA · use `none` if tracked but not blocking.
- When resolved: move the row to "Resolved Decisions". Never delete. Increment version. Log in `strategic-change-log.md`.

---

## 8. objectives-architecture.md

**Note:** use only the sections the Input can populate honestly. Numeric targets and KPIs are only added when the human defines them or accepts an explicit agent proposal. See SKILL.md — Generation Principles.

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

## Purpose
Define measurable objectives that validate the strategy phase by phase.
This artifact must exist before the roadmap is generated.

## Strategic Objectives
High-level outcomes the product must produce. Not features — behavior or business changes.

## Phase [N]: [Name]

**What must be true at the end of this phase:**
[Free text. Human-defined or human-accepted proposal. Not generated from template structure alone.]

**Signals that would indicate it is working (2–3 max):**
- [Observable signal — human-defined or human-accepted]
- [Observable signal]

**Signals that would indicate it is NOT working (falsification):**
- [What would trigger a strategic response?]

**Thesis link:** Which claim in product-thesis.md does this phase validate or falsify?

## KPI Architecture
[Only populated when the human defines targets or accepts an explicit agent proposal.
Leave as [TO BE DEFINED] → OQ-XXX until then.
External benchmarks allowed only when marked [external reference — not a product decision].]

| KPI | Definition | Phase | Target | Signal type | Thesis link |
|---|---|---|---|---|---|

## Validation Sequence
[Only include if the Input provides sequencing signals.
Order by uncertainty — the most uncertain assumption is validated first, at the lowest cost.]

## Anti-metrics
[Only include if the human or Input identifies specific misleading signals.]

| Anti-metric | Why it is misleading | What to track instead |
|---|---|---|

## Open Questions
[Each must reference → OQ-XXX.]
```
