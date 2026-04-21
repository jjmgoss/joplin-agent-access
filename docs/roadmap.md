# Roadmap

## Phase 0 - Proof of concept

- Verify local access to Joplin Data API
- Implement a minimal client
- Search notes successfully
- Create a note in a designated notebook
- Keep writes narrow and explicit

## Phase 1 - Reproducible local service

- Create minimal service wrapper around Joplin client
- Add configuration via environment variables
- Add smoke test path
- Add audit logging
- Add basic tests around policy enforcement
- Document setup and operations

## Phase 2 - Safer controlled writes

- Improve write policy and provenance metadata
- Add stronger validation around note creation
- Introduce better caller identity and request context
- Improve operational observability

## Later phases

- Private remote access for the owner
- Public authenticated integration mode if justified
- Additional tool protocols or adapters
- Carefully scoped update flows if truly needed

## Anti-goals for early phases

- No generalized platformization
- No direct raw-storage integration
- No broad destructive operations
- No internet exposure as a blocker for initial value
