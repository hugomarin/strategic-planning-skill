# Research: Solopreneurs & "New Creatives" in the UI Builder Space
> Date: 2026-05-17 | Via /research-agent

## Key Findings

- **The "no schema pain" narrative is a platform narrative, not a user reality.** Sources written from a platform marketing angle (solopreneur tech stack blogs, "new wave" profiling) consistently omit database and backend as pain points — treating them as solved by the tools themselves. But sources written from a practitioner or product angle (FlowNinja, House of Loops) reveal the opposite: Bubble's database relationships must be architected correctly upfront or performance degrades at scale, and Webflow's CMS hits hard walls that push users to bolt on Supabase or Firebase without the technical foundation to do so. The pain exists; it just doesn't surface in aspirational solopreneur content.

- **There is a structural split in the solopreneur segment that determines whether SchemaFlow is relevant at all.** The Simply Business 2025 report confirms a lifestyle-first majority (coaches, photographers, artists) that never encounters data complexity — they don't build products that need relational schemas. The relevant sub-segment is builders using Bubble or Supabase to ship actual SaaS micro-products: they inherit relational data design obligations without the engineering background to handle them. These two populations share a label ("solopreneur") but have almost nothing else in common from SchemaFlow's perspective.

- **Bubble creates a schema design obligation disguised as a feature.** Bubble's built-in database is positioned as a superpower — and it is, for getting started. But as FlowNinja and House of Loops both confirm, data type relationships must be modeled correctly before the app scales. There's no migration tooling, no visual schema audit layer, and no way to export to another system. Bubble builders are locked into a schema they likely didn't architect with intention. SchemaFlow's opportunity here is pre-build schema planning — not database management — specifically for people about to design in Bubble who want to think through data relationships before they're locked in.

- **The schema tooling market is currently oriented toward engineering teams, not non-technical builders.** The DbSchema blog survey of tools frames the target user as someone who "designs before deployment" — which is the right framing — but every tool in the category assumes SQL literacy, developer toolchains, or team-based workflows. The Reliable Data Engineering piece on code-generating schema tools surfaces the same gap: tools that bridge visual modeling and actual implementation are underserved, but they're being built for engineers who want to skip writing DDL, not for founders who don't know what DDL is. SchemaFlow addresses a segment that the current market has not designed for.

- **"New Creatives" as a segment behaves like a segment but doesn't know it's one.** No source uses the label, but the behavioral pattern is consistent across practitioner sources: design-developer hybrids who chose Bubble or Webflow because they think visually, who are building revenue-generating products, and who are hitting backend ceilings they weren't warned about. This group hires Bubble Experts not because they want to outsource but because schema complexity exceeded their mental model. That outsourcing moment is the pain event SchemaFlow could prevent.

---

## Surprising / Challenges Assumptions

- **The dominant blocker for this segment isn't technical complexity — it's invisible complexity.** The assumption going in was that builders know they have a schema problem. The research suggests they often don't — Bubble's abstraction is good enough that they ship an MVP without realizing their data model is fragile. The pain is deferred and then acute (performance degradation, scaling dead ends), not felt upfront. This means SchemaFlow's positioning challenge isn't "convince them they need this" but "surface the pain before it's too late to fix it" — which is a different product and marketing problem entirely.

- **The most analytically rigorous source (Simply Business primary data) is the least useful for SchemaFlow.** It has real numbers, real segmentation, and credible methodology — but it measures the wrong segment. The 60%+ who underestimated managing every role alone are mostly lifestyle solopreneurs (tradespeople, coaches, artists) dealing with sales and admin overwhelm, not data modeling. High-quality data about the wrong population creates a false signal of "solopreneurs are overwhelmed" that doesn't translate to schema design demand. Signal quality and source quality are not the same thing here.

---

## Gaps — What's Still Unknown

- **No primary data on the Bubble/Supabase builder sub-segment specifically.** All practitioner sources are editorial or consultancy opinion — no survey data, no community research, no product analytics. We don't know how many of these builders exist, how often they hit schema ceilings, or what they actually do when they do (hire experts, abandon the project, find workarounds). This is the most important gap. What would fill it: a structured Reddit/Indie Hackers analysis of "my Bubble app is slow" or "I regret my data model" threads — the Gatherer step flagged this signal exists but didn't retrieve it.

- **We don't know when in the builder journey the schema pain becomes acute.** The research implies it happens at scale — but "scale" is undefined. Is it 100 users? 1,000 records? A second data type? Without understanding the trigger moment, it's impossible to know whether SchemaFlow should be positioned as a day-one planning tool or a triage tool for builders who've already shipped and are now stuck.

- **No data on willingness to pay or tool adoption behavior in this sub-segment.** Solopreneurs are notoriously cost-sensitive (Simply Business data supports this indirectly), but the Bubble builder sub-segment spends on Bubble Expert time — meaning there IS budget for schema help, it's just going to humans. SchemaFlow's pricing and positioning needs to compete with "hire a Bubble Expert" more than it needs to compete with free diagramming tools.

- **The Webflow-to-Supabase migration path is a secondary pain with high potential.** FlowNinja notes that Webflow users who outgrow the CMS often bolt on Supabase without the technical foundation. This transition moment — designer wants dynamic data, chooses Supabase, now needs to design a schema — is a clean, specific trigger event. It wasn't explored in depth in any source, and it may be a better initial beachhead than Bubble (more technically approachable users, cleaner separation between UI layer and data layer).

---

## Source Tensions

**Tension 1: "No pain" sources vs. "structural ceiling" sources.**
The Synthesizer's read: this is not a real contradiction — it's a sampling artifact. "No pain" sources are aspirational solopreneur content written for a broad audience and have no incentive to surface technical complexity. "Structural ceiling" sources are written by practitioners for practitioners who are already inside the pain. Both are accurate about their respective populations. SchemaFlow should weight the practitioner sources heavily and treat the lifestyle solopreneur narrative as a red herring for targeting purposes.

**Tension 2: Bubble's database as superpower AND schema trap.**
This is the central product insight, not a tension to resolve. It's both things simultaneously, at different points in the builder journey. Bubble's database is a superpower at inception (zero setup, immediate data relationships) and a trap at scale (no export, no schema audit, performance tied to early modeling decisions). SchemaFlow's value proposition lives precisely in that gap — it can be the planning layer that makes Bubble's superpower durable. The framing shouldn't be "Bubble's database is bad" but "Bubble's database rewards good schema design, and we help you get there."

**Tension 3: "New Creatives" as an undefined category.**
The Evaluator was right to flag this. The Synthesizer's read: the label is useful as a targeting lens for SchemaFlow's positioning and messaging, but it should not be treated as a validated segment in any external communication or go-to-market claim. Internally, use it to sharpen ICP definition. Externally, describe the behavior ("founders and design-developer hybrids building SaaS on no-code platforms") rather than the label.

---

## Sources Used

- https://www.houseofloops.com/blog/bubble-vs-webflow-vs-framer⭐ Bubble vs. Webflow vs. Framer — House of Loops | https://www.houseofloops.com/blog/bubble-vs-webflow-vs-framer
- https://medium.com/@reliabledataengineering/15-data-modeling-tools-that-generate-code-not-just-diagrams-fea51fa4b785⭐ 15 Data Modeling Tools That Generate Code — Medium / Reliable Data Engineering | https://medium.com/@reliabledataengineering/15-data-modeling-tools-that-generate-code-not-just-diagrams-fea51fa4b785
- https://www.flowninja.com/blog/webflow-vs-bubbleWebflow vs. Bubble — FlowNinja | https://www.flowninja.com/blog/webflow-vs-bubble
- https://dbschema.com/blog/design/best-database-design-tools-2025/Best Database Schema Design Tools in 2026 — DbSchema Blog | https://dbschema.com/blog/design/best-database-design-tools-2025/
- https://medium.com/@e2larsen/emerging-saas-niches-for-solopreneurs-in-2025-e5bf8a6db903Emerging SaaS Niches for Solopreneurs — Medium / Eddie Larsen | https://medium.com/@e2larsen/emerging-saas-niches-for-solopreneurs-in-2025-e5bf8a6db903
- https://www.baytechconsulting.com/blog/why-most-low-code-platforms-eventually-face-limitations-and-strategic-considerations-for-the-futureWhy Low-Code Platforms Fail — Baytech Consulting | https://www.baytechconsulting.com/blog/why-most-low-code-platforms-eventually-face-limitations-and-strategic-considerations-for-the-future
- https://www.simplybusiness.com/resource/2025-solopreneur-report/2025 Solopreneur Report — Simply Business | https://www.simplybusiness.com/resource/2025-solopreneur-report/

---

## Connected to Your Work

| Finding | Project / Goal | So what? |
| --- | --- | --- |
| The schema tooling market is built for engineering teams — non-technical founders and no-code builders are an unserved segment | **SchemaFlow** | This is your market position. Don't soften it. The gap is real and documented. Lean into "designed for founders, not engineers" as the explicit differentiation. |
| Bubble creates schema obligations disguised as features — the pain is deferred, then acute | **SchemaFlow** | SchemaFlow's primary positioning should be pre-build planning, not database management. "Design your schema before Bubble locks you in" is a cleaner, more urgent hook than a general schema tool pitch. |
| The "New Creatives" sub-segment hires Bubble Experts when schema complexity exceeds their mental model — meaning there IS budget, it just goes to humans | **SchemaFlow** | Pricing and positioning should compete with "hire a Bubble Expert for $X/hour" — not with free diagramming tools. This reframes the willingness-to-pay question entirely. |
| The Webflow-to-Supabase transition is an underexplored, clean trigger event with technically approachable users | **SchemaFlow** | This may be a better initial beachhead than Bubble-first. Webflow users already know design tools; they're less locked in; and the UI-to-data separation is cleaner. Worth testing as an ICP hypothesis. |
| The pain is "invisible complexity" — builders don't know they have a schema problem until it's expensive to fix | **SchemaFlow** | Marketing problem as much as product problem. Content strategy needs to surface the deferred pain before it hits — tutorials, case studies, or a "schema health check" entry point could work. |
| Marginalia uses Supabase + Prisma + PostgreSQL — Sergio is living inside the exact stack this segment struggles with | **Marginalia** / **SchemaFlow** | Sergio's own experience building Marginalia is legitimate firsthand ICP research. Decisions made in that schema are signal worth documenting and potentially reusing as SchemaFlow demo content. |
| The "solopreneur" label covers two populations with nothing in common from a schema perspective | **SchemaFlow** (ICP definition) / **Personal brand — Writing** | Don't target "solopreneurs." Target the builder sub-segment specifically. This also applies to any articles Sergio writes about this space — the segment split is a strong editorial angle. |

---

## Memory Recommendations

- [ ] `Memory/learnings/icp-segment-splitting.md` — The "solopreneur" label obscures two populations with completely different needs; the principle of splitting broad segment labels before validating product fit is reusable across any future product or writing work.
- [ ] `Memory/learnings/deferred-pain-positioning.md` — When the user doesn't feel the problem until it's expensive to fix, the marketing problem is surfacing invisible pain early; this pattern (deferred-then-acute pain) recurs in no-code, automation, and tech-debt contexts and is worth naming.
- [ ] `Memory/decisions/schemaflow-icp.md` — Document the decision to focus SchemaFlow on Bubble/Supabase builders (not broad solopreneurs), and log the Webflow-to-Supabase path as the secondary ICP hypothesis to test first; this decision should be stable before any go-to-market work begins.
- [ ] `_Projects/SchemaFlow.md` → Create this file — SchemaFlow has no registry entry yet; it needs one before the project grows any further, and this research gives it a strong Research section to start from.
- [ ] Not worth saving — the Simply Business primary data (60%+ overwhelmed by managing every role). High-quality source, wrong population. No reuse value for SchemaFlow or Sergio's current goals.

---

## Immediate Action Items

- [ ] **Create \****`_Projects/SchemaFlow.md`** — SchemaFlow is active but has no registry file. Use this research as the founding Research section. Include: ICP definition (Bubble builders and Webflow-to-Supabase migrants), positioning anchor ("pre-build schema planning for non-technical founders"), and the competitor framing ("competes with hiring a Bubble Expert, not with diagramming tools"). Path: `/Users/smartinez/Workspace/systems/sergio-os/_Projects/SchemaFlow.md`
- [ ] **Define the two ICP hypotheses as testable bets** — Write one paragraph each for (A) Bubble builders pre-ship and (B) Webflow users migrating to Supabase. Pin which one SchemaFlow will validate first and what evidence would confirm or kill it. This goes in the new `_Projects/SchemaFlow.md` under a "ICP Hypotheses" section.
- [ ] **Mine Marginalia's Prisma schema for SchemaFlow demo content** — Sergio built a real schema for a real app. Document the decisions made in `/Users/smartinez/Workspace/projects/Marginalia/web-nextjs/prisma/schema.prisma` as a case study: what relationships exist, what would have been hard to design without tooling, what a visual schema would have surfaced earlier. This is credible, non-generic demo material.
- [ ] **Run a targeted Reddit/Indie Hackers search on "Bubble slow" or "regret my data model"** — The research flagged this as the most important gap: no primary data on how often the Bubble builder sub-segment hits schema ceilings or what they do when they do. A structured Gatherer pass on these threads would close the most critical unknown before committing to positioning.
- [ ] **Draft one article using the segment-split insight** — "Why 'solopreneurs' is the wrong lens for no-code tools" or a variation is a strong Q2 writing angle that builds personal brand credibility in the builder space, reinforces SchemaFlow's ICP thinking, and serves the Writing goal (3 articles by June 30). Surfaces Sergio as a thinker in this space before SchemaFlow launches.
