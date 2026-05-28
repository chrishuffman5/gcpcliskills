# gcloud policy-troubleshoot — Policy Troubleshooter

## Overview

Policy Troubleshooter (part of the Policy Intelligence suite) answers the question "why does — or doesn't — this principal have permission X on resource Y?" `gcloud policy-troubleshoot iam` evaluates a resource's effective IAM policy interpretation (allow policies, deny policies, and principal access boundary policies along the resource hierarchy) and reports whether a given permission is granted to a given principal, plus the bindings that produced that result. Reach for it when an engineer is unexpectedly denied (or unexpectedly allowed) access and you need to see exactly which policy binding is responsible.

## Quick reference — common workflows

### Enable the API

```bash
gcloud services enable policytroubleshooter.googleapis.com
```

Basic troubleshooting also requires `roles/iam.securityReviewer` (granted on the organization that contains the target resource) at minimum; deny-policy and principal-access-boundary checks need additional roles (`roles/iam.denyReviewer`, `roles/iam.principalAccessBoundaryViewer`).

### Check whether a user has a permission on a project

```bash
gcloud policy-troubleshoot iam \
    //cloudresourcemanager.googleapis.com/projects/PROJECT_ID \
    --principal-email=user@example.com \
    --permission=resourcemanager.projects.get
```

The positional `RESOURCE` is the full resource name (note the leading `//`); see the resource-names doc below for the format per service.

### Troubleshoot access to a Cloud Storage bucket

```bash
gcloud policy-troubleshoot iam \
    //storage.googleapis.com/projects/_/buckets/MY_BUCKET \
    --principal-email=user@example.com \
    --permission=storage.objects.get
```

### Troubleshoot a service account's access to a Compute Engine instance

```bash
gcloud policy-troubleshoot iam \
    //compute.googleapis.com/projects/PROJECT_ID/zones/ZONE/instances/INSTANCE_ID \
    --principal-email=my-sa@PROJECT_ID.iam.gserviceaccount.com \
    --permission=compute.instances.get
```

Only Google Accounts and service accounts are supported for `--principal-email`.

### Evaluate a conditional (time-based) binding

```bash
gcloud policy-troubleshoot iam \
    //cloudresourcemanager.googleapis.com/projects/PROJECT_ID \
    --principal-email=user@example.com \
    --permission=resourcemanager.projects.get \
    --request-time=2025-06-01T12:00:00Z
```

### Evaluate full conditional context (IP, port, resource attributes)

```bash
gcloud policy-troubleshoot iam \
    //compute.googleapis.com/projects/PROJECT_ID/zones/ZONE/instances/INSTANCE_ID \
    --principal-email=user@example.com \
    --permission=compute.instances.get \
    --destination-ip=198.1.1.1 \
    --destination-port=443 \
    --resource-type=compute.googleapis.com/Instance \
    --resource-service=compute.googleapis.com \
    --resource-name=//compute.googleapis.com/projects/PROJECT_ID/zones/ZONE/instances/INSTANCE_ID
```

The `--destination-*` and `--resource-*` flags supply the request attributes used to evaluate IAM Conditions; they only affect the result when the policy contains conditional bindings.

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `policy-troubleshoot` (top-level) | [`_commands.md`](_commands.md) | 1 | `iam` — check a principal's permission on a resource against the effective IAM policy |

See [`index.md`](index.md) for the one-line index of the (single) GA command.

## Common flags & tips

- **Required flags.** Every invocation needs the positional `RESOURCE`, `--permission` (e.g. `resourcemanager.projects.get`), and `--principal-email`.
- **Resource name format.** `RESOURCE` must be a *full* resource name beginning with `//` (e.g. `//cloudresourcemanager.googleapis.com/projects/PROJECT_ID`, `//storage.googleapis.com/projects/_/buckets/BUCKET`). The format differs per service — consult the resource-names reference below.
- **Conditional-binding context.** `--request-time` (RFC 3339, e.g. `2021-01-01T00:00:00Z`), `--destination-ip`, `--destination-port`, `--resource-name`, `--resource-service`, and `--resource-type` populate the request attributes used to evaluate IAM Conditions. They are optional and only change the outcome when conditional bindings are present.
- **Principals.** Only Google Accounts and service accounts are accepted by `--principal-email`; groups and other principal types are not supported as the subject of the check.
- **Output / format.** The command prints the access state plus the explaining bindings; use the global `--format` to script results, e.g. `--format='value(access)'` or `--format=json` to capture the full explanation.
- **Where to grant roles.** Troubleshooting roles must be held on the organization that contains the target resource, not merely on the project.

## beta / alpha

The same `iam` subcommand exists on all three release tracks — `gcloud policy-troubleshoot iam` (GA), `gcloud beta policy-troubleshoot iam`, and `gcloud alpha policy-troubleshoot iam` — with identical flags. The beta and alpha forms add no distinct flags or capabilities (both carry the "might change without notice" caveat). Use the GA form for production scripts.

## Official documentation

- [Policy Intelligence overview](https://cloud.google.com/policy-intelligence/docs/overview) — the suite that contains Policy Troubleshooter, Analyzer, and Simulator (product docs home).
- [Troubleshoot access](https://cloud.google.com/policy-intelligence/docs/troubleshoot-access) — main how-to: prerequisites, required roles, and the step-by-step gcloud workflow.
- [Resource names](https://cloud.google.com/iam/docs/resource-names) — full resource name format needed to construct the `RESOURCE` argument.
- [Troubleshooting access](https://cloud.google.com/iam/docs/troubleshooting-access) — IAM troubleshooting guide that cross-references Policy Troubleshooter.
- [gcloud policy-troubleshoot iam reference](https://cloud.google.com/sdk/gcloud/reference/policy-troubleshoot/iam) — full CLI reference (all flags and examples).
