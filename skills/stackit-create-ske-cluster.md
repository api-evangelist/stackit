---
name: stackit-create-ske-cluster
description: Create a STACKIT Kubernetes Engine (SKE) cluster and fetch a kubeconfig
api: openapi/stackit-ske-openapi.yml
operations:
- ListProviderOptions
- CreateOrUpdateCluster
- GetCluster
- CreateKubeconfig
- ListClusters
generated: '2026-10-18'
method: generated
---

# Create a STACKIT Kubernetes Engine (SKE) cluster and fetch a kubeconfig

Grounded in `openapi/stackit-ske-openapi.yml` (server https://ske.api.stackit.cloud).

## Steps

1. Read supported Kubernetes versions, machine types and zones with `ListProviderOptions`.
2. Create the cluster with `CreateOrUpdateCluster` (PUT on clusterName: idempotent by name).
3. Poll `GetCluster` until status reports the cluster healthy.
4. Issue a kubeconfig with `CreateKubeconfig`.
5. Verify with `ListClusters`.

## Rules

- Authenticate with a STACKIT service-account bearer token (`Authorization: Bearer ...`).
- Resources are scoped by `projectId` (and `region` where the path includes it).
- Provisioning is asynchronous: poll the GET operation rather than assuming success.
- No Idempotency-Key header is declared in the contract; do not blindly retry POST creates — check with the list/get operation first.
- Delete operations are destructive; confirm with a human first.
