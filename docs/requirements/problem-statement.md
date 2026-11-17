# Problem Statement

## Status

Initial requirements baseline.

## Context

Flash sales create a high-contention purchasing problem.

A small and fixed quantity of inventory may be offered while many users try
to purchase at approximately the same time. A design that works correctly
for one request may fail when multiple requests read and update the same
inventory concurrently.

This project is an educational simulation. It will not initially integrate
with a real payment provider.

## Core problem

The backend must coordinate limited inventory, reservations, orders and
simulated payments without selling more units than are available.

It must also remain correct when:

- multiple buyers attempt to purchase simultaneously
- the same purchase request is submitted more than once
- a payment callback is delivered more than once
- a payment callback arrives late
- a reservation expires
- processing temporarily fails
- a component restarts
- an operator needs to investigate what happened

## Future workload scenario

A future test scenario will attempt to model:

- 10,000 purchase attempts
- 100 available units
- inventory never falling below zero
- at most 100 successful purchases
- duplicate requests being handled safely
- successful purchases remaining traceable
- failed processing being recoverable

The numbers above are a future test scenario. They are not measured results,
production traffic, user counts or performance guarantees.

## Correctness invariants

An invariant is a rule that must remain true even when requests overlap or
fail.

The initial invariants are:

1. Available inventory must never become negative.
2. Successful purchases must not exceed the available inventory.
3. Repeating the same request with the same idempotency identity must not
   create multiple purchases.
4. Repeating the same payment callback must not apply the payment twice.
5. Every successful purchase must be traceable through stored records.
6. Released or expired inventory must be accounted for correctly.
7. Illegal order-state transitions must be rejected.

These invariants describe required behavior. The implementation strategy
will be selected and tested in later phases.

## Initial scope

The completed project is expected to support:

- products
- inventory
- flash-sale windows
- purchase or reservation attempts
- orders
- simulated payment initiation
- simulated payment callbacks
- idempotency
- reservation expiry
- inventory release
- event publication
- notification simulation
- administrative visibility
- auditability
- operational metrics

## Initial out of scope

The foundation phase does not include:

- real payment-gateway integration
- production deployment
- microservices
- Kubernetes
- multi-region infrastructure
- unsupported scale claims
- unsupported availability claims
- unsupported throughput or latency claims

## Success criteria

The project succeeds when its important correctness, reliability and
performance claims are demonstrated through code, tests, failure experiments
and documented measurements rather than architectural diagrams alone.