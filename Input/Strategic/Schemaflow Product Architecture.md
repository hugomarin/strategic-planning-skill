# Product Architecture — Schemaflow

## Artifact: product-architecture

### Description

This artifact defines the product architecture required for Schemaflow to express its product thesis. It describes the principles, modules, critical flows, indispensable features, constraints, dependencies, risks, and open questions that should guide product decisions and build sequencing.

Schemaflow’s architectural premise is that the product is not merely a UI scanner. It is a progressive visual governance layer for AI-assisted product development: it helps builders extract the real UI kit from their product, understand drift, define what is official, generate AI-actionable context, and return to re-scan so visual control can be maintained over time.

---

## PA-01 — Product Principles

### Question

What principles should guide product decisions when there is a trade-off between two valid options?

### Answer

Schemaflow’s product decisions should be guided by lifecycle-aware principles. The product should not optimize for the same thing at every stage of the user journey.

In acquisition, Schemaflow should prioritize immediate clarity: it should reveal the user’s real UI kit, expose drift, and make the current state of the product visible fast.

In retention, Schemaflow should prioritize governance: it should help users define what is official, correct what has drifted, and maintain reusable AI-actionable context over time.

Across both stages, Schemaflow should not hide complexity in the name of simplicity. The goal is not to simplify the product’s reality away. The goal is to expose the real state of the UI in a way that helps the user understand, prioritize, and act faster.

### Core Principles

1. **Lifecycle-aware product decisions**  
   Acquisition features and retention features should be judged differently. Acquisition should create fast clarity and a strong aha moment. Retention should create governance, correction, maintenance, and repeated scans.

2. **Immediate clarity in acquisition**  
   The first experience should quickly show the user something true and useful about their product: the real UI kit, visible drift, inconsistencies, and unexpected variation.

3. **Governance in retention**  
   Once the user understands the problem, the product must move from diagnosis to control: official components, valid variants, correction rules, reusable context, and repeatable governance loops.

4. **Expose complexity, but make action faster**  
   Schemaflow should not hide drift, duplicate styles, inconsistent components, or visual debt just to feel simple. It should organize complexity so the user can govern it faster.

5. **AI-actionability over manual interpretation**  
   The user should not have to manually translate findings into prompts, instructions, or rules. Schemaflow must generate actionable context for agents.

6. **User authorship over automatic enforcement**  
   Schemaflow may suggest what appears official or inconsistent, but the user should preserve authorship over design decisions. The product should restore control, not take it away.

7. **Real UI over aspirational documentation**  
   The product should start from what actually exists in screens, code, rendered UI, HTML, and CSS. Brand manuals or declared design systems can be useful references, but the real UI is the source of truth for diagnosis.

### Consolidated Answer

**Schemaflow’s product decisions should be guided by lifecycle-aware principles. In acquisition, the product should prioritize immediate clarity: reveal the user’s real UI kit, expose drift, and make the current state of the product visible fast. In retention, the product should prioritize governance: helping users define what is official, correct what has drifted, and maintain reusable AI-actionable context. Across both stages, Schemaflow should not hide complexity in the name of simplicity. It should expose the real problems in the product while making them faster to understand, prioritize, and act on. The user should not have to manually translate diagnosis into instructions; Schemaflow must generate actionable context for agents while preserving user authorship over design decisions.**

---

## PA-02 — Core Modules

### Question

What are the core modules or capabilities the product requires, and what does each one do?

### Answer

Schemaflow requires a set of core modules that together turn an existing UI into a governable, AI-actionable design system. The modules should cover ingestion, extraction, diagnosis, governance, context generation, action generation, and iteration.

### 1. UI Ingestion Module

Captures the real state of the product from URLs, screens, code, screenshots, repositories, rendered pages, or equivalent product evidence.

Its responsibility is to answer:

**What product are we analyzing, and where does the visual evidence come from?**

This module should not assume that the brand manual or declared design system is the truth. It starts from the real UI.

### 2. Real UI Kit Extraction Module

Extracts the components, styles, tokens, patterns, variants, and visual decisions that actually exist in the product.

Its responsibility is to answer:

**What UI kit actually exists in this product, even if nobody documented it explicitly?**

This module produces the first acquisition value: it shows the user something they likely do not have organized.

### 3. Drift & Consistency Analysis Module

Detects inconsistencies, accidental variants, visual duplication, deviations between components, and gaps between intended design and actual implementation.

Its responsibility is to answer:

**Where is visual coherence being lost, and how important is each deviation?**

This module should not merely say that differences exist. It should begin to organize which differences matter for product governance.

### 4. Governance & Officialization Module

Lets the user define which components, variants, styles, or patterns are official and which should be corrected, removed, deprecated, or consolidated.

Its responsibility is to answer:

**Which parts of the visual system should become the source of truth?**

This module is essential because Schemaflow should not automatically impose the correct design. It should suggest, but preserve user authorship.

### 5. Design Context Module

Turns visual decisions into structured context: usage rules, component intent, constraints, tokens, valid variants, allowed patterns, and implementation criteria.

Its responsibility is to answer:

**How should design context be organized so humans can manage it and AI agents can understand it?**

This is where Schemaflow becomes more than a scanner. It does not only detect; it structures the product’s visual knowledge.

### 6. AI-Actionable Output Module

Generates outputs that can be used by AI agents and coding tools: `design.md`, `ui-kit.md`, prompts, skills, implementation rules, correction instructions, or conceptual patches.

Its responsibility is to answer:

**How do we turn visual governance into instructions that AI can execute?**

This module reduces the user’s manual work. The user should not have to translate diagnosis into prompts from scratch.

### 7. Correction & Re-scan Loop Module

Closes the loop by supporting correction, re-scan, comparison, and verification that coherence improved.

Its responsibility is to answer:

**Did the product recover visual control after action was taken?**

This module is critical for retention because it turns Schemaflow into a recurring workflow, not a one-time report.

### 8. Design Intelligence Module

Over time, analyzes component logic and usage patterns to suggest improvements, consolidate variants, detect weak component decisions, and build a reusable component ontology.

Its responsibility is to answer:

**How can the design system improve, not only be corrected?**

This module is not necessarily part of the earliest MVP, but it represents a more defensible strategic direction once Schemaflow has structured component and usage context.

### Consolidated Answer

**Schemaflow’s core modules are: UI Ingestion, Real UI Kit Extraction, Drift & Consistency Analysis, Governance & Officialization, Design Context, AI-Actionable Output, Correction & Re-scan Loop, and Design Intelligence. Together, these modules transform an existing product UI into a governable design system that humans can understand and AI agents can apply. The early product depends most heavily on ingestion, extraction, drift analysis, officialization, and AI-actionable output. Design Intelligence is a later module that becomes valuable once Schemaflow has enough structured component and usage context.**

---

## PA-03 — Critical Flows

### Question

What flows must work end-to-end for the product to express its thesis — what is the critical path?

### Answer

Schemaflow’s critical path is the end-to-end loop that turns a first scan into repeated governance.

The product must let a user enter URLs, scan the product, see the real UI kit being generated, understand the problems and recommended actions, correct them with minimal friction, and return for another scan.

The core flow is not only:

**scan and diagnose**

It is:

**scan → understand → correct → maintain → re-scan**

The most important product challenge is turning the first scan into a second, third, fourth, and fifth scan. Re-scan behavior is the clearest signal that Schemaflow is becoming a governance workflow rather than a one-time diagnostic tool.

### 1. URL Intake / Product Entry

The user enters the product URLs that should be analyzed.

This entry point must be simple because it is the first acquisition moment. If this step has too much friction, the user never reaches the value.

### 2. Scan / Real UI Detection

Schemaflow scans the pages and detects real components, styles, patterns, variants, tokens, and visual signals.

The point is to show what exists, not what the user assumes exists.

### 3. Real UI Kit Generation

The product generates a representation of the real UI kit.

This should create the first aha moment:

**Now I can see the visual system my product actually has.**

### 4. Problem Understanding / Action Clarity

The user must understand what is wrong, what is duplicated, what has drifted, what is inconsistent, and which action is recommended.

Schemaflow must avoid becoming an overwhelming report. It should turn complexity into clear actions.

### 5. Correction Support

Schemaflow must make correction easier through agent instructions, prompts, `ui-kit.md`, `design.md`, rules of use, official/unofficial component decisions, or prioritized fixes.

The user should not have to manually translate the diagnosis into action.

### 6. Maintenance / Official System

After correction, the product should help maintain the system: official components, valid variants, usage rules, and the context AI should use in future iterations.

### 7. Re-scan / Governance Loop

The most critical moment is getting the user to return.

The second scan is the signal that Schemaflow was not only interesting, but useful as part of the workflow. The product should show progress, drift reduction, new issues, regressions, or changes compared with the previous scan.

### Consolidated Answer

**The critical flow for Schemaflow is: user enters product URLs → Schemaflow scans the product → generates the real UI kit → explains drift and recommended actions → helps the user correct issues through AI-actionable outputs → preserves the official system → encourages re-scan to verify improvement and maintain governance. The most important product challenge is not only producing a useful first scan, but turning that first scan into a second, third, fourth, and fifth scan. Re-scan behavior is the clearest sign that Schemaflow is becoming a governance workflow rather than a one-time diagnostic tool.**

---

## PA-04 — Core Features

### Question

What features are indispensable — without them the product cannot deliver its core value proposition?

### Answer

The core value proposition is:

**Turn an existing AI-assisted UI into a governable design system that can be corrected, maintained, and reused by AI agents.**

The indispensable features are those required to deliver that value. This is not a list of everything that may eventually be useful. If a feature can wait without breaking the core thesis, it should not be treated as indispensable.

### 1. URL-based Product Scan

The user must be able to enter one or more product URLs.

Without this, there is no simple acquisition path into the product.

### 2. Real UI Kit Extraction

Schemaflow must extract the real UI kit: components, styles, variants, colors, typography, spacing, buttons, inputs, cards, and other visual patterns.

Without this, there is no aha moment.

### 3. Drift and Inconsistency Detection

The product must detect accidental variants, visual inconsistencies, and elements that do not follow a shared visual logic.

Without this, the user does not see the governance problem.

### 4. UI Kit Visualization

The user must be able to see and understand the generated system.

It is not enough to extract data internally. The user must be able to trust what was detected.

### 5. Actionable Recommendations

Schemaflow must tell the user what to do: what to consolidate, what to correct, what to mark as official, what to remove, or what to review first.

Without action, the product is only diagnostic.

### 6. Official / Unofficial Component Decisioning

The user must be able to define what is official and what is not.

This feature is essential because governance requires human authorship, not only automatic inference.

### 7. AI-actionable Export

Schemaflow must generate a usable output for coding agents from the MVP.

In the first version, this can start as copyable prompts, correction instructions, `ui-kit.md`, or `design.md`. Over time, it can evolve into structured skills, rules, repo files, agent memory, or deeper integrations.

This feature is indispensable because the user should not have to manually translate diagnosis into instructions.

### 8. Re-scan / Comparison

The user must be able to scan again and see whether the product improved or whether new drift appeared.

Without this, Schemaflow remains a one-time diagnostic tool rather than a governance loop.

### Non-core Initial Features

The following may become valuable later, but are not indispensable for the first core product loop:

- advanced collaboration,
- team workflows,
- sophisticated history,
- multi-project management,
- deep GitHub/Figma/Linear integrations,
- component marketplaces,
- advanced design recommendations,
- comparative scoring across products,
- automatic continuous monitoring,
- and broad design intelligence.

### Consolidated Answer

**The indispensable features are: URL-based product scan, real UI kit extraction, drift and inconsistency detection, UI kit visualization, actionable recommendations, official/unofficial component decisioning, AI-actionable export, and re-scan/comparison. The AI-actionable export must exist from the MVP, even if it starts as simple copyable prompts, `ui-kit.md`, `design.md`, or correction instructions. Without these features, Schemaflow cannot deliver its core value proposition: helping builders turn an existing AI-assisted UI into a governable design system that can be corrected, maintained, and reused by AI agents.**

---

## PA-05 — Product Constraints

### Question

What are the hard constraints — rules that cannot be broken without compromising the product's integrity or trust?

### Answer

Schemaflow’s hard constraints are trust constraints.

The product must accurately map the real UI, avoid hallucinating components or styles, distinguish observed facts from inferred interpretations, protect product access and credentials, and always make diagnosis actionable.

If users cannot trust what Schemaflow sees, what it infers, or how it handles access to their product, the governance thesis breaks.

### 1. Map the Real UI Comprehensively Enough to Preserve Trust

Schemaflow must detect the styles, components, and variants that are actually being used.

If there are seven button styles in the product and Schemaflow only maps two, the user will lose trust. The experience can organize and prioritize findings to avoid overwhelming the user, but it cannot hide important omissions.

### 2. Never Hallucinate Components, Styles, or Usage Patterns

The product must not invent components that do not exist, variants that are not used, or patterns that are not present in the real UI.

Schemaflow may infer groupings or suggest consolidations, but it must clearly distinguish between:

- **observed**
- **inferred**
- **recommended**

### 3. Separate Observed Facts from Product Interpretation

The UX should clearly show what was directly observed and what the system is interpreting.

For example:

- “These 7 button styles were detected” is an observed fact.
- “This appears to be the official primary button” is an inference.
- “We recommend consolidating these 3 variants” is a recommendation.

### 4. Do Not Simplify by Hiding Real Complexity

Schemaflow can summarize, group, and prioritize, but it must not distort reality so the product looks simpler than it is.

If there is a lot of drift, the product should show it in a navigable way. The promise is not to make disorder look ordered. The promise is to make disorder governable.

### 5. Protect Access and Credentials as a First-class Trust Layer

If the product needs to enter private pages, dashboards, or authenticated flows, credential handling must be treated as a core product concern, not a technical detail.

The user should ideally be able to create an additional or test account for Schemaflow, provide credentials through a secure mechanism, use temporary sessions, or rely on a trusted local/desktop flow.

The product should never feel like a random form asking the user to paste sensitive credentials.

### 6. Minimize Sensitive Access Whenever Possible

Schemaflow should request the least access necessary to perform the scan.

If a public page is enough, it should not require credentials. If login is required, Schemaflow should explain why, what it will access, what it will not touch, and how the session or credentials are protected.

### 7. Never Produce Diagnosis Without an Actionable Path

Showing problems without telling the user what to do increases anxiety and work.

Every important finding should offer a next step: officialize, consolidate, ignore, export to agent, generate a rule, generate a fix, or mark for review.

### 8. Never Make Governance Slower Than Manual Correction

If using Schemaflow takes more time than correcting manually in Cursor, Claude, Figma, or code, it loses its reason to exist.

Schemaflow can expose complexity, but it must reduce the time needed to decide and act.

### Consolidated Answer

**Schemaflow’s hard constraints are trust constraints. The product must accurately map the real UI, avoid hallucinating components or styles, distinguish observed facts from inferred interpretations, and protect product access and credentials. If the user sees seven button styles in their product but Schemaflow only detects two, trust breaks. If Schemaflow invents components that do not exist, trust breaks. The product may organize, group, and prioritize complexity, but it must not hide or fabricate the real state of the UI. Because Schemaflow may need access to authenticated product areas, credential handling must be treated as a first-class product concern: access should be minimal, secure, explainable, and preferably handled through test accounts, temporary sessions, environment-style configuration, or another trusted mechanism. Every diagnosis must also lead to an actionable next step, otherwise Schemaflow adds work instead of restoring control.**

---

## PA-06 — Dependencies

### Question

What dependencies exist between modules, features, data, or external systems that affect build sequence?

### Answer

Schemaflow’s build sequence is constrained by a simple dependency chain:

**It cannot govern what it cannot accurately see. It cannot generate useful actions from a weak diagnosis. It cannot create retention without a re-scan loop.**

The most important dependency is the site access model.

Before Schemaflow can reliably extract the real UI kit, it must decide how it will access rendered product pages, HTML, CSS, and relevant authenticated states. This decision affects scan quality, user trust, security, and usability.

### Key Architectural Dependency: Site Access Model

Schemaflow must decide how it enters the user’s site, navigates pages, reads HTML/CSS, captures rendered UI state, and handles authenticated areas.

This is not only a technical dependency. It determines:

- the product’s trust model,
- user experience,
- security posture,
- scan quality,
- product coverage,
- and roadmap sequencing.

### Option A — Server-side Scanner

Schemaflow runs the scan from a server. The user enters URLs and the system processes them in the background.

**Pros**

- Simple experience.
- Good for acquisition.
- Easier to scale.
- The user does not see technical complexity.

**Cons**

- Credential handling is more sensitive.
- Greater security burden.
- More difficulty with protected sites.
- Potential issues with authentication, sessions, bot detection, CORS, or private routes.
- Less transparency for the user.

### Option B — Browser-visible Scanning Session

Schemaflow opens a browser or scanning window where the user can see the process or authenticate directly.

**Pros**

- More transparent.
- Better for trust.
- Can handle login with the user present.
- Allows scanning of real authenticated states.

**Cons**

- More friction.
- Less magical experience.
- May feel slower or more technical.

### Option C — Desktop / Local Scanner / MCP-style Flow

Schemaflow runs locally as a desktop app or as a tool connected to the user’s local environment.

**Pros**

- Better for privacy.
- Useful for localhost and internal environments.
- Credentials are less exposed to a remote server.
- Potentially better access to repo context, local styles, and development state.

**Cons**

- Higher installation friction.
- Worse for simple acquisition.
- More complex to distribute and maintain.

### Option D — Hybrid Model

Start with public URL scanning for acquisition and later offer authenticated, visible, local, or desktop scanning for more mature use cases.

**Pros**

- Captures quick value without solving every access problem immediately.
- Separates acquisition from deep authenticated product coverage.
- Allows the product to grow toward more professional use cases.

**Cons**

- Introduces multiple product paths.
- Increases architecture and UX complexity.

### Recommended Direction

A hybrid model is likely the healthiest roadmap direction.

For acquisition, the user should be able to enter a public URL and receive a quick first scan.

For more serious products, where dashboards, logged-in states, internal screens, or user-specific states matter, Schemaflow will need a higher-trust mode: visible browser session, test account, temporary session, secure credential vault, desktop/local scanner, or MCP-style flow.

### Dependency Chain

1. **Site access model → blocks scan quality and coverage**  
   Without a clear access model, Schemaflow cannot reliably extract HTML, CSS, or rendered UI state.

2. **Authenticated access → blocks mature-product use cases**  
   If Schemaflow only scans public pages, it can support acquisition but may fail on real products where important UI lives behind login.

3. **HTML/CSS/rendered-state extraction → blocks real UI kit generation**  
   Once Schemaflow can enter the site and read rendered UI, downstream modules become much more viable.

4. **Scan quality → blocks trust**  
   If the scan misses obvious styles or components, the user will not trust the diagnosis.

5. **Real UI kit extraction → blocks drift diagnosis**  
   Drift cannot be diagnosed reliably without a representation of the real UI kit.

6. **Drift analysis → blocks meaningful recommendations**  
   Recommendations depend on knowing what is inconsistent, duplicated, accidental, or legitimate.

7. **Officialization → blocks true governance**  
   Without user-defined official components, Schemaflow can diagnose but cannot build a reliable source of truth.

8. **Design context → blocks AI-actionable export**  
   Agent instructions require structured context: what is official, what to avoid, what to correct, and how components should be used.

9. **AI-actionable export → blocks correction behavior**  
   If users must translate findings manually, correction becomes less likely.

10. **Correction behavior → blocks re-scan value**  
   Re-scan only matters if the user has made changes.

11. **Re-scan history → blocks governance over time**  
   Long-term governance requires previous states, comparisons, drift history, and official decisions.

### Consolidated Answer

**The most important dependency in Schemaflow is the site access model. The product cannot extract a reliable real UI kit unless it can access the user’s rendered product pages, HTML, CSS, and relevant authenticated states. This access model may take several forms: a server-side scanner for simple public URLs, a browser-visible session where the user can authenticate and observe the scan, a desktop/local scanner or MCP-style flow for higher-trust environments, or a hybrid model that separates acquisition from deeper authenticated scanning. This decision affects the entire build sequence because scan quality depends on access, full product coverage depends on authentication, and user adoption depends on whether credential handling feels secure and explainable. Once Schemaflow can reliably enter the site and extract HTML/CSS/rendered UI state, the downstream modules — real UI kit extraction, drift diagnosis, officialization, AI-actionable export, and re-scan — become much more straightforward.**

---

## PA-07 — Risks

### Question

What are the top risks that could prevent the product from working as intended — technically, in adoption, or in design?

### Answer

Schemaflow’s main risks are not only market risks. They are trust, access, scan quality, workflow, and positioning risks.

If the product fails to see the UI accurately, fails to make findings actionable, or fails to turn the first scan into repeated scans, the product will not express its thesis.

### 1. Scan Trust Risk

**Risk:** Schemaflow fails to map the real UI with enough coverage.

If the user sees seven button styles in their product but Schemaflow only detects two, trust breaks. The user will assume the product is unreliable, even if the rest of the experience is well designed.

**Failure mechanism:** incomplete detection → user notices missing styles/components → diagnosis loses credibility → user does not act or return.

### 2. Hallucination Risk

**Risk:** Schemaflow invents components, variants, styles, or usage patterns that do not exist.

This is especially dangerous because the product’s authority depends on showing the real state of the UI. If it fabricates patterns, it becomes worse than useless: it creates false governance.

**Failure mechanism:** hallucinated component → user sees mismatch with real product → confidence collapses → generated instructions become suspect.

### 3. Site Access and Credential Risk

**Risk:** The product cannot access the right parts of the user’s product safely and comfortably.

If it only scans public URLs, it may miss the real product surface: dashboards, logged-in states, account settings, admin flows, or product areas where most components live. But if it asks for credentials in a way that feels unsafe, users will not trust it.

**Failure mechanism:** poor access model → partial scan or credential anxiety → incomplete UI kit or user drop-off → weak aha moment.

### 4. First Scan Dead-end Risk

**Risk:** The first scan is interesting but does not lead to action.

The user may think “this is cool” but not know what to do next. If the report adds cognitive load instead of reducing work, Schemaflow becomes a diagnostic curiosity, not a governance tool.

**Failure mechanism:** scan produces report → user sees problems → no clear action path → no correction → no second scan.

### 5. Re-scan Failure Risk

**Risk:** The product does not create a strong reason to return.

The critical retention signal is not the first scan. It is the second, third, fourth, and fifth scan. If users do not re-scan after correcting or changing their product, Schemaflow fails to become part of the workflow.

**Failure mechanism:** first scan creates aha → user does not correct or return → no governance loop → low retention.

### 6. Actionability Risk

**Risk:** The product detects drift but does not translate it into useful instructions for AI agents.

If the user has to manually interpret every finding and write prompts or fixes themselves, Schemaflow adds work instead of removing it.

**Failure mechanism:** diagnosis without AI-actionable export → manual translation burden → user goes back to Cursor/Claude prompts → Schemaflow becomes optional.

### 7. Overwhelm Risk

**Risk:** The product shows the full complexity of the UI but fails to organize it.

Schemaflow should not hide complexity, but if it dumps every inconsistency without hierarchy, users may feel worse, not more in control.

**Failure mechanism:** too many findings → no prioritization → user feels overwhelmed → no action.

### 8. ICP Dilution Risk

**Risk:** The product is positioned too broadly as “for anyone building with AI.”

The pain is likely real but not equally urgent for everyone. Very early-stage builders may use it for free but not pay. The paying segment is likely narrower: users with mature products, multiple products, client work, or enough design sensitivity.

**Failure mechanism:** broad ICP → many curious free users → weak paid conversion → unclear roadmap signals.

### 9. Commodity Scanner Risk

**Risk:** The product is perceived as a UI scanner rather than a governance layer.

If users understand Schemaflow as “a tool that finds UI inconsistencies,” it may be copied, commoditized, or absorbed by incumbents. The defensible position is design context, officialization, AI-actionable governance, and re-scan loops.

**Failure mechanism:** scanner positioning → low differentiation → incumbent/competitor parity → weak willingness to pay.

### 10. Native Tool Absorption Risk

**Risk:** AI coding/design tools solve the problem natively.

If Cursor, Claude, Lovable, v0, Figma, or similar platforms can reliably extract UI kits, preserve design context, and enforce consistency across iterations, a separate governance layer becomes less necessary.

**Failure mechanism:** incumbents integrate visual governance → standalone workflow loses urgency → Schemaflow must reposition or integrate.

### Consolidated Answer

**Schemaflow’s top risks are: incomplete scan coverage, hallucinated UI elements, unsafe or uncomfortable site access, first scans that do not lead to action, failure to create re-scan behavior, weak AI-actionable outputs, overwhelming diagnosis, overly broad ICP, commodity scanner positioning, and native absorption by AI coding/design tools. The most dangerous risks are trust-related: if Schemaflow cannot accurately see the real UI, clearly separate observed facts from inference, and safely access authenticated product areas, users will not trust the governance layer built on top of it. The most important adoption risk is that users find the first scan interesting but do not correct issues or return for a second scan.**

---

## PA-08 — Open Questions / Unknowns

### Question

What important product architecture questions remain unresolved and must be answered through discovery, prototyping, or early usage?

### Answer

Schemaflow still has several unresolved product architecture questions. Most of them are not purely technical. They sit at the intersection of product strategy, UX, trust, security, and workflow design.

### 1. What is the right site access model?

The most important open question is how Schemaflow enters the user’s product to inspect HTML, CSS, and rendered visual state.

Open options include:

- server-side scanner for public URLs,
- browser-visible scan where the user can observe or authenticate,
- desktop/local scanner or MCP-style flow,
- hybrid model with simple public acquisition and advanced authenticated scanning.

This decision affects security, trust, scan coverage, UX, and acquisition speed.

### 2. How much scan completeness is enough to preserve trust?

Schemaflow does not need to be perfect from day one, but it must be complete enough for the user to trust it.

The key question is:

**What level of coverage makes the user feel that Schemaflow is truly seeing their product?**

If it misses obvious components, trust breaks. If it shows too much without structure, the user gets overwhelmed.

### 3. How should the product separate observed facts, inference, and recommendations?

The product must distinguish between what it saw, what it inferred, and what it recommends.

- **Observed:** elements directly detected in the UI/code.
- **Inferred:** patterns or hierarchy the system deduces.
- **Recommended:** actions suggested to correct or consolidate.

The open question is how to make this distinction clear without making the UX feel heavy.

### 4. What makes a user run a second scan?

This is probably the most important retention question.

A first scan may create curiosity. But the product only becomes a workflow if the user returns.

The key question is:

**What trigger turns the first scan into the second, third, and fourth scan?**

Possible triggers include improvement comparison, drift reduction, history, new pages, recent changes, agent export, or post-deploy monitoring.

### 5. What should be the first AI-actionable output?

AI-actionable output is core, but the first format remains open.

Options include:

- copyable prompts,
- `ui-kit.md`,
- `design.md`,
- rules files,
- agent skills,
- prioritized correction instructions,
- component-specific implementation guidance.

The decision should be based on which output reduces the most manual work and increases the probability that the user corrects the drift.

### 6. Where is the first monetizable ICP?

Schemaflow may be useful for many builders, but not all of them will pay.

The key question is:

**Who feels that paying for visual governance is cheaper than correcting manually?**

Likely candidates include freelancers, small agencies, builders with several products, already-monetized products, teams with brand-sensitive interfaces, and founders with real B2B or client-facing products.

### 7. What belongs in free vs. paid?

The free tier should let users experience the magic, but not capture all the value.

The key question is:

**What limit separates exploration from real governance?**

Possible limits include:

- number of URLs,
- pages,
- scans,
- projects,
- history,
- exports,
- re-scan comparison,
- authenticated scans,
- generated files,
- persistent rules,
- or agent-actionable outputs.

### 8. How much should Schemaflow correct vs. govern?

There is a strategic tension between correction and governance.

Open questions:

- Should Schemaflow correct directly?
- Should it generate instructions for agents to correct?
- Should it only govern and preserve context?
- Should it eventually integrate with the repo?

The thesis points to governance, but users may value fast correction. The product needs to find the right balance.

### 9. How does Schemaflow avoid becoming a commodity scanner?

The strategic question is:

**What makes Schemaflow a governance layer and not just a visual report?**

The answer likely lives in officialization, design context, AI-actionable files, re-scan loops, history, component ontology, and usage intelligence.

### 10. What is the minimum viable governance loop?

Before building a complete platform, Schemaflow must define the smallest end-to-end loop that validates the thesis.

The likely loop is:

**URL → scan → real UI kit → drift → action → export → correction → re-scan**

The open question is what version of that loop is enough to create value, trust, and repeated usage.

### Consolidated Answer

**The main open questions for Schemaflow are: what site access model creates the right balance between trust, coverage, and ease of use; what level of scan completeness is required to preserve confidence; how the UX should separate observed facts from inference and recommendations; what makes users run a second scan; what AI-actionable output should ship first; which ICP is most likely to pay; what belongs in free vs. paid; how much the product should correct directly versus govern through agent instructions; and how Schemaflow avoids being perceived as a commodity scanner. The most important unresolved question is the minimum viable governance loop: what is the smallest end-to-end experience that lets users scan a real product, understand drift, act on it, and return to verify improvement?**

---

## Summary

Schemaflow’s product architecture should serve one strategic idea:

**AI-assisted development creates a new governance problem. Schemaflow turns the real UI of a product into a governable system that humans can control and AI agents can apply.**

The product architecture should therefore prioritize:

- real UI extraction,
- scan trust,
- visual drift diagnosis,
- official component decisions,
- AI-actionable outputs,
- secure site access,
- and repeated scans.

The first product loop should not attempt to become a full design platform. It should prove that users can enter URLs, scan their product, see their real UI kit, understand drift, take action, and return to scan again.

The strongest architectural concern is the site access model: how Schemaflow enters the user’s product, reads rendered UI, handles authenticated states, and protects trust.

The strongest adoption concern is re-scan behavior. If users do not return after the first scan, Schemaflow remains a diagnostic curiosity. If they return repeatedly, it begins to operate as a true governance layer.

The strongest strategic concern is differentiation. If Schemaflow is perceived as a scanner, it risks becoming a commodity feature. If it owns the workflow around design context, officialization, agent-actionable governance, and repeated correction, it can become a durable product layer for AI-assisted product development.
