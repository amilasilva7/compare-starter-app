### **Feature Requirement Specification: Data-Driven & Personalization Capabilities**

---

### **1. Feature Name:**
Data-Driven & Personalization Capabilities

### **2. Feature Goal:**
To provide users with a personalized and efficient experience by enabling secure account management, saving user details for convenience, offering relevant product recommendations, and delivering timely reminders, thereby increasing engagement and conversion rates. This feature aims to leverage user data (with explicit consent) to add significant value beyond basic comparison, serving as a key differentiator for the PCW prototype.

### **3. User Stories:**

*   **As a Customer, I want to** create and manage a secure user account, **so that I can** save my details and access personalized features.
*   **As a Customer, I want to** securely log in to my account, **so that I can** access my saved information and personalized dashboard.
*   **As a Customer, I want to** save my car and personal details in my profile after completing a quote, **so that I don't** have to re-enter them for every new comparison.
*   **As a Customer, I want to** view a personalized dashboard with my saved quotes, purchased policies, and relevant product recommendations, **so that I can** easily manage my financial products and discover new savings opportunities.
*   **As a Customer, I want to** receive personalized product recommendations based on my profile, **so that I can** discover relevant deals tailored to my specific needs and purchase history.
*   **As a Customer, I want to** set and receive smart reminders (e.g., for policy renewals), **so that I don't** miss important dates and can compare new quotes proactively.
*   **As a Customer, I want to** be confident that my personal data is handled securely and in compliance with privacy regulations, **so that I can** trust the platform with my information.

### **4. Functional Requirements:**

*   **FR1: User Account Creation & Management**
    *   **Prerequisites:**
        *   The user SHALL have an active internet connection.
        *   Email verification service SHALL be available (mocked for prototype).
    *   **User Registration:**
        *   The system SHALL provide a secure user registration process accessible via a "Register" button in the main navigation (e.g., header, footer, or dedicated registration page).
        *   **Content/Microcopy:**
            *   **Page Title:** "Create Your Account"
            *   **Field Labels:** "Email Address", "Password", "Confirm Password"
            *   **Button Text:** "Register"
            *   **Link:** "Already have an account? Login" (redirects to login form)
        *   **Validation & Error Messages (Inline & Real-time):**
            *   **Email Invalid Format:** "Please enter a valid email address (e.g., name@example.com)."
            *   **Email Already Registered:** "This email address is already registered. Please login or use 'Forgot Password'."
            *   **Password Mismatch:** "Passwords do not match."
            *   **Password Weak:** "Password must be at least 8 characters long, include an uppercase letter, a lowercase letter, a number, and a special character."
            *   **Generic Server Error:** "Registration failed. Please try again later."
        *   The system SHALL send an email verification link to the registered email address.
        *   **Email Subject:** "Verify Your [Your Brand Name] Account"
        *   **Email Content (Dummy for Prototype):** "Hi [User's Email], please click the link below to verify your email and activate your account: [Mock Verification Link, e.g., a URL that confirms verification via a GET request to our backend]."
        *   The system SHALL confirm successful registration and prompt for email verification.
        *   **Confirmation Message (UI, after registration):** "Registration successful! Please check your email to verify your account." (Displayed prominently at the top of the page).
        *   **Redirection after Verification:** Upon successful email verification, the system SHALL redirect the user to a "Verification Successful" page or directly to their dashboard.
    *   **User Login:**
        *   The system SHALL provide a secure user login process accessible via a "Login" button in the main navigation.
        *   **Content/Microcopy:**
            *   **Page Title:** "Login to Your Account"
            *   **Field Labels:** "Email Address", "Password"
            *   **Button Text:** "Login"
            *   **Link:** "Forgot Password?" (redirects to password reset flow)
            *   **Link:** "Don't have an account? Register" (redirects to registration form)
        *   **Validation & Error Messages:**
            *   **Invalid Credentials:** "Invalid email or password."
            *   **Account Unverified:** "Your account is not verified. Please check your email for the verification link." (Displayed above login form with a "Resend Verification Email" link).
            *   **Account Locked:** "Your account is temporarily locked due to too many failed attempts. Please try again in 5 minutes." (Displayed above login form).
            *   **Generic Server Error:** "Login failed. Please try again later."
        *   The system SHALL implement account lockout after multiple failed login attempts (refer to NFRs).
        *   **Refresh Behavior:** If the user refreshes the login page, the form fields SHALL be cleared.
    *   **User Profile Management:**
        *   The system SHALL allow authenticated users to view and update their personal details (e.g., first name, last name, address, contact number) via a "My Profile" section accessible from their dashboard navigation.
        *   The system SHALL allow authenticated users to change their password via the "My Profile" section, requiring current and new password confirmation.
        *   **Content/Microcopy:**
            *   **Page Title:** "My Profile"
            *   **Field Labels (Text Inputs):** "First Name", "Last Name", "Address Line 1", "Address Line 2", "City", "Postcode", "Phone Number"
            *   **Button Text:** "Save Changes" (for profile details), "Change Password" (for password update).
            *   **Confirmation Message (Toast/Banner):** "Profile updated successfully!" or "Password changed successfully!"
            *   **Error Message (Update Failed):** "Failed to update profile. Please try again."
            *   **Error Message (User Unavailable):** "User information could not be loaded. Please try again."
*   **FR2: Saved Details & Pre-filling**
    *   The system SHALL allow authenticated users to save their car and driver details (from FR1 of Car Insurance Quote FRS) to their profile after completing a quote, via a clear UI option on the quote results page.
    *   **Content/Microcopy:**
        *   **Button on Quote Results Page:** "Save Quote Details to Profile" (Prominently displayed near the quote results, perhaps below each quote card or as a general option).
        *   **Confirmation Message (Pop-up/Toast):** "Your details have been saved to your profile."
        *   **Error Message (Save Failed):** "Failed to save details. Please try again."
    *   When an authenticated user starts a new quote process, the system SHALL offer to pre-fill the questionnaire with their most recently saved details.
    *   **Content/Microcopy (Pre-fill Prompt, displayed at the start of the quote form):** "We found saved details in your profile. Would you like to use them to pre-fill this form?" (with "Yes, Pre-fill" and "No, Start Fresh" buttons).
*   **FR3: Personalized Dashboard**
    *   The system SHALL provide an authenticated user with a personalized dashboard accessible via a "My Dashboard" link after successful login.
    *   **Dashboard Content:**
        *   Display a list of saved quotes (from FR4 of Car Insurance Quote FRS), showing provider, premium, and key features, with a "View Details" or "Compare Again" button.
        *   Display a list of purchased policies (dummy data for prototype), including policy type, provider, and renewal date, with a "View Policy" button (linking externally or to a mock page).
        *   Display personalized product recommendations (FR4), presented as interactive cards.
    *   **Content/Microcopy:**
        *   **Page Title:** "My Dashboard"
        *   **Section Headings:** "My Saved Quotes", "My Policies", "Recommended for You"
        *   **Empty State (Saved Quotes):** "You haven't saved any quotes yet. Start comparing now!" (with a "Compare Now" button).
        *   **Empty State (Policies):** "No policies found. Compare and buy your first policy!" (with a "Add Policy" or "Compare Now" button).
*   **FR4: Personalized Product Recommendations**
    *   The system SHALL generate personalized product recommendations based on the user's profile data (e.g., age, location, saved quotes, purchased policies).
    *   **Recommendation Logic (Prototype):** For the prototype, recommendations will be based on simple, pre-defined rules (e.g., if user has car insurance, recommend home insurance; if an energy bill is due soon, recommend energy comparison).
    *   The system SHALL display these recommendations on the user's dashboard and potentially other relevant pages (e.g., after completing a quote).
    *   **Content/Microcopy:**
        *   **Heading:** "Based on your profile, you might be interested in..." (Displayed above the recommendation cards).
        *   Each recommendation SHALL be presented in a card format, similar to quote cards, with product type (e.g., "Home Insurance"), a brief description (e.g., "Protect your home and belongings"), and a "Compare Now" button.
*   **FR5: Smart Reminders**
    *   The system SHALL allow authenticated users to set policy renewal reminders for any saved quote or purchased policy.
    *   **Content/Microcopy:**
        *   **Button/Link:** "Set/Manage Renewal Reminder" (Displayed on saved quote/policy details).
        *   **Reminder Options (within a modal/form):** "1 month before", "2 weeks before", "1 week before", "Custom Date" (with a date picker).
        *   **Button Text:** "Save Reminder"
        *   **Confirmation Message (Pop-up/Toast):** "Renewal reminder set for [Policy Type] on [Date]." or "Reminder updated!"
        *   **Error Message:** "Failed to set reminder. Please try again."
    *   The system SHALL send email notifications to the user for upcoming renewals based on their set preferences.
    *   **Email Subject:** "Reminder: Your [Policy Type] Policy Renewal is Approaching!" (Dummy email will be logged to console for prototype).
    *   **Email Content (Dummy):** "Hi [User's First Name], your [Policy Type] policy with [Provider Name] is due for renewal on [Date]. Don't forget to compare new quotes to find the best deal! [Link to Compare on your site]"
    *   *(Prototype Note: Email sending will be mocked or logged to console/mock service for demonstration purposes).*

### **5. Non-Functional Requirements:**

*   **NFR1: Performance:**
    *   **User Login:** SHALL complete within 2 seconds for 90% of users.
    *   **Dashboard Load:** SHALL load within 3 seconds for 90% of authenticated users (rendering saved quotes, policies, and recommendations).
    *   **Profile Update:** Profile updates SHALL complete within 1 second.
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general performance NFRs).
*   **NFR2: Security:**
    *   All user account data (email, password hashes, saved personal details) SHALL be encrypted at rest and in transit.
    *   Password hashing SHALL use a strong, rainbow table-resistant algorithm (e.g., bcrypt, Argon2).
    *   Account lockout mechanisms SHALL prevent brute-force attacks.
    *   Authentication tokens (e.g., JWTs) SHALL be securely managed (e.g., HTTP-only cookies).
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general security NFRs and `06_security_access_considerations/` for detailed strategies).
*   **NFR3: Data Privacy (Compliance with UK GDPR):**
    *   User explicit consent SHALL be obtained for data collection and personalization activities where required (e.g., clearly stated in Privacy Policy, explicit opt-in for certain data uses).
    *   Users SHALL have the right to access, rectify, and erase their personal data stored in their profile via specific functionalities.
    *   (Refer to `project_definition/05_regulatory_compliance.md` for general regulatory compliance).
*   **NFR4: Usability:**
    *   User registration and login forms SHALL be intuitive and easy to complete.
    *   The user dashboard SHALL clearly present information and navigation options.
    *   (Refer to `project_definition/08_non_functional_requirements.md` for general NFRs).

### **6. UI/UX Considerations:**

*   **Design System Adherence:** The UI SHALL strictly adhere to the Agoda-inspired visual theme and component library defined in `09_ui_ux_accessibility/01_design_system_guidelines.md`. This includes color palette, typography (Roboto), card-based layouts, and 4px border radius.
*   **Interactive Content:** User flows (e.g., registration, profile updates) SHALL be presented in a clear, guided manner, consistent with the interactive content principles from `09_ui_ux_accessibility/04_content_strategy.md`.
*   **Personalized Dashboard:** The dashboard layout SHALL prioritize key user information (saved quotes, policies) and personalized recommendations concisely, reflecting our Agoda-inspired card-based layout and information density principles.
*   **Responsiveness:** All account management, dashboard, and profile pages SHALL be fully responsive and optimized for desktop, tablet, and mobile devices, ensuring a consistent and accessible experience across screen sizes.
*   **Accessibility:** All user-facing components SHALL meet WCAG 2.1 Level AA standards, ensuring keyboard navigation, screen reader compatibility, and sufficient color contrast.
*   **Visual Feedback:** The system SHALL provide clear visual feedback for successful operations (e.g., profile saved) and errors (e.g., invalid login).

### **7. Technical Considerations:**

*   **Microservices Involved:**
    *   **Frontend (React):** Handles UI rendering for registration, login, profile, and dashboard. Manages user authentication flow.
    *   **Web App BFF (Node.js/Express):** Acts as a secure gateway, orchestrating API calls between the frontend and backend services for user management, profile updates, and dashboard data aggregation.
    *   **Users Service (Node.js/Express):** Manages user accounts, authentication, authorization, and storage of personal data.
    *   **Quotes Service (Node.js/Express):** Provides saved quotes data to the BFF for display on the user dashboard.
    *   **Personalization Service (Node.js/Express - New):** A dedicated service to generate and manage personalized recommendations and reminders based on user profiles and other data.
*   **State Management:**
    *   **Frontend UI State:** Managed using React Hooks (e.g., form input state for registration/login) and Redux Toolkit (`createSlice` for user session status, authentication tokens, notification state).
    *   **User Data State:** Managed using RTK Query for fetching and updating user profiles, saved quotes, and personalization data, leveraging its caching and invalidation features.
*   **Data Models:** Define clear data models for `User`, `SavedQuote`, `Policy`, `Recommendation`, and `Reminder` (refer to `08_data_management/05_database_schema_design.md`).
*   **Security Implementation:** Utilize JSON Web Tokens (JWTs) for session management between the BFF and backend services. Store password hashes using bcrypt. Implement secure cookie management for JWTs. Enforce RBAC for user access. 
*   **Error Handling:** Implement robust error handling across all services, ensuring secure and user-friendly error messages are propagated to the frontend.
*   **Dummy Data Strategy (Prototype):**
    *   `Users Service` will manage dummy user accounts and profiles.
    *   `Quotes Service` will provide dummy data for saved quotes.
    *   `Personalization Service` will generate dummy recommendations based on simple rules and manage dummy reminders.
    *   Email verification and reminder emails will be mocked (e.g., logged to console/mock service).

### **8. Acceptance Criteria:**

*   A new user can successfully register with valid dummy credentials and receive a dummy email verification (console log).
*   A registered user can successfully perform a dummy email verification action and then log in.
*   An authenticated user can view, update, and save their profile details (First Name, Last Name, Address, Postcode, Phone Number).
*   An authenticated user can successfully change their password.
*   An authenticated user can save car/driver details from a quote to their profile.
*   An authenticated user can initiate a new quote process and successfully pre-fill the questionnaire with their saved details.
*   The personalized dashboard loads within 3 seconds and displays at least:
    *   3 dummy saved quotes.
    *   2 dummy purchased policies.
    *   3 dummy personalized recommendations.
*   An authenticated user can successfully set a policy renewal reminder and receive a dummy email reminder (console log).
*   All user account operations (registration, login, profile update) meet the specified NFRs for performance and security.
*   The authentication flow correctly handles invalid credentials and account lockout scenarios, displaying appropriate error messages.

### **9. Out of Scope (for this prototype iteration):**

*   Full implementation of Multi-Factor Authentication (MFA); only design for future integration.
*   Advanced password recovery mechanisms (e.g., SMS verification, security questions).
*   Integration with real email sending services; will use mocked email services or console output.
*   Integration with external financial APIs (e.g., for credit score, bank accounts).
*   Sophisticated AI/ML algorithms for advanced personalization; will use rule-based recommendations.
*   Comprehensive user data deletion/right to be forgotten functionality beyond basic profile updates.
*   Custom user role management, beyond a basic "customer" role.
*   Internationalization (i18n) or localization (l10n) for user-facing content.