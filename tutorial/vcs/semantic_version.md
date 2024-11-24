---
title: Semantic Versioning
layout: default
parent: Git
grand_parent: Version Control System
description: "Semantic Versioning"
---

# Semantic Versioning

**Semantic Versioning (SemVer)** is a versioning scheme used to indicate the nature and impact of changes in software.
The idea behind Semantic Versioning is to provide an easy-to-understand way to communicate version changes so that users
can understand whether a new version will break existing functionality, add new features, or contain bug fixes.

Semantic Versioning follows the format:

```
MAJOR.MINOR.PATCH
```

Each part of the version number is incremented based on the type of change made to the software, and the rules for
incrementing these numbers are well-defined.

---

## Table of Contents

- [What is Semantic Versioning?](#what-is-semantic-versioning)
- [The Structure of Semantic Versioning](#the-structure-of-semantic-versioning)
- [When to Increment Each Version Part](#when-to-increment-each-version-part)
- [Pre-release Versions](#pre-release-versions)
- [Build Metadata](#build-metadata)
- [Advantages of Semantic Versioning](#advantages-of-semantic-versioning)
- [Tools for Automating Versioning](#tools-for-automating-versioning)
- [Conclusion](#conclusion)

---

## What is Semantic Versioning?

Semantic Versioning (SemVer) is a versioning standard that uses three numbers (MAJOR, MINOR, PATCH) to communicate the
type of changes in a software release. It is designed to convey meaningful information about how a version compares to
previous versions.

The version number format is:

```
<MAJOR>.<MINOR>.<PATCH>
```

This version number communicates the following:

- **MAJOR** version is incremented when there are incompatible API changes.
- **MINOR** version is incremented when new features are added in a backward-compatible manner.
- **PATCH** version is incremented when backward-compatible bug fixes are made.

This helps developers and users understand the level of change in a new release.

---

## The Structure of Semantic Versioning

### 1. **MAJOR Version**

The **MAJOR** version is incremented when there are breaking changes to the software that are not backward compatible.
Users need to be aware that updating to this version might cause their existing code or integrations to break.

Examples of when to increment the MAJOR version:

- Removing or renaming an existing API method.
- Changing the behavior of an API in such a way that it is no longer compatible with previous versions.
- Major refactoring that breaks backwards compatibility.

**Example**: `2.0.0` → `3.0.0`

### 2. **MINOR Version**

The **MINOR** version is incremented when new functionality is introduced in a backward-compatible manner. These changes
add new features but do not break or change existing functionality. Users can safely upgrade to a new MINOR version
without worrying about breaking their current code.

Examples of when to increment the MINOR version:

- Adding new methods or features that don't break existing features.
- Adding new configuration options or supporting new formats without changing the existing behavior.

**Example**: `1.1.0` → `1.2.0`

### 3. **PATCH Version**

The **PATCH** version is incremented when backward-compatible bug fixes are introduced. These changes improve the
software without adding new features or breaking any functionality. Users can safely upgrade to a new PATCH version to
benefit from fixes without the risk of breaking their current code.

Examples of when to increment the PATCH version:

- Fixing a bug that was affecting the performance or usability of the software.
- Resolving security vulnerabilities or critical issues.
- Minor tweaks or improvements that do not change the API.

**Example**: `1.0.1` → `1.0.2`

---

## When to Increment Each Version Part

- **MAJOR Version**:
    - Breaking changes, such as an incompatible API change, require a change in the MAJOR version number.
    - Example: If an API method is removed or changed in a way that existing applications relying on it will break,
      increment the MAJOR version.

- **MINOR Version**:
    - New features that are backward-compatible should cause an increment in the MINOR version.
    - Example: Adding new features like additional methods or capabilities that do not affect existing ones.

- **PATCH Version**:
    - Bug fixes or minor improvements that do not affect the software’s interface should increment the PATCH version.
    - Example: Fixing a memory leak or resolving a non-breaking bug.

---

## Pre-release Versions

Pre-release versions are used for versions that are not yet stable or complete. They allow developers to release early
versions of software for testing or early feedback.

A pre-release version is indicated by appending a hyphen (`-`) and a label (such as `alpha`, `beta`, or `rc` for "
release candidate") to the version number.

For example:

- `1.0.0-alpha` (alpha release)
- `1.0.0-beta` (beta release)
- `1.0.0-rc.1` (release candidate 1)

A pre-release version can also have additional labels to specify the type or stage of the release.

Example:

- `1.0.0-alpha.1` → First alpha version.
- `1.0.0-beta.2` → Second beta version.

---

## Build Metadata

Build metadata is additional information about a build, such as build number or commit hash, and it is appended to the
version number using a `+` symbol.

Example:

- `1.0.0+20130313144700` (build version with timestamp)
- `1.0.0+sha256.abc123` (build version with commit hash)

Build metadata does not affect the versioning order or semantic versioning rules, but it can be useful for tracking
specific builds or versions in a CI/CD pipeline.

---

## Advantages of Semantic Versioning

### 1. **Clear Communication of Changes**

Semantic versioning makes it easy for developers to understand the potential impact of upgrading to a new version. By
looking at the version number, you can quickly tell if the update introduces breaking changes, new features, or just bug
fixes.

### 2. **Predictable Release Cycles**

With Semantic Versioning, both maintainers and users can predict how new versions will behave. This helps in managing
dependencies and ensures smooth upgrades, as you can rely on the version number to indicate the scope of changes.

### 3. **Better Dependency Management**

Many tools, such as npm for JavaScript, rely on Semantic Versioning to manage dependencies. This allows projects to
automatically update to compatible versions while avoiding breaking changes.

### 4. **Automated Tools for Versioning**

Semantic Versioning can be automated with tools that read commit messages, analyze the types of changes, and determine
the appropriate version bump. Tools like **semantic-release** and **standard-version** can automate versioning and
changelog generation based on the rules of SemVer.

---

## Tools for Automating Versioning

To streamline the process of adhering to Semantic Versioning, several tools can automate version management and
changelog generation:

- **semantic-release**: Automates versioning and changelog generation based on commit messages. It ensures that version
  numbers are automatically bumped according to Semantic Versioning rules.

- **standard-version**: An easier-to-use tool for automating versioning and changelog generation based on the Semantic
  Versioning format.

- **commitizen**: Helps in writing conventional commit messages that can be automatically parsed by tools like *
  *semantic-release**.

---

## Conclusion

Semantic Versioning provides a standardized, predictable approach to versioning that helps developers understand the
changes made between releases. By using a MAJOR.MINOR.PATCH format, Semantic Versioning makes it clear whether a new
release introduces breaking changes, adds new features, or only contains bug fixes. Using tools like **semantic-release
** and **standard-version**, developers can automate the process of managing versions and changelogs, improving the
overall software development and release process.