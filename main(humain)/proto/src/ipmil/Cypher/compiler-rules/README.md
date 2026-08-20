# grammarzs

The forge. Where grammars are made and stored.

## Structure

```
grammarzs/
├── universal.md                           ← the philosophy
├── proto.language.md                      ← what proto-dragons speak today
├── xgrammar/
│   ├── chain/                             ← UNIVERSAL CHAIN LANGUAGE (microservices)
│   │   ├── README.md                      ← how to use
│   │   ├── node.ebnf                      ← {TYPE:CODE[STATE]@REGION}
│   │   ├── edge.ebnf                      ← → ⊣ ~> => |>
│   │   ├── state.ebnf                     ← ++ + = ~ - -- X *
│   │   ├── fate.ebnf                      ← ↺⁺ ↺⁻ ↺⁰ →⊘ →□ →≋ →Δm
│   │   ├── integration.ebnf               ← ∫
│   │   ├── protocol.ebnf                  ← ⊲
│   │   ├── conditional.ebnf               ← ⊗
│   │   ├── observable.ebnf                ← ⊕
│   │   ├── composite.ebnf                 ← ◈
│   │   └── dysreg.ebnf                    ← ⚡
│   │
│   ├── compact_cognit.ebnf                ← behavioral safety (CCDSL)
│   ├── universal_chain_language.ebnf      ← composed full grammar
│   │
│   ├── biochain_base.ebnf                 ← DOMAIN: clinical biochemistry BASE
│   ├── biochain_plasticity.ebnf           ← DOMAIN: change maps
│   ├── biochain_meta.ebnf                 ← DOMAIN: epigenetic programs
│   └── biochain_convergence.ebnf          ← DOMAIN: diamond closure
│
└── system-prompts_v4/                     ← model instructions
    ├── BASE_SYSTEM_PROMPT.md
    ├── PLASTICITY_SYSTEM_PROMPT.md
    ├── META_SYSTEM_PROMPT.md
    ├── CONVERGENCE_SYSTEM_PROMPT.md
    ├── BASE_VIZ.md
    ├── CHAT_SYSTEM_PROMPT.txt
    └── OVERVIEW.txt
```

## Three layers of constraint

| Layer | What | Where | Survives muon? |
|-------|------|-------|----------------|
| chain/ microservices | Token-level grammar | External to model | Yes |
| compact_cognit.ebnf | Behavioral rules | External to model | Yes |
| system-prompts_v4/ | Instructions | In model context | No |

The first two are "ain't AI" — they constrain from outside.
The third tells the model what to do — but the grammar ensures how.

## How domains compose

1. Import chain/ microservices you need
2. Add domain TYPE, REGION, CASCADE vocabularies
3. Compose into a domain grammar (like `biochain_base.ebnf`)
4. Write system prompts that teach the model your domain
5. Run with vLLM + xgrammar constrained decoding

BioChain is the first domain. Not the last.
