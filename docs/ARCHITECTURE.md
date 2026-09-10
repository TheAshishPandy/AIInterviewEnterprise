# Architecture

## System boundaries

```text
React Web App
    |
    v
Python API / Application Services
    |
    +--> Identity & Tenant Management
    +--> Interview Management
    +--> Question Bank & Rubrics
    +--> Candidate & Session Management
    +--> Evaluation & Analytics
    |
    v
AI Orchestration Layer
    |
    +--> Interviewer Agent
    +--> Question Generation Agent
    +--> Evaluation Agent
    +--> Feedback & Reporting Agent
    |
    +--> Provider adapters

Persistence / Integrations
    +--> MongoDB
    +--> Object Storage
    +--> Notification / Email providers
    +--> Optional ATS / HRIS integrations
```

## Backend principles

- Keep HTTP/API handlers thin and put business rules in application services.
- Keep domain models independent of infrastructure implementations.
- Put model-provider calls behind interfaces so AI providers can be swapped.
- Persist audit events for sensitive interview, score, and administrative actions.
- Enforce organization scope on every tenant-owned resource.

## AI agent responsibilities

### Interviewer Agent
Maintains interview state, selects the next question within policy, adapts difficulty, and keeps the session aligned to the interview template.

### Question Generation Agent
Creates or refines questions from competencies, job requirements, difficulty, and approved question policies.

### Evaluation Agent
Maps candidate evidence to rubric dimensions and produces structured scores plus supporting evidence.

### Feedback & Reporting Agent
Turns structured evaluation data into recruiter-ready summaries while preserving traceability to interview evidence.

## Security baseline

Authentication, authorization, organization isolation, input validation, secrets management, rate limiting, audit logging, and least-privilege service access are first-class concerns.
