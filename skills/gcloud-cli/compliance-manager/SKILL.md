---
name: gcloud-compliance-manager
description: >-
  Compliance Manager via gcloud (`gcloud compliance-manager`). Manage Compliance Manager resources — cloud-control-deployments, cloud-controls, framework-deployments, frameworks, operations.
---

# gcloud compliance-manager — Compliance Manager

## Overview

`gcloud compliance-manager` manages Compliance Manager, a feature of Security Command Center that helps organizations show their Google Cloud infrastructure meets security and regulatory requirements. You define **cloud controls** (individual checks, optionally with CEL detection rules), group them into **frameworks** (such as FedRAMP, ISO 27001, NIST SP 800-53, or PCI DSS 4.0, plus your own custom frameworks), and **deploy** those frameworks against organization, folder, or project resources. Reach for it when you need to codify a compliance baseline and continuously evaluate cloud resources against it. All resources are scoped to an organization at location `global`.

## Quick reference — common workflows

### 1. Enable the APIs
Compliance Manager findings are served by the Cloud Security Compliance API alongside Security Command Center.
```bash
gcloud services enable securitycenter.googleapis.com \
    cloudsecuritycompliance.googleapis.com
```

### 2. List frameworks and cloud controls
```bash
# List all frameworks in the organization
gcloud compliance-manager frameworks list \
    --organization=my-organization-id --location=global

# Inspect a specific framework (optionally pin a major revision)
gcloud compliance-manager frameworks describe my-framework-id \
    --organization=my-organization-id --location=global \
    --major-revision-id=1

# List all cloud controls in the organization
gcloud compliance-manager cloud-controls list \
    --organization=my-organization-id --location=global
```

### 3. Create a custom cloud control with a CEL rule
```bash
gcloud compliance-manager cloud-controls create my-cloud-control-id \
    --organization=my-organization-id --location=global \
    --display-name="No VM IP Forwarding" \
    --description="Ensure Compute instances do not have IP forwarding enabled." \
    --severity=medium \
    --categories=cc-category-infrastructure \
    --supported-cloud-providers=gcp \
    --supported-target-resource-types=target-resource-crm-type-org \
    --rules='[{"description":"VM IP forwarding check","ruleActionTypes":["rule-action-type-detective"],"celExpression":{"expression":"resource.canIpForward == false","resourceTypesValues":{"values":["compute.googleapis.com/Instance"]}}}]'

# Verify it was created
gcloud compliance-manager cloud-controls describe my-cloud-control-id \
    --organization=my-organization-id --location=global
```

### 4. Create a custom framework grouping controls
```bash
gcloud compliance-manager frameworks create my-framework-id \
    --organization=my-organization-id --location=global \
    --display-name="My Security Framework" \
    --description="Internal framework for baseline security controls." \
    --category=custom-framework \
    --cloud-control-details='[{"name":"organizations/my-organization-id/locations/global/cloudControls/my-cloud-control-id","majorRevisionId":1,"parameters":[]}]'
```

### 5. Deploy a framework against an existing folder
```bash
gcloud compliance-manager framework-deployments create my-framework-deployment-id \
    --organization=my-organization-id --location=global \
    --framework="organizations/my-organization-id/locations/global/frameworks/my-framework-id" \
    --framework-major-revision-id=1 \
    --target-resource-config-existing=folders/my-folder-id \
    --cloud-control-metadata='[{"cloudControlDetails":{"name":"organizations/my-organization-id/locations/global/cloudControls/my-cloud-control-id","majorRevisionId":1,"parameters":[]},"enforcementMode":"DETECTIVE"}]' \
    --description="Deploying my framework to the dev folder" \
    --async

# Check deployment status
gcloud compliance-manager framework-deployments describe my-framework-deployment-id \
    --organization=my-organization-id --location=global
```

### 6. Inspect cloud control deployments and track operations
```bash
# List the cloud-control-level deployments produced by a framework deployment
gcloud compliance-manager cloud-control-deployments list \
    --organization=my-organization-id --location=global

# List long-running operations (e.g. after an --async create)
gcloud compliance-manager operations list \
    --organization=my-organization-id --location=global

# Wait for a specific operation to finish
gcloud compliance-manager operations wait my-operation-id \
    --organization=my-organization-id --location=global
```

### 7. Clean up — delete a deployment, framework, then control
```bash
gcloud compliance-manager framework-deployments delete my-framework-deployment-id \
    --organization=my-organization-id --location=global

gcloud compliance-manager frameworks delete my-framework-id \
    --organization=my-organization-id --location=global

gcloud compliance-manager cloud-controls delete my-cloud-control-id \
    --organization=my-organization-id --location=global
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `compliance-manager cloud-control-deployments` | [`cloud-control-deployments.md`](cloud-control-deployments.md) | 2 | Describe and list the per-cloud-control deployments created by framework deployments |
| `compliance-manager cloud-controls` | [`cloud-controls.md`](cloud-controls.md) | 4 | Create, describe, list, and delete cloud controls (CEL-backed checks) |
| `compliance-manager framework-deployments` | [`framework-deployments.md`](framework-deployments.md) | 4 | Deploy frameworks against resources and manage those deployments |
| `compliance-manager frameworks` | [`frameworks.md`](frameworks.md) | 4 | Create, describe, list, and delete frameworks (groupings of controls) |
| `compliance-manager operations` | [`operations.md`](operations.md) | 5 | Describe, list, wait on, cancel, and delete long-running operations |

See [`index.md`](index.md) for a one-line index of all 19 GA commands.

## Common flags & tips

- **Organization + location are required everywhere.** Every command needs `--organization=ORG_ID` and `--location=global` (the only supported location), unless you pass a fully qualified resource name like `organizations/ORG_ID/locations/global/frameworks/FRAMEWORK_ID` in the positional argument.
- **Structured flags accept JSON, shorthand, or a file.** `--rules`, `--parameter-spec` (on `cloud-controls create`), `--cloud-control-details` (on `frameworks create`), and `--cloud-control-metadata` (on `framework-deployments create`) each accept inline JSON (`'[{...}]'`), gcloud shorthand, or `--FLAG=path_to_file.yaml`/`.json` for anything non-trivial.
- **CEL rules.** `--rules` carries the detection logic: a `celExpression.expression` (max 1000 chars), the `resourceTypesValues.values` it applies to (e.g. `compute.googleapis.com/Instance`), and `ruleActionTypes` (e.g. `rule-action-type-detective`).
- **Enumerated values.** `--severity` is one of `critical`, `high`, `medium`, `low`. `--categories` values are the `cc-category-*` set (e.g. `cc-category-infrastructure`, `cc-category-network-security`). `--supported-cloud-providers` is `gcp`, `aws`, or `azure`. `--supported-target-resource-types` is `target-resource-crm-type-{org,folder,project}` or `target-resource-type-application`. Framework `--category` is one of `custom-framework`, `assured-workloads`, `data-security`, `google-best-practices`, `industry-defined-standard`.
- **Pinning revisions.** `frameworks describe` and `cloud-controls describe` take `--major-revision-id`; omit it to get the most recently updated revision. Framework deployments require `--framework-major-revision-id`.
- **Deployment targets.** `framework-deployments create` targets an existing resource with `--target-resource-config-existing=folders/ID` (or a project), or creates a new folder/project via the `--target-resource-creation-config-*` flags.
- **Async + concurrency.** `framework-deployments create`/`delete` accept `--async` (return immediately, then poll via `operations`) and `--etag` (optimistic concurrency control).
- **Filtering / formatting.** All `list` commands support `--filter`, `--sort-by`, `--limit`, `--page-size`, and `--uri`:
  ```bash
  gcloud compliance-manager frameworks list \
      --organization=my-organization-id --location=global \
      --filter="category=custom-framework" --format="table(name,majorRevisionId)"
  ```

## Official documentation

- [Compliance Manager overview](https://cloud.google.com/security-command-center/docs/compliance-manager) — concepts, tiers, built-in frameworks, and component definitions.
- [Enable Compliance Manager](https://cloud.google.com/security-command-center/docs/compliance-manager-enable) — required roles, service agents, and activation paths.
- [Built-in frameworks reference](https://cloud.google.com/security-command-center/docs/compliance-manager-frameworks) — CIS GCP/GKE, FedRAMP, ISO 27001, NIST, PCI DSS, and more.
- [Built-in cloud controls reference](https://cloud.google.com/security-command-center/docs/compliance-manager-cloud-controls) — available controls and their enforcement modes.
- [Manage custom cloud controls](https://cloud.google.com/security-command-center/docs/compliance-manager-manage-cloud-controls) — create, view, edit, and delete custom controls.
- [Write CEL expressions](https://cloud.google.com/security-command-center/docs/compliance-manager-write-cel-expressions) — authoring detection rules for custom cloud controls.
- [gcloud compliance-manager CLI reference](https://cloud.google.com/sdk/gcloud/reference/compliance-manager) — full command and flag reference (GA).
