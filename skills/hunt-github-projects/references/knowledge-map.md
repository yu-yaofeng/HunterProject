# Role Knowledge Map

## Contents

- Construction method
- Source precedence
- Map schema
- Role-family routing
- Coverage and pruning

## Construction method

Build each map from a stable template and dynamic evidence:

```text
role-family baseline
  + explicit JD requirements
  + repeated current-market requirements when available
  + company or domain context
  - capabilities outside the user's feasible scope
= search-time knowledge map
```

Do not rely on either a static template alone or unrestricted generation alone. Templates provide consistency; the JD and market prevent staleness.

## Source precedence

When sources conflict, use this order:

1. explicit responsibilities and requirements in the target JD;
2. repeated requirements across current comparable jobs in the target market;
3. stable role fundamentals;
4. project popularity or repository marketing.

Distinguish:

- required for the target role;
- preferred or differentiating;
- useful for production depth;
- irrelevant or unrealistic for this user's project window.

Do not turn every technology named in a JD into a must-have project feature. Some requirements describe the employer's environment rather than a reasonable portfolio scope.

## Map schema

```yaml
role:
  family: ""
  subrole: ""
core_concepts: []
implementation_signals: []
engineering_signals: []
production_signals: []
domain_signals: []
bonus_signals: []
anti_signals: []
search_terms:
  primary: []
  adjacent: []
  code_evidence: []
```

For each important signal, define what would count as repository evidence. Example:

```text
Signal: RAG
Weak evidence: README mentions retrieval augmented generation
Strong evidence: ingestion, chunking, embedding, vector retrieval, cited answer flow, and evaluation or tests
```

## Role-family routing

Use these families as starting points, then narrow to the actual subrole:

| Family | Common subrole distinctions | Typical project evidence |
|---|---|---|
| Backend | product backend, platform, distributed systems, middleware | APIs, data model, auth, caching, queues, tests, observability |
| Frontend | product UI, web platform, visualization | state, accessibility, performance, testing, complex interaction, build tooling |
| Full stack | product delivery, SaaS, internal tools | end-to-end flow, auth, data, UI, deployment, tests |
| Mobile | Android, iOS, cross-platform | lifecycle, local storage, network, offline behavior, tests, release setup |
| AI/LLM | AI application, Agent, RAG, LLM platform | retrieval, tool use, evaluation, tracing, model abstraction, safety |
| ML | applied ML, ML engineering, research reproduction | data pipeline, baseline, training, evaluation, serving, reproducibility |
| Data | analytics, data engineering, streaming | ingestion, transformation, orchestration, quality, lineage, serving |
| DevOps/SRE | platform, cloud, reliability | IaC, CI/CD, containers, monitoring, recovery, operational evidence |
| Security | application, cloud, detection, tooling | threat model, safe test scope, rules, findings, remediation, tests |
| Embedded/IoT | firmware, device integration, edge | hardware constraints, drivers, protocols, timing, testability |
| QA/Automation | test engineering, quality platform | test architecture, fixtures, reporting, CI integration, reliability |
| Game/Graphics | gameplay, engine, rendering, tools | systems design, performance, assets pipeline, tooling, build reproducibility |

For an unsupported or niche role, generate a temporary map using the same schema. Label unsupported assumptions and use current JD evidence where possible.

## Coverage and pruning

Before repository search, mark every map item as:

- **Must cover:** central to the role and realistic in the project;
- **Should cover:** valuable differentiation or production depth;
- **Reference only:** useful to study but unreasonable to own in this project;
- **Out of scope:** irrelevant, too costly, unsafe, or incompatible with the user.

Use the pruned map to generate queries and evaluate coverage. A project does not need every item; it needs a coherent set that creates a strong role signal.
