# PKI Infrastructure & Secure Web Server Implementation
**Name:** Aniket Anil Naik

**SJSU ID:** 019107114

**Course:** SJSU CMPE 272 - Enterprise Software Platforms

**Assignment:** HW 7 - Security

## 📖 Project Overview
This repository contains the configuration and command history for building a 3-tier Public Key Infrastructure (PKI) from scratch. The goal was to establish a Chain of Trust and secure a local Apache Tomcat web server with a custom-signed TLS certificate.

### 🏗️ Infrastructure Hierarchy
1.  **Root CA (The Trust Anchor):** Self-signed certificate (`MyRootCA`).
2.  **Signing CA (Intermediate):** Signed by the Root CA (`MySigningCA`).
3.  **End-Entity (Localhost):** Web server certificate signed by the Signing CA.

---

## 📂 Directory Structure
```text
.
├── rootCA/          # Contains the Root CA private key and certificate
├── signingCA/       # Contains the Intermediate CA key, CSR, and certificate
├── server/          # Contains the Server key, CSR, certificate, and PKCS12 keystore
└── README.md        # Project documentation
