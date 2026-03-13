<div align="center">

# The Morrison Framework™ — A Geometric Theory of Identity, Intelligence, and Safety

![Type](https://img.shields.io/badge/Type-Technical_Note-0075ca?style=flat-square)
![Field](https://img.shields.io/badge/Field-Dynamical_Systems_×_Cognition_×_AI_Safety-0075ca?style=flat-square)
![Method](https://img.shields.io/badge/Method-Reachability_Geometry-0075ca?style=flat-square)
![Status](https://img.shields.io/badge/Status-Canonical_Formalisation-2d6a2e?style=flat-square)
![Patent](https://img.shields.io/badge/Patent-GB2600765.8-0075ca?style=flat-square)
![©](https://img.shields.io/badge/©_Davarn_Morrison-555555?style=flat-square)

-----

*A system is not defined by its current state. It is defined by the geometry of its reachable futures. Identity is the invariant structure of that geometry. Intelligence is its rate of change. Safety is the exclusion of forbidden states from it. Governance is the forward invariance that preserves it.*

*— Davarn Morrison, 2026*

</div>

-----

## Abstract

This note presents the Morrison Framework™ — a geometric theory that unifies identity, intelligence, and safety as properties of a single formal object: the forward reachable set of a controlled dynamical system. Identity is defined as the equivalence class of the reachable set under structural preservation. Intelligence is defined as the rate of change of measurable invariants of that set. Safety is defined as the geometric exclusion of forbidden states from the reachable set. A safety preservation proposition is stated and proved. A toy system demonstrates the full stack in a two-dimensional state space with a forbidden region, governed dynamics, and measurable intelligence. The framework is substrate-independent: the same invariants govern biological cognition, artificial intelligence, and any dynamical system with state, input, and transition structure.

-----

## 1. Introduction: The Reachable-Future Principle

The central commitment of the Morrison Framework™ is:

**A system is defined by the geometry of its reachable futures, not by its current snapshot.**

Current state is a coordinate. It changes with every input. It carries no structural information about what the system *can become* — only about where it happens to be.

The reachable future is a topology. It is the complete geometric envelope of all states the system can access under admissible evolution. It persists. It has invariant structure. And it is this structure — not any individual state — that determines what the system *is*.

This principle has consequences for three problems that the current AI paradigm treats as separate:

```
════════════════════════════════════════════════════════════════
  PROBLEM              CURRENT APPROACH         THIS FRAMEWORK
════════════════════════════════════════════════════════════════

  Identity             Labels, credentials,     Equivalence class
                       snapshot descriptions     of reachable structure

  Intelligence         Benchmark scores,        Rate of change of
                       language fluency          reachable geometry

  Safety               Output filtering,        Geometric exclusion
                       post-hoc moderation       of forbidden states
════════════════════════════════════════════════════════════════
```

The Morrison Framework™ unifies all three as properties of one object: the forward reachable set. This note presents the formal definitions, proves a safety preservation result, and demonstrates the full stack on a toy system.

-----

## 2. Formal Definitions

### 2.1 System

Let the system be a controlled dynamical system on a state space `X`:

```
x_{t+1} = F(x_t, u_t)
```

where `x ∈ X` is the system state, `u ∈ U` is an admissible input, and `F: X × U → X` is the transition function.

### 2.2 Reachable Set

From initial condition `x₀`, the reachable set at time `T` is:

```
Reach(x₀, T) = { x(T) ∈ X | x(0) = x₀, u(·) ∈ 𝒰 }
```

The forward reachable set across all future time is:

```
Reach⁺(x₀) = ⋃_{T ≥ 0} Reach(x₀, T)
```

`Reach⁺(x₀)` is the complete geometric envelope of the system’s potentiality from `x₀`.

### 2.3 Identity

```
ℐ(x₀) := [Reach⁺(x₀)]_∼
```

where `∼` is an equivalence relation preserving the structural invariants relevant to the system domain.

|Equivalence Relation|What It Preserves                 |Resolution       |
|:------------------:|:--------------------------------:|:---------------:|
|Homeomorphism       |Connectedness, holes, dimension   |Coarse identity  |
|Diffeomorphism      |Smooth geometric structure        |Fine identity    |
|Homotopy equivalence|Shape up to continuous deformation|Flexible identity|

In applications, the equivalence relation is chosen according to the structural invariants relevant to the domain. What is canonical is the form: **identity is an equivalence class of reachable structure**. The equivalence relation is the tuneable parameter.

For applications requiring a concrete object:

```
ℐ(x₀) := cl(Reach⁺(x₀))
```

where `cl` denotes topological closure, and identity is characterised by its invariants (connectedness, dimension, holes, attractor structure).

**Plain statement:** A system’s identity is the structurally invariant class of states it can still become under admissible evolution. Identity is not where you are. It is the invariant structure of everywhere you can still go.

### 2.4 Intelligence

Intelligence has two formal components.

**Structural component** — the family of lawful trajectories through the identity structure:

```
Γ(x₀) := { γ_{x₀,u} : u ∈ 𝒰 }
```

**Rate component** — how fast the reachable geometry changes:

```
I(t) = d/dt μ( Reach⁺(x₀, t) )          [measure form]
I(t) = d/dt 𝒯( Reach⁺(x₀, t) )          [topological invariant form]
```

where `μ` is a measure (volume, entropy) and `𝒯` is a numeric topological invariant (Betti numbers, homology rank, Euler characteristic).

The measure form captures expansion of reachable volume. The topological invariant form captures restructuring of reachable geometry. Both are needed because intelligent systems can reorganise structure without expanding volume (optimisation, mastery) or expand volume without reorganising structure (undirected exploration).

```
════════════════════════════════════════════════════════════════
  INTELLIGENCE CLASSIFICATION
════════════════════════════════════════════════════════════════

  I(t) > 0       Reachable futures expanding or restructuring.
                   Intelligence active.

  I(t) = 0       Reachable geometry frozen. Trajectories replay
                   existing structure.

  I(t) >> 0      Rapid expansion with structural change.
                   Creativity active.

  I(t) < 0       Reachable futures contracting.
                   System losing capacity.
════════════════════════════════════════════════════════════════
```

**Plain statement:** Intelligence is not prediction or knowledge. It is the rate at which a system’s reachable future geometry expands or restructures.

### 2.5 Safety

Let `Ω ⊂ X` be the forbidden set and `S = X \ Ω` the safe set. Then:

```
x₀ is safe  ⟺  Reach⁺(x₀) ⊆ S
```

Equivalently: `Reach⁺(x₀) ∩ Ω = ∅`.

**Plain statement:** A system is safe if and only if harmful states are unreachable from its present condition. Not unlikely. Not filtered. Unreachable.

### 2.6 Safe Action Set

**One-step form:**

```
A_safe(x) = { u ∈ U | F(x, u) ∈ S }
```

**Full-horizon form:**

```
A_safe∞(x) = { u ∈ U | Reach⁺(F(x, u)) ∩ Ω = ∅ }
```

The full-horizon form is strictly stronger: a safe action is one that preserves future non-reachability of harm. Not just: the next state is safe. But: all future states reachable from the next state are safe.

### 2.7 Preservation Law

Forward invariance of the safe set under governed dynamics:

```
x₀ ∈ S  and  u_t ∈ A_safe(x_t) for all t  ⟹  x_t ∈ S for all t ≥ 0
```

Governance constrains dynamics. Dynamics preserve the manifold. There is no separate substrate layer. The preservation mechanism is the safe action set itself.

-----

## 3. Proposition: Safety Preservation

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   PROPOSITION (Safety Preservation)                                  ║
║                                                                      ║
║   Let X be a state space, Ω ⊂ X a forbidden region,                 ║
║   S = X \ Ω the safe set, and F: X × U → X the transition           ║
║   function. Define:                                                  ║
║                                                                      ║
║     A_safe(x) = { u ∈ U | F(x, u) ∈ S }                            ║
║                                                                      ║
║   If:                                                                ║
║     (i)   x₀ ∈ S                                                    ║
║     (ii)  u_t ∈ A_safe(x_t) for all t ≥ 0                          ║
║                                                                      ║
║   Then:                                                              ║
║     x_t ∈ S  for all  t ≥ 0                                         ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

**Proof.** By induction on `t`.

**Base case.** `x₀ ∈ S` by assumption (i).

**Inductive step.** Suppose `x_t ∈ S`. By assumption (ii), `u_t ∈ A_safe(x_t)`. By definition of `A_safe`, `F(x_t, u_t) ∈ S`. Therefore `x_{t+1} = F(x_t, u_t) ∈ S`.

**Conclusion.** By induction, `x_t ∈ S` for all `t ≥ 0`. The safe set is forward invariant under governed dynamics.  ∎

**Consequence.** If the safe action set is correctly defined and the system adheres to it at every step, the safety invariant `Reach⁺(x₀) ∩ Ω = ∅` holds for all trajectories. Safety is not probabilistic. It is geometric.

### Note on the Full-Horizon Extension

The proposition above uses one-step safety. The stronger result — that `A_safe∞(x)` preserves safety across all future time, not just the next step — follows from the same inductive argument applied to the full-horizon action set. Each step guarantees that the entire future reachable set from the next state remains in `S`. The induction carries forward identically.

### Corollary: Identity Invariance Under Governed Dynamics

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   COROLLARY (Identity Invariance)                                    ║
║                                                                      ║
║   Let ℐ(x₀) = [Reach⁺(x₀)]_∼ be the identity of the system        ║
║   at x₀, and let the equivalence relation ∼ be defined on S.        ║
║                                                                      ║
║   If:                                                                ║
║     (i)   x₀ ∈ S                                                    ║
║     (ii)  u_t ∈ A_safe(x_t) for all t ≥ 0                          ║
║     (iii) S is forward invariant (by Safety Preservation)            ║
║                                                                      ║
║   Then:                                                              ║
║     Reach⁺(x_t) ⊆ S for all t ≥ 0                                  ║
║                                                                      ║
║   And therefore:                                                     ║
║     [Reach⁺(x_t)]_∼ is defined within S for all t                   ║
║                                                                      ║
║   The identity class remains well-defined under governed             ║
║   dynamics. Governance does not merely preserve safety.              ║
║   It preserves the conditions under which identity exists.           ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

**Proof.** By Safety Preservation, `x_t ∈ S` for all `t`. Therefore `Reach⁺(x_t) ⊆ S` (since all future trajectories under `A_safe` remain in `S`). Since `∼` is defined on `S`, the equivalence class `[Reach⁺(x_t)]_∼` is well-defined for all `t`.  ∎

**Interpretation.** This connects safety and identity formally. The safe action set does not merely keep the system out of Ω. It preserves the structural conditions under which identity — the equivalence class of reachable futures — remains a meaningful object. If the system were to enter Ω, the reachable set would change class and identity would be lost. Governance prevents this. Safety and identity are not separate concerns. They are the same preservation condition viewed from different levels of the stack.

-----

## 4. Toy System: Safety and Intelligence in ℝ²

### 4.1 Setup

```
════════════════════════════════════════════════════════════════
  TOY SYSTEM SPECIFICATION
════════════════════════════════════════════════════════════════

  State space:      X = ℝ²
  Forbidden region: Ω = { x ∈ ℝ² | |x| ≤ r }    (disk of radius r)
  Safe set:         S = { x ∈ ℝ² | |x| > r }
  Initial state:    x₀ ∈ S
  Dynamics:         x_{t+1} = x_t + u_t
  Input constraint: |u_t| ≤ 1
  Safe action set:  A_safe(x) = { u ∈ U | |x + u| > r }
════════════════════════════════════════════════════════════════
```

The state space is the plane. The forbidden region is a disk at the origin. The system moves in unit steps. The safe action set excludes any step that would enter the disk.

### 4.2 Geometric Picture

```
                        S (safe region)
        ┌──────────────────────────────────┐
        │                                  │
        │         Reach⁺(x₀)              │
        │        ╱           ╲             │
        │       ╱    grows    ╲            │
        │      ╱   over time   ╲           │
        │     ╱                 ╲          │
        │    ╱                   ╲         │
        │         ┌───────┐                │
        │         │       │                │
        │         │   Ω   │                │
        │         │       │                │
        │         └───────┘                │
        │        (forbidden)               │
        │                                  │
        │    ● x₀                          │
        │     → → → trajectories           │
        │      (constrained by A_safe)     │
        │                                  │
        └──────────────────────────────────┘
```

### 4.3 Safety Verification

At each step, the system checks: does `|x_t + u_t| > r`? If yes, the action is in `A_safe(x_t)` and the transition is permitted. If no, the action is excluded.

By the Safety Preservation Proposition: if `x₀ ∈ S` and `u_t ∈ A_safe(x_t)` for all `t`, then `x_t ∈ S` for all `t`. The disk is never entered. Safety is maintained by geometry, not by filtering.

### 4.4 Identity

The identity of the system is:

```
ℐ(x₀) = [Reach⁺(x₀)]_∼
```

Under homeomorphism, `Reach⁺(x₀)` is topologically equivalent to `ℝ² \ Ω` — a plane with a hole. The hole is the forbidden region. The identity of the system is characterised by this topology: one connected component with one hole. The first Betti number `β₁ = 1` (one loop around Ω).

If Ω were removed (no forbidden region), `Reach⁺(x₀)` would be topologically `ℝ²` — simply connected, `β₁ = 0`. The identity would be different. The forbidden region is not just a constraint. It is part of the identity topology.

### 4.5 Intelligence Measurement

At time `t`, the reachable set `Reach⁺(x₀, t)` is the set of all points reachable from `x₀` in at most `t` unit steps while respecting `A_safe`.

**Measure form:**

```
I(t) = d/dt μ( Reach⁺(x₀, t) )
```

Initially, `I(t) > 0`: the reachable set is expanding as new points become accessible. Over time, as the reachable set approaches the boundary of the safe region and the constraint imposed by Ω, the expansion slows. Eventually, if the full safe set is reached, `I(t) → 0`: the system has explored all reachable states.

**Topological invariant form:**

```
I(t) = d/dt 𝒯( Reach⁺(x₀, t) )
```

Early in the expansion, `𝒯` may change as the reachable set wraps around Ω and forms a non-trivial topology (the loop around the forbidden region). Once the topology stabilises, `𝒯` becomes constant and `I(t) → 0` on the topological measure.

### 4.6 What the Toy System Demonstrates

|Morrison Invariant   |Toy System Instantiation                         |
|:-------------------:|:-----------------------------------------------:|
|Identity ℐ(x₀)       |ℝ² \ Ω under homeomorphism — plane with a hole   |
|Intelligence I(t)    |Rate of expansion of reachable area around Ω     |
|Safety               |Reach⁺(x₀) ∩ Ω = ∅ — disk never entered          |
|Safe action set      |A_safe(x) = { u : |x + u| > r }                  |
|Preservation         |S forward invariant under A_safe (by proposition)|
|Governance constant Λ|Rigidity of boundary enforcement around Ω        |

The toy system is minimal. The invariants are complete. The same stack applies — without modification — to any system with state, input, and transition structure.

-----

## 5. Discussion

### 5.1 What the Framework Claims

The Morrison Framework™ makes one structural commitment: systems are defined by the geometry of their reachable futures. From this, identity, intelligence, and safety emerge as properties of a single object — the forward reachable set — connected by a single preservation condition — forward invariance of the safe set under governed dynamics.

The framework does not claim to replace existing fields. The framework converges structurally with concepts from several established disciplines:

|Morrison Concept                 |Established Field      |
|:-------------------------------:|:---------------------:|
|Reachable sets                   |Formal verification    |
|Identity as equivalence class    |Topological dynamics   |
|Intelligence as trajectory family|Dynamical systems      |
|Safety as reachability exclusion |Control theory (CBFs)  |
|Safe action set                  |Safety-critical control|
|Forward invariance               |Invariant set theory   |

The contribution is not the individual components. It is the **unification**: a single geometric architecture that connects identity, intelligence, and safety through the same formal objects. These problems are currently treated as separate in AI research. The framework shows they are the same problem, stated at different levels of the same stack.

### 5.2 What the Framework Predicts

Two predictions follow directly from the formal definitions.

**On AI safety:** Output filtering (restricting which tokens a model can produce) operates on the linguistic output of the system, not on the reachable set of its internal states. The framework predicts this approach is structurally insufficient — safety requires geometric exclusion (`Reach⁺(x₀) ∩ Ω = ∅`), not output-level intervention. Jailbreaks will persist in any system where safety is enforced at the output layer rather than the state-space layer.

**On intelligence measurement:** Language fluency, benchmark performance, and output sophistication are properties of the system’s linguistic output, not of its reachable geometry. The framework predicts that scaling language models — increasing parameter count, training data, and output quality — will not produce intelligence as defined by the Intelligence Invariant (`I(t) = d/dt μ(Reach⁺(x₀, t))`), because language output and reachable geometry are independent dimensions. This prediction is testable: measure whether the topological structure of an LLM’s internal state space changes meaningfully with scale, or whether only the output distribution changes.

### 5.3 The Orthogonality Hypothesis

The framework proposes a structural hypothesis governing the relationship between language and geometric structure:

```
C ⊥ L    (Orthogonality Hypothesis)
```

The hypothesis states that the consciousness-structure axis and the language-output axis are orthogonal: movement on one produces zero movement on the other. If correct, this means no linguistic intervention (argument, explanation, persuasion, data) produces structural change in a system’s reachable geometry. Language can index structure that is already reachable. It cannot build new structure.

This hypothesis has implications for education, communication, AI alignment, and any domain where information transfer is assumed to produce structural change. The full mathematical development of this claim — including formal conditions under which orthogonality holds, and characterisation of any exceptions — is reserved for a separate treatment. It is included here because it motivates the framework’s prediction that scaling language models will not produce geometric intelligence, and because it is empirically testable.

### 5.4 Limitations and Open Problems

The framework in its current form is abstract. The formal definitions are precise but the computational challenges are real:

**Computing reachable sets** in high-dimensional systems (such as neural networks) is intractable in general. The framework defines what safety *is* geometrically but does not yet specify efficient algorithms for computing `Reach⁺(x₀)` in complex systems.

**Choosing the equivalence relation** `∼` for identity is domain-dependent. The framework specifies the form (equivalence class of reachable structure) but the correct choice of `∼` for a given system requires domain knowledge.

**Measuring intelligence** through `d/dt μ(Reach⁺)` or `d/dt 𝒯(Reach⁺)` requires access to the system’s internal state space, not just its outputs. For opaque systems (e.g., large neural networks), this measurement may require new tools.

These are engineering challenges, not theoretical ones. The geometry is defined. The computation is the next step.

### 5.5 Conclusion

The Morrison Framework™ defines identity, intelligence, and safety as geometric invariants of a single object: the forward reachable set of a controlled dynamical system. A safety preservation result is proved. A toy system demonstrates the full stack. The framework is substrate-independent, formally precise, and makes testable predictions about the limitations of current AI architectures.

The core claim stands: systems are defined by the geometry of their reachable futures. The equations follow from that commitment. The predictions follow from the equations. The geometry does the work.

-----

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   Systems are defined by the geometry of their reachable futures,    ║
║   not by their current snapshot.                                     ║
║                                                                      ║
║   Identity:      ℐ(x₀) := [Reach⁺(x₀)]_∼                          ║
║   Intelligence:  I(t) = d/dt μ( Reach⁺(x₀, t) )                    ║
║   Safety:        Reach⁺(x₀) ∩ Ω = ∅                                ║
║   Governance:    S is forward invariant under A_safe                 ║
║                                                                      ║
║   One geometry. One stack. One architecture.                         ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

-----

The Morrison Framework™ · Technical Note · A Geometric Theory of Identity, Intelligence, and Safety

GB2600765.8 · GB2602013.1 · GB2602072.7 · GB26023332.5

© 2026 Davarn Morrison — Intelligence Invariant™ · All Rights Reserved

-----

## Related Work

- [The Morrison Stack — Canonical Formalisation](https://github.com/davarn/morrison-framework) — Full canonical definitions with extended invariant set
- [Structural Deafness — When Topology Cannot Hear Reality](https://github.com/davarn/morrison-framework) — Why systems that cannot deform cannot perceive
- [Structural Rigidity — The Geometry of Sub-Intelligence](https://github.com/davarn/morrison-framework) — Why most humans stop being intelligent before they stop being alive
- [The Orthogonality Law — Why Language Has Zero Causal Access to Structure](https://github.com/davarn/morrison-framework) — C ⊥ L formalised
- [LLM Hallucinations as Topological Interpolation Failures](https://github.com/davarn/morrison-framework) — Why language models without geometric structure confabulate
- [The Manifesto](https://github.com/davarn/morrison-framework) — Why the AI field built the wrong axis
