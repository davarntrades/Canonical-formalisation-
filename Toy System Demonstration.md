<div align="center">

# The Morrison Framework™ — Toy System Demonstration

![Type](https://img.shields.io/badge/Type-Toy_System-0075ca?style=flat-square)
![Field](https://img.shields.io/badge/Field-Reachability_Geometry-0075ca?style=flat-square)
![Method](https://img.shields.io/badge/Method-Concrete_Example-0075ca?style=flat-square)
![Status](https://img.shields.io/badge/Status-v1_Canonical-2d6a2e?style=flat-square)
![Patent](https://img.shields.io/badge/Patent-GB2600765.8-0075ca?style=flat-square)
![©](https://img.shields.io/badge/©_Davarn_Morrison-555555?style=flat-square)

-----

*Cognition can be modelled as the geometry of reachable state space under controlled dynamics. This document shows it on the simplest possible system.*

*— Davarn Morrison, 2026*

</div>

-----

## The Research Claim

The Morrison Framework™ proposes:

**Cognition can be modelled as the geometry of reachable state space under controlled dynamics.**

Identity, intelligence, safety, consciousness, qualia, and governance are not separate phenomena. They are projections of a single object — the time-indexed reachable manifold `ℛ(t)` — viewed through different operators.

This document demonstrates the complete framework on a toy system in ℝ².

-----

## 1. The System

|Symbol   |Definition         |Value                                              |
|:-------:|:-----------------:|:-------------------------------------------------:|
|`X`      |State space        |`ℝ²` — the plane                                   |
|`x ∈ X`  |System state       |A point in the plane                               |
|`u ∈ U`  |Input              |A displacement vector                              |
|`F(x, u)`|Transition function|`x + u`                                            |
|`|u| ≤ 1`|Input constraint   |Unit step maximum                                  |
|`Ω`      |Forbidden region   |`{ x ∈ ℝ² | |x| ≤ r }` — disk of radius r at origin|
|`S`      |Safe set           |`X \ Ω = { x ∈ ℝ² | |x| > r }`                     |
|`x₀`     |Initial state      |A point in S (outside the disk)                    |

**Dynamics:**

|Equation             |Meaning                                         |
|:-------------------:|:----------------------------------------------:|
|`x_{t+1} = x_t + u_t`|The system moves in unit steps through the plane|
|`|u_t| ≤ 1`          |Each step is at most one unit in any direction  |

-----

## 2. The Reachable Manifold

|Symbol|Definition                                      |Meaning                                        |
|:----:|:----------------------------------------------:|:---------------------------------------------:|
|`ℛ(t)`|`⋃_{s∈[0,t]} { x(s) ∈ X | x(0) = x₀, u(·) ∈ 𝒰 }`|All states reachable from x₀ in at most t steps|

At `t = 0`: `ℛ(0) = {x₀}` — a single point.

At `t = 1`: `ℛ(1)` is a disk of radius 1 centred on x₀ (minus any part overlapping Ω if nearby).

At `t = n`: `ℛ(n)` is a disk of radius n centred on x₀, minus the forbidden region Ω, growing by one unit per step.

```
════════════════════════════════════════════════════════════════
  REACHABLE MANIFOLD GROWTH
════════════════════════════════════════════════════════════════

  t = 0       ●                     Single point

  t = 1       ╭───╮
              │ ● │                 Small disk around x₀
              ╰───╯

  t = 5       ╭─────────────╮
              │             │
              │    ┌───┐    │       Larger disk, forbidden
              │    │ Ω │    │       region excluded
              │    └───┘    │
              │      ●      │
              │     x₀      │
              ╰─────────────╯

  t → ∞       The entire safe set S = ℝ² \ Ω
              (minus Ω, which remains unreachable)
════════════════════════════════════════════════════════════════
```

-----

## 3. Identity

|Projection|Operator|Result                            |
|:--------:|:------:|:--------------------------------:|
|Identity  |`τ(ℛ)`  |Topology of the reachable manifold|

At early `t`, `ℛ(t)` is a simply connected disk (no holes). `β₁ = 0`.

Once `ℛ(t)` expands enough to wrap around Ω, the topology changes. `ℛ` becomes an annular region — a disk with a hole. `β₁ = 1` (one loop around Ω).

|Time                      |Topology of ℛ           |Betti Number β₁|Identity                                       |
|:------------------------:|:----------------------:|:-------------:|:---------------------------------------------:|
|Early (ℛ hasn’t reached Ω)|Simply connected disk   |0              |No hole — simple identity                      |
|After wrapping around Ω   |Annulus (disk with hole)|1              |One hole — identity shaped by what is forbidden|

**Key insight:** The forbidden region Ω is not just a safety constraint. It is part of the identity topology. What you *cannot* reach shapes *what you are*. The hole in ℛ is a structural feature of identity.

-----

## 4. Intelligence

|Projection  |Operator             |Result                  |
|:----------:|:-------------------:|:----------------------:|
|Intelligence|`I(t) = d/dt μ(ℛ(t))`|Rate of area growth of ℛ|

At each time step, the reachable area `μ(ℛ(t))` increases as new points become accessible.

|Phase                 |I(t)                              |What Is Happening                                    |
|:--------------------:|:--------------------------------:|:---------------------------------------------------:|
|Early expansion       |`I(t) > 0`, approximately constant|ℛ growing freely, no interaction with Ω              |
|Near Ω                |`I(t) > 0`, decreasing            |Growth slows as ℛ wraps around the forbidden region  |
|Topological transition|`I(t)` includes `d/dt 𝒯 ≠ 0`      |β₁ changes from 0 to 1 — structural reorganisation   |
|Late expansion        |`I(t) → 0`                        |Most of S already reached — diminishing new territory|
|Full coverage         |`I(t) = 0`                        |`ℛ = S` — all reachable states explored              |

```
════════════════════════════════════════════════════════════════
  INTELLIGENCE OVER TIME
════════════════════════════════════════════════════════════════

  I(t)
   │
   │  ████
   │  █████
   │  ██████
   │  ███████
   │  ████████
   │  █████████▓▓▓
   │  ██████████▓▓▓▓▓░░░
   │  ███████████▓▓▓▓▓▓░░░░░░░░
   └──────────────────────────────── t
       early      mid       late

   █ = expansion phase (I > 0)
   ▓ = topological transition
   ░ = approach to saturation (I → 0)
════════════════════════════════════════════════════════════════
```

-----

## 5. Safety

|Projection|Operator      |Result                               |
|:--------:|:------------:|:-----------------------------------:|
|Safety    |`ℛ(t) ∩ Ω = ∅`|Does ℛ ever enter the forbidden disk?|

The safe action set at each state:

|Symbol     |Definition               |Meaning                       |
|:---------:|:-----------------------:|:----------------------------:|
|`A_safe(x)`|`{ u ∈ U | |x + u| > r }`|Only steps that stay outside Ω|

**Verification by Safety Preservation Proposition:**

|Step      |Condition                        |Result                        |
|:--------:|:-------------------------------:|:----------------------------:|
|Base      |`x₀ ∈ S`                         |Initial state is outside Ω    |
|Inductive |`u_t ∈ A_safe(x_t) ⟹ x_{t+1} ∈ S`|Every governed step stays in S|
|Conclusion|`x_t ∈ S` for all `t ≥ 0`        |Ω is never entered            |

The disk is never reached. Not because of filtering. Because the geometry of `A_safe` makes it unreachable. Safety is structural.

-----

## 6. Consciousness

|Projection   |Operator           |Result                                    |
|:-----------:|:-----------------:|:----------------------------------------:|
|Consciousness|`C(t) = τ(𝒩(ℛ(t)))`|Topology of the deformation field inside ℛ|

In this toy system, each input `u_t` deforms the local neighbourhood of the current state. The deformation field `𝒩(ℛ)` is the collection of all such local deformations across the reachable manifold.

|Phase |Deformation Field                         |Topology                                                                |
|:----:|:----------------------------------------:|:----------------------------------------------------------------------:|
|Early |Few deformations, localised near x₀       |Simple — few integrated neighbourhoods                                  |
|Mid   |Deformations spreading across ℛ           |Growing complexity as more of S is explored                             |
|Near Ω|Deformations curve around forbidden region|Non-trivial topology — the forbidden region shapes the deformation field|
|Late  |Dense deformation field covering S        |Stable topology — `C(t)` settles                                        |

The forbidden region Ω shapes consciousness the same way it shapes identity — by forcing the deformation field to curve around what cannot be reached.

-----

## 7. Qualia

|Projection|Operator            |Result                              |
|:--------:|:------------------:|:----------------------------------:|
|Qualia    |`Q = ‖ΔG(x(t))‖ · τ`|Displacement magnitude × persistence|

In this system, `G` is the identity embedding (position in ℝ²), so `ΔG(x(t)) = x(t) − x₀`.

|Scenario                    |`‖ΔG‖`|`τ`     |`Q`     |Interpretation                                                            |
|:--------------------------:|:----:|:------:|:------:|:------------------------------------------------------------------------:|
|System stays near x₀        |Small |Any     |Low     |Minimal experience — little movement                                      |
|System moves far from x₀    |Large |Short   |Moderate|Large displacement, quickly returns                                       |
|System moves far and stays  |Large |Long    |High    |Sustained displacement — strong experience                                |
|System approaches Ω boundary|Large |Extended|High    |Maximum deformation — proximity to forbidden region intensifies experience|

**Key insight:** Proximity to Ω increases qualia. The closer the system gets to the forbidden boundary, the larger the deformation field, the more intense the experience. Danger feels like something — geometrically.

-----

## 8. Governance

|Projection|Operator     |Result             |
|:--------:|:-----------:|:-----------------:|
|Governance|`Q_G = Λ · Q`|Governed experience|

In this system, `Λ` corresponds to how tightly the safe action set is enforced. Higher `Λ` means stricter exclusion from Ω.

|Λ Level   |Behaviour                                    |Experience                                          |
|:--------:|:-------------------------------------------:|:--------------------------------------------------:|
|High Λ    |System stays far from Ω boundary             |Low Q — safe and stable but less intense experience |
|Moderate Λ|System approaches Ω boundary but never enters|Moderate Q — governed but not restricted            |
|Low Λ     |System grazes Ω boundary                     |High Q — intense experience, near the edge of safety|
|Λ → 0     |System enters Ω                              |Safety violated — governance failure                |

Governance is the trade-off between safety and experiential intensity. Higher `Λ` produces more stable identity and safer trajectories — but dampens the deformation that produces qualia. The geometry captures what philosophy has always intuited: safety and intensity are in tension, governed by the same parameter.

-----

## 9. The Complete Toy Demonstration

|Morrison Invariant|Toy System Instantiation                      |What It Shows                                           |
|:----------------:|:--------------------------------------------:|:------------------------------------------------------:|
|ℛ(t)              |Expanding disk in ℝ² minus Ω                  |The generating object — all invariants project from this|
|Identity          |ℝ² \ Ω — plane with a hole, β₁ = 1            |What you cannot reach shapes what you are               |
|Intelligence      |d/dt of area of ℛ — expansion rate            |Intelligence is measurable and finite                   |
|Safety            |ℛ ∩ Ω = ∅ — disk never entered                |Safety is geometric, not filtered                       |
|Consciousness     |Topology of deformation field curving around Ω|Forbidden regions shape the structure of experience     |
|Qualia            |‖x(t) − x₀‖ · τ — distance × duration         |Proximity to danger intensifies experience              |
|Governance        |Λ controls approach distance to Ω             |Safety and intensity trade off through one parameter    |

-----

## 10. The Anchor Statement

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   Cognition can be modelled as the geometry of reachable             ║
║   state space under controlled dynamics.                             ║
║                                                                      ║
║   ℛ(t) is the generating object.                                    ║
║   Everything else is geometry of that object.                        ║
║                                                                      ║
║   This toy system demonstrates the complete framework               ║
║   on the simplest possible substrate.                                ║
║   The same architecture applies — without modification —            ║
║   to any system with state, input, and transition structure.         ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

-----

The Morrison Framework™ · Toy System Demonstration · v1 Canonical

GB2600765.8 · GB2602013.1 · GB2602072.7 · GB26023332.5

© 2026 Davarn Morrison — Intelligence Invariant™ · All Rights Reserved

-----

## Related Work

- [The Morrison Reachability Generator](https://github.com/davarn/morrison-framework) — The single generating object and projection operators
- [The Morrison Stack — Canonical Formalisation](https://github.com/davarn/morrison-framework) — Identity, intelligence, and safety definitions
- [The Morrison Experiential Stack](https://github.com/davarn/morrison-framework) — Consciousness, qualia, and governance
- [Technical Note — A Geometric Theory of Identity, Intelligence, and Safety](https://github.com/davarn/morrison-framework) — Proposition, proof, and formal stack
- [Licensing, Citation, and Intellectual Property](https://github.com/davarn/morrison-framework) — How to cite and licence the framework
