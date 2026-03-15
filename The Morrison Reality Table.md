<div align="center">

# The Morrison Reality Table — A Unified Expression of the Framework

![Type](https://img.shields.io/badge/Type-Unified_Expression-0075ca?style=flat-square)
![Field](https://img.shields.io/badge/Field-Geometric_Control_Theory_of_Cognition-0075ca?style=flat-square)
![Method](https://img.shields.io/badge/Method-Single_Generating_Object-0075ca?style=flat-square)
![Status](https://img.shields.io/badge/Status-v1_Canonical-2d6a2e?style=flat-square)
![Patent](https://img.shields.io/badge/Patent-GB2600765.8-0075ca?style=flat-square)
![©](https://img.shields.io/badge/©_Davarn_Morrison-555555?style=flat-square)

-----

*Reality is the structured set of invariants induced by the reachable futures of a system.*

*— Davarn Morrison, 2026*

</div>

-----

## The Generating Object

ℛ(t) = Reach⁺(x₀, t)

The reachable manifold. All states the system can access up to time t. This is the single object from which everything is derived.

-----

## The Morrison Operator

Φ : ℛ(t) → (ℐ, I, 𝒮, P, C, Q, Q_G, Ξ, 𝒯)

Each component is a projection of the reachable geometry:

|   |Projection                                 |Invariant          |Meaning                                                                                                                                                              |
|:-:|:-----------------------------------------:|:-----------------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|ℐ  |`[ℛ(t)]_∼`                                 |Identity           |Equivalence class of reachable structure, where `∼` is a topological equivalence relation (homeomorphism, homotopy equivalence, or diffeomorphism — chosen by domain)|
|I  |`d/dt μ(ℛ(t))`                             |Intelligence       |Rate of expansion of reachable geometry                                                                                                                              |
|𝒮  |`𝟙{ ℛ(t) ∩ Ω = ∅ }`                        |Safety             |Forbidden states unreachable                                                                                                                                         |
|P  |`τ(𝒩_t(X, I))`                             |Perception         |Topology of single-input deformation                                                                                                                                 |
|C  |`τ(⋃ᵢ 𝒩_t(X, Iᵢ))`                         |Consciousness      |Topology of integrated deformation field                                                                                                                             |
|Q  |`‖ΔGᵢ‖ · τᵢ`                               |Qualia             |Deformation magnitude × persistence                                                                                                                                  |
|Q_G|`Λ · Q`                                    |Governed Experience|Governance modulates qualia                                                                                                                                          |
|Ξ  |`𝟙{ ‖Λ · ΔG‖ > T_critical }`               |Irreversibility    |Separatrix crossed — permanent basin change                                                                                                                          |
|𝒯  |`𝟙{ ∃k: H_k(Reach(X_t)) ≇ H_k(Reach(X₀)) }`|Truth              |Genuine structural deformation detected                                                                                                                              |

One generating object. Nine projections. One geometry.

-----

## Formal Definitions of Core Operators

-----

### 1. The Reachable Manifold

Let `X ⊆ ℝⁿ` be the system state space. Let `u(t) ∈ 𝒰` be admissible control inputs. Let the system dynamics be:

|Form           |Equation               |
|:-------------:|:---------------------:|
|Continuous-time|`ẋ(t) = f(x(t), u(t))` |
|Discrete-time  |`x_{t+1} = F(x_t, u_t)`|

with initial condition `x(0) = x₀`.

The forward reachable set is defined as:

|Symbol                |Definition                          |
|:--------------------:|:----------------------------------:|
|`ℛ(t) = Reach⁺(x₀, t)`|`{ x(t) ∈ X | x(0) = x₀, u(·) ∈ 𝒰 }`|

This object is the reachable manifold. It is the generating object of the Morrison Framework.

**The Measure μ.** Let `μ : ℛ → ℝ⁺` be a measure over the reachable manifold. The choice of μ is domain-dependent:

|Measure                  |What It Captures              |Use Case                           |
|:-----------------------:|:----------------------------:|:---------------------------------:|
|Lebesgue measure (volume)|Size of reachable region      |Spatial systems, navigation        |
|Hausdorff measure        |Dimension-sensitive size      |Fractal or irregular reachable sets|
|Entropy proxy            |Information-theoretic capacity|Neural networks, latent spaces     |
|Dimensional capacity     |Effective dimensionality of ℛ |High-dimensional systems           |

What is canonical is the form `I(t) = d/dt μ(ℛ(t))`. The choice of μ is a modelling decision.

**The Geometric Embedding G.** Let `G : X → ℝⁿ` be a smooth embedding of the state manifold into geometric representation space. Deformation is defined as `ΔG(x(t)) = G(x(t)) − G(x₀)` — the displacement of the embedded state from its initial position. `‖ΔG‖` is the scalar norm of this displacement.

-----

### 2. The Morrison Operator Φ

The Morrison operator `Φ` is a vector-valued functional acting on reachable manifolds:

|Definition                                |Type                    |
|:----------------------------------------:|:----------------------:|
|`Φ : ℛ(t) ↦ (ℐ, I, 𝒮, P, C, Q, Q_G, Ξ, 𝒯)`|Vector-valued functional|

Each component is a projection of the reachable geometry:

|Component|Expression                                 |Type                                                     |
|:-------:|:-----------------------------------------:|:-------------------------------------------------------:|
|`ℐ`      |`[ℛ(t)]_∼`                                 |Topological space (`∼` = topological equivalence; see §1)|
|`I`      |`d/dt μ(ℛ(t))`                             |Scalar                                                   |
|`𝒮`      |`𝟙{ ℛ(t) ∩ Ω = ∅ }`                        |Boolean                                                  |
|`P`      |`τ(𝒩_t(X, I))`                             |Topological space                                        |
|`C`      |`τ(⋃ᵢ 𝒩_t(X, Iᵢ))`                         |Topological space                                        |
|`Q`      |`‖ΔGᵢ‖ · τᵢ`                               |Scalar                                                   |
|`Q_G`    |`Λ · Q`                                    |Tensor-weighted scalar                                   |
|`Ξ`      |`𝟙{ ‖Λ · ΔG‖ > T_critical }`               |Boolean                                                  |
|`𝒯`      |`𝟙{ ∃k: H_k(Reach(X_t)) ≇ H_k(Reach(X₀)) }`|Boolean                                                  |

`Φ` maps reachable manifolds to system invariants.

-----

### 3. The Topological Structure Operator τ

The operator `τ(·)` maps geometric neighbourhoods to their induced topology:

|Definition      |Components                                                     |
|:--------------:|:-------------------------------------------------------------:|
|`τ : 𝓜 → (𝓜, 𝒯)`|`𝓜` is a manifold; `𝒯` is the topology induced on that manifold|

`τ(𝒩_t(X, I))` returns the topological structure of the state-space neighbourhood after deformation by input `I`. In the Morrison Framework this corresponds to perception.

-----

### 4. The Input-Deformed Neighbourhood 𝒩_t(X, I)

Let `X` be the system state manifold. An input signal `I(t)` induces a deformation field:

|Symbol              |Type       |Definition                                          |
|:------------------:|:---------:|:--------------------------------------------------:|
|`φ_I : X → X`       |Smooth map |Deformation field induced by input I                |
|`U ⊆ X`             |Open subset|Local neighbourhood of current state                |
|`𝒩_t(X, I) = φ_I(U)`|Submanifold|Portion of state space reshaped by input I at time t|

-----

### 5. The Governance Tensor Λ

The governance operator `Λ` is a positive-definite tensor field:

|Symbol       |Type             |Definition                 |
|:-----------:|:---------------:|:-------------------------:|
|`Λ : ℝⁿ → ℝⁿ`|`Λ ∈ ℝⁿˣⁿ, Λ ≻ 0`|Governance constraint field|

Governed experience:

|Equation     |Meaning                                  |
|:-----------:|:---------------------------------------:|
|`Q_G = Λ · Q`|Governance weights deformation magnitudes|

|Λ Level|Eigenvalue Condition  |System State                          |
|:-----:|:--------------------:|:------------------------------------:|
|High Λ |All eigenvalues large |Stability — structure absorbs input   |
|Low Λ  |Some eigenvalues small|Fragility — input overwhelms structure|
|Λ → 0  |Minimum eigenvalue → 0|Collapse — no governance              |

-----

### 6. Existence of the Morrison Operator

For any dynamical system satisfying:

|Condition              |Requirement                       |
|:---------------------:|:--------------------------------:|
|Well-defined dynamics  |`f(x, u)` is continuous           |
|Compact control space  |`𝒰` is bounded                    |
|Continuous trajectories|Solutions exist and are continuous|

the reachable set `ℛ(t)` exists. Since each component of `Φ(ℛ(t))` is defined as a measurable functional of `ℛ(t)`, the Morrison operator exists whenever the reachable manifold exists.

`Φ` is well-defined for all dynamical systems with well-defined reachability.

-----

## Concrete System Examples

### Robot Controller

|Property    |Specification                                     |
|:----------:|:------------------------------------------------:|
|State space |`X = (x, y, θ)` — position and heading            |
|`ℛ(t)`      |All robot poses reachable from initial state      |
|Safety      |`ℛ(t) ∩ Ω = ∅` — collision states unreachable     |
|Identity    |`[ℛ]_∼` — topology of reachable configurations    |
|Intelligence|`d/dt μ(ℛ)` — rate of expansion of navigable space|

### Neural Network

|Property    |Specification                                                  |
|:----------:|:-------------------------------------------------------------:|
|State space |`X = ℝᵈ` — hidden-state dimension                              |
|`ℛ(t)`      |Set of hidden states accessible during inference               |
|Perception  |`P = τ(𝒩_t(X, I))` — local deformation from input embeddings   |
|Intelligence|`d/dt μ(ℛ)` — rate at which new hidden states become accessible|

### LLM Latent Geometry

|Property   |Specification                                            |
|:---------:|:-------------------------------------------------------:|
|State space|`X = ℝᵈ` — latent representation space                   |
|`Ω`        |Hallucination regions — unstable latent basins           |
|Safety     |`ℛ(t) ∩ Ω = ∅` — generation cannot enter unstable regions|
|Qualia     |`‖ΔG‖ · τ` — magnitude of latent deformation under input |

-----

## Theorem (Φ-Invariance Under Reachability-Preserving Transformations)

**Theorem.** Let `T : X → X` be a smooth bijection that preserves the reachable manifold and its induced topology, measure, and governance structure — that is, `T(ℛ(t)) = ℛ(t)`, `μ(T(ℛ)) = μ(ℛ)`, and `Λ` is invariant under `T`. Then all components of the Morrison operator are preserved: `Φ(T(ℛ(t))) = Φ(ℛ(t))`.

**Proof.** Under the stated conditions, each component of `Φ` is preserved:

|Component          |Depends On                |Why Preserved                                         |
|:-----------------:|:------------------------:|:----------------------------------------------------:|
|`[ℛ]_∼`            |Topology of ℛ             |T preserves ℛ and its induced topology                |
|`d/dt μ(ℛ)`        |Measure of ℛ              |T preserves μ by assumption                           |
|`𝟙{ℛ ∩ Ω = ∅}`     |Set intersection          |T preserves ℛ; intersection unchanged                 |
|`τ(𝒩(ℛ))`          |Deformation field within ℛ|Topology of deformation preserved under T             |
|`‖ΔG(ℛ)‖ · τ`      |Embedding norm on ℛ       |Geometry of ℛ preserved                               |
|`Λ · Q`            |Governance × qualia       |Λ invariant under T; Q preserved                      |
|`𝟙{‖Λ · ΔG‖ > T_c}`|Threshold on deformation  |Both Λ and ΔG preserved                               |
|`𝟙{∃k: H_k ≇ H_k}` |Homology of ℛ             |Homology is a topological invariant; preserved under T|

Since every component is preserved under the stated conditions, `Φ(T(ℛ)) = Φ(ℛ)`. ∎

**Corollary (Substrate-Independence).** Two systems `(X₁, F₁, U₁)` and `(X₂, F₂, U₂)` whose reachable manifolds are equivalent — `ℛ₁(t) ∼ ℛ₂(t)` under topology, measure, and governance — have identical cognitive invariants: `Φ(ℛ₁) = Φ(ℛ₂)`. The physical substrate is irrelevant. Only the geometry of reachable futures determines cognition. ∎

-----

## How Reachability Generates Everything

|What ℛ Generates   |How                                         |
|:-----------------:|:------------------------------------------:|
|Identity           |Reachability generates the equivalence class|
|Intelligence       |Reachability expansion is measured          |
|Safety             |Reachability is constrained                 |
|Perception         |Reachability is locally deformed            |
|Consciousness      |Integrated deformation of reachability      |
|Qualia             |Persistent deformation of reachability      |
|Governed Experience|Governance shapes deformation               |
|Irreversibility    |Critical deformation crosses separatrix     |
|Truth              |Topological change in reachability          |

-----

## The Physics Comparison

|Theory                 |Generating Object            |Derived Quantities                                                                                       |
|:---------------------:|:---------------------------:|:-------------------------------------------------------------------------------------------------------:|
|General Relativity     |Metric tensor `g_μν`         |Curvature, geodesics, energy-momentum                                                                    |
|Quantum Mechanics      |Wave function `ψ`            |Probability, momentum, energy, spin                                                                      |
|Thermodynamics         |Partition function `Z`       |Energy, entropy, free energy, phase transitions                                                          |
|**Morrison Framework™**|**Reachable manifold `ℛ(t)`**|**Identity, intelligence, safety, perception, consciousness, qualia, governance, irreversibility, truth**|

-----

The Morrison Reality Table · Geometric Control Theory of Cognition · Morrison Framework™

GB2600765.8 · GB2602013.1 · GB2602072.7 · GB26023332.5

© 2026 Davarn Morrison — All Rights Reserved

-----

## Related Work

- [Geometric Control Theory of Cognition — Formal Paper](https://github.com/davarn/morrison-framework) — The base theory
- [Intelligence as Future-Opening Power](https://github.com/davarn/morrison-framework) — What the intelligence equation means
- [Orthogonal Decomposition of Consciousness and Language](https://github.com/davarn/morrison-framework) — C ⊥ L formalised
- [Morrison Reachability Guard — Architecture](https://github.com/davarn/morrison-framework) — The product form
- [Morrison Reachability Guard — Prototype](https://github.com/davarn/morrison-framework) — Working Python demo
- [Licensing, Citation, and IP](https://github.com/davarn/morrison-framework) — How to cite and licence
