# Front-end starter kit [![Build Status](https://travis-ci.org/springload/frontend-starter-kit.svg?branch=master)](https://travis-ci.org/springload/frontend-starter-kit) [![Coverage Status](https://coveralls.io/repos/github/springload/frontend-starter-kit/badge.svg)](https://coveralls.io/github/springload/frontend-starter-kit) [![Dependency Status](https://david-dm.org/springload/frontend-starter-kit.svg?style=flat-square)](https://david-dm.org/springload/frontend-starter-kit) [![devDependency Status](https://david-dm.org/springload/frontend-starter-kit/dev-status.svg?style=flat-square)](https://david-dm.org/springload/frontend-starter-kit#info=devDependencies)

> Springload's reference and starter kit for front-end development.

| Documentation in [`docs/`](docs/) :book:|
|---------------------|
|[Front-end tech stack](docs/README.md)|
|[Front-end principles](docs/front-end-principles.md)|
|[Frontend guidelines questionnaire](docs/front-end-questionnaire.md)|
|[Launch QA checklists](docs/launch-checklist.md)|
|[Useful tooling](docs/useful-tooling.md)|
|[Demo page](https://rawgit.com/springload/frontend-starter-kit/master/core/templates/demo.html)|

## Installation

> Clone the project on your computer, and install [Node](https://nodejs.org). This project also uses [nvm](https://github.com/springload/frontend-starter-kit/blob/master/docs/useful-tooling.md#nvm).

From the command-line:

```sh
cd ~/Development/sites/
git clone git@github.com:springload/frontend-starter-kit.git
cd frontend-starter-kit
```

To install our dependencies:

```sh
nvm install
# Then, install all project dependencies.
npm install
# Install the git hooks.
./.githooks/deploy
# Install global dependencies to integrate tooling with your editor of choice.
npm install --global sass-lint babel-eslint eslint-config-airbnb eslint eslint-plugin-react eslint-plugin-import eslint-plugin-jsx-a11y
```

## Working on the project

> Everything mentioned in the installation process should already be done.

```sh
# Make sure you use the right node version.
nvm use
# Start the server and the development tools.
npm run start
# Builds frontend assets.
npm run build
# Runs linting.
npm run lint
# Runs tests.
npm run test
# View other available commands with:
npm run
```

### Using the git hooks

> Git hooks automatically check your code before every commit.

```sh
# To enable the hooks, from the project root:
./.githooks/deploy
# To disable the hooks for a single commit, use the --no-verify flag:
git commit --no-verify
```

### Tests

We use [Jest](https://facebook.github.io/jest/) for unit tests.

```sh
# Run all the tests.
npm run test
# Run tests in a watcher.
npm run test:watch
# Run test coverage
npm run test:coverage
# Open the coverage report with:
open coverage/lcov-report/index.html
```

#### Manual tests

- Cross-platform favicons – https://realfavicongenerator.net/favicon_checker
- Structured data (schema.org) – https://search.google.com/structured-data/testing-tool
- Facebook Open Graph metadata – https://developers.facebook.com/tools/debug/sharing/
- Twitter cards metadata — https://cards-dev.twitter.com/validator

### Adding and upgrading dependencies

This project is [shrinkwrapped](https://docs.npmjs.com/cli/shrinkwrap). Its dependencies are locked down in `npm-shrinkwrap.json` file. To update them,

1. Use `npm run lint:versions` to confirm you are using the right node version.
2. Use `npm install <package>` with `--save` or `--save-dev` options to change the dependencies.
3. Check the project still works with the new dependencies / new versions.
4. Run **`npm run lock`** to regenerate `npm-shrinkwrap.json`.
5. Commit this file, and push.

## Deploying a new version

### To production

```sh
npm run deploy
```

From your local machine, it's a good idea to push to the master before pushing to the deploy branch. That way you know that both are up to date.

### Setting up tests on continuous integration

The CI tests require the following setup. Some of those might already be done within the CD build.

```sh
nvm install
npm install
npm install -g david hyperlink
```

Use `npm run test:ci` as part of the test pipeline.

## Documentation

### Code styleguide and linting

The project's code is linted with [ESLint](http://eslint.org/) for JavaScript and [Sass Lint](https://github.com/sasstools/sass-lint) for Sass.

For Sublime Text 3 users, install [SublimeLinter](http://sublimelinter.readthedocs.io/en/latest/), [SublimeLinter-contrib-eslint](https://github.com/roadhump/SublimeLinter-eslint), and [SublimeLinter-contrib-sass-lint](https://github.com/skovhus/SublimeLinter-contrib-sass-lint).

### Browser support

> Copy/paste & adapt [Browser & device support template](https://github.com/springload/frontend-starter-kit/blob/master/docs/README.md#browser--device-support)

### Polyfills

Basic polyfills are included in the starter kit, and loaded via Webpack.

### Analytics

Analytics are set up with Google Analytics.

[JavaScript errors](https://github.com/springload/frontend-starter-kit/search?utf8=%E2%9C%93&q=analyticsException) are tracked in Google Analytics as ["Exceptions"](https://developers.google.com/analytics/devguides/collection/analyticsjs/exceptions). A custom report needs to be created for this data to be visible inside the GA interface.

### Favicons

To generate new favicons,

1. Go to https://realfavicongenerator.net/
2. Upload your favicon source file as an SVG or PNG with a resolution of at least 512x512.
3. Configure the favicon generation. Use specific images for each platform if relevant.
4. Grab the result files, [use ImageOptim to losslessly optimize their size](https://imageoptim.com/) them.
5. Grab the result HTML tags, add it to the [`core/templates/core/includes/favicons.html`](core/templates/core/includes/favicons.html) file.
6. Make sure the files are served by the server as expected.

### Debugging

#### JavaScript

There are a lot of [development aids](https://github.com/springload/frontend-starter-kit/search?utf8=%E2%9C%93&q=process.env.NODE_ENV) within the code. Use them.
