# Worked Example: Platform-as-a-Product Operating Model

A concrete, fully-developed example of the **Platform Engineering** archetype (the right-hand end of
the spectrum in `operating-models.md`). Use it as a pattern library when an organization is heading
toward — or already running — a product-centric platform. The bundled diagram
`assets/platform-opmodel-example.drawio` renders this model visually; copy and adapt
`assets/opmodel-diagram-template.drawio` to produce one for a specific organization.

This isn't a model to recommend by default — it's the destination for organizations with the scale
and engineering maturity to justify an internal platform. Lift the *techniques* below into any
federated or platform assessment, even when the full model is overkill.

## The structure: three layers

A clean way to render a platform operating model is as three layers, left to right:

1. **Customer personas** — who the platform serves.
2. **Platform product model** — what the platform offers and how it's organized to deliver it.
3. **Foundations** — the existing core (network, identity, landing zone, security) the platform
   sits on, plus any legacy estate transitioning in.

This layering is itself a useful communication device: it shows leaders that the platform is built
*for customers*, *on existing foundations*, rather than as technology for its own sake.

## Technique 1 — Persona-driven platform design

Design platform products around customer segments, where each segment is defined by **workload
archetype × cloud maturity**, with an explicit statement of what they *want*. Example personas:

| Persona | Workload archetype | Cloud maturity | Wants |
| --- | --- | --- | --- |
| Enterprise App Team | Stateful IaaS (lift-and-shift, traditional DB/middleware) | Low | Managed VM + storage, patching, backup, DR |
| Cloud-Native Developer | Containers / PaaS, GitOps | High | K8s namespaces, PaaS APIs, self-service |
| Data & Analytics Team | PaaS / managed data services | Medium | Self-service data services, cost-efficient at scale |
| DevOps / SRE Team | Immutable, ephemeral IaaS | High | API-driven ephemeral infra, spot/auto-scaling |
| Business / Citizen Developer | Portal / low-code | Low | Click-to-deploy, dashboards, cost visibility |

Why it matters: a platform that ignores persona maturity either over-serves high-maturity teams
(slowing them with hand-holding) or abandons low-maturity teams (who then can't adopt it). Knowing
the personas *first* tells you which products to build and how much self-service vs. assistance each
needs. This technique is valuable in **any** federated assessment, not just full platform models —
it's how you decide where the responsibility boundary sits for each customer.

## Technique 2 — Meet customers at their maturity ("Assisted Services")

Self-service is not all-or-nothing. The platform offers products along an assistance gradient:
low-maturity personas consume **managed/assisted** products (the platform does more for them);
high-maturity personas consume **API-driven self-service** (the platform gets out of their way). The
same platform serves both by varying *how much it does for the customer*, not by forking into two
platforms. Framing products as "assisted services" rather than pure self-service keeps low-maturity
teams able to adopt while still pushing everyone toward more autonomy over time.

## Technique 3 — Product taxonomy

Organize the platform's offerings as a small menu of **products**, each owned end-to-end. A typical
set:

- **Stateful IaaS** — managed VMs, persistent storage, patching/backup, OS lifecycle, DR/HA.
- **Immutable IaaS** — ephemeral compute, image pipelines, auto-scaling groups, spot, build agents.
- **Container Platform** — managed K8s, namespace-as-a-service, service mesh, registry/scanning, GitOps.
- **PaaS Services** — managed databases, serverless, messaging/queues, caching, API gateways.
- **Developer Portal** — Backstage/custom, API docs, scaffolding/CLI, plugin ecosystem, tech radar.

Sitting above the products: an **experience layer** (service catalogue, self-service portal, golden
paths/docs, cost & usage dashboards). Sitting beneath: **shared platform capabilities** every product
draws on (IaC & automation, CI/CD, observability, security & compliance, FinOps, identity & access,
service management, governance & guardrails).

## Technique 4 — Product-centric squads

Staff the platform as cross-functional **squads, one per product**, rather than as technology towers.
Each squad has a **Product Owner** plus the engineers needed to build and run that product (platform
engineers, SRE, specialist roles). This is the operational embodiment of "treat the platform as a
product" — every product has an owner accountable for its roadmap, adoption, and reliability.

**Cross-cutting roles** span the squads:
- **Head of Cloud Platform (GM)** — owns the platform's overall outcome and funding.
- **Platform Architect** — coherence across products.
- **FinOps Lead** — cost across the estate.
- **Security Champion** — security posture across products.

## Technique 5 — Graduated engagement / support model

Define how customers get help as **tiers of increasing platform involvement** — a practical mechanism
for balancing scale (self-service) with the reality that some teams need hands-on help:

- **Tier 0 — Self-Service:** portal + docs; the customer does it themselves.
- **Tier 1 — Assisted:** the product squad handles the request for the customer.
- **Tier 2 — Consultative:** architecture review / advisory engagement.
- **Tier 3 — Embedded:** a platform engineer joins the customer's team for a period.

The tiering lets the platform scale (most interactions at Tier 0) while still supporting low-maturity
or high-stakes work (Tiers 2–3). It also gives a clear answer to "how do I get help?" — which is half
of platform adoption.

## Technique 6 — Tower → product-squad transition (the org-change crux)

The hardest part of moving to this model is **what happens to the existing infrastructure towers**
(Windows, Linux, storage, network, database teams). The pattern that works: **specialists retrain and
embed into cross-functional product squads, bringing their domain expertise into the teams rather than
remaining as siloed towers.** A storage specialist becomes part of the Stateful IaaS squad; a database
specialist joins the PaaS/Data squad.

This reframes a threatening re-org ("we're disbanding your team") as a growth path ("your expertise
moves into a product squad where it has more leverage"). It directly addresses the people-risk that
kills operating-model transitions — see the failure modes in `transition-roadmap.md`. Make this
migration explicit in the roadmap: which towers map to which squads, the retraining path, and the
timeline. It is usually the make-or-break workstream.

## How to use this in an assessment

- If the recommended target is **Platform Engineering / Platform-as-a-Product**, use this structure
  for the §6 "How it works" section and generate a diagram from the template.
- If the target is **Federated/CCoE** but evolving toward platform, borrow Techniques 1, 2, and 5
  (personas, assisted services, engagement tiers) to sharpen the design without committing to a full
  IDP.
- In **any** transition involving on-prem towers, use Technique 6 as the centerpiece of the people /
  org-change workstream.
