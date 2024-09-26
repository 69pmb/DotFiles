---
title: eslint config
---  
Using `@angular-eslint/eslint-plugin@~15.2` and `gts@~5.0`

```json
{
  "extends": [
    "./node_modules/gts/",
    "plugin:@angular-eslint/recommended"
  ],
  "rules": {
    "@angular-eslint/component-selector": [
      "error",
      {
        "type": "element",
        "prefix": "app",
        "style": "kebab-case"
      }
    ],
    "node/no-unpublished-import": ["error"],
    "complexity": ["error", 12],
    "curly": ["warn"],
    "arrow-body-style": ["error", "as-needed"],
    "@typescript-eslint/explicit-function-return-type": [
      "error",
      {
        "allowExpressions": true
      }
    ],
    "no-console": [
      "error",
      {
        "allow": ["warn", "error"]
      }
    ],
    "no-unused-vars": "off",
    "@typescript-eslint/no-unused-vars": ["error", {"args": "all"}],
    "no-duplicate-imports": ["error"],
    "max-lines-per-function": [
      "error",
      {
        "skipBlankLines": true
      }
    ],
    "lines-between-class-members": [
      "error",
      "always",
      {
        "exceptAfterSingleLine": true
      }
    ]
  },
  "plugins": ["@angular-eslint"]
}
```
