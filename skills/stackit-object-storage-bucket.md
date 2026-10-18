---
name: stackit-object-storage-bucket
description: Enable Object Storage, create a bucket and issue S3 access keys
api: openapi/stackit-object-storage-openapi.yml
operations:
- EnableService
- GetServiceStatus
- CreateCredentialsGroup
- CreateAccessKey
- CreateBucket
- ListBuckets
generated: '2026-10-18'
method: generated
---

# Enable Object Storage, create a bucket and issue S3 access keys

Grounded in `openapi/stackit-object-storage-openapi.yml` (server https://object-storage.api.stackit.cloud).

## Steps

1. Enable Object Storage for the project with `EnableService` and check with `GetServiceStatus`.
2. Create a credentials group with `CreateCredentialsGroup`.
3. Create S3 access keys with `CreateAccessKey` (the secret is only returned once).
4. Create a bucket with `CreateBucket` and confirm with `ListBuckets`.

## Rules

- Authenticate with a STACKIT service-account bearer token (`Authorization: Bearer ...`).
- Resources are scoped by `projectId` (and `region` where the path includes it).
- Provisioning is asynchronous: poll the GET operation rather than assuming success.
- No Idempotency-Key header is declared in the contract; do not blindly retry POST creates — check with the list/get operation first.
- Delete operations are destructive; confirm with a human first.
