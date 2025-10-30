# Tech Stack Details

This section outlines the core technologies and frameworks used across the PCW application. The choices are driven by considerations for scalability, performance, developer productivity, and maintainability.

## 1. Frontend
*   **Framework:** React.js (with Next.js for server-side rendering and static site generation)
*   **Language:** TypeScript
*   **Styling:** Tailwind CSS, Styled Components
*   **State Management:** React Query, Zustand/Redux Toolkit
*   **Testing:** Jest, React Testing Library, Cypress (E2E)

## 2. Backend Services
*   **Primary Language:** Python (with FastAPI for REST APIs)
*   **Alternative Language (for specific services):** Go (for high-performance, low-latency services)
*   **Frameworks:** FastAPI, Django (for Admin Panel/CMS if needed)
*   **Testing:** Pytest

## 3. Databases
*   **Relational:** PostgreSQL (for core transactional data, user profiles, product configurations)
*   **NoSQL:** MongoDB (for flexible data storage, e.g., user preferences, analytics events)
*   **Caching:** Redis (for session management, rate limiting, frequently accessed data)

## 4. Cloud Infrastructure
*   **Provider:** AWS (Amazon Web Services) - chosen for its comprehensive suite of services, scalability, and global reach.
*   **Key Services:**
    *   **Compute:** AWS Lambda (serverless functions), Amazon ECS/EKS (container orchestration)
    *   **Networking:** Amazon VPC, AWS Load Balancer, Amazon Route 53
    *   **Storage:** Amazon S3, Amazon RDS (for PostgreSQL), Amazon DocumentDB (for MongoDB compatible)
    *   **Messaging:** Amazon SQS, Amazon SNS, Apache Kafka (managed service like Confluent Cloud or self-hosted on EC2)
    *   **Monitoring & Logging:** Amazon CloudWatch, Prometheus, Grafana, ELK Stack (Elasticsearch, Logstash, Kibana)
    *   **Security:** AWS IAM, AWS WAF, AWS KMS

## 5. CI/CD & DevOps
*   **Version Control:** Git (GitHub)
*   **CI/CD Platform:** GitHub Actions / GitLab CI / AWS CodePipeline
*   **Containerization:** Docker
*   **Infrastructure as Code (IaC):** Terraform

## 6. Other Tools
*   **API Documentation:** OpenAPI/Swagger UI
*   **Message Broker:** Apache Kafka (for event streaming)
*   **Search:** Elasticsearch (for full-text search capabilities)
*   **Monitoring:** Prometheus, Grafana
*   **Logging:** ELK Stack (Elasticsearch, Logstash, Kibana)

This tech stack is subject to evolution based on project needs and emerging best practices. Always refer to the project's `package.json`, `requirements.txt`, or `go.mod` files for the exact versions of libraries and dependencies.