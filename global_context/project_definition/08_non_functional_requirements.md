# Non-Functional Requirements (NFRs)

This document defines the quantifiable quality attributes and operational characteristics that the UK Price Comparison Website application must meet. These NFRs guide architectural decisions, development practices, and testing efforts to ensure the application is performant, scalable, reliable, secure, and maintainable.

---

### **1. Performance**

*   **Frontend Page Load Time:**
    *   **Largest Contentful Paint (LCP):** < 2.5 seconds for 75% of users.
    *   **First Input Delay (FID):** < 100 milliseconds for 75% of users.
    *   **Cumulative Layout Shift (CLS):** < 0.1 for 75% of users.
    *   **Overall Page Load:** < 3 seconds for 90% of users on a typical broadband connection (e.g., 50 Mbps).
*   **API Response Time (Backend):**
    *   **Critical APIs (e.g., Quote Generation, User Authentication):** < 200 milliseconds for 95% of requests.
    *   **Non-Critical APIs (e.g., User Profile Update, Reference Data Lookup):** < 500 milliseconds for 95% of requests.
*   **Throughput:** The system must be able to sustain 500 concurrent active users and process 2,000 requests per second during peak load.

### **2. Scalability**

*   **Horizontal Scaling:** All microservices and the frontend must be designed to be horizontally scalable (stateless where possible).
*   **Load Handling:** The system must be able to automatically scale resources (via Kubernetes autoscaling) to handle a 5x increase in typical traffic within 30 minutes, without degradation of performance NFRs.
*   **Resource Utilization:** Average CPU utilization for any service should not exceed 70% under normal peak load.

### **3. Reliability & Availability**

*   **Uptime:**
    *   **Critical Services (e.g., Quote Generation, User Authentication, Payment Processing):** 99.9% monthly uptime.
    *   **Non-Critical Services (e.g., Blog, Static Content):** 99.5% monthly uptime.
*   **Data Durability (RPO - Recovery Point Objective):** Maximum acceptable data loss of 5 minutes in the event of a major system failure.
*   **Recovery Time (RTO - Recovery Time Objective):** The system must be fully recoverable and operational within 30 minutes following a major outage.
*   **Fault Tolerance:** The failure of any single microservice instance should not lead to a complete system outage.

### **4. Security**

*   **Vulnerability Management:** All critical vulnerabilities (CVSS score > 7.0) identified through scans or audits must be patched or mitigated within 7 days of discovery. High vulnerabilities (CVSS 4.0-6.9) within 30 days.
*   **Data Encryption:** All sensitive data (e.g., Personally Identifiable Information - PII, financial details) must be encrypted at rest and in transit (TLS 1.2+).
*   **Authentication:** Multi-factor authentication (MFA) must be enforced for all administrative access and highly recommended for user accounts.
*   **Authorization:** Role-Based Access Control (RBAC) must be implemented to ensure users only access resources they are authorized for.
*   **Compliance:** Adherence to UK GDPR and FCA data security guidelines (as detailed in `05_regulatory_compliance.md`).

### **5. Maintainability & Operability**

*   **Code Coverage:** Minimum 80% unit test coverage for all new code.
*   **Deployment Frequency:** Ability to deploy to production multiple times per day with minimal risk.
*   **Monitoring & Alerting:** All critical services must have comprehensive logging, metrics, and distributed tracing enabled, with automated alerts for predefined thresholds (e.g., error rates, latency spikes).
*   **Documentation:** All APIs, services, and significant architectural decisions must be documented.

### **6. Usability & Accessibility**

*   **Accessibility:** WCAG 2.1 Level AA compliance for all user-facing interfaces.
*   **Browser Support:** Full functionality and consistent experience across the latest two major versions of Chrome, Firefox, Edge, and Safari.
