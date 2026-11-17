# CODEFATHER Flash-Sale Backend

A production-minded Java and Spring Boot flash-sale backend built in public
to study concurrency, transactions, reliability, distributed systems,
observability and performance.

## Project status

The project is currently in the foundation phase.

Application code has not yet been generated. The current work defines the
problem, requirements, constraints and cloud development workflow before
architecture and implementation begin.

## Problem

A flash sale contains a limited number of products or tickets while many
users may attempt to purchase them simultaneously.

The completed system must address:

- limited inventory
- concurrent purchase attempts
- prevention of overselling
- duplicate purchase requests
- duplicate or delayed payment callbacks
- temporary component failures
- reservation expiry
- inventory recovery
- auditability
- measured rather than fabricated performance claims

## Future test scenario

A future load and concurrency test will model:

- 10,000 purchase attempts
- 100 available units
- inventory never falling below zero
- duplicate requests producing no duplicate purchase
- every successful purchase remaining traceable

This is a planned test scenario. It is not an achieved benchmark or
production-scale claim.

## Initial architecture direction

The system will begin as a modular monolith.

PostgreSQL will initially be the source of truth.

Redis will be considered only after a working database-backed baseline
demonstrates a genuine caching or traffic-control problem.

Kafka will be considered only after the project demonstrates a genuine
asynchronous communication or reliable event-delivery problem.

Kubernetes and unnecessary cloud infrastructure are out of scope.

## Development environment

GitHub is the source of truth.

GitHub Codespaces is the default development environment. No local project
folder or local Java, PostgreSQL, Redis or Kafka installation is required.

## Documentation

- [Problem statement](docs/requirements/problem-statement.md)
- [Functional requirements](docs/requirements/functional-requirements.md)
- [Non-functional requirements](docs/requirements/non-functional-requirements.md)
- [Cloud development workflow](docs/requirements/cloud-development-workflow.md)
- [Current project state](docs/progress/PROJECT_STATE.md)

## Evidence policy

No throughput, latency, availability, scale or reliability claim will be
published unless it is supported by code, tests and documented measurements.