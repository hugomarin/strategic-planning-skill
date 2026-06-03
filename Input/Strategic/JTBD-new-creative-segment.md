# JTBD : The New Creative (High Taste, Low Craft)
> Date: 2026-05-16 | Source: prd-mvp-ui-governance.md | Segment not addressed in current MVP
> Framing: AI as Enabler — not as a governance problem, but as a capability expander

---

## The Frame

The New Creative doesn't have a design system to protect. They have *taste* — a clear sense of what they want their product to look and feel like — but they lack the craft to formalize it or the technical fluency to enforce it. AI coding assistants gave them superpowers they didn't have before. But those superpowers come with a hidden cost: **the faster you generate, the faster you drift.**

The problem isn't governance. The problem is *identity continuity* at AI speed.

---

## Segment Profile

**Who they are:**

- Solopreneurs, indie hackers, non-technical founders
- Content creators building digital products (courses, newsletters, tools)
- Designers who can wireframe but can't code
- Writers and strategists who "vibe their way to a UI"
- Side-project builders who want their thing to look *them*

**What they can do:**

- Describe what they want in vivid natural language
- Recognize good design instantly ("that's not the right energy")
- Iterate quickly with AI tools (Cursor, Lovable, v0, Claude Code)
- Make taste-based decisions with confidence

**What they can't do:**

- Write a DTCG token schema
- Maintain a CLAUDE.md with design constraints
- Debug why three sections of the same page feel visually unrelated

**Their relationship to AI:**

AI is not a threat to their workflow — it *is* their workflow. Without AI, this product doesn't exist. With AI, they can ship things that would have required a developer six months ago. The problem is they've discovered a new failure mode they never had before: **aesthetic drift at generation speed.**

---

## The Struggling Moment

> *"I've been building this for three months. I know exactly what I want it to feel like — warm, editorial, premium, not generic AI. But every time I start a new session and ask Claude to build another section, it doesn't remember what we did before. Now my hero looks like one product, my pricing section looks like another, and my about page looks like a third. I have screenshots of what I liked but I can't get back to it consistently."*

**What just happened:**
- They told the AI to "make the hero section warm and editorial" — and it did.
- They told the AI to "build a pricing table that feels premium" — and it did.
- Neither talked to each other. Both forgot the first conversation.
- Three months in: a beautiful Frankenstein.

**The trigger:** A visitor, a collaborator, or their own fresh eyes looking at the product and saying "it feels a bit... inconsistent." That moment of recognition is the struggling moment. It's not the first session where drift happened — it's the first time they *see* it clearly.

---

## The Jobs

### Functional Job

> **Ship a UI that feels consistently me — across every page, every session, every AI-assisted component — without needing to explain my aesthetic from scratch every time.**

Sub-jobs:
- Lock down a color palette so the AI always uses the right ones
- Define a "feel" that persists beyond a single session
- Catch when a component doesn't match the rest of the system — without knowing what tokens are
- Be able to hand the product off (to a developer, a collaborator, or a different AI session) and have it stay recognizable

### Social Job

> **Look like someone with intentional design sensibility — not someone who vibed their way to a UI.**

The New Creative is acutely aware of the "AI-generated look" — the generic sans-serif, the blue gradient, the shadow-heavy card. They have high taste precisely because they can identify that look and hate it. Their product being visually incoherent doesn't just feel bad aesthetically — it signals to their audience that they didn't care. That's a social cost they feel deeply.

They want their product to look *authored*. Not designed by a system, but designed by a *person*.

### Emotional Job

> **Trust that what I'm building has a coherent identity — that the thing I made last Tuesday still matches what I make today.**

This is the deepest job and the least obvious. It's not about the output — it's about the *feeling* of creative control. The New Creative's greatest anxiety with AI generation isn't quality (AI is good enough) — it's **continuity**. Did the AI understand what I meant? Will tomorrow's session build something that belongs in the same world as today's?

When this job isn't done: they feel like a passenger in their own product. The AI is building, but it's not building *them*.

---

## Forces of Progress

### Push — What's Driving Them to Look for a Solution

- Visual incoherence is visible to anyone who looks at the product carefully
- New AI sessions don't inherit old decisions — they start fresh every time
- The longer they build, the harder it becomes to maintain consistency manually
- Screenshots and "vibe references" as system documentation don't scale
- Collaborators or contractors who touch the product immediately break the aesthetic

### Pull — What the Ideal Future Looks Like

- One document (or a workflow) that I write once and the AI reads every time
- The AI knows my colors, my fonts, my spacing philosophy — without me repeating it
- When something is off, it's flagged in plain English, not technical jargon
- My product feels coherent to a stranger who looks at it for the first time

### Anxiety — What's Stopping Them from Acting

- "I don't know what a design token is. Is this for me?"
- "Setting this up sounds like a project. I just want to ship."
- "What if I define it wrong and get locked into something I don't like?"
- "This sounds like enterprise tooling for teams. I'm one person."

### Habit — What They're Doing Today Instead

- Pasting screenshots of "the vibe I want" into every new AI session
- Writing long preambles: "remember we're going for warm, editorial, premium..."
- Manually comparing new components to old ones and fixing by eye
- Keeping a "color notes" doc in Notion with hex codes they copy-paste
- Giving up on consistency and accepting "good enough"

---

## What They're Hiring Today

| "Job" | Current hire | Why it fails |
| --- | --- | --- |
| Lock down my colors | Copy-paste hex from Notion into every prompt | Fragile, forgotten, error-prone |
| Define the vibe | Long natural-language preambles in every session | Session drift; the AI interprets differently each time |
| Catch drift | Their own eyes when something feels wrong | Slow, unreliable, requires fresh eyes |
| Explain the system to a collaborator | "Here are some screenshots of what I like" | Not actionable; collaborator still guesses |
| Have a design system | They don't — they have vibes and screenshots | Vibes don't version, don't reference, don't enforce |

---

## What They'd Hire If It Existed

A **design identity file** that:

1. **Lives in natural language first** — they describe their aesthetic in plain English and the system translates it to machine-readable tokens
2. **Gets read by their AI tools automatically** — placed in the project, the AI picks it up without being told to
3. **Flags drift in plain English** — "this component uses a blue that doesn't match your palette" not "violation: `--color-info` not in schema"
4. **Takes 15 minutes to set up** — not 2 hours of configuration
5. **Can be generated from an existing site** — they shouldn't have to start from scratch if they already have something they like

This product doesn't exist in its ideal form. But the building blocks do:

- **design.md** gives them the file format — but they'd need to know what tokens are to write one
- **Odessay** could generate one from their existing site — but it's aimed at enterprise DesignOps
- **Token Audit CLI** could flag drift — but it requires CI/CD and a machine-readable schema they don't have

The gap: **no product in this space has been designed for the person who has taste but not craft.**

---

## Implications for the MVP

The PRD's MVP is explicitly aimed at teams with existing design systems. The New Creative is excluded by assumption.

**Why this matters:**

The New Creative is the fastest-growing segment of AI-assisted UI builders. Every tool that makes it easier to ship UI without learning to code — Lovable, v0, Bolt, Cursor with no prior experience — creates more New Creatives. The market is expanding faster than the DesignOps segment.

**What the MVP would need to change to serve them:**

| Current MVP requirement | New Creative equivalent |
| --- | --- |
| W3C DTCG token schema | Natural language design description OR auto-generated from existing site |
| CI/CD GitHub Action integration | Local-only lint: `npx @[product]/check` on a directory |
| Violation report with token names | Plain-English violation: "this color (#3B82F6) isn't in your palette" |
| DesignOps-led setup | Solo setup in under 15 minutes, no team coordination |
| Figma export compatibility | Generated from URL or from a conversation |

**The opportunity signal:**

The New Creative will tell 10 people when something solves their problem. DesignOps leads write RFPs. If the goal is viral adoption at the bottom of the market, The New Creative is the user. If the goal is enterprise revenue, they're not. But they're the distribution engine either way — because every enterprise DesignOps lead started as someone who cared about craft before they were responsible for enforcing it.

---

## One-Line Positioning (If This Were the Product)

> "The first time you explain your design system to an AI, it should be the last time."

---

## Open Questions

1. **Is design.md the right format for them, or do they need a lower-abstraction entry point?** A natural-language-first interface that *generates* a DESIGN.md behind the scenes might serve them better than asking them to write YAML.

2. **What's the right trigger point?** The struggling moment (visual incoherence) hits 3–4 months into a build. Is there a way to intercept earlier — at the point of first drift, not after months of it?

3. **Do they need enforcement, or just persistence?** They might not need a CI gate at all — just a file that the AI reads at session start and that they can easily update. Enforcement implies a rule to enforce. They might just need *memory*.

4. **Is this a different product or a different tier?** The New Creative could be a free/self-serve tier that generates demand for the paid enterprise tier (teams). Or it could be a separate product entirely. The technology overlaps; the positioning doesn't.
