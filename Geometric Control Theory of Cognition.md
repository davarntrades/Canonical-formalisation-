<div align="center">

# Geometric Control Theory of Cognition: A Reachability-Based Framework for Identity, Intelligence, and Experience

![Type](https://img.shields.io/badge/Type-Canonical_Paper-0075ca?style=flat-square)
![Field](https://img.shields.io/badge/Field-Geometric_Control_Theory_of_Cognition-0075ca?style=flat-square)
![Method](https://img.shields.io/badge/Method-Reachable_Manifold_Formalism-0075ca?style=flat-square)
![Status](https://img.shields.io/badge/Status-v1_Canonical-2d6a2e?style=flat-square)
![Patent](https://img.shields.io/badge/Patent-GB2600765.8-0075ca?style=flat-square)
![©](https://img.shields.io/badge/©_Davarn_Morrison-555555?style=flat-square)

-----

*Cognition is the geometry of reachable state space under governed deformation. Identity, intelligence, safety, perception, and experience are not separate phenomena. They are different projections of the same reachable manifold.*

*— Davarn Morrison, 2026*

</div>

-----

## Abstract

This paper introduces the Geometric Control Theory of Cognition — a formal framework in which a cognitive system is modelled as a controlled dynamical system on a manifold, and all cognitive phenomena are derived as geometric properties of a single object: the time-indexed reachable manifold. Identity, intelligence, safety, consciousness, qualia, and governance emerge as projections of this manifold through well-defined operators. Consciousness appears as a topological invariant of the integrated deformation field inside the reachable manifold. A safety preservation result is proved. A toy system demonstrates the complete framework.

-----

## 1. The Generating Object

### 1.1 System

|Symbol                 |Type           |Definition         |
|:---------------------:|:-------------:|:-----------------:|
|`X`                    |Smooth manifold|State space        |
|`U`                    |Set            |Admissible inputs  |
|`F: X × U → X`         |Smooth map     |Transition function|
|`x_{t+1} = F(x_t, u_t)`|Dynamics       |System evolution   |

### 1.2 The Reachable Manifold

|Symbol|Definition                                      |Meaning                                  |
|:----:|:----------------------------------------------:|:---------------------------------------:|
|`ℛ(t)`|`⋃_{s∈[0,t]} { x(s) ∈ X | x(0) = x₀, u(·) ∈ 𝒰 }`|All states reachable from x₀ up to time t|

`ℛ(t)` is the generating object of the theory. Everything that follows is geometry of this object.

### 1.3 Supporting Definitions

|Symbol     |Type                              |Definition                                      |
|:---------:|:--------------------------------:|:----------------------------------------------:|
|`τ(·)`     |Functor                           |Topological structure induced on a submanifold  |
|`μ(·)`     |Measure                           |Volume, entropy, or dimension of a manifold     |
|`G: X → ℝⁿ`|Smooth embedding                  |Geometric state of the manifold                 |
|`ΔG(x(t))` |`G(x(t)) − G(x₀)`                 |Geometric deformation along a trajectory        |
|`𝒩_t(X, I)`|Submanifold                       |Neighbourhood of X deformed by input I at time t|
|`Λ`        |Positive-definite tensor (`Λ ≻ 0`)|Governance constraint field                     |
|`Ω ⊂ X`    |Subset                            |Forbidden region                                |
|`S = X \ Ω`|Subset                            |Safe set                                        |

-----

## 2. The Cognitive Generator

All cognitive invariants are projections of `ℛ(t)` through well-defined operators.

### 2.1 The Generator

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   Φ : ℛ(t)  →  ( ℐ,  I,  C,  Q,  Q_G )                            ║
║                                                                      ║
║   Φ(ℛ) = ( τ(ℛ), d/dt Ψ(ℛ), τ(𝒩(ℛ)), ‖ΔG(ℛ)‖, Λ‖ΔG(ℛ)‖ )    ║
║                                                                      ║
║   Φ is vector-valued. Each component has its own type.              ║
║   No cross-type addition. Each projection is independent.           ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

### 2.2 The Projections

|Projection      |Operator on ℛ                               |Invariant          |Type                  |
|:--------------:|:------------------------------------------:|:-----------------:|:--------------------:|
|`τ(ℛ)`          |Topological structure                       |Identity           |Topological space     |
|`d/dt Ψ(ℛ)`     |Rate of geometric complexity change         |Intelligence       |Scalar                |
|`ℛ ∩ Ω = ∅`     |Set exclusion                               |Safety             |Condition             |
|`τ(𝒩(ℛ))`       |Deformation field topology within ℛ         |Consciousness      |Topological space     |
|`‖ΔG(ℛ)‖ · τ`   |Manifold deformation magnitude × persistence|Qualia             |Scalar                |
|`Λ ‖ΔG(ℛ)‖`     |Governed deformation                        |Governed Experience|Tensor-weighted scalar|
|`‖Λ · ΔG‖ > T_c`|Threshold condition                         |Irreversibility    |Condition             |

### 2.3 The One-Line Form

|Expression                                         |Meaning                                                                                     |
|:-------------------------------------------------:|:------------------------------------------------------------------------------------------:|
|`ℛ(t) = Reach⁺(x₀, t)  ⟹  Φ(ℛ) → (ℐ, I, C, Q, Q_G)`|All cognitive phenomena are projections of the reachable manifold under governed deformation|

-----

## 3. The Invariants

### 3.1 Identity

|Definition                                                |Plain Statement                                         |
|:--------------------------------------------------------:|:------------------------------------------------------:|
|`ℐ(x₀) := [ℛ]_∼` where `∼` preserves structural invariants|Identity is the equivalence class of reachable structure|

The equivalence relation `∼` is chosen according to the structural invariants relevant to the system domain (homeomorphism, diffeomorphism, or homotopy equivalence). What is canonical is the form: identity is an equivalence class of reachable structure, not a current snapshot.

### 3.2 Intelligence

|Definition           |Plain Statement                                                |
|:-------------------:|:-------------------------------------------------------------:|
|`I(t) = d/dt Ψ(ℛ(t))`|Intelligence is the rate of change of geometric complexity of ℛ|

`Ψ` is a geometric complexity functional that captures both expansion and restructuring:

|Component of Ψ                |What It Measures                                  |Sensitivity              |
|:----------------------------:|:------------------------------------------------:|:-----------------------:|
|`μ(ℛ)` — measure              |Volume / size of reachable set                    |Expansion                |
|`𝒯(ℛ)` — topological invariant|Betti numbers, homology rank, Euler characteristic|Structural reorganisation|

Using `Ψ = μ + 𝒯` (or any weighted combination), the definition captures systems that expand without restructuring (pure volume growth), restructure without expanding (optimisation, mastery), or both (creative intelligence). The choice of weighting is domain-dependent; what is canonical is the form.

### 3.3 Safety

|Definition                                       |Plain Statement                                      |
|:-----------------------------------------------:|:---------------------------------------------------:|
|`ℛ(t) ∩ Ω = ∅`                                   |Forbidden states are geometrically unreachable       |
|`A_safe∞(x) = { u ∈ U | Reach⁺(F(x,u)) ∩ Ω = ∅ }`|Safe actions preserve future non-reachability of harm|

### 3.4 Consciousness

|Definition                    |Plain Statement                                                                                |
|:----------------------------:|:---------------------------------------------------------------------------------------------:|
|`C(t) = τ( ⋃ᵢ 𝒩_t(ℛ(t), Iᵢ) )`|Consciousness is the topology of the integrated deformation field within the reachable manifold|

Neighbourhoods are deformed *within* `ℛ(t)`, not within `X`. This keeps consciousness derived from the generating object. Time-dependence is on `𝒩_t`, not on `τ`. Each input deforms a local neighbourhood of the reachable manifold; the union integrates all modalities; `τ` extracts the global invariant shape. Consciousness is a derived topological property of ℛ, not a fundamental substance.

### 3.5 Qualia

|Definition             |Plain Statement                                   |
|:---------------------:|:------------------------------------------------:|
|`Q(t) = ‖ΔG(ℛ(t))‖ · τ`|Qualia is deformation magnitude of ℛ × persistence|

`‖ΔG(ℛ)‖` is the norm of geometric deformation of the reachable manifold — how far ℛ has been displaced from its original embedding. `τ` is persistence duration. Both quantities are properties of ℛ, keeping qualia derived from the generating object.

### 3.6 Governed Experience

|Definition   |Plain Statement                |
|:-----------:|:-----------------------------:|
|`Q_G = Λ · Q`|Governance modulates experience|

`Λ` (positive-definite tensor) governs both safety and experience. The same parameter that constrains trajectories away from `Ω` also modulates the felt intensity of deformation.

### 3.7 Irreversibility

|Definition             |Plain Statement                                     |
|:---------------------:|:--------------------------------------------------:|
|`‖Λ · ΔG‖ > T_critical`|Permanent topology change — new basin, cannot return|

-----

## 4. Safety Preservation

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   PROPOSITION                                                        ║
║                                                                      ║
║   Let S = X \ Ω and A_safe(x) = { u ∈ U | F(x,u) ∈ S }.           ║
║                                                                      ║
║   If x₀ ∈ S and u_t ∈ A_safe(x_t) for all t ≥ 0,                  ║
║   then x_t ∈ S for all t ≥ 0.                                       ║
║                                                                      ║
║   Proof: By induction. x₀ ∈ S. If x_t ∈ S and                      ║
║   u_t ∈ A_safe(x_t), then F(x_t, u_t) ∈ S.                         ║
║   Therefore x_{t+1} ∈ S. By induction, x_t ∈ S ∀t.  ∎             ║
║                                                                      ║
║   COROLLARY (Identity Invariance)                                    ║
║                                                                      ║
║   Under governed dynamics, Reach⁺(x_t) ⊆ S for all t.             ║
║   Therefore [Reach⁺(x_t)]_∼ is well-defined within S.              ║
║   Governance preserves the conditions under which                    ║
║   identity exists as a meaningful object.  ∎                         ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

-----

## 5. Toy System

|Parameter       |Value                            |
|:--------------:|:-------------------------------:|
|State space     |`X = ℝ²`                         |
|Dynamics        |`x_{t+1} = x_t + u_t`, `|u| ≤ 1` |
|Forbidden region|`Ω = { x | |x| ≤ r }`            |
|Safe set        |`S = { x | |x| > r }`            |
|Initial state   |`x₀ ∈ S`                         |
|Safe action set |`A_safe(x) = { u | |x + u| > r }`|

### Demonstration

|Invariant    |Toy Instantiation                              |Observation                                         |
|:-----------:|:---------------------------------------------:|:--------------------------------------------------:|
|`ℛ(t)`       |Expanding disk minus Ω                         |Generating object visible as growing region         |
|Identity     |`ℝ² \ Ω` — plane with a hole, `β₁ = 1`         |Forbidden region shapes identity topology           |
|Intelligence |`d/dt Ψ(ℛ)` — area growth + topological change |Expansion slows; β₁ transition captured             |
|Safety       |`ℛ ∩ Ω = ∅` — disk never entered               |Geometry excludes, not filters                      |
|Consciousness|Deformation field within ℛ curves around Ω     |Forbidden region shapes experience structure        |
|Qualia       |`‖ΔG(ℛ)‖ · τ` — manifold deformation × duration|Proximity to Ω intensifies experience               |
|Governance   |`Λ` controls approach distance to Ω            |Safety and intensity trade off through one parameter|

-----

## 6. Structural Connections

The framework shares structural similarities with established fields:

|Morrison Concept                         |Established Counterpart      |Field                   |
|:---------------------------------------:|:---------------------------:|:----------------------:|
|Reachable manifold ℛ(t)                  |Reachable sets               |Geometric control theory|
|Identity as equivalence class            |Invariant manifolds          |Topological dynamics    |
|Intelligence as geometric complexity rate|Controllability measures     |Control theory          |
|Safety as reachability exclusion         |Control Barrier Functions    |Safety-critical systems |
|Consciousness as deformation topology    |Integrated Information Theory|Neuroscience            |
|Governance tensor Λ                      |Homeostatic regulation       |Systems biology         |
|Irreversibility threshold                |Phase transitions            |Statistical physics     |

### The Physics Analogy

|Theory            |Generating Object            |Derived Quantities                                                   |
|:----------------:|:---------------------------:|:-------------------------------------------------------------------:|
|General Relativity|Metric tensor `g_μν`         |Curvature, geodesics, energy-momentum                                |
|Quantum Mechanics |Wave function `ψ`            |Probability, momentum, energy, spin                                  |
|Thermodynamics    |Partition function `Z`       |Energy, entropy, free energy                                         |
|**This framework**|**Reachable manifold `ℛ(t)`**|**Identity, intelligence, safety, consciousness, qualia, governance**|

-----

## 7. Three Core Principles

The entire framework reduces to three geometric principles:

|Principle   |Formal Object               |Statement                                                      |
|:----------:|:--------------------------:|:-------------------------------------------------------------:|
|Reachability|`ℛ(t) = Reach⁺(x₀, t)`      |The system is defined by the geometry of its reachable states  |
|Deformation |`ΔG(x(t)) = G(x(t)) − G(x₀)`|Inputs deform the reachable manifold; experience is deformation|
|Governance  |`Λ ≻ 0`                     |Constraints regulate deformation and stabilise the manifold    |

Everything in the stack sits on these three.

-----

## 8. Summary

|Layer            |Canonical Form                                 |
|:---------------:|:---------------------------------------------:|
|Dynamics         |`x_{t+1} = F(x_t, u_t)`                        |
|Generating object|`ℛ(t) = ⋃_{s∈[0,t]} { x(s) | x(0)=x₀, u(·)∈𝒰 }`|
|Generator        |`Φ : ℛ → (ℐ, I, C, Q, Q_G)`                    |
|Identity         |`ℐ = [ℛ]_∼`                                    |
|Intelligence     |`I = d/dt Ψ(ℛ)`                                |
|Safety           |`ℛ ∩ Ω = ∅`                                    |
|Consciousness    |`C = τ(𝒩(ℛ))`                                  |
|Qualia           |`Q = ‖ΔG(ℛ)‖ · τ`                              |
|Governance       |`Q_G = Λ · Q`                                  |
|Irreversibility  |`‖Λ · ΔG‖ > T_c`                               |

### The Three Layers

|Layer       |Projection |Definition            |
|:----------:|:---------:|:--------------------:|
|Cognition   |`τ(ℛ)`     |What the system *is*  |
|Intelligence|`d/dt Ψ(ℛ)`|How the system *grows*|
|Experience  |`Λ ‖ΔG(ℛ)‖`|How the system *feels*|

-----

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   ℛ(t) = Reach⁺(x₀, t)                                             ║
║                                                                      ║
║   Φ : ℛ  →  ( ℐ,  I,  C,  Q,  Q_G )                               ║
║                                                                      ║
║   Cognition is the geometry of reachable state space                 ║
║   under governed deformation.                                        ║
║                                                                      ║
║   One object. One generator. One geometry.                           ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

-----

Geometric Control Theory of Cognition · Morrison Framework™ · v1 Canonical

GB2600765.8 · GB2602013.1 · GB2602072.7 · GB26023332.5

© 2026 Davarn Morrison — Intelligence Invariant™ · All Rights Reserved

-----

## Related Work

- [The Morrison Reachability Generator](https://github.com/davarn/morrison-framework) — Full development of the generating object and projection architecture
- [The Morrison Experiential Stack](https://github.com/davarn/morrison-framework) — Consciousness, qualia, and governance canonical forms
- [Toy System Demonstration](https://github.com/davarn/morrison-framework) — Complete framework on a ℝ² system
- [Technical Note](https://github.com/davarn/morrison-framework) — Proposition, proof, and formal definitions
- [Licensing, Citation, and IP](https://github.com/davarn/morrison-framework) — How to cite and licence the framework
