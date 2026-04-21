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

### Preferred Phase 1 execution batches

#### Batch A - Design lock and trust boundary

Issues:
- #1 Define the external service contract for Phase 1
- #2 Document the Phase 1 trust model and policy defaults
- #11 Choose the first service transport shape for local callers
- #9 Research and document the future remote-access posture

Notes:
- Use a premium model for this batch
- Stop for product approval at the end of the batch

#### Batch B - Repo scaffold and Joplin substrate

Issues:
- #10 Create the initial Python project skeleton and local development layout
- #3 Implement a minimal Joplin Data API client
- #12 Implement notebook resolution and allowlisted write-target enforcement
- #15 Document Joplin local setup prerequisites for Phase 1 development

Notes:
- Prefer an included lower-cost model such as GPT-4.1 for this batch
- Only stop early if blocked by missing local configuration or missing product information

#### Batch C - Service MVP

Issues:
- #4 Implement the Phase 1 policy layer for allowed and denied operations
- #5 Stand up the first local service wrapper around the Joplin client
- #14 Implement response shaping and result-limiting for note search and reads
- #6 Add audit logging for all service actions
- #13 Define and implement provenance metadata for agent-created notes

Notes:
- Use a premium model for this batch
- Stop for product approval after the first working end-to-end slice

#### Batch D - Closure and hardening

Issues:
- #7 Create a reproducible local configuration and smoke-test path
- #8 Add initial tests for policy enforcement and critical flows
- #16 Add repo labels and organize the backlog by implementation area

Notes:
- Prefer an included lower-cost model such as GPT-4.1 for this batch
- This batch should close out Phase 1 unless tests reveal a deeper product or architecture issue

### Autonomous execution guidance

The preferred autonomous unit of work is a batch, not the entire Phase 1 roadmap.

For each batch, the agent should:
- read all issues in the batch and relevant docs
- implement the batch on a working branch
- commit incrementally
- validate behavior before pushing
- update each issue with implementation notes
- close only the issues whose acceptance criteria are clearly met
- post one batch summary before stopping

### Natural approval gates

Approval is expected:
- after Batch A
- after Batch C
- before any change that expands trust boundaries, internet exposure, auth complexity, or destructive capabilities

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
