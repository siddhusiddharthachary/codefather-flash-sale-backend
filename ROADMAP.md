# CODEFATHER Flash-Sale Backend Roadmap

## Objective

Build and document a production-minded Java and Spring Boot flash-sale backend
that demonstrates concurrency control, transactions, idempotency, reliable
processing, observability, load testing, and failure testing.

The repository must become strong through working code and evidence—not through
unsupported scale or production-readiness claims.

## Evidence policy

Every important technical claim must be supported by one or more of:

- committed source code
- automated tests
- concurrent integration tests
- load-test output
- failure-test output
- logs or metrics
- documented environment and methodology

The scenario of 10,000 purchase attempts competing for 100 units is a planned
experiment. It is not currently an achieved benchmark.

## Seven-day completion sprint

Sprint dates: November 23-29, 2026.

Optional scope will be removed before correctness, testing, documentation, or
honest reporting is removed.

### Sprint Day 1 — Architecture and runnable foundation

- HLD version 1
- architecture decision records
- technology baseline
- Spring Boot skeleton
- PostgreSQL through Docker Compose
- Flyway foundation
- Actuator health endpoint
- GitHub Actions CI

### Sprint Day 2 — Domain model and database

- product, inventory, flash-sale, reservation, order, and payment concepts
- database schema and Flyway migrations
- product, inventory, and flash-sale administration APIs
- validation and database integration tests

### Sprint Day 3 — Reproduce and prevent overselling

- deliberately naive purchase implementation
- concurrent integration test
- captured overselling or lost-update evidence
- corrected PostgreSQL concurrency strategy
- passing no-overselling invariant test

### Sprint Day 4 — Idempotent purchase and payment flow

- reservation and order workflow
- legal and illegal state transitions
- purchase request idempotency
- simulated payment initiation
- simulated payment callback
- duplicate callback protection

### Sprint Day 5 — Expiry and reliable events

- reservation expiration
- inventory release
- transactional outbox
- outbox relay and retry behavior
- database-success/event-publication-failure experiment

Redis or Kafka may be introduced only if the completed PostgreSQL-backed
baseline demonstrates a concrete problem that justifies them.

### Sprint Day 6 — Observability, load testing, and failure testing

- structured logs
- correlation/request identifiers
- application metrics
- k6 workload scripts
- benchmark methodology and measured results
- database outage, duplicate callback, restart, and retry experiments

### Sprint Day 7 — Portfolio package

- final README
- architecture and data-model diagrams
- ADR index
- API examples
- setup guide
- final test and CI evidence
- interview notes
- case-study and YouTube material
- resume bullets based only on verified results

## Mandatory Version 1 scope

- modular monolith
- PostgreSQL as source of truth
- product and inventory management
- flash-sale window
- reservation and order workflow
- no-overselling protection
- request idempotency
- duplicate payment-callback protection
- reservation expiration and inventory release
- transactional outbox
- logs and metrics
- automated tests
- concurrency tests
- load tests
- failure tests
- GitHub Actions CI
- architecture and decision documentation

## Conditional scope

The following require a separate issue and ADR before introduction:

- Redis rate limiting
- Redis sold-out fast path
- Kafka event transport
- notification consumer
- Prometheus
- Grafana

## Definition of portfolio complete

Version 1 is complete when:

- required behavior is implemented
- correctness invariants have automated tests
- CI passes
- benchmark conditions and results are documented honestly
- failure scenarios are exercised
- limitations are documented
- architecture decisions are recorded
- milestone pull requests are merged
- repository documentation matches the implementation
