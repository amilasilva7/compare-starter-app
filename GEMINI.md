# Project Context Overview

This `GEMINI.md` file serves as the primary entry point for understanding the project's context and definition. The comprehensive project details have been organized into a structured folder system for improved maintainability and clarity.

## How the Context is Organized

All detailed project documentation is now located within the `global_context/` directory. This directory contains two main sections:

1.  **Project Definition:** The core documentation outlining the project vision, features, user types, and technical considerations.
2.  **Development Guide:** Comprehensive instructions and best practices for developers.

### Main Sections:

*   **Project Definition:** The `project_definition/` folder is structured into the following top-level sections, providing a holistic view of the project's purpose and requirements:
    *   **Project Vision:** Outlines the core purpose and goals of the UK Price Comparison Website.
    *   **Key Features:** Details all functional and non-functional features, broken down by category.
    *   **User Types & Their Detailed Actions:** Describes each user role and their specific interactions with the application.
    *   **Target Audience:** Defines the primary users the application aims to serve.
    *   **Regulatory Compliance:** Covers all necessary legal and industry regulations, **including specific requirements from FCA, ICO (UK GDPR), CMA, and ASA for financial PCWs.**
    *   **Security Access Considerations:** Details the comprehensive security strategy for all user types.
    *   **Advanced Considerations & Future-Proofing:** Explores deeper requirements, operational aspects, and long-term strategic elements.
    *   **Non-Functional Requirements (NFRs):** Defines quantifiable quality attributes and operational characteristics, **including specific targets for performance, scalability, reliability, and security.**

*   **Development Guide:** The `development_guide/` folder provides detailed guidance for developers, covering the technical implementation and operational aspects of the project:
    *   **Project Overview:** High-level project summary and key business concepts.
    *   **Getting Started:** Prerequisites, **detailed local development setup using Docker Compose**, and making your first contribution.
    *   **Architecture & Tech Stack:** System architecture (microservices, BFF), technology choices (MERN + Kafka), and data flow.
    *   **Development Workflow:** Git, coding standards, **comprehensive testing strategy (Unit, Integration, E2E, Visual Regression, Accessibility)**, code reviews, and documentation.
    *   **Security Best Practices:** Secure coding, data handling, authentication/authorization, and AI security.
    *   **Deployment & Operations:** **Detailed CI/CD pipeline (GitHub Actions, pre/post-merge phases, approvals)**, deployment process, monitoring, and incident response.
    *   **API Design & Integration:** Principles for API design, **provider integration using Adapter/Factory patterns, and management of environment-specific third-party URLs/configurations.**
    *   **Data Management:** **MongoDB interaction, data migration strategy (`migrate-mongo`), master data management (Reference Data Service)**, and data quality.
    *   **UI/UX & Accessibility:** **Agoda-inspired design system, accessibility standards, frontend best practices (state management with RTK Query), and interactive content strategy.**
    *   **Troubleshooting & Support:** Common issues and how to get help.
    *   **SEO Strategy:** **Comprehensive playbook for web and AI engines, covering keywords, technical SEO, and content optimization.**

## Accessing Detailed Information

*   **Project Definition Document:**
    [Go to Project Definition Document (Main README)](./global_context/project_definition/README.md)

*   **Development Guide:**
    [Go to Development Guide (Main README)](./global_context/development_guide/README.md)