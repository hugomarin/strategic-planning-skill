# Deus — Project Context

This project uses the `strategic-planning-skill` v6.0 with a multi-agent architecture.

## What this project is

Deus is a Product Harness for converting strategic intention into verifiable, versioned production artifacts. This folder is the working environment for Moment 1: Strategic Planning.

## Skill version

`strategic-planning-skill` v6.0 is active (SKILL-v6.md in this project folder). The skill governs all execution logic, commands, artifact generation, versioning, and agent orchestration. Do not duplicate skill logic here.

## Command dispatch

This project uses `/sp-*` commands defined in the strategic-planning-skill SKILL.md.

When the user sends any message beginning with `/sp-`, read the SKILL.md before executing. The skill file contains all execution logic, phase definitions, gates, and templates. Do not execute `/sp-*` commands from memory or training — always load the skill first.

Skill location (active): `.claude/skills/strategic-planning-skill/SKILL.md` in this project folder. The skill is fully self-contained — no dependency on the global installed plugin.

### Version validation

Before executing any `/sp-*` command, verify that the active skill version matches the version declared in this file.

1. Read the `version:` field from the frontmatter of the active skill file.
2. Compare it against the version declared in the **Skill version** section of this file.
3. If they match → proceed normally.
4. If they do not match → stop and notify the user: "CLAUDE.md declares skill vX.X but the active skill file is vY.Y. Run `/sp-sync` to synchronize before proceeding."

Do not proceed with a mismatched version without explicit user confirmation.

## Agent architecture

Three roles operate in this project:

- **Orchestrator** — the skill itself. Coordinates, generates, versions, publishes, decides.
- **Diagnostic Analyst** — `.claude/agents/diagnostic-analyst.md`. Reads `Input/`, returns structured diagnostic report.
- **Adversarial Reviewer** — `.claude/agents/adversarial-reviewer.md`. Reviews KAs and roadmap, returns two-block report.

Review report schema: `.claude/references/review-report-format.md`

## Folder conventions

- `Input/` — source documents. Read-only. The agent never writes here.
- `Knowledge Artifacts/` — all generated artifacts live here.
- `.claude/agents/` — subagent definitions.
- `.claude/references/` — shared schemas and formats.
- `_analysis.md` — temporary scaffolding inside `Knowledge Artifacts/`. Deleted before handoff.
- `.claude/skills/strategic-planning-skill/` — skill local al proyecto (SKILL.md + references/). Fuente autoritativa.
- `PROJECT.md` — if present, contains the active project name, KA status, and open decisions. Read at the start of any `/sp-*` command.

## Active project

The active project is defined by the documents currently in `Input/`. Do not assume any specific project from memory or prior sessions — always read `Input/` to establish context.

If `PROJECT.md` exists in this folder, read it before executing any command.

## Commands

Commands are registered in `.claude/commands/` and available from the first message of any session. Each command loads the active skill and delegates execution to it. Run `/sp-sync` to update CLAUDE.md if the skill version changes.
