# CODEFATHER Flash-Sale Backend

A production-minded Java and Spring Boot flash-sale backend built in public to
study concurrency, transactions, reliability, distributed systems,
observability, and performance.

## Project status

The requirements baseline is complete.

The project is currently defining HLD version 1 and its technology baseline
before generating the Spring Boot application.

No benchmark result, production-scale claim, or reliability guarantee has been
established yet.

## Problem

A flash sale contains limited inventory while many users may attempt to
purchase at approximately the same time.

The completed system must address:

- prevention of overselling
- duplicate purchase requests
- duplicate or delayed payment callbacks
- temporary component failures
- reservation expiration
- inventory recovery
- auditability
- measured rather than fabricated performance claims

## Future test scenario

A future load and concurrency experiment will model:

- 10,000 purchase attempts
- 100 available units
- inventory never falling below zero
- no more successful purchases than available units
- duplicate requests producing no duplicate purchase
- every successful purchase remaining traceable

This is a planned experiment. It is not an achieved benchmark, user count, or
production-capacity claim.

## Architecture direction

The system begins as one modular monolith with logical modules for:

- catalog
- inventory
- flash sale
- reservation
- order
- payment
- outbox
- notification
- shared infrastructure

PostgreSQL is the initial source of truth.

Redis will be considered only after the working PostgreSQL-backed baseline
demonstrates a genuine caching or traffic-control problem.

Kafka will be considered only after the project demonstrates a genuine
asynchronous delivery problem.

Kubernetes and unnecessary cloud infrastructure are out of scope.

## Technology baseline

| Concern | Selection |
|---|---|
| Language | Java 21 using an OpenJDK distribution |
| Framework | Spring Boot 4.1.3 |
| Build | Maven 3.10.2 through Maven Wrapper |
| Database | PostgreSQL 18.7 |
| Migrations | Flyway |
| Tests | JUnit 5 and Testcontainers |
| Development | GitHub Codespaces and Docker Compose |
| CI | GitHub Actions |
| Load testing | k6 |
| Diagrams | Mermaid |
| Health and metrics | Spring Boot Actuator and Micrometer |

## Development environment

GitHub is the source of truth.

GitHub Codespaces is the default development environment. No local project
folder or local Java, PostgreSQL, Redis, or Kafka installation is required.

## Documentation

### Requirements

- [Problem statement](docs/requirements/problem-statement.md)
- [Functional requirements](docs/requirements/functional-requirements.md)
- [Non-functional requirements](docs/requirements/non-functional-requirements.md)
- [Cloud development workflow](docs/requirements/cloud-development-workflow.md)

### Architecture

- [High-Level Design v1](docs/architecture/hld-v1.md)
- [ADR 0001: Begin as a modular monolith](docs/adr/0001-modular-monolith.md)
- [ADR 0002: Select the technology baseline](docs/adr/0002-technology-baseline.md)

### Planning and progress

- [Seven-day completion sprint](ROADMAP.md)
- [Current project state](docs/progress/PROJECT_STATE.md)

## Evidence policy

No throughput, latency, availability, scale, or reliability claim will be
published unless it is supported by code, tests, and documented measurements.

Important failures will be preserved as engineering evidence before their
corrections are implemented.
