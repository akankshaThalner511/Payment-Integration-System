<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Payment Integration System - Akanksha Thalner</title>

  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- Icons -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/lucide-static@latest/font/lucide.css">
  
  <style>
    body {
      background-color: #f9fafb;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    .hero {
      background: linear-gradient(135deg, #2563eb, #1e40af);
      color: white;
      padding: 3rem 1rem;
      text-align: center;
      border-bottom-left-radius: 2rem;
      border-bottom-right-radius: 2rem;
    }
    .section-title {
      color: #2563eb;
      font-weight: 700;
      font-size: 1.5rem;
      margin-bottom: 1rem;
      border-left: 6px solid #2563eb;
      padding-left: 10px;
    }
    .card {
      background-color: white;
      border-radius: 1rem;
      padding: 1.5rem;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      transition: transform 0.2s ease;
    }
    .card:hover {
      transform: translateY(-5px);
    }
    code {
      background-color: #f3f4f6;
      padding: 2px 5px;
      border-radius: 5px;
      color: #1f2937;
    }
  </style>
</head>

<body>

  <!-- HERO SECTION -->
  <section class="hero">
    <h1 class="text-4xl font-bold mb-2">💳 Payment Integration System</h1>
    <p class="text-lg">A Secure, Scalable, and Modular Payment Gateway built using Spring Boot Microservices</p>
    <p class="mt-4">
      <span class="bg-white text-blue-700 px-3 py-1 rounded-lg text-sm font-semibold">Java 17</span>
      <span class="bg-white text-green-700 px-3 py-1 rounded-lg text-sm font-semibold">Spring Boot</span>
      <span class="bg-white text-yellow-700 px-3 py-1 rounded-lg text-sm font-semibold">Microservices</span>
    </p>
  </section>

  <main class="p-6 max-w-6xl mx-auto space-y-10">

    <!-- OVERVIEW -->
    <section>
      <h2 class="section-title">🧠 Overview</h2>
      <div class="card">
        <p>
          The <b>Payment Integration System</b> is a microservices-based Java application designed for secure and modular payment handling. 
          It covers the complete flow — validation, processing, digital signing, and mock provider simulation — using <b>Spring Boot</b> and advanced cryptographic algorithms such as <b>RSA256</b> and <b>HMAC-SHA256</b>.
        </p>
      </div>
    </section>

    <!-- ARCHITECTURE -->
    <section>
      <h2 class="section-title">🏗️ System Architecture</h2>
      <div class="card">
        <pre><code>
Payment-Integration-System
│
├── db-repo-jun25ct
├── payment-validation-service
├── payment-processing-service-jun25ct
├── trustly-provider-service-jun25ct
├── trustly-mock-service-jun25ct
└── README.md
        </code></pre>
        <p class="mt-3">Each service runs independently and communicates through REST APIs for scalability and modularity.</p>
      </div>
    </section>

    <!-- DIAGRAM -->
    <section>
      <h2 class="section-title">📊 Architecture Diagram</h2>
      <div class="card text-center">
        <img src="assets/architecture.png" alt="Architecture Diagram" class="rounded-lg mx-auto shadow-lg">
        <p class="text-gray-600 mt-2">Overall structure showing service-to-service interaction.</p>
      </div>
    </section>

    <!-- TECH STACK -->
    <section>
      <h2 class="section-title">🧰 Tech Stack</h2>
      <div class="grid md:grid-cols-2 gap-4">
        <div class="card">
          <ul class="list-disc pl-5 space-y-1">
            <li><b>Language:</b> Java 17</li>
            <li><b>Framework:</b> Spring Boot (Microservices)</li>
            <li><b>Security:</b> HMAC-SHA256, RSA256 (BouncyCastle)</li>
            <li><b>Database:</b> H2 / Redis</li>
          </ul>
        </div>
        <div class="card">
          <ul class="list-disc pl-5 space-y-1">
            <li><b>Communication:</b> REST APIs (Spring Cloud Eureka)</li>
            <li><b>Build Tool:</b> Maven</li>
            <li><b>Testing:</b> JUnit, Mockito</li>
            <li><b>Deployment:</b> Docker, AWS EC2</li>
          </ul>
        </div>
      </div>
    </section>

    <!-- SERVICES -->
    <section>
      <h2 class="section-title">🛡️ Microservices Overview</h2>
      <div class="grid md:grid-cols-2 gap-4">

        <div class="card">
          <h3 class="text-blue-700 font-semibold mb-2">1️⃣ Payment Validation Service</h3>
          <ul class="list-disc pl-5 space-y-1">
            <li>Validates incoming payment requests.</li>
            <li>Implements HMAC-SHA256 verification.</li>
            <li>Applies Spring Security filters for authentication.</li>
            <li>Exposes <code>/payments</code> endpoint.</li>
          </ul>
        </div>

        <div class="card">
          <h3 class="text-blue-700 font-semibold mb-2">2️⃣ Payment Processing Service</h3>
          <ul class="list-disc pl-5 space-y-1">
            <li>Receives validated requests.</li>
            <li>Prepares provider payloads and forwards them.</li>
            <li>Requests RSA signing from Provider Service.</li>
            <li>Manages transaction flow and responses.</li>
          </ul>
        </div>

        <div class="card">
          <h3 class="text-blue-700 font-semibold mb-2">3️⃣ Trustly Provider Service</h3>
          <ul class="list-disc pl-5 space-y-1">
            <li>Handles RSA256 signing & verification (BouncyCastle).</li>
            <li>Uses PEM-based private/public keys.</li>
            <li>Ensures secure provider communication.</li>
          </ul>
        </div>

        <div class="card">
          <h3 class="text-blue-700 font-semibold mb-2">4️⃣ Trustly Mock Service</h3>
          <ul class="list-disc pl-5 space-y-1">
            <li>Simulates Trustly Payment Gateway.</li>
            <li>Endpoints: <code>/trustly/initiate</code>, <code>/trustly/success</code>, <code>/trustly/failure</code>.</li>
            <li>Used for end-to-end testing.</li>
          </ul>
        </div>
      </div>
    </section>

    <!-- RUN -->
    <section>
      <h2 class="section-title">🚀 How to Run</h2>
      <div class="card">
        <p class="font-semibold">Step 1: Clone Repository</p>
        <pre><code>git clone https://github.com/akankshaThalner511/Payment-Integration-System.git
cd Payment-Integration-System</code></pre>

        <p class="font-semibold mt-4">Step 2: Run Services (Order)</p>
        <ol class="list-decimal pl-6">
          <li>db-repo-jun25ct</li>
          <li>payment-validation-service</li>
          <li>payment-processing-service-jun25ct</li>
          <li>trustly-provider-service-jun25ct</li>
          <li>trustly-mock-service-jun25ct</li>
        </ol>

        <p class="font-semibold mt-4">Step 3: Test API (Postman / Curl)</p>
        <pre><code>POST http://localhost:8081/payments
Headers:
  X-SIGNATURE: &lt;hmac_signature&gt;
Body:
{
  "amount": 1000,
  "currency": "USD",
  "userId": "U12345"
}</code></pre>
      </div>
    </section>

    <!-- AUTHOR -->
    <section>
      <h2 class="section-title">👩‍💻 Author</h2>
      <div class="card text-center">
        <h3 class="font-semibold text-lg">Developed by Akanksha Thalner</h3>
        <p>Java & Spring Boot Developer</p>
        <a href="https://github.com/akankshaThalner511" class="text-blue-700 underline">GitHub Profile</a>
      </div>
    </section>

  </main>

  <footer class="text-center py-6 text-gray-500 text-sm">
    ✨ A Secure, Modular & Future-Ready Payment Platform built with Passion and Precision. ✨
  </footer>

</body>
</html>
