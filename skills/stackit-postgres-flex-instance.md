---
name: stackit-postgres-flex-instance
description: Provision a PostgreSQL Flex instance with a database and user
api: openapi/stackit-postgres-flex-openapi.yml
operations:
- ListFlavors
- ListVersions
- CreateInstance
- GetInstance
- CreateUser
- CreateDatabase
generated: '2026-10-18'
method: generated
---

# Provision a PostgreSQL Flex instance with a database and user

Grounded in `openapi/stackit-postgres-flex-openapi.yml` (server https://postgres-flex-service.api.stackit.cloud).

## Steps

1. Choose a flavor with `ListFlavors` and a version with `ListVersions`.
2. Create the instance with `CreateInstance`.
3. Poll `GetInstance` until the instance is ready.
4. Create a user with `CreateUser` (password returned in the response).
5. Create a database with `CreateDatabase` owned by that user.

## Rules

- Authenticate with a STACKIT service-account bearer token (`Authorization: Bearer ...`).
- Resources are scoped by `projectId` (and `region` where the path includes it).
- Provisioning is asynchronous: poll the GET operation rather than assuming success.
- No Idempotency-Key header is declared in the contract; do not blindly retry POST creates — check with the list/get operation first.
- Delete operations are destructive; confirm with a human first.
