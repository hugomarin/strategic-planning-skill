# Objectives Architecture — Schemaflow

## Artifact: objectives-architecture

### Description

This artifact defines the current objectives architecture for Schemaflow. Because the product is still in a pre-ICP and value proposition validation stage, this document does not assume a finalized roadmap or monetization model.

Instead, it defines what must be validated first: whether relevant users can be recruited, whether they experience the value proposition, whether they complete the minimum governance loop, whether they return for repeated scans, and whether the product can eventually support viable pricing once usage economics are understood.

The central validation idea is:

**Schemaflow must prove that users can recover control over their design by scanning a real product, identifying visual drift, taking action, and seeing improvement in a second scan.**

---

## OA-01 — Primary Objective

### Question

What is the primary objective this product must achieve to validate the thesis?

### Answer

At this stage, Schemaflow’s primary objective is to validate the value proposition, not yet to optimize monetization.

The product must prove that users can recover control over their design by scanning a real product, identifying the actual UI elements and drift, deciding what should be official or corrected, applying changes through human or AI-assisted workflows, and seeing those changes reflected in a second scan.

The objective is not that the user completes a scan. A scan alone proves curiosity. The real objective is that the user uses the scan to recover control.

### Primary Objective

**Validate the minimum governance loop: users enter product URLs, receive a trustworthy real UI kit and drift diagnosis, understand what actions to take, use Schemaflow’s outputs to correct or guide correction, and return for a second scan to verify improvement.**

### Activation Definition

Activation is achieved when a user completes the minimum governance loop:

**first scan → identifies UI drift/components → selects or understands what should be official → applies or exports corrections → runs a second scan → sees that consistency improved**

### Core User Feeling

The product should help the user feel:

**“I found the mess, I understood it, I cleaned it up, implemented changes, and the product measurably improved.”**

### Primary Activation Metric

**Percentage of users who complete a second scan after taking a governance action.**

### Supporting Value Signals

- User identifies real UI elements in their product.
- User recognizes valid drift or inconsistency.
- User marks or accepts official/unofficial components.
- User exports instructions or rules for AI.
- User implements corrections.
- Second scan shows reduced drift or improved consistency.
- User understands that Schemaflow saved manual correction work.

### Consolidated Answer

**At this stage, Schemaflow’s primary objective is to validate the value proposition, not yet to optimize monetization. The product must prove that users can recover control over their design by scanning a real product, identifying the actual UI elements and drift, deciding what should be official or corrected, applying changes through human or AI-assisted workflows, and seeing those changes reflected in a second scan. The activation moment is not the first scan; it is the completed governance loop where the user feels: “I found the mess, cleaned it up, implemented changes, and the product measurably improved.”**

---

## OA-02 — Validation Stages / Phase Objectives

### Question

For each roadmap phase, what is the single most important thing that must be true at the end of it?

### Answer

This question should be reframed for Schemaflow’s current stage.

Schemaflow does not yet have a validated roadmap. At this stage, the product should not define phase objectives as if the roadmap were already known. Instead, the objective architecture should define validation stages.

The correction to the process is:

**Do not use “roadmap phases” before the roadmap exists. Use “validation stages” until the product has enough real learning.**

### Stage 0 — Design Partner Recruitment

**Most important thing that must be true:**  
Schemaflow can find 5–10 relevant people willing to test the product and give meaningful feedback.

This stage validates whether there is enough initial interest to recruit users into the problem space. If recruiting design partners is too difficult, that may signal that the problem is not well named, not urgent, or not positioned correctly.

**Primary question:**  
Can we get 5–10 AI-native builders or adjacent users to raise their hand and test the product?

**Signals to observe:**

- Who accepts testing.
- What profile they have.
- How difficult it is to recruit them.
- Which promise attracts them: scanner, real UI kit, governance, time savings, consistency, or AI-actionable outputs.

### Stage 1 — Value Proposition Validation

**Most important thing that must be true:**  
Users experience that Schemaflow helps them recover control over their design.

At this stage, the product is not yet validating monetization. It is validating whether users understand and experience the core value.

**Primary question:**  
Can users scan a real product, identify the mess, understand what is wrong, decide what to correct, implement changes, and see improvement in a second scan?

**Activation signal:**  
First scan → understands drift → takes action → second scan shows improvement.

### Stage 2 — Retention / Governance Behavior

**Most important thing that must be true:**  
Some users turn Schemaflow into part of their product workflow, not just a one-time diagnostic.

The second scan is activation. The third, fourth, or fifth scan begins to suggest retention.

**Primary question:**  
Do users come back when they keep building with AI and want to verify that visual consistency is being preserved?

**Signals to observe:**

- Repeat scans.
- Multiple URLs.
- More pages added.
- Exports reused.
- Corrections implemented.
- Requests for history, comparison, rules, `ui-kit.md`, `design.md`, or agent instructions.

### Stage 3 — Usage Economics / Cost Understanding

**Most important thing that must be true:**  
Schemaflow understands the cost of serving the product before defining pricing.

Before pricing, the team needs to understand operating costs: scans, crawling, HTML/CSS extraction, screenshots, AI analysis, storage, re-scans, authenticated sessions, and support.

**Primary question:**  
What does it cost to deliver a scan, a re-scan, an export, and a retained user workflow?

**Signals to observe:**

- Cost per scan.
- Cost per page.
- Cost per project.
- Cost per re-scan.
- Compute / AI cost.
- Storage cost.
- Authenticated scan complexity.
- Support cost.
- Processing time.

### Stage 4 — Monetization / Pricing Hypothesis

**Most important thing that must be true:**  
Only after value, retention, and cost are understood should Schemaflow test pricing.

At this stage, the product can begin asking what to charge, who to charge, what limit creates upgrade intent, and what packaging matches both user value and product cost.

**Primary question:**  
Which segment sees enough ROI to pay, and what pricing model matches both user value and product cost?

**Possible pricing dimensions:**

- scans,
- pages,
- projects,
- history,
- exports,
- re-scan comparison,
- authenticated scans,
- generated files,
- persistent rules,
- team usage.

### Consolidated Answer

**Schemaflow should not define roadmap phase objectives before the roadmap itself is validated. At this stage, the objective architecture should be organized around validation stages. Stage 0 is design partner recruitment: can Schemaflow find 5–10 relevant users willing to test the product and give feedback? Stage 1 is value proposition validation: can users scan a real product, identify visual drift, understand what needs to change, implement corrections, and see improvement in a second scan? Stage 2 is retention validation: do some users turn Schemaflow into part of their product workflow through repeated scans, exports, and governance behavior? Stage 3 is usage economics: what does it cost Schemaflow to deliver scans, re-scans, authenticated access, AI analysis, exports, and retained usage? Stage 4 is monetization: once value, retention, and cost are clearer, Schemaflow can test pricing and conversion. The immediate focus should remain simple: recruit design partners, validate the value proposition, observe activation, and then learn whether usage repeats before making strong monetization assumptions.**

---

## OA-03 — Key Results per Validation Stage

### Question

What are the 2–3 key results per phase that would prove the objective was achieved — stated as measurable signals with targets?

### Answer

Because Schemaflow is not yet operating against a validated roadmap, key results should be organized by validation stages rather than assumed roadmap phases.

The numbers below are initial hypotheses, not permanent targets. They exist to make learning measurable.

The dangerous failure is not adjusting the numbers later. The dangerous failure is measuring the wrong loop.

The loop to measure is:

**scan → understand → act → second scan → visible improvement**

---

### Stage 0 — Design Partner Recruitment

**Objective:** determine whether Schemaflow can recruit 5–10 relevant users willing to test the product and give feedback.

**KR-1:** Recruit **5–10 design partners** close to the learning ICP: AI-native builders, freelancers, small agencies, product engineers, design engineers, or founders with real products.

**KR-2:** At least **60% of qualified contacted users accept a demo, trial, or discovery conversation**.

**KR-3:** Identify at least **3 repeated pain patterns** among recruited users, such as visual drift, component inconsistency, loss of control, too much time correcting design, lack of a real UI kit, or need for AI-actionable outputs.

This stage does not measure the product yet. It measures whether the problem and promise attract relevant people.

---

### Stage 1 — Value Proposition / Activation

**Objective:** validate that the user recovers control over their design through the minimum governance loop.

**KR-1:** At least **70% of design partners complete a first scan** of a real product.

**KR-2:** At least **50% identify real UI problems** they recognize as valid: duplicated components, accidental variants, drift, inconsistencies, or differences from their intended visual system.

**KR-3:** At least **40% complete a governance action**: mark something as official/unofficial, export instructions, implement a correction, accept an actionable recommendation, or prepare an agent prompt.

The goal is not that users like the scan. The goal is that the scan lets them understand and act.

---

### Stage 2 — Re-scan / Retention Behavior

**Objective:** validate that Schemaflow is not a one-time diagnostic, but a governance loop.

**KR-1:** At least **30–40% of activated users run a second scan** within 7–14 days or after implementing changes.

**KR-2:** At least **50% of users who run a second scan see observable improvement**, such as fewer variants, less drift, greater consistency, or component consolidation.

**KR-3:** At least **25% of activated users run a third scan or add new URLs/pages**, signaling that Schemaflow is beginning to enter their workflow.

The second scan confirms value. The third scan begins to suggest habit.

---

### Stage 3 — Usage Economics

**Objective:** understand how much it costs to deliver value before defining pricing.

**KR-1:** Measure the **average cost per scan**, including crawling/rendering, extraction, AI analysis, storage, and processing.

**KR-2:** Measure the **average cost per activated user**, defined as a user who completes first scan + governance action + second scan.

**KR-3:** Keep the variable cost of a basic governance loop — first scan + export/action + second scan — below an internally defined threshold, for example **≤ 20–30% of a hypothetical monthly price**.

At this stage, final pricing is not required. The product only needs to know whether the unit economics are plausible.

---

### Stage 4 — Monetization Hypothesis

**Objective:** validate whether at least one segment sees enough ROI to pay.

**KR-1:** At least **20–30% of activated users express clear payment intent** when exposed to a paywall, simulated upgrade, or pricing conversation.

**KR-2:** At least **10–15% of activated users attempt to access a limited value feature**, such as more pages, more scans, history, authenticated scan, multiple projects, persistent rules, or AI-actionable exports.

**KR-3:** Identify at least **one segment with repeated ROI signals**, such as freelancers/agencies connecting Schemaflow to client delivery, or founders with mature products connecting Schemaflow to saved correction hours.

### Consolidated Answer

**Schemaflow’s key results should follow validation stages rather than an assumed roadmap. Stage 0 should prove that 5–10 relevant design partners can be recruited and that repeated pain patterns appear. Stage 1 should prove value proposition and activation: users complete a real scan, recognize valid UI problems, and take at least one governance action. Stage 2 should prove retention: activated users return for a second scan, see improvement, and some continue into a third scan or add more pages. Stage 3 should measure usage economics: cost per scan, cost per activated user, and cost per governance loop. Stage 4 should test monetization only after value and retention signals exist, using upgrade intent, paid-limit interactions, and segment-level ROI signals.**

---

## OA-04 — North Star / Core Metric

### Question

What is the single metric that best captures whether the product is delivering its core value?

### Answer

Schemaflow’s core metric should not be total scans, signups, or registered users. Those metrics may capture curiosity or acquisition, but they do not prove that the product is delivering its core value.

The best North Star candidate for this stage is:

**Completed Governance Loop Rate**

### Definition

**Completed Governance Loop = first scan → valid drift/UI kit diagnosis → governance action → second scan → visible improvement or validated control**

### Formula

**Completed Governance Loop Rate = users who complete scan → action → second scan / users who complete first scan**

### Why This Metric Matters

This metric captures the actual product thesis better than raw scan count.

It proves three things:

1. **The diagnosis was useful.**  
   The user saw valid drift, inconsistencies, or UI kit information.

2. **The user acted.**  
   The user marked components, exported instructions, accepted recommendations, or implemented changes.

3. **The user returned.**  
   The user ran a second scan to verify whether control improved.

This metric proves that the user did not merely inspect their UI. They used Schemaflow to recover control over it.

### Supporting Metrics

**Activation metric:** percentage of users who complete a first scan and recognize valid problems.

**Action metric:** percentage of users who mark official/unofficial components, export instructions, or implement corrections.

**Retention metric:** percentage of users who complete second and third scans.

**Quality metric:** reduction in drift, accidental variants, inconsistent components, or duplicated visual patterns between scans.

**Economic metric:** cost per completed governance loop.

### Consolidated Answer

**Schemaflow’s core metric should not be total scans or signups. The best North Star candidate is completed governance loops: the percentage of activated users who scan a real product, identify valid UI drift, take a governance action, and run a second scan that shows improvement or restored control. This metric best captures the product’s core value because it proves the user did not only inspect their UI; they used Schemaflow to recover control over it.**

### Stage Note

At this stage, this should be treated as an **activation North Star**, not necessarily the company’s permanent North Star. The product is still validating the value proposition.

---

## OA-05 — Validation Milestone

### Question

What specific event or data point — observable, not inferable — confirms that a given phase worked?

### Answer

Schemaflow’s validation milestones should be observable events, not inferred satisfaction.

The strongest validation event is not:

**“The user liked the scan.”**

It is:

**“The user used the scan to change the product, ran a second scan, and saw the mess get cleaner.”**

Because the product is organized around validation stages rather than fixed roadmap phases, milestones should also be stage-based.

---

### Stage 0 — Design Partner Recruitment

**Validation milestone:**  
At least **5 relevant design partners** agree to test Schemaflow with a real product surface and provide feedback.

**Observable event:**  
The design partner submits or shares a real product URL, repo, authenticated flow, screenshot set, or equivalent product surface for testing.

A friendly conversation does not count. A real product surface counts.

---

### Stage 1 — Value Proposition / Activation

**Validation milestone:**  
A user completes the first meaningful governance loop: scans a real product, sees the generated UI kit or drift diagnosis, identifies valid problems, takes at least one governance action, and prepares or applies a correction.

**Observable events include:**

- marks components as official/unofficial,
- accepts a recommendation,
- exports instructions,
- copies a prompt,
- generates `ui-kit.md` or `design.md`,
- implements at least one correction.

The stronger milestone is:

**The user completes a second scan after correction and the second scan shows observable improvement.**

---

### Stage 2 — Retention / Governance Behavior

**Validation milestone:**  
The user returns without being hand-held and runs another scan because they made product changes or want to verify consistency.

**Observable event:**  
The user initiates a second, third, or fourth scan after new UI work, new URLs, or a correction cycle.

The important event is not simply visiting again. The important event is returning to scan for a governance reason.

---

### Stage 3 — Usage Economics

**Validation milestone:**  
Schemaflow can calculate the cost of delivering the core governance loop.

**Observable data points:**

- cost per first scan,
- cost per re-scan,
- cost per activated user,
- cost per page,
- cost per export,
- processing time,
- AI analysis cost,
- storage cost,
- support / operations cost.

At this stage, the milestone is not that costs are already optimized. The milestone is that they are measurable.

---

### Stage 4 — Monetization Hypothesis

**Validation milestone:**  
At least one segment shows willingness to cross a value boundary.

**Observable events include:**

- user attempts to access a paid-limited action,
- user asks for pricing,
- user accepts a paid pilot,
- user responds positively to a simulated paywall,
- user tries to unlock more pages,
- user tries to unlock more scans,
- user tries to unlock history,
- user tries to unlock authenticated scanning,
- user tries to unlock multiple projects,
- user tries to unlock persistent rules,
- user tries to unlock AI-actionable exports.

### Consolidated Answer

**Schemaflow’s validation milestones should be observable events, not inferred satisfaction. Stage 0 works if 5–10 relevant design partners agree to test with a real product surface. Stage 1 works if users complete the first governance loop: scan a real product, identify valid UI drift, take a governance action, and ideally complete a second scan that shows improvement. Stage 2 works if users return without heavy prompting to run additional scans after new UI work or correction cycles. Stage 3 works if Schemaflow can measure the actual cost of delivering scans, re-scans, exports, and activated governance loops. Stage 4 works if at least one segment attempts to cross a paid value boundary, such as more scans, more pages, authenticated access, history, multiple projects, or AI-actionable exports.**

---

## Summary

Schemaflow’s objectives architecture should reflect the product’s current stage: value proposition validation, not monetization optimization.

The primary objective is to prove that users recover control over their design through a minimum governance loop:

**scan → understand drift → act → second scan → visible improvement**

The product should not prematurely define a roadmap or pricing model before validating design partner recruitment, activation, retention behavior, and usage economics.

The strongest activation metric is the percentage of users who complete a successful governance loop. The strongest validation milestone is a user who finds visual disorder, cleans it up, implements changes, runs a second scan, and sees improvement.

The immediate objective is simple:

**Recruit relevant design partners, prove that the governance loop creates value, and observe whether users return before making strong monetization assumptions.**
