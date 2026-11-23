# Cloud Development Workflow

## Source of truth

GitHub is the source of truth for:

- source code
- documentation
- scripts
- architecture diagrams
- tests
- issue history
- pull requests
- architecture decisions
- project progress

Work is not considered safely preserved until it has been committed, pushed
and verified on GitHub.

## Development environment

GitHub Codespaces is the default development environment.

The project does not require:

- a local project folder
- a local repository clone
- a local Java installation
- a local PostgreSQL installation
- a local Redis installation
- a local Kafka installation

Development takes place through browser-based VS Code inside a Codespace.

## Unit-of-work workflow

Each meaningful unit of work follows this sequence:

1. Create or select a GitHub issue.
2. Define explicit acceptance criteria.
3. Create a narrowly scoped feature branch.
4. Implement a small, reviewable change.
5. Add or update tests where applicable.
6. Run the relevant checks.
7. Review the diff.
8. Commit with a meaningful message.
9. Push the branch to GitHub.
10. Open a pull request.
11. Review the pull request.
12. Merge only after the acceptance criteria are satisfied.
13. Confirm that the related issue is closed.
14. Delete the feature branch when it is no longer needed.

## Branch naming

Branches should describe the type and scope of work.

Examples:

- `docs/issue-1-project-requirements`
- `design/issue-2-hld-v1`
- `feat/issue-3-spring-boot-skeleton`
- `test/issue-4-health-check-integration-test`

## Commit messages

Use meaningful prefixes such as:

- `feat:`
- `fix:`
- `test:`
- `docs:`
- `refactor:`
- `perf:`
- `chore:`

A commit should contain one understandable unit of work rather than unrelated
changes from an entire week.

## Pull-request review

Before merging, review:

- changed files
- acceptance criteria
- test and verification output
- accidental files
- unsupported claims
- credentials or secrets
- unrelated technology additions
- documentation accuracy

A solo self-review must be described honestly as a self-review. It must not
be represented as independent peer approval.

## End-of-session procedure

Before stopping or deleting a Codespace:

1. Run `git status`.
2. Run the relevant tests or checks.
3. Review the diff.
4. Commit intended work.
5. Push the current branch.
6. Verify the commit and branch on GitHub.
7. Update `docs/progress/PROJECT_STATE.md`.
8. Confirm that no secret or personal data was committed.
9. Only then stop or delete the Codespace.

## Secrets

Never commit:

- passwords
- tokens
- API keys
- private keys
- real database credentials
- personal customer data

Use environment variables, `.env.example` and GitHub repository secrets when
required.

## Architecture guardrails

The initial architecture is a modular monolith.

PostgreSQL is initially the source of truth.

Redis may be introduced only after a working database-backed baseline
demonstrates a real need.

Kafka may be introduced only after a genuine asynchronous communication or
reliable event-delivery problem has been demonstrated.

Kubernetes and unnecessary cloud infrastructure are out of scope.

Every major architecture decision must eventually be recorded as an ADR.

## Cost control

Free and open-source tooling is preferred.

Before enabling any resource that may incur charges, the expected cost and
free allowance must be reviewed.