# MakerBuilder

The `@openworkshop/maker-builder` toolchain contains various `maker-` prefixed commands for the shell. It expects to find one or more GitHub projects as sub-folders within `./src/projects`.

## Installation

- Install from source (recommended): `npm install -g ./src/maker-builder`
- Install from NPM: `npm install -g @opeworkshop/maker-builder`

## Commands

_Type any of the commands with `--help` to learn more_.

_BTD stands for builds, tests, and deploys_.

- `maker-env`: generates `hub.env` and `maker.env` for runtime.
- `maker-electron`: BTD desktop (Electron) apps.
- `maker-container`: BTD docker containers.
- `maker-npm`: BTD npm packages.
- `maker-nuget`: BTD nuget packages.
- `maker-pipeline`: generates CI build steps.
- `maker-docs`: generates `.tsx` docs from `.md` files.

## Bumping Versions

See [Versioning](versioning.md).
