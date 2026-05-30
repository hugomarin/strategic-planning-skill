# Input Analysis (internal scaffolding — delete after session)
Generated: 2026-05-30
Project: SchemaFlow

---

## Sources available

| File | Description |
|---|---|
| `Propuesta Estrategica Ampliada.md` | 15-section strategic memo for SchemaFlow. Covers ICP definition, JTBD, competitive map, lifecycle, and product recommendations. Single-authored document. Strong analytical coherence; no user research, behavioral data, financial constraints, or pricing information. All thesis support is reasoned inference, not external behavioral signal. |

## Missing sources

No external documents are explicitly referenced from within the Input. However, the document implies the existence of:

- **User research / interview data** — implied as basis for JTBD and persona pain points, but no source document exists. Uploading user interview notes or behavioral observations would improve precision of `user-architecture.md` and `product-thesis.md`. Not required to proceed.
- **Technical feasibility assessment** — URL scanning and extraction pipeline is assumed feasible; no technical document exists. Not required to proceed.

## Ontological map

| Entity | Type | Appears in | Tension with |
|---|---|---|---|
| SchemaFlow | Strategic — product | All sections | Self-defined by analysis — no external validation |
| Aesthetic drift | Strategic — core problem | §2, §3, §7 | Assumed to be primary obstacle; not validated vs. speed/capability/cost alternatives |
| AI-native product builders | User — primary ICP | §5, §6, §7 | ICP is simultaneously narrow (must feel coherence loss) and broad (4 distinct personas) — conflict C-002 |
| Design memory | Strategic — value concept | §2, §4.3, §10 | Core concept also used as differentiator — risk of being either too abstract or too feature-specific |
| Drift detection | Technical — core capability | §10, §14 | Listed as both initial priority output AND retention-phase feature — conflict C-001 |
| UI Kit / Design.md / Agent instructions | Technical — core outputs | §12, §14 | Design.md as artifact name may imply premature standard — conflict C-003 |
| Founder / indie hacker | User — persona 1 | §6.1 | One of four personas — which is primary for v1 is unresolved |
| Designer-builder | User — persona 2 | §6.2 | One of four personas |
| Developer with product sensibility | User — persona 3 | §6.3 | One of four personas |
| Small agency / boutique studio | User — persona 4 | §6.4 | One of four personas |
| getdesign.md | Competitive — direct | §9 | Named close competitor at extraction moment |
| Figma / Dev Mode | Competitive — partial overlap | §9, §11 | Integration target AND possible indirect competitor |
| Chromatic / Percy | Competitive — adjacent | §9, §11 | Pixel diff, differentiated from semantic drift |
| Cursor / Claude Code / v0 / Lovable | Ecosystem — AI coding tools | §5, §11, §14 | Both integration target AND acquisition channel |
| Manual workflows (screenshots + Claude) | Competitive — close alternative | §9 | Differentiation vs. this is asserted, not demonstrated |
| Design.md format | Strategic — potential standard | §4.3, §12.4 | §4.3 says defer standard-as-message; §2 names it as a public artifact — conflict C-003 |
| Pricing / Monetization | Missing entity | — | Completely absent |
| Runway / Financial constraints | Missing entity | — | Completely absent |
| Team composition | Missing entity | — | Completely absent |

## Coverage map

| KA | Answered | Partial | Absent | Required gaps |
|---|---|---|---|---|
| strategy-brief | SB-05, SB-06 | SB-01, SB-02, SB-03, SB-04 | SB-07, SB-08 | 4 partial required (SB-01–04) |
| product-thesis | PT-01, PT-07, PT-08 | PT-02, PT-05 | PT-03, PT-04, PT-06 | 5 partial/absent required (PT-02–06) |
| user-architecture | UA-03, UA-06 | UA-01, UA-02, UA-04, UA-05, UA-07, UA-08 | — | 6 partial required |
| product-architecture | — | PA-02, PA-04, PA-06, PA-07, PA-08 | PA-01, PA-03, PA-05 | 8 partial/absent required |
| objectives-architecture | — | — | OA-01 through OA-08 | All 8 absent |

**Total:** 7 answered / 15 partial / 17 absent across 39 questions. 26 required questions are partial or absent.

## Claims with evidence

1. "The core problem is aesthetic drift at AI generation speed" — Source: §2, §3
2. "Users feel the problem before being able to diagnose it technically" — Source: §3
3. "The category of current tools is fragmented" — Source: §3, §8
4. "AI-native builders using Cursor, Claude Code, v0, Lovable, Bolt, Replit, Windsurf are the entry ICP" — Source: §5
5. "Manual workflows with screenshots + Claude/Cursor are the main current alternative" — Source: §9
6. "getdesign.md competes directly in the extraction moment" — Source: §9
7. "Chromatic and Percy detect visual differences (pixel diff), not semantic/aesthetic drift" — Source: §11, §8
8. "Figma, Zeroheight, Specify are designed for human-to-dev workflows, not agent-to-agent context" — Source: §11
9. "Design.md should be treated as an output artifact, not the complete product" — Source: §12.4
10. "Acquisition should come through immediate utility, not through standard/category positioning" — Source: §4.3
11. "Four buyer personas identified: Founder/indie hacker, Designer-builder, Developer with product sensibility, Small agency" — Source: §6
12. "Anti-priorities include enterprise governance, Figma replacement, token management, visual regression, landing page generation" — Source: §5, §9
13. "Lock-in mechanism is the SchemaFlow format itself and project history" — Source: §4.3, §10
14. "Functional, Social, Emotional JTBD with sub-jobs; frictions: cada parte parece de una app distinta, la AI no preserva suficientemente la intención estética" — Source: §7, §6
15. "Priorities sequenced: acquisition = extraction; activation = aha moment; retention = living memory" — Source: §12, §14
16. "Activation aha moment: 'Esta herramienta entendió mi producto y produjo algo que puedo usar con mis agentes'" — Source: §12.2
17. "Recurrence comes from drift detection, re-scan, version comparison, persistent project rules — not one-time Design.md generation" — Source: §12.3

## Assumed claims

1. "Users will find the aha moment in minutes" — Appears in: §12.2 — No evidence found; product hypothesis
2. "SchemaFlow's extraction quality is meaningfully better than screenshots + prompts" — Appears in: §2, §9 — No evidence found
3. "AI-native builders will pay for a design memory layer" — Appears in: §5 implicitly — No pricing research or willingness-to-pay data cited
4. "Agent instructions generated by SchemaFlow are more actionable than manually written ones" — Appears in: §2, §12.1 — No evidence found
5. "Visual consistency is the primary obstacle for AI-native builders, not speed, capability, or cost" — Appears in: §3, §7 — No user research cited
6. "Re-scanning and versioning will drive retention" — Appears in: §12.3, §10 — No cohort data or retention signal cited
7. "The format/standard strategy will create lock-in" — Appears in: §4.3 — No adoption signal or network effect evidence cited
8. "The 'High Taste, Low Craft' framing limits the addressable market" — Appears in: §4.1 — Strategic reframing, no user research cited
9. "No single tool currently covers extraction → agent instructions → drift detection end-to-end" — Appears in: §9 — Asserted, not verified

## Source conflicts

| Conflict ID | Topic | Sources | Conflict | Strategic impact | Recommendation | NHR? |
|---|---|---|---|---|---|---|
| C-001 | Drift detection timing | §14 vs. §10 | Drift detection listed as initial priority AND as retention-phase feature — same term, may be two different capability levels | Medium — ambiguity on what ships in v1 vs. what ships at retention phase | Clarify: is MVP drift detection a "warning" (light) and retention drift detection "continuous monitoring" (deep)? | Yes |
| C-002 | Entry ICP breadth | §5 vs. §6 | §5 defines single ICP type; §6 presents four distinct personas with different triggers and pains — document does not resolve which is v1 primary | High — four personas cannot receive optimized onboarding simultaneously; activation design will be diluted | Select one primary persona for first acquisition wave; treat others as secondary | Yes |
| C-003 | Design.md as standard vs. artifact | §4.3 vs. §2 | §4.3 says "standard is a market strategy, not an initial message" — defer positioning. §2 uses Design.md as a named product output, implying a public format | Low — framing tension, not structural | Resolve: is Design.md an internal artifact name or a public format standard claim? | Yes |
| C-004 | Differentiation vs. acknowledged alternatives | §9 vs. §2–3 | Manual workflows with screenshots + Claude/Cursor named as close alternative, but SchemaFlow's quality advantage over them is not demonstrated | High — if close alternative already delivers similar output, differentiation must be in quality or depth, not category | Operationalize: what specifically does SchemaFlow do that a screenshot + Claude prompt cannot? | Yes |

## Tactical inputs found

| Tactical item | Source | Strategic interpretation | Thesis link | Constraint | Recommendation |
|---|---|---|---|---|---|
| "Dame la URL de mi app" as entry mechanism | §4.3 | Acquisition flow depends on URL-based scanning as core technical capability | Extraction = thesis activator | Technical feasibility of URL scanning (public vs. private apps, auth, SPAs) is unresolved | Validate technical feasibility before committing to this as primary acquisition flow |
| "Revisión humana de hallazgos" as initial priority | §14 | Implies extraction quality is not yet fully trustworthy | PT-04 evidence gap | Creates manual bottleneck limiting scalability at acquisition | Consider whether this is a QA gate or a product feature; affects build scope |
| Four buyer personas in §6 | §6 | Implies persona-specific messaging, pricing, and channels will eventually diverge | UA — ICP breadth | Premature fragmentation risk before PMF in one segment | Select one primary persona for initial acquisition optimization |
| Cursor, Claude Code, v0, Lovable as integration targets | §11, §14 | Adoption may depend on integration with dominant AI coding tools | PA-06 dependencies | Integration partnerships or API constraints | Evaluate as Phase 2–3 efforts, not acquisition gates |
| Design.md as named format | §2, §4.3 | Potential standard-as-lock-in strategy | PT — lock-in mechanism | Risk of premature standard claim before adoption exists | Treat as artifact name internally; defer public standard positioning |

## Candidates for open-questions.md

1. Which buyer persona is the v1 primary entry segment? (blocking — UA, SB)
2. What specific event or moment triggers an AI builder to seek SchemaFlow now? (blocking — UA)
3. What observable signal distinguishes high-fit from low-fit within "AI-native builders"? (blocking — UA)
4. What assumptions must be true for the thesis, stated as falsifiable claims? (blocking — PT)
5. What evidence supports aesthetic drift as the primary obstacle vs. speed, capability, or cost? (blocking — PT, SB)
6. What is the strongest steelmanned counterargument against the thesis? (blocking — PT)
7. What would falsify the thesis? (blocking — PT, OA)
8. What are the measurable success signals at 3, 6, and 12 months? (blocking — SB, OA)
9. What is the pricing model and willingness-to-pay signal? (blocking — SB, OA)
10. What is the current product stage? (blocking — SB, PA)
11. What is the team composition and technical capability? (blocking — PA)
12. What is the runway / financial constraint? (blocking — OA)
13. What is the primary acquisition channel? (blocking — SB, OA)
14. How does SchemaFlow demonstrate quality superiority over screenshots + Claude/Cursor? (weakening — PT, PA)
15. Is drift detection at MVP a light warning or a continuous monitoring system? (weakening — PA, C-001)
16. What makes manual re-prompting worse than renewing SchemaFlow as a retention argument? (weakening — UA, PT)

## Non-omittable questions

1. **HRQ-01 — GTM segment:** Which single persona is the first wave? Without this, messaging, channel, and onboarding cannot be designed. Affects: all artifacts.
2. **HRQ-02 — Purchase trigger:** What specific event makes an AI builder seek SchemaFlow? Without a trigger, there is no acquisition moment to optimize. Affects: UA, SB.
3. **HRQ-03 — Pricing model:** What is the monetization structure? Affects acquisition (free trial, freemium, paid) and retention design. Affects: OA, SB.
4. **HRQ-04 — Primary acquisition channel:** Community, SEO, integration marketplace, word-of-mouth, outbound? Affects: SB, OA.
5. **HRQ-05 — Demand signal:** Any signal that users would pay? Even one paid customer, pre-order, or waiting list? Affects: PT evidence.
6. **HRQ-06 — Product stage:** Is SchemaFlow a working prototype, launched product, or conceptual? Affects: PA, phase sequencing.
7. **HRQ-07 — Team / technical constraints:** Can the URL scanning and extraction pipeline be built with current resources? Affects: PA, phase sequencing.
8. **HRQ-08 — Runway:** What is the financial constraint on the timeline? Affects: OA, phase sequencing.
9. **HRQ-09 — Falsification threshold:** At what observable signal does the team pivot or stop? Affects: PT, OA.
10. **HRQ-10 — Problem evidence:** At minimum, 3–5 user conversations, forum posts, or behavioral signals that drift is real and causes users to seek solutions.

## Proposed generation order

1. **product-thesis.md** — Most answered (PT-01, PT-07, PT-08); clearest starting point. Generate with NHR on PT-02, PT-03, PT-04, PT-05, PT-06.
2. **strategy-brief.md** — Depends on thesis clarity. Generate after PT with NHR on SB-01–04, SB-07, SB-08.
3. **user-architecture.md** — Depends on thesis and ICP clarity. Generate after SB with NHR on UA-01, UA-02, UA-04, UA-05, UA-07.
4. **product-architecture.md** — Highest gap count (0 answered required). Generate after UA; apply NHR on PA-01, PA-03, PA-05; resolve C-001 first.
5. **objectives-architecture.md** — All 8 questions absent. Generate only after HRQ-01, HRQ-03, HRQ-05, HRQ-08, HRQ-09 are answered or explicitly deferred.
6. **strategic-roadmap.md** — Hold until all 5 KAs are active or needs_human_review with explicit decision to proceed.
