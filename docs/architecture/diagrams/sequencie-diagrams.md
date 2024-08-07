### Sequence Diagrams

## Introduction

Sequence diagrams provide a detailed view of the interactions between various components of the AI Assistant system over time. They illustrate how different parts of the system collaborate to achieve specific functionalities. This document describes the sequence diagrams for key use cases, providing insight into the dynamic behavior of the system.

## Sequence Diagrams

### 1. User Registration

**Description:** This sequence diagram shows the steps involved in the user registration process, where a new user registers and creates a company profile, becoming a manager.

```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant AuthService
    participant CompanyService
    participant Database

    User->>Frontend: Fill Registration Form
    Frontend->>AuthService: POST /auth/register
    AuthService->>CompanyService: Create Company
    CompanyService->>Database: Insert Company
    Database-->>CompanyService: Company Created
    AuthService->>Database: Insert User with Company ID
    Database-->>AuthService: User Created
    AuthService-->>Frontend: Registration Success
    Frontend-->>User: Show Confirmation
```

### 2. Manage Company Settings

**Description:** This sequence diagram shows how a manager updates the company settings such as logo, description, industry, and billing details.

```mermaid
sequenceDiagram
    participant Manager
    participant Frontend
    participant CompanyService
    participant Database

    Manager->>Frontend: Update Company Settings Form
    Frontend->>CompanyService: PUT /company/settings
    CompanyService->>Database: Update Company Information
    Database-->>CompanyService: Update Success
    CompanyService-->>Frontend: Update Confirmation
    Frontend-->>Manager: Show Confirmation
```

### 3. Invite Employees

**Description:** This sequence diagram illustrates how a manager invites employees to join the company.

```mermaid
sequenceDiagram
    participant Manager
    participant Frontend
    participant AuthService
    participant EmailService

    Manager->>Frontend: Enter Employee Emails
    Frontend->>AuthService: POST /auth/invite
    AuthService->>EmailService: Send Invitation Emails
    EmailService-->>AuthService: Emails Sent
    AuthService-->>Frontend: Invitation Success
    Frontend-->>Manager: Show Confirmation
```

### 4. Take Skill Test

**Description:** This sequence diagram details the process of an employee taking a skill test.

```mermaid
sequenceDiagram
    participant Employee
    participant Frontend
    participant TestService
    participant Database

    Employee->>Frontend: Start Skill Test
    Frontend->>TestService: GET /tests/{id}
    TestService->>Database: Fetch Test Details
    Database-->>TestService: Test Details
    TestService-->>Frontend: Test Details
    Employee->>Frontend: Submit Test Responses
    Frontend->>TestService: POST /tests/{id}/responses
    TestService->>Database: Save Test Responses
    Database-->>TestService: Responses Saved
    TestService-->>Frontend: Submission Confirmation
    Frontend-->>Employee: Show Confirmation
```

### 5. Evaluate Test Responses

**Description:** This sequence diagram shows how the AI model evaluates the test responses and generates results.

```mermaid
sequenceDiagram
    participant TestService
    participant AIModelService
    participant Database

    TestService->>Database: Fetch Test Responses
    Database-->>TestService: Test Responses
    TestService->>AIModelService: Send Test Responses for Evaluation
    AIModelService-->>TestService: Evaluation Results
    TestService->>Database: Save Evaluation Results
    Database-->>TestService: Results Saved
```

### 6. View Reports

**Description:** This sequence diagram shows how a manager views detailed reports based on employee test results.

```mermaid
sequenceDiagram
    participant Manager
    participant Frontend
    participant ReportService
    participant Database

    Manager->>Frontend: View Reports
    Frontend->>ReportService: GET /reports
    ReportService->>Database: Fetch Report Data
    Database-->>ReportService: Report Data
    ReportService-->>Frontend: Report Data
    Frontend-->>Manager: Display Reports
```

### 7. View Test Results

**Description:** This sequence diagram illustrates how an employee views their own test results.

```mermaid
sequenceDiagram
    participant Employee
    participant Frontend
    participant TestService
    participant Database

    Employee->>Frontend: View Test Results
    Frontend->>TestService: GET /tests/{id}/results
    TestService->>Database: Fetch Test Results
    Database-->>TestService: Test Results
    TestService-->>Frontend: Test Results
    Frontend-->>Employee: Display Test Results
```

## Conclusion

The sequence diagrams provide a detailed view of the interactions between different components of the AI Assistant system for key use cases. These diagrams help in understanding the dynamic behavior of the system, ensuring that the interactions between various parts are well-defined and coordinated. By following these sequences, developers can ensure that the system's functionalities are implemented correctly and efficiently.