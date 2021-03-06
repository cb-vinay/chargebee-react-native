# Contributing

We want this community to be friendly and respectful to each other. Please follow it in all your interactions with the project.

## Development workflow

To get started with the project, run `yarn bootstrap` in the root directory to install the required dependencies for each package:

```sh
yarn bootstrap
```

While developing, you can run the [example app](/example/) to test your changes.

To start the packager:

```sh
yarn example start
```

To run the example app on Android:

```sh
yarn example android
```

To run the example app on iOS:

```sh
yarn example ios
```

Make sure your code passes TypeScript and ESLint. Run the following to verify:

```sh
yarn typescript
yarn lint
```

To fix formatting errors, run the following:

```sh
yarn lint --fix
```

Remember to add tests for your change if possible. Run the unit tests by:

```sh
yarn test
```

To edit the Objective-C files, open `example/ios/ChargebeeExample.xcworkspace` in XCode and find the source files at `Pods > Development Pods > react-native-chargebee`.

To edit the Kotlin files, open `example/android` in Android studio and find the source files at `reactnativechargebee` under `Android`.

### Commit message convention

We follow the [conventional commits specification](https://www.conventionalcommits.org/en) for our commit messages:

- `fix`: bug fixes, e.g. fix crash due to deprecated method.
- `feat`: new features, e.g. add new method to the module.
- `refactor`: code refactor, e.g. migrate from class components to hooks.
- `docs`: changes into documentation, e.g. add usage example for the module..
- `test`: adding or updating tests, eg add integration tests using detox.
- `chore`: tooling changes, e.g. change CI config.

Our pre-commit hooks verify that your commit message matches this format when committing.
Other available commit types are build, ci, perf, revert, style.
To change/add commit types check https://github.com/conventional-changelog/commitlint

#### Note
When there are any backward incompatible changes please add a footer line to the commit message as below:

`BREAKING CHANGE: <Message>`

This will tag the release automatically as next major version.
For an example, you can take a look at the commit message of commit id `d48c299` in this repo

### Linting and tests

[ESLint](https://eslint.org/), [Prettier](https://prettier.io/), [TypeScript](https://www.typescriptlang.org/)

We use [TypeScript](https://www.typescriptlang.org/) for type checking, [ESLint](https://eslint.org/) with [Prettier](https://prettier.io/) for linting and formatting the code, and [Jest](https://jestjs.io/) for testing.

Our pre-commit hooks verify that the linter and tests pass when committing.

### Scripts

The `package.json` file contains various scripts for common tasks:

- `yarn bootstrap`: setup project by installing all dependencies and pods.
- `yarn typescript`: type-check files with TypeScript.
- `yarn lint`: lint files with ESLint.
- `yarn test`: run unit tests with Jest.
- `yarn example start`: start the Metro server for the example app.
- `yarn example android`: run the example app on Android.
- `yarn example ios`: run the example app on iOS.

### Release
Github token is needed to push a release tag to the repo with `repo` access (`admin` is not needed).

`export GITHUB_TOKEN=<Github Token>`

NPM Token is needed to publish to npm

`export NPM_TOKEN=<Npm token here>`

To release from a local machine in interactive mode
`yarn release`

To do a dry run of the release process
`yarn release --dry-run`

To trigger the release process from CI
`yarn release --ci`
The release process:
 1. Creates a release version in Github
 2. Publishes to npm [More info](https://github.com/release-it/release-it/blob/master/docs/npm.md)

#### Skip publish

To bump the version in `package.json` with the release, but not publish to the registry:

```json
{
  "npm": {
    "publish": false
  }
}
```

#### Ignore version

To ignore the `version` from `package.json`, (and use the latest Git tag instead):

```json
{
  "npm": {
    "ignoreVersion": true
  }
}
```

Or `--npm.ignoreVersion` from the command line.
