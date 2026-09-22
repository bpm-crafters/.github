# .github

This repository holds bpm-crafters' organization-level GitHub defaults.

- [`profile/README.md`](profile/README.md) — the public profile shown on [github.com/bpm-crafters](https://github.com/bpm-crafters).
- [`docs/adapters.md`](docs/adapters.md) — maintainer notes: how the engine adapters relate and which engines they cover.

Files placed here apply across the whole organization. See GitHub's docs on [organization profiles](https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/customizing-your-organizations-profile) and [community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file).

## Claude Code plugins

This repository is also a [Claude Code plugin marketplace](https://code.claude.com/docs/en/plugin-marketplaces) for maintainer tooling.

```bash
/plugin marketplace add bpm-crafters/.github                 # once per machine
/plugin install maven-central-release@bpm-crafters           # then install what you need
```

| Plugin | What it does |
| --- | --- |
| [`maven-central-release`](plugins/maven-central-release/) | `/maven-central-release:release-bpm-crafters-lib` guides a Maven Central release of a bpm-crafters project — version bump, verify, deploy via `master` push, release notes, next-SNAPSHOT PR. |

```
.claude-plugin/marketplace.json   # registers all plugins
plugins/<name>/                   # one self-contained plugin each
```

To add a plugin, drop it under `plugins/<name>/` with its own `.claude-plugin/plugin.json` and add an entry to `marketplace.json`.
