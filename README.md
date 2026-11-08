# Restful Booker API Test Automation

A REST API test automation project built using **Postman, JavaScript, Newman, and GitHub Actions**.

The project tests the public Restful Booker API, covering authentication, booking CRUD operations, response validation, and negative testing.

## Technologies Used

- Postman — API request development and test execution
- JavaScript — Automated API assertions
- Newman — Command-line execution of Postman collections
- Node.js and npm — Dependency management and test scripts
- GitHub Actions — Continuous integration (CI)

## Test Coverage

### CRUD Workflow

The automated CRUD workflow includes:

1. Create an authentication token
2. Create a new booking
3. Retrieve the booking by ID
4. Update the booking
5. Verify the updated booking details
6. Delete the booking
7. Verify that the deleted booking returns HTTP 404

The workflow validates HTTP status codes, response bodies, booking details, and the complete booking lifecycle.

### Negative Testing

Additional tests explore:

- Retrieving a nonexistent booking
- Updating a booking without authentication
- Creating a booking with missing required fields
- Creating a booking with invalid data types

Some negative tests intentionally highlight unexpected API behaviour and are kept separate from the passing CI workflow.

## Test Results

The CRUD workflow has been successfully executed using Postman Collection Runner, Newman, and GitHub Actions.

| Metric | Result |
|---|---|
| Requests | 7 |
| Assertions | 21 |
| Passed | 21 |
| Failed | 0 |

## Running the Tests Locally

### Prerequisites

- Node.js
- npm

### Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/YOUR-USERNAME/restful-booker-api-tests.git
cd restful-booker-api-tests
npm ci
```

Replace `Tomibbbb` with your GitHub username.

### Execute Tests

```bash
npm test
```

This runs the CRUD workflow using Newman.

## Continuous Integration

GitHub Actions automatically runs the API tests on pushes and pull requests. The workflow can also be triggered manually.

The CI pipeline:

1. Checks out the repository
2. Sets up Node.js
3. Installs project dependencies
4. Executes the automated API tests using Newman
5. Reports test results and failures

## API Under Test

Restful Booker practice API:

https://restful-booker.herokuapp.com

## Future Improvements

- Generate HTML test reports
- Expand negative and boundary-value testing
- Add data-driven API tests
- Improve reporting of known API validation issues

## Project Purpose

This project demonstrates practical QA automation skills, including REST API testing, JavaScript assertions, authentication handling, CRUD operations, negative testing, command-line execution, and CI integration.