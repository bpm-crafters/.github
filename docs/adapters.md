# Adapter landscape

How the engine adapters around the [Process Engine API](https://github.com/bpm-crafters/process-engine-api)
relate, which process engines they cover, and how far along each one is. This is maintainer
documentation — the public pitch lives in [`profile/README.md`](../profile/README.md), the full
reference on the [documentation site](https://bpm-crafters.github.io/process-engine-api-docs/stable/).

## The idea: one API, many engines

The [`process-engine-api`](https://github.com/bpm-crafters/process-engine-api) is an
**engine-agnostic** contract for building process applications. Your business code talks to the API;
an **adapter** binds that API to a concrete process engine. Swap the adapter (and its Spring Boot
starter) and the same application runs on a different engine — ideally with no code changes.

Two integration styles recur across the adapters:

- **Embedded** — the engine runs *inside* your Spring Boot application; service logic executes as
  in-process delegates.
- **Remote** — the engine runs *as a separate host*; your application attaches as an external-task
  **worker** (see [`process-engine-worker`](https://github.com/bpm-crafters/process-engine-worker))
  and owns only the logic.

## Overview

```mermaid
graph LR
  app["Your process application"]:::app
  api["process-engine-api<br/>engine-agnostic contract"]:::api
  worker["process-engine-worker<br/>external-task worker"]:::api

  app --> api
  app -. remote engines .-> worker
  worker --> api

  api --> c7["adapters-camunda-7<br/>embedded · remote"]:::stable
  api --> c8["adapters-camunda-8"]:::inc
  api --> cib["adapters-cib-seven<br/>embedded"]:::inc
  api --> op["adapters-operaton<br/>embedded · remote"]:::inc

  c7 --> C7[("Camunda 7")]:::eng
  c8 --> C8[("Camunda 8 / Zeebe")]:::eng
  cib --> CIB[("CIB seven")]:::eng
  op --> OP[("Operaton")]:::eng

  c7 -. forked into .-> op

  classDef app fill:#f5f5f5,stroke:#bbb,color:#111
  classDef api fill:#1f6feb,stroke:#1f6feb,color:#fff
  classDef stable fill:#2da44e,stroke:#2da44e,color:#fff
  classDef inc fill:#bf8700,stroke:#bf8700,color:#fff
  classDef eng fill:#eaeef2,stroke:#8b949e,color:#111
```

<sub>🟩 stable · 🟧 incubating</sub>

## The adapters

| Adapter | Engine | Integration modes | Lifecycle | Latest release | API version |
| --- | --- | --- | --- | --- | --- |
| [`process-engine-adapters-camunda-7`](https://github.com/bpm-crafters/process-engine-adapters-camunda-7) | Camunda Platform 7 | Embedded · Remote | 🟩 stable | `2026.06.2` | 1.7 |
| [`process-engine-adapters-camunda-8`](https://github.com/bpm-crafters/process-engine-adapters-camunda-8) | Camunda Platform 8 / Zeebe | Remote (SaaS & self-managed) | 🟧 incubating | `2026.06.2` | 1.7 |
| [`process-engine-adapters-cib-seven`](https://github.com/bpm-crafters/process-engine-adapters-cib-seven) | CIB seven | Embedded | 🟧 incubating | `2026.04.1` | 1.5 |
| [`process-engine-adapters-operaton`](https://github.com/bpm-crafters/process-engine-adapters-operaton) | Operaton | Embedded · Remote | 🟧 incubating | *unreleased* | 1.7 |

Lifecycle badges follow the [Holisticon open-source lifecycle](https://github.com/holisticon#open-source-lifecycle).
Version/compatibility tables are maintained in each adapter's `README.md`.
