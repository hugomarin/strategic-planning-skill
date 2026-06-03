# Feature Definition — Schemaflow

## Purpose

This document translates Schemaflow’s product thesis, product architecture, user architecture, and objectives architecture into a concrete feature framework.

Schemaflow is not just a UI scanner. It is a progressive visual governance layer for AI-assisted product development. Its core job is to help builders recover control over their design by scanning a real product, extracting the real UI kit, revealing drift, defining what is official, generating AI-actionable outputs, and validating improvement through re-scan.

The feature architecture should therefore support one primary loop:

**scan real product → extract real UI kit → reveal drift → define official system → generate AI-actionable outputs → correct → re-scan → verify improvement**

At the current stage, Schemaflow is validating the value proposition, not optimizing monetization. Features should be judged by whether they help users complete the minimum governance loop and feel that they recovered control over their product’s design.

---

# 1. Product Feature Principles

## 1.1 Lifecycle-aware features

Schemaflow should not optimize every feature for the same goal.

In acquisition, features should help the user quickly understand the real state of their UI.

In activation, features should help the user identify visual drift, understand what matters, and take action.

In retention, features should help the user maintain the system, re-scan, compare improvement, and reuse design context with AI agents.

## 1.2 Governance over diagnosis

A feature is more valuable when it helps the user govern the product, not merely inspect it.

A scanner tells the user what exists. A governance layer helps the user decide what should exist, what should be corrected, and how future AI-generated work should preserve those decisions.

## 1.3 Actionability over reporting

Every important finding should lead to a clear action: officialize, consolidate, ignore, export, correct, re-scan, or generate agent instructions.

Reports that do not produce action increase cognitive load.

## 1.4 Real UI over declared intent

Schemaflow should begin from the UI that actually exists in the product: rendered screens, HTML, CSS, components, styles, variants, and visual behavior.

Brand manuals, Figma files, or intended design systems can be references, but the first source of truth is the product’s real UI.

## 1.5 User authorship over automatic enforcement

Schemaflow can infer and recommend, but the user should preserve control over final design decisions.

The product should distinguish between:

- observed facts,
- inferred patterns,
- recommended actions,
- and user-confirmed official decisions.

## 1.6 Trust as a feature constraint

The product must not hallucinate components, invent styles, or hide important inconsistencies.

If the user sees seven button styles and Schemaflow detects only two, trust breaks. If Schemaflow invents components that do not exist, trust breaks. Scan quality and evidence transparency are foundational features, not technical details.

---

# 2. Feature Stages

The feature roadmap should be framed as validation stages, not as a fixed roadmap.

## Stage 0 — Design Partner Enablement

Goal: recruit 5–10 relevant design partners and make it easy to test Schemaflow with a real product surface.

## Stage 1 — Value Proposition / Activation

Goal: prove that users can recover control over their design by scanning, understanding drift, acting, and seeing improvement in a second scan.

## Stage 2 — Retention / Governance Behavior

Goal: prove that users return to Schemaflow as part of their product workflow, not as a one-time diagnostic.

## Stage 3 — Usage Economics

Goal: measure the cost of scans, re-scans, exports, authenticated access, AI analysis, and activated governance loops.

## Stage 4 — Monetization Hypothesis

Goal: test which segment sees enough ROI to pay and which product limits create upgrade intent.

---

# 3. Core Feature Set

## Feature 1 — Product URL Intake

### Description

Allows the user to enter one or more product URLs to start a scan.

### User value

The user can quickly test Schemaflow on a real product without complex setup.

### Why it matters

This is the acquisition entry point. If it is too hard to start, users never reach the aha moment.

### MVP scope

- URL input.
- Basic validation.
- Multiple URL support if technically feasible.
- Clear explanation of what will be scanned.
- Scan status feedback.

### Later scope

- Bulk URL upload.
- Sitemap discovery.
- Crawl depth settings.
- Authenticated URL flows.
- Project grouping.

### Priority

**P0**

---

## Feature 2 — Public Page Scanner

### Description

Scans publicly accessible product pages and captures rendered UI state, HTML, CSS, visual styles, and relevant component evidence.

### User value

The user gets an initial scan without needing to install anything or provide credentials.

### Why it matters

This is the simplest way to validate acquisition and value proposition before solving authenticated product access.

### MVP scope

- Scan one or more public URLs.
- Capture rendered DOM.
- Extract CSS/style information.
- Capture screenshots or visual references.
- Identify visible components and style patterns.

### Later scope

- Authenticated scan.
- Browser-visible scan.
- Local/desktop scan.
- MCP-style scanner.
- Private dashboard scanning.
- Crawl session replay.

### Priority

**P0**

---

## Feature 3 — Real UI Kit Extraction

### Description

Extracts the UI kit that actually exists in the product from scanned screens and code evidence.

### User value

The user sees the real system their product is using, even if it was never documented.

### Why it matters

This is the first major aha moment: “now I can see what my product’s UI actually is.”

### MVP scope

Detect and organize:

- colors,
- typography,
- spacing patterns,
- buttons,
- inputs,
- cards,
- switches,
- navigation elements,
- layout patterns,
- repeated visual elements,
- component variants.

### Later scope

- Component ontology.
- Cross-page component clustering.
- Design token extraction.
- Variant classification.
- Usage frequency.
- Component lineage.
- Comparison against brand manual or Figma.

### Priority

**P0**

---

## Feature 4 — UI Kit Visualization

### Description

Displays the generated UI kit in a way the user can inspect, understand, and trust.

### User value

The user can see what Schemaflow detected and judge whether it reflects the real product.

### Why it matters

Extraction alone is not enough. The user must be able to inspect the generated system and believe it.

### MVP scope

- Visual inventory of components.
- Grouped styles and variants.
- Basic UI kit sections: buttons, typography, colors, spacing, components.
- Evidence links to where each element was detected.
- Clear distinction between observed and inferred information.

### Later scope

- Interactive component explorer.
- Component usage map.
- Cross-page frequency.
- Variant comparison.
- Official vs unofficial views.
- Search and filters.

### Priority

**P0**

---

## Feature 5 — Drift and Inconsistency Detection

### Description

Detects inconsistencies, accidental variants, duplicated styles, and deviations between similar UI elements.

### User value

The user understands where visual control is being lost.

### Why it matters

This feature exposes the governance problem. Without it, Schemaflow is only an inventory tool.

### MVP scope

Detect examples such as:

- multiple button styles,
- inconsistent typography,
- irregular spacing,
- duplicated component variants,
- inconsistent input styles,
- card variations,
- color drift,
- inconsistent border radius or shadows.

### Later scope

- Severity scoring.
- Visual debt score.
- Drift trends over time.
- Component-level regression detection.
- Comparison against official system.
- Page-level drift heatmap.

### Priority

**P0**

---

## Feature 6 — Action Clarity / Recommended Fixes

### Description

Turns detected drift into recommended actions.

### User value

The user knows what to do next instead of receiving a passive report.

### Why it matters

A diagnosis without an action path creates more work. Schemaflow must reduce cognitive load.

### MVP scope

For each important issue, recommend actions such as:

- consolidate variants,
- mark one version as official,
- update inconsistent styles,
- remove duplicate component styles,
- align typography,
- align spacing,
- generate agent instructions,
- ignore intentionally different elements.

### Later scope

- Prioritized fix queue.
- Impact scoring.
- Estimated effort.
- Grouped batch actions.
- “Fix with agent” flow.
- Suggested design-system refactor.

### Priority

**P0**

---

## Feature 7 — Official / Unofficial Component Decisioning

### Description

Lets the user define which components, styles, or variants are official and which are not.

### User value

The user regains authorship over the visual system.

### Why it matters

Governance requires human judgment. Schemaflow should not automatically decide the correct design without user confirmation.

### MVP scope

- Mark component or variant as official.
- Mark component or variant as unofficial / drift.
- Accept suggested official component.
- Ignore intentional differences.
- Save user decisions for the project.

### Later scope

- Approval workflow.
- Component status lifecycle.
- Official component library.
- Deprecated variants.
- Team review.
- Rules attached to official components.

### Priority

**P0**

---

## Feature 8 — AI-actionable Export

### Description

Generates outputs that AI agents and coding tools can use to correct or preserve the design system.

### User value

The user does not need to manually translate a diagnosis into prompts or rules.

### Why it matters

This is one of Schemaflow’s strongest differentiators. The product should not stop at analysis. It must generate context AI can act on.

### MVP scope

Generate one or more of:

- copyable correction prompts,
- `ui-kit.md`,
- `design.md`,
- component correction instructions,
- agent-ready rules,
- prioritized fix instructions.

### Later scope

- Cursor rules.
- Claude Code instructions.
- MCP-compatible context.
- Agent skills.
- Repo file export.
- Pull request-ready guidance.
- Auto-generated issue list.
- Integration with GitHub/Linear.

### Priority

**P0**

---

## Feature 9 — Correction Workflow

### Description

Helps the user move from diagnosis to implementation.

### User value

The user can correct drift faster, using human or AI-assisted workflows.

### Why it matters

The value proposition depends on the user being able to clean the mess, not only see it.

### MVP scope

- Export instructions.
- Copy prompt to agent.
- Show issue-by-issue correction guidance.
- Provide component-specific correction notes.
- Track whether an issue has been marked as addressed.

### Later scope

- Agent integration.
- GitHub branch / PR support.
- Linear issue generation.
- Patch suggestions.
- Auto-fix recommendations.
- Batch correction plans.

### Priority

**P0 / P1**

The MVP needs correction support, but not necessarily direct code modification.

---

## Feature 10 — Re-scan

### Description

Allows users to run another scan after making changes.

### User value

The user can verify whether the product improved.

### Why it matters

The second scan is the activation moment. Re-scan behavior is the strongest sign that Schemaflow is becoming a governance workflow.

### MVP scope

- Run second scan for same URL/project.
- Compare current scan against previous scan.
- Show whether detected drift improved, remained, or worsened.
- Highlight changed components or variants.

### Later scope

- Scan history.
- Drift trend over time.
- Release comparison.
- Scheduled scans.
- Post-deploy scans.
- Regression alerts.

### Priority

**P0**

---

## Feature 11 — Improvement Comparison

### Description

Shows users how the product changed between scans.

### User value

The user sees evidence that the mess got cleaner.

### Why it matters

The user needs visible proof that Schemaflow helped restore control.

### MVP scope

- Before/after comparison.
- Reduced inconsistency count.
- Variant consolidation count.
- Official components adopted.
- Remaining drift.
- New drift introduced.

### Later scope

- Visual diffs.
- Component-level history.
- Page-level improvement score.
- Governance score over time.
- Comparison against official UI kit.

### Priority

**P0 / P1**

This is tightly coupled with re-scan and should be present early, even if simple.

---

## Feature 12 — Scan Evidence and Trust Layer

### Description

Shows where each detected component, style, or pattern came from.

### User value

The user can verify that Schemaflow is not hallucinating or hiding important findings.

### Why it matters

Trust is a product requirement. Users must believe the scan before they act on it.

### MVP scope

- Evidence per component.
- Source URL/page.
- Screenshot or DOM reference.
- Observed vs inferred labels.
- Confidence indicators where useful.

### Later scope

- Click to inspect element source.
- DOM/CSS references.
- Cross-page evidence.
- Detection confidence.
- Explainability panel.
- Error reporting: “you missed this.”

### Priority

**P0**

---

## Feature 13 — Scan Quality Feedback

### Description

Allows users to report missing or incorrect detections.

### User value

The user can correct the system and preserve trust.

### Why it matters

Scan quality will not be perfect early. A feedback mechanism helps product learning and prevents silent trust erosion.

### MVP scope

- “This is wrong.”
- “You missed a component.”
- “This variant is intentional.”
- “This grouping is incorrect.”
- Basic feedback capture.

### Later scope

- Human review queue.
- Detection model improvement loop.
- User correction memory.
- Project-specific detection rules.
- Active learning.

### Priority

**P1**

---

## Feature 14 — Project Workspace

### Description

Groups scans, UI kit, decisions, exports, and history around a single product/project.

### User value

The user can maintain visual governance over time instead of treating every scan as isolated.

### Why it matters

Governance requires persistence.

### MVP scope

- Create project from URL.
- Save first scan.
- Save decisions.
- Save exports.
- Run re-scan in same project.

### Later scope

- Multiple projects.
- Project settings.
- Auth credentials per project.
- Team access.
- Project-level design rules.
- Workspace dashboard.

### Priority

**P1**

A lightweight project concept is useful early, but complex workspace management can wait.

---

## Feature 15 — Authenticated Scan

### Description

Allows Schemaflow to scan product areas behind login.

### User value

The user can scan real product surfaces, not only public marketing pages.

### Why it matters

Many mature products contain their most important UI behind authentication.

### MVP scope

This may not be required for the first acquisition MVP, but it is critical for mature use cases.

Possible early approaches:

- test account credentials,
- temporary session,
- browser-visible login,
- guided scanning session,
- limited authenticated flow.

### Later scope

- Secure credential vault.
- Local/desktop scanner.
- MCP-style flow.
- Session replay.
- Role-based test accounts.
- Authenticated crawl maps.

### Priority

**P1 / P0 for mature-user validation**

If design partners mostly need private product scans, this becomes P0.

---

## Feature 16 — Site Access Mode Selection

### Description

Lets Schemaflow support different access modes depending on user need and trust level.

### User value

The user can choose a scan mode that matches their product and security comfort.

### Why it matters

The site access model is one of Schemaflow’s most important architectural dependencies.

### Possible modes

- public URL scan,
- server-side scan,
- browser-visible scan,
- authenticated scan,
- local/desktop scan,
- MCP-style scan.

### MVP scope

Start with public URL scanning. Document constraints clearly.

### Later scope

Hybrid model:

- public scan for acquisition,
- browser-visible or authenticated scan for deeper use,
- local scanner for high-trust or private environments.

### Priority

**P1**

---

## Feature 17 — Usage Cost Instrumentation

### Description

Tracks the internal cost of delivering scans, analysis, exports, storage, and re-scans.

### User value

Indirect. It helps Schemaflow define sustainable pricing and limits.

### Why it matters

Pricing cannot be defined responsibly without knowing cost per scan, re-scan, page, project, and activated governance loop.

### MVP scope

Track:

- cost per scan,
- cost per page,
- processing time,
- AI analysis cost,
- storage cost,
- export generation cost,
- re-scan cost.

### Later scope

- margin dashboards,
- pricing simulation,
- free-tier cost monitoring,
- customer-level cost profile,
- usage-based limits.

### Priority

**P0 internal**

---

## Feature 18 — Free Tier Limits

### Description

Defines what users can experience for free and what requires upgrade.

### User value

The user can try the magic before paying.

### Why it matters

Schemaflow needs free usage to validate acquisition and value proposition, but should avoid giving away all governance value indefinitely.

### MVP scope

Initially, this can be manual or simple. The goal is to observe value boundaries, not optimize pricing.

Possible limits:

- number of URLs,
- number of pages,
- number of scans,
- number of re-scans,
- number of exports,
- scan history,
- authenticated scan,
- multiple projects.

### Later scope

- pricing tiers,
- paywalls,
- team plans,
- usage-based pricing,
- pro exports,
- governance history.

### Priority

**P2 initially / P1 once retention signals exist**

---

## Feature 19 — Design Context Library

### Description

Stores official decisions, rules, usage logic, and component intent in a reusable project context.

### User value

The user can maintain a design system that AI agents can reuse.

### Why it matters

This is where Schemaflow becomes more defensible than a scanner.

### MVP scope

Could begin as saved decisions and exported markdown files.

### Later scope

- component ontology,
- official component library,
- design rule memory,
- usage guidelines,
- project-specific agent context,
- versioned design context,
- reusable skills.

### Priority

**P1 / P2**

---

## Feature 20 — Design Intelligence

### Description

Uses accumulated component and usage data to recommend improvements, not just corrections.

### User value

The user can improve their design system over time.

### Why it matters

This is a longer-term defensibility layer.

### MVP scope

Not required for initial validation.

### Later scope

- component ontology,
- variant consolidation,
- weak pattern detection,
- recommendations for better component usage,
- design architecture suggestions,
- layout consistency recommendations,
- product-specific design quality insights.

### Priority

**P2**

---

# 4. MVP Feature Definition

The MVP should validate the minimum governance loop:

**URL → scan → real UI kit → drift diagnosis → action → export → correction → re-scan → visible improvement**

## MVP P0 Features

1. Product URL Intake  
2. Public Page Scanner  
3. Real UI Kit Extraction  
4. UI Kit Visualization  
5. Drift and Inconsistency Detection  
6. Action Clarity / Recommended Fixes  
7. Official / Unofficial Component Decisioning  
8. AI-actionable Export  
9. Re-scan  
10. Improvement Comparison  
11. Scan Evidence and Trust Layer  
12. Internal Usage Cost Instrumentation  

## MVP P1 Features

1. Correction Workflow  
2. Project Workspace  
3. Scan Quality Feedback  
4. Authenticated Scan, if design partners require it  
5. Site Access Mode Selection  
6. Design Context Library, lightweight version  

## Later P2 Features

1. Advanced authenticated scan modes  
2. Desktop/local/MCP scanner  
3. Team collaboration  
4. Deep GitHub/Figma/Linear integrations  
5. Scheduled scans  
6. Drift monitoring  
7. Advanced history  
8. Design Intelligence  
9. Component ontology  
10. Pricing tiers and advanced paywalls  

---

# 5. Feature Prioritization Matrix

| Feature | Stage | Priority | Main Job | Validates |
|---|---:|---:|---|---|
| Product URL Intake | Acquisition | P0 | Start scan quickly | Low-friction entry |
| Public Page Scanner | Acquisition | P0 | Capture real UI | Scan feasibility |
| Real UI Kit Extraction | Activation | P0 | Reveal actual UI system | Aha moment |
| UI Kit Visualization | Activation | P0 | Make detected system understandable | Trust and clarity |
| Drift Detection | Activation | P0 | Reveal visual governance problem | Problem recognition |
| Recommended Fixes | Activation | P0 | Tell user what to do | Actionability |
| Official/Unofficial Decisions | Activation | P0 | Restore authorship | Governance |
| AI-actionable Export | Activation | P0 | Translate diagnosis into agent context | Correction likelihood |
| Re-scan | Retention | P0 | Verify improvement | Second-scan activation |
| Improvement Comparison | Retention | P0/P1 | Show mess got cleaner | Value proof |
| Scan Evidence Layer | Trust | P0 | Prevent hallucination anxiety | Scan trust |
| Cost Instrumentation | Internal | P0 | Understand delivery cost | Pricing readiness |
| Project Workspace | Retention | P1 | Persist scans and decisions | Governance over time |
| Authenticated Scan | Expansion | P1/P0 | Scan real product surfaces | Mature-user fit |
| Design Context Library | Retention | P1/P2 | Store reusable design rules | Defensibility |
| Design Intelligence | Expansion | P2 | Improve design system | Long-term moat |

---

# 6. Key Feature Risks

## 6.1 Incomplete scan risk

If Schemaflow misses obvious styles or components, the user will not trust the product.

Mitigation: evidence layer, feedback mechanism, clear scan limitations, iterative detection improvement.

## 6.2 Hallucination risk

If Schemaflow invents components or styles, it creates false governance.

Mitigation: observed / inferred / recommended labels, source evidence, confidence indicators.

## 6.3 Dead-end report risk

If the product shows issues but does not generate action, it adds work.

Mitigation: every issue should have a next step.

## 6.4 Re-scan failure risk

If users do not return for a second scan, Schemaflow remains a curiosity.

Mitigation: emphasize correction loop, improvement comparison, and scan history.

## 6.5 Access model risk

If Schemaflow cannot scan real product surfaces or handle credentials safely, it may be limited to public pages.

Mitigation: start with public URL scans, then validate authenticated/browser-visible/local scan needs with design partners.

## 6.6 Commodity scanner risk

If Schemaflow is perceived as a scanner only, it becomes easy to copy.

Mitigation: prioritize officialization, AI-actionable context, re-scan, governance history, and design context library.

---

# 7. What Not to Build First

Schemaflow should avoid building the following too early:

- full enterprise collaboration,
- complex role/permission systems,
- design system compliance dashboards,
- marketplace of components,
- automatic full redesign,
- deep Figma/GitHub/Linear integrations before validating the loop,
- advanced design intelligence before reliable extraction,
- heavy project management,
- complex pricing before usage economics,
- broad team workflows before individual value.

These features may become useful later, but they should not distract from validating the minimum governance loop.

---

# 8. Feature Validation Questions

For each feature, the team should ask:

1. Does this help the user complete the governance loop?
2. Does this help the user recover control?
3. Does this reduce manual correction work?
4. Does this increase the chance of a second scan?
5. Does this generate reusable context for AI agents?
6. Does this improve trust in the scan?
7. Does this help us learn who the real ICP is?
8. Does this help us understand cost or pricing later?

If a feature does not support at least one of these questions, it should probably wait.

---

# 9. Summary

Schemaflow’s feature architecture should be built around the minimum governance loop:

**scan → understand → act → re-scan → verify improvement**

The first product should not try to become a full design platform. It should prove that users can scan a real product, see their real UI kit, recognize drift, decide what should be official, generate AI-actionable instructions, correct the product, and see improvement in a second scan.

The most important P0 features are:

- URL intake,
- public page scan,
- real UI kit extraction,
- UI kit visualization,
- drift detection,
- action clarity,
- official/unofficial decisions,
- AI-actionable export,
- re-scan,
- improvement comparison,
- scan evidence,
- and cost instrumentation.

The most important strategic feature is the one that converts Schemaflow from a scanner into a governance layer:

**AI-actionable design context that preserves user-authored design decisions across future AI-assisted iterations.**
