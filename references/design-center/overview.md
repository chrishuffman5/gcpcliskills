# gcloud design-center — Application Design Center

## Overview
Application Design Center (ADC) lets platform and development teams create, share, and deploy
standardized application architectures on Google Cloud from policy-aligned templates. Use
`gcloud design-center` to manage **spaces** (collaboration areas), **application templates**
(reusable architectures built from **components** and **connections**), **catalogs** (for sharing
approved templates across spaces), and **applications** (deployable instances of a template).
The service is GA, backed by `designcenter.googleapis.com`, and all resources are regional
(every command needs a `--location`).

## Quick reference — common workflows

### Enable the API and create a space
```bash
gcloud services enable designcenter.googleapis.com

# Browse available locations, then create a space with Google shared templates enabled
gcloud design-center locations list --project=my-project
gcloud design-center spaces create my-space \
    --project=my-project --location=us-central1 \
    --display-name="My Platform Space" \
    --description="Space for platform team templates" \
    --enable-gcp-shared-templates

gcloud design-center spaces describe my-space \
    --project=my-project --location=us-central1
gcloud design-center spaces list --project=my-project --location=us-central1
```

### Build an application template with components and connections
```bash
gcloud design-center spaces application-templates create my-app-template \
    --space=my-space --project=my-project --location=us-central1 \
    --display-name="My App Template" --description="Three-tier web application"

# Find a shared template revision to base a component on
gcloud design-center spaces shared-templates list \
    --space=my-space --project=my-project --location=us-central1

# Add a component from a shared-template revision (same space)
gcloud design-center spaces application-templates components create frontend \
    --application-template=my-app-template \
    --space=my-space --project=my-project --location=us-central1 \
    --shared-template-revision-uri=my-shared-template/revisions/rev1 \
    --display-name="Frontend Service"

# Connect the frontend component to a backend component
gcloud design-center spaces application-templates components connections create my-conn \
    --component=frontend --application-template=my-app-template \
    --space=my-space --project=my-project --location=us-central1 \
    --destination-component-uri=backend

# Commit to create an immutable revision, then list revisions
gcloud design-center spaces application-templates commit my-app-template \
    --space=my-space --project=my-project --location=us-central1
gcloud design-center spaces application-templates revisions list \
    --application-template=my-app-template \
    --space=my-space --project=my-project --location=us-central1
```

### Generate IaC (Terraform or Helm) for a template
```bash
gcloud design-center spaces application-templates generate my-app-template \
    --space=my-space --project=my-project --location=us-central1 \
    --iac-format=terraform --gcs-uri=gs://my-bucket

gcloud design-center spaces application-templates generate my-app-template \
    --space=my-space --project=my-project --location=us-central1 \
    --iac-format=helm
```

### Create, preview, and deploy an application
```bash
# Create an application from a committed template revision
gcloud design-center spaces applications create my-app \
    --space=my-space --project=my-project --location=us-central1 \
    --scope-type=global \
    --source-application-template-revision=projects/my-project/locations/us-central1/spaces/my-space/applicationTemplates/my-app-template/revisions/rev1

# Preview (plan), then deploy — both can create a deployment service account
gcloud design-center spaces applications preview my-app \
    --space=my-space --project=my-project --location=us-central1 --create-sa
gcloud design-center spaces applications deploy my-app \
    --space=my-space --project=my-project --location=us-central1 --create-sa --async

# Track the long-running deploy operation
gcloud design-center operations list --project=my-project --location=us-central1
gcloud design-center operations wait OPERATION_ID \
    --project=my-project --location=us-central1
```

### Manage space IAM
```bash
gcloud design-center spaces get-iam-policy my-space \
    --location=us-central1 --project=my-project
gcloud design-center spaces set-iam-policy my-space \
    --location=us-central1 --project=my-project /path/to/policy.json
gcloud design-center spaces test-iam-permissions my-space \
    --location=us-central1 --project=my-project \
    --permissions=designcenter.spaces.get,designcenter.spaces.update
```

### Share templates via catalogs
```bash
gcloud design-center spaces catalogs create my-catalog \
    --space=my-space --project=my-project --location=us-central1

# Share the catalog into another space (--destination-space is required)
gcloud design-center spaces catalogs shares create my-share \
    --catalog=my-catalog --space=my-space --project=my-project \
    --location=us-central1 --destination-space=my-destination-space

# Pull updates into a share; list templates a catalog publishes
gcloud design-center spaces catalogs shares sync my-share \
    --catalog=my-catalog --space=my-space --location=us-central1
gcloud design-center spaces catalogs templates list \
    --catalog=my-catalog --space=my-space --project=my-project \
    --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `design-center locations` | [`locations.md`](locations.md) | 2 | Manage Design Center locations |
| `design-center operations` | [`operations.md`](operations.md) | 5 | Manage long-running operation resources |
| `design-center spaces` | [`spaces.md`](spaces.md) | 62 | Manage spaces, application templates, components, connections, applications, catalogs, shares, and shared templates |

See [`index.md`](index.md) for a one-line index of all 69 commands.

## Common flags & tips
- **Regional everywhere.** Almost every command needs `--location` (e.g. `us-central1`); list valid
  regions with `gcloud design-center locations list`. Resource flags like `--space`,
  `--application-template`, `--catalog`, and `--component` scope nested resources.
- **Fully qualified names vs. flags.** Any resource can be named either by short ID + scoping flags,
  or by its full path, e.g.
  `projects/PROJECT/locations/LOCATION/spaces/SPACE/applicationTemplates/TEMPLATE`. When the full
  path is given, the project/location/space flags can be omitted.
- **Templates are immutable once committed.** Edit components/connections, then run
  `application-templates commit` to mint a new `revisions/...` entry; create applications from those
  revision URIs (`--source-application-template-revision`).
- **Deployment service accounts.** `applications preview` and `applications deploy` accept
  `--create-sa` (mint a new SA) and/or `--service-account`; deploy adds `--replace` to update an
  already-DEPLOYED app and `--worker-pool` to pick a Cloud Build worker pool.
- **IaC generation.** `--iac-format` accepts `terraform` or `helm` on both
  `application-templates generate` and `applications generate`.
- **Async + operations.** Mutating commands such as `applications deploy`, `catalogs delete`, and
  `catalogs shares sync` accept `--async`; track them with `operations list` / `operations wait`.
- **Google Catalog shortcut.** `shared-templates list/describe` and their `revisions` subcommands
  accept `--google-catalog` to browse Google's curated templates instead of a space.
- **Filtering & listing.** List commands support standard `--filter`, `--limit`, `--page-size`, and
  `--sort-by`, e.g. `--filter="displayName:my-app-template*"` or `--sort-by=createTime`.

## beta / alpha
- There is no `gcloud beta design-center` surface; the GA group covers all 69 documented commands.
- `gcloud alpha design-center` mirrors the GA surface and exposes experimental, `v1alpha`-backed
  features that "might change without notice." See the alpha reference for the current list.

## Official documentation
- [Application Design Center docs home](https://docs.cloud.google.com/application-design-center/docs) — product landing page and entry point.
- [ADC overview / concepts](https://docs.cloud.google.com/application-design-center/docs/overview) — spaces, templates, components, catalogs, applications.
- [Setup guide](https://docs.cloud.google.com/application-design-center/docs/setup) — APIs to enable and required IAM roles.
- [Quickstart](https://docs.cloud.google.com/application-design-center/docs/quickstart) — create a space and template, then deploy an app.
- [Design application templates](https://docs.cloud.google.com/application-design-center/docs/design-application-templates) — build templates with components and connections via gcloud.
- [Manage applications](https://docs.cloud.google.com/application-design-center/docs/manage-applications) — create and configure applications from templates.
- [Deploy applications](https://docs.cloud.google.com/application-design-center/docs/deploy-applications) — preview and deploy with service accounts.
- [Supported resources](https://docs.cloud.google.com/application-design-center/docs/supported-resources) — component resource types (Cloud Run, GKE, Cloud SQL, Spanner, etc.).
- [REST API reference](https://docs.cloud.google.com/application-design-center/docs/reference/rest) — `designcenter.googleapis.com` (v1 + v1alpha).
- [gcloud design-center reference](https://cloud.google.com/sdk/gcloud/reference/design-center) — full CLI command reference.
