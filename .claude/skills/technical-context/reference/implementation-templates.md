# Implementation Context Templates

## Table of Contents

1. `stack.md`
2. `schema.md`
3. `architecture.md`
4. `feature-[name].md`
5. `technical-change-log.md`
6. `technical-open-questions.md`

**Usage rules:**
- Templates define structure, not content. Sections are populated only when Input/ supports them.
- A sparse but honest artifact is more useful than a dense artifact built on agent inference.
- Sections with no Input coverage are left with an explicit question → OQ-XXX, not filled structurally.
- Every artifact includes YAML frontmatter. Status starts as `draft`. Only the human changes it to `active`.

---

## 1. stack.md

```md
---
artifact: stack
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
---

# Stack — [Project Name]

Reference document for BUILD agents.
Read this before any implementation decision involving technology, performance, environment, or conventions.

---

## Operating Principle

[One sentence that governs every technical decision. Must be specific enough to resolve a trade-off.
Example: "Every decision must make the app feel faster and more immediate — or it should not be made."]

---

## Performance Contract

Measurable thresholds per dimension. These are not principles — they are enforceable rules.
Every PR that touches a relevant dimension must declare its impact in the Performance Contract section
of its Linear issue.

| Dimension | What it measures | Threshold | How to verify |
|---|---|---|---|
| [e.g. Interaction latency] | [e.g. Time from user action to visible response] | [e.g. < 16ms at 60fps] | [e.g. Playwright performance trace] |

[If thresholds are not yet defined, leave as [TO BE DEFINED] → OQ-XXX. Do not invent numbers.]

---

## Core Technologies

| Technology | Version | Role in this system | What it does NOT do here |
|---|---|---|---|

[For each technology: state its role AND its boundary. An agent that does not know the boundary
will use a technology for something it should not handle.]

---

## Architecture Pattern

[Document the primary data flow as an explicit sequence, not as a principle.
Example:
  User writes → local storage (immediate, no debounce) → sync queue → remote DB (background, debounce Xs)
  The user never waits for the remote write. The local layer is the source of truth for all reads.

If multiple runtimes exist (web, desktop, mobile), document each separately.]

**Web runtime:**
```
[explicit sequence]
```

**Desktop runtime (if applicable):**
```
[explicit sequence, or: "Not yet defined → OQ-XXX"]
```

---

## Services

| Service | Role | What this system uses it for | What it does NOT handle in this system |
|---|---|---|---|

[List every external service. The "does NOT handle" column prevents agents from routing
the wrong operations to the wrong service.]

---

## Authentication

[Document the complete auth flow: provider, session management, trigger on user creation,
email domain, redirect behavior.]

- **Provider:** [e.g. Supabase Auth with email + password]
- **Session management:** [e.g. Next.js middleware protects private routes]
- **On user creation:** [e.g. Database trigger creates profile automatically]
- **Email domain:** [e.g. auth.example.com]
- **Redirect on auth failure:** [e.g. /login]
- **OAuth / external providers:** [e.g. None — email + password only]

---

## Environments

### Development / Staging

| Service | Configuration | Notes |
|---|---|---|

**Critical rule:** [e.g. Agents never operate against production. All operations run against staging.]

### Production

| Service | Configuration | Notes |
|---|---|---|

---

## Agent Conventions

Rules, not preferences. An agent that reads a preference may deviate. An agent that reads a rule does not.

**Structure:**
[e.g. Next.js App Router: /app, /components, /lib, /api]

**Naming:**
[e.g. English for all code, URLs, components, DB. UI uses i18n.]

**Commits:**
[e.g. Conventional commits: feat:, fix:, chore: with issue ID at end — feat: description [TEAM-N]]

**Styling:**
[e.g. Tailwind only. No CSS modules, no styled-components.]

**Testing:**
[e.g. Playwright for E2E on critical flows. List which flows require Playwright coverage.]

**Typography:**
[e.g. [Font A] for functional UI. [Font B] for content. Never mix in the same element.]

**Icons:**
[e.g. [Library]. strokeWidth=[N] always, no exception.]

**What agents must never do:**
- [Rule 1]
- [Rule 2]

---

## Environment Variables

| Variable | Scope | Purpose | Environment |
|---|---|---|---|
| [VAR_NAME] | server-only / client-safe | [what it is for] | all / staging / prod |

[Variables marked server-only must never appear in client-side code.
Variables marked client-safe may use NEXT_PUBLIC_ or equivalent.]

---

## Hard Constraints

Rules that cannot be broken without compromising system integrity or user trust.
These apply to every issue, every PR, every agent.

| Constraint | Rule | Consequence of violation |
|---|---|---|
```

---

## 2. schema.md

```md
---
artifact: schema
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
---

# Schema — [Project Name]

Reference document for BUILD agents.
Read this before any migration, query, RLS policy, or data operation.

This document describes the **objective schema** (what we are building toward).
See "Schema Transition Rules" for the relationship between the objective schema
and the currently deployed schema.

---

## Entity Relationships

[A diagram or text map showing how tables relate. The purpose is to let an agent reason
about joins, cascades, and dependencies without tracing foreign keys one by one.

Example:
  auth.users
    └── profiles
          ├── writings
          │     ├── correspondences
          │     ├── writing_shares
          │     └── ai_observations
          └── collections
                └── writing_collections
]

---

## Domain Concepts

[Business-level concepts that the schema models. This section explains the "why" before the "what."
Each concept should answer: what is it, why does it exist as its own entity, and what does it enable.

Example:
  Correspondence — a thread with its own identity. Not just a writing with replies.
  It exists so the AI editor can use the full thread as context, and so the product
  can narrate the history of an exchange. Created automatically when a writing receives
  its first reply.]

---

## Tables

[One section per table. Order from parent to child — auth first, then profiles, then entities that
depend on profiles.]

### [table_name]

[One sentence on why this table exists and what it represents.]

| Field | Type | Constraints | Purpose |
|---|---|---|---|
| [field] | [type] | [PK / FK → table.field / unique / not null / nullable / default X] | [why this field exists; what values are valid; what it must not be confused with] |

**Business rules:**
[Explicit rules, not descriptions. Each rule should be a trigger or automatic operation:]
- [e.g. Created automatically via trigger when user registers. The trigger sets id = auth.users.id.]
- [e.g. correspondence_id is set automatically when a writing with parent_id receives its first reply.]

**Sync behavior:**
[Which fields are local-only, which are remote, which direction sync flows.]
- Local-only (never sent to server): [field list]
- Remote source of truth: [field list]
- Derived locally from remote: [field list]

---

## RLS Policies

[Every table × every operation. "Not permitted" and "public" are valid and required answers.
Leaving a table out is not acceptable — an agent cannot assume an undocumented policy.]

| Table | Select | Insert | Update | Delete |
|---|---|---|---|---|
| [table] | [who can select, or: public / not permitted] | [condition] | [condition] | [condition] |

[For complex policies, add a note below the table explaining the condition in plain language.]

---

## Indices

| Index | Table | Fields | Query it serves | Notes |
|---|---|---|---|---|

[Purpose: an agent building a new query must know whether an existing index covers it
or whether a new one is required.]

---

## Auth Integration

[How authentication connects to the schema. Document the complete flow:]

**Registration:**
1. [Step 1 — e.g. User registers with email + password via auth provider]
2. [Step 2 — e.g. Trigger creates profile with id = auth.users.id]
3. [Step 3 — e.g. Username and display_name passed as metadata to trigger]

**Session:**
[How the authenticated user ID is used in RLS policies and queries.]

---

## Schema Transition Rules

[This section governs the gap between the objective schema (this document) and the
effective schema (what is currently deployed in production/staging).]

**Current state:** [e.g. Schema aligns with this document as of YYYY-MM-DD. OR: Fields X, Y, Z are in transition — see notes below.]

**Rules for BUILD:**

1. **Objective vs. effective.** This document describes the target. It does not guarantee the deployed schema matches point for point.
2. **Forward compatibility.** Code must not fail when a new column appears.
3. **Backward compatibility.** Code must not assume a column exists until its migration is confirmed deployed.
4. **RPC/trigger validation.** No RPC or trigger is production-ready until validated against the effective schema, not just this document.

**Checklist before merging a schema change:**
- [ ] Migration applied to staging?
- [ ] Code has fallback for the previous schema if migration has not run?
- [ ] RPCs/triggers reference only columns that exist in the deployed schema?
- [ ] This document updated to reflect the new objective schema?
- [ ] Evidence that deployed schema matches what the code expects?
```

---

## 3. architecture.md

```md
---
artifact: architecture
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
---

# Architecture — [Project Name]

Reference document for BUILD agents.
Read this before building any page, component, navigation element, or data flow.

---

## Application Modes

[Each mode is a distinct context with its own purpose and constraints.
An agent that confuses modes will add write functionality to a read surface,
or add navigation chrome to a focus surface.]

| Mode | Purpose | Primary behavior | What it is NOT — explicit exclusions |
|---|---|---|---|

[For each mode that needs more detail, add a subsection.]

### [Mode Name]

**Purpose:** [What this mode exists to do]
**Primary behavior:** [What the user does here and what the system does in response]
**Excluded behaviors:** [What this mode must never do — stated as rules]
**Tone of interface:** [e.g. Interface disappears, text is protagonist. Or: Functional, table-based.]

---

## Navigation Architecture

[Document with exact dimensions and coordination rules. An agent that does not know the
exact dimensions and coordination rules will invent them and break the layout contract.]

### Layout Zones

```
[ASCII or text diagram of the layout with zone names and widths]
Example:
┌──────────┬──────────────────────┬─────────────┐
│ Sidebar  │ List Panel           │ Editor      │
│  52px    │  240px               │  flex-1     │
└──────────┴──────────────────────┴─────────────┘
  always     opens/closes           never moves
  visible    without moving editor
```

**Total width constraint:** [e.g. Sidebar + List Panel = 292px always. Editor never moves.]

### [Panel/Zone Name] — States

| State | Width | Content | Transition |
|---|---|---|---|
| [e.g. Expanded] | [px] | [what shows] | [e.g. 300ms cubic-bezier(0.4,0,0.15,1)] |
| [e.g. Collapsed] | [px] | [what shows] | [same transition] |

**Coordination rules:**
[e.g. When List Panel opens, Sidebar collapses simultaneously. List Panel transition is 20ms
slower than Sidebar (300ms vs 320ms) so Sidebar makes space first.]

---

## Page Inventory

| Route | Auth | Redirect if unauthenticated | Mobile | Description |
|---|---|---|---|---|
| [/route] | public / private / dual | [route] / N/A | full / read-only / unavailable | [one line] |

[For pages that need more than a table row — complex layouts, special states, key constraints:]

### [Route] — [Page Name]

**Layout:** [describe structure]
**Sections:**
- [Section name]: [what it shows, key constraints]

**States:**
- Empty: [what shows when there is no data]
- Loading: [what shows while data loads]
- Error: [what shows if the page fails to load]

**Notes:** [implementation constraints, decisions, references to feature specs]

---

## Data Architecture

[Document how data flows through the system at the component level.
The principle alone ('local-first') is not enough — document what it means for each type of operation.]

### [Runtime name — e.g. Web]

```
[Explicit sequence per operation type]
Example:
Write:  User action → local DB (immediate) → sync queue → remote DB (background, Xs debounce)
Read:   local DB first → remote only if local is empty or stale
Navigation: local DB — no server fetch triggered by navigation events
```

**Rules:**
- [e.g. Navigation between views does not trigger server fetches. Data is already in local DB.]
- [e.g. sync_status is local-only. Never include it in server payloads.]

### [Runtime name — e.g. Desktop] (if applicable)

[Same structure, or: "Not yet defined → OQ-XXX"]

---

## Architectural Decisions

[Each decision extracted as an explicit rule with rationale.
An explanation is not a rule. A rule can be applied without judgment.]

| Decision | Rule | Rationale | Applies to |
|---|---|---|---|
| [topic] | [exact rule — what BUILD must do or never do] | [why this decision was made] | [all / specific component / specific runtime] |

---

## Invariants

[Rules that must hold at every system boundary. Each invariant describes a class of violation
that has caused or could cause a bug. An agent must check these before merging any PR
that touches a boundary.]

| Boundary | Invariant | Example of violation |
|---|---|---|
| [e.g. Product → HTTP headers] | [e.g. User text normalized before use in headers] | [e.g. Title with em-dash in Content-Disposition without sanitization] |
| [e.g. Product → SQL] | [e.g. Never interpolate user text in queries — always parameterize] | [e.g. Query built with string template containing user input] |
| [e.g. Product → Remote DB] | [e.g. Local-only fields never sent to server] | [e.g. sync_status included in PATCH payload] |

**Checklist for BUILD before merging code that crosses a boundary:**
- [ ] Does user-supplied data pass through a normalization layer before crossing?
- [ ] Does the normalization handle worst-case inputs (empty, Unicode, special characters, extreme length)?
- [ ] Is there a test that fails if the normalization is removed?
- [ ] Is the input/output contract of the adapter documented?
```

---

## 4. feature-[name].md

```md
---
artifact: feature-[name]
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
strategic_reference: Strategic Artifacts/features/[feature-name].md
---

# Feature: [Feature Name]

Reference document for BUILD agents.
Read this document and the relevant sections of stack.md, schema.md, and architecture.md
before implementing any issue in this feature.

---

## What this feature does

[One paragraph. Purpose, who uses it, what workflow it enables, and what product
value it delivers. Must be concrete — not "manages state" but "allows the author
to write and have their content saved immediately without any explicit save action."]

## What it is NOT

[Explicit exclusions. What this feature must not do, to prevent scope creep in issues.]

- [e.g. This is not a collaboration feature — only the author can edit their own writing.]
- [e.g. This is not a publishing flow — visibility and sharing are separate features.]

---

## Dependencies

[What must exist and be working before this feature can function correctly.]

| Dependency | Type | Status | Notes |
|---|---|---|---|
| [e.g. schema.md — writings table] | Schema | [deployed / in transition] | [any notes] |
| [e.g. feature-auth.md] | Feature | [active / draft] | [what specifically is needed] |
| [e.g. Supabase Realtime] | Service | [configured / pending] | [for what] |

---

## User Flows

[One section per distinct flow. A flow is a complete path from trigger to outcome.
Every step must specify: who acts, what they do, and what the system does in response.]

### Flow [N]: [Flow Name]

**Trigger:** [What initiates this flow — user action, system event, navigation]

| Step | Actor | Action | System response |
|---|---|---|---|
| 1 | [User / System] | [specific action] | [specific system response — which layer, which operation] |
| 2 | ... | ... | ... |

**Outcome:** [The verifiable state at the end of this flow]

**Error conditions:**

| Failure point | What fails | System response | User sees |
|---|---|---|---|
| Step [N] | [what can go wrong] | [how system handles it: retry / fallback / fail fast] | [exact message or UI state] |

**Loading states:**

| Step | Async operation | UI while waiting | Duration estimate |
|---|---|---|---|
| [N] | [what operation] | [what shows] | [e.g. instant / < 1s / variable] |

**Empty state:** [What the view shows when this flow produces no data or is first accessed]

---

## Data Operations

[One row per data operation across all flows. Agents use this to know exactly which
table, which operation, which fields, and what triggers each write or read.]

| Flow | Step | Table | Operation | Fields included | Triggered by |
|---|---|---|---|---|---|
| [flow name] | [N] | [table] | [SELECT / INSERT / UPDATE / DELETE / upsert] | [field list or: all] | [user action / system event / debounce] |

---

## Permissions

[Every user action that requires a permission check. An agent that does not know
the permission model will either show actions to everyone or hide them from everyone.]

| Action | Who can perform it | Permission source | If not permitted |
|---|---|---|---|
| [e.g. Respond to a writing] | [e.g. Users in writing_shares with can_respond = true] | [e.g. RLS on writing_shares + can_respond field] | [e.g. Respond button not shown] |

---

## UI Specification

[Per view or interactive component that needs specification beyond the page inventory
in architecture.md. Every interactive element must have: label, position, component,
states, and action.]

### [View or Component Name]

**Layout:** [describe structure, key dimensions if relevant]

**Components:**

| Element | Label / Content | Component | Position | States | Action on interact |
|---|---|---|---|---|---|
| [e.g. Save button] | [e.g. "Save" / icon] | [e.g. Button, primary] | [e.g. Top right of editor] | [default / loading / disabled] | [e.g. Triggers PATCH /api/writings/[id]] |

**Copy:** [Exact text for all labels, messages, and empty state copy — if defined]

---

## Edge Cases

[Scenarios where the normal flow breaks. Every edge case must have a documented
system response so BUILD does not have to invent it.]

| Scenario | System response | User sees |
|---|---|---|
| [e.g. User navigates away mid-flow before async operation completes] | [e.g. Operation completes in background; result visible on return] | [e.g. No interruption] |
| [e.g. Duplicate submission (user clicks twice)] | [e.g. Second request is debounced / deduplicated] | [e.g. No duplicate created] |
| [e.g. Dependency no longer exists when flow completes] | [e.g. Graceful fallback to previous state] | [e.g. Error message X] |
| [e.g. Offline when remote write is attempted] | [e.g. Queued for retry; local state preserved] | [e.g. Subtle indicator, no blocking] |

---

## Acceptance Criteria

[Binary, testable conditions. Each criterion must be verifiable by an agent or automated
test without human judgment. If a criterion requires a human to decide whether it passes,
it is not ready — rewrite it or mark it [TO BE DEFINED] → OQ-XXX.]

- [ ] [e.g. Auto-save triggers within Xms of the last keystroke — measurable by Playwright timer]
- [ ] [e.g. Writing exists in local DB before any remote write is attempted — verifiable by intercepting network requests]
- [ ] [e.g. sync_status field is never present in the PATCH payload — verifiable by inspecting request body]
- [ ] [e.g. Empty state is shown when the user has no writings — visible in Playwright snapshot]
```

---

## 5. technical-change-log.md

```md
# Technical Change Log

## Purpose
Track meaningful changes to implementation artifacts: stack, schema, architecture, and feature specs.

| Date | Artifact | Version | Change | Reason | Decision / Human Input | Current? |
|---|---|---|---|---|---|---|
```

---

## 6. technical-open-questions.md

```md
---
artifact: technical-open-questions
version: 0.1
status: active
last_updated: YYYY-MM-DD
---

# Technical Open Questions

## Open Questions

| ID | Question / Gap | Artifact | Section | Current assumption | Blocks | Priority |
|---|---|---|---|---|---|---|
| OQ-T001 | [question or gap] | [artifact name] | [section name] | [assumption if agent proceeded, or —] | stack / schema / architecture / feature:[name] / none | High / Medium / Low |

## Resolved Decisions

| ID | Original question | Decision | Resolution date | Decided by |
|---|---|---|---|---|
| OQ-T000 | [original question text] | [decision taken] | YYYY-MM-DD | [human / agent assumption / inferred] |
```

**Column notes:**
- `Current assumption` — if the agent proceeded without a human answer, the assumption must be stated explicitly here. This is what `/impl-check` surfaces so the human can confirm or replace without opening the file.
- `Blocks` — name the artifact this question blocks. Use `none` if tracked but not blocking.
- When resolved: move the row to "Resolved Decisions". Never delete. Increment version. Log in `technical-change-log.md`.
