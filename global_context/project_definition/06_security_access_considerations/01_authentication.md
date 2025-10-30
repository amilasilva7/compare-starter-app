### Authentication (Verifying Identity)

1.  **Strong Password Policies:** Enforce minimum length, complexity, prevent reuse, use strong hashing (e.g., bcrypt, Argon2) with salt.
2.  **Multi-Factor Authentication (MFA):** Mandatory for Admin/Provider/Affiliate/Data Analyst; optional/recommended for Customers.
3.  **Account Lockout Mechanisms:** Temporarily lock accounts after multiple failed login attempts.
4.  **"Forgot Password" / Account Recovery:** Secure processes verifying identity without exposing sensitive information.
5.  **Single Sign-On (SSO):** For internal staff and potentially providers, integrate with a secure SSO solution.