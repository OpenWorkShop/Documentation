# Development Essentials

## Prerequisites

- A linux or unix (mac) computer.
- NodeJS v16 ([download](https://nodejs.org/en/download/current/))
- Yarn (`npm install -g yarn`)
- Dotnet 5 SDK ([download](https://dotnet.microsoft.com/download/dotnet/5.0))

## Development Workflow

1. Clone the repository (e.g., `git clone https://github.com/OpenWorkShop/MakerHub.git`)
2. Check out a branch (`git checkout -b my-sweet-feature`)
3. (Re) install the [@openworkshop/maker-builder toolchain](maker-builder.md).
4. Set up a project (below) if you have not done so.
5. Follow a normal git workflow. Pre-commit hooks should do most of the rest of the work.

For releases/deployments, see [versioning](versioning.md).

### Setting Up a Project

For example, to check out the Makerverse project...

```
MAKER_HUB_PROJECT="Makerverse"
GH_SRC="https://github.com/makermadecnc/makerverse.git"
```

You could change the above variables to other projects, and all the following commands will still work. Start by cloning the git repository:

```
mkdir -p "src/projects/$MAKER_HUB_PROJECT"
git clone "$GH_SRC" "src/projects/$MAKER_HUB_PROJECT"
```

Then, you'll want to enable development mode.

```
maker-env dev "$MAKER_HUB_PROJECT"
```

NPM packages will be linked such that they use the `MakerHub` from the root of this repository. This will be automatically switched off later, as a `pre-commit` hook.

### Optimal IDE / Dev. Exp.

To do both frontend and backend work, I use JetBrains' WebStorm (TypeScript/JavaScript) and Rider (C#).
As such, the repository comes with `*.sln` and various web config files.
It is a good idea to set your **build/run** hotkey/action to `yarn start-frontend` and `yarn start-backend` for the respective IDEs.

Other options, like Sublime, are also viable. Just use `yarn start` for a one-line, forked development server. The project directories get large, so you probably want to ensure you have good exclusion patterns set (see: `.gitignore` file tree).

### Development & Testing

If you've set up your project (above), you should now simply be able to start the Makerverse app in development mode:

```
yarn start
```

This monorepo provides various components:

- [**npm**] `@openworkshop/maker-builder`: CI CLI toolchain for building, testing, and deploying projects.
- [**npm**] `@openworkshop/maker-hub`: Core frontend components that run MakerHub
- [**nuget**] `OpenWorkShop.MakerHub`: Core backend components that serve MakerHub.
- [**docker**] `openworkshop/hub-base`: cross-architecture base image capable of running a MakerHub project.
- [**docker**] `openworkshop/maker-builder`: CI container capable of building a MakerHub project.

### Versioning & Commits

- If you are making changes to your project, first `cd src/$MAKER_HUB_PROJECT` to execute commands from your GitHub source root.
- In any case, simply call `maker-env bump-version` to generate a new minor-bump in the semantic version.

When you later make a commit, the git pre-commit hook will switch the project into "production" mode (disabling development) by automatically running `maker-env sync Makerverse`.
This will also sanitize & update the `yarn.lock` files.

_Notice!_ When the pre-commit hook runs, if it makes changes, you should add & amend them to your git changes:

```
git add *
git commit --amend
```

Be careful to only do this once you have a commit on your branch.

## Pull Requests

MakerHub uses a standard workflow:

- Semantic versioning is applied by `maker-env bump-version` (see [versioning](versioning.md))
- Merging directly to master is forbidden.
- Pull Requests are reviewed by maintainers.
- CI (Continuous Integration) builds applications.

### Containerized Builds

You can find Docker containers with all the required build tools pre-installed for Linux (`debian:stable-slim`), with multi-arch support for `x64` and `armhf` at `http://openworkshop/maker-builder:latest`.
