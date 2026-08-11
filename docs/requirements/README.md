# CoreBankX QA Lab — Requirements

## 1. Purpose

This document defines the functional and non-functional requirements for the CoreBankX QA Lab digital banking platform.

The application will simulate a modern Internet Banking (INB) and Mobile Banking (MOB) platform for Quality Engineering and automation practice.

---

## 2. Internet Banking Requirements

### 2.1 Authentication

The system shall provide:

- Login
- Logout
- Forgot Password
- Password Reset
- OTP
- Multi-Factor Authentication
- Session Management
- Account Lock/Unlock

### 2.2 Customer Management

The system shall provide:

- Customer Profile
- Personal Information
- Contact Details
- KYC Information
- Nominee
- Address
- Service Requests

### 2.3 Account Management

The system shall provide:

- Account Summary
- Savings Account
- Current Account
- Balance Enquiry
- Transaction History
- Account Statement
- Account Details

### 2.4 Fund Transfer

The system shall support:

- Own Account Transfer
- Within Bank Transfer
- Other Bank Transfer
- NEFT
- RTGS
- IMPS
- UPI concepts
- Scheduled Transfer
- Transfer Status

### 2.5 Beneficiary Management

The system shall provide:

- Add Beneficiary
- Modify Beneficiary
- Delete Beneficiary
- Activate Beneficiary
- Deactivate Beneficiary
- Beneficiary Validation

### 2.6 Payments

The system shall provide:

- Bill Payments
- Recharge
- Utility Payments
- Payment History
- Scheduled Payments

### 2.7 Card Management

The system shall provide:

- Debit Card
- Credit Card
- Card Details
- Card Activation
- Block/Unblock
- PIN Services
- Card Limits
- Card Transactions

---

# 3. Mobile Banking Requirements

The mobile banking application shall support:

- Mobile Login
- OTP
- PIN
- Biometric Authentication
- Device Registration
- Dashboard
- Accounts
- Balance Enquiry
- Transaction History
- Fund Transfer
- Beneficiary
- Payments
- Cards
- Statements
- Notifications
- Profile
- Service Requests

Android will be the primary mobile automation platform.

---

# 4. Database Requirements

PostgreSQL will be used as the primary relational database.

Core entities will include:

- Customers
- Accounts
- Transactions
- Beneficiaries
- Cards
- Payments
- Statements
- Notifications
- Audit Logs

---

# 5. API Requirements

The backend shall expose REST APIs for:

- Authentication
- Customer
- Accounts
- Transactions
- Beneficiaries
- Payments
- Cards
- Statements
- Notifications

The APIs shall support appropriate HTTP methods including:

- GET
- POST
- PUT
- PATCH
- DELETE

---

# 6. Quality Engineering Requirements

The project shall support:

- Manual Testing
- Functional Testing
- Regression Testing
- Integration Testing
- System Testing
- UAT
- API Testing
- Database Testing
- UI Automation
- Mobile Testing
- Performance Testing
- Security Testing
- AI-assisted QA

---

# 7. Automation Requirements

The project will contain automation implementations using:

### Java

- Selenium
- TestNG
- Maven
- REST Assured
- Cucumber

### Python

- Pytest

### TypeScript

- Playwright

### Mobile

- Appium

---

# 8. CI/CD Requirements

The project shall demonstrate:

- Git
- GitHub
- Jenkins
- Docker
- Automated test execution
- Automated reporting

---

# 9. Reporting Requirements

The project shall generate:

- Test Execution Reports
- Automation Reports
- API Reports
- Performance Reports
- Defect Metrics
- QA Dashboards

Power BI will be used for selected analytics dashboards.

---

# 10. AI QA Requirements

The project shall demonstrate AI-assisted capabilities including:

- Test Case Generation
- Test Scenario Generation
- SQL Generation
- SQL Explanation
- Test Data Generation
- Defect Analysis
- Automation Assistance
- Failure Analysis
- QA Assistant

---

# 11. Documentation Requirements

The repository shall maintain:

- Requirements
- Architecture
- Test Strategy
- Test Cases
- Test Data
- API Documentation
- Database Documentation
- Automation Documentation
- Daily Development Notes
- Project Journal
- Interview Bank

---

# 12. Non-Functional Requirements

The application should consider:

- Security
- Performance
- Reliability
- Availability
- Usability
- Maintainability
- Scalability
- Compatibility
- Accessibility

---

# 13. Banking Transaction Integrity

The system shall maintain transactional consistency.

For a successful fund transfer:

```text
Source Account Balance
        ↓
Debit Amount
        ↓
Transaction Processing
        ↓
Credit Destination Account
        ↓
Transaction Record
        ↓
Audit Log
        ↓
Notification
