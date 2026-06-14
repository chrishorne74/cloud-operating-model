# Architecture & Operating-Model Skills

This repo holds [Claude](https://claude.com/claude-code) **skills** (each with a matching GitHub
Copilot prompt-file edition) for senior technology-strategy work:

- **[Cloud Operating Model](#cloud-operating-model)** — describe, compare, recommend, and transition
  between cloud operating models.
- **[Enterprise Architecture Team](#enterprise-architecture-team)** — define, charter, and run an
  enterprise architecture function: responsibilities, vision, principles, standards & governance, and
  stakeholder engagement.

---

# Cloud Operating Model

A **skill** for describing, designing, comparing, scoring,
and recommending cloud operating models in a corporate environment — and producing a phased
transition roadmap to move from the current model to a target one.

The flagship output is a **layered assessment document**: an executive summary any leader can read,
backed by the technical depth an architect or platform lead needs to act on, ending in a phased
transition roadmap. Optionally, it generates a one-page visual operating-model diagram.

## What it does

- **Describe** an operating model in the organization's own context.
- **Compare** 2–4 candidate models against weighted criteria.
- **Recommend** a target model with rationale, trade-offs, and preconditions.
- **Plan the transition** as phases, with RACI/ownership shifts and exit criteria.
- **Right-size the team** — benchmark required FTE against peers (top-down ratios + bottom-up model).
- **Visualize** the target model as an adaptable draw.io diagram.

It anchors on vendor-neutral archetypes — **Centralized, Decentralized, Federated/Hub-and-Spoke
(CCoE), and Platform Engineering** — with a cross-walk to Azure CAF, AWS, and Gartner vocabulary.

## Structure

```
cloud-operating-model/
├── SKILL.md                              # workflow, mode-routing, grounding guidance
├── references/
│   ├── operating-models.md               # archetype catalog + framework cross-walk
│   ├── evaluation-criteria.md            # weighted criteria + scoring rubric
│   ├── transition-roadmap.md             # phasing, RACI evolution, failure modes
│   ├── workforce-sizing.md               # FTE benchmarking & right-sizing vs. peers
│   └── platform-as-a-product.md          # worked Platform Engineering example + techniques
└── assets/
    ├── assessment-template.md            # layered exec + technical output document
    ├── opmodel-diagram-template.drawio   # adaptable three-layer diagram skeleton
    └── platform-opmodel-example.drawio   # a complete worked diagram (gold standard)
```

## Usage

### Claude (Agent Skills)

Place the `cloud-operating-model/` folder where your Claude skills are discovered, then ask in
natural language — e.g. *"help me pick the right cloud operating model and a roadmap to get there"*
or *"compare a centralized cloud team vs a federated CCoE."* The skill auto-triggers from its
description and routes to the right depth (a quick description vs. a full assessment).

### GitHub Copilot (prompt file)

The same workflow is available to Copilot as a prompt file at
[`.github/prompts/cloud-operating-model.prompt.md`](.github/prompts/cloud-operating-model.prompt.md).
In VS Code, Visual Studio, or a JetBrains IDE with Copilot Chat, invoke it on demand with
`/cloud-operating-model`. It reuses the same `cloud-operating-model/references/*` and `assets/*`
files, so the two editions stay in sync from one source of truth.

---

# Enterprise Architecture Team

A **skill** for **establishing, articulating, and running an enterprise architecture (EA) function** —
the team that aligns technology to business strategy and sets the guardrails everyone else builds
within. It is **TOGAF-aligned but vendor-neutral**: it borrows TOGAF's structure (the ADM, the
principles template, stakeholder management) without forcing heavyweight process.

## What it does

- **Charter** the team — responsibilities, mandate & decision rights, RACI, governance, cadence.
- **Vision** — a short, outcome-led target-state statement a CIO would say out loud.
- **Principles** — an architecture principles catalog in the four-part form (name, statement,
  rationale, implications) across business, data, application, technology, and security.
- **Standards & governance** — a standards register with a lifecycle, a technology reference model /
  tech radar, the Architecture Review Board, and the exception/waiver process.
- **Stakeholder engagement** — who the stakeholders are, what each actually cares about, a
  power/interest grid, and a per-group engagement plan.

It routes to the right depth — a quick explanation, a single artifact, or the whole operating blueprint
assembled under one executive summary.

## Structure

```
enterprise-architecture-team/
├── SKILL.md                                  # workflow, mode-routing, grounding guidance
├── references/
│   ├── responsibilities-and-vision.md        # responsibility catalog, team shapes, mandate, maturity, vision
│   ├── principles-and-standards.md           # principle anatomy + quality bar, starter set, standards, ARB, exceptions
│   └── stakeholder-engagement.md             # stakeholder catalog + concerns, power/interest grid, anti-patterns
└── assets/
    ├── ea-charter-template.md                # charter skeleton (mandate, RACI, cadence, metrics)
    ├── architecture-principles-template.md   # principles catalog skeleton (four-part form)
    ├── standards-and-governance-template.md  # standards register, tech radar, ARB ToR, exception process
    └── stakeholder-engagement-template.md    # stakeholder catalog, grid, engagement plan
```

## Usage

### Claude (Agent Skills)

Place the `enterprise-architecture-team/` folder where your Claude skills are discovered, then ask in
natural language — e.g. *"help me set up our enterprise architecture team's charter and principles"* or
*"who are the stakeholders for enterprise architecture and what do they care about?"* The skill
auto-triggers from its description and routes to the right depth.

### GitHub Copilot (prompt file)

The same workflow is available to Copilot as a prompt file at
[`.github/prompts/enterprise-architecture-team.prompt.md`](.github/prompts/enterprise-architecture-team.prompt.md).
In VS Code, Visual Studio, or a JetBrains IDE with Copilot Chat, invoke it on demand with
`/enterprise-architecture-team`. It reuses the same `enterprise-architecture-team/references/*` and
`assets/*` files, so the two editions stay in sync from one source of truth.

---

## License

[MIT](LICENSE) © 2026 Chris Horne

## Grounding

Vendor and framework specifics evolve. When current, citable wording is needed, the skills verify
against live documentation sources (Microsoft Learn, AWS docs, official framework sources) where
available, and attribute named frameworks (Azure CAF, AWS, Gartner, TOGAF, Zachman, ArchiMate)
accurately. The archetype catalogs and EA reference material stand on their own without them.
