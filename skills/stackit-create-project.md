---
name: stackit-create-project
description: Create and inspect a STACKIT project in the resource hierarchy
api: openapi/stackit-resource-manager-openapi.yml
operations:
- ListOrganizations
- ListFolders
- CreateProject
- GetProject
- PartialUpdateProject
generated: '2026-10-18'
method: generated
---

# Create and inspect a STACKIT project in the resource hierarchy

Grounded in `openapi/stackit-resource-manager-openapi.yml` (server https://resource-manager.api.stackit.cloud).

## Steps

1. List organizations with `ListOrganizations` to find the parent container.
2. Optionally list folders with `ListFolders` to choose a folder parent.
3. Create the project with `CreateProject` (name, parent containerId, members).
4. Poll `GetProject` until the lifecycle state is active.
5. Apply labels or rename with `PartialUpdateProject`.

## Rules

- Authenticate with a STACKIT service-account bearer token (`Authorization: Bearer ...`).
- Resources are scoped by `projectId` (and `region` where the path includes it).
- Provisioning is asynchronous: poll the GET operation rather than assuming success.
- No Idempotency-Key header is declared in the contract; do not blindly retry POST creates — check with the list/get operation first.
- Delete operations are destructive; confirm with a human first.
