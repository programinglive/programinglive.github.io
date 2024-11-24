---
title: Git Conventional Commit
layout: default
parent: Git
grand_parent: Version Control System
description: "Git Conventional Commit"
---

# Git Conventional Commits

**Conventional Commits** is a standardized format for commit messages that aims to make version control history more
structured and machine-readable. By adhering to a set of defined rules for commit message formatting, teams can automate
tasks such as changelog generation, versioning, and release management. This approach provides clarity about the nature
of each change made to the codebase and enables automation for tools like semantic versioning.

---

## Table of Contents

- [What are Conventional Commits?](#what-are-conventional-commits)
- [Structure of a Conventional Commit](#structure-of-a-conventional-commit)
- [Commit Types](#commit-types)
- [Scope](#scope)
- [Message Format](#message-format)
- [Example Commit Messages](#example-commit-messages)
- [Why Use Conventional Commits?](#why-use-conventional-commits)
- [Automating Versioning and Changelog with Conventional Commits](#automating-versioning-and-changelog-with-conventional-commits)
- [Tools for Enforcing Conventional Commits](#tools-for-enforcing-conventional-commits)
- [Conclusion](#conclusion)

---

## What are Conventional Commits?

Conventional Commits is a specification for writing standardized commit messages. It encourages developers to use a
consistent format for commit messages, making it easier to understand the purpose of a change, track the evolution of a
project, and automate tasks like changelog generation and versioning. The goal is to create a clear and structured
commit history.

---

## Structure of a Conventional Commit

A conventional commit follows this basic structure:

```
<type>(<scope>): <message>
```

- **type**: A keyword describing the type of change.
- **scope**: An optional part to specify the area of the codebase affected by the change (e.g., a specific module,
  feature, or subsystem).
- **message**: A short, concise description of the change.

### Full Commit Message Example:

```
feat(auth): add login functionality
```

This structure makes it clear that:

- The change is a **feature** (`feat`).
- The scope is **authentication** (`auth`).
- The change adds **login functionality**.

---

## Commit Types

The **type** defines the category of the change. The most common types used in Conventional Commits include:

- **feat**: A new feature.
- **fix**: A bug fix.
- **docs**: Documentation changes.
- **style**: Code style changes (e.g., formatting, missing semi-colons) that do not affect the logic.
- **refactor**: Code changes that neither fix a bug nor add a feature (e.g., restructuring code).
- **perf**: Performance improvements.
- **test**: Adding or modifying tests.
- **chore**: Routine tasks such as configuration changes or updates to build tools.
- **ci**: Continuous Integration related changes (e.g., updating CI configuration files).
- **build**: Changes to the build process (e.g., adding a new build tool).
- **revert**: Reverts a previous commit.

---

## Scope

The **scope** is an optional part of the commit message that describes the area of the codebase impacted by the change.
For example, in the commit:

```
feat(auth): add login functionality
```

- **auth** is the scope, indicating that the change is related to the authentication system.

Scopes are particularly helpful for larger projects where different parts of the application are managed by different
teams. It helps narrow down what area the commit is related to.

---

## Message Format

The **message** part of the commit should provide a clear and concise description of what the change is and why it was
made. This part should be written in the **imperative mood**, which is typically used to describe actions (e.g., "Add
feature," "Fix bug," "Update docs").

### Good Practices for Commit Messages:

- Be clear and concise.
- Use the imperative mood.
- Capitalize the first letter of the message.
- Avoid using unnecessary punctuation (e.g., no periods at the end of the message).

---

## Example Commit Messages

Here are some examples of valid commit messages using Conventional Commits:

- `feat(auth): implement login API`
- `fix(button): resolve issue with button click event`
- `docs(readme): update installation instructions`
- `style(css): clean up unused classes`
- `refactor(code): simplify auth logic`
- `test(auth): add unit tests for login function`
- `perf(api): optimize data fetching logic`
- `chore(config): update build configuration`
- `ci(cicd): update deployment pipeline`

---

## Why Use Conventional Commits?

There are several benefits to using Conventional Commits in your project:

### 1. **Clarity and Consistency**

Commit messages follow a consistent format, making it easy for developers to understand the nature of each change in the
project history.

### 2. **Automated Versioning**

Conventional Commits are compatible with tools like **semantic versioning**, which automatically adjust version numbers
based on commit types. For example:

- `feat` (new features) bump the major version.
- `fix` (bug fixes) bump the patch version.
- Breaking changes can be detected and bump the major version.

### 3. **Changelog Generation**

By following a consistent commit message format, you can automatically generate a changelog that summarizes the
project's changes. Tools like **standard-version** or **semantic-release** can automate this process.

### 4. **Improved Collaboration**

Standardized commit messages improve communication within teams and across different teams working on the same project,
as everyone follows the same guidelines.

---

## Automating Versioning and Changelog with Conventional Commits

Tools like **semantic-release** and **standard-version** can automatically manage versioning and changelog generation
based on commit messages that follow the Conventional Commit format.

- **semantic-release**: This tool automates the versioning and changelog generation process by analyzing the commit
  history and determining the correct version bump based on commit types. It can also publish the release to npm and
  generate release notes.

- **standard-version**: A simpler tool that creates version tags and changelogs based on conventional commits. It helps
  automate the release process, ensuring the version is incremented according to the rules of semantic versioning.

---

## Tools for Enforcing Conventional Commits

To ensure that all commits follow the Conventional Commit format, you can use tools like **Commitlint** and **Husky**:

- **Commitlint**: A tool that checks if your commit messages follow the specified conventions. It can be configured with
  a variety of rules.
- **Husky**: A tool that allows you to run Git hooks, like `commit-msg`, to enforce commit message rules before a commit
  is made.
- **Commitizen**: A tool that helps developers format their commit messages according to a specific convention, making
  it easier to follow the Conventional Commit guidelines.

---

## Conclusion

Conventional Commits provide a clear and standardized format for writing commit messages, which makes it easier to
understand changes, automate versioning, and generate changelogs. By using these conventions, teams can improve
collaboration, automate tedious tasks, and ensure a consistent project history. Integrating tools like **Commitlint**, *
*Husky**, and **semantic-release** makes enforcing this process easy, helping teams maintain a clean and organized
development workflow.