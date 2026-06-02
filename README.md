# Trello API Test Automation
End-to-end API test automation framework built with Postman, Newman, and GitHub Actions.
## Overview

This project demonstrates automated API testing of the Trello REST API using **Postman**, **Newman**, and **GitHub Actions**.

The test suite validates core Trello functionality including board, list, card, and checklist operations. Tests are executed automatically through a CI/CD pipeline whenever code is pushed to the repository or when the workflow is manually triggered.

This project showcases API testing, test automation, environment management, and continuous integration skills.

---

## Repository Structure

```text
.
├── .github/
│   └── workflows/
│       └── trello_api.yml
├── Trello_collection.json
├── Trello_Prod_environment.json
└── README.md
```

---

## Technology Stack

* Postman
* Newman
* GitHub Actions
* Node.js
* Trello REST API

---

## Features

* Automated API testing using Postman collections
* CI/CD integration with GitHub Actions
* Secure credential management using GitHub Secrets
* Environment-based test execution
* Dynamic variable handling across requests
* End-to-end validation of Trello workflows

---

## Test Coverage

The collection validates the following Trello API operations:

| Feature    | Operation        |
| ---------- | ---------------- |
| Boards     | Create Board     |
| Boards     | Get Board        |
| Boards     | Update Board     |
| Boards     | Delete Board     |
| Lists      | Create List      |
| Lists      | Get List         |
| Lists      | Update List      |
| Lists      | Archive List     |
| Lists      | Unarchive List   |
| Cards      | Create Card      |
| Cards      | Get Card         |
| Cards      | Update Card      |
| Checklists | Create Checklist |
| Checklists | Get Checklist    |
| Checklists | Update Checklist |

---

## Authentication

Authentication is managed through GitHub Secrets.

| Secret Name    | Description      |
| -------------- | ---------------- |
| POSTMAN_AI_KEY | Trello API Key   |
| POSTMAN_TOKEN  | Trello API Token |

These secrets are injected into the workflow at runtime and are never stored in source control.

---

## Environment Variables

The collection uses the following environment variables:

| Variable     | Description                        |
| ------------ | ---------------------------------- |
| base_url     | Trello API Base URL                |
| key          | Trello API Key                     |
| token        | Trello API Token                   |
| board_id     | Generated after board creation     |
| list_id      | Generated after list creation      |
| card_id      | Generated after card creation      |
| checklist_id | Generated after checklist creation |

Dynamic variables are automatically populated during test execution.

---

## GitHub Actions Workflow

The workflow executes automatically:

* On every push to the repository
* When manually triggered from the Actions tab

### Workflow File

```yaml
name: Trello API Tests

on:
  push:
  workflow_dispatch:

jobs:
  run-postman-tests:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Install Newman
        run: npm install -g newman

      - name: Run Collection
        env:
          POSTMAN_AI_KEY: ${{ secrets.POSTMAN_AI_KEY }}
          POSTMAN_TOKEN: ${{ secrets.POSTMAN_TOKEN }}
        run: |
          newman run "Trello_collection.json" \
            -e "Trello_Prod_environment.json" \
            --env-var "key=${POSTMAN_AI_KEY}" \
            --env-var "base_url=https://api.trello.com" \
            --env-var "token=${POSTMAN_TOKEN}"
```

---

## Running Tests Locally

### Install Newman

```bash
npm install -g newman
```

### Execute the Collection

```bash
newman run Trello_collection.json \
-e Trello_Prod_environment.json
```

---

## Sample Test Flow

1. Create Board
2. Retrieve Board Details
3. Create List
4. Retrieve List Details
5. Create Card
6. Retrieve Card Details
7. Create Checklist
8. Retrieve Checklist Details
9. Update Resources
10. Archive/Unarchive List
11. Delete Board
12. Verify Resource Deletion

---

## CI/CD Validation

Successful execution validates:

* Authentication
* API availability
* Request/response handling
* Resource creation
* Resource updates
* Resource deletion
* End-to-end workflow integrity

---

## Skills Demonstrated

* API Testing
* REST API Validation
* Postman Collections
* Newman CLI
* GitHub Actions
* CI/CD Pipelines
* Environment Management
* Secret Management
* Test Automation
* Quality Assurance

---

## Author

Mutasim Mohamed
themanno1001@gmail.com

QA Automation Engineer | API Testing | Test Automation | CI/CD

This project was created to demonstrate practical API automation skills using modern testing and DevOps tools.



