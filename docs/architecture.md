# Architecture Notes

## High-level shape

- Joplin is the system of record
- Joplin Data API is the integration substrate
- A thin local gateway sits in front of Joplin
- Agent callers interact with the gateway, not with Joplin directly
- The gateway enforces policy, logging, and future portability

## Initial deployment model

Phase 1 is local-only:
- Joplin desktop runs locally
- Joplin Data API is enabled locally
- Gateway service runs on the same trusted machine
- No public internet exposure in initial milestone

## Initial allowed operations

- search notes
- fetch note content by id
- create note only in allowlisted notebook

## Initial denied operations

- update arbitrary notes
- delete notes
- notebook management
- attachment writes
- raw storage access

## Preferred autonomous implementation shape

This project should be implemented in bounded batches rather than as a single open-ended autonomous run.

Why:
- Phase 1 has natural design and trust-boundary checkpoints
- batching reduces orchestration churn and makes validation easier
- approval should happen only at meaningful product gates rather than after every small issue

Expected stop points:
- after design lock and trust-boundary decisions
- after the first working end-to-end local service slice
- before any expansion of trust boundaries, auth complexity, or internet exposure

Expected autonomous behavior within a batch:
- read the relevant issues and docs first
- work on a single branch for the batch
- commit incrementally
- validate before pushing
- document implementation in issue comments
- close only the issues that clearly meet acceptance criteria

## Future evolution

The gateway should be designed so that it can later sit behind:
- private remote access for the owner
- authenticated public integration for tightly scoped external tools
- alternate agent runtimes or tool protocols

That future should not change the core service contract or trust boundary.
