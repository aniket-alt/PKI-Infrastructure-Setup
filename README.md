\# PKI Infrastructure Setup

SJSU CMPE 272 - HW 7



\## Project Overview

Designed and built a 3-tier PKI infrastructure including:

1\. Root CA (Self-Signed)

2\. Signing CA (Intermediate)

3\. End-Entity Certificate (Localhost)



\## Commands Used



\### 1. Root CA Setup

openssl genrsa -aes256 -out rootCA/rootCA.key 4096

openssl req -x509 -new -nodes -key rootCA/rootCA.key -sha256 -days 3650 -out rootCA/rootCA.pem



\### 2. Signing CA Setup

openssl genrsa -out signingCA/signingCA.key 4096

openssl req -new -key signingCA/signingCA.key -out signingCA/signingCA.csr

openssl x509 -req -in signingCA/signingCA.csr -CA rootCA/rootCA.pem -CAkey rootCA/rootCA.key -CAcreateserial -out signingCA/signingCA.crt -days 500 -sha256



\### 3. Server Certificate \& Tomcat

openssl genrsa -out server/server.key 2048

openssl req -new -key server/server.key -out server/server.csr

openssl x509 -req -in server/server.csr -CA signingCA/signingCA.crt -CAkey signingCA/signingCA.key -CAcreateserial -out server/server.crt -days 365 -sha256



\### 4. Keystore Generation

openssl pkcs12 -export -in server/server.crt -inkey server/server.key -certfile signingCA/signingCA.crt -out server/keystore.p12 -name tomcat

