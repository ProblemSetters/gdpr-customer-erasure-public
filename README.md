# GDPR customer erasure task

This repository is a public reference implementation of a long horizon software engineering task. The task asks an agent to add customer data erasure to a brownfield payments platform while preserving financial records, tenant isolation, retry safety and service behavior.

The task is designed for behavior-based evaluation. The candidate sees the task instruction and incomplete PayFlow codebase. The evaluator runs the application in an isolated environment and checks the resulting behavior against the contract.

## Repository structure

```text
tasks/task.toml                 Task metadata
tasks/instruction.md            Candidate-facing instruction
codebase/                       Incomplete candidate application
environment/                    Reproducible Docker environments
verifier/                       Acceptance criteria, scoring and checks
reference_solution/             Complete reference implementation metadata
app-setup-starter/              Application setup contract
schemas/                        Task and scoring schemas
readiness_checks/               Package and verifier checks
scripts/                        Local packaging and validation utilities
```

## What the task tests

- Multi-service data erasure across PostgreSQL, Redis, OpenSearch, object storage and email
- Preservation of financial facts while removing personal data
- Idempotency, retries, delayed work and replay suppression
- Tenant isolation and authorization
- API compatibility and observable completion semantics
- Partial-credit scoring across independent behavioral criteria

## Local use

Use the task metadata and instruction under `tasks/`. The verifier entry point is `verifier/run.py`; the detailed checks and scoring manifest are in `verifier/`. The reference implementation is retained for understanding the intended behavior and for local calibration.

This repository intentionally excludes model trajectories, benchmarking runs, telemetry, generated dashboards, provider credentials and internal platform configuration. All credentials used by local fixtures are synthetic development values.

## Harbor relationship

The repository follows the broad Harbor and Terminal-Bench task shape: task instruction, task metadata, a pinned environment, a solution or reference implementation, tests and a reward-producing verifier. It uses the Astra task layout, so the manifest is under `tasks/task.toml` rather than at the repository root.

## License and use

This repository is shared as a reference for designing and evaluating software engineering environments. Review the repository and dependency licenses before incorporating any component into another benchmark or product.
