# Hardcore ESLint Shareable Config

[![Travis CI build status](https://img.shields.io/travis/EvgenyOrekhov/eslint-config-hardcore/master.svg?style=flat-square)](https://travis-ci.org/EvgenyOrekhov/eslint-config-hardcore)

## About

[Shareable Configs](https://eslint.org/docs/developer-guide/shareable-configs)
are designed to work with the `extends` feature of `.eslintrc` files.

| Rules                                                                                                     | Total | Enabled |
| --------------------------------------------------------------------------------------------------------- | ----: | ------: |
| [ESLint](https://eslint.org/docs/rules/)                                                                  |   264 | **241** |
| [eslint-plugin-unicorn](https://github.com/sindresorhus/eslint-plugin-unicorn)                            |    46 |  **39** |
| [eslint-plugin-import](https://github.com/benmosher/eslint-plugin-import)                                 |    40 |  **32** |
| [eslint-plugin-sonarjs](https://github.com/SonarSource/eslint-plugin-sonarjs)                             |    25 |  **24** |
| [eslint-plugin-security](https://github.com/nodesecurity/eslint-plugin-security)                          |    13 |  **12** |
| [eslint-plugin-promise](https://github.com/xjamundx/eslint-plugin-promise)                                |    14 |  **11** |
| [eslint-plugin-array-func](https://github.com/freaktechnik/eslint-plugin-array-func)                      |     6 |   **6** |
| [eslint-plugin-eslint-comments](https://github.com/mysticatea/eslint-plugin-eslint-comments)              |     8 |   **6** |
| [eslint-plugin-no-constructor-bind](https://github.com/markalfred/eslint-plugin-no-constructor-bind)      |     2 |   **2** |
| [eslint-plugin-no-use-extend-native](https://github.com/dustinspecker/eslint-plugin-no-use-extend-native) |     1 |   **1** |
| [eslint-plugin-no-secrets](https://github.com/nickdeis/eslint-plugin-no-secrets)                          |     1 |   **1** |
| [eslint-plugin-optimize-regex](https://github.com/BrainMaestro/eslint-plugin-optimize-regex)              |     1 |   **1** |
| [eslint-plugin-json](https://github.com/azeemba/eslint-plugin-json)¹ ²                                    |     1 |   **1** |
| **Total: `hardcore`**                                                                                     |   422 | **377** |
| [eslint-plugin-fp](https://github.com/jfmengels/eslint-plugin-fp)                                         |    17 |  **15** |
| [eslint-plugin-ramda](https://github.com/ramda/eslint-plugin-ramda)                                       |    26 |  **24** |
| **Total: `hardcore` + `hardcore/fp`**                                                                     |   465 | **417** |
| [eslint-plugin-node](https://github.com/mysticatea/eslint-plugin-node)                                    |    26 |  **26** |
| **Total: `hardcore` + `hardcore/fp` + `hardcore/node`**                                                   |   491 | **443** |

¹ eslint-plugin-json actually includes 19 rules, but we consider them as one
"no-invalid-json" rule.

² You have to use the `--ext` option to lint `*.json` files:
`eslint . --ext .js,.json`

## Usage

Install:

```bash
npm install eslint-config-hardcore --save-dev
```

Then, add it to your `.eslintrc` file and specify your
[environments](https://eslint.org/docs/user-guide/configuring#specifying-environments):

```json
{
  "extends": ["hardcore"],
  "env": {
    "browser": true
  }
}
```

## `hardcore/fp`

This config adds rules for functional programming.

Use it **in addition** to the `hardcore` config:

```json
{
  "extends": ["hardcore", "hardcore/fp"],
  "env": {
    "browser": true
  }
}
```

## `hardcore/node`

This config adds rules and globals for Node.js.

Use it **in addition** to other configs:

```json
{
  "extends": ["hardcore", "hardcore/fp", "hardcore/node"]
}
```

Or, if your project contains both non-Node and Node files, use it like this:

```json
{
  "extends": ["hardcore", "hardcore/fp"],
  "env": {
    "browser": true
  },
  "overrides": [
    {
      "files": ["server/**/*.js"],
      "extends": ["hardcore/node"],
      "env": {
        "browser": false
      }
    }
  ]
}
```

## [Changelog](https://github.com/EvgenyOrekhov/eslint-config-hardcore/releases)

## License

[MIT](LICENSE)
