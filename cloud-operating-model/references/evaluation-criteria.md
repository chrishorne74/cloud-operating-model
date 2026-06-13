# Evaluation Criteria & Scoring

How to compare operating models objectively and build the comparison matrix (Step 3). The point of a
scored matrix is not false precision — it's to make the reasoning *visible and contestable*. A reader
should be able to challenge one cell and watch the conclusion shift.

## The criteria

These eight dimensions cover what matters when choosing an operating model. Use all that are
relevant; drop any that don't apply to the organization and say why.

| Criterion | What it measures | Tends to favor… |
| --- | --- | --- |
| **Speed / agility** | How fast workload teams can deliver and self-serve | Decentralized, Platform Engineering |
| **Governance & risk control** | Consistency of policy enforcement; auditability | Centralized, Federated |
| **Cost efficiency** | Spend visibility, optimization, avoidance of duplication | Federated/Platform (visibility) vs Centralized (control) |
| **Scalability** | Does it hold up as workload teams multiply without a bottleneck? | Platform Engineering, Federated |
| **Skills demand** | How much cloud skill is needed, and *where* (central vs every team) | Centralized concentrates it; Decentralized demands it everywhere |
| **Security posture** | Strength and consistency of security controls | Centralized, Platform (governance-as-code) |
| **Innovation / autonomy** | Freedom for teams to experiment and own outcomes | Decentralized, Platform Engineering |
| **Change effort / disruption** | How hard the transition is from *today* | (Penalizes models far from current state) |

"Change effort" is special: it doesn't describe the model in the abstract, it describes the *distance
from the current state*. A great target model that requires a brutal re-org may lose to a good one
that's reachable. Always score it relative to where the organization is now.

## Weighting to the drivers

A flat, unweighted matrix hides the most important input: **what this organization is actually
trying to solve.** Take the dominant drivers from intake (Step 1) and weight accordingly. Make the
weights explicit in the document — they encode the business priorities and are the first thing a
leader should sanity-check.

**Examples:**
- *Driver = "audit finding, security inconsistent"* → weight Governance, Security high; Speed lower.
  Likely pulls toward Federated or Centralized-then-Federated.
- *Driver = "we're too slow, teams route around central IT"* → weight Speed, Scalability, Innovation
  high. Likely pulls toward Federated → Platform Engineering.
- *Driver = "cloud spend is out of control"* → weight Cost efficiency, Governance high. Often
  Federated with a strong FinOps function.
- *Driver = "scaling from 5 to 50 teams"* → weight Scalability, Skills demand high; Centralized
  scores badly on the bottleneck.

A simple, defensible scheme: weight each criterion 1–3 (3 = directly tied to a primary driver, 1 =
nice-to-have), score each model 1–5 per criterion, multiply, sum. Don't over-engineer the math — the
transparency of *why* each score landed matters more than the arithmetic.

## Scoring rubric (1–5)

Keep scores honest and the rationale one line each. Suggested anchors:

- **5** — Model is a natural strength here; little effort to realize.
- **3** — Workable but with caveats or required investment.
- **1** — Structural weakness; would need significant mitigation.

Avoid scoring everything 3–4 (no signal) or stacking the deck for a pre-chosen answer (no
credibility). If two models tie, that's a legitimate finding — surface it and let secondary criteria
or the change-effort score break it.

## Matrix format

Render as a table the reader can scan. Show weights, per-criterion scores, and weighted totals.
Example shape (scores illustrative):

| Criterion (weight) | Centralized | Federated/CCoE | Platform Eng |
| --- | :-: | :-: | :-: |
| Speed/agility (×3) | 2 | 4 | 5 |
| Governance & risk (×3) | 5 | 4 | 4 |
| Cost efficiency (×2) | 3 | 4 | 4 |
| Scalability (×3) | 1 | 4 | 5 |
| Skills demand (×2) | 4 | 3 | 2 |
| Security posture (×2) | 4 | 4 | 5 |
| Innovation (×1) | 2 | 4 | 5 |
| Change effort (×2) | 5 | 3 | 1 |
| **Weighted total** | **…** | **…** | **…** |

Always include a sentence under the matrix interpreting it — the number is the start of the argument,
not the end. Note where the result is sensitive (e.g. "if Speed were weighted ×2 instead of ×3,
Federated and Platform tie").
