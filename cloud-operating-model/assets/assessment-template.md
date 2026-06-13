# Cloud Operating Model Assessment & Transition Roadmap
**Organization:** [name] · **Prepared:** [date] · **Author:** [name/role] · **Status:** [Draft/Final]

> This template is layered on purpose. The **Executive Summary** and **Recommendation** are written
> for leaders — business outcomes, light jargon. Everything below is for architects and platform
> leads. Fill every bracket; delete any section that genuinely doesn't apply (and say why if its
> absence is notable). Keep the exec layer to ~1 page.

---

## 1. Executive Summary
*(≤1 page. A leader who reads only this should understand the situation, the recommendation, and what
it costs.)*

- **Situation:** [1–2 sentences: how cloud is run today and why it's being reviewed.]
- **Recommendation:** [The target operating model, in one sentence.]
- **Why:** [2–3 bullets tying the recommendation to the business drivers.]
- **What it takes:** [Headline cost/effort/timeline and the key trade-off being accepted.]
- **Key risks:** [Top 2–3, each with a one-line mitigation.]

---

## 2. Context & Drivers
*(The assumptions the recommendation rests on. If these are wrong, the recommendation changes.)*

- **Business drivers:** [what's forcing the change — ranked, dominant driver first]
- **Current operating model:** [name it honestly — centralized / ad hoc / nascent CCoE / …]
- **Scale & maturity:** [# workload teams, cloud spend, in-house skill level, single/hybrid/multi-cloud]
- **Constraints:** [regulation, data residency, org boundaries, re-org appetite]
- **Cloud platform(s):** [AWS / Azure / GCP / multi]
- **Goals (12–24 mo) & non-negotiables:** [target state; guardrails that can't move]

---

## 3. Candidate Operating Models Considered
*(Brief description of each model in the running, in this organization's terms. 2–4 models. Full
archetype detail lives in the appendix or the reference catalog — keep these tight and contextual.)*

- **[Model A]** — [what it would mean here, in 2–3 sentences]
- **[Model B]** — …
- **[Model C]** — …

---

## 4. Comparison & Scoring
*(The analytical core. Weights reflect the drivers in §2 — sanity-check them first.)*

**Criteria weights (tied to drivers):** [list weights and why each is weighted as it is]

| Criterion (weight) | [Model A] | [Model B] | [Model C] |
| --- | :-: | :-: | :-: |
| Speed / agility (×_) | _ | _ | _ |
| Governance & risk (×_) | _ | _ | _ |
| Cost efficiency (×_) | _ | _ | _ |
| Scalability (×_) | _ | _ | _ |
| Skills demand (×_) | _ | _ | _ |
| Security posture (×_) | _ | _ | _ |
| Innovation / autonomy (×_) | _ | _ | _ |
| Change effort (×_) | _ | _ | _ |
| **Weighted total** | **_** | **_** | **_** |

**Interpretation:** [1 short paragraph — what the matrix says, and where it's sensitive: "if X were
weighted differently, B and C tie."]

---

## 5. Recommendation
*(A clear steer, not a menu.)*

- **Target model:** [name — and the vendor-framework term if useful, e.g. "Federated / Azure CAF
  Shared Management"]
- **Rationale:** [why it wins given the drivers — reference the matrix]
- **Trade-offs accepted:** [what they give up — be honest]
- **Preconditions for success:** [skills, sponsorship, tooling that must be true]
- **(If hybrid):** [which model applies to which zone of the estate, and why]

---

## 6. Target Operating Model — How It Works
*(The technical depth: what the target actually looks like in operation.)*

- **Team structure:** [central/platform team, workload teams, security/GRC, FinOps, enabling team]
- **Responsibility boundary:** [the crucial line — what the centre owns vs. what workload teams own]
- **Governance approach:** [how guardrails are set and enforced — manual review vs. governance-as-code]
- **Shared services / platform scope:** [landing zone, network, identity, paved paths, etc.]

### Target RACI (summary)
| Responsibility | Central/Platform | Workload teams | Security/GRC | FinOps |
| --- | :-: | :-: | :-: | :-: |
| Landing zone / network | A/R | I | C | I |
| Provisioning | [A/R] | [R] | I | I |
| Workload security config | [C] | [A/R] | [C] | I |
| IAM / security baseline | C | I | A/R | I |
| Cost ownership | I | [R] | I | A |
| Workload incident response | [C] | [A/R] | I | I |

*(R = Responsible, A = Accountable, C = Consulted, I = Informed. Adjust to the chosen model.)*

---

## 7. Transition Roadmap
*(Phased, with ownership shifts and exit criteria. Adapt the phases to the from→to distance.)*

### Phase 0 — Foundation & Mandate — [timeframe]
- **Objective:** [...]
- **Key activities:** [...]
- **Quick win:** [...]
- **Exit criteria:** [...]

### Phase 1 — Guardrails & Foundations — [timeframe]
- **Objective / activities / RACI shifts / capabilities needed / quick win / exit criteria:** [...]

### Phase 2 — Pilot Delegation — [timeframe]
- [...]

### Phase 3 — Scale-out — [timeframe]
- [...]

### Phase 4 — Optimize & Evolve — [ongoing]
- [...]

### Responsibility shift across phases
| Responsibility | Today | Phase 1 | Phase 2 | Target |
| --- | --- | --- | --- | --- |
| [e.g. Provisioning] | Central (ticket) | Central + pilot self-serve | Self-serve (pilots) | Self-service platform |
| … | | | | |

---

## 8. Capabilities, People & Change
*(Where transitions actually succeed or fail.)*

- **Central/platform team needs:** [skills — hire / train / partner]
- **Workload teams need:** [cloud fluency to own their scope — the usual gating constraint]
- **Org-change actions:** [role changes, incentives, comms, addressing team identity/resistance]
- **Executive sponsor:** [named role accountable for removing blockers]

---

## 9. Risks & Mitigations
| Risk | Likelihood / Impact | Mitigation |
| --- | --- | --- |
| [CCoE becomes a gatekeeper] | [M/H] | [Charter the team as enabling; measure adoption not gating] |
| [Delegation without enablement] | [ / ] | [Enabling team + training before handing accountability] |
| [Ambiguous responsibility boundary] | [ / ] | [Publish RACI; review at each phase exit] |
| [No sponsorship] | [ / ] | [Name sponsor in Phase 0; escalation path] |
| … | | |

---

## 10. Success Metrics
*(How you'll know the new model is working.)*

- [e.g. lead time to provision compliant infra: from __ to __]
- [e.g. % workload teams self-serving; ticket-queue volume; security findings; cost variance]
- [Review cadence — when to reassess the model itself]

---

## Appendix
- [Full archetype descriptions, framework mapping, glossary, current-state inventory, references]
