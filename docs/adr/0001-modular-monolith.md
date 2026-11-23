# ADR 0001: Begin as a Modular Monolith

## Status

Accepted.

## Date

November 23, 2026.

## Context

The project must model inventory contention, reservations, orders, payment
callbacks, retries, and event delivery.

Starting with separate network services would add deployment, communication,
tracing, consistency, and operational complexity before the business
invariants have been implemented or tested.

The project needs clear business boundaries without premature distributed
deployment.

## Decision

Build one Spring Boot application organized as a modular monolith.

Initial logical modules:

- catalog
- inventory
- flashsale
- reservation
- order
- payment
- outbox
- notification
- shared
- infrastructure

Each module owns its business responsibility and persistence changes.

Modules communicate through explicit application interfaces. Domain logic
must not depend directly on controllers, database drivers, or external
transport details.

All modules are built, tested, and deployed together during Version 1.

## Consequences

### Positive

- Business invariants can be protected with local database transactions.
- Refactoring across modules is inexpensive.
- Codespaces and CI require fewer moving parts.
- Concurrency can be studied without network noise.
- Logs, debugging, and integration testing remain straightforward.
- Business boundaries remain visible.

### Negative

- One application failure can affect every module.
- All modules initially scale together.
- Poor package discipline could create hidden coupling.
- Transactions may span multiple logical modules.
- Future extraction requires deliberate ownership discipline.

## Guardrails

- Package by business capability.
- Do not access another module's repository merely for convenience.
- Keep transaction orchestration in application services.
- Do not create empty abstraction layers.
- Record exceptions to ownership rules.
- Do not call the modules microservices.
- Do not add network boundaries without measured justification.

## Alternatives considered

### Microservices from the beginning

Rejected because the project has not demonstrated independent scaling,
deployment, availability, or ownership requirements that justify distributed
complexity.

### Traditional layered monolith

Not selected as the primary structure because global controller, service, and
repository folders group code by technical layer rather than business
capability.

### Serverless functions

Rejected because the core workflow depends on coordinated transactional state,
controlled concurrency, and repeatable failure experiments.

## Revisit conditions

Revisit this decision only if evidence demonstrates that a module requires:

- independent scaling
- independent deployment
- a different availability boundary
- a separate data-ownership boundary
- organizational ownership that cannot be handled in one application
