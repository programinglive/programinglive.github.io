---
title: Commitlint in JavaScript
layout: default
parent: Git
grand_parent: Version Control System
description: "Commitlint in JavaScript"
---

# Commitlint in JavaScript

**Commitlint** is a tool used to ensure that commit messages in a Git repository adhere to a specific convention or
style. It checks commit messages for proper formatting according to predefined rules or configurations, ensuring
consistency in commit messages across a project. This is particularly useful in team projects, where standardizing
commit messages can help with readability, versioning, and automated changelog generation.

Commitlint is commonly used alongside **Husky** and **Lint-staged** to enforce commit message rules during the Git
commit process.

---

## Table of Contents

- [What is Commitlint?](#what-is-commitlint)
- [How Does Commitlint Work?](#how-does-commitlint-work)
- [Setting Up Commitlint](#setting-up-commitlint)
- [Using Commitlint with Conventional Commits](#using-commitlint-with-conventional-commits)
- [Commitlint Configuration](#commitlint-configuration)
- [Example Commit Messages](#example-commit-messages)
- [Integrating Commitlint with Husky](#integrating-commitlint-with-husky)
- [Conclusion](#conclusion)

---

## What is Commitlint?

Commitlint is a tool that validates your commit messages based on a set of rules. The primary goal is to ensure that
commit messages follow a consistent format, which is especially useful when generating changelogs or creating automated
tools for versioning.

It typically follows a **Conventional Commit** style, which is a widely adopted standard. Conventional Commits are
structured messages that include information about the type of change being made and an optional scope.

---

## How Does Commitlint Work?

Commitlint works by inspecting commit messages and ensuring they follow a specific convention. If a commit message
violates the specified format, it will reject the commit and display an error message. The process can be automated by
integrating Commitlint into your Git workflow using **Husky**, which runs the commitlint checks before each commit is
finalized.

---

## Setting Up Commitlint

To set up Commitlint in your JavaScript project, follow these steps:

### 1. Install Commitlint

You need to install `commitlint` and its configuration package:

```bash
npm install --save-dev @commitlint/{config-conventional,cli}
```

This installs the Commitlint CLI tool and the conventional config that adheres to the **Conventional Commits**
specification.

### 2. Create a Commitlint Configuration File

After installing Commitlint, create a configuration file named `commitlint.config.js` in the root of your project.

```javascript
module.exports = {
	extends: ['@commitlint/config-conventional']
};
```

This file tells Commitlint to use the default **Conventional Commits** configuration. You can customize it further if
needed.

---

## Using Commitlint with Conventional Commits

**Conventional Commits** is a standard for commit messages, and using Commitlint ensures that all your commit messages
follow this pattern. A typical commit message follows this format:

```
<type>(<scope>): <message>
```

- **type**: Describes the type of change. Common types include:
    - `feat`: New feature
    - `fix`: Bug fix
    - `docs`: Documentation changes
    - `chore`: Routine tasks like refactoring or build configuration
    - `style`: Code style changes (no changes to logic)
    - `refactor`: Code changes that neither fix a bug nor add a feature
    - `test`: Adding or modifying tests
    - `perf`: Performance improvements
- **scope**: Optional, a section to specify the area of the codebase being changed (e.g., `ui`, `api`, `auth`).
- **message**: A brief description of the change.

### Example of Conventional Commit Messages:

- `feat(auth): add login functionality`
- `fix(api): handle null values in user data`
- `docs(readme): update API documentation`
- `chore(build): update webpack config`
- `style(ui): fix button alignment`

---

## Commitlint Configuration

You can extend or modify the Commitlint rules by creating a custom configuration. The `@commitlint/config-conventional`
is a good starting point, but if you need specific rules, you can override them in your `commitlint.config.js` file.

### Example: Customizing Commitlint Configuration

```javascript
module.exports = {
	extends: ['@commitlint/config-conventional'],
	rules: {
		'type-enum': [
			2,
			'always',
			['feat', 'fix', 'docs', 'chore', 'style', 'refactor', 'test', 'perf']
		],
		'subject-min-length': [2, 'always', 10],  // Enforce a minimum length of 10 characters for the subject
		'subject-case': [2, 'always', 'sentence-case'],  // Enforce sentence case for the subject
	}
};
```

This example overrides the `type-enum` rule to only allow certain commit types, ensures that the commit message subject
is at least 10 characters long, and forces sentence case for the subject line.

---

## Example Commit Messages

Here are some examples of valid commit messages with the Conventional Commits format:

- `feat(auth): implement two-factor authentication`
- `fix(api): correct endpoint URL for fetching user data`
- `chore(tests): add unit tests for validation module`
- `docs(readme): update instructions for setting up the project`
- `style(ui): improve layout of the dashboard page`

---

## Integrating Commitlint with Husky

To automate commit message checks, it's common to integrate Commitlint with **Husky**. Husky is a tool that allows you
to run scripts before certain Git hooks, such as `pre-commit`, `commit-msg`, or `pre-push`. Here's how you can integrate
Commitlint into your workflow:

### 1. Install Husky

```bash
npm install --save-dev husky
```

### 2. Enable Git Hooks with Husky

After installing Husky, you need to enable the Git hooks:

```bash
npx husky install
```

### 3. Add a `commit-msg` Hook to Run Commitlint

You can now configure Husky to run Commitlint during the `commit-msg` Git hook, which is triggered when a commit message
is created:

```bash
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit $1'
```

This command tells Husky to run Commitlint on the commit message before allowing the commit to proceed. If the message
doesn't follow the defined rules, the commit will be rejected.

---

## Conclusion

Commitlint is a valuable tool for enforcing consistent commit message conventions, which can help maintain a clean
project history, improve collaboration, and automate processes like changelog generation. By setting up Commitlint with
**Conventional Commits** and integrating it with **Husky**, you ensure that all team members follow the same standards
for commit messages, improving the maintainability of the codebase.