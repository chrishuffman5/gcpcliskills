# gcloud apihub — API hub

## Overview

Apigee API hub is a centralized catalog and governance platform for all of the APIs in your organization, regardless of where they run (Apigee, other gateways, or no gateway at all). You register APIs with versions, attach machine-readable specs (OpenAPI and others), record deployments and API operations, and enrich everything with attributes, curations, and dependencies for discovery and governance. A host project runs the API hub instance; runtime projects are attached to it so their APIs (e.g. Apigee proxies) can be registered and auto-discovered, and plugins integrate Google Cloud or third-party sources. The `gcloud apihub` group covers the full GA surface: instance provisioning, the API/version/spec/operation hierarchy, deployments, governance resources, discovery results, plugins, project registration/attachment, and long-running operations. The service to enable is `apihub.googleapis.com`.

## Quick reference — common workflows

### 1. Enable the API and grant access

```bash
gcloud services enable apihub.googleapis.com --project PROJECT_ID

# Full access to all API hub resources
gcloud projects add-iam-policy-binding PROJECT_ID \
    --member="user:USER@example.com" \
    --role="roles/apihub.admin"

# Read-only access
gcloud projects add-iam-policy-binding PROJECT_ID \
    --member="user:USER@example.com" \
    --role="roles/apihub.viewer"
```

### 2. Provision an API hub instance and register the host project

```bash
# Create the (single) API hub instance in the host project
gcloud apihub api-hub-instances create --project=my-project \
    --location=us-central1

# Register the host project
gcloud apihub host-project-registrations create \
    --host-project-registration=my-registration \
    --gcp-project=my-gcp-project --project=my-project \
    --location=us-central1
```

### 3. Register an API with a version and a spec

```bash
gcloud apihub apis create --api=my-api --display-name="My API" \
    --project=my-project --location=us-central1

gcloud apihub apis versions create --version=my-version \
    --api=my-api --display-name="My Version" --project=my-project \
    --location=us-central1

gcloud apihub apis versions specs create --spec=my-spec \
    --version=my-version --api=my-api --display-name="My Spec" \
    --spec-type=openapi --project=my-project --location=us-central1
```

### 4. Lint a spec and retrieve its contents

```bash
gcloud apihub apis versions specs lint my-spec \
    --version=my-version --api=my-api --project=my-project \
    --location=us-central1

gcloud apihub apis versions specs get-contents my-spec --api=my-api \
    --version=my-version --location=us-central1
```

### 5. Record a deployment

```bash
gcloud apihub deployments create --deployment=my-deployment \
    --display-name="My Deployment" --deployment-type=apigee \
    --project=my-project --location=us-central1
```

### 6. Attach a runtime project (and look up existing attachments)

```bash
gcloud apihub runtime-project-attachments create \
    --runtime-project-attachment=my-attachment \
    --runtime-project=my-runtime-project \
    --project=my-project --location=us-central1

gcloud apihub runtime-project-attachments lookup \
    --service-project=my-service-project --location=us-central1
```

### 7. Add a plugin and create a plugin instance

```bash
gcloud apihub plugins create --plugin=my-plugin \
    --display-name="My Plugin" --type=apigee --project=my-project \
    --location=us-central1

gcloud apihub plugins instances create --plugin-instance=my-instance \
    --plugin=my-plugin --display-name="My Instance" \
    --project=my-project --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `apihub addons` | [`addons.md`](addons.md) | 3 | manage Addon resources |
| `apihub api-hub-instances` | [`api-hub-instances.md`](api-hub-instances.md) | 4 | manage Api Hub Instance resources |
| `apihub apis` | [`apis.md`](apis.md) | 22 | manage Api resources (incl. nested `versions`, `versions operations`, `versions specs`) |
| `apihub attributes` | [`attributes.md`](attributes.md) | 5 | manage Attribute resources |
| `apihub curations` | [`curations.md`](curations.md) | 5 | manage Curation resources |
| `apihub dependencies` | [`dependencies.md`](dependencies.md) | 5 | manage Dependency resources |
| `apihub deployments` | [`deployments.md`](deployments.md) | 5 | manage Deployment resources |
| `apihub discovered-api-observations` | [`discovered-api-observations.md`](discovered-api-observations.md) | 4 | manage Discovered Api Observation resources (incl. nested `discovered-api-operations`) |
| `apihub external-apis` | [`external-apis.md`](external-apis.md) | 5 | manage External Api resources |
| `apihub host-project-registrations` | [`host-project-registrations.md`](host-project-registrations.md) | 3 | manage Host Project Registration resources |
| `apihub operations` | [`operations.md`](operations.md) | 5 | manage Operation resources |
| `apihub plugins` | [`plugins.md`](plugins.md) | 12 | manage Plugin resources (incl. nested `instances`) |
| `apihub runtime-project-attachments` | [`runtime-project-attachments.md`](runtime-project-attachments.md) | 5 | manage Runtime Project Attachment resources |

See [`index.md`](index.md) for a one-line index of all 83 commands.

## Common flags & tips

- **`--location` is pervasive.** Nearly every command takes `--location` (the region of the API hub instance, e.g. `us-central1`) plus `--project`; both can be inferred from a fully qualified resource name passed as the positional argument.
- **`create` commands use resource flags, not positionals.** Several reference pages carry the note "The positional argument ... is currently not supported" — pass the ID via the matching flag instead: `--api=`, `--version=`, `--spec=`, `--deployment=`, `--dependency=`, `--curation=`, `--plugin=`, `--plugin-instance=`, `--attachment` style flags (`--runtime-project-attachment=`), and `--host-project-registration=`.
- **Resource hierarchy:** `apis` → `versions` → `specs` / `operations`. Commands on nested resources require the ancestors as flags, e.g. `specs describe my-spec --version=my-version --api=my-api`.
- **List commands** support the standard gcloud list flags: `--filter`, `--limit`, `--page-size`, `--sort-by`, `--uri`. `list` commands generally require `--location` as a flag (there is no positional parent).
- **Long-running operations:** provisioning and some mutations return operations; track them with `gcloud apihub operations describe/list/wait/cancel/delete`.
- **Host vs. runtime projects:** the API hub instance lives in the host project (`api-hub-instances create`, `host-project-registrations create`); attach service/runtime projects with `runtime-project-attachments create`, and find which attachment covers a given project with `runtime-project-attachments lookup`.
- **IAM:** `roles/apihub.admin` grants full access to all API hub resources; `roles/apihub.viewer` grants read access. Provisioning also involves the API hub service agent (`roles/apihub.runtimeProjectServiceAgent`). See the predefined-roles docs for the full role list.

## beta / alpha

There is no `gcloud beta apihub` surface (the beta reference URL returns 404). An **alpha** surface (`gcloud alpha apihub`) exists and mirrors the same 13 subgroups as GA (addons, api-hub-instances, apis, attributes, curations, dependencies, deployments, discovered-api-observations, external-apis, host-project-registrations, operations, plugins, runtime-project-attachments); it is where new fields and commands appear first and may change without notice.

## Official documentation

- **Product docs home (what is API hub):** https://docs.cloud.google.com/apigee/docs/apihub/what-is-api-hub — concepts: APIs, versions, specs, deployments, operations, attributes, curations, dependencies, plugins, host/runtime projects.
- **Provisioning:** https://docs.cloud.google.com/apigee/docs/apihub/provision — provision API hub in the Cloud console; https://docs.cloud.google.com/apigee/docs/apihub/provision-cli — provision from the command line.
- **Predefined IAM roles:** https://docs.cloud.google.com/apigee/docs/apihub/iam-roles — API hub roles; see also https://docs.cloud.google.com/iam/docs/roles-permissions/apihub for the roles/apihub.* permission index.
- **Register APIs:** https://docs.cloud.google.com/apigee/docs/apihub/register-api — manual and automatic API registration.
- **Locations:** https://docs.cloud.google.com/apigee/docs/apihub/locations — supported regions for API hub.
- **REST API reference:** https://docs.cloud.google.com/apigee/docs/reference/apis/apihub/rest — the API hub REST API backing these commands.
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/apihub — the `gcloud apihub` command group.
