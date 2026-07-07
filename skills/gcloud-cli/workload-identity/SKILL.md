---
name: gcloud-workload-identity
description: >-
  Workload Identity via gcloud (`gcloud workload-identity`). Manage Workload Identity — service-agents.
---

# gcloud workload-identity — Workload Identity

## Overview

The `gcloud workload-identity` group manages Workload Identity. Its GA surface currently contains a single subgroup, `service-agents`, with one command: `generate`, which creates (provisions) the service agents for a specified service producer (API endpoint, e.g. `bigquery.googleapis.com`) on a project, folder, or organization at a given location. Service agents are Google-managed service accounts that let a Google Cloud service access your resources on your behalf; some services require their service agents to exist (and hold roles) before you use certain features. The IAM guide "Create and grant roles to service agents" documents this command as the way to trigger service agent creation for each endpoint and resource you identified — the command's response lists each service agent's email address and the roles you should then grant it. It sits alongside the broader IAM workload identities family (workload identity federation, managed workload identities).

## Quick reference — common workflows

### 1. Generate service agents for a service in a project

```bash
gcloud workload-identity service-agents generate \
    --service="bigquery.googleapis.com" \
    --location="global" \
    --project="123456"
```

### 2. Generate service agents for a service in a folder

```bash
gcloud workload-identity service-agents generate \
    --service="bigquery.googleapis.com" \
    --location="global" \
    --folder="123456"
```

### 3. Generate service agents for a service in an organization

```bash
gcloud workload-identity service-agents generate \
    --service="bigquery.googleapis.com" \
    --location="global" \
    --organization="123456"
```

### 4. Record the output, then grant the listed roles to each service agent

```bash
# The generate response lists each created service agent's email address and
# the roles to grant. Grant them, e.g.:
gcloud projects add-iam-policy-binding PROJECT_ID \
    --member="serviceAccount:SERVICE_AGENT_EMAIL" \
    --role="ROLE_FROM_RESPONSE"
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `workload-identity service-agents` | [`service-agents.md`](service-agents.md) | 1 | manage Service Agents for Workload Identity |

See [`index.md`](index.md) for a one-line index of the 1 command.

## Common flags & tips

- **`--service` is required** — the service producer to generate service agents for, given as the API endpoint (e.g. `bigquery.googleapis.com`, `aiplatform.googleapis.com`).
- **Exactly one parent resource is required:** `--project`, `--folder`, or `--organization`, each taking the *number* of the resource (e.g. `123456`).
- **`--location` defaults to `global`.** Supply it explicitly if the service documents regional service agents.
- **Review the response.** Each run returns the service agent(s) created for that endpoint/resource, including the email address to grant roles to; the roles are not granted automatically — grant them yourself (e.g. with `gcloud projects add-iam-policy-binding`).
- **Run per endpoint and per resource.** The IAM guide has you invoke the command once for each endpoint and resource you identified as needing service agents.

## beta / alpha

Both `gcloud beta workload-identity` and `gcloud alpha workload-identity` surfaces exist and mirror the same structure — a single `service-agents` group with the `generate` command — with no documented beta/alpha-only additions. Pre-GA tracks may change without notice.

## Official documentation

- **Create and grant roles to service agents:** https://docs.cloud.google.com/iam/docs/create-service-agents — the IAM guide that documents `gcloud workload-identity service-agents generate`.
- **Identities for workloads:** https://docs.cloud.google.com/iam/docs/workload-identities — overview of workload identity options on Google Cloud.
- **Managed workload identities overview:** https://docs.cloud.google.com/iam/docs/managed-workload-identity — X.509/SPIFFE-based managed workload identities for GKE and Compute Engine.
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/workload-identity — the `gcloud workload-identity` command group.
