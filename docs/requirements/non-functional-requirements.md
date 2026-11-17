# Non-Functional Requirements

## Status

Initial non-functional-requirements baseline.

No numeric latency, throughput, availability or scale target is considered
achieved until it has been tested under documented conditions.

## Requirements

### NFR-001 — No overselling

The system must preserve the invariant that inventory does not fall below
zero and that successful purchases do not exceed available inventory.

### NFR-002 — Request idempotency

Retries and duplicate client submissions must not create duplicate business
effects when they share the same valid idempotency identity.

### NFR-003 — Duplicate callback and event handling

Duplicate payment callbacks and duplicate event deliveries must be safe.

### NFR-004 — Defined consistency boundaries

The project must document which operations require strong consistency and
where eventual consistency is acceptable.

### NFR-005 — Transaction management

Transaction boundaries must be explicit, tested and documented.

### NFR-006 — Recoverable failures

Temporary failures must not silently lose inventory, orders, payments or
events. Recovery behavior and remaining limitations must be documented.

### NFR-007 — Concurrency control

Shared inventory updates must use a concurrency-control strategy that is
demonstrated with concurrent tests.

### NFR-008 — Rate limiting and traffic control

The project must eventually evaluate traffic-control mechanisms without
allowing them to become the source of business correctness.

### NFR-009 — Observability

Important requests and business transitions must eventually be observable
through useful logs, request or correlation identifiers and metrics.

### NFR-010 — Performance measurement

Performance claims must include the workload, environment, methodology and
limitations under which they were measured.

### NFR-011 — Testability

Important behavior must be testable using unit, integration, concurrency,
failure and load tests where appropriate.

### NFR-012 — Maintainability

The codebase must use clear module boundaries, understandable naming and
documented architectural decisions without unnecessary abstraction.

### NFR-013 — Security basics

External input must be validated, secrets must not be committed and
authorization boundaries must be reviewed before exposing administrative
operations.

### NFR-014 — Auditability

The system must retain enough durable information to reconstruct important
order, reservation, inventory and payment transitions.

### NFR-015 — Documented trade-offs

Major design decisions must explain their benefits, costs, alternatives and
remaining limitations.

## Evidence policy

No claim such as "production scale," "highly available," "handles 10,000
concurrent users" or "zero data loss" may be made without supporting
experiments and documented evidence.