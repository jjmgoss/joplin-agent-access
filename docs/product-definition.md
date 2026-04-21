# Product Definition

## Problem statement

Joplin is the user's personal notes system, but agentic tools should not be given raw access to synced storage, unrestricted destructive powers, or direct dependency on Joplin internals. This project creates a controlled integration layer that allows safe note search and limited note creation while preserving portability and future flexibility.

## Goals

- Provide safe note search for agent workflows
- Provide a limited note-creation path into an allowlisted notebook
- Keep Joplin as the system of record
- Avoid raw WebDAV or filesystem access for agents
- Support future reuse by different agent runtimes or model providers
- Preserve portability and reproducibility

## Non-goals

- No generalized personal control plane in the first milestone
- No direct WebDAV manipulation
- No broad update/delete access in Phase 1
- No public internet exposure in the initial milestone
- No attempt to replace Joplin

## Initial user stories

- As the owner, I want an agent to search my notes for relevant context
- As the owner, I want an agent to create a new note in a designated notebook without modifying arbitrary existing notes
- As the owner, I want all note actions to be logged and constrained by policy
- As the owner, I want the integration boundary to remain stable even if I later change agent frameworks or hosting patterns

## Risks and trust concerns

- Direct exposure of Joplin API would provide too much capability
- Direct storage access would couple the system to the wrong layer
- Agent writes without auditability would be hard to trust
- Early overengineering could delay proof of value

## Phase 1 success

Phase 1 is successful when a local service can reliably:
- connect to Joplin Data API
- search notes
- return note content in a controlled way
- create a note only in an allowlisted notebook
- deny unsafe operations by default
- emit audit logs for all requests
