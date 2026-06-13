---
name: cloud-operating-model
description: >-
  Describe, design, compare, score, and recommend cloud operating models for a corporate
  environment, and produce a phased transition roadmap to move from the current model to a target
  one. Use this whenever the user talks about cloud operating models, target operating models (TOM),
  cloud ops models, CCoE / Cloud Center of Excellence, platform engineering vs centralized vs
  federated vs decentralized cloud teams, "who should run our cloud," cloud org design, landing-zone
  governance ownership, RACI for cloud, or how to transition/restructure cloud operations — even if
  they don't use the exact phrase "operating model." Also trigger when someone asks to compare
  centralized vs federated cloud teams, pick a model, or build a roadmap for reorganizing cloud
  responsibilities.
---

# Cloud Operating Model Advisor

Help corporate teams **describe, design, compare, recommend, and transition between cloud operating
models** — the way an organization structures its people, responsibilities, governance, and ways of
working to run cloud at scale. The flagship output is a **layered assessment document**: an
executive summary any leader can read, backed by the technical depth an architect or platform lead
needs to act on, ending in a **phased transition roadmap**.

A "cloud operating model" is not an architecture diagram and not a tooling choice. It answers: *who
owns what, who decides what, how work flows between platform and workload teams, and how governance
is enforced without becoming a bottleneck.* Keep that human-and-process lens throughout — it's easy
to drift into infrastructure detail, but the value here is org design.

## When to use which mode

The user may want the whole assessment or just one piece. Match the request:

| If they ask to… | Do this |
| --- | --- |
| **Describe / explain** a model ("what's a federated cloud model?") | Pull the archetype from `references/operating-models.md`, explain it in their context, don't force the full document. |
| **Compare** two or more models | Build a comparison matrix (see Step 3) scored against criteria; recommend if they want a steer. |
| **Recommend** a target model | Run intake (Step 1) → score candidates (Steps 2–4) → state a recommendation with rationale. |
| **Create the full assessment + roadmap** | Run the whole workflow and assemble the document from `assets/assessment-template.md`. |
| **Plan the transition** (model already chosen) | Jump to Step 5 using `references/transition-roadmap.md`. |

When in doubt, ask one or two sharp scoping questions rather than guessing — an operating-model
recommendation built on wrong assumptions about team size, regulation, or cloud maturity is worse
than no recommendation.

## Workflow

### Step 1 — Gather context (intake)

A recommendation is only as good as what you know about the organization. Before naming any model,
establish these. If the user hasn't supplied them, ask for the ones that actually change the answer
(don't interrogate — 3–5 well-chosen questions beats a 20-field form):

- **Drivers** — what's forcing the change? (speed to market, cost control, a breach/audit finding, a
  cloud migration, M&A, a re-org, "shadow IT everywhere"). The dominant driver usually points at the
  model.
- **Current state** — how is cloud run *today*? Central IT ticket queue? Each team does its own
  thing? A nascent CCoE? Name the current model honestly, even if it's "ad hoc."
- **Scale & maturity** — number of workload teams, cloud spend, in-house cloud skills, how many
  clouds (single / hybrid / multi).
- **Constraints** — regulation (financial services, healthcare, public sector), data residency,
  existing org boundaries, union/works-council factors, appetite for re-org.
- **Cloud platform(s)** — AWS, Azure, GCP, multi. This shapes which vendor framework vocabulary to
  lean on (Azure CAF, AWS CCoE / Well-Architected, GCP) — but the archetypes are vendor-neutral.
- **Goals & guardrails** — where do they want to be in 12–24 months, and what's non-negotiable
  (e.g. "central security team keeps veto on IAM").

Capture these explicitly in the document's "Context & drivers" section — a leader reading it later
needs to see the assumptions the recommendation rests on.

### Step 2 — Identify candidate models

From `references/operating-models.md`, select 2–4 archetypes worth comparing for *this*
organization. Don't list all of them mechanically — a 50-person startup doesn't need a federated
CCoE comparison, and a regulated bank won't go fully decentralized. The canonical archetypes:

- **Centralized** — one cloud team runs everything.
- **Decentralized** — each team owns its full cloud stack.
- **Federated / Hub-and-Spoke (CCoE)** — a central team sets guardrails; workload teams operate
  within them. (Azure CAF calls the modern form "Shared Management"; AWS frames the hub as a CCoE.)
- **Platform Engineering** — the central team runs an internal developer platform with self-service
  "paved roads"; the product-centric evolution of federated.

Usually include the current model and 1–2 plausible targets. Note the vendor-framework mapping so
the document speaks the language of whatever cloud they're on (`references/operating-models.md` has
the cross-walk to Azure CAF, AWS, and Gartner concepts).

### Step 3 — Compare against weighted criteria

Build a comparison matrix. Use the criteria in `references/evaluation-criteria.md` (speed/agility,
governance & risk control, cost efficiency, scalability, skills demand, security posture, innovation,
change effort). **Weight the criteria to the drivers from Step 1** — if cost is the burning platform,
cost efficiency carries more weight, and the matrix should show that. Score each model per criterion
(a simple 1–5 or High/Med/Low), make the scoring rationale visible, and total it.

The matrix is the analytical heart of the document. Don't hand-wave it — a reader should be able to
disagree with a single cell and see exactly how it moves the conclusion.

### Step 4 — Recommend a target

State a clear recommendation, not a menu. Name the target model, summarize *why it wins given their
drivers*, and — just as important — name the **trade-offs they're accepting** and what has to be
true for it to work (skills, exec sponsorship, tooling). Honesty about cons builds trust; a
recommendation with no downsides reads as a sales pitch. If a hybrid model genuinely fits (e.g.
shared management for core, decentralized for an innovation lab), say so — hybrids are common and
legitimate, not a cop-out.

### Step 5 — Build the transition roadmap

This is what makes the document actionable rather than academic. Using
`references/transition-roadmap.md`, lay out the move from current model to target as **phases**, not
a big bang. For each phase give: objective, key activities, the **RACI / ownership shifts**
(operating-model change is fundamentally about responsibility moving between teams), required
capabilities/hires/training, guardrails to stand up, quick wins to build momentum, and exit criteria
to the next phase. Surface the people risks explicitly — operating-model transitions fail on org
change far more often than on technology.

### Step 6 — Assemble the document

Build the deliverable from `assets/assessment-template.md`. It is deliberately **layered**: a tight
executive summary and recommendation up front (business-outcome framing, light jargon), then the
comparison matrix, model descriptions, and transition roadmap below for architects and platform
leads. One artifact, two reading depths — so it survives being forwarded from the CTO to the
delivery team without losing either audience.

### Step 7 (optional) — Produce a visual operating-model diagram

A one-page picture of the target model communicates to leaders what pages of prose can't. Offer it
whenever the recommendation is a federated or platform model, or whenever the user wants something
deck- or wall-friendly. To make one, **copy `assets/opmodel-diagram-template.drawio` and adapt it**
— replace every `[PLACEHOLDER]`, add/remove boxes to fit, and delete the how-to note. The template
is a three-layer structure (Customer Personas → Platform Product Model → Foundations) that suits
platform/federated models; for a simpler centralized or decentralized picture, strip it back.

`assets/platform-opmodel-example.drawio` is a complete, real worked example to reference for what
"good" looks like — and `references/platform-as-a-product.md` explains every element in it. The
output is a `.drawio` file the user opens in diagrams.net / draw.io. If they'd prefer an inline SVG
instead, the same structure can be rendered with the visualization tools when available.

## Grounding and accuracy

The archetypes and their trade-offs are stable and captured in the reference files. **Vendor
framework specifics evolve** (Azure CAF renamed several operating models in 2025; AWS guidance gets
revised). When you need current, citable vendor wording — or the user is clearly standardizing on one
cloud — verify against live sources rather than relying on memory:

- **Azure / Microsoft CAF** — use the Microsoft Learn MCP (`microsoft_docs_search` /
  `microsoft_docs_fetch`) if available.
- **AWS CCoE / Well-Architected** — use the AWS Documentation MCP (`search_documentation` /
  `read_documentation`) if available.

Attribute named frameworks (Gartner, Team Topologies, vendor models) accurately. If you're unsure
whether a specific named model or quote is current, describe the concept and flag the uncertainty
rather than inventing a citation — a fabricated Gartner quadrant name in a board document is a
credibility-killer.

## Reference files

- `references/operating-models.md` — the archetype catalog: each model's definition, how it works,
  pros/cons, when it fits, RACI shape, and the cross-walk to Azure CAF / AWS / Gartner / Team
  Topologies vocabulary. Read this for Steps 2 and the model-description sections.
- `references/evaluation-criteria.md` — the comparison dimensions, how to weight them to drivers,
  and the scoring rubric. Read this for Step 3.
- `references/transition-roadmap.md` — phasing patterns, RACI-evolution guidance, common
  sequencing, quick wins, and the failure modes of operating-model change. Read this for Step 5.
- `references/platform-as-a-product.md` — a fully worked example of the Platform Engineering model,
  with reusable techniques (persona-driven design, assisted-services maturity gradient, product
  taxonomy, product-centric squads, engagement tiers, and the tower→squad transition). Read this
  when the target is a federated or platform model, or for the org-change workstream of any
  tower-to-squad move.
- `assets/assessment-template.md` — the layered output document skeleton. Use this for Step 6.
- `assets/opmodel-diagram-template.drawio` — adaptable three-layer diagram skeleton for Step 7.
- `assets/platform-opmodel-example.drawio` — a complete worked diagram to reference as the gold
  standard.
