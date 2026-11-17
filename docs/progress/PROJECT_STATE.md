# Current Project State

- Date: November 17, 2026
- Day number: 1
- Current phase: Days 1-7 — Foundation
- Current milestone: Define requirements and cloud development workflow

## Completed Today

- Created the public `codefather-flash-sale-backend` repository.
- Opened the repository in GitHub Codespaces.
- Verified the repository remote and `main` branch.
- Created Issue #1 with explicit acceptance criteria.
- Created and checked out `docs/issue-1-project-requirements`.
- Documented the problem statement.
- Documented the initial functional requirements.
- Documented the initial non-functional requirements.
- Documented the cloud-only development workflow.
- Updated the repository README.

## What I Learned

- Functional requirements describe what the system must do.
- Non-functional requirements describe qualities and correctness constraints.
- Requirements should be defined before selecting architecture.
- An invariant is a rule that must remain true during concurrency and failure.
- A workload scenario is not an achieved benchmark.
- A Git branch is not complete work until the change is reviewed and merged.

## GitHub Evidence

## GitHub Evidence

- Issue: #1 — Define project requirements and cloud development workflow
- Branch: `docs/issue-1-project-requirements`
- Pull request: #2
- Commit: `docs: define project requirements and cloud workflow`
- Tests run: `git diff --cached --check` and manual requirements review


## Current Architecture

- Documentation-first foundation.
- Modular monolith selected as the initial architecture direction.
- PostgreSQL selected as the initial source of truth.
- No application code has been generated.
- Redis and Kafka are deferred until a demonstrated need exists.
- Kubernetes and unnecessary cloud infrastructure are out of scope.

## Open Problems

- HLD version 1 has not been created.
- Exact compatible Java and Spring Boot versions have not been selected.
- The Spring Boot project has not been generated.
- PostgreSQL has not been configured.
- No automated tests or CI pipeline exist yet.
- No benchmark has been run.

## Decisions Made

- GitHub is the source of truth.
- GitHub Codespaces is the default development environment.
- No local project folder is required.
- Requirements will be documented before architecture and implementation.
- PostgreSQL correctness will be established before adding Redis.
- A real asynchronous problem must be demonstrated before adding Kafka.
- No measured performance or reliability result will be fabricated.

## YouTube Asset Produced

- Captured or planned screenshots of the repository, Issue #1, Codespace,
  feature branch, documentation tree and pull request.
- No long-form video has been published yet.
- Week 1 content will be based on completed foundation evidence rather than
  unsupported architecture claims.

## Next Session's First Task

Create Issue #2 for HLD version 1 and identify the system boundary, major
modules and primary request flow.

## Exact Resume Evidence Earned

No resume bullet yet. Repository and requirements setup are necessary project
evidence, but they are not yet sufficient for a technical achievement claim.