# API Design Principles

This document outlines the core principles for designing and implementing APIs within our PCW application. Adhering to these principles ensures consistency, usability, and maintainability across all services.

## 1. API Contract First Development with OpenAPI (Swagger)

We adopt an **API Contract First** approach, where the API specification is defined using **OpenAPI (formerly Swagger)** *before* any code is written. This specification serves as the single source of truth for all API interactions.

### Benefits:
*   **Clear Communication:** Provides a precise and unambiguous contract between API producers and consumers (frontend, other microservices, external partners).
*   **Parallel Development:** Frontend and backend teams can work in parallel, mocking API responses based on the agreed-upon contract.
*   **Automated Documentation:** Generates interactive API documentation (Swagger UI) automatically.
*   **Code Generation:** Enables automatic generation of client SDKs and server stubs.
*   **Early Validation:** Allows for early validation of API design against business requirements.

### Best Practices for OpenAPI Definitions:
*   **Granularity:** Define each endpoint, its parameters, request/response bodies, and error responses in detail.
*   **Reusability:** Use OpenAPI's schema definitions (`#/components/schemas`) for common data structures to promote consistency.
*   **Validation:** Integrate OpenAPI specification validation into the CI/CD pipeline (e.g., using Spectral) to ensure adherence to standards.

## 2. RESTful Principles

Our APIs will primarily follow REST (Representational State Transfer) architectural style.

*   **Resource-Based:** APIs should expose resources (e.g., `/users`, `/products`, `/quotes`) that can be manipulated using standard HTTP methods.
*   **Stateless:** Each request from a client to a server must contain all the information needed to understand the request. The server should not store any client context between requests.
*   **Client-Server:** Clear separation of concerns between the client and server.
*   **Cacheable:** Responses should explicitly define themselves as cacheable or not to improve performance.
*   **Layered System:** Clients should not be able to tell whether they are connected directly to the end server or to an intermediary.

## 3. HTTP Methods

Use standard HTTP methods for their intended actions, clearly defined in the OpenAPI spec:
*   `GET`: Retrieve a resource or a collection of resources (should be idempotent and safe).
*   `POST`: Create a new resource.
*   `PUT`: Update an existing resource (replace the entire resource).
*   `PATCH`: Partially update an existing resource.
*   `DELETE`: Remove a resource.

## 4. Naming Conventions

Consistent naming is crucial for API usability and maintainability, and will be enforced via OpenAPI definitions:
*   **Resources:** Use plural nouns for resource names (e.g., `/users`, `/products`).
*   **URLs:** Use lowercase and hyphens (`-`) for readability (e.g., `/user-profiles`). Avoid underscores (`_`).
*   **Actions:** For non-CRUD actions, consider nesting (e.g., `/products/{id}/activate`) or using custom methods if truly necessary.
*   **Parameters:** Use `camelCase` for query parameters and `snake_case` for path parameters in the OpenAPI definition.

## 5. Request & Response Formats

*   **JSON:** Use JSON (JavaScript Object Notation) as the primary format for request and response bodies.
*   **Content-Type Header:** Always set the `Content-Type` header for requests with a body (e.g., `application/json`).
*   **Consistent Structure:** Maintain a consistent structure for responses, including success and error messages, defined by OpenAPI schemas.

## 6. Versioning

API versioning is crucial for managing changes without breaking existing clients. We will use **URL-based versioning**, clearly defined in the OpenAPI spec for each version.
*   **Example:** `/v1/users`, `/v2/products`
*   **Deprecation Strategy:** Clearly communicate API deprecation schedules and provide ample time for clients to migrate to newer versions. OpenAPI definitions for deprecated versions will be maintained for a defined period.

## 7. Error Handling

Provide clear, consistent, and informative error responses, fully documented in the OpenAPI spec.
*   **HTTP Status Codes:** Use appropriate HTTP status codes to indicate the type of error (e.g., `400 Bad Request`, `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, `500 Internal Server Error`).
*   **Error Body:** Include a JSON error body with:
    *   `code`: A unique application-specific error code.
    *   `message`: A human-readable error message.
    *   `details`: (Optional) More specific information about the error (e.g., validation errors).

## 8. Authentication & Authorization

*   All APIs must be secured using appropriate authentication and authorization mechanisms (see [Authentication & Authorization Implementation](../../05_security_best_practices/03_auth_auth_implementation.md)).
*   OpenAPI definitions will specify the security schemes (e.g., OAuth2, Bearer Token) required for each endpoint.

## 9. Rate Limiting

Implement rate limiting on all public and critical API endpoints to prevent abuse and ensure fair usage (see [API Security](../../05_security_best_practices/05_api_security.md)). OpenAPI definitions can include rate limit headers in responses.

By following these principles and leveraging OpenAPI as our central contract definition tool, we aim to build robust, intuitive, and secure APIs that are easy to integrate with and maintain.
