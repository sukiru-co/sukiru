### Data Flow Diagram

## Introduction

The data flow diagram (DFD) provides a visual representation of the flow of data within the AI Assistant system. It illustrates how data moves between different components, highlighting the processes, data stores, and external entities involved. This document describes the DFD for key processes within the system, offering a clear picture of the system’s data dynamics.

## Data Flow Diagram

### Level 0: Context Diagram

The Level 0 DFD provides an overview of the entire system, showing the major processes and the flow of data between them.

```mermaid
graph TD;
    User -->|1. Registration Data| Process1[User Registration];
    Process1 -->|2. Company Data| DataStore1[(Database)];
    Manager -->|3. Company Settings| Process2[Manage Company Settings];
    Process2 -->|4. Updated Company Data| DataStore1;
    Manager -->|5. Employee Emails| Process3[Invite Employees];
    Process3 -->|6. Invitations| EmailService;
    Employee -->|7. Test Responses| Process4[Take Skill Test];
    Process4 -->|8. Responses| DataStore1;
    Process4 -->|9. Evaluation Request| Process5[Evaluate Test Responses];
    Process5 -->|10. Evaluation Results| DataStore1;
    Manager -->|11. Report Request| Process6[View Reports];
    Process6 -->|12. Report Data| DataStore1;
    Process6 -->|13. Reports| Manager;
    Employee -->|14. Result Request| Process7[View Test Results];
    Process7 -->|15. Results Data| DataStore1;
    Process7 -->|16. Test Results| Employee;

    subgraph External Entities
        User
        Manager
        Employee
        EmailService
    end

    subgraph Data Stores
        DataStore1[(Database)]
    end

    subgraph Processes
        Process1[User Registration]
        Process2[Manage Company Settings]
        Process3[Invite Employees]
        Process4[Take Skill Test]
        Process5[Evaluate Test Responses]
        Process6[View Reports]
        Process7[View Test Results]
    end
```

### Level 1: Detailed Diagrams

#### 1. User Registration

**Description:** This process involves a user registering and creating a company profile.

```mermaid
graph TD;
    User -->|Registration Form| Frontend;
    Frontend -->|Registration Data| AuthService;
    AuthService -->|Create Company| CompanyService;
    CompanyService -->|Insert Company| Database;
    Database -->|Company Created| CompanyService;
    AuthService -->|Insert User| Database;
    Database -->|User Created| AuthService;
    AuthService -->|Registration Success| Frontend;
    Frontend -->|Show Confirmation| User;
```

#### 2. Manage Company Settings

**Description:** This process involves a manager updating the company settings.

```mermaid
graph TD;
    Manager -->|Update Form| Frontend;
    Frontend -->|Updated Settings| CompanyService;
    CompanyService -->|Update Company| Database;
    Database -->|Update Success| CompanyService;
    CompanyService -->|Update Confirmation| Frontend;
    Frontend -->|Show Confirmation| Manager;
```

#### 3. Invite Employees

**Description:** This process involves a manager inviting employees to the company.

```mermaid
graph TD;
    Manager -->|Employee Emails| Frontend;
    Frontend -->|Invite Request| AuthService;
    AuthService -->|Send Invitations| EmailService;
    EmailService -->|Invitations Sent| AuthService;
    AuthService -->|Invitation Success| Frontend;
    Frontend -->|Show Confirmation| Manager;
```

#### 4. Take Skill Test

**Description:** This process involves an employee taking a skill test.

```mermaid
graph TD;
    Employee -->|Start Test| Frontend;
    Frontend -->|Get Test Details| TestService;
    TestService -->|Fetch Test| Database;
    Database -->|Test Details| TestService;
    TestService -->|Test Details| Frontend;
    Employee -->|Submit Responses| Frontend;
    Frontend -->|Submit Responses| TestService;
    TestService -->|Save Responses| Database;
    Database -->|Responses Saved| TestService;
    TestService -->|Submission Confirmation| Frontend;
    Frontend -->|Show Confirmation| Employee;
```

#### 5. Evaluate Test Responses

**Description:** This process involves evaluating the skill test responses using the AI model.

```mermaid
graph TD;
    TestService -->|Fetch Responses| Database;
    Database -->|Test Responses| TestService;
    TestService -->|Evaluate Responses| AIModelService;
    AIModelService -->|Evaluation Results| TestService;
    TestService -->|Save Results| Database;
    Database -->|Results Saved| TestService;
```

#### 6. View Reports

**Description:** This process involves a manager viewing detailed reports.

```mermaid
graph TD;
    Manager -->|Request Reports| Frontend;
    Frontend -->|Get Reports| ReportService;
    ReportService -->|Fetch Report Data| Database;
    Database -->|Report Data| ReportService;
    ReportService -->|Report Data| Frontend;
    Frontend -->|Display Reports| Manager;
```

#### 7. View Test Results

**Description:** This process involves an employee viewing their test results.

```mermaid
graph TD;
    Employee -->|Request Results| Frontend;
    Frontend -->|Get Results| TestService;
    TestService -->|Fetch Results| Database;
    Database -->|Results Data| TestService;
    TestService -->|Results Data| Frontend;
    Frontend -->|Display Results| Employee;
```

## Conclusion

The data flow diagrams provide a clear visual representation of the data movement within the AI Assistant system. By understanding these flows, developers can ensure that data is handled efficiently and securely across different components of the system. This detailed mapping helps in designing, maintaining, and troubleshooting the system effectively.