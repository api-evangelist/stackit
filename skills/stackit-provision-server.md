---
name: stackit-provision-server
description: Provision a virtual server with network, security group and public IP
  on STACKIT IaaS
api: openapi/stackit-iaas-openapi.yml
operations:
- CreateNetwork
- CreateSecurityGroup
- CreateServer
- GetServer
- CreatePublicIP
- AddPublicIpToServer
- ListServers
generated: '2026-10-18'
method: generated
---

# Provision a virtual server with network, security group and public IP on STACKIT IaaS

Grounded in `openapi/stackit-iaas-openapi.yml` (server https://iaas.api.stackit.cloud).

## Steps

1. Create a network with `CreateNetwork` (projectId, region).
2. Create a security group with `CreateSecurityGroup` for ingress rules.
3. Create the server with `CreateServer` (machine type, image/boot volume, networking).
4. Poll `GetServer` until the server status is ACTIVE.
5. Allocate an address with `CreatePublicIP` and attach it with `AddPublicIpToServer`.
6. Confirm with `ListServers`.

## Rules

- Authenticate with a STACKIT service-account bearer token (`Authorization: Bearer ...`).
- Resources are scoped by `projectId` (and `region` where the path includes it).
- Provisioning is asynchronous: poll the GET operation rather than assuming success.
- No Idempotency-Key header is declared in the contract; do not blindly retry POST creates — check with the list/get operation first.
- Delete operations are destructive; confirm with a human first.
