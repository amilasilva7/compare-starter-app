# Testing Strategy

Testing is an integral part of our development process, ensuring the reliability, correctness, and quality of the PCW application. This document outlines our comprehensive testing strategy and best practices.

## 1. Testing Pyramid

We adhere to the testing pyramid principle, emphasizing a higher proportion of fast, isolated tests at the lower levels and fewer, more comprehensive tests at the higher levels.

### a. Unit Tests (Base - Numerous, Fast, Isolated)
*   **Focus:** Individual functions, methods, classes, or small modules in isolation.
*   **What to Test:** A single responsibility. Verify the logic, inputs, outputs, and side effects of the unit under test.
*   **What NOT to Test:** Do not test framework internals, third-party libraries (unless a wrapper around them), or external dependencies (databases, APIs, file system).
*   **Isolation:** Unit tests must run independently, without requiring external services or a running application.
*   **Structure & Naming:**
    *   Place unit test files alongside the code they test (e.g., `src/module/tests/unit/test_my_func.py` or `src/component/MyComponent.test.tsx`).
    *   Name test functions/methods descriptively: `test_function_name_should_do_x_when_y()` or `should_return_correct_value_when_given_valid_input()`.
*   **Tools:** `pytest` (Python), `Jest` with `React Testing Library` (JavaScript/TypeScript).

### b. Integration Tests (Middle - Fewer, Slower, Interacting)
*   **Focus:** Verify the interaction and communication between different components or services.
*   **What to Test:**
    *   API endpoints interacting with a database.
    *   Communication between two microservices.
    *   A service interacting with a message queue.
    *   Data persistence and retrieval operations.
*   **Environment Setup:**
    *   Use dedicated test databases (e.g., in-memory SQLite, spinning up a Dockerized PostgreSQL instance for tests) that are cleaned up after each test run.
    *   Limit external dependencies. Mock external APIs or services that are not the immediate focus of the integration.
*   **Structure & Naming:**
    *   Place integration test files in a distinct location (e.g., `src/module/tests/integration/test_api_endpoint.py`).
    *   Name test files to reflect the integration being tested.
*   **Tools:** `pytest` (Python, often with `httpx` for API calls), `Jest` (JavaScript/TypeScript, often with `supertest` for API calls).

### c. End-to-End (E2E) Tests (Top - Fewest, Slowest, Full Stack)
*   **Focus:** Simulate real user scenarios across the entire application stack, from UI to backend services and external integrations.
*   **What to Test:** Critical user journeys (e.g., user registration, comparing products, submitting an application, purchasing a policy).
*   **Tools:** `Cypress` (Frontend), `Playwright`.

## 2. Visual Regression Testing

Visual regression testing ensures that UI changes do not inadvertently alter the appearance of existing components or pages. This is crucial for maintaining a consistent user experience and brand identity.

*   **Focus:** Detecting unintended visual changes at the pixel level.
*   **What to Test:** Key UI components, critical pages, and responsive layouts.
*   **Tools:** We will integrate a tool like `Percy` or `Chromatic` (often integrated with Storybook) into our CI/CD pipeline.
*   **Automation:** Automated to run on every Pull Request or merge, comparing current UI screenshots against approved baselines.

## 3. Automated Accessibility Testing

Automated accessibility testing helps ensure our application is usable by the widest possible audience, including individuals with disabilities, and adheres to standards like WCAG 2.1 Level AA.

*   **Focus:** Identifying common accessibility violations.
*   **What to Test:** Missing `alt` text, insufficient color contrast, incorrect ARIA attributes, keyboard navigability issues.
*   **Tools:** We will integrate `Axe-core` (via Cypress or as a standalone CI check) to scan for violations.
*   **Automation:** Automated to run during the CI phase of our pipeline.

## 4. Test-Driven Development (TDD)

We encourage a Test-Driven Development (TDD) approach where applicable. This approach leads to cleaner code, less debugging, and a comprehensive test suite.

1.  **Red:** Write a failing test for a new feature or bug fix.
2.  **Green:** Write the minimum amount of code to make the test pass.
3.  **Refactor:** Improve the code while ensuring all tests still pass.

## 5. Test Coverage

*   **Target:** Aim for high test coverage, especially for critical business logic. While 100% coverage is not always practical or necessary, strive for a minimum of **80% line coverage** for new code.
*   **Tools:** Use coverage tools (`pytest-cov` for Python, `Jest` coverage reports for JavaScript) to monitor and report coverage.

## 6. Mocking & Stubbing

Mocking and stubbing are essential for isolating components and controlling test environments.

*   **Purpose:** To replace dependencies of a unit/component with controlled doubles that simulate the behavior of real dependencies.
*   **For Unit Tests:** Use mocking/stubbing extensively to isolate units under test from *all* their dependencies (e.g., external APIs, databases, message queues, other services).
    *   **Tools:** `unittest.mock` (Python), `Jest mocks` (JavaScript), `Sinon.js` (JavaScript).
*   **For Integration Tests:** Use mocking/stubbing more judiciously. While internal dependencies (like a test database) should be real, *external services* (e.g., third-party provider APIs) should often be mocked to ensure tests are deterministic, fast, and don't accrue real costs.
    *   **When NOT to Mock (in Integration Tests):** Avoid mocking internal components that are part of the integration you are trying to test, as this defeats the purpose of an integration test.

## 7. Test Data Management

Managing test data effectively is crucial for reliable and reproducible tests.

*   **Consistency:** Use consistent, anonymized test data for all environments.
*   **Avoid Production Data:** Never use real production data in non-production environments.
*   **Data Factories:** Use test data factories (e.g., `Faker` with `factory-boy` for Python, `Faker.js` with `factory.js` for JavaScript) to generate realistic, dynamic test data programmatically.
*   **Database Seeding:** Implement scripts or fixtures to seed test databases with a known state before running integration tests.
*   **Cleanup:** Ensure test data is cleaned up (rolled back or deleted) after test runs to maintain test isolation and prevent pollution.

## 8. Running Tests Locally

*   **Run All Tests:**
    *   `python -m pytest` (Python Backend)
    *   `npm test` or `yarn test` (Frontend)
*   **Run Specific Test File:**
    *   `python -m pytest services/backend-api/tests/unit/test_auth.py`
    *   `npm test -- src/components/Button/Button.test.tsx`
*   **Run Specific Test on Frontend (Watch Mode):**
    *   `npm test -- --watch` (often default for `Jest`)
*   **Debugging Tests:** Utilize your IDE's debugging features to set breakpoints and step through test execution.

## 9. Test Reporting & CI Integration

*   **Local Reports:** Generate and view test reports locally:
    *   Test results: Standard output of test runner (`pytest`, `Jest`).
    *   Coverage reports: `coverage html` (Python), `npm test -- --coverage` (Jest) to generate HTML reports locally.
*   **CI/CD Integration:** All tests (unit, integration, E2E) are integrated into the CI/CD pipeline.
    *   **Gatekeeping:** Pull Requests will not be merged if tests fail or coverage significantly drops (as defined in [Coding Standards & Linting](../02_coding_standards_linting.md)).
    *   **Reporting:** Test results and coverage reports are automatically published to the CI/CD dashboard for easy viewing and analysis.

## 10. Performance Testing

*   Regularly conduct performance tests (e.g., load testing, stress testing) against staging environments to ensure the application meets NFRs for response times and throughput.
*   **Tools:** `JMeter`, `Locust`, `k6`.

## 11. Security Testing

*   Integrated into CI/CD (SAST, DAST).
*   Regular penetration testing (external firms).