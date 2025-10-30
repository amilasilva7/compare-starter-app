# Coding Standards & Linting

Adhering to consistent coding standards is crucial for code maintainability, readability, and collaborative development. This document outlines our guidelines and the tools we use to enforce them.

## 1. General Principles

*   **Readability:** Code should be easy to read and understand by other developers (and your future self).
*   **Consistency:** Follow established patterns and styles within the codebase.
*   **Simplicity:** Prefer simple, straightforward solutions over overly complex ones.
*   **Clarity:** Variable names, function names, and comments should clearly convey intent.
*   **DRY (Don't Repeat Yourself):** Avoid duplicating code; abstract common logic into reusable components or functions.

## 2. Language-Specific Standards

### Python
*   **Style Guide:** [PEP 8](https://www.python.org/dev/peps/pep-0008/)
*   **Linting Tool:** `Flake8` (combines PyFlakes, pycodestyle, and McCabe complexity checker)
*   **Formatting Tool:** `Black` (opinionated formatter, run with `--check` in CI)
*   **Type Checking:** `mypy` (for static type checking)

### JavaScript/TypeScript
*   **Style Guide:** [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript) (for JavaScript), [TypeScript ESLint Recommended](https://typescript-eslint.io/docs/linting/configs/#recommended) (for TypeScript)
*   **Linting Tool:** `ESLint` (with appropriate plugins for React, TypeScript)
*   **Formatting Tool:** `Prettier` (integrated with ESLint)

### Go
*   **Style Guide:** [Effective Go](https://go.dev/doc/effective_go)
*   **Linting/Formatting:** `go fmt`, `go vet`, `golangci-lint`

## 3. Editor Integration

It is highly recommended to integrate linting and formatting tools directly into your IDE (e.g., VS Code, IntelliJ IDEA). This provides immediate feedback as you write code.

*   **VS Code Extensions:**
    *   Python: Pylance, Black Formatter, isort
    *   JavaScript/TypeScript: ESLint, Prettier

## 4. Automated Enforcement (CI)

All linting and formatting checks are enforced as part of our Continuous Integration (CI) pipeline. Pull Requests will fail if code does not adhere to the defined standards. This ensures that only high-quality, consistently formatted code is merged into `main`.

## 5. Code Quality Metrics

We use tools like `SonarQube` (or similar) to track code quality metrics such as:
*   Code complexity
*   Duplication
*   Test coverage
*   Security vulnerabilities

Aim to keep these metrics within acceptable thresholds and improve them over time.