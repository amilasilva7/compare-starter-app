# Git Workflow

This document outlines the Git workflow to be followed for all development on the PCW application. Adhering to this workflow ensures a clean, traceable, and collaborative development process.

## 1. Branching Strategy: GitHub Flow

We will primarily use a **GitHub Flow** branching strategy. This is a lightweight, branch-based workflow that is simple and effective for continuous delivery.

*   **`main` branch:** This branch is always deployable. All new features and bug fixes are developed on separate branches and merged into `main` after review.
*   **Feature/Bugfix Branches:**
    *   Create a new branch from `main` for every new feature, bug fix, or task.
    *   Name branches descriptively (e.g., `feature/add-mfa-to-admin`, `bugfix/fix-login-redirect`, `chore/update-dependencies`).
    *   Work on your changes in this branch.

## 2. Commit Message Conventions

We follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification. This provides a standardized format for commit messages, making it easier to understand the history and automate changelog generation.

**Format:**

```
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

**Examples:**

*   `feat(auth): Implement multi-factor authentication for admin users`
*   `fix(login): Correct redirect after successful login`
*   `docs(readme): Update local setup instructions`
*   `chore(deps): Upgrade frontend dependencies to latest stable versions`

**Common Types:**
*   `feat`: A new feature
*   `fix`: A bug fix
*   `docs`: Documentation only changes
*   `style`: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc.)
*   `refactor`: A code change that neither fixes a bug nor adds a feature
*   `perf`: A code change that improves performance
*   `test`: Adding missing tests or correcting existing tests
*   `build`: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
*   `ci`: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
*   `chore`: Other changes that don't modify src or test files
*   `revert`: Reverts a previous commit

## 3. Pull Request (PR) Process

1.  **Create a PR:** Once your feature/bugfix branch is ready, open a Pull Request against the `main` branch.
2.  **Descriptive Title & Description:** The PR title should follow commit message conventions. The description should clearly explain:
    *   What problem it solves.
    *   How it solves it.
    *   Any relevant screenshots or GIFs for UI changes.
    *   Links to related issues in the project management tool.
3.  **Link Issues:** Reference relevant issues (e.g., `Closes #123`, `Fixes #456`).
4.  **Request Reviews:** Assign appropriate reviewers (at least two, including a senior developer for critical changes).
5.  **Address Feedback:** Respond to all comments and make necessary changes.
6.  **Merge:** Once approved, the PR can be merged into `main`. We prefer **Squash and Merge** to keep the `main` branch history clean, or **Rebase and Merge** for more complex feature branches.

## 4. Keeping Your Branch Up-to-Date

Regularly rebase your feature branch on `main` to avoid large merge conflicts:

```bash
git checkout main
git pull origin main
git checkout your-feature-branch
git rebase main
```

Resolve any conflicts that arise during the rebase.