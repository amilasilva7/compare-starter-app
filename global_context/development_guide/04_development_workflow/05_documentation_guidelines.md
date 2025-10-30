# Documentation Guidelines

Comprehensive and up-to-date documentation is vital for knowledge sharing, onboarding new team members, and ensuring the long-term maintainability of the PCW application. This document outlines our guidelines for documentation.

## 1. General Principles

*   **Accuracy:** Documentation must reflect the current state of the code and system.
*   **Clarity:** Use clear, concise language. Avoid jargon where possible, or explain it.
*   **Completeness:** Document all significant aspects of the system, including design decisions, APIs, and complex logic.
*   **Maintainability:** Treat documentation as code; keep it version-controlled and update it as changes occur.
*   **Audience:** Consider who will be reading the documentation (developers, QA, product owners, non-technical stakeholders).

## 2. Types of Documentation

### a. In-Code Comments
*   **Purpose:** Explain *why* a piece of code exists, *what* its intent is, and *how* complex logic works. Avoid commenting on *what* the code does if it's self-evident.
*   **Best Practices:**
    *   Explain non-obvious logic, edge cases, and workarounds.
    *   Document public APIs, functions, and classes with docstrings (e.g., JSDoc for JavaScript, Sphinx/Google style for Python).
    *   Keep comments up-to-date with code changes.

### b. README Files
*   **Purpose:** Provide a quick overview and essential information for a repository, service, or major component.
*   **Location:** Every repository and significant sub-directory (e.g., `services/auth/README.md`).
*   **Content:**
    *   Project/Service name and brief description.
    *   How to set up and run locally.
    *   How to run tests.
    *   Key dependencies.
    *   Links to more detailed documentation.

### c. API Documentation
*   **Purpose:** Describe how to use the APIs, including endpoints, request/response formats, authentication, and error codes.
*   **Tools:** OpenAPI/Swagger for REST APIs. Generated automatically where possible.
*   **Best Practices:** Keep API documentation synchronized with the actual API implementation.

### d. Design Documents (ADRs - Architectural Decision Records)
*   **Purpose:** Document significant architectural decisions, their context, alternatives considered, and the chosen solution with its consequences.
*   **Location:** A dedicated `docs/adr/` folder in the main repository.
*   **Format:** Use a simple template (e.g., Markdown) for consistency.

### e. User Guides / Product Documentation
*   **Purpose:** Explain how to use the application from a user's perspective (e.g., for the Admin Panel, Provider Portal).
*   **Audience:** Non-technical users, product owners, support staff.

## 3. Documentation Tools
*   **Markdown:** For most general documentation (READMEs, design docs).
*   **Sphinx/MkDocs:** For generating comprehensive project documentation websites from Markdown or reStructuredText.
*   **Swagger UI / Postman:** For interactive API documentation.

## 4. Review & Maintenance
*   Documentation should be reviewed as part of the code review process.
*   Schedule regular documentation audits to ensure accuracy and completeness.
*   Treat documentation updates as part of any feature or bug fix task.