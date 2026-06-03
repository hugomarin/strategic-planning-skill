# Strategy & Competitive Analysis — SchemaFlow
> Date: 2026-05-16 | Framework: Good Strategy Kernel + Competitive Profiling + Porter's 5 Forces

---

## Progress

```
Strategy Template Progress:
- [x] Step 1: Define strategic question and context
- [x] Step 2: Conduct competitive analysis
- [x] Step 3: Apply Good Strategy kernel
- [x] Step 4: Create action plan
- [ ] Step 5: Validate with quality checklist
```

---

## 1. Strategic Question & Context

### Strategic Question

How should **SchemaFlow position** against existing** design system tools to win the AI-era design governance market** — and which segment (enterprise DesignOps vs. **solo New Creative**) should it prioritize first?

### Business Context

**Company/Product:**
- **Name**: SchemaFlow
- **Industry**: Developer / Design tooling (SaaS)
- **Stage**: Pre-launch / MVP
- **Current position**: Product defined, MVP targeting teams with existing design systems

**Strategic Context:**
- **Goal**: Become the standard for AI-era design consistency enforcement — the file format + enforcement layer that AI coding tools use to maintain visual coherence
- **Timeline**: MVP launching in current cycle; New Creative segment identified as high-growth but not yet addressed
- **Constraints**: Solo/early-stage — no sales team, limited distribution, competing against Figma's ecosystem and established players like Tokens Studio (264k users)
- **Stakeholders**: Founder-led; design/dev community adoption critical before enterprise sales

---

## 2. Competitive Analysis

### Relevant Competitors (filtered from full product list)

From the provided list, the following products have meaningful overlap with SchemaFlow. Products are grouped by relevance tier.

#### Tier 1 — Direct competitors (same job, same output)

| Product | Overlap | Why |
| --- | --- | --- |
| **getdesign.md** | Very High | Extracts design system from existing site → AI-readable DESIGN.md. Same target user (solo AI builders), same format vision. **Only competitor explicitly building the exact artifact SchemaFlow centers on.** |
| **Tokens Studio for Figma** | High | #1 design token management plugin (264k Figma users). Manages W3C DTCG tokens, syncs with GitHub, enables theme switching. Largest incumbent in the token layer SchemaFlow operates in. |
| **Specify** | High | Design token engine — syncs tokens from Figma/Tokens Studio/JSON to code across 50+ platforms (CSS, Tailwind, React, Flutter). Overlaps on the token pipeline SchemaFlow intends to own. |
| **~~Backlight~~** | High | Full design system platform: tokens + components + docs + Figma sync + npm publishing. Most comprehensive competitor — code-centric, with bi-directional Figma sync and version control. |
| **Chromatic** | High | Visual testing and review for Storybook. Catches UI drift via visual regression snapshots — alternative approach to the same problem (design inconsistency). Built on Storybook; strong for component-level teams. |
| **infa.ai** | High | "Visualize Design System in use" — monitors design system adoption and compliance across projects. Directly overlaps with SchemaFlow's enforcement/visibility goal. |

#### Tier 2 — Adjacent tools (same workflow, partial overlap)
| Product | Overlap | Why |
| --- | --- | --- |
| **Figma Code Connect** | Medium-High | Maps Figma components to code components via CLI. Part of design-to-code consistency enforcement. Figma platform play — not a standalone product but builds Figma's moat. |
| **Figma Dev Mode** | Medium | Design-to-code handoff layer. Part of the same design system workflow. Positions Figma as the source of truth — if Figma wins, SchemaFlow needs to be compatible. |
| **Zeroheight** | Medium | Design system documentation platform (79% user satisfaction). Adjacent on design system management but focused on docs and human communication, not machine-readable enforcement. |
| **Percy** | Medium | Cross-browser visual regression testing (BrowserStack). Alternative drift detection approach — less Storybook-specific than Chromatic, more QA-oriented. |

#### Tier 3 — Ecosystem tools (less competitive, more adjacent)

| Product | Overlap | Why |
| --- | --- | --- |
| **Storybook** | Low-Medium | Component development environment and living style guide. Foundation for Chromatic; indirect overlap. Primarily a dev tool, not a governance tool. |

---

### Porter's 5 Forces Analysis

| Force | Assessment | Evidence | Strategic Implication |
| --- | --- | --- | --- |
| **Competitive Rivalry** | High | Tokens Studio (264k users), Specify, Backlight, Zeroheight, Chromatic are all established. Figma is the 800-lb gorilla with platform control. | Differentiation on AI-era governance required — competing on features alone against these players is losing. |
| **Threat of New Entrants** | Very High | AI makes new tools cheap to build. getdesign.md, Banani, Google Stitch, Superdesign all entered 2025-2026. Market is attracting well-funded entrants. | Speed to define the standard matters more than feature depth. Whoever names and owns the format wins. |
| **Threat of Substitutes** | High | Solo builders substitute with: Notion color docs, screenshot pasting, long AI prompt preambles, manual CLAUDE.md files. Enterprise teams substitute with Chromatic + Storybook. | The substitute is "doing it manually" — which means there's no strong incumbent to displace, but also no proven willingness to pay. |
| **Buyer Power** | Medium | Enterprise DesignOps teams have procurement processes and compare multiple options; solo builders decide in minutes. Two very different buyer behaviors. | Low-friction solo-first entry (free tier, fast setup) required to build community before enterprise sales. |
| **Supplier Power** | Medium | Figma controls the design source of truth; GitHub/npm control distribution; LLM providers control AI integration. | SchemaFlow must be Figma-compatible and AI-tool-agnostic to avoid being squeezed by platform dependencies. |

**Overall Industry Attractiveness**: Medium — large market, growing fast due to AI, but highly fragmented with strong platform risk from Figma.

**Key Dynamics**: The market is splitting between Figma-centric visual tools and code-side enforcement tools, with a third emerging category (AI-native design context) that no incumbent owns yet. Chromatic and Percy own the "catch drift after it ships" layer. Tokens Studio and Specify own the "manage tokens in Figma" layer. No one owns the "AI builds consistently with your design system" layer. That gap is SchemaFlow's opening.

---

### Competitor Profiling

**Competitor 1: Tokens Studio for Figma**
| Dimension | Assessment | Notes |
| --- | --- | --- |
| **Product/Features** | W3C DTCG token management, GitHub sync, theme switching, JSON export | Most feature-complete token tool in Figma; standard for design-dev handoff |
| **Pricing** | Free + Pro (individual/team); Plus tier with auto-docs sync | 264k Figma users on free; strong upsell path |
| **Target Customers** | Designers and design system teams using Figma | Enterprise and mid-market design teams; some freelancers |
| **Positioning** | "Design systems, fully automated" — Figma-native token management | Token management layer; the standard Figma plugin |
| **Strengths** | Massive user base (264k), Figma-native, W3C DTCG standard, GitHub sync | Network effects via community; de facto standard |
| **Weaknesses** | Figma-locked; no AI governance layer; no enforcement for AI coding tools; technical barrier for non-designers | Zero value for Cursor/Claude Code users who don't use Figma |
| **Strategy Inference** | Expanding into platform (Studio, Plus tier with docs) — moving from plugin to platform | Building switching costs via integration depth |
| **Threat Level** | High | If they add AI coding tool integration, they close SchemaFlow's main gap |

**Competitor 2: getdesign.md**
| Dimension | Assessment | Notes |
| --- | --- | --- |
| **Product/Features** | Extracts design system from existing site → DESIGN.md (colors, typography, spacing as tokens); Vibecoder Kit with AI playbooks | Service-based currently; closest to SchemaFlow's vision for New Creative |
| **Pricing** | Free DESIGN.md; paid Vibecoder Kit | Low barrier to entry; premium tier bundles starter templates |
| **Target Customers** | Solo builders using Lovable, Bolt, v0, ChatGPT, Claude | Exactly the New Creative segment — "vibe coders" |
| **Positioning** | "Custom design system for your website as an AI-readable markdown" | Format-first; positions DESIGN.md as the output artifact |
| **Strengths** | First mover on AI-readable design system format; zero-craft entry (no token knowledge required); exact right target user | Owns the DESIGN.md brand association |
| **Weaknesses** | Service model (not automated); no enforcement/lint layer; no Figma integration; no team/collaboration features | Manual extraction limits scale; no validation or drift detection |
| **Strategy Inference** | Building audience/community around the format; may productize extraction automation | Early in product journey; vulnerable to better-executed competitors |
| **Threat Level** | Very High | Closest direct competitor on positioning and target user; first-mover advantage |

**Competitor 3: Chromatic**
| Dimension | Assessment | Notes |
| --- | --- | --- |
| **Product/Features** | Visual snapshot testing for Storybook; PR review workflow; baseline tracking via git; UI Test and UI Review | Unlimited parallel test runs; git-aware baselines |
| **Pricing** | Free (limited snapshots); paid scales with snapshots/seats | Enterprise pricing for large component libraries |
| **Target Customers** | Frontend teams using Storybook; design system teams with component-driven architecture | Requires Storybook adoption; developer-led tooling |
| **Positioning** | "Catch UI bugs before they ship" — visual regression testing in CI | QA/testing frame, not design governance frame |
| **Strengths** | Storybook integration is deep; developer workflow fit (CI, PRs, git); strong in enterprise design system teams | Solves drift detection for teams with mature component architecture |
| **Weaknesses** | Requires Storybook (high setup cost); catches drift after component is written, not before; no AI coding tool integration; no token governance | Reactive not proactive; catches bugs, doesn't prevent AI session drift |
| **Strategy Inference** | Expanding into broader visual testing beyond Storybook; competing with Percy | Infrastructure play; building toward QA platform |
| **Threat Level** | Medium | Different approach (test-based vs. governance-based); complements SchemaFlow more than competes |

**Competitor 4: ****~~Backlight~~**
| Dimension | Assessment | Notes |
| --- | --- | --- |
| **Product/Features** | Tokens + components + docs + Storybook/stories + Figma sync + npm publishing; MDX/MDVue documentation; version control | Most complete design system platform |
| **Pricing** | Team-based pricing; enterprise | Not self-serve friendly |
| **Target Customers** | Design system teams at scale; front-end-focused organizations | Enterprise / mature design system orgs |
| **Positioning** | "Code-side design system management" — developer-centric platform | Full-platform play; code as source of truth |
| **Strengths** | Comprehensive; version control integration; bi-directional Figma sync; no separate token tool needed | Replaces Tokens Studio + Zeroheight + Storybook in one |
| **Weaknesses** | High setup complexity; no AI coding tool integration; enterprise-only pricing; overkill for solo users | Not accessible to New Creative; no AI-era governance features |
| **Strategy Inference** | Competing with Supernova, Abstract for enterprise design system platform | Platform consolidation play |
| **Threat Level** | Medium | Aimed at enterprise; different market than SchemaFlow's initial target; risk if SchemaFlow moves upstream |

**Competitor 5: infa.ai**
| Dimension | Assessment | Notes |
| --- | --- | --- |
| **Product/Features** | Visualizes design system in use — monitors adoption and compliance across projects | Earliest stage; positioning around visibility/monitoring |
| **Pricing** | Unknown — likely early pricing or pre-launch | Limited public information |
| **Target Customers** | Design system teams who need adoption visibility | DesignOps-oriented |
| **Positioning** | Design system compliance visualization | Monitoring frame; similar to SchemaFlow's enforcement intent |
| **Strengths** | Novel angle on the problem (visualization of system usage) | Differentiated approach |
| **Weaknesses** | Unknown product maturity; no community signals; no AI coding tool integration known | Needs validation |
| **Strategy Inference** | Early-stage; exploring design system observability space | Worth monitoring; could move toward SchemaFlow's territory |
| **Threat Level** | Medium (to watch) | Overlap on enforcement layer; unclear how far they'll go |

**Additional competitors to monitor:**
- **Specify** — token pipeline that connects Figma → code; strong integration play if they add AI governance
- **Zeroheight** — documentation layer; low direct threat but captures mindshare in the design system conversation
- **Percy** — visual regression alternative to Chromatic; BrowserStack distribution advantage

---

### Competitive Positioning Map

**Axes:**
- X-axis: **Target sophistication** — New Creative (zero craft) → Enterprise DesignOps (high craft)
- Y-axis: **AI integration depth** — None (design/dev workflow only) → Native (AI coding tool integration)

```
                    HIGH AI INTEGRATION
                           |
              SchemaFlow   |   (target position)
              getdesign.md |
                           |
    ───────────────────────┼───────────────────────────
    NEW CREATIVE           |                  ENTERPRISE
    (zero craft)           |                 (high craft)
                           |
          Tokens Studio ───┤─── Backlight
          Specify          |    Zeroheight
          infa.ai          |    Figma Code Connect
                           |    Chromatic / Percy
                    LOW AI INTEGRATION
```

**Insight**: The upper-left quadrant (New Creative + AI-native) is entirely unoccupied. getdesign.md is trying to enter it but is limited by a service model. The upper-right (Enterprise + AI-native) is also empty — no incumbent has built AI coding tool integration into enterprise design system governance. SchemaFlow can own the upper-left first (faster to validate, viral distribution potential) and expand upper-right as the format becomes standard.

---

### Competitive Advantages (Moats)

**Our current moats:**
- [ ] Network effects: Not yet — format adoption could create network effects if DESIGN.md becomes a standard
- [ ] Switching costs: Potentially high once DESIGN.md is embedded in CLAUDE.md and project roots
- [x] **First-mover on AI governance framing**: The "design identity file that AI reads automatically" framing is not yet owned by any competitor
- [ ] Brand: Not yet
- [ ] Cost advantages: No
- [ ] Regulatory/IP: No

**Competitor moats to be aware of:**
- Tokens Studio: 264k user community; de facto standard in Figma ecosystem
- getdesign.md: DESIGN.md brand association; first-mover with solo builders
- Chromatic: Storybook integration depth; enterprise CI workflows
- Figma: Platform control — owns the design source of truth

**Moat to build**: **Format standard adoption** — if DESIGN.md (or SchemaFlow's equivalent) becomes the default design context file that AI coding tools look for, the switching cost becomes very high. This is the "package.json for design systems" play. The format is the moat, not the SaaS product.

---

## 3. Strategy Formulation (Good Strategy Kernel)

### Diagnosis: What's the Challenge?

**Core challenge:**

The design system tooling market has a structural gap that none of the incumbents are positioned to fill: all existing tools were built for human-to-human workflows (designer → developer handoff) and have not been redesigned for AI-to-AI workflows (design system → AI coding tool → generated UI). The fastest-growing segment of UI builders — solopreneurs and "New Creatives" using AI coding assistants — is explicitly excluded from enterprise-tier consistency features by every major player. Meanwhile, the problem they face (aesthetic drift at AI generation speed) is real, widespread, and unnamed — giving no incumbent a defensible position and no user a vocabulary to search for a solution.

**Supporting analysis:**

| Finding | Evidence | Implication |
| --- | --- | --- |
| AI coding tools default to generic aesthetics | MindStudio: "Silence in your design system = Claude defaults" | Every AI session that runs without design context produces drift. This is structural, not accidental. |
| Enterprise-tier gating locks solo users out | Lovable, v0, Bolt all gate consistency features behind Enterprise | The fastest-growing segment (solo AI builders) has no product. This is intentional by incumbents. |
| No product closes the "describe once, AI reads always" loop | DESIGN.md exists as a format; Banani generates it; but neither auto-injects into AI tool context | The gap between format creation and AI consumption is unbridged. |
| Workaround prevalence is strong market signal | Notion color docs, screenshot pasting, long prompt preambles are widespread substitutes | The job is real; current substitutes are fragile, invisible, and don't scale. |
| Aesthetic drift is unnamed | No shared vocabulary in Indie Hackers / HN threads for the design-specific version of session amnesia | No search demand yet — but whoever names the problem first owns the frame. |

**Root cause:**

Existing design system tools were designed for teams who already have design systems and designers who can maintain them. They optimize for Figma-native workflows and developer handoff. The AI coding revolution created a new user class (high taste, zero craft) and a new failure mode (aesthetic drift at generation speed) that existing tools cannot address because they require technical authorship to set up and have no AI coding tool integration layer.

---

### Guiding Policy: Overall Approach

**Guiding policy:**

Own the AI-era design governance layer by being the **format-first, AI-native design identity standard** — starting with the New Creative segment to build viral adoption and format legitimacy, then expanding to enterprise teams as the format becomes the de facto standard for AI-consistent design systems.

**Strategic choice rationale:**

**Why this approach?**
1. **Addresses the diagnosis directly**: The gap is in AI integration, not in token management or documentation. Building the AI layer first captures the uncontested space before incumbents add it as a feature.
2. **Plays to early-stage strengths**: A format-first approach (file + CLI + spec) requires less capital than a full SaaS platform and can achieve distribution through open-source/community adoption.
3. **Exploits competitor weaknesses**: Tokens Studio and Specify are Figma-locked and technically complex for solo users. Chromatic requires Storybook. None has an on-ramp for the New Creative. SchemaFlow's zero-craft entry (auto-generate from existing site) serves a market all incumbents have abandoned.

**Why not alternatives?**
- *Compete head-to-head with Tokens Studio on token management*: Rejected — 264k user base, deep Figma integration, and W3C DTCG standard adoption make this a losing fight on their terrain.
- *Start with enterprise DesignOps*: Rejected for Phase 1 — requires sales team, compliance features, procurement cycles. Slower to validate and slower to distribute. Enterprise can follow after format adoption.
- *Build a visual testing tool (like Chromatic)*: Rejected — different problem frame (catch bugs vs. prevent drift). Visual testing is reactive; SchemaFlow's value is proactive context injection. Not the same job.

**How this creates competitive advantage:**

The format (DESIGN.md or SchemaFlow's spec) becomes embedded in project roots and CLAUDE.md files. Once embedded, removing it requires active effort — high switching cost. If SchemaFlow becomes the file that AI coding tools look for by default, the moat is the format standard, not the SaaS product. This mirrors how package.json became non-negotiable in JavaScript projects — not because npm is irreplaceable, but because the format is ubiquitous.

---

### Coherent Actions: Coordinated Steps

**Action 1: Publish the format spec as open source**
- **Description**: Release SchemaFlow's DESIGN.md spec (or equivalent format name) as a fully open, versioned standard on GitHub. Include the schema, documentation, and examples for common AI coding tool integrations (CLAUDE.md, Cursor rules, system prompts).
- **How it supports guiding policy**: Format legitimacy requires openness. A proprietary format will not become the standard. Open-sourcing it invites adoption without requiring a product purchase.
- **How it reinforces other actions**: Creates the foundation for the CLI (Action 2), the validation layer (Action 3), and community distribution (Action 5).
- **Owner**: Founder
- **Timeline**: Pre-launch deliverable; must ship before or with the CLI

**Action 2: Ship a zero-craft entry point for New Creatives**
- **Description**: Build "generate from URL" — paste an existing site URL, get a DESIGN.md back in under 60 seconds. No token vocabulary required. No Figma account needed. Output includes colors, typography, spacing, and a plain-English design description suitable for AI prompt injection.
- **How it supports guiding policy**: Removes the technical barrier that all incumbents use to gate solo users out. "Describe once, AI reads always" — this is the zero-to-one moment.
- **How it reinforces other actions**: Generated files drive CLI usage (Action 3); generates community content (real DESIGN.md files shared publicly); validates the New Creative market.
- **Owner**: Founder
- **Timeline**: MVP feature; ship alongside or before the CLI

**Action 3: Build and publish the SchemaFlow CLI lint/validate command**
- **Description**: `npx schemaflow check` — runs against a project directory, validates tokens against the DESIGN.md schema, flags violations in plain English ("this component uses #3B82F6, which isn't in your palette"). Local-only first; GitHub Action second.
- **How it supports guiding policy**: Creates the enforcement layer that makes the format valuable beyond documentation. This is the "drift detection" moat.
- **How it reinforces other actions**: Works with the generated DESIGN.md (Action 2); can be added to CI for enterprise teams (Action 4); demonstrates value immediately on first use.
- **Owner**: Founder
- **Timeline**: Q2 2026; ship within 4 weeks of format spec

**Action 4: Name the problem publicly**
- **Description**: Publish the "aesthetic drift" framing — the named concept for the AI-era design consistency failure. Ship as a long-form article ("Why your vibe-coded UI looks like everyone else's"), distributed on Indie Hackers, Hacker News, and Product Hunt. The framing positions SchemaFlow as the solution without requiring a product pitch.
- **How it supports guiding policy**: Whoever names the problem owns the conversation. No search demand exists yet — creating demand is prerequisite to capturing it.
- **How it reinforces other actions**: Drives top-of-funnel for the URL generator (Action 2); establishes SchemaFlow as thought leader before incumbents move; creates content for community seeding (Action 5).
- **Owner**: Founder
- **Timeline**: Q2 2026; publish before or concurrent with product launch

**Action 5: Seed the format in AI coding tool communities**
- **Description**: Create DESIGN.md templates, CLAUDE.md integration guides, and Cursor rules examples. Distribute through the AI builder communities where New Creatives live: Lovable community, r/ChatGPT, Indie Hackers, v0 Discord, Claude Code users. Position the format as a productivity tool, not a governance tool.
- **How it supports guiding policy**: Format adoption requires distribution, and distribution in this market happens peer-to-peer in builder communities, not through sales.
- **How it reinforces other actions**: Amplifies the naming article (Action 4); drives URL generator usage (Action 2); creates community validators for the spec (Action 1).
- **Owner**: Founder
- **Timeline**: Ongoing from launch; initial seed push concurrent with article (Action 4)

**Coherence check:**
- [x] All actions support guiding policy (format-first, AI-native, New Creative entry)
- [x] Actions reinforce each other (format → CLI → article → community → adoption loop)
- [x] No contradictions (all actions support open/accessible positioning; none require enterprise sales motion)
- [x] Actions are specific and concrete

---

## 4. Action Plan

### Strategic Initiatives

| Initiative | Owner | Timeline | Success Metrics | Dependencies |
| --- | --- | --- | --- | --- |
| Open-source format spec | Founder | Pre-launch | GitHub stars, forks, issues; community adoption signal | None |
| URL → DESIGN.md generator | Founder | MVP / Q2 2026 | Generated files per week; completion rate; return usage | Format spec |
| SchemaFlow CLI (`npx schemaflow check`) | Founder | Q2 2026 (+4 weeks) | Weekly active CLI installs; violations caught per run | Format spec + generator |
| "Aesthetic drift" naming article | Founder | Q2 2026 (concurrent with launch) | HN/IH upvotes; URL generator signups from article | Product must be live to convert |
| Community seeding campaign | Founder | Ongoing from launch | Format files created; community mentions; GitHub stars | Article + generator |

### Success Metrics & Targets

**North Star Metric**: DESIGN.md files created per week (measures format adoption, not just awareness)
- **Baseline**: 0
- **Target**: 100/week by end of Q3 2026
- **Timeline**: Q3 2026

**Supporting Metrics:**

| Metric | Baseline | 3-Month Target | 6-Month Target | Why This Matters |
| --- | --- | --- | --- | --- |
| CLI weekly active installs | 0 | 50 | 200 | Measures enforcement adoption, not just file creation |
| GitHub stars on spec | 0 | 500 | 1,500 | Format legitimacy signal; precursor to standard status |
| Article-driven signups | 0 | 200 first week | — | Validates naming strategy and distribution channel |
| Time to first DESIGN.md (new user) | Baseline TBD | <5 minutes | <2 minutes | Product quality proxy; key for New Creative adoption |

---

### Assumptions & Risks

**Critical Assumptions:**

1. **New Creative segment will pay (or convert to team tier)** — Assumption: Solo builders who care about aesthetic identity will eventually pay for enforcement/collaboration features. **Validation plan**: Offer free tier; measure upgrade rate after 30 days of usage. If <2% upgrade, revisit monetization model.

2. **DESIGN.md format will not be standardized by Google Stitch before SchemaFlow launches** — Assumption: Google's DESIGN.md proposal remains advisory, not enforced by AI tools. **Validation plan**: Monitor Google Stitch announcements monthly; be ready to position as "the best DESIGN.md implementation" rather than the format owner if Google formalizes the spec.

3. **Solo builders will generate DESIGN.md files and use them across sessions** — Assumption: The job is real and the activation moment ("generate from my site URL") triggers habitual usage. **Validation plan**: Instrument the CLI; measure DESIGN.md files injected into CLAUDE.md/cursor rules within 7 days of generation. Target: >30% of generated files get actively used.

**Key Risks:**

| Risk | Likelihood | Impact | Mitigation |
| --- | --- | --- | --- |
| Tokens Studio adds AI coding tool integration | Medium | High | Accelerate format spec open-sourcing; establish community standard before they move |
| getdesign.md productizes and scales faster | Medium | High | Compete on enforcement (they have none) and ecosystem integration (Figma, CLI, CI) |
| Google Stitch/DESIGN.md becomes the de facto standard | Medium | Medium | Position as the best DESIGN.md implementation and toolchain; own the CLI layer |
| Enterprise DesignOps teams don't trust a solo-born format | Low (near-term) | High (long-term) | Build credibility via open-source adoption first; enterprise features come after format legitimacy |
| Solo builders don't convert to paid | Medium | High | Test willingness to pay early with a one-time Vibecoder Kit style offering before building subscription infrastructure |

**Competitive Response Scenarios:**

**If Tokens Studio ships AI integration**: Double down on the New Creative segment they can't serve (too technical, too Figma-locked). Become the "Tokens Studio for people who don't use Figma."

**If Figma absorbs Code Connect + Dev Mode into a full AI governance product**: Position SchemaFlow as the AI-coding-tool-first alternative — "works with Cursor, Claude Code, v0; not just Figma." The Figma moat helps users who are Figma-native; SchemaFlow serves users who build with AI, not with Figma.

---

### Decision Points & Review Cadence

**Go/No-Go Decision Points:**
- **Format spec launch**: Pre-launch — criteria: schema is stable enough for community feedback; one working example integration (CLAUDE.md injection) documented
- **Q3 2026 pivot check**: Criteria: if DESIGN.md files/week < 30 by end of Q2 2026, reassess New Creative segment fit vs. enterprise pivot

**Review Cadence:**
- **Weekly**: CLI install count, generator usage, GitHub star velocity
- **Monthly**: Competitive landscape scan (Tokens Studio, getdesign.md, Google Stitch announcements); article distribution metrics; community signal
- **Quarterly**: Strategy validation — is format adoption accelerating? Is monetization path becoming clear? Is enterprise segment ready to activate?

---

## Quality Checklist

**Diagnosis:**
- [x] Diagnosis is specific — "AI coding tool gap in design governance, not in token management or documentation"
- [x] Grounded in evidence — JTBD research, competitor analysis, community signal from IH/HN, MindStudio research
- [x] Identifies root cause — tools designed for human workflows, not AI workflows
- [x] Clear why this is the critical challenge — fastest-growing segment is unserved; problem is unnamed = no incumbent defense

**Guiding Policy:**
- [x] Directly addresses the diagnosis — format-first, AI-native, New Creative entry
- [x] High-level approach — not a feature list
- [x] Explains how it solves the diagnosed problem — format standard creates the AI governance layer incumbents lack
- [x] Explains why vs. alternatives — head-to-head with Tokens Studio rejected; enterprise-first rejected
- [x] Describes competitive advantage created — format adoption = switching cost moat

**Coherent Actions:**
- [x] 5 specific actions
- [x] All support guiding policy
- [x] Actions reinforce each other (format → CLI → article → community loop)
- [x] No contradictions
- [x] Each has owner, timeline, and success signal

**Competitive Analysis:**
- [x] Key competitors identified and profiled (5 detailed, additional monitored)
- [x] Strengths/weaknesses per competitor
- [x] Positioning map with clear white space identification
- [x] Competitive moats identified
- [x] Porter's 5 Forces completed

**Action Plan:**
- [x] Initiatives with timelines and metrics
- [x] Assumptions stated explicitly with validation plans
- [x] Risks identified with mitigations and scenarios
- [x] Review cadence and decision points set

**Overall:**
- [x] Strategy defensible — format standard moat; open-source distribution
- [x] Evidence-based — grounded in JTBD research, competitive research, community signals
- [x] Realistic — solo-stage constraints respected; enterprise deferred
- [x] Internally consistent — all moves support the format-first positioning
