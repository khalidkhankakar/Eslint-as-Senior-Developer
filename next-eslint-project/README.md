# 🧠 ESLint Setup in Next.js using `@antfu/eslint-config`

This guide helps you set up **ESLint** in a **Next.js** project using the powerful and opinionated [`@antfu/eslint-config`](https://github.com/antfu/eslint-config). It includes TypeScript support, custom rules, and VS Code integration for a seamless development experience.

---

## 🚀 Getting Started

### 1. Create a Next.js App

You can use any tool to bootstrap your app:

```bash
# Using NPX
npx create-next-app@latest

# Using BUN
bunx create-next-app

# Using Yarn
yarn create next-app
```

## 2. 🧩 Install ESLint & Antfu Config

Once your Next.js app is created, install **ESLint** along with **@antfu/eslint-config** using your preferred package manager.

### Using pnpm (recommended)
```bash
pnpm i -D eslint @antfu/eslint-config
```
### Or using npm
```bash
npm i -D eslint @antfu/eslint-config
```
### Or using yarn
```bash
yarn add -D eslint @antfu/eslint-config
```

### Or using bun
```bash
bun add -d eslint @antfu/eslint-config
```

## 3. ⚙️ Create ESLint Configuration File

Now, create a file named **`eslint.config.mjs`** in the root of your project and paste the following configuration:

```js
import antfu from "@antfu/eslint-config";

export default antfu(
  {
    type: "app",
    typescript: true,
    formatters: true,
    stylistic: {
      indent: 2,
      semi: true,
      quotes: "double",
    },
  },
  {
    rules: {
      "ts/no-redeclare": "off",
      "ts/consistent-type-definitions": ["error", "type"],
      "no-console": ["warn"],
      "antfu/no-top-level-await": ["off"],
      "node/prefer-global/process": ["off"],
      "node/no-process-env": ["error"],
      "perfectionist/sort-imports": [
        "error",
        {
          tsconfigRootDir: ".",
        },
      ],
      "unicorn/filename-case": [
        "error",
        {
          case: "kebabCase",
          ignore: ["README.md"],
        },
      ],
    },
  }
);

```
---

### ✅ Step 4: Setup VS Code for Auto-Fix on Save


## 4. 🛠️ Setup VS Code for Auto-Fix on Save

To make ESLint auto-fix your code whenever you save a file in **Visual Studio Code**, create a file at **`.vscode/settings.json`** and paste the following:

```json
{
  "prettier.enable": false,
  "editor.formatOnSave": false,

  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit",
    "source.organizeImports": "never"
  },

  "eslint.rules.customizations": [
    { "rule": "style/*", "severity": "off", "fixable": true },
    { "rule": "format/*", "severity": "off", "fixable": true },
    { "rule": "*-indent", "severity": "off", "fixable": true },
    { "rule": "*-spacing", "severity": "off", "fixable": true },
    { "rule": "*-spaces", "severity": "off", "fixable": true },
    { "rule": "*-order", "severity": "off", "fixable": true },
    { "rule": "*-dangle", "severity": "off", "fixable": true },
    { "rule": "*-newline", "severity": "off", "fixable": true },
    { "rule": "*quotes", "severity": "off", "fixable": true },
    { "rule": "*semi", "severity": "off", "fixable": true }
  ],

  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact",
    "vue",
    "html",
    "markdown",
    "json",
    "jsonc",
    "yaml",
    "toml",
    "xml",
    "gql",
    "graphql",
    "astro",
    "svelte",
    "css",
    "less",
    "scss",
    "pcss",
    "postcss"
  ]
}

```

## 5. 🚀 Add Lint Script to `package.json`

To easily lint and fix your codebase, add the following script to your `package.json` file:

```json
{
  "scripts": {
    "lint:fix": "eslint . --fix"
  }
}
```
### 6. 🎉 Run your script
```bash
pnpm lint:fix
```
# or
```bash
npm run lint:fix
```
# or
```bash
yarn lint:fix
```
# or
```bash
bun run lint:fix
```

### ✅ Done!
You're now all set with a clean and powerful ESLint setup using @antfu/eslint-config! 🧼🔥

