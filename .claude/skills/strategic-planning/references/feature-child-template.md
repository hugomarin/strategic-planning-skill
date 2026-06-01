# Feature Child Template

Use this template for every file in `Strategic Artifacts/features/`.

Each file describes one feature or module from the user's perspective. It does not duplicate strategic intent from `product-architecture.md` — that document owns principles and architectural reasoning. Feature children own concrete behavior: what it does, why it exists, and how it should work.

---

## Naming convention

```
Strategic Artifacts/features/[feature-name].md
Strategic Artifacts/features/cross-cutting.md   ← auth, notifications, search, and other transversal features
```

---

## Template

```md
---
artifact: feature-[name]
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
technical_reference: Technical Artifacts/features/feature-[name].md
---

# Feature: [Name]

## What it does
One paragraph. What the feature does from the user's perspective.

## Why it exists
The problem it solves. Why this feature exists in this product specifically.

## Where it lives
URL or location in the app.

---

## Sub-feature: [Sub-feature name] (if applicable)

### What it does
What this sub-feature does from the user's perspective.

### Why it exists
Why this sub-feature exists and what problem it solves.

### Where it lives
URL or location in the app.

### How it is composed
Components, states, or UI elements that make up this sub-feature.

### Who can use it
User roles or conditions required to access this sub-feature.

### Rules
Business rules, constraints, or logic that govern this sub-feature's behavior.

### What happens when it fails or is empty
Empty states, error states, fallback behavior.

### Known issues
Reference OQ-ID for each known issue. Example: OQ-012 — description.
Leave blank if none.

### How it should evolve
Pending improvements or future decisions. Reference OQ-ID for each item.
Example: OQ-017 — add bulk action support.
```

---

## Rules

- Every open question, issue, or pending definition must reference its OQ-ID from `Strategic Artifacts/open-questions.md`.
- Do not duplicate strategic intent from `product-architecture.md`. Children describe mechanics, not principles.
- Cross-cutting features (auth, notifications, search) go in `cross-cutting.md`, not individual feature files.
- `product-architecture.md` must include an index table of all feature children with links.

---

## Index table (add to product-architecture.md)

```md
## Feature Children Index

| Feature | File | Status | Last updated | Technical spec |
|---|---|---|---|---|
| [Feature name] | Strategic Artifacts/features/[name].md | draft | YYYY-MM-DD | Technical Artifacts/features/feature-[name].md |
| Cross-cutting | Strategic Artifacts/features/cross-cutting.md | draft | YYYY-MM-DD | — |
```
