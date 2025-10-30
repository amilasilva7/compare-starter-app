# High-Level Architecture

The application is built on a **cloud-native, microservices-based architecture**. This model was chosen for its scalability, resilience, and flexibility, allowing teams to develop, deploy, and manage services independently.

## Architectural Principles

*   **Microservices:** The application is decomposed into a suite of small, independent services, each focused on a specific business domain.
*   **Backend for Frontend (BFF):** Instead of a single generic API gateway, we use a dedicated backend for each frontend experience (e.g., Web App BFF, Mobile App BFF). This allows us to tailor API responses and data aggregation for each specific client.
*   **Asynchronous Event-Driven Communication:** Services are loosely coupled and communicate asynchronously using a message broker (Apache Kafka) wherever possible. This improves resilience and scalability.
*   **Synchronous Communication:** For direct request/response interactions (e.g., user login), services communicate synchronously via REST APIs.

## Architectural Diagram

```
                               +-------------------------+
                               |   Browser (React App)   |
                               +-------------------------+
                                           |
                                           | (HTTPS)
                                           v
+-----------------------------------------------------------------------------------+
|                                   Web App BFF                                     |
| (Backend for Frontend - Node.js/Express.js)                                       |
| - Aggregates data from core services for the UI                                   |
| - Handles authentication                                                          |
+-----------------------------------------------------------------------------------+
  |        |                  |                   |                  |        |
  | (REST) |                  | (REST)            | (REST)           | (REST) |
  v        v                  v                   v                  v        v
+----------+      +-----------+      +------------+      +-----------+      +---------+
|  Users   |      | Comparison|      |   Quotes   |      | Providers |      | Payments|
| Service  |      |  Service  |      |  Service   |      |  Service  |      | Service |
+----------+      +-----------+      +------------+      +-----------+      +---------+
  |   ^                 |   ^                |   ^               |   ^            |   ^
  |   |                 |   |                |   |               |   |            |   |
  v   | (Publish)       v   | (Publish)      v   | (Publish)     v   | (Publish)  v   | (Publish)
+-----------------------------------------------------------------------------------+
|                                                                                   |
|                               Apache Kafka (Message Broker)                       |
|                                                                                   |
+-----------------------------------------------------------------------------------+
      ^
      | (Subscribe)
      |
+----------------------+
| Notifications Service|
| - Sends emails, SMS  |
+----------------------+

```

## Core Services & Responsibilities

1.  **Web App BFF (Backend for Frontend):**
    *   The single entry point and API provider for the React web application.
    *   Aggregates data from multiple core services to provide a simple, efficient API for the frontend.
    *   Offloads complex orchestration from the client.

2.  **Users Service:**
    *   Manages user registration, authentication, profiles, and personal data.
    *   Publishes events like `UserRegistered` to Kafka.

3.  **Comparison Service:**
    *   The core engine for searching, filtering, and comparing product data.
    *   Consumes updated data from the Providers Service.

4.  **Quotes Service:**
    *   Generates and stores historical quotes for users.
    *   Publishes events like `QuoteGenerated` to Kafka.

5.  **Providers Service:**
    *   Manages all integrations with third-party product providers.
    *   Periodically fetches and normalizes data from external APIs.
    *   Publishes `ProviderDataUpdated` events to Kafka.

6.  **Payments Service:**
    *   Handles all monetization logic, including affiliate tracking and commission calculations.
    *   Integrates with payment gateways using the Adapter pattern.

7.  **Notifications Service:**
    *   A fully decoupled service that listens for events on Kafka (e.g., `UserRegistered`, `QuoteGenerated`).
    *   Responsible for sending all user communications (email, SMS, etc.).
