---
title: Standard Version
layout: default
parent: Git
grand_parent: Version Control System
description: "Standard Version"
---

## Standard Version

Managing software versions and creating changelogs can be time-consuming, especially when done manually. **Standard Version** is a powerful tool that simplifies versioning and changelog management by automating the release process. By using a set of clear commit message conventions, Standard Version can automatically determine version numbers, generate changelogs, and create Git tags — all without needing you to manage these steps manually.

### What is Standard Version?

**Standard Version** is a JavaScript tool that automates semantic versioning and changelog generation. It uses commit messages to determine whether a release should be a major, minor, or patch update based on [Semantic Versioning](https://semver.org) (also known as "semver") principles. With Standard Version, releases are more predictable, and your changelogs are consistently structured, helping both your team and users understand changes in each release.

### Why Use Standard Version?

Standard Version offers several benefits:
- **Automated Versioning**: Reduces manual work by automatically calculating version updates.
- **Clear Changelogs**: Generates changelogs based on commit messages, making it easy to track changes.
- **Consistent Releases**: Encourages structured commit messages (e.g., Conventional Commits) to streamline release management.
- **Improved Collaboration**: Keeps teams and users informed of updates, improving transparency and communication.

### Setting Up Standard Version

Let’s walk through how to set up Standard Version in your project.

#### 1. Install Standard Version

You can install Standard Version in your JavaScript project via npm:

```bash
npm install --save-dev standard-version
```

#### 2. Configure Your Project for Standard Version

Add a release script to your project’s `package.json` file. This script will run Standard Version to handle versioning and changelog generation.

```json
// package.json
{
  "scripts": {
    "release": "standard-version"
  }
}
```

With this setup, you can run `npm run release` to automate your versioning and changelog updates.

#### 3. Make Sure You’re Using Conventional Commits

Standard Version relies on commit message conventions to determine version updates. The **Conventional Commits** standard is commonly used, which categorizes commit messages with types like `feat`, `fix`, and `docs`.

For example:
- **`fix`**: Indicates a bug fix, triggering a patch version bump (e.g., 1.0.1).
- **`feat`**: Represents a new feature, triggering a minor version bump (e.g., 1.1.0).
- **`BREAKING CHANGE`**: Indicates a significant change, triggering a major version bump (e.g., 2.0.0).

### Using Standard Version to Release

Once set up, Standard Version automates the release process. Here’s how to use it:

1. **Commit Your Changes**: Make sure you’re committing changes with clear, Conventional Commit messages.
2. **Run the Release Script**: Execute `npm run release`. Standard Version will:
    - Update your project’s version number in `package.json`.
    - Generate or update a `CHANGELOG.md` file based on commit messages.
    - Commit these changes and create a Git tag for the new version.
3. **Push the Changes and Tags**: After running the release script, push your changes to the remote repository:

    ```bash
    git push --follow-tags origin main
    ```

With these simple steps, you’ve created a new release complete with a version bump, changelog, and Git tag.

### Customizing Standard Version

Standard Version is configurable to suit specific project needs. Here are a few ways to customize it:

- **Skip Certain Steps**: If you don’t want Standard Version to handle certain steps, like creating a Git tag, you can modify the command:

    ```bash
    npm run release -- --skip.tag
    ```

- **Prereleases**: To create prerelease versions (e.g., beta, alpha), use the `--prerelease` flag:

    ```bash
    npm run release -- --prerelease beta
    ```

This command will generate a version like `1.1.0-beta.0`.

- **Customize Changelog Header**: To change the header text in the generated changelog, configure the `changelogHeader` option in `package.json`:

    ```json
    "standard-version": {
      "changelogHeader": "# Project Changelog"
    }
    ```

### Integrating Standard Version with CI/CD

Standard Version integrates smoothly with CI/CD pipelines, making it possible to automate releases entirely. A CI/CD setup can:
- Run tests and ensure code quality.
- Automatically execute `npm run release` when changes are merged to the main branch.
- Push new tags and changelog updates to the repository.

### Benefits of Standard Version

Using Standard Version provides numerous advantages for managing software releases:
- **Time Savings**: Automated versioning and changelog generation save time, especially in large projects.
- **Predictability**: Consistent commit messages and automated version bumps ensure that each release is predictable and standardized.
- **Transparency**: Changelogs generated from commit messages improve transparency, making it easier for users and contributors to track changes.

### Conclusion

Standard Version is an excellent tool for any project that values structured releases, predictable versioning, and clear changelogs. By adopting Standard Version, you can simplify the release process, ensure that all changes are properly documented, and create a more transparent and organized workflow. Whether for an open-source library or an internal project, Standard Version makes releases more manageable and professional.