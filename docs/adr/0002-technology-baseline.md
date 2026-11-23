# ADR 0002: Select the Initial Technology Baseline

## Status

Accepted.

## Date

November 23, 2026.

## Decision

Use this initial baseline:

| Concern | Selection |
|---|---|
| Language | Java 21 using an OpenJDK distribution |
| Application framework | Spring Boot 4.1.3 |
| Build | Maven 3.10.2 through Maven Wrapper |
| Database | PostgreSQL 18.7 |
| Migrations | Flyway |
| Unit and integration tests | JUnit 5 |
| Database integration tests | Testcontainers |
| Development database | Docker Compose inside GitHub Codespaces |
| CI | GitHub Actions |
| Architecture diagrams | Mermaid |
| Load testing | k6 |
| Health and metrics | Spring Boot Actuator and Micrometer |

Framework-managed dependency versions will be used where practical. Individual
library versions will not be overridden without a documented compatibility or
security reason.

## Java rationale

Java 21 is a long-term-support release and is within the supported Java range
of the selected Spring Boot line.

An OpenJDK distribution will be used so that the project does not depend on a
proprietary JDK distribution.

## Spring Boot rationale

Spring Boot 4.1.3 is selected as a stable patch release in the 4.1 line.

Spring Boot 4.2.0 was considered but is a newly released feature line at the
time of this decision. The project prefers the stable 4.1 patch line during
its compressed implementation sprint.

## Maven rationale

Maven is selected because:

- the project requirements identify Maven
- it provides repeatable lifecycle commands
- Maven Wrapper removes dependence on a globally installed Maven version
- it integrates directly with Spring Boot and GitHub Actions

Maven 4 is not selected because it remains a preview rather than a generally
available production release.

## PostgreSQL rationale

PostgreSQL provides:

- transactions
- row-level locking
- unique constraints
- conditional updates
- indexes
- durable state
- isolation controls
- strong support for concurrency experiments

PostgreSQL 18.7 is selected instead of PostgreSQL 19 because version 19 was
released only days before this decision. The project prefers the supported,
established 18 release line during the seven-day sprint.

## Flyway rationale

Database changes must be reproducible in Codespaces, CI, and integration tests.

Flyway provides ordered and reviewable schema migrations.

## Testcontainers rationale

Persistence and concurrency behavior must be tested against a real PostgreSQL
engine rather than an in-memory database with different SQL or locking
behavior.

## Deferred technologies

### Redis

Redis is deferred until the PostgreSQL-backed baseline demonstrates a real
need such as:

- traffic throttling
- sold-out short-circuiting
- a carefully defined cache
- reduced load on a measured hot path

Redis will never become the sole authority for inventory correctness.

### Kafka

Kafka is deferred until a genuine asynchronous delivery problem has been
implemented and demonstrated.

The transactional outbox will be designed before selecting Kafka as an event
transport.

### Kubernetes

Kubernetes is explicitly out of scope. The project does not currently have a
deployment-orchestration problem that justifies it.

## Consequences

### Positive

- Mutually compatible, current core technologies.
- Repeatable cloud-only development.
- Real PostgreSQL concurrency behavior.
- Limited infrastructure during the correctness phase.
- Fewer manually pinned dependencies.

### Negative

- Spring Boot 4 uses a newer framework generation.
- Java 21 does not demonstrate Java 25-specific features.
- PostgreSQL 18 omits PostgreSQL 19-specific features.
- Docker-backed tests are slower than in-memory tests.

These trade-offs are acceptable for a correctness-first portfolio project.

## Upgrade policy

- Do not silently upgrade Java, Spring Boot, Maven, or PostgreSQL.
- Open a separate issue for a baseline upgrade.
- Record motivation and compatibility evidence.
- Run the full test suite before merging.
- Update or supersede this ADR.

## Official references

- Spring Boot documentation: https://docs.spring.io/spring-boot/
- Spring Boot 4.1.3 release: https://spring.io/blog/2026/11/20/spring-boot-4-1-3-available-now/
- Java support roadmap: https://www.oracle.com/java/technologies/java-se-support-roadmap.html
- Apache Maven downloads: https://maven.apache.org/download.cgi
- PostgreSQL versioning: https://www.postgresql.org/support/versioning/
