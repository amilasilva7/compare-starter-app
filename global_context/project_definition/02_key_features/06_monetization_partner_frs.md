### **Feature Requirement Specification: Monetization & Partner Management**

---

### **1. Feature Name:**
Monetization & Partner Management

### **2. Feature Goal:**
To establish a robust and flexible system for managing monetization models (commission, CPC, lead generation) and providing partners (providers, affiliates) with the tools to manage their listings, track performance, and access billing information. This feature is critical for the PCW's business sustainability and aims to streamline partner operations and foster strong relationships.

### **3. User Stories:**

*   **As a Provider/Partner, I want to** manage my product listings and offers on the PCW, **so that I can** ensure my information is accurate and competitive.
*   **As a Provider/Partner, I want to** track the performance of my products and referrals, **so that I can** understand my return on investment.
*   **As a Provider/Partner, I want to** access my commission statements and billing information, **so that I can** reconcile payments.
*   **As an Administrator, I want to** configure and manage different monetization models for providers, **so that I can** optimize revenue streams.
*   **As an Administrator, I want to** onboard and offboard providers and affiliates efficiently, **so that I can** scale our partner network.
*   **As an Administrator, I want to** generate commission reports and process payouts to partners, **so that I can** ensure timely and accurate financial operations.
*   **As an Affiliate Partner, I want to** access marketing materials and track my referrals, **so that I can** effectively promote the PCW and earn commissions.

### **4. Functional Requirements:**

*   **FR1: Provider/Partner Portal - Product & Offer Management**
    *   **Prerequisites:** Provider/Partner account is active and authenticated.
    *   **Navigation:** Accessible via a dedicated "Partner Login" on the main site, leading to a "Provider Dashboard."
    *   **Content/Microcopy:**
        *   **Page Title:** "Provider Dashboard - Product Management"
        *   **Section Heading:** "Your Products & Offers"
        *   **Table Columns:** "Product Name", "Product Type", "Status", "Last Updated", "Actions (Edit, View)"
        *   **Button Text:** "Add New Product", "Edit Product", "Save Changes"
        *   **Form Fields (for Add/Edit Product):** "Product Name", "Description", "Features (list)", "Terms & Conditions URL", "Product Type (dropdown)".
    *   The system SHALL provide a secure portal for authenticated Provider/Partners to view, add, and edit their product listings and associated offers.
    *   The system SHALL allow partners to update product details, including features, descriptions, and terms and conditions URLs.
    *   *(Prototype Note: Product management will be simplified, allowing updates to pre-defined dummy products. No complex product creation workflows).*
*   **FR2: Provider/Partner Portal - Performance & Analytics**
    *   **Prerequisites:** Provider/Partner account is active and authenticated.
    *   **Navigation:** Accessible from the "Provider Dashboard."
    *   **Content/Microcopy:**
        *   **Page Title:** "Provider Dashboard - Performance Analytics"
        *   **Section Headings:** "Referral Overview", "Conversion Funnel", "Commission Earned"
        *   **Metrics Display:** "Total Clicks", "Quotes Generated", "Conversions", "Conversion Rate", "Total Commission"
        *   **Date Range Selector:** (e.g., "Last 7 Days", "Last 30 Days", "Custom")
        *   **Chart Labels:** (e.g., "Daily Clicks", "Conversion Rate by Product")
    *   The system SHALL display key performance metrics for the Provider/Partner, including clicks, quotes generated, conversions, and earned commissions, within a specified date range.
    *   The system SHALL present this data visually (e.g., simple charts) and in tabular format.
    *   *(Prototype Note: Data will be dummy and pre-generated, simulating performance metrics).*
*   **FR3: Provider/Partner Portal - Billing & Invoicing**
    *   **Prerequisites:** Provider/Partner account is active and authenticated.
    *   **Navigation:** Accessible from the "Provider Dashboard."
    *   **Content/Microcopy:**
        *   **Page Title:** "Provider Dashboard - Billing & Payments"
        *   **Section Headings:** "Commission Statements", "Payment History"
        *   **Table Columns (Commission Statements):** "Statement ID", "Period", "Total Commission", "Status", "Actions (Download PDF)"
        *   **Table Columns (Payment History):** "Payment ID", "Date Paid", "Amount", "Method"
    *   The system SHALL allow Provider/Partners to view and download their commission statements and payment history.
    *   *(Prototype Note: Statements will be dummy PDF links or simple tables. No actual payment processing).*
*   **FR4: Admin Dashboard - Monetization Model Configuration**
    *   **Prerequisites:** Administrator account is active and authenticated.
    *   **Navigation:** Accessible via a dedicated "Admin Login" on the main site, leading to an "Admin Dashboard."
    *   **Content/Microcopy:**
        *   **Page Title:** "Admin Dashboard - Monetization Configuration"
        *   **Section Heading:** "Provider Monetization Settings"
        *   **Table Columns:** "Provider Name", "Monetization Model", "Commission Rate", "Actions (Edit)"
        *   **Form Fields (for Edit Monetization):** "Monetization Model (dropdown: Commission, CPC, Lead Gen)", "Commission Rate (number input)", "CPC Rate (number input)", "Lead Gen Fee (number input)".
    *   The system SHALL provide an administrative interface to configure monetization models (e.g., commission-based, CPC, lead generation) and associated rates for each provider.
    *   *(Prototype Note: Configuration will be simplified, allowing updates to pre-defined dummy providers).*
*   **FR5: Admin Dashboard - Partner Onboarding & Management**
    *   **Prerequisites:** Administrator account is active and authenticated.
    *   **Navigation:** Accessible from the "Admin Dashboard."
    *   **Content/Microcopy:**
        *   **Page Title:** "Admin Dashboard - Partner Management"
        *   **Section Heading:** "Providers & Affiliates"
        *   **Table Columns:** "Partner Name", "Type (Provider/Affiliate)", "Status", "Contact Email", "Actions (Approve, Deactivate, Edit)"
        *   **Button Text:** "Add New Partner"
        *   **Form Fields (for Add Partner):** "Partner Name", "Type", "Contact Email", "Initial Status".
    *   The system SHALL allow administrators to onboard new providers and affiliates, manage their status (active/inactive), and update basic contact information.
    *   The system SHALL provide functionality to issue and manage API keys for third-party integrations, including IP whitelisting configuration.
    *   *(Prototype Note: Onboarding will be a simplified form. API key management will be a placeholder for future implementation).*
*   **FR6: Admin Dashboard - Commission Calculation & Payouts**
    *   **Prerequisites:** Administrator account is active and authenticated.
    *   **Navigation:** Accessible from the "Admin Dashboard."
    *   **Content/Microcopy:**
        *   **Page Title:** "Admin Dashboard - Financial Operations"
        *   **Section Heading:** "Commission & Payouts"
        *   **Table Columns (Pending Payouts):** "Partner Name", "Period", "Amount Due", "Actions (Generate Payout)"
        *   **Button Text:** "Generate Payouts for Selected"
        *   **Confirmation Message:** "Payouts generated successfully."
    *   The system SHALL automatically calculate commissions based on configured monetization models and track pending payouts.
    *   The system SHALL provide an interface for administrators to review and trigger payouts to partners.
    *   *(Prototype Note: Commission calculation will use dummy data. Payout generation will be simulated, updating status without actual financial transactions).*
*   **FR7: Affiliate Partner Portal - Marketing & Tracking**
    *   **Prerequisites:** Affiliate Partner account is active and authenticated.
    *   **Navigation:** Accessible via a dedicated "Affiliate Login" on the main site, leading to an "Affiliate Dashboard."
    *   **Content/Microcopy:**
        *   **Page Title:** "Affiliate Dashboard"
        *   **Section Heading:** "Your Referral Link"
        *   **Referral Link Display:** Unique, shareable URL.
        *   **Share Buttons:** Social media sharing buttons.
        *   **Section Heading:** "Marketing Materials"
        *   **Material List:** "Banner Ad (728x90)", "Text Link", "Product Widget"
        *   **Button Text:** "Get Code"
        *   **Section Heading:** "Performance Overview"
        *   **Metrics Display:** "Total Clicks", "Conversions", "Commission Earned"
    *   The system SHALL provide Affiliate Partners with a unique referral link and access to marketing materials (e.g., banners, widgets).
    *   The system SHALL display performance metrics for the affiliate, including clicks, conversions, and earned commissions.
    *   *(Prototype Note: Marketing materials will be dummy code snippets. Performance metrics will be dummy data).*

### **5. Non-Functional Requirements:**

*   **NFR1: Performance:**
    *   **Partner Dashboard Load:** All partner dashboard pages (FR1, FR2, FR3, FR7) SHALL load within 2 seconds for 90% of users.
    *   **Admin Actions:** Admin configuration and payout generation actions (FR4, FR5, FR6) SHALL complete within 3 seconds for 90% of users.
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general NFRs).
*   **NFR2: Security:**
    *   All partner and admin portals SHALL be secured with robust authentication and authorization (MFA mandatory for admin/partner roles).
    *   Sensitive financial data (commission rates, payout details) SHALL be encrypted at rest and in transit.
    *   API keys and IP whitelisting configurations SHALL be managed securely.
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general NFRs and `06_security_access_considerations/` for detailed strategies).
*   **NFR3: Regulatory Compliance:**
    *   Monetization models and disclosures SHALL comply with FCA and CMA regulations regarding transparency and fair practices.
    *   Data handling for partner performance and billing SHALL comply with UK GDPR.
    *   (Refer to `project_definition/05_regulatory_compliance.md` for detailed compliance requirements).
*   **NFR4: Usability:**
    *   Partner and Admin interfaces SHALL be intuitive and efficient for managing products, tracking performance, and handling financial operations.
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general NFRs).

### **6. UI/UX Considerations:**

*   **Design System Adherence:** The UI SHALL strictly adhere to the Agoda-inspired visual theme and component library defined in `09_ui_ux_accessibility/01_design_system_guidelines.md`. This includes color palette, typography (Roboto), card-based layouts, and 4px border radius.
*   **Content Strategy:** All content within the partner and admin portals SHALL be clear, concise, and professional, following the tone of voice outlined in `09_ui_ux_accessibility/04_content_strategy.md`.
*   **Responsiveness:** All partner and admin portal pages SHALL be fully responsive and optimized for desktop, tablet, and mobile devices.
*   **Accessibility:** The UI SHALL meet WCAG 2.1 Level AA standards, ensuring keyboard navigation, screen reader compatibility, and sufficient color contrast, especially for data tables and forms.
*   **Data Visualization:** Use clear and effective charts/graphs for performance analytics in partner and admin dashboards.

### **7. Technical Considerations:**

*   **Microservices Involved:**
    *   **Frontend (React):** Renders partner and admin portal UIs, handles form submissions, and displays data.
    *   **Web App BFF (Node.js/Express):** Acts as a secure gateway for partner and admin portals, orchestrating calls to backend services.
    *   **Monetization Service (Node.js/Express):** Manages monetization models, calculates commissions, tracks referrals, and handles payout logic. Owns `partner_accounts`, `commission_records`, `performance_metrics` collections.
    *   **Providers Service (Node.js/Express):** Manages provider product data and configurations. Owns `providers`, `products` collections.
    *   **Users Service (Node.js/Express):** Manages user authentication and authorization for partner and admin roles.
*   **State Management:**
    *   **Frontend UI State:** Managed using React Hooks (e.g., form input state, table filtering) and Redux Toolkit (`createSlice` for global state like active partner/admin user).
    *   **Data State:** Managed using RTK Query for fetching and updating partner/admin data (products, performance, billing, configurations).
*   **Data Models:** Utilize and extend `partner_accounts`, `commission_records`, `performance_metrics` in `Monetization Service` and `providers`, `products` in `Providers Service` (refer to `08_data_management/05_database_schema_design.md`).
*   **Security Implementation:** Implement robust RBAC for different partner and admin roles. Secure API endpoints for all management functions. Use secure session management.
*   **Error Handling:** Implement comprehensive error handling for all partner and admin operations, providing clear feedback.
*   **Dummy Data Strategy (Prototype):**
    *   `Monetization Service` will manage dummy partner accounts, commission rates, and generate dummy performance and billing data.
    *   `Providers Service` will manage dummy product listings.
    *   Payout generation will be simulated without actual financial transactions.

### **8. Acceptance Criteria:**

*   Authenticated Provider/Partners can log into a dedicated portal.
*   Provider/Partners can view and edit their dummy product listings.
*   Provider/Partners can view dummy performance metrics (clicks, quotes, conversions, commission).
*   Provider/Partners can view dummy commission statements and payment history.
*   Authenticated Administrators can log into a dedicated portal.
*   Administrators can configure dummy monetization models and rates for providers.
*   Administrators can add/manage dummy providers and affiliates.
*   Administrators can trigger simulated payouts for pending commissions.
*   Authenticated Affiliate Partners can log into a dedicated portal.
*   Affiliate Partners can access their unique referral link and dummy marketing materials.
*   Affiliate Partners can view dummy performance metrics (clicks, conversions, commission).
*   All partner and admin portal pages are fully responsive and accessible (WCAG 2.1 Level AA).

### **9. Out of Scope (for this prototype iteration):**

*   Complex workflow for product approval or versioning.
*   Real-time integration with external accounting or payment systems.
*   Advanced fraud detection for partner activities.
*   Self-service API key generation and management for partners (will be admin-managed).
*   Detailed reporting customization for partners beyond pre-defined dashboards.
*   Multi-currency support for monetization.
*   Automated tax calculation for payouts.
