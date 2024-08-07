### README.md

# AI Assistant

Welcome to the AI Assistant project! This project aims to create an AI assistant that helps users identify their skills based on personality tests. The system allows managers to invite users, manage company settings, and view reports. This README provides an overview of the project, how to set it up, and how to contribute.

## Table of Contents

- [AI Assistant](#ai-assistant)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Features](#features)
  - [Architecture](#architecture)
  - [Setup and Installation](#setup-and-installation)
    - [Prerequisites](#prerequisites)
    - [Installation Steps](#installation-steps)
  - [Usage](#usage)
  - [API Documentation](#api-documentation)
  - [Frontend Documentation](#frontend-documentation)
  - [Testing](#testing)
    - [Running Tests](#running-tests)
    - [Test Documentation](#test-documentation)
  - [Contributing](#contributing)
  - [License](#license)

## Overview

The AI Assistant system is designed to help managers and employees identify and analyze skills based on personality tests. The system includes features for user registration, company management, skill testing, AI-based evaluation, and detailed reporting.

## Features

- User Registration and Authentication
- Company Management (Create, Update, Settings)
- Employee Invitations and Management
- Skill Test Administration and Response Collection
- AI-based Evaluation of Test Responses
- Detailed Reporting and Analytics

## Architecture

The system follows a modular architecture with the following main components:

- **Frontend:** A React application that provides the user interface.
- **Backend:** A NestJS application that provides the API and business logic.
- **Database:** PostgreSQL for storing user, company, test, and evaluation data.
- **AI Model:** Integrates with AI services for evaluating test responses.

For more detailed information, refer to the [Architecture Overview](docs/architecture/overview.md) and the [Design Principles](docs/architecture/design-principles.md) documents.

## Setup and Installation

### Prerequisites

- Node.js (version 14.x or higher)
- npm (version 6.x or higher) or yarn
- PostgreSQL (version 12.x or higher)
- Docker (optional, for containerized deployment)

### Installation Steps

1. **Clone the repository:**

```bash
git clone https://github.com/sukiru-co/sukiru.git
cd sukiru
```

2. **Set up the backend:**

```bash
cd api
cp .env.example .env
npm install
```

Update the `.env` file with your database and other configurations.

3. **Set up the frontend:**

```bash
cd ../frontend
cp .env.example .env
npm install
```

Update the `.env` file with your API endpoint and other configurations.

4. **Run the backend:**

```bash
cd ../api
npm run start:dev
```

5. **Run the frontend:**

```bash
cd ../frontend
npm start
```

## Usage

1. **Register a new user and create a company.**
2. **Invite employees to join the company.**
3. **Administer skill tests and collect responses.**
4. **View detailed reports and analytics on employee skills.**

## API Documentation

The API documentation provides details on all available endpoints, including request and response formats, error codes, and examples.

- [API Overview](docs/api/index.md)
- [Authentication Endpoints](docs/api/auth/index.md)
- [Company Management Endpoints](docs/api/company/index.md)
- [Employee Management Endpoints](docs/api/employee/index.md)
- [Testing Endpoints](docs/api/testing/index.md)
- [Reporting Endpoints](docs/api/reporting/index.md)

## Frontend Documentation

The frontend documentation includes information on components, pages, and general usage guidelines.

- [Component Documentation](docs/frontend/components/index.md)
- [Page Documentation](docs/frontend/pages/index.md)
- [Styling Guidelines](docs/frontend/general/styling.md)

## Testing

Testing is an essential part of ensuring the reliability and stability of the system. This project includes unit tests, integration tests, and end-to-end tests.

### Running Tests

1. **Backend Tests:**

```bash
cd backend
npm run test
```

2. **Frontend Tests:**

```bash
cd frontend
npm run test
```

### Test Documentation

- [Backend Testing](docs/testing/backend-testing.md)
- [Frontend Testing](docs/testing/frontend-testing.md)
- [End-to-End Testing](docs/testing/end-to-end-testing.md)

## Contributing

We welcome contributions from the community! To contribute to the project, please follow these steps:

1. **Fork the repository.**
2. **Create a new branch:**

```bash
git checkout -b feature/your-feature-name
```

3. **Make your changes and commit them:**

```bash
git commit -m "Add some feature"
```

4. **Push to the branch:**

```bash
git push origin feature/your-feature-name
```

5. **Open a pull request.**

Please make sure to update tests as appropriate and follow the project's coding standards.

## License


---

Thank you for using the AI Assistant! If you have any questions or need further assistance, please refer to the documentation or open an issue in the repository.