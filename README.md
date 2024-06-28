# @jihyunlab/prettier-config

[![Version](https://img.shields.io/npm/v/@jihyunlab/prettier-config.svg?style=flat-square)](https://www.npmjs.com/package/@jihyunlab/prettier-config?activeTab=versions) [![Downloads](https://img.shields.io/npm/dt/@jihyunlab/prettier-config.svg?style=flat-square)](https://www.npmjs.com/package/@jihyunlab/prettier-config) [![Last commit](https://img.shields.io/github/last-commit/jihyunlab/prettier-config.svg?style=flat-square)](https://github.com/jihyunlab/prettier-config/graphs/commit-activity) [![License](https://img.shields.io/github/license/jihyunlab/prettier-config.svg?style=flat-square)](https://github.com/jihyunlab/prettier-config/blob/master/LICENSE) [![Linter](https://img.shields.io/badge/linter-eslint-blue?style=flat-square)](https://eslint.org) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)\
[![Build](https://github.com/jihyunlab/prettier-config/actions/workflows/build.yml/badge.svg)](https://github.com/jihyunlab/prettier-config/actions/workflows/build.yml) [![Lint](https://github.com/jihyunlab/prettier-config/actions/workflows/lint.yml/badge.svg)](https://github.com/jihyunlab/prettier-config/actions/workflows/lint.yml)

JihyunLab Prettier config.

## Installation

```bash
npm i --save-dev @jihyunlab/prettier-config prettier eslint-config-prettier eslint-plugin-prettier
```

## Configuration

### Configure Prettier

Create and edit the <U>prettier.config.mjs</U> file.

```
├─ prettier.config.mjs
└─ ...
```

```
import { jihyunlabPrettierConfig } from '@jihyunlab/prettier-config';

export default {
  ...jihyunlabPrettierConfig,
};
```

### Configure Prettier Ignore

Create and edit the <U>.prettierignore</U> file.

```
├─ .prettierignore
└─ ...
```

```
/node_modules
/build
/dist
/coverage
```

### Configure ESLint for Prettier

When using ESLint, Edit the <U>eslint.config.mjs</U> file.
For ESLint installation and configuration, see [@jihyunlab/eslint-config](https://www.npmjs.com/package/@jihyunlab/eslint-config).

```
├─ eslint.config.mjs
└─ ...
```

```
import eslint from '@eslint/js';
import tsEslint from 'typescript-eslint';
import eslintPluginPrettierRecommended from 'eslint-plugin-prettier/recommended';
import { jihyunlabEslintConfig } from '@jihyunlab/eslint-config';

export default tsEslint.config(
  {
    ignores: ['node_modules', 'dist', 'build', 'coverage'],
  },
  {
    languageOptions: {
      parserOptions: {
        project: './tsconfig.eslint.json',
        tsconfigRootDir: import.meta.dirname,
      },
    },
  },
  {
    files: ['**/*.ts', '**/*.tsx', '**/*.cts', '**/*.mts'],
    extends: [
      eslint.configs.recommended,
      ...tsEslint.configs.recommendedTypeChecked,
      jihyunlabEslintConfig,
      eslintPluginPrettierRecommended,
    ],
  }
);
```

### Configure VSCode for Prettier

When using VSCode, create and edit the <U>.vscode/settings.json</U> file.

```
├─ .vscode
│  └─ settings.json
└─ ...
```

```
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true
}
```

## Credits

Authored and maintained by JihyunLab <<info@jihyunlab.com>>

## License

Open source [licensed as MIT](https://github.com/jihyunlab/prettier-config/blob/master/LICENSE).
