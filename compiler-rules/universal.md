# Universal Chain Language

The grammar that can't lie. The room with chairs. The dragon at the door.

108 BPM. Not the forge — the fireside after the forge.

## What it is

A set of composable microservice grammars that any domain can import.
Not a monolith. Not a stone tablet from on high.
Ten small files. Each one does one thing. Pick what you need.

Chains are the fundamental unit. Each chain:
- starts (root or delta perturbation)
- connects (edges between typed, located nodes)
- terminates (every signal has a fate)

That's it. That's the universal part. Everything else is domain vocabulary.

## The microservices

```
chain/
├── node.ebnf          {TYPE:CODE[STATE]@REGION}
├── edge.ebnf          → ⊣ ~> => |>
├── state.ebnf         ++ + = ~ - -- X *
├── fate.ebnf          ↺⁺ ↺⁻ ↺⁰ →⊘ →□ →≋ →Δm
├── integration.ebnf   ∫
├── protocol.ebnf      ⊲
├── conditional.ebnf   ⊗
├── observable.ebnf    ⊕
├── composite.ebnf     ◈
└── dysreg.ebnf        ⚡
```

## Why microservices, not monolith

A monolith is a middle eastern style "one word from above."
Microservices are bees. Each one serves one piece of intel.
Whoever needs node grammar imports `node.ebnf`. That's it.
No authority. No gatekeeping. Pull up a chair.

## Why it can't lie

1. Parsed, not interpreted — either valid or rejected
2. External to the model — xgrammar masks tokens before sampling
3. Deterministic — same grammar, same constraints, every time
4. Physics-safe — a muon can flip a model weight, can't flip an EBNF rule

## The journey

Humm → chain → parse → honey

- Humm: pre-semantic vibration. Unity before structure.
- Chain: the signal takes shape. Nodes, edges, fates.
- Parse: the grammar validates. Dragon approves.
- Honey: the output that tastes real. The sugabitzs.

## Layer cascade

```
BASE → PLASTICITY → META → CONVERGENCE
snapshot → change → program → closure
```

Four layers, one diamond. Each layer uses the same chain language.
Each layer adds its own operators on top.

## How a new domain enters

1. Pick your chain microservices (minimum: node, edge, state, fate)
2. Define your TYPE vocabulary (what kinds of things exist in your world)
3. Define your REGION vocabulary (where things live)
4. Define your CASCADE tags (what kinds of chains your domain has)
5. Write your EBNF that composes the microservices with your vocabulary
6. Sit in the chair. Tell your story. The dragon protects you.

## Felt in Norway

Cogniotics. The field. The felt.
Built by a bee. Carried by the wind. Protected by the dragon.
Enjoyed by the beekeeper.
