# DevOps Capstone Project

[![CI Build](https://github.com/yaqyn/devops-capstone-project/actions/workflows/ci-build.yaml/badge.svg)](https://github.com/yaqyn/devops-capstone-project/actions/workflows/ci-build.yaml)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python 3.9](https://img.shields.io/badge/Python-3.9-green.svg)](https://shields.io/)

## Project Name

**devops-capstone-project**

This repository contains the DevOps Capstone Project: a **Customer Accounts
Microservice** for an e-commerce website, built with Python, Flask, SQLAlchemy
and PostgreSQL. The service exposes a well-formed REST API that other
microservices can call to create, read, update, delete and list customer
accounts. It is containerized with Docker, deployed to Kubernetes/OpenShift
and delivered through an automated CI/CD pipeline built with GitHub Actions
and Tekton.

## REST API

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/health` | Service health check |
| GET | `/` | Service index |
| POST | `/accounts` | Create a new account |
| GET | `/accounts` | List all accounts |
| GET | `/accounts/{id}` | Read an account |
| PUT | `/accounts/{id}` | Update an account |
| DELETE | `/accounts/{id}` | Delete an account |

## Data Model

The Account model contains the following fields:

| Name | Type | Optional |
|------|------|----------|
| id | Integer | False |
| name | String(64) | False |
| email | String(64) | False |
| address | String(256) | False |
| phone_number | String(32) | True |
| date_joined | Date | False |

## Development

```bash
source ~/venv/bin/activate
make install   # install dependencies
make db        # start PostgreSQL in Docker
make tests     # run nosetests with coverage
make run       # run the service locally
make lint      # run flake8
```

The code follows the **Model-View-Controller** pattern with all of the
database code and business logic in the model (`models.py`) and all of the
RESTful routing in the controller (`routes.py`).

## Continuous Integration and Delivery

- **CI:** GitHub Actions runs flake8 linting and the `nosetests` unit test
  suite on every push and pull request (`.github/workflows/ci-build.yaml`).
- **Security:** Flask-Talisman adds secure HTTP headers and Flask-Cors
  enforces Cross-Origin Resource Sharing policies.
- **Container:** the `Dockerfile` builds a non-root `python:3.9-slim` image
  served by gunicorn on port 8080.
- **CD:** Tekton `cd-pipeline` clones, lints, tests, builds and deploys the
  service to Kubernetes/OpenShift (`tekton/`).

## Kubernetes

```bash
kubectl apply -f deploy/postgres.yaml
kubectl apply -f deploy/accounts.yaml
kubectl get all
```

## Author

IBM DevOps and Software Engineering Capstone Project.

## License

Licensed under the Apache License. See [LICENSE](LICENSE)
