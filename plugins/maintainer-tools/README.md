# maintainer-tools

A Claude Code plugin bundling the skills maintainers of bpm-crafters libraries use day to day. Add new skills under `skills/<name>/SKILL.md`.

## Skills

### `/maintainer-tools:release-bpm-crafters-lib`

Runs the full manual Maven Central release: asks for the release and next development version, creates the milestone and assigns the merged PRs, cuts a `release/<version>` branch with `versions:set`, verifies the build locally, merges into `master`, and only after an explicit approval pushes `master` — which is what deploys to Maven Central. Afterwards it closes the milestone to generate the draft release notes, publishes the GitHub release, opens the next-SNAPSHOT PR against `develop`, and verifies the artifacts on Central.

The skill reads the root `artifactId`, `groupId`, and current version from `pom.xml`, so it works unchanged for every process-engine adapter. On the release branch it also adds the new row to the README compatibility table, derived from the engine, API and Spring Boot properties in the POM.

**Prerequisites in the target repository**

- `.github/workflows/master.yml` deploys to Maven Central on push to `master`
- `.github/workflows/release-notes.yml` creates a draft release when a milestone is closed
- default branch `develop`, release trigger branch `master`
- calendar versioning `YYYY.MM.n`
- `gh` authenticated, commits signed with your registered key

Publishing to Maven Central is irreversible. The skill stops at an approval gate and pushes `master` only after you confirm.

## License

Apache-2.0
