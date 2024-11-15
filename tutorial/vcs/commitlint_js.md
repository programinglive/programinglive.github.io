---
title: Commitlint JS
layout: default
parent: Git
grand_parent: Version Control System
description: "Commitlint JS"
---

## Commitlint JS

In collaborative software projects, consistent commit messages play a key role in code readability and project organization. However, maintaining this consistency can be challenging, especially in larger teams. **Commitlint JS** is a powerful tool that helps enforce commit message conventions, ensuring that every commit follows the same structure and standards.

### What is Commitlint JS?

**Commitlint JS** is a JavaScript tool that validates commit messages to ensure they meet predefined conventions. Commonly used with **Conventional Commits**, Commitlint checks whether each commit message adheres to the required structure, such as including specific types, scopes, and descriptions. By setting rules in Commitlint, you can enforce a consistent format, which is particularly useful for generating changelogs, automating release processes, and improving project history.

### Why Use Commitlint?

Here are some key reasons to use Commitlint in your project:
- **Enforced Standards**: By automatically enforcing rules for commit messages, Commitlint helps maintain consistency across the team.
- **Clearer Git History**: With standardized commit messages, it’s easier to understand the history and purpose of each change.
- **Automated Changelogs**: Commitlint works well with tools that generate changelogs or automate releases, which rely on consistent commit formats.
- **Improved Collaboration**: Commitlint ensures that all contributors, including new team members, follow the same format, improving readability and collaboration.

### Getting Started with Commitlint JS

Let’s go through the steps to set up Commitlint in a JavaScript project.

#### 1. Install Commitlint

To begin, install Commitlint and its config-conventional package. The `@commitlint/config-conventional` configuration enforces Conventional Commits format, which is widely used and recognized.

```bash
npm install --save-dev @commitlint/{config-conventional,cli}
```

#### 2. Configure Commitlint

After installation, create a `commitlint.config.js` file in the root of your project to define Commitlint’s rules. The following configuration file sets up Commitlint to use Conventional Commits:

```javascript
// commitlint.config.js
module.exports = {
  extends: ['@commitlint/config-conventional'],
};
```

This configuration ensures that Commitlint checks for the types and structure defined in Conventional Commits, such as `feat`, `fix`, and `docs`.

#### 3. Integrate Commitlint with Git Hooks

To automatically validate commit messages, you can integrate Commitlint with a Git Hook. This will check each commit message before it’s recorded, preventing commits that don’t meet the standard.

For easier setup, you can use **Husky**, a tool that simplifies managing Git Hooks in JavaScript projects. Install Husky with:

```bash
npm install --save-dev husky
```

Then, set up Husky to run Commitlint on every commit:

```bash
npx husky install
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
```

This configuration will run Commitlint on each commit message, stopping any commit that doesn’t adhere to the rules.

### Customizing Commitlint Rules

Commitlint’s default configuration works well for most projects, but you can customize rules to fit your project’s needs. For example, you can specify allowed commit types, limit message length, or enforce scope presence.

To customize rules, update `commitlint.config.js` as shown below:

```javascript
module.exports = {
  extends: ['@commitlint/config-conventional'],
  rules: {
    'type-enum': [2, 'always', ['feat', 'fix', 'docs', 'style', 'refactor', 'test', 'chore']],
    'subject-case': [2, 'never', ['sentence-case']], // Restrict case in commit subjects
    'subject-max-length': [2, 'always', 72], // Limit commit message length to 72 characters
  },
};
```

In this example:
- **`type-enum`** restricts commit types to specific options.
- **`subject-case`** prevents sentence-case formatting in the commit subject.
- **`subject-max-length`** limits the commit message length for readability.

### Using Commitlint with Other Tools

Commitlint can work alongside other tools for a smooth development process:
- **Commitizen**: This tool provides prompts to help developers create Conventional Commit messages. Integrate Commitizen with Commitlint for easier commit message formatting.
- **semantic-release**: A powerful tool for automating releases, semantic-release uses commit messages to determine version updates and generate changelogs, relying on consistent commit formats.

### Benefits of Using Commitlint JS

- **Improved Documentation**: Commitlint encourages developers to provide meaningful messages, making Git history a more valuable resource.
- **Error Prevention**: Validating commit messages reduces mistakes and ensures consistency, especially across larger teams.
- **Automation Ready**: Tools that depend on commit messages, such as automated release systems, work more effectively with standardized commit logs.

### Conclusion

Commitlint JS is an excellent tool for enforcing commit message consistency and improving project organization. By setting up Commitlint, you can enhance readability, automate changelogs, and create a more collaborative development environment. Consistent commit messages make a world of difference, and with Commitlint, achieving this standard is easy and effective.