# @jihyunlab/prettier-config

[![Version](https://img.shields.io/npm/v/@jihyunlab/prettier-config.svg?style=flat-square)](https://www.npmjs.com/package/@jihyunlab/prettier-config?activeTab=versions) [![Downloads](https://img.shields.io/npm/dt/@jihyunlab/prettier-config.svg?style=flat-square)](https://www.npmjs.com/package/@jihyunlab/prettier-config) [![Last commit](https://img.shields.io/github/last-commit/jihyunlab/prettier-config.svg?style=flat-square)](https://github.com/jihyunlab/prettier-config/graphs/commit-activity) [![License](https://img.shields.io/github/license/jihyunlab/prettier-config.svg?style=flat-square)](https://github.com/jihyunlab/prettier-config/blob/master/LICENSE) [![Linter](https://img.shields.io/badge/linter-eslint-blue?style=flat-square)](https://eslint.org) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)\
[![Build](https://github.com/jihyunlab/prettier-config/actions/workflows/build.yml/badge.svg)](https://github.com/jihyunlab/prettier-config/actions/workflows/build.yml) [![Lint](https://github.com/jihyunlab/prettier-config/actions/workflows/lint.yml/badge.svg)](https://github.com/jihyunlab/prettier-config/actions/workflows/lint.yml)

JihyunLab Prettier config.

## Setup

### 1) Setup regular JihyunLab Prettier config

```bash
npm i --save-dev @jihyunlab/prettier-config
```

or

```bash
yarn add --dev @jihyunlab/prettier-config prettier@^2.8.4 eslint-config-prettier@^8.6.0 eslint-plugin-prettier@^4.2.1
```

### 2) Configure Prettier

.prettierrc.js file structure

    .
    ├── .prettierrc.js
    └── ...

Within your .prettierrc.js file:

```diff
+ module.exports = {
+   ...require('@jihyunlab/prettier-config')
+ };
```

Example .prettierrc.js file:

```diff
module.exports = {
  ...require('@jihyunlab/prettier-config'),
  printWidth: 120, // your additional prettier configs
};
```

Restart the editor after changing the prettier config.

### 3) Conflict handling with ESLint and setting Prettier error display in ESLint

Delete Prettier related configs in ESLint.

Within your .eslintrc.json file:

```diff
"extends": [
  "@jihyunlab/eslint-config",
+ "prettier"
]
```

Setting Prettier error display in ESLint.

Within your .eslintrc.json file:

```diff
"plugins": [
+ "prettier"
],
"rules": {
+ "prettier/prettier": "error"
}
```

Example .eslintrc.json file:

```diff
{
  "extends": [
    "@jihyunlab/eslint-config", // your eslint extends
    "prettier"
  ],
  "plugins": [
    "prettier"
  ],
  "parserOptions": {
    "project": "./tsconfig.json"
  },
  "rules": {
    "prettier/prettier": "error"
  }
}
```

## Additional settings

Additional settings file structure

    .
    ├── .vscode                   # Visual Studio Code
    │   ├── extensions.json
    │   ├── settings.json
    ├── .editorconfig             # EditorConfig
    ├── .prettierignore           # Ignore file(Prettier)
    └── ...

Additional configuration files can be found on the git page.

https://github.com/jihyunlab/prettier-config

### 1) Ignore file

Example .prettierignore file:

```diff
/node_modules
/build
/dist
```

### 2) EditorConfig

Example .editorconfig file:

```diff
root = true

[*]
indent_style = space
indent_size = 2
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true

[*.md]
trim_trailing_whitespace = false
```

### 3) Visual Studio Code

Within your .vscode/extensions.json file:

```diff
{
  "recommendations": [
+   "esbenp.prettier-vscode",
+   "editorconfig.editorconfig"
  ]
}
```

Within your .vscode/settings.json file:

```diff
{
+ "editor.defaultFormatter": "esbenp.prettier-vscode",
+ "editor.formatOnSave": true
}
```

## JihyunLab Prettier configs

```diff
{                                       # Default
  "printWidth": 80,                     # 80
  "tabWidth": 2,                        # 2
  "useTabs": false,                     # false
  "semi": true,                         # true
  "singleQuote": true,                  # false
  "quoteProps": "as-needed",            # "as-needed"
  "jsxSingleQuote": false,              # false
  "trailingComma": "es5",               # "es5"
  "bracketSpacing": true,               # true
  "bracketSameLine": false,             # false
  "arrowParens": "always",              # "always"
  "proseWrap": "preserve",              # "preserve"
  "htmlWhitespaceSensitivity": "css",   # "css"
  "endOfLine": "auto",                  # "lf"
  "singleAttributePerLine": false       # false
}
```

## Credits

Authored and maintained by JihyunLab <<info@jihyunlab.com>>

## License

Open source [licensed as MIT](https://github.com/jihyunlab/prettier-config/blob/master/LICENSE).
