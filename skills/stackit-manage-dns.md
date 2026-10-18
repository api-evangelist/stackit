---
name: stackit-manage-dns
description: Create a DNS zone and record sets in STACKIT DNS
api: openapi/stackit-dns-openapi.yml
operations:
- CreateZone
- GetZone
- CreateRecordSet
- ListRecordSets
- PartialUpdateRecordSet
generated: '2026-10-18'
method: generated
---

# Create a DNS zone and record sets in STACKIT DNS

Grounded in `openapi/stackit-dns-openapi.yml` (server https://dns.api.stackit.cloud).

## Steps

1. Create the zone with `CreateZone`.
2. Poll `GetZone` until the zone state is CREATE_SUCCEEDED.
3. Add records with `CreateRecordSet`.
4. List with `ListRecordSets`; edit with `PartialUpdateRecordSet`.

## Rules

- Authenticate with a STACKIT service-account bearer token (`Authorization: Bearer ...`).
- Resources are scoped by `projectId` (and `region` where the path includes it).
- Provisioning is asynchronous: poll the GET operation rather than assuming success.
- No Idempotency-Key header is declared in the contract; do not blindly retry POST creates — check with the list/get operation first.
- Delete operations are destructive; confirm with a human first.
