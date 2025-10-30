# Your First Contribution

Welcome! This guide will walk you through making a small, safe first contribution to the project. This helps you get familiar with our development workflow without making major changes.

## Goal: Fix a Typo in Documentation

We'll fix a hypothetical typo in a documentation file, specifically in `./docs/README.md` (or any other non-code documentation file).

## Steps:

1.  **Ensure Local Setup is Complete:**
    *   Follow the [Local Development Setup](../02_local_development_setup.md) guide.
    *   Ensure all prerequisites are met and your environment is running smoothly.

2.  **Clone the Repository:**
    *   If you haven't already, run: `git clone git@github.com:your-org/your-pcw-project.git`
    *   Navigate into the project directory: `cd your-pcw-project`

3.  **Create a New Branch:**
    *   Always work on a new branch for any changes. Use a clear, descriptive name (e.g., `fix/docs-typo-in-readme`).
    *   `git checkout -b fix/docs-typo-in-readme`

4.  **Make the Change:**
    *   Open `./docs/README.md` (or your chosen documentation file) in your IDE.
    *   Find the typo (e.g., change "recieve" to "receive").
    *   Save the file.

5.  **Commit Your Changes:**
    *   Stage the changes: `git add docs/README.md`
    *   Commit with a clear, concise message following our conventions (see [Git Workflow](../../04_development_workflow/01_git_workflow.md)).
    *   Example: `git commit -m "docs: Fix typo on how to recieve updates"`

6.  **Push Your Branch:**
    *   `git push origin fix/docs-typo-in-readme`

7.  **Create a Pull Request (PR):**
    *   Go to our GitHub repository in your web browser.
    *   You should see a prompt to create a new Pull Request from your recently pushed branch.
    *   Fill out the PR template, referencing any relevant issues.
    *   Assign appropriate reviewers (e.g., your team lead or a senior developer).

8.  **Address Feedback & Merge:**
    *   Respond to any comments from reviewers.
    *   Once approved, your branch can be merged into `main` (often done by the reviewer or lead).

Congratulations on your first contribution! This process will be followed for all code and documentation changes.