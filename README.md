# Tableau Dashboard Blueprint

**Tableau Dashboard Design Advisor | v1.1**

---

## What It Does

Tableau Dashboard Blueprint produces a complete design specification for a Tableau dashboard — the blueprint you follow when you open Tableau Desktop. Given a datasource, business questions, and a target audience, it tells you: which chart types to use, where to place them, how many filters to expose, what colors mean what, what goes in each tooltip, how the layout reshapes on smaller screens, and which Tableau containers and sizing modes to use when building it.

It's the prescriptive step between "I have data" and "I'm dragging fields onto shelves."

---

## What It Does NOT Do

**It does not build the dashboard for you.** Tableau Dashboard Blueprint produces a design spec — a document, wireframe, or in-chat specification. You still open Tableau and build it yourself. The spec reduces guesswork and rework, but the hands-on-keyboard construction is yours.

**It does not write calculated fields or LOD expressions.** It will identify *which* calculations you need (e.g., "you need a YoY % change calc") and note them in the implementation section, but it won't debug your FIXED expression or explain table calc addressing. For that, you need a dedicated calculation skill.

**It does not evaluate an existing dashboard.** If you already have a dashboard and want it scored, that's VizCritique Pro. Tableau Dashboard Blueprint is forward-looking — it designs what you haven't built yet. It doesn't look at what you've already built and tell you what's wrong.

**It does not connect to your data or query it.** It reads your datasource's *schema* (field names, types, cardinality) via the Tableau API to inform design decisions. It never queries your actual data values, runs aggregations, or profiles distributions. (Hyper Synthetic Forge does that.)

**It does not produce a functional Tableau workbook file (.twb/.twbx).** The output is a specification — text, Word document, or HTML wireframe. You translate the spec into a real workbook. The spec is designed to make that translation straightforward, but it's not a one-click deploy.

**It does not replace domain expertise.** It asks what questions the dashboard should answer, but it doesn't know your business well enough to tell you *which* questions matter. You bring the "what" and "why" — it handles the "how."

---

## What It Actually Produces

A design specification containing all of the following:

| Section | Content |
|---------|---------|
| Question → Chart Mapping | Each business question matched to a chart type, field assignments, and position on the layout |
| KPI Hierarchy | Which metrics get BAN treatment, what comparison period to use, display format |
| Layout Wireframe | ASCII grid or HTML mockup showing exact spatial arrangement with proportions |
| Filter Strategy | Which filters, what type (dropdown, radio, search), where placed, default values, scope |
| Interaction Model | Dashboard actions (filter, highlight, navigate), what's clickable, what happens |
| Tooltip Design | Content per chart — which fields, in what order, viz-in-tooltip yes/no, action cues |
| Color System | Full palette with hex codes, semantic assignments, categorical set, accessibility notes |
| Typography | Font, size, weight for every text level (title, subtitle, chart headers, labels, KPIs) |
| Responsive Behavior | What changes at each breakpoint — what compresses, what drops, how filters collapse |
| Tableau Implementation Notes | Container strategy, sizing mode, device layouts, context filters, performance guidance |
| Pre-Score Estimate | Projected VizCritique Pro score with rationale per domain and the key execution risk |

---

## Required & Companion Skills

Tableau Dashboard Blueprint is designed to work standalone or as part of a skill suite. Here's what's required, what's recommended, and what's optional:

| Skill | Relationship | Why |
|-------|-------------|-----|
| **Tableau MCP** (connector) | **Required** | Tableau Dashboard Blueprint reads datasource schemas via `get-datasource-metadata`. Without it, you can still use the skill by describing your data verbally — but live schema analysis won't work. |
| **VizCritique Pro** | **Recommended** | Tableau Dashboard Blueprint pre-calibrates every design decision against VizCritique's scoring domains. After you build, VizCritique evaluates the result. Using both creates a design→build→evaluate loop. Without it, Tableau Dashboard Blueprint still works — you just lose the post-build scoring step. |
| **Hyper Synthetic Forge** | **Optional** | If you need realistic test data before building, Forge generates it and Tableau Dashboard Blueprint can reference the Forge schema directly. Unnecessary if you already have production data. |
| **Word Document skill (docx)** | **Optional** | Only needed if you want the design spec delivered as a formatted .docx file. Text-on-screen and HTML wireframe outputs don't require it. |

**Minimum viable setup:** Tableau MCP connected + Tableau Dashboard Blueprint installed. Everything else adds value but isn't blocking.

**Full suite for maximum workflow coverage:**
```
Hyper Synthetic Forge → Tableau Dashboard Blueprint → Build in Tableau → VizCritique Pro
(generate data)         (design what to build)        (you build it)     (evaluate result)
```

Each handoff is clean — Forge's schema feeds directly into Tableau Dashboard Blueprint's analysis, and the design spec is pre-calibrated to score well under VizCritique's framework. VizCritique then evaluates the result against the same principles Tableau Dashboard Blueprint used to design it.

---

## What's NOT in This Skill (and Where to Find It)

| Capability You Might Need | Where It Lives | Why It's Separate |
|---|---|---|
| Writing LOD expressions, table calcs, or complex formulas | Not yet built (Tableau Calc Lab — planned) | Calculation authoring is a deep domain that requires debugging, explaining addressing/partitioning, and formula validation |
| Generating synthetic test data | Hyper Synthetic Forge | Data generation requires statistical profiling, calibration algorithms, and export logic — different problem space |
| Scoring/evaluating a finished dashboard | VizCritique Pro | Evaluation requires image analysis, evidence-based scoring, and a different cognitive mode than prescriptive design |
| Building the actual .twb/.twbx file | You + Tableau Desktop | Programmatic workbook generation is fragile and version-dependent; a spec you translate manually is more reliable and educational |
| Querying data values or running aggregations | Tableau MCP (`query-datasource`) | Tableau Dashboard Blueprint reads schema only — it doesn't need to know your actual Sales numbers to tell you "put Sales on the Y-axis as a line chart" |

---

## How to Trigger

Say any of:
- "Tableau Dashboard Blueprint"
- "Help me design a dashboard"
- "What should I build with this data?"
- "Recommend a layout"
- "Wireframe this"
- "What charts should I use for..."
- "I have [data], now what?"

---

## What It Needs From You

Three inputs — all required before design begins:

1. **Data schema** — A Tableau datasource (name or LUID), a list of fields and types, or even a general description ("sales data with orders, dates, regions, products"). More specificity produces a better spec.

2. **Business questions** — What should the dashboard answer? 2-5 specific questions is ideal. A single high-level objective works too ("monitor regional performance"). If you don't know what to ask, Tableau Dashboard Blueprint will suggest questions based on your field types.

3. **Target audience** — Who uses this and how? "VP of Sales, 30 seconds, Monday mornings" is perfect. Just "executive" or "analyst" works too. This drives every downstream decision: chart complexity, filter count, interaction model, tooltip depth.

---

## Workflow (10 Phases)

| Phase | What Happens |
|-------|--------------|
| 1. Intake & Requirements | Gathers inputs. Applies question prioritization (P1 decision-critical → P4 reference). Locks in audience constraints. |
| 2. Datasource Analysis | Classifies fields. Detects schema gaps. Maps questions to field combinations. |
| 3. Chart Selection | Question pattern → optimal chart type with conditional alternatives. Anti-pattern prevention. |
| 4. Layout Architecture | Grid zones, title strategy, responsive breakpoints, multi-page architecture if needed. |
| 5. Filter & Interaction Strategy | Filter types by cardinality and audience. Actions. Tooltip content per chart. |
| 6. Color System | Full palette with hex codes, semantic assignments, accessibility compliance. |
| 7. KPI & Metric Hierarchy | Primary/secondary identification, comparison periods, BAN format. |
| 8. Design Spec Output | Complete specification as text, Word document, or HTML wireframe. |
| 9. Tableau Implementation Guide | Containers, sizing, device layouts, filter patterns, performance notes. |
| 10. Pre-Score Estimate | Projected VizCritique Pro score with execution risk identification. |

---

## Audience Profiles

Every design decision cascades from the audience tier:

| Audience | Time Budget | Max Filters | Max Charts | Tooltip Depth | Interaction |
|----------|------------|-------------|------------|---------------|-------------|
| Executive | 5-30 sec | 0-2 | 4-6 | 2-3 lines | Scan-only |
| Manager | 1-3 min | 2-4 | 5-8 | 3-5 lines | Light filtering |
| Analyst | 3-15 min | 4-8 | 6-12 | 5-8 lines + viz | Heavy cross-filtering |
| Operations | 5-30 sec | 1-2 | 3-5 | 2-3 lines | Alert-driven |
| External | 30-90 sec | 0-1 | 3-5 | 2-3 lines | Minimal |

These aren't suggestions — they're enforced constraints. The skill will push back if your request exceeds what your audience can absorb.

---

## Output Formats

| Format | What You Get |
|--------|--------------|
| **Text on screen** | Full 9-section spec in-chat with ASCII wireframe |
| **Word document (.docx)** | Formatted document with layout diagrams, color swatches, and implementation notes |
| **HTML wireframe** | Visual blueprint showing labeled zones, proportions, and component relationships |

---

## Use Cases

**Greenfield design** — You have data and questions but no dashboard. Tableau Dashboard Blueprint gives you the blueprint so you build right the first time.

**Redesign** — Something's not working about your current dashboard. Describe the problems and Tableau Dashboard Blueprint designs a replacement architecture.

**Team standardization** — Use specs as shared references for how each audience tier's dashboards should be structured.

**Stakeholder alignment** — Generate a wireframe or Word doc to get design approval before investing build time. Reduces "that's not what I wanted."

**Responsive planning** — Targeting multiple devices? The breakpoint table tells you exactly what to build in each Tableau Device Layout.

**Pre-validation** — The pre-score estimate flags execution risks before you've committed time. Know where you'll score before you start.

---

## Design Principles

1. **Audience first, always.** Every decision serves the target viewer's time budget and decision context.
2. **Fewer things, done well.** Four clear charts beat twelve competing for attention.
3. **Show the answer, not the data.** Charts answer questions — they don't display fields.
4. **Interaction is earned.** Every filter justifies its existence for the specific audience.
5. **Consistency builds trust.** Colors, fonts, spacing are internally coherent.
6. **Optimize for the realistic case.** Design for how people actually use dashboards: scan, decide, leave.
7. **No decoration without function.** Every visual element earns its ink.
