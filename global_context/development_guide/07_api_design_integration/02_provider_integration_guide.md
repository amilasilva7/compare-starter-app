# Provider Integration Guide

This guide outlines the architectural best practices for integrating with third-party services. The primary goal is to ensure that these integrations are loosely coupled, allowing the application to switch between providers with minimal code changes.

## The Adapter and Factory Strategy

To avoid tightly coupling the application to a specific third-party SDK (e.g., Stripe, SendGrid), we will use a combination of the **Adapter Pattern** and the **Factory Pattern**. This approach ensures that our business logic is completely decoupled from the specific implementation details of any external service.

### Core Principles

1.  **Define a Generic Internal Interface:** For each *type* of service (e.g., Payment Gateway, Email Service, SMS Gateway), we must define a generic interface within our application. This interface dictates the methods our application will use, without any knowledge of the external provider.

2.  **Create Concrete Adapters:** For each third-party provider we support, we will create a concrete "Adapter" class that implements our internal interface. The adapter's sole responsibility is to translate the calls from our generic interface into the specific API calls required by the third-party SDK.

3.  **Use a Factory for Instantiation:** A Factory class will be responsible for creating and returning the correct adapter based on a configuration setting, typically an environment variable (e.g., `PAYMENT_PROVIDER=stripe`). The application will always request the service from the factory, never instantiating an adapter directly.

### Example: Payment Gateway Integration

Let's illustrate with a payment gateway.

#### 1. Define the Generic Interface

First, we define an interface that represents the concept of a payment provider in our application.

```typescript
// src/core/payments/IPaymentProvider.ts

export interface ChargeResponse {
  success: boolean;
  chargeId: string;
}

export interface RefundResponse {
  success: boolean;
  refundId: string;
}

// Our application's generic payment provider interface
export interface IPaymentProvider {
  createCharge(amount: number, currency: string, token: string): Promise<ChargeResponse>;
  createRefund(chargeId: string): Promise<RefundResponse>;
}
```

#### 2. Create Concrete Adapters

Next, we create adapters for Stripe and PayPal.

**Stripe Adapter:**
```typescript
// src/services/payments/StripeAdapter.ts
import { Stripe } from 'stripe';
import { IPaymentProvider, ChargeResponse, RefundResponse } from '''../../core/payments/IPaymentProvider''';

export class StripeAdapter implements IPaymentProvider {
  private stripe = new Stripe(process.env.STRIPE_API_KEY);

  async createCharge(amount: number, currency: string, token: string): Promise<ChargeResponse> {
    const charge = await this.stripe.charges.create({
      amount: amount * 100, // Stripe uses cents
      currency,
      source: token,
    });
    return { success: true, chargeId: charge.id };
  }

  async createRefund(chargeId: string): Promise<RefundResponse> {
    const refund = await this.stripe.refunds.create({ charge: chargeId });
    return { success: true, refundId: refund.id };
  }
}
```

**PayPal Adapter (Conceptual):**
```typescript
// src/services/payments/PayPalAdapter.ts
import { IPaymentProvider, ChargeResponse, RefundResponse } from '''../../core/payments/IPaymentProvider''';
import { PayPalApi } from '''./paypal-sdk'''; // A hypothetical PayPal SDK wrapper

export class PayPalAdapter implements IPaymentProvider {
  private payPalApi = new PayPalApi(process.env.PAYPAL_CLIENT_ID, process.env.PAYPAL_CLIENT_SECRET);

  async createCharge(amount: number, currency: string, token: string): Promise<ChargeResponse> {
    const order = await this.payPalApi.createOrder({ amount, currency, token });
    return { success: true, chargeId: order.id };
  }

  async createRefund(chargeId: string): Promise<RefundResponse> {
    const refund = await this.payPalApi.refundOrder(chargeId);
    return { success: true, refundId: refund.id };
  }
}
```

#### 3. Use a Factory

The factory provides the correct adapter based on configuration.

```typescript
// src/core/payments/PaymentFactory.ts
import { IPaymentProvider } from '''./IPaymentProvider''';
import { StripeAdapter } from '''../../services/payments/StripeAdapter''';
import { PayPalAdapter } from '''../../services/payments/PayPalAdapter''';

export class PaymentFactory {
  public static getProvider(): IPaymentProvider {
    const provider = process.env.PAYMENT_PROVIDER;

    switch (provider) {
      case 'stripe':
        return new StripeAdapter();
      case 'paypal':
        return new PayPalAdapter();
      default:
        throw new Error(`Unsupported payment provider: ${provider}`);
    }
  }
}
```

### Conclusion

By following this pattern for all third-party integrations, the application remains agile and is not locked into any single vendor. To switch providers, one only needs to change an environment variable and ensure the corresponding adapter is implemented.

---

## **Managing Third-Party URLs & Environment-Specific Configuration**

It is crucial to differentiate between **Master Data** (business information about a provider) and **Environment-Specific Configuration** (technical details for connecting to a provider).

### **1. Master Data vs. Environment-Specific Configuration**

*   **Master Data:** This includes the provider's name, logo URL (for static assets), and unique ID. This data is generally consistent across environments and is stored in our database, managed by the Reference Data Service.
*   **Environment-Specific Configuration:** This includes the provider's API base URL (e.g., `https://api.aviva.com/prod/v1`, `https://api.aviva.com/staging/v1`, or `http://localhost:8081/mock-aviva`) and sensitive credentials like API keys/secrets. These details **must not** be stored in the database.

### **2. Management Strategy for Configuration**

We will manage environment-specific configurations using a combination of environment variables and application profiles.

*   **Environment Variables (Primary Mechanism):**
    *   **Local Development:** Developers will use `.env` files (which are `.gitignore`d) to define these URLs and secrets. For example:
        ```
        AVIVA_API_BASE_URL=http://localhost:8081/mock-aviva
        STRIPE_API_KEY=sk_test_...
        ```
        This allows local development to use mock servers or local test endpoints.
    *   **Deployed Environments (Staging, Production):** The CI/CD system will inject these values as environment variables into the running application containers (Kubernetes pods). Sensitive values will be stored securely in:
        *   CI/CD System Secrets (e.g., GitHub Secrets).
        *   Dedicated Secrets Manager (e.g., HashiCorp Vault, AWS Secrets Manager, Google Secret Manager).

*   **Application Profiles (Complementary Layer):**
    *   We will use environment variables like `NODE_ENV` (`development`, `production`, `test`) and potentially a custom `APP_ENV` (`local`, `dev`, `staging`, `production`) to define the active application profile.
    *   **Purpose:** Profiles allow our application code to load different sets of configurations or apply environment-specific behaviors (e.g., different logging levels, feature flags) based on the active profile.
    *   **Integration:** Our provider adapters will read their base URLs and API keys from the environment variables that are active for the given profile.

### **3. Impact on Adapter Pattern**

*   Each provider adapter (e.g., `StripeAdapter`, `AvivaAdapter`) will be configured to read its base URL and API key from the environment variables available to the microservice it runs within.
*   This ensures that the core business logic remains decoupled from environment-specific connection details, maintaining the flexibility provided by the Adapter Pattern.
