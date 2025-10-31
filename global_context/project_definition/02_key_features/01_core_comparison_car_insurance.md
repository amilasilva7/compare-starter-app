### **Feature Requirement Specification: Core Comparison Engine - Car Insurance Quote**

---

### **1. Feature Name:**
Core Comparison Engine - Car Insurance Quote

### **2. Feature Goal:**
To enable users to quickly and easily obtain and compare car insurance quotes from multiple providers based on their input, facilitating an informed decision-making process. This feature serves as the foundational value proposition of the PCW prototype, demonstrating the end-to-end comparison journey.

### **3. User Stories:**

*   **As a Customer, I want to** easily input my car and personal details through a guided, interactive process, **so that I can** receive relevant car insurance quotes without feeling overwhelmed.
*   **As a Customer, I want to** view multiple car insurance quotes in a clear, card-based, and comparable format, **so that I can** quickly identify the best option for my needs.
*   **As a Customer, I want to** see key policy details (e.g., excess, coverage level, payment options) for each quote, **so that I can** understand what I'm buying beyond just the price.
*   **As a Customer, I want to** be able to refine my search or apply filters/sorting to the results, **so that I can** narrow down options based on my specific preferences.
*   **As a Customer, I want to** click through to the provider's website from a selected quote, **so that I can** finalize the purchase seamlessly.
*   **As a Customer, I want to** receive quotes quickly, **so that I don't** have to wait long for results.

### **4. Functional Requirements:**

*   **FR1: User Input Collection (Interactive Questionnaire)**
    *   **Prerequisites:**
        *   The user SHALL NOT be required to log in or create an account to access or complete the car insurance quote questionnaire.
        *   The user SHALL have an active internet connection.
    *   **Navigation & Flow:**
        *   The questionnaire SHALL be accessible from the homepage via a prominent "Get Car Insurance Quote" Call-to-Action button.
        *   The system SHALL present the questionnaire as a multi-step, guided process, allowing progression only upon valid input for the current step.
        *   The system SHALL allow users to navigate back to previous steps using a "Back" button without losing previously entered data for the current session.
        *   **Pop-up Message (Exit Confirmation):** If a user attempts to navigate away from the questionnaire mid-progress (e.g., closing tab, navigating to another page), the system SHALL display a confirmation pop-up: "Are you sure you want to leave? Your progress will be lost." with "Leave" and "Stay" options.
        *   **Refresh Behavior:** If the user refreshes the page mid-questionnaire, the system SHALL reset the questionnaire to the first step, losing all unsaved progress for the current session.
    *   **Content/Microcopy for Questionnaire Steps:**
        *   **Step 1 (Vehicle Details):**
            *   **Heading:** "Tell us about your car."
            *   **Field Label:** "Vehicle Registration Number"
            *   **Placeholder:** "e.g., AB12 CDE"
            *   **Help Text:** "This helps us find the right quotes for you."
            *   **Field Label:** "Estimated Annual Mileage"
            *   **Placeholder:** "e.g., 8000 miles"
            *   **Field Label:** "Where do you park overnight?"
            *   **Options:** "Garage", "Driveway", "Street", "Other" (as radio buttons or dropdown)
            *   **Button Text:** "Continue"
        *   **Step 2 (Main Driver Details):**
            *   **Heading:** "Now, about the main driver."
            *   **Field Label:** "Date of Birth"
            *   **Placeholder:** "DD/MM/YYYY"
            *   **Field Label:** "Occupation"
            *   **Placeholder:** "e.g., Software Engineer"
            *   **Field Label:** "Postcode"
            *   **Placeholder:** "e.g., SW1A 0AA"
            *   **Field Label:** "Driving Licence Type"
            *   **Options:** "Full UK", "Provisional", "EU", "Other" (as radio buttons or dropdown)
            *   **Field Label:** "Years No Claims Discount (NCD)"
            *   **Options:** "0", "1", "2", "3", "4", "5+", "None" (as dropdown)
            *   **Field Label:** "Have you had any claims or convictions in the last 5 years?"
            *   **Options:** "Yes", "No" (as radio buttons)
            *   **Button Text:** "Get Quotes"
        *   **Step 3 (Desired Policy Details - *Implicit in FR1, but for clarity*):**
            *   **Field Label:** "Desired Coverage Type"
            *   **Options:** "Third Party", "Third Party Fire & Theft", "Comprehensive" (as radio buttons or dropdown)
            *   **Field Label:** "Desired Voluntary Excess Amount"
            *   **Options:** "£0", "£100", "£250", "£500", "£1000" (as dropdown)
    *   **Validation & Error Messages:**
        *   The system SHALL validate user input in real-time for format and completeness.
        *   **Generic Invalid Input:** "Please enter a valid value for this field." (Displayed below the field in red text).
        *   **Specific Error Messages:**
            *   "Vehicle Registration Number: Please enter a valid UK registration number (e.g., AB12 CDE)."
            *   "Estimated Annual Mileage: Please enter a valid number of miles (e.g., 5000)."
            *   "Date of Birth: Please enter a valid date of birth in DD/MM/YYYY format."
            *   "Postcode: Please enter a valid UK postcode."
            *   "Occupation: Please select your occupation."
            *   "Driving Licence Type: Please select your driving licence type."
            *   "NCD: Please select your years of No Claims Discount."
            *   "Claims/Convictions: Please indicate if you've had claims or convictions."
            *   "Coverage Type: Please select your desired coverage type."
            *   "Voluntary Excess: Please select your desired voluntary excess."
    *   *(Prototype Note: Initial focus on essential fields; advanced features like pre-filling from registration lookup or adding additional drivers are out of scope for this prototype iteration).* 
*   **FR2: Quote Generation Request & Orchestration**
    *   The system SHALL, upon submission of valid user input, send a request to the Backend-for-Frontend (BFF) to initiate quote generation.
    *   **Loading State Content:**
        *   The system SHALL display a full-screen overlay with a central loading spinner (e.g., a rotating circle).
        *   **Loading Message:** "Searching for the best car insurance quotes..." (Displayed below the spinner).
    *   **Error Message (Quote Generation Failure):** "We couldn't get quotes right now. Please try again later or check your internet connection." (Displayed as a prominent banner or pop-up, with a "Try Again" button).
    *   **Refresh Behavior:** If the user refreshes the page during the quote generation loading state, the system SHALL restart the quote generation process from the beginning of FR2 (i.e., re-submit the request).
    *   The BFF SHALL orchestrate requests to the internal `Quotes Service` and `Providers Service` to gather quotes from multiple providers.
    *   The `Providers Service` SHALL utilize the Adapter Pattern to communicate with external third-party insurance providers.
    *   *(Prototype Note: For this prototype, the `Providers Service` will return pre-defined dummy quote data for a set of fictional providers, simulating real provider responses. No actual external API calls will be made).* 
*   **FR3: Quote Aggregation & Normalization**
    *   The `Quotes Service` SHALL aggregate responses received from all (dummy) providers.
    *   The `Quotes Service` SHALL normalize provider-specific policy details into a consistent internal data model for comparison.
*   **FR4: Quote Display (Card-Based Results)**
    *   **Prerequisites:**
        *   The user SHALL NOT be required to log in or create an account to view the quote results.
    *   **Content/Microcopy for Results Page:**
        *   **Page Title:** "Your Car Insurance Quotes" (Displayed prominently at the top of the page).
        *   **No Results Message:** "Sorry, we couldn't find any quotes matching your criteria. Please try adjusting your details or contact support." (Displayed centrally if no quotes are returned).
        *   **Quote Card Elements (for each dummy quote):**
            *   **Provider Name:** (e.g., "Fictional InsureCo", "Alpha Insurance", "Beta Protect")
            *   **Provider Logo:** (dummy image, e.g., "InsureCo Logo")
            *   **Premium Price:** (e.g., "£450.00 / year", "£37.50 / month")
            *   **Key Features (example labels):** "Voluntary Excess:", "Coverage:", "Payment Option:", "Legal Cover:", "Breakdown Cover:" (Displayed as bullet points or clear labels within the card).
            *   **Button Text:** "Go to Provider" (Agoda-inspired vibrant yellow).
        *   **Dummy Data Indicator:** The UI SHALL clearly display a message indicating the use of dummy data.
            *   **Indicator Text (prominently displayed at the top of the results list):** "Note: These are dummy quotes for prototype demonstration only and do not reflect real prices or providers."
    *   Each quote card SHALL clearly present: Provider Name and Logo (dummy logos for prototype), Premium Price (dummy data), Key Policy Features (e.g., excess amount, coverage level, payment options - dummy data), and a prominent "Go to Provider" Call-to-Action button.
    *   *(Prototype Note: The UI will clearly indicate that displayed quotes are dummy data).* 
*   **FR5: Filtering & Sorting**
    *   The system SHALL provide user interface elements to filter quotes by criteria such as provider, coverage level, and payment options.
    *   **Content/Microcopy for Filters & Sort:**
        *   **Filter Section Heading:** "Refine Your Results" (Displayed in a sidebar or collapsible section).
        *   **Filter Labels:** "Provider", "Coverage Type", "Payment Options", "Voluntary Excess" (Each with a list of selectable options).
        *   **Sort Dropdown Label:** "Sort by:"
        *   **Sort Options:** "Price (Lowest First)", "Price (Highest First)", "Provider (A-Z)" (as a dropdown menu).
    *   **Interaction:** Applying a filter or sort option SHALL immediately update the displayed quote results without a full page refresh.
    *   The system SHALL visually indicate the currently active filters and sort order.
    *   The system SHALL provide user interface elements to sort quotes by price (low to high, high to low) as a minimum.
*   **FR6: Provider Click-Through**
    *   The system SHALL, upon clicking the "Go to Provider" button, redirect the user to a simulated provider's website (e.g., a static placeholder page or a simple mock URL).
    *   **Interaction:** Clicking the "Go to Provider" button SHALL open the simulated provider's website in a new browser tab/window.
    *   **Pop-up Message (Redirection Confirmation):** Upon clicking "Go to Provider," the system SHALL display a brief pop-up message (e.g., a toast notification at the bottom of the screen) confirming the redirection: "Redirecting you to [Provider Name]..." This message SHALL disappear automatically after 3-5 seconds.
    *   *(Prototype Note: For the prototype, this redirection will be a simple URL to demonstrate the flow, without actual data transfer to a real provider).* 

### **5. Non-Functional Requirements:**

*   **NFR1: Performance:**
    *   **Quote Generation Time:** The system SHALL display initial quote results within 5 seconds from the final submission of the questionnaire (FR1) for 90% of users.
    *   **Page Load Time (Results Page):** The results page SHALL load within 2.5 seconds (LCP) for 75% of users.
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general NFRs).
*   **NFR2: Security:**
    *   All user input data SHALL be transmitted securely using HTTPS.
    *   No Personally Identifiable Information (PII) SHALL be stored for anonymous quote requests.
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general NFRs).
*   **NFR3: Usability:**
    *   The interactive questionnaire SHALL be intuitive and easy to complete for users with varying technical proficiencies.
    *   The results page SHALL be easy to navigate and understand, allowing users to quickly compare options.
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general NFRs).
*   **NFR4: Reliability:**
    *   The quote generation process SHALL have a success rate of 99% (for internal mock calls in prototype).
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general NFRs).

### **6. UI/UX Considerations:**

*   **Design System Adherence:** The UI SHALL strictly adhere to the Agoda-inspired visual theme and component library defined in `09_ui_ux_accessibility/01_design_system_guidelines.md`. This includes color palette, typography (Roboto), card-based layouts, and 4px border radius.
*   **Interactive Content:** The questionnaire SHALL follow the principles of interactive content outlined in `09_ui_ux_accessibility/04_content_strategy.md`, using a guided, conversational approach with clear headings and concise questions.
*   **Responsiveness:** The entire user flow (questionnaire, loading state, results page) SHALL be fully responsive and optimized for desktop, tablet, and mobile devices, ensuring a consistent experience across screen sizes.
*   **Accessibility:** The UI SHALL meet WCAG 2.1 Level AA standards, ensuring keyboard navigation, screen reader compatibility, and sufficient color contrast.
*   **Visual Feedback:** The system SHALL provide clear visual feedback for all user interactions (e.g., button clicks, form field validation).

### **7. Technical Considerations:**

*   **Microservices Involved:**
    *   **Frontend (React):** Handles UI rendering, user input, and display of results.
    *   **Web App BFF (Node.js/Express):** Orchestrates calls between frontend and backend services, handles quote generation requests, and aggregates responses.
    *   **Quotes Service (Node.js/Express):** Aggregates and normalizes quote data from providers.
    *   **Providers Service (Node.js/Express):** Manages communication with (mock) third-party insurance providers using the Adapter Pattern.
    *   **Reference Data Service (Node.js/Express):** Provides static reference data (e.g., postcode validation, occupation lists, car makes/models).
*   **State Management:**
    *   **Frontend UI State:** Managed using React Hooks (e.g., `useState` for form fields) and Redux Toolkit (`createSlice` for global UI state like filter selections).
    *   **Quote Data State:** Managed using RTK Query for fetching, caching, and invalidating quote results.
*   **Data Models:**
    *   Define clear data models for `QuoteRequest` (user input) and `QuoteResponse` (normalized quote data) to ensure consistent data exchange between services.
*   **Error Handling:** Implement robust error handling across all services, with clear error propagation to the frontend to display user-friendly messages.
*   **Dummy Data Strategy (Prototype):**
    *   The `Providers Service` will be configured to return a fixed set of dummy quotes for various input combinations.
    *   Dummy provider logos will be used.
    *   The `Reference Data Service` will provide dummy data for dropdowns (e.g., occupations, NCD years).

### **8. Acceptance Criteria:**

*   The user can successfully complete the multi-step questionnaire with valid dummy data.
*   All validation rules for input fields are correctly enforced with appropriate error messages displayed.
*   The system displays a loading spinner and message during quote generation.
*   The system displays a minimum of 3 dummy car insurance quotes in a card-based format on the results page.
*   Each quote card displays the provider name, logo, premium price, and at least 3 key policy features.
*   The results page clearly indicates that dummy data is being displayed.
*   The user can filter quotes by at least one criterion (e.g., coverage type) and the results update immediately.
*   The user can sort quotes by price (lowest first) and the results update immediately.
*   Clicking "Go to Provider" redirects the user to a simulated provider page in a new tab, with a temporary confirmation message.
*   The questionnaire and results page are fully responsive across desktop, tablet, and mobile views.
*   The questionnaire allows navigation back to previous steps without data loss in the current session.

### **9. Out of Scope (for this prototype iteration):**

*   Actual integration with real third-party insurance provider APIs.
*   User authentication/account creation for quote generation (quotes are anonymous).
*   Saving quotes to a user account.
*   Advanced personalization features (e.g., AI-driven recommendations).
*   Adding multiple drivers or vehicles.
*   Detailed policy customization beyond basic coverage type and excess.
*   Payment processing or purchase finalization on our platform.
*   Complex analytics or reporting for this feature.
*   Internationalization (i18n) or localization (l10n).
*   Deep linking into provider sites with pre-filled data.
