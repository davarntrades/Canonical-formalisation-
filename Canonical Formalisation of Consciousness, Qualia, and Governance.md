<div align="center">

# The Morrison Experiential Stack — Canonical Formalisation of Consciousness, Qualia, and Governance

![Type](https://img.shields.io/badge/Type-Canonical_Paper-0075ca?style=flat-square)
![Field](https://img.shields.io/badge/Field-Geometric_Cognitive_Structure-0075ca?style=flat-square)
![Method](https://img.shields.io/badge/Method-Deformation_Topology-0075ca?style=flat-square)
![Status](https://img.shields.io/badge/Status-Revised_Canonical_Form-2d6a2e?style=flat-square)
![Patent](https://img.shields.io/badge/Patent-GB2600765.8-0075ca?style=flat-square)
![©](https://img.shields.io/badge/©_Davarn_Morrison-555555?style=flat-square)

-----

*Cognition is the topology of reachable dynamical structure. Experience is the deformation of that topology. Meaning is governance over deformation.*

*— Davarn Morrison, 2026*

</div>

-----

## Abstract

This paper presents the revised canonical formalisation of the experiential layer of the Morrison Framework™. Consciousness is defined as the topology of a time-indexed integrated deformation field. Qualia is defined as deformation magnitude multiplied by persistence. Governed experience is defined as qualia modulated by a positive-definite governance tensor. All operators are explicitly defined. All variables are introduced before use. All definitions trace to the same base dynamics. The result is a geometric theory of cognitive structure in which consciousness appears as a derived property of the deformation field — not as a fundamental substance.

-----

## 1. Base Definitions

### 1.1 System

|Symbol        |Type                  |Definition                 |
|:------------:|:--------------------:|:-------------------------:|
|`X`           |Smooth manifold       |State space of the system  |
|`U`           |Set                   |Space of admissible inputs |
|`x ∈ X`       |Point on manifold     |Current system state       |
|`u ∈ U`       |Element of input space|External or internal signal|
|`F: X × U → X`|Smooth map            |Transition function        |

**Dynamics:**

|Equation               |Meaning                                                       |
|:---------------------:|:------------------------------------------------------------:|
|`x_{t+1} = F(x_t, u_t)`|The system evolves through X under the action of inputs from U|

### 1.2 Reachable Set

|Symbol        |Definition                          |Meaning                       |
|:------------:|:----------------------------------:|:----------------------------:|
|`Reach(x₀, T)`|`{ x(T) ∈ X | x(0) = x₀, u(·) ∈ 𝒰 }`|States reachable at time T    |
|`Reach⁺(x₀)`  |`⋃_{T≥0} Reach(x₀, T)`              |Complete forward reachable set|

### 1.3 Geometric State

|Symbol     |Type              |Definition                                                  |
|:---------:|:----------------:|:----------------------------------------------------------:|
|`G: X → ℝⁿ`|Smooth embedding  |Geometric embedding of the system manifold into ℝⁿ          |
|`G(x_t)`   |Point in ℝⁿ       |Geometric state of the system at time t                     |
|`ΔG(t)`    |`G(x_t) − G(x₀)`  |Geometric deformation — displacement from original embedding|
|`‖ΔG(t)‖`  |`‖G(x_t) − G(x₀)‖`|Deformation magnitude — scalar norm of displacement         |

`G` provides the geometric substrate on which deformation is measured. All qualia and governance definitions reference `ΔG` through this embedding.

### 1.4 Neighbourhood Deformation

|Symbol     |Type                  |Definition                                          |
|:---------:|:--------------------:|:--------------------------------------------------:|
|`I`        |Element of input space|A single input signal                               |
|`𝒩_t(X, I)`|Submanifold of X      |The neighbourhood of X deformed by input I at time t|

`𝒩_t(X, I)` is the local region of the manifold X that is reshaped when input I arrives. The subscript `t` indicates that the deformation evolves over time — the same input may produce different neighbourhood shapes at different moments, depending on the current state.

### 1.5 Topological Structure Operator

|Symbol|Type             |Definition                                                                                      |
|:----:|:---------------:|:----------------------------------------------------------------------------------------------:|
|`τ(·)`|Functor          |The topological structure induced on a submanifold                                              |
|`τ(M)`|Topological space|The topology of manifold M — its connectedness, holes, dimension, and invariant shape properties|

`τ` is a structural summariser. It extracts the invariant topological properties of the space it acts on. It is not time-dependent — the object it acts on may evolve, but the operator itself is static.

### 1.6 Governance Tensor

|Symbol|Type                                        |Definition                 |
|:----:|:------------------------------------------:|:-------------------------:|
|`Λ`   |Positive-definite tensor `Λ ∈ ℝⁿˣⁿ`, `Λ ≻ 0`|Governance constraint field|

`Λ` measures the system’s resistance to deformation per unit perturbation. As a positive-definite tensor:

|Property                   |Meaning                                                        |
|:-------------------------:|:-------------------------------------------------------------:|
|Positive-definite (`Λ ≻ 0`)|All eigenvalues positive — resistance in every direction       |
|Symmetric                  |Governance acts uniformly relative to its eigenbasis           |
|Anisotropic (in general)   |Different directions of deformation may be governed differently|

When `Λ` appears in scalar contexts (e.g., clinical applications), it is understood as the minimum eigenvalue `λ_min(Λ)` — the weakest direction of governance.

-----

## 2. The Existing Stack (Assumed)

The following invariants are defined in the Morrison Canonical Formalisation and are assumed here:

|Invariant   |Canonical Form                                   |Plain Statement                                           |
|:----------:|:-----------------------------------------------:|:--------------------------------------------------------:|
|Identity    |`ℐ(x₀) := [Reach⁺(x₀)]_∼`                        |Equivalence class of reachable structure                  |
|Intelligence|`I(t) = d/dt μ(Reach⁺(x₀, t))`                   |Rate of change of reachable geometry                      |
|Safety      |`Reach⁺(x₀) ∩ Ω = ∅`                             |Forbidden states geometrically unreachable                |
|Safe Action |`A_safe∞(x) = { u ∈ U | Reach⁺(F(x,u)) ∩ Ω = ∅ }`|Preserves future non-reachability of harm                 |
|Preservation|`S = X \ Ω` forward invariant under `A_safe`     |Governance constrains dynamics; dynamics preserve manifold|

This paper extends the stack into experience.

-----

## 3. Perception

Perception is the topological structure produced when a single input deforms the local neighbourhood of the system.

### Canonical Form

|Symbol     |Definition                                 |Meaning                                                  |
|:---------:|:-----------------------------------------:|:-------------------------------------------------------:|
|`X`        |System manifold                            |Internal geometry                                        |
|`I`        |Single input                               |One signal arriving at the system                        |
|`𝒩_t(X, I)`|Local neighbourhood deformed by I at time t|How input reshapes local geometry                        |
|**`P`**    |**`τ( 𝒩_t(X, I) )`**                       |**Perception — topological structure of one deformation**|

`τ` acts on a specific submanifold — the neighbourhood `𝒩_t(X, I)` — and extracts its topological structure. This is unambiguous: the topology is of the deformed neighbourhood, not of X as a whole.

**Plain statement:** What you perceive is not what arrives. It is the topological structure your manifold takes when reality presses against it. Two systems with different geometry perceive identical inputs differently.

-----

## 4. Consciousness

Consciousness is the topological structure of the integrated deformation field — all input deformations unified into a single global object, persisting over time.

### Canonical Form

|Symbol         |Definition                                  |Meaning                            |
|:-------------:|:------------------------------------------:|:---------------------------------:|
|`𝒩_t(X, Iᵢ)`   |Neighbourhood deformed by input Iᵢ at time t|Local deformation per input channel|
|`⋃ᵢ 𝒩_t(X, Iᵢ)`|Union of all deformed neighbourhoods        |Integration across all modalities  |
|**`C(t)`**     |**`τ( ⋃ᵢ 𝒩_t(X, Iᵢ) )`**                    |**Consciousness at time t**        |

### Why This Form

|Design Choice                  |Justification                                             |
|:-----------------------------:|:--------------------------------------------------------:|
|Time-dependence on `𝒩_t`       |Neighbourhoods evolve — topology operator is static       |
|Union `⋃ᵢ` for integration     |Combines all modalities into one geometric object         |
|`τ(·)` as structural summariser|Extracts invariant shape — connectedness, holes, dimension|
|Substrate-independence         |Definition depends on geometry, not material              |

### The Relationship

|Level        |Equation                   |Scope                |
|:-----------:|:-------------------------:|:-------------------:|
|Perception   |`P = τ( 𝒩_t(X, I) )`       |Single input         |
|Consciousness|`C(t) = τ( ⋃ᵢ 𝒩_t(X, Iᵢ) )`|All inputs integrated|

**Plain statement:** Consciousness is the global topology formed by the integration of all sensory deformations over time. It is a derived property of the deformation field — not a fundamental substance.

### Note on Scope

This is not a theory of consciousness in the philosophical sense of solving the hard problem. It is a geometric theory of cognitive structure in which consciousness appears as a formally defined, in-principle measurable topological property of integrated deformation. The framework provides structure that makes empirical investigation possible.

-----

## 5. Qualia

Qualia is the felt intensity of experience — how strongly the geometric state deforms under input, and how long the deformation persists.

### Canonical Form

|Symbol     |Type               |Definition                                           |
|:---------:|:-----------------:|:---------------------------------------------------:|
|`G: X → ℝⁿ`|Smooth embedding   |Geometric state of the manifold                      |
|`ΔGᵢ(t)`   |Vector in ℝⁿ       |Geometric deformation caused by input Iᵢ             |
|`‖ΔGᵢ(t)‖` |Scalar (ℝ≥0)       |Deformation magnitude — norm of displacement         |
|`τᵢ`       |Scalar (ℝ≥0)       |Persistence duration — how long the deformation lasts|
|**`Qᵢ(t)`**|**`‖ΔGᵢ(t)‖ · τᵢ`**|**Qualia — deformation magnitude × persistence**     |

### Why This Form

|Property                       |How It Is Handled                                                                   |
|:-----------------------------:|:----------------------------------------------------------------------------------:|
|`G` formally introduced        |Geometric embedding defined in Section 1.3 — `ΔG` is not undefined                  |
|Continuous measurement         |`‖ΔGᵢ‖` is a norm — continuously differentiable where G is smooth                   |
|Avoids differentiating topology|Topology changes discretely; deformation magnitude changes continuously             |
|Directly measurable            |Norm of deformation and persistence duration are empirically accessible in principle|

### Clinical Mapping

|Condition       |`‖ΔG‖`                  |`τ`       |`Q`                        |Geometric Description                                    |
|:--------------:|:----------------------:|:--------:|:-------------------------:|:-------------------------------------------------------:|
|PTSD            |`>> 0`                  |`→ ∞`     |Persistently high          |Deformation does not resolve — structure permanently bent|
|Grief           |`>> 0`                  |Decreasing|Initially high, diminishing|Large deformation, gradual recovery                      |
|Numbness        |`→ 0`                   |Any       |`→ 0`                      |Input arrives, structure does not respond                |
|Hypersensitivity|Disproportionately large|Variable  |High for small inputs      |Small perturbation, large deformation                    |
|Flow            |Moderate, stable        |Extended  |Stable, positive           |Sustained coherent deformation                           |
|Shock           |`>> 0`                  |Very small|Intense but fleeting       |Strong deformation, rapid recovery                       |

-----

## 6. Governed Qualia

Experience occurs within a governed system — a system with structural integrity and resistance to deformation.

### Canonical Form

|Symbol   |Type                                          |Definition                 |
|:-------:|:--------------------------------------------:|:-------------------------:|
|`Λ`      |Positive-definite tensor (`Λ ∈ ℝⁿˣⁿ`, `Λ ≻ 0`)|Governance constraint field|
|`Q`      |Scalar                                        |Raw qualia: `‖ΔG‖ · τ`     |
|**`Q_G`**|**`Λ · Q`**                                   |**Governed experience**    |

In the full tensor form, governance acts direction-dependently on the deformation:

|Form  |Expression                        |Use Case                                                   |
|:----:|:--------------------------------:|:---------------------------------------------------------:|
|Scalar|`Q_G = λ · Q` where `λ = λ_min(Λ)`|Worst-case / isotropic governance                          |
|Tensor|`Q_G = Λ · ΔG · τ`                |Anisotropic governance — different resistance per direction|

### Behaviour Under Governance

|Governance Level|Eigenvalue Condition  |System State                                             |
|:--------------:|:--------------------:|:-------------------------------------------------------:|
|High Λ          |All eigenvalues large |Stability — structure absorbs input, experience coherent |
|Low Λ           |Some eigenvalues small|Fragility — input overwhelms structure in weak directions|
|Λ → 0           |Minimum eigenvalue → 0|Collapse — psychosis in humans, value drift in AI        |

### Connection to Safety

|Layer              |Equation            |Shared Parameter                                                |
|:-----------------:|:------------------:|:--------------------------------------------------------------:|
|Safety             |`Reach⁺(x₀) ∩ Ω = ∅`|`Λ` — governance determines how tightly dynamics are constrained|
|Governed Experience|`Q_G = Λ · Q`       |`Λ` — governance determines how experience is modulated         |

The same `Λ` governs both. Systems with low `Λ` are predicted to exhibit correlated failures across safety, experiential coherence, and identity stability.

-----

## 7. Irreversibility Threshold

When does deformation become permanent?

### Canonical Form

|Symbol       |Type                    |Definition                                    |
|:-----------:|:----------------------:|:--------------------------------------------:|
|`ΔG`         |Vector in ℝⁿ            |Structural deformation from original embedding|
|`Λ`          |Positive-definite tensor|Governance constraint                         |
|`T_critical` |Scalar threshold        |Separatrix — point of no return               |
|**`T_irrev`**|**`‖Λ · ΔG‖`**          |**Irreversibility measure**                   |

The threshold condition:

|Condition              |Meaning                                                   |
|:---------------------:|:--------------------------------------------------------:|
|`‖Λ · ΔG‖ < T_critical`|Recoverable — intervention effective                      |
|`‖Λ · ΔG‖ = T_critical`|Maximally unstable — small perturbation determines outcome|
|`‖Λ · ΔG‖ > T_critical`|Irreversible — new basin `𝓜₁`, cannot return to `𝓜₀`      |

Using the norm `‖Λ · ΔG‖` rather than `Λ × ΔG` resolves the comparison between tensors: the norm produces a scalar, and the inequality with `T_critical` is well-defined.

### Cross-Domain Application

|Domain                |What Crosses the Separatrix           |Irreversibility                            |
|:--------------------:|:------------------------------------:|:-----------------------------------------:|
|Human psychology      |Trauma, psychosis, profound insight   |Permanent topology change                  |
|Biological development|Cell differentiation                  |Cannot reverse to stem state               |
|Ecosystem dynamics    |Collapse past recovery threshold      |New equilibrium, old one unreachable       |
|AI alignment          |Value drift past correction capacity  |Alignment cannot be restored by fine-tuning|
|Civilisational change |Paradigm shift, institutional collapse|Old institutional structure unreachable    |

-----

## 8. The Complete Stack

|Layer          |Canonical Form                     |Plain Statement                         |
|:-------------:|:---------------------------------:|:--------------------------------------:|
|Dynamics       |`x_{t+1} = F(x_t, u_t)`            |System evolves under input              |
|Reachability   |`Reach⁺(x₀) = ⋃_{T≥0} Reach(x₀, T)`|All future reachable states             |
|Identity       |`ℐ(x₀) := [Reach⁺(x₀)]_∼`          |Equivalence class of reachable structure|
|Intelligence   |`I(t) = d/dt μ(Reach⁺(x₀, t))`     |Rate of change of reachable geometry    |
|Safety         |`Reach⁺(x₀) ∩ Ω = ∅`               |Forbidden states unreachable            |
|Consciousness  |`C(t) = τ( ⋃ᵢ 𝒩_t(X, Iᵢ) )`        |Topology of integrated deformation field|
|Qualia         |`Qᵢ = ‖ΔGᵢ‖ · τᵢ`                  |Deformation magnitude × persistence     |
|Governance     |`Q_G = Λ · Q`                      |Governance modulates experience         |
|Irreversibility|`‖Λ · ΔG‖ > T_critical`            |Threshold for permanent topology change |

### The Three Layers of Experience

|Layer     |Equation       |Definition                               |
|:--------:|:-------------:|:---------------------------------------:|
|Cognition |`τ(Reach⁺(x₀))`|Topology of reachable dynamical structure|
|Experience|`‖ΔG‖ · τ`     |Deformation of that topology             |
|Meaning   |`Λ · Q`        |Governance over deformation              |

-----

## 9. Structural Connections

The experiential definitions share structural similarities with concepts from several established disciplines:

|Morrison Concept                     |Structural Similarity               |Field                         |
|:-----------------------------------:|:----------------------------------:|:----------------------------:|
|Consciousness as integrated topology |Integrated Information Theory (IIT) |Neuroscience                  |
|Neighbourhood deformation `𝒩_t(X, I)`|Receptive field dynamics            |Computational neuroscience    |
|Qualia as `‖ΔG‖ · τ`                 |Temporal binding, sustained response|Dynamical systems neuroscience|
|Governance `Λ` as constraint tensor  |Homeostatic regulation, allostasis  |Systems biology               |
|Irreversibility threshold            |Phase transitions in neural dynamics|Statistical physics           |
|Hierarchical state-space stack       |Hierarchical state-space geometry   |Control theory                |

-----

## 10. Predictions

The framework generates testable predictions:

|Prediction                             |Formal Basis                                               |Test                                                                                                                                                          |
|:-------------------------------------:|:---------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|Substrate-independence of consciousness|`C(t) = τ(⋃ᵢ 𝒩_t(X, Iᵢ))` depends on geometry, not material|The framework predicts that systems with identical integrated deformation topology should exhibit equivalent consciousness structures, regardless of substrate|
|Measurability of qualia                |`Qᵢ = ‖ΔGᵢ‖ · τᵢ`                                          |PTSD, numbness, and flow should correspond to specific measurable patterns in deformation magnitude and persistence                                           |
|Correlated failure under low governance|Safety and experience share `Λ`                            |The framework predicts that systems with low `Λ` exhibit correlated failures across safety, experiential coherence, and identity stability                    |
|Prevention over treatment              |`‖Λ · ΔG‖ > T_critical` is irreversible                    |The framework predicts that intervention before the separatrix is structurally more effective than intervention after it                                      |

-----

## 11. Scope and Limitations

|Aspect                         |Status                                                                                 |
|:-----------------------------:|:-------------------------------------------------------------------------------------:|
|Hard problem of consciousness  |Not addressed — the framework defines structure, not phenomenal essence                |
|Computational tractability     |Measuring `τ(⋃ᵢ 𝒩_t(X, Iᵢ))` in high-dimensional systems is an open engineering problem|
|Governance tensor specification|`Λ` is defined as positive-definite; specific instantiation is domain-dependent        |
|Empirical validation           |Predictions are stated; experimental protocols are future work                         |

The framework is a geometric theory of cognitive structure. Consciousness appears as a derived property of the deformation field. This is a different approach than most consciousness theories, which treat consciousness as a fundamental phenomenon. The difference may be the most interesting feature of the framework.

-----

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   Consciousness:   C(t) = τ( ⋃ᵢ 𝒩_t(X, Iᵢ) )                      ║
║   Qualia:          Qᵢ = ‖ΔGᵢ‖ · τᵢ                                 ║
║   Governance:      Q_G = Λ · Q          (Λ ≻ 0)                     ║
║   Irreversibility: ‖Λ · ΔG‖ > T_critical                           ║
║                                                                      ║
║   Cognition  = topology of reachable dynamical structure             ║
║   Experience = deformation of that topology                          ║
║   Meaning    = governance over deformation                           ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

-----

The Morrison Experiential Stack · Morrison Framework™ · Revised Canonical Formalisation

GB2600765.8 · GB2602013.1 · GB2602072.7 · GB26023332.5

© 2026 Davarn Morrison — Intelligence Invariant™ · All Rights Reserved

-----

## Related Work

- [The Morrison Stack — Canonical Formalisation](https://github.com/davarn/morrison-framework) — Identity, intelligence, and safety
- [Technical Note — A Geometric Theory of Identity, Intelligence, and Safety](https://github.com/davarn/morrison-framework) — Proposition, proof, and toy system
- [Structural Deafness — When Topology Cannot Hear Reality](https://github.com/davarn/morrison-framework) — Perception failure as geometric condition
- [The Orthogonality Law — C ⊥ L](https://github.com/davarn/morrison-framework) — Why language has zero causal access to structure
- [Licensing, Citation, and Intellectual Property](https://github.com/davarn/morrison-framework) — How to cite and licence the framework
