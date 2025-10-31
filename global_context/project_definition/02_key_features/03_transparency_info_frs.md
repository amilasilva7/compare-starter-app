### **Feature Requirement Specification: Transparency & Detailed Information**

---

### **1. Feature Name:**
Transparency & Detailed Information

### **2. Feature Goal:**
To empower users with comprehensive, unbiased, and easily understandable information about financial products and the comparison process, fostering trust and enabling informed decision-making. This feature aims to differentiate the PCW by going beyond price comparison to provide deep insights into policy details, terms, and the platform's operational model, inspired by GoCompare's approach.

### **3. User Stories:**

*   **As a Customer, I want to** view comprehensive details of each policy, including features, exclusions, and terms, **so that I can** understand what I am buying beyond just the price.
*   **As a Customer, I want to** easily compare key policy specifics side-by-side, **so that I can** quickly identify the best fit for my needs.
*   **As a Customer, I want to** understand how the comparison results are ordered and how the PCW makes money, **so that I can** trust the impartiality of the platform.
*   **As a Customer, I want to** access educational content and guides, **so that I can** make informed decisions about complex financial products.
*   **As a Customer, I want to** see customer reviews and ratings for providers, **so that I can** gauge the reputation and service quality of different options.
*   **As a Customer, I want to** easily navigate and understand all information presented, **so that I don't** feel overwhelmed by jargon or complex layouts.

### **4. Functional Requirements:**

*   **FR1: Comprehensive Policy Details Display**
    *   **Prerequisites:**
        *   User has completed a comparison (e.g., Car Insurance Quote) and is viewing the results page.
        *   The `Quotes Service` has normalized policy features from various providers.
    *   **Interaction:** Each quote card on the results page SHALL include a prominent "View Details" button or expandable section.
    *   **Content/Microcopy:**
        *   **Button Text:** "View Details" (on each quote card).
        *   **Modal/Page Title:** "[Provider Name] - [Policy Type] Details"
        *   **Sections within Details:**
            *   **Key Features:** A clear list of included benefits (e.g., "Courtesy Car", "Legal Cover", "Breakdown Assistance").
            *   **Exclusions:** A clear list of what is NOT covered (e.g., "Driving abroad", "Personal belongings").
            *   **Excess:** Clearly state compulsory and voluntary excess amounts.
            *   **Payment Options:** Available payment frequencies (e.g., "Annually", "Monthly") and any associated fees.
            *   **Terms & Conditions:** A link to the full terms and conditions document (external PDF or dedicated page).
            *   **Underwriter Information:** Clearly state the underwriter if different from the brand (MGA model).
    *   The system SHALL display comprehensive policy details in a user-friendly, scannable format (e.g., bullet points, clear headings) within a modal or dedicated detail page.
    *   *(Prototype Note: Policy details will be dummy data, pre-defined for each fictional provider, simulating real-world complexity).*
*   **FR2: Side-by-Side Comparison Tool**
    *   **Prerequisites:**
        *   User is viewing the comparison results page.
        *   At least two quotes are available.
    *   **Interaction:** The system SHALL provide an option to select multiple quotes (e.g., checkboxes on each quote card) for a side-by-side comparison. A "Compare Selected" button SHALL become active when at least two quotes are selected.
    *   **Content/Microcopy:**
        *   **Checkbox Label:** "Add to Compare" (on each quote card).
        *   **Button Text:** "Compare Selected ([X])" (where X is the number of selected quotes).
        *   **Comparison Page Title:** "Side-by-Side Comparison"
        *   **Comparison Table Headings:** "Feature", "[Provider 1 Name]", "[Provider 2 Name]", etc.
        *   **Comparison Table Rows:** List key policy features, excesses, payment options, ratings, etc., with values for each selected provider.
    *   The system SHALL display a dedicated comparison view (e.g., a table) highlighting differences and similarities between selected policies.
    *   *(Prototype Note: The comparison will be limited to a pre-defined set of key features for dummy quotes).*
*   **FR3: Transparency Disclosure (How We Work)**
    *   **Prerequisites:** None.
    *   **Navigation:** A prominent link (e.g., "How We Work", "Our Business Model") SHALL be available in the footer or main navigation.
    *   **Content/Microcopy:**
        *   **Page Title:** "How [Your Brand Name] Works"
        *   **Sections:**
            *   **"How We Make Money":** Clearly explain commission-based model, CPC, lead generation.
            *   **"Our Impartiality Promise":** State commitment to unbiased results.
            *   **"How Results Are Ordered":** Explain default sorting (e.g., "cheapest first") and how users can change it.
            *   **"Who We Compare":** List the number of providers and categories compared.
            *   **"Regulatory Compliance":** Briefly mention FCA, ICO, CMA adherence with links to full policies.
    *   The system SHALL provide a dedicated, easily accessible page explaining the PCW's business model, revenue generation, and commitment to impartiality.
    *   The page SHALL clearly state how comparison results are ordered by default and how users can modify sorting/filtering.
*   **FR4: Educational Content & Guides**
    *   **Prerequisites:** None.
    *   **Navigation:** A "Guides" or "Blog" section SHALL be accessible from the main navigation or footer.
    *   **Content/Microcopy:**
        *   **Section Title:** "Guides & Advice"
        *   **Search Input Field Label:** "Search Guides"
        *   **Search Input Placeholder:** "e.g., Car insurance excess, No claims bonus"
        *   **Search Button Text:** "Search"
        *   **Article Titles:** (e.g., "Understanding Car Insurance Excess", "What is No Claims Discount?", "Choosing the Right Home Insurance").
        *   **Article Content:** Clear, concise, jargon-free explanations, using bullet points, headings, and potentially infographics.
    *   The system SHALL host a library of educational articles and guides to help users understand financial products and make informed decisions.
    *   The system SHALL provide a search input field to allow users to find relevant guides.
    *   *(Prototype Note: A few dummy articles will be created and displayed, demonstrating the CMS functionality. Search functionality will be basic, filtering dummy articles by title/keywords).*
*   **FR5: Customer Reviews & Ratings Display**
    *   **Prerequisites:**
        *   User is viewing the comparison results page or a provider's detail page.
        *   The `CMS Service` has dummy review data.
    *   **Interaction:** Each quote card SHALL display an aggregate star rating (e.g., "4.5/5 stars") and the number of reviews. Clicking on this SHALL open a modal or navigate to a page showing detailed reviews.
    *   **Content/Microcopy:**
        *   **Rating Display:** "X.X/5 stars (Y reviews)" (on quote cards and provider details).
        *   **Review Modal/Page Title:** "Customer Reviews for [Provider Name]"
        *   **Review Elements:** Reviewer name (anonymized), star rating, review text, date.
    *   The system SHALL display aggregate customer ratings and individual reviews for each provider, sourced from an internal CMS (or mocked for prototype).
    *   *(Prototype Note: Dummy review data will be used, associated with fictional providers).*

### **5. Non-Functional Requirements:**

*   **NFR1: Performance:**
    *   **Policy Details Load:** Comprehensive policy details (FR1) SHALL load within 1.5 seconds for 90% of users.
    *   **Side-by-Side Comparison Load:** The comparison view (FR2) SHALL render within 2 seconds for 90% of users, assuming up to 4 selected quotes.
    *   **Educational Content Load:** Articles (FR4) SHALL load within 1 second for 90% of users.
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general NFRs).
*   **NFR2: Security:**
    *   All content served SHALL be protected against XSS and other injection attacks.
    *   Links to external sites (e.g., T&Cs) SHALL be handled securely (e.g., `rel="noopener noreferrer"`).
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general NFRs and `06_security_access_considerations/` for detailed strategies).
*   **NFR3: Regulatory Compliance:**
    *   The "How We Work" page (FR3) SHALL meet CMA's "CARE" principles for clarity, accuracy, and responsibility.
    *   All information presented SHALL be fair, clear, and not misleading, adhering to FCA guidelines.
    *   (Refer to `project_definition/05_regulatory_compliance.md` for detailed compliance requirements).
*   **NFR4: Usability:**
    *   Information architecture SHALL be intuitive, allowing users to easily find detailed information.
    *   Content SHALL be scannable and digestible, avoiding information overload.
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general NFRs).

### **6. UI/UX Considerations:**

*   **Design System Adherence:** The UI SHALL strictly adhere to the Agoda-inspired visual theme and component library defined in `09_ui_ux_accessibility/01_design_system_guidelines.md`. This includes color palette, typography (Roboto), card-based layouts, and 4px border radius.
*   **Content Strategy:** All content, especially educational guides and transparency disclosures, SHALL follow the principles of clear, encouraging, and empathetic tone of voice, and visual/scannable writing outlined in `09_ui_ux_accessibility/04_content_strategy.md`.
*   **Responsiveness:** All detail views, comparison tables, and content pages SHALL be fully responsive and optimized for desktop, tablet, and mobile devices.
*   **Accessibility:** The UI SHALL meet WCAG 2.1 Level AA standards, ensuring keyboard navigation, screen reader compatibility, and sufficient color contrast, especially for complex tables and forms.
*   **Visual Hierarchy:** Clear visual hierarchy will be used to present detailed information, using headings, subheadings, and visual separators to break up content.

### **7. Technical Considerations:**

*   **Microservices Involved:**
    *   **Frontend (React):** Renders policy details, comparison tables, transparency page, educational content, and reviews. Manages UI state for comparison selection.
    *   **Web App BFF (Node.js/Express):** Aggregates data from `Quotes Service`, `Providers Service`, and `CMS Service` to present comprehensive policy details and reviews.
    *   **Quotes Service (Node.js/Express):** Provides normalized quote data and associated policy features.
    *   **Providers Service (Node.js/Express):** Provides provider-specific information (logo, contact, underwriter details).
    *   **CMS Service (Node.js/Express):** Manages and serves educational articles, guides, and customer reviews.
*   **State Management:**
    *   **Frontend UI State:** Managed using React Hooks (e.g., for modal visibility, selected quotes for comparison, search input value) and Redux Toolkit (`createSlice` for global filter/sort state).
    *   **Content Data State:** Managed using RTK Query for fetching and caching policy details, articles, and reviews.
*   **Data Models:** Utilize existing `Quote`, `Provider`, and `Product` models. Introduce `Article` and `Review` models within the `CMS Service` (refer to `08_data_management/05_database_schema_design.md`).
*   **Error Handling:** Implement robust error handling for data retrieval, ensuring graceful degradation if a specific piece of information (e.g., a provider's T&Cs link) is unavailable.
*   **Dummy Data Strategy (Prototype):**
    *   `Quotes Service` will return dummy policy features and exclusions.
    *   `Providers Service` will provide dummy underwriter information and T&C links.
    *   `CMS Service` will serve dummy articles and reviews.

### **8. Acceptance Criteria:**

*   Users can click "View Details" on a quote card and see a modal/page with comprehensive policy features, exclusions, excess, payment options, and a link to T&Cs.
*   The policy details clearly state the underwriter if different from the brand.
*   Users can select at least two quotes and initiate a side-by-side comparison, which displays key features in a table format.
*   The "How We Work" page is accessible and clearly explains the PCW's business model, revenue, and impartiality.
*   The "How We Work" page explicitly states how results are ordered by default.
*   Users can navigate to a "Guides" section and view dummy educational articles.
*   The "Guides" section includes a search input field with a placeholder.
*   Users can type into the search input field to filter dummy articles by title/keywords.
*   Each quote card and provider detail page displays an aggregate star rating and number of reviews (dummy data).
*   Clicking on the rating/reviews opens a view with individual dummy customer reviews.
*   All transparency and information pages are fully responsive and accessible (WCAG 2.1 Level AA).

### **9. Out of Scope (for this prototype iteration):**

*   User submission of reviews or ratings.
*   Complex content personalization based on user behavior for educational content.
*   Integration with external review platforms (e.g., Trustpilot).
*   Advanced analytics on content consumption.
*   Multi-language support for content.
*   Dynamic generation of T&Cs documents; will use static links.
*   Real-time updates of policy details from external provider APIs; will use pre-defined dummy data.
