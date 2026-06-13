# Cloud Operating Model

A [Claude](https://claude.com/claude-code) **skill** for describing, designing, comparing, scoring,
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

## License

[MIT](LICENSE) © 2026 Chris Horne

## Grounding

Vendor framework specifics evolve. When current, citable vendor wording is needed, the skill
verifies against live documentation sources (Microsoft Learn, AWS docs) where available, and
attributes named frameworks accurately. The archetype catalog stands on its own without them.
