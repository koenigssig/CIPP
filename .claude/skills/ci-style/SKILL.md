---
name: ci-style
description: Adopt the CI pipeline and code style of koenigssig/CIPP. Use when you want to set up ESLint, Prettier, EditorConfig, and GitHub Actions workflows matching the CIPP project standards.
---

# CI & Code Style Setup — CIPP Style

Apply the CI pipeline and code style conventions from the [koenigssig/CIPP](https://github.com/KelvinTegelaar/CIPP) project to the current repository.

## Workflow

Make a todo list for all tasks and work through them one at a time.

### 1. Analyze Current Project

Inspect the project to understand its current state:
- Check `package.json` for framework (Next.js, plain React, etc.) and existing lint scripts
- Check for existing `.eslintrc.*`, `.editorconfig`, `.prettierrc.*` files
- Check for `.github/workflows/` directory and existing CI workflows
- Note the primary branch names (main, master, dev, etc.)

### 2. Apply ESLint Configuration

**For all JavaScript/React projects**, create or update `.eslintrc.cjs`:

```js
module.exports = {
  env: {
    browser: true,
    es6: true,
    node: true,
  },
  parserOptions: {
    ecmaVersion: 'latest',
    sourceType: 'module',
    ecmaFeatures: {
      jsx: true,
    },
  },
  settings: {
    react: {
      version: 'detect',
    },
  },
  extends: [
    'eslint:recommended',
    'plugin:import/recommended',
    'plugin:react/recommended',
    'plugin:react/jsx-runtime',
    'plugin:react-hooks/recommended',
    'plugin:prettier/recommended',
  ],
  plugins: ['react-hooks', 'import'],
  rules: {
    'no-unused-vars': 'off',
    'react/prop-types': 'warn',
    'react/no-unescaped-entities': 'off',
  },
}
```

**For Next.js projects only**, also create or update `.eslintrc.json`:

```json
{
  "extends": ["next/core-web-vitals"],
  "rules": {
    "@next/next/no-img-element": "off",
    "@next/next/google-font-display": "off",
    "@next/next/google-font-preconnect": "off",
    "jsx-a11y/alt-text": "off",
    "jsx-a11y/aria-props": "off",
    "jsx-a11y/aria-proptypes": "off",
    "jsx-a11y/aria-unsupported-elements": "off",
    "jsx-a11y/role-has-required-aria-props": "off",
    "jsx-a11y/role-supports-aria-props": "off",
    "react/display-name": "off",
    "react/no-unescaped-entities": "off",
    "react/jsx-max-props-number": ["warn", { "maximum": 10 }]
  }
}
```

Install required ESLint packages if not already present:
```bash
npm install --save-dev eslint eslint-plugin-import eslint-plugin-react eslint-plugin-react-hooks eslint-config-prettier eslint-plugin-prettier prettier
```

For Next.js projects, also install:
```bash
npm install --save-dev eslint-config-next
```

### 3. Apply EditorConfig

Create or update `.editorconfig` at the project root:

```ini
[*]
charset = utf-8
end_of_line = lf
indent_size = 2
indent_style = space
insert_final_newline = false
max_line_length = 100
tab_width = 2
```

### 4. Update package.json Scripts

Ensure `package.json` contains lint scripts. Add if missing:

- For Next.js: `"lint": "next lint"` and `"lint-fix": "next lint --fix"`
- For plain React/JS: `"lint": "eslint ."` and `"lint-fix": "eslint . --fix"`

Edit `package.json` with the appropriate script values, merging into the existing `"scripts"` object.

### 5. Create GitHub Actions CI Workflows

Create the `.github/workflows/` directory if it doesn't exist.

**Create `.github/workflows/Node_Project_Check.yml`** (adapt branch names to match the project):

```yaml
name: NodeJS Project Check
on:
  pull_request:
    branches:
      - main
      - dev
concurrency:
  group: ${{ github.workflow }}-${{ github.event_name == 'pull_request' && github.head_ref || github.ref }}
  cancel-in-progress: false
jobs:
  install-build:
    name: NPM Install and Build
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [20.x]
        os: [ubuntu-latest]
    steps:
      - uses: actions/checkout@v4
      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node-version }}
      - name: Install and Build Test
        run: |
          npm install --legacy-peer-deps
          npm run build
        env:
          CI: true
```

**Create `.github/workflows/pr_check.yml`** (adapt branch names):

```yaml
name: PR Branch Check

on:
  pull_request_target:
    types: [opened, synchronize, reopened]
    branches:
      - main
      - master

permissions:
  pull-requests: write
  issues: write

jobs:
  check-branch:
    runs-on: ubuntu-latest
    steps:
      - name: Check and Comment on PR
        if: |
          github.event.pull_request.head.repo.fork == true &&
          ((github.event.pull_request.head.ref == 'main' || github.event.pull_request.head.ref == 'master') ||
          (github.event.pull_request.base.ref == 'main' || github.event.pull_request.base.ref == 'master'))
        uses: actions/github-script@v7
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          script: |
            let message = '';
            message += '⚠️ PRs cannot target the main branch directly. Please PR to the dev branch.\n\n';
            if (context.payload.pull_request.head.repo.fork &&
                (context.payload.pull_request.head.ref === 'main' || context.payload.pull_request.head.ref === 'master')) {
              message += '⚠️ This PR originates from your fork\'s main/master branch. Please PR from a feature branch.\n\n';
            }
            message += '🔒 This PR will now be automatically closed.';
            await github.rest.issues.createComment({
              ...context.repo,
              issue_number: context.issue.number,
              body: message
            });
            await github.rest.pulls.update({
              ...context.repo,
              pull_number: context.issue.number,
              state: 'closed'
            });
```

### 6. Validate Linter

Run the linter on a single example file to confirm the configuration works:

```bash
npx eslint src/index.js --max-warnings=0
# or for Next.js:
npm run lint -- --file src/pages/index.js
```

If errors occur, fix the ESLint config or install missing plugins.

### 7. Commit and Push

Stage and commit all new/modified files:
```bash
git add .eslintrc.cjs .eslintrc.json .editorconfig .github/workflows/ package.json
git commit -m "chore: adopt CIPP CI pipeline and code style"
git push
```

## Wrap Up

After completing all steps, provide the user with a summary:

* **Changes made**: List every file created or modified
* **Validation results**:
  1. ✅/‼️ ESLint configuration (include error details if failed)
  2. ✅/‼️ EditorConfig applied
  3. ✅/‼️ GitHub Actions workflows created
  4. ✅/‼️ Linter run on sample file
* **Next steps**: Inform the user that the CI workflows will activate on the next PR targeting the configured branches.
