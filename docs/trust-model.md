# Trust Model

## Core principle

Agents must not receive raw or unrestricted access to note storage or broad note mutation capabilities.

## Trust boundary

The gateway is the enforcement boundary.

- Joplin token is held by the gateway
- Agents call the gateway
- Agents do not access WebDAV storage directly
- Agents do not call Joplin Data API directly in the intended design

## Default policy

Allowed in Phase 1:
- search notes
- fetch note content in a controlled way
- create new note only in designated notebook

Denied in Phase 1:
- update existing notes
- delete notes
- move notes between notebooks
- tag mutation
- attachment upload
- broad notebook enumeration unless explicitly needed

## Logging requirements

Every request should record:
- timestamp
- caller identity if available
- action requested
- target note or notebook if applicable
- outcome
- error details if failed

## Safety posture

- deny by default
- keep write scope narrow
- preserve provenance for agent-created notes
- optimize for reversibility and auditability
