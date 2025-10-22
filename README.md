💳 Payment Integration System

A complete Spring Boot Microservices-based Payment Integration System that securely handles the entire payment flow — from validation and processing to provider communication — using RSA256, HMAC-SHA256, and RESTful communication between services.

🧩 System Architecture Overview

This project is composed of five microservices, each handling a specific part of the payment workflow.

Payment-Integration-System
│
├── db-repo-jun25ct                  # Centralized in-memory DB module (H2 / Redis repo)
│
├── payment-validation-service        # Validates incoming payment requests (HMAC, schema)
│
├── payment-processing-service-jun25ct# Processes validated payments, prepares Trustly requests
│
├── trustly-provider-service-jun25ct  # Handles signing & verification (RSA256) and communication
│
├── trustly-mock-service-jun25ct      # Mock Trustly API for testing success/failure responses
│
└── README.md

⚙️ Microservice Responsibilities
🛡️ Payment Validation Service

Performs request validation using a modular validator framework.

Uses HmacSHA256 filter to ensure message integrity.

Implements Spring Security for request filtering and authentication.

Exposes the /payments endpoint for receiving payment requests.

Dynamically executes validators based on ValidatorEnum.

⚙️ Payment Processing Service

Receives validated requests from the Validation Service.

Prepares deposit/payment initiation payloads.

Calls Trustly Provider Service for digital signing.

Forwards the signed request to the Trustly Mock Service.

Handles response mapping and error codes.

🔐 Trustly Provider Service

Implements RSA256-based signing and verification using the BouncyCastle provider.

Loads private and public keys from PEM files.

Handles secure communication with the Trustly Mock Service.

Validates Trustly responses before forwarding them to the Processing Service.

🧪 Trustly Mock Service

Acts as a simulated Trustly Payment Gateway.

Provides endpoints like:

/trustly/initiate

/trustly/success

/trustly/failure

Used for end-to-end testing of request/response flow.

🗃️ DB Repo

Shared module containing repository configurations.

Provides access to in-memory data stores or persistent DB for local testing.

Used by multiple microservices via dependencies.

🔄 Payment Flow Diagram
sequenceDiagram
    participant Client
    participant ValidationService
    participant ProcessingService
    participant ProviderService
    participant MockTrustly

    Client->>ValidationService: POST /payments (HMAC Secured)
    ValidationService-->>Client: 200 OK (Validated)
    ValidationService->>ProcessingService: Forward Validated Request
    ProcessingService->>ProviderService: Request Digital Signature (RSA256)
    ProviderService-->>ProcessingService: Signed Payload
    ProcessingService->>MockTrustly: POST /trustly/initiate (Signed)
    MockTrustly-->>ProcessingService: Response (Success/Failure)
    ProcessingService-->>Client: Final Payment Response

🧰 Tech Stack
Category	Tools / Technologies
Language	Java 17
Framework	Spring Boot
Architecture	Microservices
Security	HmacSHA256, RSA256 (BouncyCastle)
Communication	REST APIs (Spring Web, Eureka Discovery)
Database	H2 / Redis (for caching)
Build Tool	Maven
Testing	JUnit, Mockito
Deployment	AWS EC2, Docker-ready
🚀 How to Run Locally
1️⃣ Clone the Repository
git clone https://github.com/akankshaThalner511/Payment-Integration-System.git
cd Payment-Integration-System

2️⃣ Start Each Microservice

Run each service from its root directory:

mvn spring-boot:run


Order:

db-repo-jun25ct

payment-validation-service

payment-processing-service-jun25ct

trustly-provider-service-jun25ct

trustly-mock-service-jun25ct

3️⃣ Test the Flow

Use Postman or curl:

POST http://localhost:8081/payments
Headers:
  X-SIGNATURE: <hmac_signature>
Body:
{
  "amount": 1000,
  "currency": "USD",
  "userId": "U12345"
}

🧾 Features Summary

✅ Modular Validation Framework
✅ Secure HmacSHA256 Request Filter
✅ RSA256 Digital Signature Implementation
✅ Mock Gateway for Realistic Testing
✅ Clear Microservice Segregation
✅ Error Handling via Custom Enums
✅ Spring Security Integration

📜 Example Output

Client → /payments
✔️ Returns success or failure response with unique transaction ID and message.
✔️ All logs traceable in microservice consoles for debugging.

👩‍💻 Author

Akanksha Thalner
Java & Spring Boot Developer
GitHub Profile
