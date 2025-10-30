# Master Data Management

This document defines our strategy for managing master data, which is the core, non-transactional data essential for the operation of our UK Price Comparison Website. Effective master data management ensures consistency, accuracy, and a single source of truth across all microservices.

---

### **1. Definition of Master Data**

For our application, master data includes, but is not limited to:

*   **Product Categories:** (e.g., "Car Insurance", "Home Insurance", "Broadband", "Energy").
*   **Provider Information:** (e.g., "Aviva", "Direct Line", "BT") - including names, logos, contact details, and unique identifiers.
*   **Reference Data:** (e.g., UK postcodes, car makes/models, types of coverage options, energy tariff types).
*   **User Roles/Permissions:** (e.g., "Customer", "Provider Admin", "Internal Admin").

### **2. Storage & Ownership**

*   **Primary Storage:** All master data will be persistently stored in **MongoDB**.
*   **Dedicated Service:** A dedicated **"Reference Data Service"** microservice will be the sole owner and manager of all master data. This service is responsible for:
    *   Defining the schema and structure of master data.
    *   Validating master data upon creation or update.
    *   Providing a well-defined API for other microservices and the BFF to consume master data.

### **3. Automated Master Data Deployment**

Master data will be deployed automatically and consistently across all environments (development, staging, production) without direct manual database updates.

*   **Integration with Migrations:** Initial master data and subsequent updates will be defined within `migrate-mongo` scripts (as detailed in [Data Migration Strategy](./02_data_migration_strategy.md)).
*   **Version Control:** These migration scripts, containing master data changes, will be version-controlled alongside the Reference Data Service's codebase.
*   **CI/CD Integration:** The CI/CD pipeline for the Reference Data Service will automatically execute any pending `migrate-mongo` scripts during deployment. This ensures that master data is always up-to-date and consistent with the deployed service version.

### **4. Accessing Master Data**

*   **API-First Access:** Other microservices and the Backend-for-Frontend (BFF) will **never directly access MongoDB** for master data.
*   They will always query the **Reference Data Service's API** to retrieve the necessary master data. This enforces a single source of truth, ensures data consistency, and allows the Reference Data Service to enforce business rules and access controls.

### **5. Master Data Updates**

*   **Programmatic Updates:** Updates to master data will primarily occur via the Reference Data Service's API, ensuring all changes go through a controlled and validated process.
*   **Administrative UI (Future):** For certain types of master data, an internal administrative UI might be developed to allow authorized personnel to manage data through the Reference Data Service's API.
