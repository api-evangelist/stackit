---
name: stackit-create-and-manage-application-load-balancer
description: Create and manage an Application Load Balancer with observability credentials in a project.
api: openapi/stackit-alb-openapi.yml
operations:
- GetQuota
- CreateCredentials
- CreateLoadBalancer
- GetLoadBalancer
- UpdateTargetPool
generated: '2026-10-18'
method: generated
generator: extract-docs-artifacts.py skills (deepseek)
source: openapi/stackit-alb-openapi.yml ; every operationId checked against the contract
---

# stackit-create-and-manage-application-load-balancer

Create and manage an Application Load Balancer with observability credentials in a project.

## Steps

1. 1. Check quota availability using `GetQuota` with `projectId` and `region` path parameters
2. 2. Create observability credentials using `CreateCredentials` with `projectId` and `region` path parameters and credentials data in the request body
3. 3. Create the load balancer using `CreateLoadBalancer` with `projectId` and `region` path parameters and load balancer configuration in the request body
4. 4. Retrieve the created load balancer details using `GetLoadBalancer` with `projectId`, `region`, and `name` path parameters
5. 5. Update target pool configuration using `UpdateTargetPool` with `projectId`, `region`, `name`, and `targetPoolName` path parameters and target pool data in the request body

## Rules

- Authentication required via authorization header
- All operations require projectId and region path parameters
- Create operations are not idempotent - duplicate requests create new resources
- GET operations support pagination for listing multiple resources
