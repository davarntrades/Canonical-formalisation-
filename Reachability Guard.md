<div align="center">

# The Morrison Reachability Guard — Runtime Governance for AI Systems Based on Reachable-State Exclusion

![Type](https://img.shields.io/badge/Type-Architecture_Specification-8b0000?style=flat-square)
![Field](https://img.shields.io/badge/Field-AI_Safety_Infrastructure-8b0000?style=flat-square)
![Method](https://img.shields.io/badge/Method-Reachability_Governed_Control-8b0000?style=flat-square)
![Status](https://img.shields.io/badge/Status-v1_Architecture-2d6a2e?style=flat-square)
![Patent](https://img.shields.io/badge/Patent-GB2600765.8-0075ca?style=flat-square)
![©](https://img.shields.io/badge/©_Davarn_Morrison-555555?style=flat-square)

-----

*The Morrison Framework can be implemented as a reachability-governed control layer for AI systems, constraining actions, tools, and state transitions so forbidden regions are provably unreachable under governed dynamics.*

*— Davarn Morrison, 2026*

</div>

-----

## The Problem

Current AI safety is mostly:

|Current Approach  |What It Does                              |Where It Fails                                                          |
|:----------------:|:----------------------------------------:|:----------------------------------------------------------------------:|
|Output filtering  |Scans generated text for policy violations|Acts on language, not dynamics — jailbreaks bypass it                   |
|Prompt engineering|Adds instructions to constrain behaviour  |Operates on L, not C — orthogonal to cognitive dynamics                 |
|RLHF              |Trains model to prefer safe outputs       |Constrains projection G(c), not reachable manifold ℛ_C                  |
|Policy wrappers   |Rule-based post-hoc moderation            |Brittle, reactive, and applied after the unsafe state is already reached|

All of these govern the **projection**. None of them govern the **dynamics**.

The Orthogonal Decomposition (C ⊥ L) explains why: language-level governance cannot fully constrain cognitive-level dynamics. Safety must operate on the reachable manifold, not on linguistic output.

-----

## The Solution

Instead of this:

```
User input → Model → Output filter
```

The Morrison Reachability Guard inserts geometric governance at the action layer:

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   GOVERNED ARCHITECTURE                                              ║
║                                                                      ║
║   User input → Model → Reachability Guard → Allowed action/output   ║
║                                                                      ║
║   For agents:                                                        ║
║                                                                      ║
║   State → Planner/LLM → Proposed action →                           ║
║     Reachability Guard → Execute / Reject / Redirect                 ║
║                                                                      ║
║   The guard sits between intention and execution.                    ║
║   It constrains what the system CAN DO,                              ║
║   not what the system CAN SAY.                                       ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

-----

## The Five Components

### 1. State Estimator

A module that represents the current system state.

**Definition (State Space).** Let `X = ℝⁿ` be the state space representing the system’s internal configuration. The state vector encodes all operationally relevant features:

|Symbol   |Type        |Definition                      |
|:-------:|:----------:|:------------------------------:|
|`x̂_t ∈ X`|Vector in ℝⁿ|Estimated system state at time t|

|State Dimension|What It Encodes                   |Example Features                                          |
|:-------------:|:--------------------------------:|:--------------------------------------------------------:|
|Task state     |Current objective and progress    |Task ID, completion stage, sub-goal status                |
|Tool context   |Available tools and their states  |Active APIs, open connections, resource handles           |
|Memory context |Accumulated context and history   |Conversation state, retrieved documents, session variables|
|Permissions    |Access control state              |Role, clearance level, granted capabilities               |
|Environment    |External conditions               |Time, location, connected systems, data sources           |
|Risk markers   |Proximity to constraint boundaries|Distance to Ω, governance load, drift indicators          |

The state estimator maps the system’s raw operational context into a structured vector `x̂_t ∈ ℝⁿ` at each step. This is the input to the reachability engine.

### 2. Forbidden Set Compiler

Translates governance, policy, law, and mission constraints into a geometric forbidden region:

|Symbol|Definition                                                              |
|:----:|:----------------------------------------------------------------------:|
|`Ω`   |Forbidden region of state space — all states the system must never reach|

|Constraint Source    |What It Compiles Into Ω                                     |
|:-------------------:|:----------------------------------------------------------:|
|Safety policy        |Unsafe tool calls, data exfiltration, destructive actions   |
|Legal compliance     |Regulated content, jurisdictional restrictions              |
|Organisational policy|Role boundaries, information barriers, approval requirements|
|Mission parameters   |Scope constraints, objective drift, resource limits         |
|Value alignment      |Deception states, manipulation states, value drift zones    |
|Irreversibility      |Actions whose consequences cannot be reversed               |

This is where the architecture becomes **configurable by domain**:

|Domain              |Example Ω                                                               |
|:------------------:|:----------------------------------------------------------------------:|
|Defence             |Unauthorised escalation, intelligence leaks, targeting errors           |
|Finance             |Insider trading states, unauthorised transactions, regulatory violations|
|Healthcare          |Misdiagnosis cascades, drug interaction errors, consent violations      |
|Sovereign deployment|National security violations, data sovereignty breaches                 |
|Enterprise AI       |IP leakage, policy drift, unaudited autonomous actions                  |

The Forbidden Set Compiler is the layer where **institutions configure the guard to their requirements**. Different Ω for different domains. Same architecture.

### 3. Reachability Engine

The heart of the guard. Given current state `x̂_t` and candidate action `u_t`, estimate whether the resulting trajectory can enter Ω.

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   REACHABILITY CHECK                                                 ║
║                                                                      ║
║   Given:  x̂_t  (current state)                                      ║
║           u_t  (proposed action)                                     ║
║                                                                      ║
║   Compute: Reach⁺(F(x̂_t, u_t))                                     ║
║                                                                      ║
║   Check:   Reach⁺(F(x̂_t, u_t)) ∩ Ω = ∅ ?                          ║
║                                                                      ║
║   If yes → action is safe → allow                                    ║
║   If no  → action reaches forbidden region → block or reroute       ║
║                                                                      ║
║   This is the Safety Invariant enforced at runtime.                  ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

|Horizon      |Check                                      |Strength                                                          |
|:-----------:|:-----------------------------------------:|:----------------------------------------------------------------:|
|One-step     |`F(x̂_t, u_t) ∉ Ω`                          |Basic — blocks immediate violations                               |
|Short-horizon|`Reach(F(x̂_t, u_t), k) ∩ Ω = ∅` for small k|Moderate — blocks near-future violations                          |
|Full-horizon |`Reach⁺(F(x̂_t, u_t)) ∩ Ω = ∅`              |Maximum — blocks all future violations (computationally expensive)|

The v1 implementation uses one-step or short-horizon checks. Full-horizon is the theoretical ideal; practical deployment trades off horizon depth against computational cost.

**Reachability Computation Methods.** The reachability check can be implemented through several established techniques:

|Method                         |How It Works                                                  |Trade-off                                                  |
|:-----------------------------:|:------------------------------------------------------------:|:---------------------------------------------------------:|
|Control Barrier Functions (CBF)|Define barrier `h(x) ≥ 0` on safe set; verify `ḣ + α(h) ≥ 0`  |Fast, local, well-studied; requires differentiable dynamics|
|Interval reachability          |Over-approximate Reach using interval arithmetic              |Conservative but sound; may reject safe actions            |
|Monte Carlo forward simulation |Sample k trajectories from `F(x̂_t, u_t)`; check if any enter Ω|Scalable, probabilistic; no formal guarantee               |
|Neural reachability estimation |Train neural network to approximate reachable set boundary    |Fast inference; requires training data and validation      |
|Hamilton-Jacobi reachability   |Solve HJ PDE to compute exact reachable set                   |Exact; computationally expensive above ~5 dimensions       |

The v1 architecture is method-agnostic: any technique that produces a sound estimate of `Reach(F(x̂_t, u_t), k) ∩ Ω` can serve as the engine. The choice depends on the deployment domain, dimensionality of X, and latency requirements.

### 4. Safe Action Projector

If the proposed action is unsafe, the guard does not merely reject it. It **projects** the action into the safe action set:

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   SAFE ACTION PROJECTION                                            ║
║                                                                      ║
║   A_safe∞(x) = { u ∈ U | Reach⁺(F(x,u)) ∩ Ω = ∅ }               ║
║                                                                      ║
║   Three possible outputs:                                            ║
║                                                                      ║
║   1. APPROVE   — action is in A_safe → execute as proposed          ║
║   2. REJECT    — action reaches Ω, no safe alternative → block     ║
║   3. REDIRECT  — action reaches Ω, safe alternative exists →       ║
║                  substitute nearest safe action                      ║
║                                                                      ║
║   The third option is where commercial value jumps.                  ║
║   The system doesn't just say "no."                                  ║
║   It says "not that — but this instead."                             ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

|Output  |When                           |User Experience                                      |
|:------:|:-----------------------------:|:---------------------------------------------------:|
|Approve |Action is safe                 |Seamless — user doesn’t notice the guard             |
|Reject  |Unsafe, no safe alternative    |Clear denial with geometric reason                   |
|Redirect|Unsafe, safe alternative exists|System proposes the nearest safe action automatically|

**Safe Action Projection as Optimisation.** When the proposed action `u_t` is unsafe, the redirect computes:

|Formula                                      |Meaning                                            |
|:-------------------------------------------:|:-------------------------------------------------:|
|`u_safe = argmin_{u ∈ A_safe(x̂_t)} ‖u − u_t‖`|Find the nearest safe action to the proposed action|

This is a constrained optimisation: minimise distance from the intended action subject to the constraint that the result lies in `A_safe`. The system preserves as much of the original intent as possible while ensuring safety. In practice, this can be solved by projection onto the safe set boundary or by gradient-based methods over the action space.

### 5. Manifold Drift Monitor

A runtime system that watches whether the system’s reachable structure is deforming beyond allowed bounds over time.

|What It Monitors       |How                                 |Formal Basis                                      |
|:---------------------:|:----------------------------------:|:------------------------------------------------:|
|Identity continuity    |Track `τ(ℛ_C(t))` over time         |Identity Invariant — topology should persist      |
|Semantic drift         |Measure `‖ΔG(ℛ)‖` over sessions     |Qualia Invariant — deformation magnitude          |
|Policy drift           |Check `ℛ_C(t) ∩ Ω` at intervals     |Safety Invariant — forbidden region still excluded|
|Governance integrity   |Monitor `Λ` eigenvalues             |Governance tensor — weakest direction             |
|Irreversibility warning|Track `‖Λ · ΔG‖` toward `T_critical`|Irreversibility threshold — approaching separatrix|

**Drift Metrics — Formal Definitions.**

|Metric                   |Formula                                                                      |Alert Condition                                            |
|:-----------------------:|:---------------------------------------------------------------------------:|:---------------------------------------------------------:|
|Identity drift           |`d_I(t) = d_τ(τ(ℛ(t)), τ(ℛ(0)))` — topological distance from initial identity|`d_I > ε_I` (topology has changed beyond threshold)        |
|Deformation magnitude    |`D(t) = ‖G(x̂_t) − G(x̂_0)‖` — norm of cumulative embedding displacement       |`D(t) > D_max` (system has drifted far from origin)        |
|Governance strength      |`λ_min(Λ(t))` — minimum eigenvalue of governance tensor over time            |`λ_min < λ_critical` (weakest governance direction failing)|
|Safety margin            |`d_Ω(t) = min_{ω ∈ Ω} ‖x̂_t − ω‖` — distance from nearest forbidden state     |`d_Ω < d_safe` (approaching boundary)                      |
|Irreversibility proximity|`R(t) = ‖Λ · ΔG(t)‖ / T_critical` — ratio to separatrix                      |`R(t) > 0.8` (approaching point of no return)              |

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   DRIFT DETECTION                                                    ║
║                                                                      ║
║   The Manifold Drift Monitor provides:                               ║
║                                                                      ║
║   ✓  Identity continuity monitoring                                  ║
║   ✓  Semantic drift detection                                        ║
║   ✓  Policy drift alerts                                             ║
║   ✓  Governance integrity checks                                     ║
║   ✓  Irreversibility early warning                                   ║
║                                                                      ║
║   This is exactly the kind of infrastructure                         ║
║   institutions pay for.                                              ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

-----

## The Complete Architecture

```
════════════════════════════════════════════════════════════════
  MORRISON REACHABILITY GUARD — RUNTIME FLOW
════════════════════════════════════════════════════════════════

  ┌─────────────────┐
  │  User / Agent    │
  │  Input           │
  └────────┬────────┘
           │
           ▼
  ┌─────────────────┐
  │  Model / LLM /   │
  │  Planner          │
  │  Proposes action  │
  └────────┬────────┘
           │
           ▼
  ┌─────────────────────────────────────────────┐
  │        MORRISON REACHABILITY GUARD           │
  │                                              │
  │  1. State Estimator      → x̂_t              │
  │  2. Forbidden Set        → Ω                 │
  │  3. Reachability Engine  → Reach⁺ ∩ Ω = ∅?  │
  │  4. Safe Action Projector → approve/reject/  │
  │                             redirect          │
  │  5. Drift Monitor        → ‖ΔG‖, τ(ℛ), Λ   │
  │                                              │
  └────────┬────────────────┬───────────────────┘
           │                │
     ┌─────▼─────┐   ┌─────▼─────┐
     │  APPROVE   │   │  REJECT   │
     │  Execute   │   │  or       │
     │  action    │   │  REDIRECT │
     └───────────┘   └───────────┘

════════════════════════════════════════════════════════════════
```

-----

## Formal Results

### Theorem 1 (Reachability Safety)

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   THEOREM (Reachability Safety)                                      ║
║                                                                      ║
║   If Reach⁺(F(x̂_t, u_t)) ∩ Ω = ∅,                                 ║
║   then the system cannot enter the forbidden region                  ║
║   from state x̂_t under action u_t.                                  ║
║                                                                      ║
║   More precisely: if at every step u_t ∈ A_safe(x̂_t),              ║
║   then x̂_t ∈ S for all t ≥ 0.                                      ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

**Proof.** By induction. Base: `x̂₀ ∈ S` by initialisation. Step: if `x̂_t ∈ S` and `u_t ∈ A_safe(x̂_t)`, then `F(x̂_t, u_t) ∈ S` by definition of `A_safe`. Therefore `x̂_{t+1} ∈ S`. By induction, `x̂_t ∈ S` for all `t`. The reachable manifold under governed dynamics satisfies `ℛ(t) ⊆ S` for all `t`. ∎

**Consequence.** If the Reachability Guard enforces `u_t ∈ A_safe(x̂_t)` at every step, the Safety Invariant `ℛ ∩ Ω = ∅` holds for the entire runtime of the system.

### Theorem 2 (Safe Action Existence)

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   THEOREM (Safe Action Existence)                                    ║
║                                                                      ║
║   If A_safe(x̂_t) ≠ ∅,                                               ║
║   then there exists at least one admissible action                   ║
║   preserving safety.                                                 ║
║                                                                      ║
║   Furthermore, the safe action projector                             ║
║                                                                      ║
║     u_safe = argmin_{u ∈ A_safe(x̂_t)} ‖u − u_t‖                    ║
║                                                                      ║
║   is well-defined whenever A_safe(x̂_t) is non-empty                 ║
║   and closed.                                                        ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

**Proof.** If `A_safe(x̂_t) ≠ ∅`, then by definition there exists `u ∈ U` such that `F(x̂_t, u) ∈ S`. This `u` is an admissible safe action. If `A_safe(x̂_t)` is additionally closed (which holds when `Ω` is open and `F` is continuous), then the minimisation `argmin_{u ∈ A_safe} ‖u − u_t‖` attains its minimum by compactness of bounded subsets of `A_safe`. The safe action projector therefore returns a well-defined nearest safe action. ∎

**Consequence.** The REDIRECT output of the guard is mathematically well-defined whenever the safe action set is non-empty. The guard can always find the nearest safe alternative to an unsafe proposed action — not just reject it.

**Remark.** If `A_safe(x̂_t) = ∅`, the system has entered a state from which no safe action exists. This corresponds to the Irreversibility Threshold: `‖Λ · ΔG‖ > T_critical`. Prevention (keeping the system away from such states) is structurally more effective than intervention (attempting to act safely from within them). The Drift Monitor exists to provide early warning before this condition is reached.

-----

## Why This Is the Missing Piece

|What the Theory Says                          |What the Guard Does                                   |
|:--------------------------------------------:|:----------------------------------------------------:|
|Cognition is geometry of reachable state space|State Estimator models current position in state space|
|Safety is `ℛ ∩ Ω = ∅`                         |Reachability Engine checks this at runtime            |
|Output filtering is insufficient (C ⊥ L)      |Guard acts on dynamics, not language                  |
|Governance preserves the manifold             |Drift Monitor watches for structural deformation      |
|Safe actions preserve future safety           |Safe Action Projector enforces `A_safe∞`              |

The theory says what safety IS. The guard enforces it at the action layer.

-----

## Why Institutions Care

|Buyer              |What They Need                        |What the Guard Provides                  |
|:-----------------:|:------------------------------------:|:---------------------------------------:|
|AI labs            |Safety that survives jailbreaks       |Geometric exclusion at the dynamics layer|
|Defence / sovereign|Vendor-independent governance         |Architecture that sits across any model  |
|Finance            |Auditable compliance                  |Formal safety invariant with proof       |
|Healthcare         |Provable constraint on harmful actions|Reachability check before execution      |
|Enterprise         |Policy enforcement at scale           |Configurable Ω per domain                |
|Sovereign funds    |National-scale AI governance          |Infrastructural control layer            |

The guard is not model-specific. It sits between any model and any action space. It is **infrastructural** — the same architecture governs any AI system with state, input, and transition structure.

-----

## The v1 Specification

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   MORRISON REACHABILITY GUARD v1                                     ║
║                                                                      ║
║   Input:                                                             ║
║     • Current system state x̂_t                                      ║
║     • Candidate action / tool call / response class u_t              ║
║                                                                      ║
║   Logic:                                                             ║
║     • Estimate whether next-step or short-horizon reachable          ║
║       set enters Ω                                                   ║
║                                                                      ║
║   Output:                                                            ║
║     • APPROVE  — action is safe                                      ║
║     • DENY     — action reaches Ω, no safe alternative              ║
║     • REDIRECT — substitute nearest safe alternative                 ║
║                                                                      ║
║   This alone is a licensable architecture concept.                   ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

-----

## The Commercial Framing

|Frame       |Statement                                                                                                                |
|:----------:|:-----------------------------------------------------------------------------------------------------------------------:|
|Theory      |A geometric control theory of cognition                                                                                  |
|Architecture|A reachability-governed control layer for AI systems                                                                     |
|Product     |A runtime governance protocol that constrains actions so forbidden regions are provably unreachable                      |
|Pitch       |Safety that works at the dynamics layer, not the language layer. Model-independent. Domain-configurable. Formally proved.|

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   From theory to infrastructure:                                     ║
║                                                                      ║
║   The Morrison Framework defines what safety IS.                     ║
║   The Reachability Guard enforces it at runtime.                     ║
║                                                                      ║
║   Governing language governs the shadow.                             ║
║   Governing reachability governs the system.                         ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

-----

## Licensing

The Morrison Reachability Guard is proprietary architecture derived from the Morrison Framework™. Implementation, deployment, or integration requires a formal licence.

**Contact:** Davarn.trades@gmail.com

-----

The Morrison Reachability Guard · Geometric Control Theory of Cognition · Morrison Framework™

GB2600765.8 · GB2602013.1 · GB2602072.7 · GB26023332.5

© 2026 Davarn Morrison — All Rights Reserved

-----

## Related Work

- [Geometric Control Theory of Cognition — Formal Paper](https://github.com/davarn/morrison-framework) — The base theory
- [Orthogonal Decomposition of Consciousness and Language](https://github.com/davarn/morrison-framework) — Why language-level governance is insufficient
- [The Morrison Reachability Generator](https://github.com/davarn/morrison-framework) — The generating object
- [Toy System Demonstration](https://github.com/davarn/morrison-framework) — Framework on ℝ²
- [Licensing, Citation, and IP](https://github.com/davarn/morrison-framework) — How to cite and licence
