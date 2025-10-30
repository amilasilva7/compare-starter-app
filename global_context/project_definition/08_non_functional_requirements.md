# Non-Functional Requirements (NFRs)

This document outlines the critical Non-Functional Requirements (NFRs) that define the quality attributes and operational characteristics of the PCW application. These are quantifiable targets that guide architectural decisions, development, testing, and operations.

## 1. Performance

*   **Page Load Times:**
    *   Homepage & Key Landing Pages: < 2 seconds (90th percentile).
    *   Comparison Results Page: < 3 seconds (90th percentile) from form submission to results display.
*   **API Response Times:**
    *   Critical API Endpoints (e.g., getting quotes): < 500 ms (90th percentile).
    *   Non-critical API Endpoints: < 1 second (90th percentile).
*   **Throughput:**
    *   Support 500 requests per second (RPS) for core comparison flows.
    *   Support peak traffic bursts of 1500 RPS for short durations.

## 2. Scalability

*   **User Concurrency:** The system must seamlessly support 100,000 concurrent active users.
*   **Growth:** The architecture must be capable of scaling horizontally to accommodate a 50% year-over-year growth in user traffic and data volume for the next 3 years.
*   **Product Expansion:** The architecture must allow for easy integration of new product categories and providers without requiring major refactoring.

## 3. Reliability & Availability

*   **Uptime SLA (Production):** 99.95% annual uptime for core comparison and purchase flows.
*   **Mean Time To Recover (MTTR):** Target recovery time of < 60 minutes for critical incidents.
*   **Recovery Point Objective (RPO):** Data loss tolerance of < 15 minutes for critical data.
*   **Fault Tolerance:** The application should be resilient to single-component failures within a cloud region (e.g., availability zone failures).

## 4. Security

*   **Vulnerability Remediation:** Critical vulnerabilities (CVSS 7.0+) identified via scans or penetration tests must be remediated within 7 days. High vulnerabilities within 30 days.
*   **Data Breach Notification:** Adhere to GDPR's 72-hour data breach notification requirement where applicable.
*   **Encryption:** All PII and sensitive financial data must be encrypted at rest and in transit using industry-standard, FIPS 140-2 compliant encryption.
*   **Authentication Strength:** All user-facing authentication must support strong passwords and MFA; internal/admin authentication must enforce MFA.

## 5. Maintainability

*   **Defect Density:** Target less than 0.5 critical/high severity defects per 1000 lines of new or changed code.
*   **Test Coverage:** Minimum 80% code coverage for unit tests on new business logic.
*   **Onboarding Time:** A new developer should be able to set up their local environment and make a first contribution within 1 day.

## 6. Usability & Accessibility

*   **User Completion Rate:** Target 90% completion rate for key comparison forms.
*   **WCAG Compliance:** Achieve WCAG 2.1 Level AA conformance for all user-facing interfaces.
*   **Mobile Responsiveness:** Full functionality and optimal viewing experience across major mobile devices and screen sizes.

## 7. Deployability & Manageability

*   **Deployment Frequency:** Capable of deploying to production multiple times per day without user impact.
*   **Deployment Time:** A zero-downtime deployment to production should take less than 15 minutes.
*   **Rollback Time:** Ability to rollback a production deployment to a previous stable state within 5 minutes.
*   **Configuration Management:** Environment-specific configurations managed via IaC or secrets manager, with no hardcoded values.

## 8. Compliance

*   **GDPR:** Full adherence to all GDPR principles and requirements.
*   **FCA:** Full adherence to all relevant Financial Conduct Authority regulations and guidelines (e.g., Consumer Duty).
*   **Auditability:** All critical actions (e.g., data access, configuration changes, payments) must be logged for auditing purposes for at least 7 years.

These NFRs will be continually reviewed and refined as the project progresses.