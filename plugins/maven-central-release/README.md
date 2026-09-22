# maven-central-release

A Claude Code plugin that walks a maintainer through releasing a bpm-crafters Maven project to Maven Central.

## Skills

### `/maven-central-release:release-bpm-crafters-lib`

Runs the full manual release: asks for the release and next development version, creates the milestone and assigns the merged PRs, cuts a `release/<version>` branch with `versions:set`, verifies the build locally, merges into `master`, and only after an explicit approval pushes `master` — which is what deploys to Maven Central. Afterwards it closes the milestone to generate the draft release notes, publishes the GitHub release, opens the next-SNAPSHOT PR against `develop`, and verifies the artifacts on Central.

The skill reads the root `artifactId`, `groupId`, and current version from `pom.xml`, so it works unchanged for every process-engine adapter.

**Prerequisites in the target repository**

- `.github/workflows/master.yml` deploys to Maven Central on push to `master`
- `.github/workflows/release-notes.yml` creates a draft release when a milestone is closed
- default branch `develop`, release trigger branch `master`
- calendar versioning `YYYY.MM.n`
- `gh` authenticated, commits signed with your registered key

Publishing to Maven Central is irreversible. The skill stops at an approval gate and pushes `master` only after you confirm.

## License

Apache-2.0
