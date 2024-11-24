---
title: Git Hook
layout: default
parent: Git
grand_parent: Version Control System
description: "Git Hook"
---

# Git Hooks

**Git hooks** are scripts that Git executes before or after certain events, such as committing, merging, or pushing
changes. These hooks can be used to automate workflows, enforce standards, and perform checks, making them a powerful
tool for improving the quality and consistency of your codebase.

Git hooks are stored as executable scripts in the `.git/hooks/` directory of a repository. By using Git hooks,
developers can customize the behavior of Git during key phases of the Git workflow, such as pre-commit, post-commit,
pre-push, and more.

---

## Table of Contents

- [What are Git Hooks?](#what-are-git-hooks)
- [Common Types of Git Hooks](#common-types-of-git-hooks)
- [How to Set Up Git Hooks](#how-to-set-up-git-hooks)
- [Using Git Hooks for Automation](#using-git-hooks-for-automation)
- [Popular Git Hook Examples](#popular-git-hook-examples)
- [Git Hook Configuration with Husky](#git-hook-configuration-with-husky)
- [Conclusion](#conclusion)

---

## What are Git Hooks?

Git hooks are scripts that run at specific points in the Git lifecycle. You can use hooks to enforce policies (such as
commit message conventions), automate tasks (such as running tests before pushing code), or modify Git's default
behavior. For example, you could use a hook to prevent commits that contain debug statements, automatically format your
code, or update documentation.

Git hooks are available in every Git repository. They are located in the `.git/hooks` directory of the project. By
default, this directory contains example scripts for common Git hook types, which can be used as templates.

---

## Common Types of Git Hooks

Git hooks can be divided into two categories:

1. **Client-Side Hooks**: These run locally on your machine.
2. **Server-Side Hooks**: These run on the server, typically in the context of a central Git repository or remote
   server.

### Client-Side Hooks

These hooks are used to customize or enforce local behavior in your Git workflow.

- **pre-commit**: Runs before a commit is made. This is typically used for tasks such as linting or testing code to
  ensure that only valid code gets committed.
- **commit-msg**: Runs after the commit message is written, but before the commit is saved. This hook can be used to
  enforce commit message standards (e.g., using conventional commit messages).
- **post-commit**: Runs after a commit has been made. This hook is often used for sending notifications or triggering
  actions like continuous integration (CI) pipelines.
- **pre-push**: Runs before a push to a remote repository. This is useful for ensuring that tests pass or that certain
  checks are met before pushing code.
- **post-merge**: Runs after a merge has been completed. This can be used for tasks like notifying team members or
  rebuilding a project.
- **pre-rebase**: Runs before a rebase operation begins.

### Server-Side Hooks

Server-side hooks are typically used in a central repository to enforce server-wide policies or behavior. Some examples
include:

- **pre-receive**: Runs before any changes are accepted by the remote repository.
- **update**: Runs before a reference is updated.
- **post-receive**: Runs after a push has been accepted into the repository.

---

## How to Set Up Git Hooks

### 1. Locate the `.git/hooks` Directory

Each Git repository has a `.git/hooks` directory where hooks are stored. Inside this directory, you'll find sample hook
scripts (e.g., `pre-commit.sample`, `commit-msg.sample`) that you can modify and rename to enable the hooks.

### 2. Create or Modify Hook Scripts

You can enable a hook by creating or modifying the corresponding script file in the `.git/hooks` directory. Each script
must be executable.

For example, to set up a `pre-commit` hook, you can create a file called `pre-commit` in the `.git/hooks/` directory and
add your custom logic to it.

```bash
#!/bin/sh
# Example pre-commit hook to run linting
npm run lint
```

### 3. Make the Hook Executable

For the hook script to run, you need to make it executable. You can do this by running the following command:

```bash
chmod +x .git/hooks/pre-commit
```

This will ensure that Git can execute the hook when the corresponding event occurs.

---

## Using Git Hooks for Automation

Git hooks can be used to automate a variety of tasks, including:

### 1. **Code Linting**

You can set up a `pre-commit` hook to run linters (e.g., ESLint, Pylint) before commits to ensure that all code follows
the style guide.

```bash
#!/bin/sh
npm run lint
```

### 2. **Running Unit Tests**

Before pushing code to a repository, you can use the `pre-push` hook to ensure that all unit tests pass.

```bash
#!/bin/sh
npm test
```

### 3. **Commit Message Validation**

You can use the `commit-msg` hook to enforce commit message conventions (e.g., ensuring that messages follow the
Conventional Commits format).

```bash
#!/bin/sh
commit_msg=$(cat $1)
if ! [[ $commit_msg =~ ^(feat|fix|docs|style|refactor|test)\(.*\):\ .+$ ]]; then
  echo "Commit message does not follow the Conventional Commits format."
  exit 1
fi
```

### 4. **Automated Documentation Generation**

You can automate tasks such as generating documentation or updating version numbers after a commit or push.

---

## Popular Git Hook Examples

Here are a few common examples of Git hooks:

### Pre-Commit Hook: Linting and Formatting

```bash
#!/bin/sh
# Run linting before committing
npm run lint
if [ $? -ne 0 ]; then
  echo "Linting failed. Please fix the issues before committing."
  exit 1
fi
```

### Pre-Push Hook: Run Tests Before Pushing

```bash
#!/bin/sh
# Run tests before pushing
npm test
if [ $? -ne 0 ]; then
  echo "Tests failed. Push aborted."
  exit 1
fi
```

### Commit Msg Hook: Enforce Conventional Commit Messages

```bash
#!/bin/sh
commit_msg=$(cat $1)
if ! [[ $commit_msg =~ ^(feat|fix|docs|chore)\(.*\):\ .+$ ]]; then
  echo "Invalid commit message format."
  echo "Expected format: <type>(<scope>): <message>"
  exit 1
fi
```

---

## Git Hook Configuration with Husky

While Git hooks are powerful, manually setting them up for every project can be cumbersome. **Husky** is a popular tool
that simplifies the process of managing and setting up Git hooks, especially in JavaScript projects.

### Setting Up Husky

1. **Install Husky**

```bash
npm install husky --save-dev
```

2. **Enable Husky**

```bash
npx husky install
```

3. **Set Up a Git Hook Using Husky**

```bash
npx husky add .husky/pre-commit "npm test"
```

This command will add a `pre-commit` hook to run `npm test` before each commit.

4. **Ensure Husky Runs on All Developers' Machines**

```bash
npm set-script prepare "husky install"
npm run prepare
```

Husky automatically creates `.husky/` directory to store your hook configurations.

---

## Conclusion

Git hooks are a powerful way to automate and enforce rules during various stages of the Git workflow. They help
developers maintain high code quality, enforce commit message conventions, and automate tasks like running tests and
linters. While Git provides built-in hooks, tools like **Husky** can simplify and standardize the process across a
project, ensuring consistency in workflows and improving team collaboration.
