# Transition Roadmap Patterns

How to plan the move from the current operating model to the target (Step 5). This is what separates
an actionable assessment from an academic one. **Operating-model transitions fail on org change far
more often than on technology** — so this guidance leans heavily on people, responsibility, and
sequencing.

## Core principles

1. **Phase it; never big-bang.** Re-orging cloud responsibilities overnight breaks delivery and
   burns trust. Move in waves with exit criteria between them.
2. **Responsibility moves before tooling.** The essence of an operating-model change is *who is
   accountable for what* shifting between teams. The RACI evolution is the real backbone of the
   roadmap; the platform/tooling enables it.
3. **Earn trust with quick wins.** Workload teams give up the new model the first time it makes them
   slower. Front-load visible wins (a self-service path, a removed ticket queue) before asking teams
   to take on new responsibility.
4. **Keep security and identity central until the autonomous side is provably ready.** The safest
   sequencing is: stand up guardrails centrally first, then progressively delegate within them.
5. **Name an executive sponsor and a target date.** Transitions without sponsorship stall the moment
   they hit an org boundary. The sponsor's job is removing those blockers.

## A typical phased shape

Adapt to the specific from→to. This is the common arc (e.g. Centralized → Federated → Platform):

### Phase 0 — Foundation & mandate (weeks)
- Secure exec sponsorship and funding; agree the target model and success metrics.
- Stand up (or formalize) the central team / CCoE and its charter.
- Baseline the current state: estate inventory, current RACI, pain points, skills gap.
- **Exit criteria:** sponsor signed up, target model agreed, central team chartered.

### Phase 1 — Guardrails & foundations (months)
- Build the landing zone, network, identity baseline, security policy, and cost visibility.
- Define and publish the **responsibility boundary** between central and workload teams (the single
  most important artifact — ambiguity here is the top failure mode).
- Establish governance-as-policy where possible so the compliant path is automated.
- **Quick win:** first reusable pattern / paved path that saves a workload team real time.
- **Exit criteria:** guardrails live, RACI published, one workload team operating in the new model.

### Phase 2 — Pilot delegation (months)
- Onboard 2–3 pilot workload teams into the target model; they take on their accountable scope
  within the guardrails.
- Build enablement: training, documentation, an enabling team to support adoption.
- Tune the boundary and guardrails based on real friction.
- **Exit criteria:** pilots running successfully; playbook for onboarding the rest exists.

### Phase 3 — Scale-out (quarters)
- Roll the model across the remaining workload teams in waves (by readiness/risk).
- Mature FinOps, security monitoring, and platform self-service.
- Decommission the old ticket-queue / central-provisioning path.
- **Exit criteria:** majority of teams in the target model; old model retired.

### Phase 4 — Optimize / evolve (ongoing)
- Treat the platform as a product; measure adoption and developer experience.
- Evolve toward the next point on the spectrum if warranted (e.g. Federated → Platform Engineering).
- Regularly reassess — the right model at 10 teams may be wrong at 50.

## The RACI evolution

Show, per phase, how accountability shifts. A compact way to render it:

| Responsibility | Today | Phase 1 | Target |
| --- | --- | --- | --- |
| Landing zone / network | Central | Central | Central (platform) |
| Provisioning | Central (ticket) | Central + self-serve pilot | Self-service (platform) |
| Workload security config | Central | Shared | Workload (within guardrails) |
| IAM / security baseline | Central | Central | Central (veto retained) |
| Cost ownership | Central | Shared (showback) | Workload (chargeback) + FinOps |
| Incident response (workload) | Central | Shared | Workload |

The pattern: **platform-level concerns stay or consolidate central; workload-level concerns migrate
out to the teams; security/identity baseline stays central even as everything else delegates.**

## Capabilities, hires, and training

For each phase note what the org needs to *become* capable of:
- Central/platform team: automation, IaC, platform-product, FinOps, security engineering skills.
- Workload teams: enough cloud fluency to own their accountable scope — this is usually the gating
  constraint and the reason decentralized models fail when imposed too early.
- Enabling function: to raise workload-team skills and drive platform adoption.
Name whether each is hire / train / partner, because "we'll just upskill everyone" is where roadmaps
quietly fail.

## Quick wins to seed momentum

- Self-service provisioning for the most-requested resource (kills the most-hated ticket).
- A golden-path pipeline a team can adopt in a day.
- A cost dashboard that gives teams visibility they never had.
- Automating one painful compliance check so it stops being a manual gate.

## Common failure modes (call these out as risks)

- **CCoE-as-gatekeeper**: the central team renames itself but keeps gating — no agility gained.
- **Delegation without enablement**: teams handed accountability they lack the skills to carry.
- **Ambiguous boundary**: "I thought platform owned that" — gaps in security/ops ownership.
- **No sponsor**: stalls at the first org boundary.
- **Big-bang**: simultaneous re-org breaks delivery and credibility.
- **Tooling-first**: a shiny platform nobody adopts because the responsibility model didn't change.
- **Ignoring the people side**: roles, incentives, and team identity not addressed — quiet
  resistance kills it.

Map the top risks to mitigations in the document's risk section; don't leave them implicit.
