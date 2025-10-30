# Data Flow Overview

Understanding how data moves through the system is crucial for developing and troubleshooting the PCW application. This section provides a simplified overview of key data flows.

## 1. User Comparison & Quote Generation

```mermaid
sequenceDiagram
    actor User
    participant Frontend
    participant API_Gateway
    participant Comparison_Service
    participant Provider_Integration_Service
    participant External_Provider_APIs
    participant Product_DB

    User->>Frontend: Enters comparison details
    Frontend->>API_Gateway: Request /compare (details)
    API_Gateway->>Comparison_Service: Forward request
    Comparison_Service->>Provider_Integration_Service: Request quotes (details)
    Provider_Integration_Service->>External_Provider_APIs: Fetch quotes from multiple providers
    External_Provider_APIs-->>Provider_Integration_Service: Return raw quotes
    Provider_Integration_Service->>Product_DB: Store/Cache raw quotes
    Provider_Integration_Service-->>Comparison_Service: Return processed quotes
    Comparison_Service->>Frontend: Return sorted/filtered results
    Frontend->>User: Display comparison results
```

## 2. User Account & Profile Management

```mermaid
sequenceDiagram
    actor User
    participant Frontend
    participant API_Gateway
    participant Auth_Service
    participant User_Profile_Service
    participant User_DB

    User->>Frontend: Registers/Logs in
    Frontend->>API_Gateway: Request /register or /login
    API_Gateway->>Auth_Service: Authenticate/Authorize
    Auth_Service->>User_DB: Verify credentials/Store new user
    User_DB-->>Auth_Service: User data
    Auth_Service-->>API_Gateway: Token/Success
    API_Gateway-->>Frontend: Token/Success

    User->>Frontend: Updates profile
    Frontend->>API_Gateway: Request /profile/update (data)
    API_Gateway->>User_Profile_Service: Forward request (with token)
    User_Profile_Service->>User_DB: Update user data
    User_DB-->>User_Profile_Service: Success
    User_Profile_Service-->>Frontend: Success
```

## 3. Event-Driven Analytics

```mermaid
sequenceDiagram
    participant Service_A
    participant Service_B
    participant Message_Broker
    participant Analytics_Service
    participant Data_Warehouse

    Service_A->>Message_Broker: Publish Event (e.g., "QuoteGenerated")
    Service_B->>Message_Broker: Publish Event (e.g., "PolicyPurchased")
    Message_Broker->>Analytics_Service: Deliver Events
    Analytics_Service->>Data_Warehouse: Process & Store Event Data
    Data_Warehouse->>BI_Tools: Data for Reporting
```

These diagrams provide a simplified view. For detailed data models and API specifications, refer to the respective service documentation.