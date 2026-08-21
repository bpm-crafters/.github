## One process API. Any engine.

Picking a process engine shouldn't lock your application to it. bpm-crafters builds an
**engine-agnostic Process Engine API** for Kotlin / Spring Boot — your business and application logic
talk to one clean, implementation-independent contract, and a thin **adapter** binds it to the engine
you actually run. Change the engine, keep the code.

- 🧩 **Engine-agnostic API** — deployment, process, correlation, signals, service & user tasks, behind one contract
- 🔌 **Adapters for every engine** — Camunda 7, Camunda 8 / Zeebe, CIB seven, Operaton — embedded or remote
- 🛠️ **Batteries included** — an annotation-based external-task [worker](https://github.com/bpm-crafters/process-engine-worker) and test fixtures
- 🔁 **Migration-friendly** — swap the adapter, not your application

## Start here

- 📚 **[Documentation](https://bpm-crafters.github.io/process-engine-api-docs/stable/)** — intro, quickstarts and the full API reference
- 🧠 **[process-engine-api](https://github.com/bpm-crafters/process-engine-api)** — the core, engine-agnostic API
- 🧭 **[Adapter landscape](../docs/adapters.md)** · **[Documentation landscape](../docs/documentation.md)** — how the pieces fit together
- ✨ **[awesome-bpm-tools](https://github.com/bpm-crafters/awesome-bpm-tools)** — a curated list of BPM(N) engines, frameworks & tooling

## Get involved

bpm-crafters is open source and built in the open. Browse the repositories, open an issue, or send a
pull request — contribution guides live in each project and on the [documentation site](https://bpm-crafters.github.io/process-engine-api-docs/stable/).
