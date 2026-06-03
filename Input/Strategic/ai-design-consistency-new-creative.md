# Research: AI Design Consistency for the New Creative
> Date: 2026-05-16 | Via /research-agent | JTBD: "Ship a UI that feels consistently me — without explaining my aesthetic from scratch every time."

---

## Key Findings

- **The problem is real, widespread, and unnamed.** Communities describe "contextual amnesia", "aesthetic drift", "AI slop", and "the slow drift" — but no shared vocabulary exists yet for the design-specific version of session amnesia. Logic/architecture memory loss is named; aesthetic drift is experienced but not yet categorized. This is a positioning opportunity: whoever names the problem owns the conversation.

- **AI coding tools default to a recognizable generic aesthetic — and high-taste solo builders know it by sight.** Lovable, Bolt, v0, Claude Code all default to Inter/Geist fonts, blue/indigo accents, rounded corners, gradient heroes, and Shadcn-style UI patterns. MindStudio's research surfaces a precise rule: *"Silence in your design system = Claude defaults."* High-taste users recognize this as the "AI-generated look" and reject it — which means they are already doing active work to resist it, without a product that helps.

- **Enterprise-tier gating is locking solo users out of the solutions that exist.** Lovable's design system consistency features (enforced brand kits, codified component constraints) are Enterprise-only. v0 and Bolt have similar dynamics. Solo builders — the fastest-growing segment of AI UI builders — are being explicitly excluded from the primary governance product surface by every major player.

- **Three categories of emerging tools are converging on this gap from different angles — but none has closed it.** (1) *Format specs*: DESIGN.md (Google) provides a machine-readable file format — but requires technical authorship. (2) *Natural language → design system*: Google Stitch and Banani let users describe aesthetics in plain English and get structured tokens back — closest to the solo user need, but not yet integrated into AI coding workflows. (3) *Screenshot extraction*: Superdesign (open-source VS Code extension) extracts a design system from existing app screenshots and uses it as the foundation for future AI-generated components — the most promising "no craft required" approach.

- **Current workarounds are friction-heavy, fragile, and invisible to the market.** Solo builders maintain Notion color docs, paste screenshots in every prompt, write long preambles ("warm, editorial, premium, not generic AI"), or build manual `docs/memory.md` files that burn extra AI tokens. These are not solutions — they are substitutes that break silently and produce inconsistency that compounds. The workaround behavior is the strongest market signal: the job is real, no product is doing it.

---

## Surprising / Challenges Assumptions

- **Aesthetic drift is not yet named as a distinct pain point in the builder community.** The Indie Hackers and Hacker News threads on session amnesia focus almost entirely on logic, architecture, and decisions — not on visual consistency. The assumption that "aesthetic drift" is a recognized, searched-for problem is not validated. It is experienced but not yet articulated. The JTBD document frames the problem more precisely than any existing community discussion does. This means there is no search traffic to capture yet — but there is an opportunity to be the voice that names it.

- **Superdesign's screenshot-to-design-system approach may be the most viable zero-craft entry point.** The assumption was that "natural language first" would be the path for non-technical users. But screenshot extraction requires zero vocabulary — users show the AI what they like and the system extracts it. This pattern (extract-from-existing rather than describe-from-scratch) may be lower-friction than any text-based approach for users who "know it when they see it."

---

## Gaps — What's Still Unknown

- **No product has closed the loop from "describe your aesthetic once" to "every AI session reads it automatically."** DESIGN.md can be injected into CLAUDE.md — but users still have to write the DESIGN.md. Superdesign extracts it — but only from screenshots, not from natural language. Banani generates it from prompts — but output isn't yet natively integrated into Cursor, Claude Code, or Lovable workflows.

- **No enforcement layer exists for solo users at all.** Token Audit CLI and pipeline enforcement require CI/CD. Every solo-user solution is upstream-only (context injection, file formats, prompt preambles) — there is no "catch drift before it ships" for solo builders. It's unknown whether solo users want enforcement or just persistence.

- **Market size is unquantified.** No data exists on how many solo builders are actively experiencing aesthetic drift as a pain point. The proxy signal is workaround prevalence — which is high — but conversion to paid product hasn't been tested.

- **The natural language → tokens → AI pipeline isn't connected end-to-end.** Banani and Stitch can generate design systems from text, but the export-to-CLAUDE.md / DESIGN.md → AI coding assistant path is manual. Nobody has built the automatic connection.

---

## Source Tensions

- **Screenshot extraction vs. natural language first**: Superdesign bets on "show me what you have"; Banani and Stitch bet on "tell me what you want." Both are valid — but they serve different moments. Screenshot extraction serves users who already have something they like. Natural language serves users starting from scratch. The product that covers both moments wins.

- **Format standard vs. workflow tool**: DESIGN.md (Google) is positioning as "package.json for design systems" — a durable standard that AI tools will natively support. Banani, Superdesign, and Stitch are workflow tools whose output formats may not survive consolidation. If DESIGN.md achieves standard status, the workflow tools will need to export to it or become irrelevant.

---

## Connected to Your Work

| Finding | Project / Goal | So what? |
| --- | --- | --- |
| Aesthetic drift is unnamed — no shared vocabulary exists yet | Writing goal (3 articles, Q2 2026) | Strong article angle: name the problem. "Why your vibe-coded UI looks like everyone else's" — if you publish this before others name it, you own the frame. |
| Enterprise-tier gating locks solo users out of consistency tools | JTBD-new-creative-segment.md (product research) | Confirms the market gap is real and intentional, not accidental. The incumbents have chosen enterprise. |
| Superdesign's screenshot extraction is the most viable zero-craft path | Product strategy (if product direction pursued) | The "extract from existing" pattern lowers the barrier below even natural language — worth studying as a UX model. |
| Every major AI coding tool defaults to the same generic aesthetic | sergiomartinez.co (personal website, active build) | Your own site is at risk of this. A DESIGN.md or equivalent at project root would solve it — worth doing now, independent of product strategy. |
| Workaround prevalence (Notion docs, screenshot pasting, manual preambles) is strong market signal | JTBD-new-creative-segment.md | The habit column in the JTBD doc is validated. These are documented, widespread substitutes — not edge cases. |

---

## Memory Recommendations

- [ ] `Memory/learnings/ai-design-consistency.md` — "Aesthetic drift is unnamed in the builder community; whoever names it first owns the positioning." Reusable across writing and product strategy.
- [ ] `_Projects/sergiomartinez.co.md` → Research section — Add note: existing site is vulnerable to the same aesthetic drift problem. DESIGN.md or minimal design context file at project root recommended before landing page improvements continue.
- [ ] Not worth saving to decisions — no decision has been made yet; this is still in research/exploration phase.

---

## Immediate Action Items

- [ ] Add a DESIGN.md (or minimal design context file) to `~/Workspace/projects/sergiomartinez.co` before continuing landing page work — this is a direct application of the research to active work.
- [ ] Draft article outline: "Why your vibe-coded UI looks like everyone else's" — name the aesthetic drift problem, cite the AI slop defaults, position DESIGN.md-style files as the solution. Strong Q2 2026 article candidate.
- [ ] Review Superdesign and Banani more closely if product direction on New Creative segment is being considered — both are recent (2025-2026), solo-builder-targeted, and approaching the gap from viable angles.

---

## Raw Sources Used

- ★ [Design Systems + Lovable, Bolt, V0, Replit](https://www.designsystemscollective.com/design-systems-lovable-bolt-v0-and-replit-50a0a197bc35) — Design Systems Collective (Anchor)
- ★ [How to Maintain Brand Control with Lovable](https://lovable.dev/blog/how-to-maintain-brand-control-when-build-with-lovable) — Lovable (Anchor)
- ★ [Superdesign: Open-Source Design Agent](https://github.com/superdesigndev/superdesign) — GitHub (Anchor)
- ★ [Banani AI Design System Generator](https://www.banani.co/product/ai-design-system-generator) — Banani (Anchor)
- [DESIGN.md: Fix AI UI Inconsistency](https://www.buildthisnow.com/blog/guide/mechanics/design-md-claude-code) — Build This Now
- [Avoid AI Slop with Claude Design System](https://www.mindstudio.ai/blog/claude-design-avoid-ai-slop-design-system) — MindStudio
- [Artificial AI Memory System for Lovable](https://www.theuntitledhandbook.com/p/artificial-ai-memory-system-context) — The Untitled Handbook
- [How Indie Hackers Are Using Design Systems in 2026](https://www.matchkit.io/blog/indie-hacker-design-system-2026) — MatchKit
- [Google Stitch DESIGN.md Announcement](https://blog.google/innovation-and-ai/models-and-research/google-labs/stitch-design-md/) — Google Labs
- [Google Stitch: Vibe Design Platform](https://mlq.ai/news/google-introduces-stitch-vibe-design-platform-with-voice-and-natural-language-interface/) — MLQ.ai
- [Indie Hackers: Session Amnesia Thread](https://www.indiehackers.com/post/how-do-you-handle-the-fact-that-your-ai-forgets-everything-between-sessions-03d215aa82) — Indie Hackers
- [IH: Design-to-Code Still Broken](https://www.indiehackers.com/post/we-keep-wondering-why-design-to-code-still-feels-this-broken-MnOX2WlIfRIpSwmjviTS) — Indie Hackers
- [HN: Vibe Coding vs. Context-Aware Coding](https://news.ycombinator.com/item?id=45751880) — Hacker News
