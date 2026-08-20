# BioInfer — Signal Cascade Inference Framework

## The Model

Four lines. Everything else is instantiation.

```
BASE:         chains→∫→⊲→⊗→EMIT                       (bottom-up runtime)
PLASTICITY:   Δ0→Δ1→Δ2→Δ3                              (between ticks)
META:         ⊗̃→⊲̃→∫̃→σ̃                                (top-down projection)
CONVERGENCE:  scalar(t) = f(v_past, v_current, v_meta)  (diamond closure)
```

These four pipelines are domain-agnostic. They don't care whether the signals
are neurochemical, financial, social, or mechanical. The domain-specific content
is the nodes and edges. The computational architecture is these four pipelines.

---

## The Diamond

```
                 ⊗̃   projected architecture
                ╱    ╲
             ⊲̃       ∫̃
                ╲    ╱
                 σ̃   baselines ─────────── v_meta
                  │                            │
                  │              ┌──────────────┤
                  │              │              │
              chains  scalar(t) = f(v_past, v_current, v_meta)
                  │
                  ∫   neurons ───────────── v_current
                ╱    ╲
              ⊲       ⊗
                ╲    ╱
                EMIT
                  │
            ┌─────┘
            │  Δ0→Δ1→Δ2→Δ3
            │        │
            │   append-only ──────── v_past
            └──→ next tick
```

The bottom half goes up — activity builds complexity.
The top half comes down — the program unfolds into specifics.
They meet at the scalar/meta-scalar interface.

---

## The Algebra

Operators are borrowed, not invented. Each symbol activates training signal
across multiple domains simultaneously.

```
∫  = calculus integration    : weighted sum of inputs → scalar output
⊲  = group action            : structured transformation with parameters
⊗  = tensor product          : exists only when multiple inputs simultaneously present
Δ  = finite difference       : what changed between observations
∮  = contour integral         : sum all forces around a node, check if they net
∇× = curl                    : feedback rotation at a point. ⁺ = amplifying, ⁻ = damping
→? = conditional execution   : gate passes if condition met
σ̃  = distribution parameter  : where the system thinks normal is
≫  = monadic bind            : sustained trigger produces transformed state
```

| Rank   | What it is | What it adds        | Operator | Cross-domain reading                          |
| ------ | ---------- | ------------------- | -------- | --------------------------------------------- |
| chains | Signal     | Magnitude           | → ⊣ ~> => \|> | Reaction arrows, signal flow, implication |
| ∫      | Structure  | Direction + length  | ∫        | Calculus integral, PID integrator, forward pass |
| ⊲      | Protocol   | Pairwise rules      | ⊲        | Group action G ⊲ X, transfer function          |
| ⊗      | Context    | Multi-way conditionals | ⊗     | Tensor product, logic gate, coincidence         |

| Rank | Meta-level   | What it adds       | Operator | Cross-domain reading                    |
| ---- | ------------ | ------------------ | -------- | --------------------------------------- |
| σ̃    | Setpoint     | Target baseline    | σ̃        | Distribution parameter, control setpoint |
| ∫̃    | Remodeling   | Structural program | ∫̃        | Target integration, programmed accumulation |
| ⊲̃    | Program      | Protocol schedule  | ⊲̃        | Locked group action, fixed transfer function |
| ⊗̃    | Architecture | Connectivity plan  | ⊗̃        | Projected tensor structure, topology program |

| Rank | Plasticity                  | What changes                                 | Timescale |
| ---- | --------------------------- | -------------------------------------------- | --------- |
| Δ0   | Scalar self-adaptation      | Release, reuptake, baseline, synthesis       | ms → wk   |
| Δ1   | Structural plasticity       | Spines, dendrites, axons, cell state         | h → wk    |
| Δ2   | Protocol plasticity         | Gain, gate, tau, density, coupling           | min → mo  |
| Δ3   | Cross-connective plasticity | Associations, extinctions, conditional logic | h → yr    |

---

## Five Edges

Every edge is a typed triple: (source_type, edge_op, target_type).
Invalid triples are compile errors.

```
→   activates    L→R  R→Gp  Gp→2m  2m→K  K→K  K→TF  N→N
⊣   inhibits     L⊣R  L⊣K  K⊣K  R⊣N  2m⊣K
~>  modulates    L~>R  L~>⊲  2m~>K
=>  transcribes  TF=>G  G=>L  G=>R  G=>E
|>  transports   L|>T  T|>E  L|>⊘  T|>⊘
```

That's it. Strength lives in ⊲ gain, not edge type.
Bidirectional is two edges. Reverse is the edge written forward.

---

## Type System

The grammar is the type system. Wrong biology is a parse error.

### Declaration-before-use
First mention: full type. `{L.nt:DA[↓]@NAc}` → registers DA@NAc as L.nt.
Subsequent: short form. `{DA@NAc}` → resolved from symbol table.
Unresolvable short form = COMPILE ERROR.

### Typed edge triples
`{TF:CREB}→{L.nt:DA}` = ERROR. TF→L requires `=>`.
`{L.nt:DA}=>{R:D1}` = ERROR. Ligand doesn't transcribe receptor.

### Dependent coupling
`{R:D1(coup:Gs)}` can only → `{Gp:Gs}`, not `{Gp:Gq}`.
Coupling value inside receptor narrows valid targets.

### Mandatory intracellular cascade (reachability)
L reaches K without passing through R = ERROR.
Not a rule. A reachability constraint the compiler checks.

### Typestate on receptors
`{R:D1(st:act)}` has different valid edges than `{R:D1(st:des)}`.
Δ transitions consume old state. References to consumed state = ERROR.

```
st:      act ↔ des → supersens
gate:    open ↔ closed ↔ desens | open → locked (one-way)
dens:    norm ↔ up ↔ down
release: norm ↔ depleted ↔ enhanced
```

Invalid transitions = COMPILE ERROR.

### Ring closure
`«1⁺→...→»1` must balance. Unclosed ring = ERROR.

### No dead code
∫ output never consumed = ERROR.
⊲ target doesn't exist = ERROR.
⊗ condition references undeclared node = ERROR.

---

## Compiler-inferred (not LLM-emitted)

The LLM writes topology. The compiler computes the rest.

```
∇²syn / ∇²vol    inferred from L subclass (L.nt=syn, L.h=vol)
∇·+ / ∇·−        inferred from edge topology (no-input=source, ⊘=sink)
Σ∇·              computed from graph (source count − sink count)
```

These never appear in LLM output.

---

## Progressive Inference

The four pipelines are independently valid. They layer on as data permits.
Each stage adds predictive power. None are prerequisites except as noted.

```
┌─────────────┬──────────────────┬──────────────────────────────────┐
│ Stage       │ Requires         │ Produces                         │
├─────────────┼──────────────────┼──────────────────────────────────┤
│ 1. BASE     │ one observation  │ diagnostic snapshot              │
│             │                  │ "what is happening now"           │
├─────────────┼──────────────────┼──────────────────────────────────┤
│ 2. PLAST.   │ two+ snapshots   │ change map with timescales       │
│             │ (BASE × 2)       │ "what is changing and how fast"  │
├─────────────┼──────────────────┼──────────────────────────────────┤
│ 3. META     │ Δ trends over    │ program map with setpoints       │
│             │ sustained period │ "where is it headed and why"     │
├─────────────┼──────────────────┼──────────────────────────────────┤
│ 4. CONV.    │ BASE + Δ + META  │ prediction engine                │
│             │ all populated    │ "what will happen if we do X"    │
└─────────────┴──────────────────┴──────────────────────────────────┘
```

### Clinical mapping:

```
Stage 1 = First appointment    → symptom map
Stage 2 = Follow-ups           → treatment tracking
Stage 3 = Long-term care       → prognosis, treatment resistance analysis
Stage 4 = Full model           → intervention simulation, trajectory prediction
```

---

## The Scalar is Never Simple

What we observe as a single number (47nM of dopamine) is a convergence
projection — the lossy collapse of a high-dimensional intersection:

```
scalar(t) = f(
    v_past:    trajectory history (append-only temporal store)
    v_current: live structural integration (∫ output)
    v_meta:    programmed setpoint (σ̃ baseline)
)
```

Two systems with identical scalar values can have completely different
underlying states:

* One arriving from above (depletion trajectory)
* One arriving from below (recovery trajectory)
* One being held there by epigenetic setpoint
* One being forced there by acute perturbation against its setpoint

Same number. Radically different systems. The convergence equation is what
distinguishes them.

---

## Execution Cycle

```
Phase 0 — META PROJECTION (once per developmental step)
    ⊗̃ → ⊲̃ → ∫̃ → σ̃
    Top-down: architecture → protocols → structure → baselines

Phase 1 — BASE RUNTIME (every tick)
    chains: RESOLVE scalars via convergence equation
    ∫:      INTEGRATE structural units
    ⊲:      APPLY pairwise protocols
    ⊗:      EVALUATE cross-connective conditionals
    EMIT → feedback to chains

Phase 2 — PLASTICITY (between ticks)
    Δ0 → Δ1 → Δ2 → Δ3
    Each level triggered by level below
    All changes deferred, applied between ticks

Phase 3 — FEEDBACK ARROWS
    Upward:   Δ3 patterns → can write new ⊗̃ entries
    Downward: σ̃ setpoints → pull scalars via convergence
    Lateral:  Δn → may trigger Δ(n+1)
```

---

## Compiler Pipeline

```
PARSE       BNF grammar → AST
RESOLVE     build symbol table, resolve short-form references
TYPECHECK   validate edge triples, coupling constraints
REACHCHECK  intracellular cascade reachability (L must reach K through R)
STATECHECK  property state machines, typestate transitions
REFCHECK    FK validation (⊲ targets, ⊗ conditions, ∫ inputs exist)
RINGCHECK   bracket matching for feedback rings
DEADCHECK   no orphans, no dead integrations/protocols/conditionals
INFER       transmission mode from L subclass, conservation from topology
EMIT        graph to store
```

Each pass = binary reward signal for GRPO training.

---

## Compiler Acceptance

The compiler accepts partial programs. Each stage is independently parseable.
Operators self-declare their pipeline — no section markers needed.

```
// Stage 1: BASE only (valid)
@domain:chem,struct
#context
chains...  ∫...  ⊲...  ⊗...  ◈...  ⚡...

// Stage 2: BASE + PLASTICITY (valid)
// above + Δ operators
Δ0: ...  Δ1: ...  Δ2: ...  Δ3: ...

// Stage 3: BASE + PLASTICITY + META (valid)
// above + tilde operators
⊗̃[window](...) ...  ⊲̃[window](...) ...  ∫̃[window](...) ...  σ̃[window](...) ...

// Stage 4: Full diamond (valid)
// above + convergence operators
∮(...) ...  ⊳(...) ...  ⚡allo: ...  ⚡resist: ...
```

---

## GRPO Reward Function

```
reward = (
  0.20 × parse_score        +  // does it parse?
  0.15 × type_score          +  // valid edge triples?
  0.15 × ref_score           +  // all FKs resolve?
  0.15 × cascade_score       +  // intracellular paths intact?
  0.10 × state_machine_score +  // valid property transitions?
  0.10 × ring_score          +  // brackets balanced?
  0.05 × dead_code_score     +  // no orphans?
  0.10 × coverage_score         // key signals represented?
)
```

All binary except coverage. All computable. No fuzzy scoring.

---

## Diagnostics

| Symbol        | Name                    | Fires when                          | Stage    |
| ------------- | ----------------------- | ----------------------------------- | -------- |
| ◈             | Composite               | behavioral cluster identified       | BASE     |
| ⚡dep/exc/sus | Dysregulation           | pathological cascade pattern        | BASE     |
| ∮             | Convergence state       | three vectors computed for signal   | CONV     |
| ⊳             | Trajectory prediction   | forward projection computed         | CONV     |
| ⚡allo        | Allostatic load         | σ̃ setpoint drifted from default    | CONV     |
| ⚡resist      | Treatment resistance    | Δ0 opposed by σ̃                    | CONV     |
| ⚡diverge     | Trajectory divergence   | v_past trend ≠ v_meta direction     | CONV     |
| ⚡unstable    | Convergence instability | three vectors disagree              | CONV     |
| ⚡lock        | Epigenetic lock         | ⊲̃ has methylation-locked protocol  | META     |

Note: Σ∇· (conservation) is compiler-computed, not a diagnostic the LLM emits.

---

## Files

| File              | Pipeline    | Content                                                      |
| ----------------- | ----------- | ------------------------------------------------------------ |
| `base.md`         | BASE        | chains→∫→⊲→⊗→EMIT. Single snapshot. Grammar + example.     |
| `plasticity.md`   | PLASTICITY  | Δ0→Δ1→Δ2→Δ3. Change map between snapshots. Grammar + example. |
| `meta.md`         | META        | ⊗̃→⊲̃→∫̃→σ̃. Epigenetic/developmental programs. Grammar + example. |
| `convergence.md`  | CONVERGENCE | ∮ + ⊳ + ⚡. Diamond closure + prediction. Grammar + example. |

Each file contains: identity line, grammar (BNF), cross-domain priming,
one worked example, boundary fences (what operators belong elsewhere).
No numbered rules. No prose quality checklists. The example IS the standard.

They compose progressively: BASE → +PLASTICITY → +META → +CONVERGENCE.

---

## Origin

Derived from the neuro-algebra pyramid:

* Scalars are the fuel (signal)
* Vectors are the trajectory (neurons)
* Matrices are the landscape (protocols)
* Tensors are the context (cross-connectivity)
* Plasticity is the landscape changing as the river flows
* Meta is the landscape's blueprint unfolding
* Convergence is where the river, the erosion, and the blueprint meet

The base stack goes up — activity builds complexity.
The meta stack comes down — the program unfolds into specifics.
Plasticity is the bridge between them.
And every observable scalar is the shadow cast by their intersection.
