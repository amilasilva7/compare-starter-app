### **Database Schema Design (MongoDB)**

This schema design outlines the primary MongoDB collections and their key fields, organized by the microservice responsible for their ownership and management. This design is simplified for the prototype, focusing on essential fields and relationships identified across all Feature Requirement Specifications.

---

### **1. Users Service Database**

*   **Purpose:** Manages user accounts, profiles, saved quotes, policies, and reminders.
*   **Collections:**

    *   **`users` Collection:**
        *   `_id`: ObjectId (Primary Key)
        *   `email`: String (Unique, Indexed)
        *   `passwordHash`: String
        *   `firstName`: String
        *   `lastName`: String
        *   `address`: { `line1`: String, `line2`: String, `city`: String, `postcode`: String }
        *   `phoneNumber`: String
        *   `dob`: Date
        *   `occupation`: String
        *   `licenseType`: String
        *   `ncdYears`: Number
        *   `claims`: Boolean
        *   `emailVerified`: Boolean (Default: false)
        *   `createdAt`: Date
        *   `updatedAt`: Date

    *   **`saved_quotes` Collection:**
        *   `_id`: ObjectId (Primary Key)
        *   `userId`: ObjectId (Reference to `users` collection)
        *   `quoteRequestId`: ObjectId (Reference to `quotes` service's `quote_requests` collection)
        *   `providerId`: ObjectId (Reference to `providers` service's `providers` collection)
        *   `premium`: Number
        *   `policyFeatures`: [String] (e.g., ["Comprehensive", "Breakdown Cover"])
        *   `validUntil`: Date
        *   `savedAt`: Date

    *   **`policies` Collection:** (For purchased policies, dummy for prototype)
        *   `_id`: ObjectId (Primary Key)
        *   `userId`: ObjectId (Reference to `users` collection)
        *   `providerId`: ObjectId (Reference to `providers` service's `providers` collection)
        *   `policyType`: String (e.g., "Car Insurance - Comprehensive")
        *   `policyNumber`: String (Unique)
        *   `premium`: Number
        *   `renewalDate`: Date
        *   `status`: String (e.g., "Active", "Expired")
        *   `purchasedAt`: Date

    *   **`reminders` Collection:**
        *   `_id`: ObjectId (Primary Key)
        *   `userId`: ObjectId (Reference to `users` collection)
        *   `policyId`: ObjectId (Reference to `policies` collection, or `savedQuoteId` if for a saved quote)
        *   `type`: String (e.g., "renewal")
        *   `remindDate`: Date
        *   `status`: String (e.g., "pending", "sent", "dismissed")
        *   `createdAt`: Date

### **2. Quotes Service Database**

*   **Purpose:** Manages quote requests and generated quotes.
*   **Collections:**

    *   **`quote_requests` Collection:**
        *   `_id`: ObjectId (Primary Key)
        *   `userId`: ObjectId (Optional, Reference to `users` service's `users` collection)
        *   `vehicleReg`: String
        *   `mileage`: Number
        *   `parkingLocation`: String
        *   `driverDob`: Date
        *   `driverOccupation`: String
        *   `driverPostcode`: String
        *   `driverLicenseType`: String
        *   `driverNcdYears`: Number
        *   `driverClaims`: Boolean
        *   `coverageType`: String
        *   `excessAmount`: Number
        *   `requestedAt`: Date

    *   **`quotes` Collection:** (Stores transient or short-term quotes)
        *   `_id`: ObjectId (Primary Key)
        *   `quoteRequestId`: ObjectId (Reference to `quote_requests` collection)
        *   `providerId`: ObjectId (Reference to `providers` service's `providers` collection)
        *   `premium`: Number
        *   `policyFeatures`: [{ `name`: String, `value`: String }] (e.g., [{name: "Voluntary Excess", value: "£250"}])
        *   `validUntil`: Date
        *   `providerQuoteRef`: String (Reference ID from external provider)
        *   `createdAt`: Date

### **3. Providers Service Database**

*   **Purpose:** Manages third-party provider information and their product offerings.
*   **Collections:**

    *   **`providers` Collection:**
        *   `_id`: ObjectId (Primary Key)
        *   `name`: String (Unique)
        *   `logoUrl`: String
        *   `contactEmail`: String
        *   `apiBaseUrl`: String (Mock URL for prototype)
        *   `status`: String (e.g., "Active", "Inactive")
        *   `createdAt`: Date
        *   `updatedAt`: Date

    *   **`products` Collection:** (Details of products offered by providers)
        *   `_id`: ObjectId (Primary Key)
        *   `providerId`: ObjectId (Reference to `providers` collection)
        *   `productType`: String (e.g., "car_insurance", "home_insurance")
        *   `name`: String (e.g., "Comprehensive Car Insurance")
        *   `description`: String
        *   `features`: [{ `name`: String, `description`: String }]
        *   `termsAndConditionsUrl`: String
        *   `createdAt`: Date
        *   `updatedAt`: Date

### **4. Reference Data Service Database**

*   **Purpose:** Stores static, lookup, or master data used across the application.
*   **Collections:**

    *   **`reference_data` Collection:**
        *   `_id`: ObjectId (Primary Key)
        *   `type`: String (Unique, Indexed, e.g., "occupations", "coverage_types", "parking_locations")
        *   `values`: [String] or [{ `key`: String, `label`: String }] (Array of values for the given type)
        *   `createdAt`: Date
        *   `updatedAt`: Date

### **5. Monetization Service Database**

*   **Purpose:** Manages partner accounts, commission structures, and performance metrics.
*   **Collections:**

    *   **`partner_accounts` Collection:**
        *   `_id`: ObjectId (Primary Key)
        *   `providerId`: ObjectId (Reference to `providers` service's `providers` collection)
        *   `email`: String (Unique, Indexed, for partner login)
        *   `passwordHash`: String
        *   `contactName`: String
        *   `commissionRate`: Number (e.g., 0.05 for 5%)
        *   `monetizationModel`: String (e.g., "commission", "cpc")
        *   `status`: String (e.g., "Active", "Pending")
        *   `createdAt`: Date
        *   `updatedAt`: Date

    *   **`commission_records` Collection:**
        *   `_id`: ObjectId (Primary Key)
        *   `partnerId`: ObjectId (Reference to `partner_accounts` collection)
        *   `referralId`: String (Unique ID for the referral event)
        *   `amount`: Number
        *   `currency`: String (e.g., "GBP")
        *   `status`: String (e.g., "pending", "paid")
        *   `eventDate`: Date
        *   `createdAt`: Date

    *   **`performance_metrics` Collection:**
        *   `_id`: ObjectId (Primary Key)
        *   `partnerId`: ObjectId (Reference to `partner_accounts` collection)
        *   `metricType`: String (e.g., "clicks", "quotes_generated", "conversions")
        *   `value`: Number
        *   `date`: Date (Indexed) 
        *   `createdAt`: Date

### **6. CMS Service Database**

*   **Purpose:** Manages static content like articles, guides, and reviews.
*   **Collections:**

    *   **`articles` Collection:**
        *   `_id`: ObjectId (Primary Key)
        *   `title`: String
        *   `slug`: String (Unique, Indexed)
        *   `content`: String (Markdown or HTML)
        *   `category`: String (e.g., "Car Insurance Guide")
        *   `author`: String
        *   `publishedDate`: Date
        *   `updatedDate`: Date

    *   **`reviews` Collection:**
        *   `_id`: ObjectId (Primary Key)
        *   `providerId`: ObjectId (Reference to `providers` service's `providers` collection)
        *   `userId`: ObjectId (Optional, Reference to `users` service's `users` collection)
        *   `rating`: Number (1-5)
        *   `comment`: String
        *   `createdAt`: Date
        *   `status`: String (e.g., "pending", "approved")

---

**Indexing Note:** For optimal performance, appropriate indexes should be created on frequently queried fields (e.g., `email` in `users`, `slug` in `articles`, `foreign key` fields like `userId`, `providerId`, `partnerId`, and date fields used in queries).
