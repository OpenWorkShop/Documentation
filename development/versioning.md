## MakerHub Versioning

### Monolithic Versioning

Because MakerHub is a monorepo, all packages (npm, nuget, Docker, etc.) are locked to the same version number by the CI.

### Semantic Versioning

MakerHub follows semantic versioning:

`[major].[minor].[patch]-[channel].[build]`

- **channel**: see Release Channels, below.
- **build**: numeric ID of the build (_only when built by CI_).

For example:

- `1.0.0-100` => v1.0.0, `latest` channel; build **#100**
- `1.0.1-beta.102` => v1.0.1, `beta` channel; build **#102**
- `1.0.12-dev` => v1.0.12 `dev` channel (_no build number_)

When you run `maker-env generate`, the version is validated and applied to all relevant files.
It also creates the **hub.env** file, which defines:

- `$MAKER_HUB_SEMVER_SHORT`: **x.y.z**
- `$MAKER_HUB_SEMVER_MEDIUM`: **x.y.z-branch**
- `$MAKER_HUB_SEMVER_LONG`: **x.y.z-branch.build**

The medium variant is used by package managers (NuGet, NPM).

The `hub.env` file is _gitignored_ so that it may represent local, generated state.

# Release Channels

_The absence of a channel designation in the semantic version implies `latest`._

The `latest` channel is built from the `master` branch on GitHub.

- `beta`: pull requests
- `alpha`: branches (without pull requests)
- `dev`: build created by a development environment

## Bumping a Version

1. Install [maker-builder](maker-builder.md).
2. Run `maker-env bump-version` from the MakerHub GitHub root
3. Get a green build on master & deploy
4. Run `maker-env sync $PROJECT` for each project to use the new version

To return to development mode, run `maker-env dev $PROJECT`.
