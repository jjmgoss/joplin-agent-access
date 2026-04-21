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

## Future evolution

The gateway should be designed so that it can later sit behind:
- private remote access for the owner
- authenticated public integration for tightly scoped external tools
- alternate agent runtimes or tool protocols

That future should not change the core service contract or trust boundary.
