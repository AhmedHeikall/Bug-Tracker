# Bug Tracker Pro

<p align="center">
  <img src="bugtracker-frontend/public/bugTracker_Logo.png" alt="Bug Tracker Logo" width="300" height="300"/>
</p>

A full-stack bug-tracking application built with **Go** for the backend and **Next.js** for the frontend. The application enables users to create, view, update, and delete bug reports, with support for comments, priorities, and status management.

The project also includes a complete **CI/CD and automated testing workflow** using **Jenkins, GitHub Actions, Docker, Playwright, k6, and Git**, integrating **Unit, API, Integration, End-to-End (E2E), and Performance Testing** with automated test execution and report generation.

## Features

* Create and manage bug reports
* Add comments to bugs
* Set priority levels and status
* Real-time updates
* Responsive design
* Comprehensive automated test coverage
* Unit testing
* API testing
* Integration testing
* End-to-End testing using Playwright
* Performance testing using k6
* Automated CI/CD pipelines
* Automated test report generation
* Dockerized application and testing environments
* Automated test execution through GitHub Actions and Jenkins

## Tech Stack

### Application

* **Backend:** Go
* **Frontend:** Next.js
* **Database:** PostgreSQL
* **Containerization:** Docker & Docker Compose

### Testing

* **Unit Testing:** Go Testing / Jest
* **API Testing:** Playwright
* **E2E Testing:** Playwright
* **Performance Testing:** k6

### CI/CD & DevOps

* **Version Control:** Git & GitHub
* **CI/CD:** GitHub Actions & Jenkins
* **Containerization:** Docker
* **Test Reports:** Playwright HTML Reports and automated CI test reports

## Prerequisites

Before running the application, ensure you have the following installed:

* [Node.js](https://nodejs.org/) (v20 or later)
* [Go](https://go.dev/) (v1.21 or later)
* [Docker and Docker Compose](https://docs.docker.com/)
* [Git](https://git-scm.com/)

## Quick Start with Docker Compose

The easiest way to run the application is using Docker Compose:

```bash
# Clone the repository
git clone https://github.com/AhmedHeikall/Bug-Tracker.git

cd Bug-Tracker

# Launch the application
docker compose up --build
```

The application will be available at:

* Frontend: `http://localhost:3000`
* Backend API: `http://localhost:8080`

## Manual Setup

### Backend

```bash
cd bugtracker-backend

# Install dependencies
go mod download

# Run the application
go run cmd/bugtracker/main.go
```

The backend API will be available at:

`http://localhost:8080`

### Frontend

```bash
cd bugtracker-frontend

# Install dependencies
npm install

# Run the development server
npm run dev
```

The frontend will be available at:

`http://localhost:3000`

## Running Tests

The project includes multiple levels of automated testing to validate application functionality and performance.

### Backend Unit Tests

```bash
cd bugtracker-backend

go test ./... -v
```

### Frontend Unit Tests

```bash
cd bugtracker-frontend

npm test
```

### API Tests

API tests are implemented using Playwright:

```bash
cd tests-api

npm install

npm run test:local
```

### End-to-End Tests

E2E tests are implemented using Playwright:

```bash
cd tests-e2e

npm install

npx playwright test
```

### Performance Tests

Performance testing is implemented using **k6**.

Install k6:

```bash
# macOS
brew install k6

# Windows
winget install k6
```

For Linux installation instructions, refer to the official k6 documentation.

Run the performance tests:

```bash
cd tests-perf

k6 run script.js
```

## Test Reports

The project automatically generates test reports to make test execution results easy to review and analyze.

### Playwright HTML Reports

After running API or E2E tests, Playwright generates an HTML report containing:

* Test execution status
* Passed and failed tests
* Execution duration
* Test steps
* Screenshots
* Traces
* Error details

Generate and view the report:

```bash
npx playwright test

npx playwright show-report
```

### CI Test Reports

Test reports are also generated during CI execution and uploaded as **GitHub Actions artifacts**, allowing test results to be downloaded and reviewed after the workflow completes.

The CI pipeline can preserve reports such as:

* Playwright HTML reports
* Test result files
* Screenshots
* Traces
* Performance test results

## GitHub Actions CI/CD

The project includes **GitHub Actions workflows** to automate the software testing and CI/CD process.

The GitHub Actions pipeline automatically executes the required validation steps when changes are pushed or Pull Requests are created.

Typical workflow:

```text
Developer Push / Pull Request
            ↓
      GitHub Actions
            ↓
       Checkout Code
            ↓
      Install Dependencies
            ↓
       Build Application
            ↓
     Unit Tests
            ↓
       API Tests
            ↓
       E2E Tests
            ↓
   Performance Tests
            ↓
     Generate Reports
            ↓
   Upload Test Reports
            ↓
        Build Docker
            ↓
    Deploy to Staging
```

The workflows are located in:

```text
.github/
└── workflows/
    ├── ci.yml
    └── cd.yml
```

GitHub Actions is responsible for automating:

* Code checkout
* Dependency installation
* Application build
* Unit test execution
* API test execution
* E2E test execution
* Performance test execution
* Test report generation
* Test report artifact upload
* Docker image building
* Deployment to the staging environment

## Jenkins CI/CD

The project also includes Jenkins pipelines located in the `jenkins/` directory.

Jenkins can be started locally using Docker Compose:

```bash
cd jenkins

docker compose up --build
```

Jenkins will then be available at:

`http://localhost:9000`

The Jenkins pipeline can be used to automate:

* Application builds
* Automated test execution
* Docker image creation
* Test report generation
* Deployment to the staging environment

## CI/CD Pipeline Strategy

The project uses both **GitHub Actions and Jenkins** to demonstrate CI/CD automation.

### GitHub Actions

Used for automated CI workflows integrated directly with GitHub:

```text
Git Push / Pull Request
        ↓
GitHub Actions
        ↓
Build
        ↓
Unit Tests
        ↓
API Tests
        ↓
E2E Tests
        ↓
Generate Reports
        ↓
Upload Artifacts
```

### Jenkins

Used to demonstrate a Jenkins-based CI/CD pipeline:

```text
Source Code
    ↓
Jenkins
    ↓
Build & Test
    ↓
Docker Image
    ↓
Test Reports
    ↓
Deploy to Staging
```

## Project Structure

```text
Bug-Tracker/
│
├── bugtracker-backend/
│   └── Go backend application
│
├── bugtracker-frontend/
│   └── Next.js frontend application
│
├── tests-api/
│   └── API tests using Playwright
│
├── tests-e2e/
│   └── End-to-End tests using Playwright
│
├── tests-perf/
│   └── Performance tests using k6
│
├── jenkins/
│   └── Jenkins pipeline configurations
│
├── .github/
│   └── workflows/
│       ├── ci.yml
│       └── cd.yml
│
├── docker-compose.yml
└── README.md
```

## What I Learned

Through this project, I gained practical experience in:

* Designing a full-stack application
* Manual and automated software testing
* Unit testing
* API testing
* Integration testing
* End-to-End testing
* Performance testing with k6
* Writing maintainable Playwright tests
* Generating and analyzing automated test reports
* Dockerizing applications
* Creating CI/CD pipelines
* GitHub Actions workflow automation
* Jenkins pipeline automation
* Managing test artifacts in CI
* Automating Docker builds
* Automated deployment to staging environments
* Integrating testing into the software development lifecycle

## Contributing

1. Fork the repository
2. Create your feature branch

```bash
git checkout -b feature/AmazingFeature
```

3. Commit your changes

```bash
git commit -m "Add some AmazingFeature"
```

4. Push to the branch

```bash
git push origin feature/AmazingFeature
```

5. Open a Pull Request

## License

This project is licensed under the MIT License - see the `LICENSE` file for details.
