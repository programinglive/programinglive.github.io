---
layout: default
title: What is Husky?
parent: JavaScript
grand_parent: FAQ
description: "What is Husky?"
---

## What is Husky?

**Husky** is a tool used in JavaScript projects to manage Git hooks, which are scripts that Git runs at certain points
in the development process (such as before committing or pushing code). Husky makes it easy to add and configure these
Git hooks directly from your project, improving the quality and consistency of your codebase by automating tasks like
linting, testing, and formatting.

By using Husky, you can ensure that developers follow certain rules (like passing tests or meeting code style
guidelines) before they commit or push their changes. This helps prevent issues from being introduced into the codebase,
improves collaboration, and maintains high code quality throughout the development lifecycle.

### Table of Contents

- [Key Features of Husky](#key-features-of-husky)
- [How Husky Works](#how-husky-works)
- [Common Use Cases for Husky](#common-use-cases-for-husky)
- [Setting Up Husky in a Project](#setting-up-husky-in-a-project)
- [Conclusion](#conclusion)

---

## Key Features of Husky:

1. **Git Hook Integration**: Husky allows you to easily configure Git hooks like `pre-commit`, `pre-push`,
   and `commit-msg` to enforce rules before changes are committed to the repository.
2. **Easy to Use**: It provides simple configuration options and integrates seamlessly with modern JavaScript tools like
   ESLint, Prettier, and testing frameworks.
3. **Prevents Bad Commits**: Husky can automatically run tasks such as linting and testing before code is committed,
   ensuring that only code that meets the standards is pushed to the repository.
4. **Customizable**: You can define custom Git hook behaviors for various stages of the Git workflow, from committing to
   pushing and beyond.
5. **Works with Other Tools**: Husky integrates well with tools like lint-staged, which only runs tasks on staged files,
   making it more efficient.

---

## How Husky Works:

Husky works by using Git hooks. Git hooks are scripts that Git executes during certain actions, such as when a commit is
made (`pre-commit`), before a push (`pre-push`), or before a commit message is written (`commit-msg`). These hooks are
typically set up in the `.git/hooks` directory.

Husky simplifies the process of adding and managing Git hooks. Once installed, it allows you to define commands to run
at each stage of the Git process using a configuration file or `package.json`. For example, Husky can run linting or
testing scripts before a commit is finalized, ensuring that only quality code is committed to the repository.

---

## Common Use Cases for Husky:

1. **Linting Code**: Run ESLint or Prettier before commits to enforce coding standards and automatically fix issues
   before the code is committed.

   Example:
   ```bash
   "lint-staged": {
     "*.js": "eslint --fix"
   }
   ```

2. **Running Tests**: Ensure that all tests pass before code is pushed to the repository.

   Example:
   ```bash
   "scripts": {
     "test": "jest"
   },
   "husky": {
     "hooks": {
       "pre-push": "npm test"
     }
   }
   ```

3. **Commit Message Validation**: Ensure that commit messages follow a specific format, such as using conventional
   commit conventions.

   Example:
   ```bash
   "husky": {
     "hooks": {
       "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
     }
   }
   ```

4. **Preventing Dangerous Commands**: Restrict or block certain Git commands from being executed unless specific
   conditions are met, such as preventing force pushes.

---

## Setting Up Husky in a Project:

To get started with Husky, follow these steps:

1. **Install Husky**: Install Husky as a dev dependency in your project.

   ```bash
   npm install husky --save-dev
   ```

2. **Enable Git Hooks**: Husky can automatically add Git hooks for your project. To enable Git hooks, run the following
   command:

   ```bash
   npx husky install
   ```

3. **Add Hooks to `package.json`**: Configure the hooks you want to use in the `husky` section of your `package.json` or
   via dedicated hook scripts.

   Example (using `pre-commit` hook to run linting):
   ```json
   "husky": {
     "hooks": {
       "pre-commit": "npm run lint"
     }
   }
   ```

4. **Set Up `lint-staged` (optional)**: If you want to run commands only on staged files (such as linting or
   formatting), install `lint-staged`.

   ```bash
   npm install lint-staged --save-dev
   ```

   Then, configure `lint-staged` in `package.json`:
   ```json
   "lint-staged": {
     "*.js": "eslint --fix"
   }
   ```

5. **Commit the Changes**: Once the hooks are set up, Husky will run automatically at the specified stages (e.g., before
   each commit).

---

## Conclusion:

Husky is a powerful tool for managing Git hooks, helping developers automate workflows such as linting, testing, and
commit message validation. By integrating Husky into your project, you can enforce quality standards, catch errors
early, and ensure that only properly formatted, tested, and linted code is committed to the repository. It is simple to
set up and highly customizable, making it an essential tool for teams looking to improve code quality and automate
repetitive tasks.  