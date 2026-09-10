# Backend

Python API/application layer placeholder.

Recommended module boundaries:

- `api/` — HTTP routes and request/response schemas.
- `application/` — use cases and orchestration.
- `domain/` — tenant, interview, candidate, evaluation, and rubric models.
- `infrastructure/` — MongoDB repositories, external integrations, and AI provider adapters.
- `tests/` — unit and integration tests.

The backend should expose versioned APIs and keep provider-specific AI code outside the domain layer.
