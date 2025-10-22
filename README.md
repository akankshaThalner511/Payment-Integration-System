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

---

<h2 style="color:#8A2BE2;">🧩 Branches Overview</h2>

| Branch | Description |
|--------|--------------|
| `main` | Stable release of the entire system |
| `payment-validation-service` | Microservice for HMAC-based validation |
| `payment-processing-service-jun25ct` | Core service to process payments |
| `trustly-provider-service-jun25ct` | Handles RSA256 Trustly API integration |
| `trustly-mock-service-jun25ct` | Mock service simulating Trustly responses |
| `db-repo-jun25ct` | Database and repository setup |
| `akankshaThalner511` | Personal development branch |

---

<h2 style="color:#FF1493;">⚙️ Tech Stack</h2>

<ul>
  <li>☕ <b>Java 17</b></li>
  <li>🌱 <b>Spring Boot 3</b> (Web, Security, Data JPA, Validation)</li>
  <li>🧩 <b>Spring Cloud Netflix Eureka</b> – for service discovery</li>
  <li>🔐 <b>RSA256 / HmacSHA256</b> – for cryptographic signing and verification</li>
  <li>💾 <b>MySQL</b> – database layer</li>
  <li>☁️ <b>AWS</b> – deployment (EC2 / S3)</li>
  <li>🧪 <b>JUnit & Mockito</b> – for testing</li>
</ul>

---

<h2 style="color:#FF6347;">💸 Payment Flow</h2>

<p align="center">
  <img src="assets/payment-flow.png" alt="Payment Flow Diagram" width="650" style="border-radius:10px; box-shadow:0 0 10px #999;" />
</p>
<p align="center">
  <img src="assets/payment-flow.png" alt="Payment Flow Diagram" width="650">
</p>


**Step-by-step Workflow:**
1. The client sends a payment request → `Payment Validation Service`  
2. Request is validated (HMAC verification + custom validators)  
3. If valid, forwarded to → `Payment Processing Service`  
4. Processing service calls → `Trustly Provider Service`  
5. Trustly Provider creates an RSA-signed request to → `Trustly Mock Service`  
6. Mock Service returns a simulated success/failure response  
7. Response flows back through provider → processing → client  

---

<h2 style="color:#00BFFF;">🚀 How to Run Locally</h2>

```bash
# Step 1: Clone the repository
git clone https://github.com/akankshaThalner511/Payment-Integration-System.git
cd Payment-Integration-System

# Step 2: Start Eureka Server
cd eureka-server
mvn spring-boot:run

# Step 3: Start Validation Service
cd ../payment-validation-service
mvn spring-boot:run

# Step 4: Start Processing Service
cd ../payment-processing-service
mvn spring-boot:run

# Step 5: Start Trustly Provider & Mock Service
cd ../trustly-provider-service && mvn spring-boot:run
cd ../trustly-mock-service && mvn spring-boot:run
