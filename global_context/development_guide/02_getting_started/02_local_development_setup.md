# Local Development Setup

This document outlines the process for setting up and running the UK Price Comparison Website application locally. We leverage **Docker Compose** to ensure a consistent and easy-to-manage local development environment for our microservices architecture.

---

### **1. Running the Full Stack with Docker Compose**

This is the primary method for spinning up all necessary services (database, message broker, backend microservices, BFF, and potentially a containerized frontend build) with a single command.

*   **Prerequisites:** Ensure Docker Desktop (or equivalent Docker engine) is installed and running on your machine.
*   **`docker-compose.yml`:** A central `docker-compose.yml` file in the project root will define all services, their dependencies, environment variables, and port mappings.
*   **Instructions:**
    1.  Navigate to the project root directory in your terminal.
    2.  Run `docker-compose up --build` to build images (if necessary) and start all services.
    3.  For subsequent runs, `docker-compose up` is sufficient.
*   **Services Started:** This command will launch:
    *   MongoDB (our primary database)
    *   Zookeeper (dependency for Kafka)
    *   Kafka (our asynchronous message broker)
    *   All individual backend microservices (e.g., `quote-service`, `user-service`)
    *   The Backend-for-Frontend (BFF)
    *   (Optional) A containerized build of the React frontend.
*   **Access:** Services will be accessible via `localhost` on their defined ports (e.g., `http://localhost:3000` for the frontend, `http://localhost:8080` for the BFF).

### **2. Running Individual Services for Faster Iteration (Hot-Reloading)**

For rapid development and hot-reloading, developers will often run the specific service they are actively working on outside of Docker, while other dependencies continue to run via Docker Compose.

*   **General Steps:**
    1.  Start the full stack with `docker-compose up` (excluding the specific service you intend to run locally, if it's defined in `docker-compose.yml`).
    2.  Navigate to the individual service's directory (e.g., `cd services/frontend-web` or `cd services/quote-service`).
    3.  Run `npm install` to ensure all dependencies are up-to-date.
    4.  Execute the service's local development command.

*   **Frontend (React App):**
    *   From the frontend application directory (`services/frontend-web`):
    *   Run `npm start`.
    *   This will typically launch the React app with hot-reloading, connecting to the backend services running in Docker.

*   **Backend Microservice (Node.js/Express):**
    *   From the microservice's directory (e.g., `services/quote-service`):
    *   Run `npm run dev` (assuming a `nodemon` or similar setup for hot-reloading).
    *   This service will connect to MongoDB and Kafka instances running in Docker.

### **3. Local Development Testing**

*   **Unit & Integration Tests:**
    *   Navigate to the specific service directory.
    *   Run `npm test` (for Node.js/React services) or `pytest` (for Python services, if any).
*   **End-to-End (E2E) Tests:**
    *   While E2E tests are typically run against a deployed staging environment, they can be executed locally against the full Docker Compose setup if needed.
    *   Configure the E2E test runner (e.g., Cypress) to point to the local `localhost` URLs of the running services.
