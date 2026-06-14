# Workforce Sizing & FTE Benchmarking

How to answer "**are we resourced right for this workload, compared to our peers?**" There is no
single right number. The credible method is to **triangulate a top-down peer ratio against a
bottom-up workload model, then normalize for maturity** — and read any gap as *automation vs.
staffing* before *hire vs. cut*.

This connects directly to the operating model: a centralized, ticket-driven model needs *more* ops
FTE per unit of work than a platform-engineering model. So a resourcing question is partly a *model*
question — don't answer it in isolation from `operating-models.md`.

## Contents
1. [Top-down ratio benchmarking](#1-top-down-ratio-benchmarking)
2. [Bottom-up workload modeling](#2-bottom-up-workload-modeling)
3. [Normalization factors](#3-normalization-factors)
4. [Hard floors](#4-hard-floors)
5. [Benchmark sources](#5-benchmark-sources)
6. [How to run it](#6-how-to-run-it)

---

## 1. Top-down ratio benchmarking

Normalize FTE against a denominator that scales with the work, then compare to a matched peer
cohort. Common ratios:

| Ratio | What it measures | Watch-out |
| --- | --- | --- |
| **Cloud spend managed per platform FTE** ($/FTE) | Financial leverage of the ops team | Spend ≠ complexity; lift-and-shift estates inflate it |
| **Workloads / apps per ops FTE** | Operational span of control | "App" definitions vary wildly between orgs |
| **Accounts / subscriptions per platform engineer** | Landing-zone scale handled | Sensitive to account-vending automation |
| **Developers supported per platform engineer** | Platform team *leverage* | The headline platform-engineering metric |
| **Workload / stream-aligned teams per platform FTE** | Team Topologies span | — |
| **Tickets / requests per FTE, or % toil** | Capacity consumed by manual work | High = automation gap, not a staffing gap |
| **Ops FTE as % of total IT / engineering** | Org-level shape | Benchmarked by Gartner ITKMD |

The most defensible denominators for a platform team are **developers-supported** and
**spend-managed**. The trap: raw ratios mislead unless normalized (§3) — two orgs running the same
estate can differ 2–3× in FTE purely on automation maturity.

## 2. Bottom-up workload modeling

Build FTE from demand so the number is defensible, not just benchmark-matched. Three lenses:

- **Functional decomposition** — size each operating-model function off its own driver: landing
  zone / network, identity, security baseline, platform products, FinOps, governance, service
  management, enablement. (Roles listed in `operating-models.md` → "Team roles that recur.")
- **Activity / toil-based** — estimate recurring demand: provisioning requests × handling time,
  patch cycles, incident volume × MTTR, change volume. Exposes toil you could automate away instead
  of hiring for.
- **Squad-based** (product / platform models) — N product squads × (1 Product Owner + k engineers +
  SRE) + cross-cutting roles. Maps to the structure in `platform-as-a-product.md`.

Then compare bottom-up **required** vs. current **actual**. The gap is the real answer, and it
splits cleanly into "hire" vs. "automate."

## 3. Normalization factors

The part most people skip — and why naïve benchmarking misleads. Only compare to peers matched on
these:

- **Automation / self-service maturity** — IaC coverage, % provisioned self-service. The single
  biggest swing factor.
- **Operating-model maturity** — centralized/ticket-driven needs more FTE per unit than
  federated/platform. The resourcing question is partly a model question.
- **Managed-services mix** — heavy PaaS/serverless structurally lowers ops FTE vs. IaaS/VMs.
- **Cloud-native vs. lift-and-shift / legacy %.**
- **Regulation & risk tier** — financial services / healthcare / public sector carry more
  governance and security FTE.
- **Multi-cloud vs. single** — multi-cloud multiplies platform surface.
- **Coverage hours** — business-hours vs. 24/7 (see §4).

"Peers" by revenue or headcount alone is **not** a peer set. Match on industry, size, cloud
maturity, and regulatory burden before comparing.

## 4. Hard floors

Some numbers are set by structure, not workload — they override the ratio math:

- **Sustainable 24/7 on-call** needs roughly **6–8 people per rota** (≤1 week in 6–8, bounded
  incidents per shift — Google SRE / PagerDuty guidance). Below that you're under-resourced
  regardless of estate size.
- **Toil cap** — SRE practice caps toil at ~50% of capacity. If operational load exceeds that, the
  answer is automation or heads, and benchmarks won't reveal it.
- **Bus-factor minimum** — ≥2 deep on every critical capability.

## 5. Benchmark sources

Use these for the peer-cohort numbers; treat published ratios as **calibration rules of thumb to
sanity-check the bottom-up model, not targets.** Verify currency before quoting in a formal document.

- **Gartner IT Key Metrics Data (ITKMD)** & Gartner Benchmark Analytics — IT/infra staffing ratios,
  FTE as % of IT.
- **FinOps Foundation (State of FinOps)** — FinOps practitioner sizing vs. cloud spend.
- **Team Topologies** — platform-team sizing heuristics (size to reduce cognitive load, not to a
  fixed ratio).
- **Google SRE book** — toil, error-budget, on-call staffing math.
- **DORA / Puppet State of DevOps / Platform Engineering reports** — productivity context.
- **Flexera State of the Cloud** — estate/spend context.

Commonly cited heuristics (validate against §3 before relying on them): platform engineer : developer
in the rough range of **1:10 to 1:25** depending on platform maturity; FinOps practitioners scaling
with cloud spend. These swing widely with automation — present them as ranges, never as a single
target.

## 6. How to run it

1. Pick a normalized denominator (developers-supported and spend-managed are the most defensible).
2. Build the bottom-up functional/squad model → **required** FTE.
3. Pull a **matched** peer cohort and compare the **normalized** ratio.
4. Where you're an outlier, ask "**automation gap or staffing gap?**" before "hire or cut?" — the
   answer is usually operating-model / automation maturity, not headcount.

Render the result as: current vs. required FTE by function, the normalized peer ratio with cohort
definition, the hard-floor checks, and a recommendation that names automation actions alongside any
hiring. Feed hiring/automation conclusions into the transition roadmap's capabilities workstream
(`transition-roadmap.md`).
