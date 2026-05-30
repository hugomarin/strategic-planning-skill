# Feature Child Template

Use this template for every file in `features/`.

Each file describes the mechanics of one feature or module. It does not duplicate strategic intent from `product-architecture.md` — that document owns principles and architectural reasoning. Children own concrete behavior.

---

## Naming convention

```
features/[feature-name].md
features/transversales.md   ← cross-cutting features (auth, notifications, search, etc.)
```

---

## Template

```md
---
artifact: feature-[name]
version: 0.1
status: draft
last_updated: YYYY-MM-DD
---

# Feature: [Name]

## Qué hace
One paragraph. What the feature does from the user's perspective.

## Por qué existe
The problem it solves. Why this feature exists in this product specifically.

## Dónde vive
URL or location in the app.

---

## Sub-feature: [Sub-feature name] (if applicable)

### Qué hace
What this sub-feature does from the user's perspective.

### Por qué existe
Why this sub-feature exists and what problem it solves.

### Dónde vive
URL or location in the app.

### Cómo se compone
Components, states, or UI elements that make up this sub-feature.

### Quién puede usarla
User roles or conditions required to access this sub-feature.

### Reglas
Business rules, constraints, or logic that govern this sub-feature's behavior.

### Qué pasa cuando falla o está vacío
Empty states, error states, fallback behavior.

### Bugs conocidos
Reference OQ-ID for each known bug. Example: OQ-012 — description.
Leave blank if none.

### Cómo debería evolucionar
Pending improvements or future decisions. Reference OQ-ID for each item.
Example: OQ-017 — add bulk action support.
```

---

## Rules

- Every open question, bug, or pending definition must reference its OQ-ID from `open-questions.md`.
- Do not duplicate strategic intent from `product-architecture.md`. Children describe mechanics, not principles.
- Cross-module features (auth, notifications, search, and other transversals) go in `transversales.md`, not in individual feature files.
- `product-architecture.md` must include an index table of all feature children with links.

---

## Index table (add to product-architecture.md)

```md
## Feature Children Index

| Feature | File | Status | Last updated |
|---|---|---|---|
| [Feature name] | features/[name].md | draft | YYYY-MM-DD |
| Transversales | features/transversales.md | draft | YYYY-MM-DD |
```
