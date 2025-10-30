# Code Review Process

Code reviews are a critical part of our development workflow, ensuring code quality, knowledge sharing, and adherence to best practices. This document outlines our code review process.

## 1. Purpose of Code Reviews

*   **Quality Assurance:** Catch bugs, design flaws, and potential issues early.
*   **Knowledge Sharing:** Spread knowledge about the codebase and new features across the team.
*   **Mentorship:** Provide opportunities for learning and growth for all developers.
*   **Consistency:** Ensure adherence to coding standards and architectural patterns.
*   **Security:** Identify potential security vulnerabilities.

## 2. When to Request a Review

*   **Every Pull Request (PR):** All code changes, no matter how small, must go through a code review before being merged into `main`.
*   **Ready for Review:** Only submit a PR for review when:
    *   All automated tests pass.
    *   Code adheres to coding standards and linting rules.
    *   Documentation (code comments, READMEs) is updated as necessary.
    *   You have self-reviewed your own code.

## 3. How to Request a Review

1.  **Open a Pull Request (PR):** Follow the guidelines in [Git Workflow](../01_git_workflow.md).
2.  **Provide Context:** Ensure your PR description clearly explains:
    *   What problem the PR solves.
    *   How it solves it (high-level design decisions).
    *   Any specific areas you'd like reviewers to focus on.
    *   Links to relevant issues or design documents.
3.  **Assign Reviewers:** Assign at least two reviewers, including a senior developer for critical changes. Consider assigning developers who are familiar with the affected area of the codebase.

## 4. Reviewer Responsibilities

*   **Timeliness:** Aim to review PRs promptly (within 24-48 hours) to avoid blocking development.
*   **Thoroughness:** Review the code for:
    *   **Correctness:** Does it solve the problem? Are there edge cases missed?
    *   **Readability & Maintainability:** Is the code clear, concise, and easy to understand?
    *   **Adherence to Standards:** Does it follow coding standards, linting rules, and architectural patterns?
    *   **Testing:** Are there sufficient tests? Do they cover critical paths?
    *   **Security:** Are there any potential security vulnerabilities?
    *   **Performance:** Are there any obvious performance bottlenecks?
    *   **Documentation:** Is the code adequately documented?
*   **Constructive Feedback:** Provide clear, actionable, and polite comments. Focus on the code, not the person.
*   **Approve/Request Changes:** Once satisfied, approve the PR. If changes are needed, clearly state them and request changes.

## 5. Author Responsibilities

*   **Respond to Feedback:** Address all comments from reviewers. If you disagree, explain your reasoning respectfully.
*   **Make Changes:** Implement requested changes and push new commits to your branch.
*   **Update PR:** Mark comments as resolved once addressed.
*   **Merge:** Once approved by all required reviewers, the PR can be merged into `main`.

## 6. Tools

*   **GitHub/GitLab PR Interface:** For comments and approvals.
*   **IDE Integrations:** For local review and commenting.

By following this process, we collectively ensure the high quality and integrity of our codebase.