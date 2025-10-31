# Design System Guidelines

Our Design System is a collection of reusable components and clear standards that guide the creation of a **premium, sophisticated, and seamless user experience**. It is the single source of truth for ensuring our application meets the high expectations of our target audience.

## 1. Design Philosophy: The Premium Experience

Our design philosophy is centered on three core principles to deliver an experience that feels like a premium concierge service:

*   **Effortless Efficiency:** The user's time is paramount. The interface must be intuitive, fast, and proactive. We achieve this through intelligent defaults, proactive personalization, and by presenting information in the clearest, most scannable way possible.
*   **Understated Elegance:** A premium aesthetic is clean, confident, and uncluttered. We prioritize generous white space, high-quality typography, and a calm, focused layout. Every element on the screen must serve a purpose and contribute to a sense of refined quality.
*   **Assured Trust & Discretion:** We build trust through professionalism and transparency. The design must feel secure, private, and respectful. This is achieved through a polished look, flawless copy, and discreet cues about data security, rather than loud, overt trust badges.

## 2. Brand & Visual Theme (Refined Agoda-Inspired)

Our visual theme is inspired by Agoda.com but refined for a more sophisticated, high-end audience. The goal is a design that is clear, value-driven, and feels premium.

### a. Refined Color Palette

The palette is clean and high-contrast, using color strategically to guide the user while ensuring optimal readability and accessibility. All color combinations for text and interactive elements must meet **WCAG 2.1 Level AA contrast requirements** (minimum 4.5:1 for normal text, 3:1 for large text and graphical objects).

*   **Primary (Agoda Blue):** `#007CE8` - The cornerstone of the brand, used for key headers and primary interactive elements.
*   **Spotlight Accent (Vibrant Yellow):** `#FFC107` - Used **sparingly** to highlight the most critical actions (e.g., a final "Buy Now" button) or key savings, making its appearance more impactful.
*   **Canvas:** The majority of the interface will be a calm palette of **White (`#FFFFFF`)**, **Light Gray (`#E0E0E0` for borders)**, and **Dark Gray (`#4A4A4A` for text)**. This creates a clean, sophisticated canvas and maximizes readability.

#### Semantic Color Palette for UI Components

To ensure consistency, beauty, and ease on the eye, we use a semantic approach to color application across UI components and states:

*   **Primary Action:** Buttons and links for primary actions will use **Primary Blue (`#007CE8`)** with **White (`#FFFFFF`)** text.
*   **Secondary Action:** Secondary buttons will use **Dark Gray (`#4A4A4A`)** borders with **Dark Gray (`#4A4A4A`)** text on a **White (`#FFFFFF`)** background.
*   **Success:** For positive feedback or successful operations, we use a subtle **Green (`#4CAF50`)** with **White (`#FFFFFF`)** text.
*   **Warning:** For cautionary messages, a soft **Orange (`#FF9800`)** with **Dark Gray (`#4A4A4A`)** text.
*   **Error:** For critical errors or negative feedback, a clear **Red (`#F44336`)** with **White (`#FFFFFF`)** text.
*   **Information:** For general informational messages, a light **Blue (`#2196F3`)** with **White (`#FFFFFF`)** text.
*   **Text:** All body text will be **Dark Gray (`#4A4A4A`)** on a **White (`#FFFFFF`)** or very light background to ensure high contrast and readability.
*   **Borders & Dividers:** Subtle **Light Gray (`#E0E0E0`)** for defining containers and separating content, providing visual structure without distraction.
*   **Hover/Active States:** Interactive elements will have subtle, accessible hover and active states, typically a slight darkening or lightening of the background color, or a change in border/text color, ensuring contrast is maintained.

### b. Elevated Typography

Typography is a key element of our premium feel.

*   **Font Pairing:** We use a sophisticated font pairing to create a clear and elegant visual hierarchy.
    *   **Headings:** **Lora** (a clean, modern serif) or **Lato** (a sophisticated sans-serif).
    *   **Body Text:** **Roboto** - for its excellent readability in UI contexts.
*   **Weights:** Headings will use a Medium (500) weight, while body text will be Regular (400).

### c. UI Style & Feel

*   **Layout:** A **card-based layout** remains central, but with generous spacing and clean lines to avoid a cluttered feel.
*   **White Space:** We will use ample white space to give content room to breathe, creating a sense of calm and focus.
*   **Data Visualization:** Complex data will be presented in clean, elegant charts and visualizations, not just tables, to make comparisons instantly clear.
*   **Iconography:** We will use a **custom-designed set of icons** that are elegant, precise, and unique to our brand.
*   **Imagery:** All imagery must be high-quality, professional photography or custom illustrations. No generic stock photos.

## 3. Micro-interactions & Delightful Details

Subtle animations and thoughtful details are crucial for a premium experience.

*   **Feedback:** Interactive elements will have subtle, graceful hover and click effects. This makes the interface feel responsive and alive.
*   **Loading States:** We will use **skeleton screens** (faint outlines of the content being loaded) instead of generic spinners. This manages user expectations and makes the application feel faster.
*   **Transitions:** Page and state transitions will be smooth, fast, and subtle (e.g., a quick fade or slide), creating a seamless flow.

## 4. How to Use the Design System

*   **Component-First:** Always use components from the official library.
*   **Adherence to Philosophy:** Every new design or feature must be evaluated against our core design philosophy.
*   **Contribution:** New components or patterns must be reviewed by design and development leads to ensure they meet our high standards for quality, accessibility, and elegance.

## 5. Tools

*   **Storybook:** For showcasing and documenting UI components.
*   **Figma/Sketch:** For the master design files.
*   **Version Control:** The design system is version-controlled.

By consistently applying these refined guidelines, we will create a cohesive, high-quality, and truly premium user interface.
