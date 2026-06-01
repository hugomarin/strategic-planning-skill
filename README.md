# Deus — Strategic Planning Harness

Working environment for **Moment 1: Strategic Planning** of the Deus Product Harness — a system for converting loose business intention into verifiable, versioned production artifacts.

This repository hosts the `strategic-planning` (v6.0) and its multi-agent orchestration: instead of generating documents that "the AI happened to produce", it produces the product that was **actually decided**, with explicit mechanisms for diagnosis, validation, and review operating *before*, *during*, and *after* every artifact.

> *"The output should not be what AI happened to generate. It should be the product that was actually decided."*

---

## What it does

The skill takes the raw material in `Input/` (strategy proposals, notes, research) and turns it into a coherent set of **Strategic Artifacts** plus an actionable `strategic-roadmap.md`:

- **strategy-brief** — the consolidated strategic reading
- **product-thesis** — where the product can exist and why
- **user-architecture** — ICP, buyer personas, JTBD
- **product-architecture** — what the product is and how it is structured
- **objectives-architecture** — objectives and how progress is measured
- **strategic-roadmap.md** — the sequenced, executable plan
- **strategic-change-log** — versioned record of strategic decisions

It never invents what the input doesn't cover, and it surfaces open questions early so the human can correct assumptions before they propagate.

---

## Architecture

Three roles operate in the harness:

| Role | Definition | Responsibility |
|------|-----------|----------------|
| **Orchestrator** | the skill itself (`SKILL.md`) | Coordinates, generates, versions, publishes, decides |
| **Diagnostic Analyst** | `.claude/agents/diagnostic-analyst.md` | Reads `Input/`, returns a structured diagnostic report |
| **Adversarial Reviewer** | `.claude/agents/adversarial-reviewer.md` | Reviews artifacts and roadmap, returns a two-block report |

---

## Commands

All commands live in `.claude/commands/` and are available from the first message of any session. Each one loads the active skill and delegates execution to it.

| Command | Purpose |
|---------|---------|
| `/sp-start` | Run the full diagnosis → artifacts → roadmap pipeline |
| `/sp-diagnose` | Run only the diagnostic analysis of `Input/` |
| `/sp-run` | Generate Strategic Artifacts |
| `/sp-roadmap` | Generate the strategic roadmap |
| `/sp-questions` | Manage the open-questions register |
| `/sp-challenge` | Adversarial review pass |
| `/sp-conflict` | Resolve conflicts between artifacts |
| `/sp-next` | Advance to the next phase |
| `/sp-status` | Show current project / artifact status |
| `/sp-sync` | Synchronize the skill version with `CLAUDE.md` |

---

## Repository layout

```
.
├── CLAUDE.md                       # Project context + command dispatch rules
├── Input/                          # Source documents (read-only — never written to)
├── Strategic Artifacts/            # All generated artifacts live here
├── skill-diseccion-strategic-planning.md   # Annotated dissection of the skill
└── .claude/
    ├── commands/                   # /sp-* command definitions
    ├── agents/                     # Subagent definitions (analyst, reviewer)
    ├── references/                 # Shared schemas (e.g. review report format)
    └── skills/
        └── strategic-planning/
            ├── SKILL.md            # The Orchestrator — all execution logic
            └── references/         # Validation engine, templates, question protocol
```

### Folder conventions

- `Input/` is **read-only**. The agent never writes there.
- `Strategic Artifacts/` holds every generated artifact.
- `Strategic Artifacts/_analysis.md` is temporary scaffolding, deleted before handoff.
- The skill is fully self-contained under `.claude/skills/` — no dependency on a globally installed plugin.

---

## Getting started

1. Drop your strategic source documents into `Input/`.
2. Run `/sp-start` to execute the full pipeline, or `/sp-diagnose` to inspect the input first.
3. Review the generated Strategic Artifacts and `strategic-roadmap.md`.
4. Use `/sp-questions` to resolve any open assumptions the skill flagged.

Before executing any `/sp-*` command, the harness validates that the active skill version matches the version declared in `CLAUDE.md`. On mismatch, run `/sp-sync`.

---

## Versioning

`strategic-planning` **v6.0** is active. Highlights:

- Verbose toggle (silent by default, `--verbose` for incremental output)
- ASCII format rule (markdown tables only — no box-drawing characters)
- Missing-document soft signal (non-blocking)
- Phase vs. output rule (phases always execute; an artifact is conditional on having material)
