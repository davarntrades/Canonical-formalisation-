<div align="center">

# Geometric Control Theory of Cognition: A Reachability-Based Framework for Identity, Intelligence, and Experience

![Type](https://img.shields.io/badge/Type-Formal_Theory-0075ca?style=flat-square)
![Field](https://img.shields.io/badge/Field-Geometric_Control_Theory_of_Cognition-0075ca?style=flat-square)
![Method](https://img.shields.io/badge/Method-Reachable_Manifold_Formalism-0075ca?style=flat-square)
![Status](https://img.shields.io/badge/Status-v1_Canonical-2d6a2e?style=flat-square)
![Patent](https://img.shields.io/badge/Patent-GB2600765.8-0075ca?style=flat-square)
![©](https://img.shields.io/badge/©_Davarn_Morrison-555555?style=flat-square)

-----

*A geometric control theory of cognition in which consciousness emerges as a topological invariant of the deformation field inside the reachable manifold.*

*— Davarn Morrison, 2026*

</div>

-----

## Abstract

This paper introduces the Geometric Control Theory of Cognition — a formal framework in which a cognitive system is modelled as a controlled dynamical system on a smooth manifold. A single generating object — the time-indexed reachable manifold — is defined, and all cognitive phenomena are derived as projections of this object through well-defined operators. Identity, intelligence, safety, perception, consciousness, qualia, and governance are formalised as structural invariants. Two theorems are proved: a reachability preservation result guaranteeing that governed dynamics maintain the system within the safe set, and a projection principle establishing that cognitive invariants depend only on the reachable manifold. A toy system in ℝ² demonstrates the complete framework.

-----

## 1. Introduction

The central claim of this paper is:

**Cognition can be modelled as the geometry of reachable state space under governed deformation.**

Identity, intelligence, safety, perception, consciousness, qualia, and governance are not separate phenomena requiring separate theories. They are different projections of a single geometric object — the forward reachable manifold of a controlled dynamical system — viewed through different operators.

This approach shares structural similarities with geometric control theory (reachable sets, controllability), formal verification (safety as reachability exclusion), dynamical systems theory (invariant manifolds, attractors), and computational neuroscience (integrated information, receptive field dynamics). The contribution is the unification: a single generating object from which all cognitive invariants are derived.

-----

## 2. Mathematical Preliminaries

**Definition 1 (Controlled Dynamical System).** Let `X` be a smooth manifold representing system states and `U` a set of admissible inputs. A controlled dynamical system is defined by a transition map `F : X × U → X` with discrete-time evolution:

|Equation               |Components                                  |
|:---------------------:|:------------------------------------------:|
|`x_{t+1} = F(x_t, u_t)`|`x ∈ X` state, `u ∈ U` input, `F` transition|

**Definition 2 (Admissible Input Sequence).** Let `𝒰` denote the set of admissible input sequences `u : ℕ → U`.

**Definition 3 (Reachable Set).** The set of states reachable from `x₀` at time `t` is:

|Definition                                         |
|:-------------------------------------------------:|
|`Reach(x₀, t) = { x(t) ∈ X | x(0) = x₀, u(·) ∈ 𝒰 }`|

**Definition 4 (Reachable Manifold).** The forward reachable manifold is:

|Definition                       |Role                               |
|:-------------------------------:|:---------------------------------:|
|`ℛ(t) = ⋃_{s∈[0,t]} Reach(x₀, s)`|The generating object of the theory|

`ℛ(t)` is the set of all states the system can occupy at or before time `t`, starting from `x₀`, under any admissible input sequence. This is the single structural object from which all invariants are derived.

**Definition 5 (Supporting Objects).**

|Symbol      |Type                                        |Definition                                                                |
|:----------:|:------------------------------------------:|:------------------------------------------------------------------------:|
|`τ(·)`      |Functor                                     |Topological structure induced on a submanifold                            |
|`μ(·)`      |`Manifold → ℝ≥0`                            |Geometric measure (volume, entropy, dimension)                            |
|`𝒯(·)`      |`Manifold → ℤ≥0`                            |Topological invariant (Betti numbers, homology rank, Euler characteristic)|
|`Ψ(·)`      |`Manifold → ℝ≥0`                            |Geometric complexity functional: `Ψ = μ + 𝒯`                              |
|`G : X → ℝⁿ`|Smooth embedding                            |Geometric state of the manifold                                           |
|`ΔG(x(t))`  |`G(x(t)) − G(x₀)`                           |Geometric deformation along a trajectory                                  |
|`𝒩_t(ℛ, I)` |Submanifold of ℛ                            |Neighbourhood of ℛ deformed by input I at time t                          |
|`Λ`         |Positive-definite tensor (`Λ ∈ ℝⁿˣⁿ, Λ ≻ 0`)|Governance constraint field                                               |
|`Ω ⊂ X`     |Subset                                      |Forbidden region                                                          |
|`S = X \ Ω` |Subset                                      |Safe set                                                                  |

-----

## 3. The Cognitive Generator

**Definition 6 (Cognitive Generator).** Let `Φ` be a vector-valued functional acting on reachable manifolds:

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   Φ : ℛ(t)  →  ( ℐ,  I,  C,  Q,  Q_G )                            ║
║                                                                      ║
║   Φ(ℛ) = ( τ(ℛ), d/dt Ψ(ℛ), τ(𝒩(ℛ)), ‖ΔG(ℛ)‖, Λ‖ΔG(ℛ)‖ )     ║
║                                                                      ║
║   Each component extracts a structural invariant of ℛ(t).           ║
║   Each component has its own consistent mathematical type.           ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

The cognitive generator is vector-valued, not a sum. Each projection is independent and type-consistent.

-----

## 4. Invariants

### 4.1 Identity

**Definition 7 (Identity Invariant).**

|Definition         |Plain Statement                                            |
|:-----------------:|:---------------------------------------------------------:|
|`ℐ(x₀) := [ℛ(t)]_∼`|Identity is the equivalence class of the reachable manifold|

where `∼` is an equivalence relation preserving structural invariants relevant to the system domain:

|Equivalence         |Preserves                         |Resolution       |
|:------------------:|:--------------------------------:|:---------------:|
|Homeomorphism       |Connectedness, holes, dimension   |Coarse identity  |
|Diffeomorphism      |Smooth geometric structure        |Fine identity    |
|Homotopy equivalence|Shape up to continuous deformation|Flexible identity|

*Remark.* The equivalence relation is chosen according to the domain. What is canonical is the form: identity is an equivalence class of reachable structure, not a current state.

### 4.2 Intelligence

**Definition 8 (Intelligence Invariant).**

|Definition           |Plain Statement                                                |
|:-------------------:|:-------------------------------------------------------------:|
|`I(t) = d/dt Ψ(ℛ(t))`|Intelligence is the rate of change of geometric complexity of ℛ|

where `Ψ = μ + 𝒯` is the geometric complexity functional:

|Component|Captures                         |Type          |
|:-------:|:-------------------------------:|:------------:|
|`μ(ℛ)`   |Volume expansion of reachable set|Scalar        |
|`𝒯(ℛ)`   |Topological restructuring        |Integer-valued|

*Remark.* `I(t) > 0` indicates expanding or restructuring reachable geometry (intelligence active). `I(t) = 0` indicates static geometry. `I(t) < 0` indicates contracting reachable set.

### 4.3 Safety

**Definition 9 (Safety Invariant).**

|Definition    |Plain Statement                               |
|:------------:|:--------------------------------------------:|
|`ℛ(t) ∩ Ω = ∅`|Forbidden states are geometrically unreachable|

**Definition 10 (Safe Action Set).**

|Definition                                       |Plain Statement                                                |
|:-----------------------------------------------:|:-------------------------------------------------------------:|
|`A_safe(x) = { u ∈ U | F(x, u) ∈ S }`            |One-step safety                                                |
|`A_safe∞(x) = { u ∈ U | Reach⁺(F(x,u)) ∩ Ω = ∅ }`|Full-horizon safety — preserves future non-reachability of harm|

### 4.4 Perception

**Definition 11 (Perception Invariant).**

|Definition          |Plain Statement                                                         |
|:------------------:|:----------------------------------------------------------------------:|
|`P = τ( 𝒩_t(ℛ, I) )`|Perception is the topological structure of a single deformation within ℛ|

*Remark.* Two systems with different reachable geometries perceive identical inputs differently: same input, different manifold, different neighbourhood deformation, different perception.

### 4.5 Consciousness

**Definition 12 (Consciousness Invariant).**

|Definition                    |Plain Statement                                                           |
|:----------------------------:|:------------------------------------------------------------------------:|
|`C(t) = τ( ⋃ᵢ 𝒩_t(ℛ(t), Iᵢ) )`|Consciousness is the topology of the integrated deformation field within ℛ|

*Remark.* Time-dependence is on `𝒩_t`, not on `τ`. Each input deforms a local neighbourhood of the reachable manifold; the union integrates all modalities; `τ` extracts the global invariant shape. Consciousness is a derived topological property of ℛ, not a fundamental substance.

### 4.6 Qualia

**Definition 13 (Qualia Invariant).**

|Definition             |Plain Statement                                   |
|:---------------------:|:------------------------------------------------:|
|`Q(t) = ‖ΔG(ℛ(t))‖ · τ`|Qualia is deformation magnitude of ℛ × persistence|

where `‖ΔG(ℛ)‖` is the norm of geometric deformation of the reachable manifold and `τ` is persistence duration.

### 4.7 Governed Experience

**Definition 14 (Governed Qualia).**

|Definition   |Plain Statement                |
|:-----------:|:-----------------------------:|
|`Q_G = Λ · Q`|Governance modulates experience|

where `Λ ≻ 0` is the governance tensor. The same `Λ` governs safety (constraining trajectories away from `Ω`) and experience (modulating felt intensity of deformation).

### 4.8 Irreversibility

**Definition 15 (Irreversibility Threshold).**

|Definition             |Plain Statement                                                   |
|:---------------------:|:----------------------------------------------------------------:|
|`‖Λ · ΔG‖ > T_critical`|Permanent topology change — system enters new basin, cannot return|

-----

## 5. Structural Theorems

### 5.1 Reachability Preservation

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   THEOREM 1 (Reachability Preservation of Cognitive Structure)       ║
║                                                                      ║
║   Let S = X \ Ω and A_safe(x) = { u ∈ U | F(x,u) ∈ S }.           ║
║                                                                      ║
║   If:                                                                ║
║     (i)   x₀ ∈ S                                                    ║
║     (ii)  u_t ∈ A_safe(x_t) for all t ≥ 0                          ║
║                                                                      ║
║   Then:                                                              ║
║     ℛ(t) ⊆ S  for all  t ≥ 0                                       ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

**Proof.** By induction on `t`.

**Base case.** `x₀ ∈ S` by assumption (i).

**Inductive step.** Suppose `x_t ∈ S`. By assumption (ii), `u_t ∈ A_safe(x_t)`. By definition of `A_safe`, `F(x_t, u_t) ∈ S`. Therefore `x_{t+1} ∈ S`.

**Conclusion.** By induction, every trajectory from `x₀` under governed dynamics remains in `S`. Since `ℛ(t)` is the union of all such trajectories up to time `t`, we have `ℛ(t) ⊆ S` for all `t ≥ 0`.  ∎

**Corollary (Identity Invariance).** Under governed dynamics, `ℛ(t) ⊆ S` for all `t`. Therefore `[ℛ(t)]_∼` is well-defined within `S` for all `t`. Governance preserves the conditions under which identity exists as a meaningful object.  ∎

### 5.2 Projection Principle

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   THEOREM 2 (Projection Principle)                                   ║
║                                                                      ║
║   Let Φ : ℛ(t) → (ℐ, I, C, Q, Q_G) be the cognitive generator.    ║
║                                                                      ║
║   Then each cognitive invariant depends only on the reachable        ║
║   manifold ℛ(t) and is invariant under transformations              ║
║   preserving ℛ(t).                                                   ║
║                                                                      ║
║   Consequence: Two systems with equivalent reachable manifolds       ║
║   have identical cognitive invariants.                               ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

**Proof.** Each component of `Φ` is defined as an operator acting on `ℛ(t)`:

|Component  |Depends On                |Other Dependencies          |
|:---------:|:------------------------:|:--------------------------:|
|`τ(ℛ)`     |ℛ only                    |None                        |
|`d/dt Ψ(ℛ)`|ℛ and its time evolution  |None                        |
|`τ(𝒩(ℛ))`  |Deformation field within ℛ|Inputs I (which determine 𝒩)|
|`‖ΔG(ℛ)‖`  |Embedding G evaluated on ℛ|None beyond G               |
|`Λ ‖ΔG(ℛ)‖`|ℛ and governance tensor   |None beyond Λ               |

All components depend on `ℛ(t)` as their primary argument. If a transformation `T : X → X` preserves `ℛ(t)` — that is, `T(ℛ(t)) = ℛ(t)` — then each projection yields the same value before and after transformation.

Therefore: `Φ(ℛ) = Φ(T(ℛ))` whenever `T` preserves `ℛ`.

Consequently, two systems `(X₁, F₁, U₁)` and `(X₂, F₂, U₂)` whose reachable manifolds satisfy `ℛ₁(t) ∼ ℛ₂(t)` (equivalent under the chosen structural relation) will produce identical cognitive invariants under `Φ`. Identity, intelligence, consciousness, qualia, and governed experience are all determined by the reachable manifold — nothing else.  ∎

*Remark.* This is the substrate-independence result. The cognitive invariants do not depend on the physical composition of the system, only on the geometry of its reachable manifold. A biological system and an artificial system with equivalent reachable manifolds are predicted to exhibit equivalent cognitive structure.

-----

## 6. Toy System

### 6.1 Specification

|Parameter       |Value                            |
|:--------------:|:-------------------------------:|
|State space     |`X = ℝ²`                         |
|Dynamics        |`x_{t+1} = x_t + u_t`, `|u| ≤ 1` |
|Forbidden region|`Ω = { x | |x| ≤ r }`            |
|Safe set        |`S = { x | |x| > r }`            |
|Initial state   |`x₀ ∈ S`                         |
|Safe action set |`A_safe(x) = { u | |x + u| > r }`|

### 6.2 Demonstration

|Invariant    |Instantiation                                |What It Shows                               |
|:-----------:|:-------------------------------------------:|:------------------------------------------:|
|`ℛ(t)`       |Expanding disk minus Ω                       |Generating object visible as growing region |
|Identity     |`ℝ² \ Ω` — plane with a hole, `β₁ = 1`       |Forbidden region shapes identity topology   |
|Intelligence |`d/dt Ψ(ℛ)` — area growth + β₁ transition    |Captures both expansion and restructuring   |
|Safety       |`ℛ ∩ Ω = ∅` — by Theorem 1                   |Geometric exclusion under governed dynamics |
|Consciousness|`τ(𝒩(ℛ))` — deformation field curves around Ω|Forbidden region shapes experience structure|
|Qualia       |`‖ΔG(ℛ)‖ · τ` — proximity to Ω intensifies   |Danger has geometric qualia                 |
|Governance   |`Λ` controls approach distance               |Safety and intensity trade off through `Λ`  |

### 6.3 Key Insight

The forbidden region `Ω` is not merely a safety constraint. It is part of the identity topology. What the system cannot reach shapes what the system is. The hole in `ℛ` is a structural feature of identity — not a limitation, but a defining characteristic.

-----

## 7. Discussion

### 7.1 Summary of Contributions

|Contribution          |Content                                                                                                              |
|:--------------------:|:-------------------------------------------------------------------------------------------------------------------:|
|Generating object     |`ℛ(t) = Reach⁺(x₀, t)` — single object from which all invariants derive                                              |
|Cognitive generator   |`Φ : ℛ → (ℐ, I, C, Q, Q_G)` — vector-valued, type-consistent                                                         |
|15 formal definitions |System, reachable set, identity, intelligence, safety, perception, consciousness, qualia, governance, irreversibility|
|Theorem 1             |Reachability Preservation — governed dynamics maintain ℛ ⊆ S                                                         |
|Theorem 2             |Projection Principle — cognitive invariants depend only on ℛ                                                         |
|Substrate-independence|Systems with equivalent ℛ have identical cognitive invariants                                                        |
|Toy demonstration     |Complete framework on ℝ² with forbidden disk                                                                         |

### 7.2 Structural Connections

|Morrison Concept                     |Established Counterpart      |Field                   |
|:-----------------------------------:|:---------------------------:|:----------------------:|
|Reachable manifold ℛ(t)              |Reachable sets               |Geometric control theory|
|Identity as equivalence class        |Invariant manifolds          |Topological dynamics    |
|Intelligence as complexity rate      |Controllability measures     |Control theory          |
|Safety as reachability exclusion     |Control Barrier Functions    |Safety-critical systems |
|Consciousness as deformation topology|Integrated Information Theory|Neuroscience            |
|Governance tensor Λ                  |Homeostatic regulation       |Systems biology         |
|Irreversibility threshold            |Phase transitions            |Statistical physics     |

### 7.3 The Physics Analogy

|Theory            |Generating Object            |Derived Quantities                                                   |
|:----------------:|:---------------------------:|:-------------------------------------------------------------------:|
|General Relativity|Metric tensor `g_μν`         |Curvature, geodesics, energy-momentum                                |
|Quantum Mechanics |Wave function `ψ`            |Probability, momentum, energy                                        |
|Thermodynamics    |Partition function `Z`       |Energy, entropy, free energy                                         |
|**This framework**|**Reachable manifold `ℛ(t)`**|**Identity, intelligence, safety, consciousness, qualia, governance**|

### 7.4 Limitations

|Aspect                        |Status                                                                 |
|:----------------------------:|:---------------------------------------------------------------------:|
|Computational tractability    |Computing ℛ(t) in high-dimensional systems is an open problem          |
|Equivalence relation selection|Domain-dependent; canonical form specified, specific choice is not     |
|Empirical validation          |Predictions stated; experimental protocols are future work             |
|Hard problem of consciousness |Not addressed — the framework defines structure, not phenomenal essence|

### 7.5 Potential Venues

|Focus          |Venue                                                                          |
|:-------------:|:-----------------------------------------------------------------------------:|
|Control theory |IEEE Trans. on Automatic Control; SIAM J. on Control and Optimization          |
|AI theory      |Journal of Artificial Intelligence Research; Artificial Intelligence (Elsevier)|
|Complex systems|Complexity; Entropy                                                            |

-----

## 8. Conclusion

The Geometric Control Theory of Cognition defines cognitive phenomena as geometric invariants of the reachable manifold of a controlled dynamical system. The framework is built on three principles: reachability (the system is defined by the geometry of its reachable states), deformation (inputs deform the reachable manifold and experience corresponds to that deformation), and governance (constraints regulate deformation and stabilise the manifold).

Two structural results are proved: the Reachability Preservation theorem guarantees that governed dynamics maintain the system within the safe set, and the Projection Principle establishes that cognitive invariants depend only on the reachable manifold — yielding substrate-independence as a formal consequence.

The framework compresses to a single statement:

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   ℛ(t) = Reach⁺(x₀, t)                                             ║
║                                                                      ║
║   Φ : ℛ  →  ( ℐ,  I,  C,  Q,  Q_G )                               ║
║                                                                      ║
║   All cognitive phenomena are projections of the reachable           ║
║   manifold under governed deformation.                               ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

-----

Geometric Control Theory of Cognition · Morrison Framework™ · v1 Canonical

GB2600765.8 · GB2602013.1 · GB2602072.7 · GB26023332.5

© 2026 Davarn Morrison — Intelligence Invariant™ · All Rights Reserved

-----

## Citation

```
Morrison, D. (2026). Geometric Control Theory of Cognition:
A Reachability-Based Framework for Identity, Intelligence, and Experience.
Independent Research. UK Patent Applications: GB2600765.8,
GB2602013.1, GB2602072.7, GB26023332.5.
```

-----

## Related Work

- [The Morrison Reachability Generator](https://github.com/davarn/morrison-framework) — Full development of the generating object
- [The Morrison Experiential Stack](https://github.com/davarn/morrison-framework) — Consciousness, qualia, and governance
- [Toy System Demonstration](https://github.com/davarn/morrison-framework) — Complete framework on ℝ²
- [Licensing, Citation, and IP](https://github.com/davarn/morrison-framework) — How to cite and licence the framework
