# Cloud Operating Model Archetypes

This is the catalog of operating-model archetypes, their trade-offs, and how the major frameworks
name them. The archetypes are vendor-neutral and stable; treat the vendor names as a translation
layer so the assessment speaks the language of whatever cloud the organization is on.

## Contents
1. [The spectrum](#the-spectrum)
2. [Centralized](#centralized)
3. [Decentralized](#decentralized)
4. [Federated / Hub-and-Spoke (CCoE)](#federated--hub-and-spoke-ccoe)
5. [Platform Engineering](#platform-engineering)
6. [Hybrid models](#hybrid-models)
7. [Framework cross-walk](#framework-cross-walk)
8. [Team roles that recur across models](#team-roles-that-recur-across-models)

---

## The spectrum

Operating models sit on a spectrum from **fully central control** to **fully distributed
autonomy**. The central tension is always the same: **standardization and control vs. speed and
autonomy.** Every model is a different answer to "how much guardrail, how much freedom."

```
Centralized ───────── Federated / CCoE ───────── Platform Engineering ───────── Decentralized
(control)            (shared management)        (product-centric platform)        (autonomy)
```

Most organizations *should* move rightward over time as cloud maturity grows — but only as fast as
their skills, guardrails, and security tooling can keep up. Moving right without guardrails just
recreates shadow IT; staying left as you scale creates a bottleneck that teams route around. The
job is to find the right point on this spectrum for the organization's current maturity, with a
direction of travel.

---

## Centralized

**Definition.** A single cloud team owns governance, security, operations, and often delivery across
the entire cloud estate. Workload teams request resources and changes through this team.

**How it works.** Central team holds the cloud accounts, the landing zone, the pipelines, the IAM,
the budgets. Requests flow in (often via tickets); the central team provisions and operates.

**Pros**
- Consistent policy, security, and cost control — one throat to choke.
- Easy to enforce compliance; attractive for highly regulated or early-stage estates.
- Concentrates scarce cloud skills in one place.
- Simplest accountability model.

**Cons**
- Becomes a **bottleneck** as the number of workload teams grows — the central team's queue is
  everyone's critical path.
- Slows delivery; workload teams feel disempowered and start routing around it (shadow IT).
- Central team gets pulled into firefighting and loses time for strategic work.

**Fits when:** small organizations / startups; single-cloud estates; highly regulated industries
early in their journey; a small number of workload teams; scarce in-house cloud skills; immediately
after a breach/audit finding when control must be re-asserted.

**RACI shape:** central team is Responsible + Accountable for almost everything; workload teams are
Consulted/Informed. The defining feature is that workload teams have little Accountable scope.

---

## Decentralized

**Definition.** Each workload/product team owns its full cloud stack — provisioning, governance,
security, operations — independently, with little or no central coordination.

**How it works.** Teams have their own accounts/subscriptions and run end-to-end ("you build it, you
run it" taken to its fullest). Central function is minimal or absent.

**Pros**
- Maximum speed and autonomy; no central queue.
- Teams optimize for their own context; high ownership and innovation.
- Scales organizationally — no single bottleneck.

**Cons**
- **Weak standardization**: divergent tooling, duplicated effort, inconsistent security.
- High risk of misconfiguration, security gaps, and runaway cost — no central guardrails.
- Hard to get an enterprise-wide view of risk, spend, or compliance.
- Demands strong cloud skills *in every team* — expensive and often unrealistic.

**Fits when:** tech-savvy startups; innovation programs / R&D labs; product companies with strong
engineering culture and uniformly high cloud skills; low regulatory burden. Rarely appropriate
wholesale for a large regulated enterprise — but valid for specific innovation pockets within a
hybrid model.

**RACI shape:** each workload team is Responsible + Accountable for its own everything. No central
Accountable party — which is exactly the risk in a regulated context.

---

## Federated / Hub-and-Spoke (CCoE)

**Definition.** A central team (often a **Cloud Center of Excellence**) sets the guardrails, builds
shared foundations, and enforces baseline governance; workload teams operate **autonomously within
those guardrails.** This is the most common target model for mid-size and enterprise organizations.

**How it works.** The hub (CCoE / platform team) owns the landing zone, network, identity, baseline
security policy, and shared services, and publishes standards and reusable patterns. The spokes
(workload teams) build and run their workloads inside the guardrails — they have real autonomy, but
inside a fence the centre defines.

**Pros**
- Balances control and agility — the "have your cake and eat it" model when done well.
- Central guardrails keep security/compliance consistent; teams still move fast.
- Scales far better than centralized; the centre enables rather than gates.
- Clear separation of "platform concerns" from "workload concerns."

**Cons**
- Requires **clear responsibility boundaries** and strong coordination — ambiguity here is the main
  failure mode ("I thought the platform team owned that").
- The CCoE must be genuinely enabling, not a renamed gatekeeper; easy to slide back into
  centralized behavior.
- Needs real investment in the central team's product/automation skills.

**Fits when:** mid-size and enterprise estates; hybrid or multi-cloud; organizations scaling cloud
adoption who've outgrown centralized but can't go fully decentralized for risk reasons. This is the
default recommendation for most corporates.

**RACI shape:** central team is Accountable for the platform, guardrails, and shared services;
workload teams are Accountable for their workloads within the guardrails. The boundary between the
two is the single most important thing to document — see `transition-roadmap.md`.

**CCoE functions** (from AWS Prescriptive Guidance) typically split into:
- *Engineering functions* — landing zone, networking, identity, security baseline, automation,
  reference architectures, tooling.
- *Business functions* — governance, financial management (FinOps), training/enablement, vendor
  management, evangelism.

---

## Platform Engineering

**Definition.** The product-centric evolution of the federated model. The central team runs an
**Internal Developer Platform (IDP)** and treats it as a *product*, offering self-service "paved
roads" (golden paths) that workload teams consume on demand. Governance is embedded *into* the
platform rather than enforced by review.

**How it works.** Platform team builds self-service capabilities: subscription/account vending,
golden-path pipelines, pre-approved infrastructure modules, developer portals. Workload teams
self-serve compliant infrastructure in minutes. "Governance as code" — guardrails are baked into the
templates teams consume, so the compliant path is the easy path.

**Pros**
- Highest velocity *with* governance — the right thing is the easy thing.
- Eliminates the ticket queue; scales to many teams without growing the centre linearly.
- Strong developer experience; reduces cognitive load on workload teams.
- Governance is automated and consistent, not dependent on manual review.

**Cons**
- Significant up-front investment and mature platform-product skills required — not a starting point.
- Risk of building a platform nobody adopts ("if you build it they won't necessarily come") — needs
  genuine product management and internal adoption work.
- Over-engineering risk for smaller estates.

**Fits when:** organizations with many workload teams, strong engineering maturity, and the scale to
justify an IDP. Usually a *destination* on the roadmap rather than a first step. Maps to **Team
Topologies**: a Platform team providing services to Stream-aligned teams, with Enabling teams
helping adoption.

**RACI shape:** platform team is Accountable for the platform-as-product and the paved roads;
workload teams are Accountable for their workloads and self-serve within the platform. Governance
moves from a Responsible *gate* to an Accountable *automated control*.

---

## Hybrid models

Real organizations rarely sit purely at one point. A **hybrid** applies different models to
different parts of the estate based on maturity and risk — e.g. **shared management / federated for
core regulated systems, decentralized for an innovation lab.** This is legitimate and common, not a
failure to decide. The key is to be *deliberate*: document which model applies where and why, so the
hybrid is a designed choice rather than drift. Azure CAF explicitly calls this out as a valid
approach.

When recommending a hybrid, define the "zones" (e.g. by risk tier, business unit, or workload type)
and the model for each, plus the few rules that apply across all zones (usually identity, security
baseline, and cost visibility stay central even in the autonomous zones).

---

## Framework cross-walk

Use this to translate the vendor-neutral archetypes into the vocabulary of the cloud the
organization is on. **Verify current vendor wording with the live MCP doc tools when citing** — the
vendors revise these (Azure CAF renamed models in 2025).

| Archetype (neutral) | Azure CAF (2025) | AWS | Gartner / industry concepts |
| --- | --- | --- | --- |
| Centralized | Centralized | Centralized cloud team; pre-CCoE | Traditional centralized I&O |
| Federated / Hub-and-Spoke | **Shared Management** (platform teams + workload teams) | **CCoE** + landing zones; WA "Separated AEO/IEO" | Federated / CCoE model |
| Platform Engineering | Shared Management with platform-as-product / subscription vending | Platform team + golden paths; WA spectrum toward integrated | Platform engineering; product-centric operating model; Team Topologies |
| Decentralized | Decentralized | Fully distributed / per-team accounts; WA "Fully Integrated" | "You build it, you run it"; distributed ownership |
| Hybrid | Hybrid operating model | Mixed per business unit | Bimodal (legacy term); differentiated operating model |

Notes:
- **Azure CAF** historically used *Decentralized / Centralized / Enterprise / Distributed*; the 2025
  guidance reframed around *Centralized / Shared Management / Decentralized / Hybrid*. If the user
  references the older four, map "Enterprise" → federated/shared-management and "Distributed" →
  decentralized, and note the rename.
- **AWS Well-Architected** frames an operating-model spectrum by how application and infrastructure
  engineering responsibilities are split: *Fully Separated* (AEO/IEO) → *Separated with shared
  responsibilities* → *Fully Integrated*. This is a useful lens for the *responsibility boundary*
  inside a federated model.
- **Gartner** emphasizes the shift from project-centric to **product-centric** operating models and
  the CCoE evolving into a broader "cloud business office" / enablement function. Treat specific
  Gartner artifact names with care and verify before quoting in a formal document.

---

## Team roles that recur across models

Useful when writing the RACI and the "capabilities required" sections:

- **Cloud platform / CCoE team** — landing zone, networking, identity, shared services, automation.
- **Security / GRC** — security baseline, policy, compliance monitoring (usually keeps central veto
  on IAM and security controls even in autonomous models).
- **FinOps / cloud financial management** — cost visibility, budgets, optimization, showback/chargeback.
- **Workload / product / stream-aligned teams** — build and run business workloads.
- **Enabling team** — helps workload teams adopt the platform and raise their cloud skills.
- **Cloud governance team** — policy definition, RACI ownership, exception handling.
- **Cloud business office / sponsor** — exec sponsorship, funding, removing org blockers (the thing
  most transitions die without).
