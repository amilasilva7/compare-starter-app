# Design System Guidelines

Our Design System is a collection of reusable components, guided by clear standards, that can be assembled to build any number of applications. It ensures visual consistency, improves development efficiency, and enhances the overall user experience.

## 1. What is a Design System?

A Design System is more than just a style guide or a component library. It's a single source of truth for all design and development decisions, encompassing:
*   **Design Principles:** Core values that guide our design decisions.
*   **Brand Guidelines:** Logo usage, typography, color palettes.
*   **Component Library:** Reusable UI components (buttons, forms, navigation, cards).
*   **Patterns:** Solutions for common UI problems (e.g., form validation, data display).
*   **Documentation:** Guidelines on how to use components, when to use them, and their accessibility considerations.

## 2. Key Benefits
*   **Consistency:** Ensures a unified look and feel across the entire application.
*   **Efficiency:** Speeds up development by providing ready-to-use, tested components.
*   **Quality:** Components are thoroughly tested for functionality, accessibility, and responsiveness.
*   **Collaboration:** Fosters better communication between design and development teams.
*   **Maintainability:** Easier to update and scale the UI.

## 3. Brand & Visual Theme (Agoda-Inspired)

Our visual theme is inspired by Agoda.com, aiming for a design that is vibrant, clear, and conversion-focused. The goal is to create a dynamic and value-driven user experience.

### a. Primary Color Palette

*   **Primary (Agoda Blue):** `#007CE8` - The cornerstone of the brand for headers, links, and primary UI elements.
*   **Accent (Vibrant Yellow):** `#FFC107` - For highlighting prices, deals, and primary calls-to-action.
*   **Secondary Accent (Action Pink):** `#E84393` - For secondary actions and promotional badges.
*   **Background (White):** `#FFFFFF` - A clean white background to maximize contrast.
*   **Text (Dark Gray):** `#4A4A4A` - For all text to ensure high readability.
*   **Borders (Light Gray):** `#E0E0E0` - For defining containers and inputs.

### b. Typography

*   **Primary Font:** **Roboto** - Used for both headings and body text to maintain a consistent and functional feel, prized for its readability.
*   **Headings Weight:** Medium (500)
*   **Body Weight:** Regular (400)

### c. UI Style & Feel

*   **Layout:** A **card-based layout** is central to the design, presenting options in a structured and easily comparable format.
*   **Information Density:** The design prioritizes showing relevant information clearly and concisely.
*   **Iconography:** Heavy use of simple, clear icons to supplement text and improve scannability.
*   **Border Radius:** A sharp, modern border-radius of **4px** on cards and buttons.
*   **Shadows & Borders:** The UI will rely on clean, 1px borders and subtle shadows to create a well-defined and scannable interface.

## 4. How to Use the Design System

### a. Component Library
*   Always use components from the official component library (e.g., Storybook, internal package) when building new features or updating existing ones.
*   Avoid creating custom components if an existing one serves the purpose.
*   Familiarize yourself with the available components, their props, and usage guidelines.

### b. Styling
*   Adhere to the defined color palette, typography, spacing, and iconography as specified in the design system.
*   Use utility classes or styled components as per the frontend framework's best practices, but always within the design system's constraints.

### c. Design Tokens
*   Utilize design tokens (e.g., for colors, fonts, spacing) to ensure consistency and easy theming.

## 4. Contributing to the Design System

*   If you identify a need for a new component or an improvement to an existing one, follow the contribution guidelines (to be detailed in a separate document).
*   All new components must be thoroughly tested, documented, and reviewed by both design and development leads.

## 5. Tools
*   **Storybook:** For showcasing and documenting UI components in isolation.
*   **Figma/Sketch:** Design files for the design system.
*   **Version Control:** The design system's code and documentation are version-controlled like any other part of the application.

By consistently applying the Design System, we ensure a cohesive, high-quality, and efficient user interface for our PCW application.