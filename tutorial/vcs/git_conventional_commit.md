---
title: Git Conventional Commit
layout: default
parent: Git
grand_parent: Version Control System
description: "Git Conventional Commit"
---

## Git Conventional Commits

Commit messages are an essential part of software development, providing context, history, and insight into code changes. However, when commit messages are inconsistent or vague, understanding the history of a project can become difficult. **Conventional Commits** provide a structured, standardized way to format commit messages, making them clear and useful for everyone involved.

### What is a Conventional Commit?

A **Conventional Commit** is a standardized commit message format that provides specific structure and meaning. This format helps developers and tools understand the purpose and scope of each commit at a glance. Conventional Commits use a simple structure that consists of a **type**, an optional **scope**, and a **description**:

```
<type>(<scope>): <description>
```

An example of a Conventional Commit message might look like this:

```
feat(login): add password reset feature
```

In this example:
- **`feat`** is the type, indicating that this commit adds a new feature.
- **`login`** is the scope, showing that this feature relates to the login functionality.
- **`add password reset feature`** is the description, providing a short summary of the change.

### Why Use Conventional Commits?

Using Conventional Commits has several advantages:
- **Clarity**: Commit messages follow a predictable structure, making them easier to read and understand.
- **Automated Releases**: Tools like semantic-release can automatically generate changelogs and release notes based on Conventional Commits.
- **Improved Collaboration**: Consistent commit messages make it easier for teams to understand each other’s work, whether in code reviews, debugging, or when onboarding new members.
- **Better Change Logs**: Conventional Commits make it straightforward to categorize commits and generate meaningful changelogs for users and stakeholders.

### Conventional Commit Types

Some common types used in Conventional Commits are:
- **feat**: For new features.
- **fix**: For bug fixes.
- **docs**: For changes to documentation only.
- **style**: For changes that do not affect the meaning of the code (like formatting or whitespace).
- **refactor**: For code changes that neither fix a bug nor add a feature.
- **test**: For adding or updating tests.
- **chore**: For routine tasks or maintenance that don’t directly affect the code.

By choosing the appropriate type for each commit, you can immediately convey the intent of your changes to the entire team.

### Writing Conventional Commits: Examples

Here are some examples of Conventional Commits:

- **Adding a new feature**:
    ```
    feat(cart): add discount code functionality
    ```

- **Fixing a bug**:
    ```
    fix(api): correct typo in API endpoint URL
    ```

- **Updating documentation**:
    ```
    docs(readme): update installation instructions
    ```

- **Refactoring code**:
    ```
    refactor(auth): simplify login logic
    ```

- **Running automated tests**:
    ```
    test(user): add unit tests for user authentication
    ```

Each message is clear, specific, and easy to understand for anyone viewing the project history.

### Using Scopes in Conventional Commits

The **scope** in a Conventional Commit message is optional but can be useful for larger projects. It helps to indicate which part of the codebase is affected. For example, in a project with multiple components, using scopes can clarify which feature or module the commit applies to.

Some example scopes might be:
- **ui** for changes to the user interface.
- **auth** for changes to authentication logic.
- **api** for modifications to the backend API.

Including scopes can help your team quickly identify what each commit is related to, which is especially helpful in larger, more complex projects.

### Automating Conventional Commits

To ensure commit messages follow the Conventional Commits format, you can use tools like **commitizen** and **commitlint**:
- **Commitizen**: Helps guide developers to write commits in a standardized format.
- **Commitlint**: Enforces rules for commit messages and integrates with Git Hooks to check each message.

These tools can make it easier to adopt Conventional Commits across your team, maintaining consistency without much manual effort.

### Conclusion

Conventional Commits bring structure and clarity to commit messages, turning your Git history into a valuable resource. By using this simple, structured format, you make it easier for team members, tools, and future contributors to understand what each change does and why it was made. Conventional Commits can improve collaboration, automate release management, and create cleaner project histories—benefiting both developers and users.