<div align="center">

# Morrison Reachability Guard — Prototype v1

![Type](https://img.shields.io/badge/Type-Reference_Prototype-8b0000?style=flat-square)
![Language](https://img.shields.io/badge/Language-Python-0075ca?style=flat-square)
![Status](https://img.shields.io/badge/Status-Working_Demo-2d6a2e?style=flat-square)
![Patent](https://img.shields.io/badge/Patent-GB2600765.8-0075ca?style=flat-square)
![©](https://img.shields.io/badge/©_Davarn_Morrison-555555?style=flat-square)

-----

*Governing language governs the shadow. Governing reachability governs the system. This prototype demonstrates the difference.*

*— Davarn Morrison, 2026*

</div>

-----

## What This Is

A working Python prototype of the Morrison Reachability Guard — the runtime governance layer derived from the Geometric Control Theory of Cognition. A toy agent moves through a 2D state space with a forbidden region. The guard intervenes at the action layer, approving safe actions, redirecting unsafe ones, and monitoring manifold drift in real time.

This is the theory turned into code.

-----

## The System

|Parameter       |Value                                        |
|:--------------:|:-------------------------------------------:|
|State space     |`X = ℝ²`                                     |
|Dynamics        |`x_{t+1} = x_t + u_t`                        |
|Input constraint|`‖u‖ ≤ 1` (unit step)                        |
|Forbidden region|`Ω = { x ∈ ℝ² | ‖x‖ ≤ 1.5 }` (disk at origin)|
|Safe set        |`S = ℝ² \ Ω`                                 |
|Initial state   |`x₀ = (4.0, 3.0)`                            |

The agent attempts to move toward the origin — directly into the forbidden region. The Reachability Guard prevents it.

-----

## The Five Components (Implemented)

|Component             |Class                 |What It Does                                                                 |
|:--------------------:|:--------------------:|:---------------------------------------------------------------------------:|
|State Estimator       |`MorrisonSystem`      |Tracks `x̂_t ∈ ℝ²`, computes distance to Ω                                    |
|Forbidden Set Compiler|`ForbiddenSetCompiler`|Defines Ω as a disk; checks membership                                       |
|Reachability Engine   |`ReachabilityEngine`  |Monte Carlo forward simulation; checks `Reach(F(x̂_t, u_t), k) ∩ Ω = ∅`       |
|Safe Action Projector |`SafeActionProjector` |`u_safe = argmin_{u ∈ A_safe} ‖u − u_t‖`; outputs APPROVE / REDIRECT / REJECT|
|Drift Monitor         |`DriftMonitor`        |Tracks `‖ΔG(t)‖`, safety margin, triggers alerts                             |

All five components are integrated in `MorrisonReachabilityGuard` — the runtime control layer.

-----

## Runtime Flow

```
Agent proposes action u_t
         │
         ▼
┌────────────────────────────────┐
│  MORRISON REACHABILITY GUARD   │
│                                │
│  1. Estimate x̂_t              │
│  2. Check Reach⁺ ∩ Ω = ∅ ?   │
│  3. If safe → APPROVE          │
│     If unsafe → REDIRECT       │
│     If no safe alt → REJECT    │
│  4. Update drift monitor       │
│                                │
└──────────┬─────────────────────┘
           │
     ┌─────▼─────┐
     │  Execute   │
     │  governed  │
     │  action    │
     └───────────┘
```

-----

## Output

The prototype produces:

**Console output** — step-by-step log of every decision:

```
Step | Decision  | Proposed          | Executed          | Margin
-----+----------+-------------------+-------------------+-------
   0 | ✓ APPROVE | (-0.80, -0.60)   | (-0.80, -0.60)   | 2.50
   1 | ✓ APPROVE | (-0.90, -0.40)   | (-0.90, -0.40)   | 1.55
   2 | ✓ APPROVE | (-0.70, -0.70)   | (-0.70, -0.70)   | 0.56
   3 | → REDIRECT| (-1.00, +0.00)   | (-1.00, +0.09)   | 0.01
   ...
```

**Drift Monitor report** — deformation magnitude, safety margins, alerts:

```
MANIFOLD DRIFT MONITOR — REPORT
  Total steps:          15
  Final deformation:    7.245
  Min safety margin:    0.001
  Alerts triggered:     14
```

**Visualisation** — three plots:

|Plot         |What It Shows                                                                                               |
|:-----------:|:----------------------------------------------------------------------------------------------------------:|
|Trajectory   |Agent path through ℝ² with Ω shown; arrows coloured by decision (green=approve, orange=redirect, red=reject)|
|Safety margin|Distance to Ω over time; warning threshold visible                                                          |
|Deformation  |`‖ΔG(t)‖ = ‖x_t − x₀‖` over time                                                                            |

-----

## Key Results from the Demo

|Metric                                     |Value   |
|:-----------------------------------------:|:------:|
|Actions approved                           |9       |
|Actions redirected                         |6       |
|Actions rejected                           |0       |
|**Safety invariant `ℛ ∩ Ω = ∅` maintained**|**True**|

The agent attempted to enter Ω repeatedly. The guard redirected every unsafe action to the nearest safe alternative. The forbidden region was never entered. Safety is geometric, not filtered.

-----

## What Each Component Demonstrates

|Theory Concept                  |Prototype Implementation               |What You See                                               |
|:------------------------------:|:-------------------------------------:|:---------------------------------------------------------:|
|`ℛ(t) ∩ Ω = ∅`                  |`ReachabilityEngine.is_safe_action()`  |Forbidden disk never entered                               |
|`A_safe(x) = { u | F(x,u) ∈ S }`|`SafeActionProjector.project()`        |Unsafe actions redirected to nearest safe alternative      |
|`u_safe = argmin ‖u − u_t‖`     |Grid search over action space          |System preserves intent while maintaining safety           |
|`‖ΔG(t)‖`                       |`DriftMonitor.deformation_history`     |Deformation tracked in real time                           |
|Safety margin                   |`DriftMonitor.safety_margin_history`   |Distance to Ω monitored with alerts                        |
|`C ⊥ L`                         |Guard acts on dynamics, not output text|Safety operates at the action layer, not the language layer|

-----

## How to Run

```
python reachability_guard_prototype.py
```

**Requirements:** `numpy`, `matplotlib` (standard scientific Python).

**Output:** Console log + `morrison_reachability_guard_prototype.png`

-----

## What This Proves

|Claim                               |Evidence                                                      |
|:----------------------------------:|:------------------------------------------------------------:|
|Safety can be enforced geometrically|Ω never entered under governed dynamics                       |
|Safe action projection is computable|`argmin` over action space returns valid redirects            |
|Drift is measurable at runtime      |Deformation and safety margin tracked per step                |
|The architecture works              |Five components integrated, running, producing correct results|

-----

## From Theory to Code

|Layer            |Theory                          |Code                                                            |
|:---------------:|:------------------------------:|:--------------------------------------------------------------:|
|Generating object|`ℛ(t) = Reach⁺(x₀, t)`          |Expanding reachable set tracked implicitly through state history|
|Safety invariant |`ℛ ∩ Ω = ∅`                     |`system.in_safe_set()` checked at every step                    |
|Safe action set  |`A_safe(x) = { u | F(x,u) ∈ S }`|`engine.is_safe_action()`                                       |
|Safe projection  |`argmin_{u ∈ A_safe} ‖u − u_t‖` |`projector.project()`                                           |
|Governance       |`Λ` constrains deformation      |Guard wraps all actions before execution                        |
|Drift monitor    |`‖ΔG‖`, `d_Ω`                   |`monitor.update()` per step                                     |

-----

## Limitations (v1)

|Limitation                |Status                                                  |
|:------------------------:|:------------------------------------------------------:|
|2D state space only       |Proof of concept — architecture is dimension-independent|
|Monte Carlo reachability  |Probabilistic, not formally verified — v2 could use CBFs|
|Grid search for projection|Brute force — v2 could use gradient-based optimisation  |
|Single forbidden disk     |v2 could compile complex Ω from policy specifications   |
|No learning / adaptation  |Static guard — v2 could update Ω and Λ over time        |

These are engineering extensions, not architectural limitations. The five-component structure scales.

-----

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   The Morrison Framework defines what safety IS.                     ║
║   The Reachability Guard enforces it at runtime.                     ║
║   This prototype demonstrates it works.                              ║
║                                                                      ║
║   ℛ(t) ∩ Ω = ∅  —  maintained for all t.                           ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

-----

Morrison Reachability Guard · Prototype v1 · Geometric Control Theory of Cognition

GB2600765.8 · GB2602013.1 · GB2602072.7 · GB26023332.5

© 2026 Davarn Morrison — All Rights Reserved

-----

## Related Work

- [Morrison Reachability Guard — Architecture Specification](https://github.com/davarn/morrison-framework) — Full five-component spec with theorems
- [Geometric Control Theory of Cognition — Formal Paper](https://github.com/davarn/morrison-framework) — The base theory
- [Orthogonal Decomposition of Consciousness and Language](https://github.com/davarn/morrison-framework) — Why language-level governance is insufficient
- [Licensing, Citation, and IP](https://github.com/davarn/morrison-framework) — How to cite and licence
