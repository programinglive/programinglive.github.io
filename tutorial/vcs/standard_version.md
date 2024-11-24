---
title: Standard Version
layout: default
parent: Git
grand_parent: Version Control System
description: "Standard Version"
---

# Standard Version

**Standard Version** is a tool used to automate versioning and changelog generation based on **Semantic Versioning**
principles. It helps manage software versions by automatically determining whether the version should be bumped (MAJOR,
MINOR, PATCH) based on commit messages. Standard Version helps ensure that the project follows the Semantic Versioning
rules without requiring manual intervention for version management, making it particularly useful for teams and
open-source projects.

---

## Table of Contents

- [What is Standard Version?](#what-is-standard-version)
- [How Does Standard Version Work?](#how-does-standard-version-work)
- [Setting Up Standard Version](#setting-up-standard-version)
- [How to Use Standard Version](#how-to-use-standard-version)
- [Commit Message Conventions](#commit-message-conventions)
- [Customizing Standard Version](#customizing-standard-version)
- [Benefits of Using Standard Version](#benefits-of-using-standard-version)
- [Conclusion](#conclusion)

---

## What is Standard Version?

Standard Version is a utility that automates versioning and changelog generation based on commit messages. It follows
the rules of **Semantic Versioning (SemVer)** and uses commit messages to determine how the version number should
change. By analyzing commits, Standard Version determines whether to increment the **MAJOR**, **MINOR**, or **PATCH**
version, and it also generates a changelog for each release.

The main features of Standard Version are:

- Automatic version bumping based on commit history.
- Changelog generation based on commits.
- Easy integration into CI/CD pipelines.

---

## How Does Standard Version Work?

Standard Version operates by inspecting commit messages that follow a specific convention. The most common convention
used is **Conventional Commits**, a standardized format for writing commit messages that includes types
like `feat`, `fix`, `docs`, and others. By analyzing these commit types, Standard Version can determine how to bump the
version number:

- **MAJOR** version bump for breaking changes (`BREAKING CHANGE` in commit messages).
- **MINOR** version bump for new features that are backward-compatible.
- **PATCH** version bump for bug fixes and minor improvements.

For example:

- A commit like `feat: add new login feature` would result in a MINOR bump.
- A commit like `fix: resolve login bug` would result in a PATCH bump.
- A commit like `BREAKING CHANGE: remove deprecated login method` would result in a MAJOR bump.

Standard Version also generates a changelog based on these commits, making it easier to track changes and releases.

---

## Setting Up Standard Version

To use Standard Version in your project, follow these steps:

### 1. **Install Standard Version**

You can install Standard Version as a development dependency using npm or yarn:

```bash
npm install --save-dev standard-version
```

or

```bash
yarn add --dev standard-version
```

### 2. **Add a Versioning Script to `package.json`**

Add a script in your `package.json` to run Standard Version. This script will automate the process of bumping versions
and generating changelogs.

```json
"scripts": {
"release": "standard-version"
}
```

### 3. **Configure Commit Message Convention (Optional)**

Standard Version works best with commit messages following the **Conventional Commits** format. If you are not already
using this format, you can enforce it by installing **Commitizen** and using **cz-conventional-changelog** to guide your
commits.

Install Commitizen:

```bash
npm install --save-dev commitizen
```

Then configure Commitizen in `package.json`:

```json
"config": {
"commitizen": {
"path": "./node_modules/cz-conventional-changelog"
}
}
```

---

## How to Use Standard Version

Once Standard Version is installed and configured, you can use it by running the following command:

```bash
npm run release
```

This will trigger Standard Version to:

1. Analyze your commit history.
2. Bump the version according to Semantic Versioning.
3. Generate or update the changelog.
4. Create a new commit and tag the release.

For example, if there have been bug fixes and minor features, it might bump the PATCH version. If there are breaking
changes, it will bump the MAJOR version, and so on.

---

## Commit Message Conventions

Standard Version relies on **Conventional Commits** for determining version bumps. Conventional commits use a structured
format that makes it easy for tools like Standard Version to automatically determine the type of change. A typical
commit message looks like this:

```
<type>(<scope>): <message>
```

- **type**: Describes the type of change, such as `feat` (new feature), `fix` (bug fix), `docs` (
  documentation), `chore` (maintenance), etc.
- **scope**: Optional. Specifies the area of the code affected (e.g., `ui`, `api`, `auth`).
- **message**: A brief, descriptive message explaining the change.

### Common Commit Types

- **feat**: A new feature.
- **fix**: A bug fix.
- **docs**: Documentation changes.
- **chore**: Routine tasks or changes not affecting code functionality.
- **style**: Changes that do not affect the meaning of the code (e.g., formatting).
- **refactor**: Code changes that neither fix a bug nor add a feature but improve the code structure.
- **test**: Adding or modifying tests.
- **BREAKING CHANGE**: Indicates a breaking change when included in the commit message body.

### Example Commit Messages

- `feat(auth): add OAuth login`
- `fix(ui): correct button alignment`
- `chore: update build dependencies`
- `BREAKING CHANGE: remove deprecated login API`

By following this commit message format, Standard Version can automatically figure out which type of version bump is
appropriate.

---

## Customizing Standard Version

While Standard Version comes with sensible defaults, you can configure it to fit your needs by creating a `.versionrc`
file or adding configuration to your `package.json`. Here are some configuration options:

- **releaseAs**: Override the default version bump (MAJOR, MINOR, PATCH).
- **skip?**: Skip certain parts of the release process, such as skipping changelog generation or version bump.
- **scripts**: Run custom scripts before or after versioning tasks.

Example `.versionrc`:

```json
{
  "releaseAs": "minor",
  "scripts": {
    "postrelease": "npm run deploy"
  }
}
```

This configuration forces a MINOR version bump regardless of the commit history and runs a custom deployment script
after the release.

---

## Benefits of Using Standard Version

1. **Automates Versioning and Changelog Generation**  
   Standard Version automates the process of versioning, ensuring that the right version number is applied based on your
   commit history. It also generates changelogs, saving time on manual tracking of changes.

2. **Enforces Consistent Commit Messages**  
   By encouraging or enforcing the use of **Conventional Commits**, Standard Version helps maintain consistency in
   commit messages, making it easier to understand changes in the codebase.

3. **Improved Collaboration**  
   Automated versioning and changelog generation ensure that all team members, including CI/CD pipelines, stay in sync
   with project versions and release notes.

4. **Reduces Human Error**  
   By automating versioning, you eliminate the risk of human error when manually bumping versions or generating
   changelogs.

5. **Easy Integration with CI/CD**  
   Standard Version can be easily integrated into your continuous integration and delivery (CI/CD) pipeline, ensuring
   that version bumps and changelogs are generated automatically during the release process.

---

## Conclusion

Standard Version is a powerful tool for automating version management and changelog generation, helping developers
follow **Semantic Versioning** principles without the hassle of manual versioning. By integrating **Conventional Commits
**, it ensures consistent commit messages and makes version bumps predictable. Whether you’re working on an open-source
project or an internal tool, Standard Version can streamline your release process, improve collaboration, and reduce
errors in version management.