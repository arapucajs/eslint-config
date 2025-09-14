# @arapucajs/eslint-config

> Compatible with ESLint 9.0 and Prettier 3.0

<hr>
<br />

<div align="center">
  <h3>ESLint presets used by the Arapuca team</h3>
  <p>The <code>arapucajs/eslint-config</code> ships with the default set of ESLint rules used by the Arapuca team. The presets are tuned to work alongside Prettier and provide both TypeScript and JavaScript support.</p>
</div>

<br />

[![npm-image]][npm-url] [![license-image]][license-url]

## Installation

Install the package from the npm registry.

```sh
npm i -D @arapucajs/eslint-config

# Install peer dependencies
npm i -D eslint@9 prettier@3
```

## Usage

After installation, use one of the following presets depending on the nature of your application/library.

**For package development**: Use the following preset when developing a package

```js
// eslint.config.js
import { configPkg } from '@arapucajs/eslint-config'
export default configPkg()
```

**For app development**: Use the following preset when developing an application

```js
// eslint.config.js
import { configApp } from '@arapucajs/eslint-config'
export default configApp()
```

## Adding additional config blocks

You can pass additional config blocks as multiple arguments to one of the preset functions.

```js
import { configApp, INCLUDE_LIST, GLOBAL_IGNORE_LIST } from '@arapucajs/eslint-config'

export default configApp({
  name: 'Custom config',
  files: INCLUDE_LIST,
  ignores: GLOBAL_IGNORE_LIST,
  plugins: {
    // ESLint plugins go here
  },
  rules: {
    // ESLint rules go here
  },
})
```

## Available exports

The package exports the following functions and constants:

- `configPkg()` - Configuration for package development
- `configApp()` - Configuration for application development
- `INCLUDE_LIST` - Default files to include in linting
- `GLOBAL_IGNORE_LIST` - Files to ignore globally
- `APP_IGNORE_LIST` - Additional files to ignore for applications
- `PLUGINS_LIST` - Default plugins configuration
- `RULES_LIST` - Default rules configuration

## Features

This ESLint configuration includes:

- **Modern ESLint v9 support** with flat config
- **TypeScript and JavaScript support**
- **Prettier integration** with automatic formatting
- **Unicorn plugin** for additional code quality rules
- **Stylistic plugin** for consistent code style
- **Opinionated rules** for clean, readable code

## License

MIT

[npm-image]: https://img.shields.io/npm/v/@arapucajs/eslint-config/latest.svg?style=for-the-badge&logo=npm
[npm-url]: https://www.npmjs.com/package/@arapucajs/eslint-config/v/latest
[license-url]: LICENSE
[license-image]: https://img.shields.io/github/license/arapucajs/eslint-config?style=for-the-badge
