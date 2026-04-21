# Joplin Agent Access

A narrow, policy-controlled gateway for allowing agentic systems to search and write to a Joplin notes environment without granting raw storage access or broad destructive capabilities.

## Purpose

This project exists to create a durable integration layer between Joplin and future agent workflows.

The first milestone is intentionally small:
- search notes safely
- fetch note content in a controlled way
- create new notes only in a designated agent-owned notebook
- log all actions

## Scope

This is not a generalized personal control plane.
It is a focused notes integration service that can later plug into a broader self-hosted agent ecosystem.

## Initial architecture

- Joplin remains the system of record
- Joplin Data API is the backend integration substrate
- This service acts as a thin policy and control layer
- Agents interact with this service, not with raw WebDAV storage or direct note files

## Planned repository structure

- `README.md`
- `docs/product-definition.md`
- `docs/architecture.md`
- `docs/trust-model.md`
- `docs/roadmap.md`
- service code to be added after design and issue setup

## Phase 1 success

Phase 1 is successful when a locally running service can:
1. connect to Joplin through the local Data API
2. search notes safely
3. create a note only in a designated notebook such as `Agent Inbox`
4. deny unsafe operations by default
5. produce audit logs for all actions
