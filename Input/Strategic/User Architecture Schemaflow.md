# User Architecture — Schemaflow

## Artifact: user-architecture

### Description

This artifact captures the current understanding of Schemaflow’s user architecture. The product is still in a pre-ICP stage, so this document should not be read as a validated buyer definition. Instead, it defines the initial learning segment, observable fit signals, user tension, current workarounds, purchase-trigger hypotheses, exclusions, and adoption logic.

The strategic premise is that Schemaflow should start with AI-native builders because they are close to the problem and have low adoption friction, but the product must progressively narrow toward the segment with the highest retention and purchase probability.

---

## UA-01 — Primary User / ICP

### Question

Who is the primary user described in observable, selectable criteria — company stage, role, tool usage, measurable behavior?

### Answer

Schemaflow is currently **pre-ICP**. The product does not yet know with confidence which segment will buy. The initial target should therefore be treated as a **learning ICP**, not a fully validated buying persona.

The initial learning ICP is:

**AI-native builders who already have a real product in motion, use AI tools to generate or modify UI, and are beginning to experience visual governance as a recurring cost.**

This segment may include:

- founder-builders,
- advanced indie hackers,
- technical freelancers,
- small agency builders,
- product engineers,
- design engineers,
- technical product operators,
- and early startups with enough product maturity or budget to care about visual consistency.

The strategic goal is to start with a broad but relevant AI-native builder segment, observe which users experience the strongest pain and willingness to pay, and progressively narrow toward the ICP with the highest purchase probability.

### Observable Criteria

**Role / profile:** founder-builder, indie hacker, freelancer, small agency builder, product engineer, design engineer, technical product operator.

**Product stage:** not just an idea; the user has a product in motion, beta, client-facing surface, demo, users, or multiple products in development.

**Tool usage:** uses AI-native tools such as Cursor, Claude, Claude Code, Lovable, v0, Bolt, Replit, Figma AI, or similar workflows to build UI or code.

**Pain behavior:** spends time correcting buttons, components, styles, spacing, typography, or visual inconsistencies introduced during AI-assisted iterations.

**Economic signal:** saving 5–10 hours per month in design correction would matter; the user already pays for tools such as AI coding tools, hosting, design tools, dev tooling, or product infrastructure.

**Purchase probability:** still uncertain. It may emerge from freelancers managing multiple client products, agencies, startups with budget, founders with monetized products, or builders whose visual consistency problem creates operational cost.

### Key Distinction

Schemaflow should separate:

1. **Acquisition / learning segment:** AI-native builders curious enough to scan their product and see their real UI kit.
2. **Likely monetizable segment:** users for whom visual drift has operational cost: multiple products, client work, monetized products, brand-sensitive interfaces, mature product surfaces, or enough correction time to justify payment.
3. **Non-priority paid segment:** people experimenting with a very early MVP, no users, no monetization, and no real cost attached to visual inconsistency.

### Consolidated Answer

**Schemaflow is currently pre-ICP. The initial target is a learning ICP, not a fully validated buying persona: AI-native builders who already have a real product in motion, use AI tools to generate or modify UI, and are beginning to experience visual governance as a recurring cost. This segment may include founder-builders, freelancers managing multiple products, small agencies, product engineers, design engineers, or early startups with enough product maturity or budget to care about visual consistency. The strategic goal is to start with a broad but relevant AI-native builder segment, observe which users experience the strongest pain and willingness to pay, and progressively narrow toward the ICP with the highest purchase probability.**

---

## UA-02 — Observable Signals

### Question

What observable signals — tools used, behaviors, actions — indicate this user is a strong fit right now?

### Answer

A strong-fit user is not just someone who “cares about design.” A strong-fit user shows observable behavior that indicates they are building with AI, producing UI changes repeatedly, and already spending time trying to recover consistency.

### Strong Fit Signals

1. **Uses AI-native building tools regularly**  
   Uses Cursor, Claude Code, Lovable, v0, Bolt, Replit, Figma AI, or similar tools to create or modify UI/code.

2. **Has a real product surface to scan**  
   Has a public URL, beta, dashboard, landing page, internal app, client project, or product in production. The user is not only ideating.

3. **Makes repeated UI changes**  
   Generates screens, components, landing pages, dashboards, settings pages, onboarding flows, or visual changes recurrently.

4. **Manually corrects visual inconsistencies**  
   Spends time adjusting buttons, fonts, spacing, colors, cards, inputs, switches, or components that AI left plausible but inconsistent.

5. **Uses prompts as a design-control workaround**  
   Prompts agents with instructions such as “make this consistent,” “use the same style,” “match the previous button,” “follow the design system,” “clean up the UI,” or “apply the same style across the app.”

6. **Has more than one product, client, or surface to maintain**  
   Payment likelihood increases if the user manages multiple projects, clients, products, landing pages, or dashboards. In these cases, visual drift becomes an operational cost.

7. **Already pays for product-building infrastructure**  
   Pays for Vercel, Supabase, hosting, AI tools, Figma, Linear, GitHub, Cursor, Claude, Lovable, or other tools. This indicates willingness to pay if Schemaflow saves real time.

8. **Has visible inconsistency in the UI**  
   The product shows accidental variants: multiple button styles, inconsistent typography, irregular spacing, different cards, duplicated components, or scattered CSS.

9. **Expresses frustration around control, not only aesthetics**  
   Says things like: “AI makes it fast, but I can’t keep it consistent,” “it does not feel fully mine,” “each chat changes things,” or “I spend more time fixing UI than building the feature.”

10. **Wants outputs that can be reused by agents**  
   Asks for `design.md`, `ui-kit.md`, rules, prompts, tokens, or instructions so the agent does not keep breaking the design.

### Consolidated Answer

**Strong-fit users show evidence that they are already building UI with AI and trying to recover visual control. Observable signals include regular use of AI-native tools such as Cursor, Claude, Lovable, v0, Bolt, Replit, or Figma AI; having a real product URL or client-facing surface; making repeated UI changes; manually correcting buttons, typography, spacing, colors, cards, inputs, or switches; prompting agents to “make it consistent”; managing multiple products or client projects; already paying for product-building infrastructure; and showing visible UI drift. The strongest fit signal is not design taste alone, but repeated behavior that reveals visual governance has become an operational cost.**

---

## UA-03 — Central Tension

### Question

What is the central tension this user lives with — the gap between what they want to do and what their current system allows?

### Answer

The user wants **AI speed without losing product authorship**.

They want to generate, iterate, and ship faster, but their current AI-native workflow makes it hard to preserve visual consistency, design intent, and control across screens, components, chats, and iterations.

The user is not blocked from producing UI. They are blocked from trusting that the UI they produce will remain coherent.

### The Tension

**Functional tension:** AI allows the user to create UI quickly, but does not reliably preserve consistency across changes.

**Emotional tension:** the product may work, but the user feels they no longer fully control how it looks. The product starts feeling less “theirs.”

**Economic tension:** correcting visual inconsistencies can take more time than building functionality, especially if the issue repeats every week or across multiple products.

### Consolidated Answer

**The central tension is that AI-native builders want to move faster without losing control, but the faster they generate UI, the harder it becomes to preserve visual coherence. Their current workflow helps them create screens, components, and features quickly, but it does not reliably maintain design intent across chats, iterations, and product surfaces. As a result, they spend disproportionate time correcting buttons, typography, spacing, switches, cards, and other visual patterns that should have stayed consistent. The product is not necessarily broken, but it no longer feels fully governed or fully theirs.**

### Positioning Line

**AI helps them build faster, but makes it harder to keep the product visually under control.**

---

## UA-04 — Workarounds

### Question

What workarounds does this user use today — what tools or behaviors indicate the problem exists and they are trying to solve it?

### Answer

AI-native builders currently try to solve visual drift through manual correction, repeated prompting, ad hoc documentation, component copying, and visual comparison.

These workarounds show the problem exists because users are already spending time trying to recover consistency, even without a dedicated governance tool.

### Current Workarounds

1. **Repeated prompting inside the coding agent**  
   Users ask Cursor, Claude, Lovable, or v0 to “make this consistent,” “use the same button style,” “match the previous screen,” “apply the same design system,” or “clean up the UI.” The agent may fix one screen while breaking another or reinterpret the instruction differently across chats.

2. **Manual visual correction in code**  
   Users manually edit CSS, Tailwind classes, component files, or stylesheets to adjust buttons, inputs, spacing, fonts, cards, and variants. This is a strong pain signal because it turns the problem into measurable time loss.

3. **Copy-paste from the “best” existing component**  
   Users find the component that looks best and copy it elsewhere. This may fix a local inconsistency but does not create a source of truth or prevent future drift.

4. **Ad hoc UI kit or design notes**  
   Users keep notes such as “this is the correct color,” “this is the primary button,” “use this border radius,” or “do not use this style.” These notes may live in Notion, README files, prompts, markdown files, comments, or memory, but they are often disconnected from the agent and the real code.

5. **Figma / manual design reference**  
   Users rely on Figma, brand manuals, or visual references as intent sources, but still have to translate them manually into AI-generated code.

6. **Screenshot comparison / eyeballing**  
   Users open screens side by side and compare buttons, fonts, spacing, or cards visually. This can identify obvious inconsistencies but does not scale.

7. **One-off cleanup sessions**  
   After many AI-assisted iterations, users run a visual cleanup session: “now I need to fix the UI.” This cleans up accumulated debt but does not prevent future drift.

8. **Component refactor after the fact**  
   When drift becomes obvious, users consolidate components or create shared components. This improves code quality but usually happens late and does not necessarily capture design intent for future generations.

### Consolidated Answer

**Today, strong-fit users work around visual drift by repeatedly prompting AI agents to make screens consistent, manually editing CSS/Tailwind/component files, copying the “best” existing component across the product, maintaining ad hoc design notes or markdown rules, referencing Figma or brand manuals manually, comparing screenshots by eye, running one-off UI cleanup sessions, and refactoring components after drift has already accumulated. These behaviors indicate that the problem is real because users are already spending time trying to restore visual control. The weakness of these workarounds is that they are local, manual, and fragile: they may fix one screen or component, but they do not create a governed design context that AI can reliably reuse across future iterations.**

---

## UA-05 — Purchase Trigger

### Question

What triggers the purchase decision — what specific moment or event makes this user look for a solution right now?

### Answer

Schemaflow does not yet know the exact purchase trigger because the product is still pre-ICP. The current purchase trigger should therefore be treated as a hypothesis, not a validated fact.

The key distinction is:

**Usefulness does not automatically create willingness to pay.**

The current hypothesis is that users will pay when visual governance becomes an ROI problem: when paying for Schemaflow is cheaper than spending hours manually correcting design drift, when consistency affects launch/client/product quality, or when the user needs confidence that AI-generated work is staying aligned with their design system.

### Purchase Trigger Hypotheses

1. **Time-savings trigger**  
   The user realizes they are spending too many hours correcting UI. If Schemaflow saves 5–10 hours per month, the price may be justified.

2. **Confidence / control trigger**  
   The user wants to continue building with AI but needs confidence that a governance layer is observing, detecting, and helping maintain visual coherence.

3. **Quality / maturity trigger**  
   The product reaches a stage where inconsistency has a cost: launch, demo, client delivery, monetized product, brand sensitivity, or team growth.

4. **Segment-specific trigger**  
   The trigger may vary by segment. Freelancers may pay before client delivery. Startups may pay before launch or demo. Mature builders may pay when recurring correction time becomes more expensive than the tool.

### Consolidated Answer

**The purchase trigger is currently a hypothesis, not a validated fact. Schemaflow is still pre-ICP, so the team should not assume that usefulness automatically creates willingness to pay. The current hypothesis is that payment becomes likely when visual governance creates clear ROI: the user saves meaningful correction time, produces better and more consistent design faster, shortens development cycles, or gains confidence that AI-generated UI is being monitored against an intended system. The trigger may vary by segment: freelancers may pay before client delivery, startups may pay before launch or demo, and mature builders may pay when recurring correction time becomes more expensive than the tool. Schemaflow should validate which situation produces the strongest willingness to pay.**

### Validation Principle

**The purchase trigger is not “the user sees drift.” The purchase trigger is when the user believes visual governance saves more time, risk, or quality loss than it costs.**

---

## UA-06 — Exclusions

### Question

Who is explicitly excluded from this product in this phase, and why?

### Answer

In this phase, Schemaflow should exclude users whose needs would pull the product away from the core learning loop:

**scan a real product → reveal visual drift → generate actionable context → correct → re-scan**

Some excluded users may become relevant later, but optimizing for them now would distort the product before Schemaflow validates the core governance loop.

### Excluded Segments

1. **Very early MVP builders with no real product surface**  
   Users who are only exploring an idea, have no real UI, no users, no quality pressure, and no cost attached to inconsistency. They may use the free tier out of curiosity, but they should not guide the roadmap.

2. **Users who only want inspiration or better taste**  
   Users looking to make their design “prettier” without a real product to govern. Schemaflow may eventually help improve design, but this phase should not compete as a visual inspiration or design-generation tool.

3. **Enterprise design-system teams with heavy governance needs**  
   These teams may appear to be a fit, but they likely require permissions, roles, compliance, Figma integrations, Storybook, design tokens, approval workflows, audit trails, and multi-team collaboration. Optimizing for them too early would make the product heavy before the individual governance loop is proven.

4. **Designers who do not work close to implementation**  
   Designers who only operate in Figma or brand direction but are disconnected from code, AI agents, or the live product may need a different tool. Schemaflow lives in the gap between real design, real code, and AI-generated implementation.

5. **Builders who do not care about visual consistency yet**  
   Users who accept inconsistency as part of a hackathon, exploration, or early MVP validation phase. They may become users later, but if they currently choose speed over control, they should not define product decisions.

6. **Users looking for full automatic redesign**  
   Users expecting Schemaflow to redesign the whole product automatically. The thesis is governance, not “AI designer that creates a new UI from scratch.”

7. **Teams whose primary need is collaboration before individual value**  
   Teams that first need roles, permissions, comments, approvals, and multiuser workflows. The product should prove individual user value before building team collaboration depth.

### Consolidated Answer

**In this phase, Schemaflow should exclude users whose needs would pull the product away from the core governance loop. This includes very early MVP builders with no real product surface, users looking only for design inspiration or better taste, enterprise design-system teams that require heavy collaboration and compliance workflows, designers disconnected from implementation, builders who do not yet care about visual consistency, users expecting a full automatic redesign, and teams whose primary need is collaboration before individual value. Some of these users may become relevant later, but optimizing for them now would distort the product before Schemaflow validates whether AI-native builders with real products will scan, correct, re-scan, and eventually pay for visual governance.**

### Strategic Exclusion

**Do not build for “anyone making UI with AI.” That segment is too broad and will dilute product decisions.**

---

## UA-07 — Adoption Logic

### Question

Why would this user adopt, use regularly, and pay — what is the adoption logic for each segment?

### Answer

Schemaflow’s adoption logic is not the same for every user. The product may attract a broad set of AI-native builders through a free scan, but regular usage and payment will likely come from narrower segments where visual drift creates recurring operational cost.

The adoption path should be evaluated in three steps:

**Try → Return → Pay**

### 1. AI-native Founder-builder

**Why they try:** they want to see the real state of their UI. The first scan works as a strong curiosity hook: “what UI kit is my product actually producing?”

**Why they return:** they return if the scan reveals problems they recognize and if the second scan shows progress after correction.

**Why they pay:** they pay if saving visual correction time becomes cheaper than manual fixing, especially before launch, demos, sales, or product growth.

### 2. Freelancer / Solo Builder Managing Client Work

**Why they try:** they need to deliver work that looks consistent without spending hours manually polishing UI.

**Why they return:** each new client/project creates another scan opportunity. Schemaflow can become part of their delivery checklist.

**Why they pay:** they pay if Schemaflow reduces rework, improves delivery quality, and helps them present a more professional product to clients.

### 3. Small Agency / Studio

**Why they try:** they manage several products or clients and need to detect visual inconsistencies quickly.

**Why they return:** each project, sprint, or delivery can require visual review.

**Why they pay:** they pay if Schemaflow standardizes visual QA, reduces review hours, and generates reusable artifacts for teams or AI agents.

### 4. Early Startup / Product Team with Some Budget

**Why they try:** they have a product surface large enough to accumulate visual debt and want to understand where inconsistency exists.

**Why they return:** they return if Schemaflow becomes part of their release or iteration cycle: before releases, after AI-assisted work, or during consistency reviews.

**Why they pay:** they pay if Schemaflow reduces quality risk, accelerates development, increases confidence, and helps maintain design as the product grows.

### 5. Free / Exploratory Users

**Why they try:** curiosity and low-friction access. They want to see their real UI kit.

**Why they return:** they return only if they discover a real problem and have a next change to validate.

**Why they pay:** they probably do not pay yet unless their product matures or they hit value limits: more pages, more scans, history, exports, authenticated scan, or multi-project usage.

### Consolidated Answer

**Schemaflow’s adoption logic should be segmented by maturity and operational cost. Broad AI-native builders may try the product because a free scan gives them immediate visibility into their real UI kit. Regular usage depends on whether the first scan creates a correction loop: the user sees drift, acts on recommendations, and returns to verify improvement. Payment is most likely when visual governance has ROI: the user saves meaningful correction time, improves delivery quality, reduces client or launch risk, or needs reusable AI-actionable context across projects. Founder-builders may pay when the product is mature enough that visual control matters; freelancers and agencies may pay when Schemaflow becomes part of client delivery and QA; startups may pay when consistency affects product quality and release confidence. Exploratory users may create acquisition volume, but should not be treated as proof of monetizable demand unless they return, correct, re-scan, export, or hit paid limits.**

### Adoption Logic Summary

**Try:** “I want to see my real UI kit.”  
**Return:** “I want to know if it improved or broke again.”  
**Pay:** “It costs me less to pay than to fix this manually or risk quality.”  

---

## Summary

Schemaflow should treat its current user architecture as a learning system, not a finished ICP definition.

The initial learning segment is AI-native builders with real product surfaces, observable UI-building behavior, and some degree of visual consistency pain. This may include founders, freelancers, agencies, product engineers, design engineers, and early startups.

The core user tension is:

**They want the speed of AI-assisted development without losing visual control, design intent, or product authorship.**

The strongest fit signals are behavioral: repeated AI-assisted UI generation, manual correction of visual inconsistencies, prompts to “make it consistent,” visible drift, and demand for reusable design context.

The product should avoid optimizing for users who are too early, too enterprise-heavy, too disconnected from implementation, or only looking for inspiration. The immediate goal is to learn which segment actually scans, corrects, re-scans, and eventually shows willingness to pay.

The next strategic step is not to declare a final ICP, but to use early design partners and product behavior to narrow toward the segment with the highest activation, retention, and ROI signals.
