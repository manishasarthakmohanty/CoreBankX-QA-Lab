# CoreBankX QA Lab — System Architecture

## 1. Architecture Overview

CoreBankX QA Lab will simulate a modern digital banking platform consisting of:

- Internet Banking (INB)
- Mobile Banking (MOB)
- Backend APIs
- PostgreSQL Database
- Authentication
- Transaction Processing
- Notification Services
- QA Automation Frameworks
- CI/CD Pipeline
- Reporting and Analytics
- AI-assisted QA components

The architecture will be developed progressively throughout the project.

---

## 2. High-Level Architecture

```text
                                             ┌──────────────────────────┐
                         │        END USERS         │
                         └────────────┬─────────────┘
                                      │
                         ┌────────────▼─────────────┐
                         │     DIGITAL BANKING      │
                         │                          │
                         │  Internet Banking (INB) │
                         │  Mobile Banking (MOB)    │
                         └────────────┬─────────────┘
                                      │
                                      ▼
                         ┌──────────────────────────┐
                         │   API GATEWAY / SECURITY  │
                         │                          │
                         │ Authentication           │
                         │ Authorization            │
                         │ Session / JWT            │
                         │ Request Validation       │
                         └────────────┬─────────────┘
                                      │
             ┌────────────────────────┼────────────────────────┐
             │                        │                        │
             ▼                        ▼                        ▼
   ┌──────────────────┐    ┌──────────────────┐    ┌──────────────────┐
   │ Authentication   │    │ Banking APIs     │    │ Notification     │
   │ / Identity       │    │                  │    │ Service          │
   │                  │    │ Customer         │    │                  │
   │ Login            │    │ Accounts         │    │ Email            │
   │ OTP              │    │ Transactions     │    │ SMS              │
   │ MFA              │    │ Beneficiary      │    │ Push             │
   │ Password         │    │ Payments         │    └──────────────────┘
   └──────────────────┘    │ Cards            │
                           │ Statements       │
                           └────────┬─────────┘
                                    │
                                    ▼
                         ┌──────────────────────────┐
                         │     BUSINESS LAYER       │
                         │                          │
                         │ Banking Rules            │
                         │ Validation               │
                         │ Transaction Processing   │
                         │ Security Rules            │
                         │ Balance Management       │
                         └────────────┬─────────────┘
                                      │
                    ┌─────────────────┼─────────────────┐
                    │                 │                 │
                    ▼                 ▼                 ▼
          ┌─────────────────┐ ┌────────────────┐ ┌─────────────────┐
          │   PostgreSQL   │ │ Audit / Logs   │ │ External / Mock │
          │                 │ │                │ │ Banking Systems │
          │ Customers       │ │ Audit Logs     │ │ NEFT            │
          │ Accounts        │ │ Application    │ │ RTGS            │
          │ Transactions    │ │ Logs           │ │ IMPS            │
          │ Beneficiaries   │ │                │ │ UPI Concept     │
          │ Cards           │ └────────────────┘ │ Payment Gateway │
          │ Payments        │                    └─────────────────┘
          │ Statements      │
          └─────────────────┘


────────────────────── QUALITY ENGINEERING LAYER ──────────────────────

   ┌──────────────────────────────────────────────────────────────────┐
   │                         QA ENGINEERING                           │
   │                                                                  │
   │ Manual │ Selenium │ Pytest │ Playwright │ Postman │ REST Assured │
   │ Cucumber/BDD │ Appium │ JMeter │ Security Testing │ DB Testing  │
   └──────────────────────────────┬───────────────────────────────────┘
                                  │
                                  ▼
                       ┌──────────────────────┐
                       │    TEST REPORTING    │
                       │                      │
                       │ Execution Reports    │
                       │ Defect Metrics       │
                       │ Automation Metrics   │
                       │ Performance Metrics  │
                       └──────────┬───────────┘
                                  │
                                  ▼
                              Power BI


────────────────────────── DEVOPS LAYER ────────────────────────────────

        GitHub
           │
           ▼
        Jenkins
           │
      ┌────┼─────┐
      ▼    ▼     ▼
    Build API   UI
      │    │     │
      └────┼─────┘
           ▼
        Reports
           │
           ▼
         Docker
           │
           ▼
      Test Environment


──────────────────────────── AI QA LAYER ─────────────────────────────

                         ┌──────────────────────┐
                         │       AI QA          │
                         │                      │
                         │ Test Generation      │
                         │ SQL Assistant        │
                         │ Test Data Generation │
                         │ Defect Analysis      │
                         │ Failure Analysis     │
                         │ QA Assistant         │
                         └──────────────────────┘

## 3. Architecture Components

### 3.1 Internet Banking (INB)

Internet Banking will provide the web-based banking experience for customers.

Major capabilities:

- Authentication
- Customer Profile
- Account Management
- Balance Enquiry
- Transaction History
- Fund Transfer
- Beneficiary Management
- Payments
- Card Management
- Statements
- Notifications
- Service Requests

### 3.2 Mobile Banking (MOB)

Mobile Banking will provide the Android-focused mobile banking experience.

Major capabilities:

- Mobile Login
- OTP
- PIN
- Biometric Authentication
- Device Registration
- Accounts
- Fund Transfer
- Beneficiaries
- Payments
- Cards
- Statements
- Notifications
- Profile

### 3.3 API Gateway / Security

The API Gateway/Security layer will provide:

- Authentication
- Authorization
- JWT/session handling
- Request validation
- API access control
- Security-related request processing

### 3.4 Authentication / Identity

The authentication component will handle:

- Login
- Logout
- OTP
- MFA
- Password management
- Account lock/unlock
- Session management

### 3.5 Banking APIs

REST APIs will expose banking functionality including:

- Customer APIs
- Account APIs
- Transaction APIs
- Beneficiary APIs
- Payment APIs
- Card APIs
- Statement APIs
- Notification APIs

### 3.6 Notification Service

The notification service will simulate:

- Email notifications
- SMS notifications
- Push notifications
- Transaction alerts
- Security alerts

### 3.7 Business Layer

The business layer will contain banking rules and processing logic.

Examples:

- Balance validation
- Transaction limits
- Beneficiary validation
- Transfer validation
- Account status validation
- Transaction processing
- Balance updates

### 3.8 PostgreSQL Database

PostgreSQL will store:

- Customers
- Accounts
- Transactions
- Beneficiaries
- Cards
- Payments
- Statements
- Notifications
- Audit information

### 3.9 Audit / Application Logs

The system will maintain:

- Audit logs
- Application logs
- Transaction logs
- Security events
- Error information

Sensitive information will not be stored unnecessarily in logs.

### 3.10 External / Mock Banking Systems

External systems will be simulated where required.

Examples:

- NEFT
- RTGS
- IMPS
- UPI concepts
- Payment Gateway

These integrations will initially use mock services rather than real banking networks.

### 3.11 QA Engineering Layer

The QA layer will validate the application using:

- Manual Testing
- SQL / Database Testing
- Postman
- REST Assured
- Selenium
- TestNG
- Pytest
- Playwright
- Cucumber / BDD
- Appium
- JMeter
- Security Testing

### 3.12 Test Reporting & Analytics

Testing results will generate:

- Test execution reports
- Automation reports
- API reports
- Performance reports
- Defect metrics
- Quality metrics

Selected metrics will be visualized using Power BI.

### 3.13 GitHub

GitHub will be used for:

- Source code
- Test automation
- Documentation
- Test cases
- Test data
- CI/CD configuration
- Version control

### 3.14 Jenkins / CI-CD

Jenkins will orchestrate automated testing.

Example pipeline:

Build
↓
Unit Tests
↓
API Tests
↓
UI Tests
↓
Reports
↓
Publish Results

### 3.15 Docker

Docker will provide reproducible environments for selected components such as:

- Banking application
- PostgreSQL
- API environment
- Automation execution environment

### 3.16 AI QA

AI-assisted QA capabilities will include:

- Test case generation
- Test scenario generation
- SQL assistance
- Test data generation
- Defect analysis
- Failure analysis
- Automation assistance
- QA Assistant

AI components will remain controlled QA proof-of-concepts and will not be unnecessarily coupled to the core banking transaction flow.

---

## 4. Architecture Principles

The project will follow these principles:

- Modular design
- Separation of concerns
- API-first integration
- Database integrity
- Secure-by-design QA
- Automation-friendly architecture
- Reusable test components
- Environment-independent configuration
- Traceability from requirements to tests
- CI/CD readiness
- Observability through logs and reports
- Controlled use of AI

---

## 5. Progressive Architecture

The architecture will be implemented progressively.

### Stage 1 — Core Application

The initial implementation will establish the basic end-to-end flow between the banking frontend, backend REST APIs, and PostgreSQL database.

```text
Frontend
   ↓
Backend API
   ↓
PostgreSQL

```
### Stage 2 — Security & Business Layer

The second stage will introduce API security and a dedicated business layer for banking rules and transaction processing.

```text
Frontend
   ↓
API Gateway / Security
   ↓
Backend APIs
   ↓
Business Layer
   ↓
PostgreSQL

```
### Stage 3 — Supporting Banking Services

The third stage will introduce supporting banking services required for a realistic digital banking platform, including authentication, notifications, audit logging, and external/mock banking integrations.

```text
Frontend
   ↓
API Gateway / Security
   ↓
Backend APIs
   ↓
Business Layer
   ├── PostgreSQL
   ├── Authentication
   ├── Notification Service
   ├── Audit / Logs
   └── External / Mock Banking Systems

```
###STAGE 4
                 COREBANK QA LAB
                        │
        ┌───────────────┼────────────────┐
        ▼               ▼                ▼
      INB UI          MOB UI          REST API
        │               │                │
        └───────────────┼────────────────┘
                        ▼
                 Banking Platform
                        │
          ┌─────────────┼─────────────┐
          ▼             ▼             ▼
      PostgreSQL     Mock Systems   Audit/Logs
                        │
                        ▼
                   QA ENGINEERING
                        │
     ┌──────────────────┼──────────────────┐
     ▼                  ▼                  ▼
 Manual/ISTQB       Automation          API/DB
     │                  │                  │
     ├─ Test Cases      ├─ Selenium       ├─ Postman
     ├─ RTM             ├─ TestNG         ├─ REST Assured
     ├─ Defects         ├─ Pytest         └─ SQL
     └─ Exploratory     └─ Playwright
                        │
                        ▼
                 CI/CD + DevOps
                        │
             ┌──────────┼──────────┐
             ▼          ▼          ▼
            Git       Docker    Kubernetes
             │
             ▼
       Jenkins / GitHub Actions

 ```

 ###Stage 5 — Automation & CI/CD
GitHub
   ↓
Jenkins
   ↓
Build
   ↓
Automated Test Execution
   ├── Selenium / Java
   ├── Pytest / Python
   ├── Playwright / TypeScript
   ├── REST Assured
   ├── Cucumber / BDD
   └── Appium
   ↓
Test Reports
   ↓
Docker Test Environment
Stage 6 — Analytics & AI QA

Test Results
     │
     ├──────────────► Power BI
     │
     └──────────────► AI QA
                         │
              ┌──────────┼──────────┐
              ▼          ▼          ▼
        Test Generation SQL       Defect
                         Assistant Analysis
              │          │          │
              └──────────┼──────────┘
                         ▼
                   QA Assistant
