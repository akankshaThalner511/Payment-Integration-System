<h1 style="color:#1E90FF; text-align:center;">💳 Payment Integration System</h1>

<p style="text-align:center;">
<b>Developed by Akanksha Thalner</b>  
A modular <b>Spring Boot microservices-based Payment Integration System</b> that enables secure payment validation, processing, and Trustly integration.
</p>

---

<h2 style="color:#32CD32;">🧠 Overview</h2>

<p>
This project is a distributed <b>Payment Integration System</b> built with <b>Spring Boot and Microservices architecture</b>.  
It handles <b>end-to-end payment flow</b> — from validation to processing and integration with the <b>Trustly API</b> for real-time payment authorization.
</p>

---

<h2 style="color:#FF8C00;">🏗️ System Architecture</h2>

<p>
The system is divided into multiple microservices for modularity, scalability, and maintainability:
</p>

📦 Payment-Integration-System/
├── payment-validation-service/
│ ├── HmacSHA256 security filter
│ ├── Dynamic validation framework
│ └── Custom Spring Security configuration
│
├── payment-processing-service/
│ ├── Prepares and forwards payment requests
│ ├── Handles deposit initiation
│ └── Communicates with Trustly Provider
│
├── trustly-provider-service/
│ ├── Handles RSA256 signing & verification
│ ├── Communicates with Trustly Mock service
│ └── Uses BouncyCastle for key management
│
├── trustly-mock-service/
│ ├── Simulates Trustly API endpoints
│ ├── Provides mock payment success/failure responses
│ └── Used for testing integration flow
│
└── eureka-server/
└── Service discovery and registration
