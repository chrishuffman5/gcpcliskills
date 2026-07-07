---
name: gcloud-artifacts
description: >-
  Artifact Registry via gcloud (`gcloud artifacts`). Manage Artifact Registry resources — apt, attachments, docker, files, generic, go, locations, operations.
---

# gcloud artifacts — Artifact Registry

## Overview

Artifact Registry is Google Cloud's fully managed service for storing and managing build artifacts and dependencies — Docker/OCI container images, Maven/Gradle, npm, Python, Go, apt/yum OS packages, KFP, and generic files. Reach for `gcloud artifacts` to create and govern repositories, push/pull and inspect artifacts, configure native build tools, manage IAM and cleanup policies, and run vulnerability scans. It is the recommended successor to Container Registry, adding multi-format support, fine-grained IAM, VPC Service Controls, and three repository modes: standard, remote (proxy/cache), and virtual (aggregated endpoint).

## Quick reference — common workflows

### 1. Enable the API, create a repository, and set defaults
```bash
# One-time: enable the Artifact Registry API
gcloud services enable artifactregistry.googleapis.com

# Create a Docker repository
gcloud artifacts repositories create my-docker-repo \
    --repository-format=docker \
    --location=us-central1 \
    --description="Docker images for my project"

# Confirm it exists
gcloud artifacts repositories list --location=us-central1

# Set defaults so you can drop --location / --repository on later commands
gcloud config set artifacts/location us-central1
gcloud config set artifacts/repository my-docker-repo
```

### 2. Authenticate Docker and inspect images
```bash
# Configure Docker auth for the registry host (a gcloud auth command, then use docker push/pull)
gcloud auth configure-docker us-central1-docker.pkg.dev

# List images in a repository
gcloud artifacts docker images list \
    us-central1-docker.pkg.dev/my-project/my-docker-repo

# List images with their tags
gcloud artifacts docker images list \
    us-central1-docker.pkg.dev/my-project/my-docker-repo --include-tags

# Describe an image, including its vulnerability summary
gcloud artifacts docker images describe \
    us-central1-docker.pkg.dev/my-project/my-docker-repo/my-image:latest \
    --show-package-vulnerability

# Delete an image and all of its tags
gcloud artifacts docker images delete \
    us-central1-docker.pkg.dev/my-project/my-docker-repo/my-image:old \
    --delete-tags
```

### 3. Manage language packages and versions (Maven / Python / npm)
```bash
# Create a Maven repository that only stores release versions
gcloud artifacts repositories create my-maven-repo \
    --repository-format=maven \
    --location=us-central1 \
    --version-policy=release

# Print build-tool snippets to connect to the repository
gcloud artifacts print-settings mvn    --repository=my-maven-repo  --location=us-central1
gcloud artifacts print-settings gradle --repository=my-maven-repo  --location=us-central1
gcloud artifacts print-settings npm    --repository=my-npm-repo    --location=us-central1
gcloud artifacts print-settings python --repository=my-python-repo --location=us-central1

# List packages, then list versions of one package
gcloud artifacts packages list --repository=my-maven-repo --location=us-central1
gcloud artifacts versions list \
    --package=com.example:my-lib \
    --repository=my-maven-repo --location=us-central1
```

### 4. Grant repository access (IAM)
```bash
# View the current policy
gcloud artifacts repositories get-iam-policy my-docker-repo --location=us-central1

# Grant read access to a service account
gcloud artifacts repositories add-iam-policy-binding my-docker-repo \
    --location=us-central1 \
    --member="serviceAccount:my-sa@my-project.iam.gserviceaccount.com" \
    --role="roles/artifactregistry.reader"

# Grant write access to a user
gcloud artifacts repositories add-iam-policy-binding my-docker-repo \
    --location=us-central1 \
    --member="user:developer@example.com" \
    --role="roles/artifactregistry.writer"
```

### 5. Apply cleanup policies to control storage
```bash
# Preview what a policy would delete (no deletions performed)
gcloud artifacts repositories set-cleanup-policies my-docker-repo \
    --location=us-central1 \
    --policy=cleanup-policy.json \
    --dry-run

# Apply the policy for real
gcloud artifacts repositories set-cleanup-policies my-docker-repo \
    --location=us-central1 \
    --policy=cleanup-policy.json

# Review and remove policies
gcloud artifacts repositories list-cleanup-policies my-docker-repo --location=us-central1
gcloud artifacts repositories delete-cleanup-policies my-docker-repo \
    --location=us-central1 --policynames=my-delete-policy
```

### 6. Scan a container image for vulnerabilities (On-Demand Scanning)
```bash
# Start a scan of an image stored in Artifact Registry (analysis runs in a multi-region)
gcloud artifacts docker images scan \
    us-central1-docker.pkg.dev/my-project/my-docker-repo/my-image:latest \
    --remote --location=us

# Check the async scan operation, then list the findings
gcloud artifacts docker images get-operation OPERATION_ID --location=us
gcloud artifacts docker images list-vulnerabilities SCAN_ID --location=us

# List vulnerabilities recorded in Artifact Analysis for an image URI
gcloud artifacts vulnerabilities list \
    us-central1-docker.pkg.dev/my-project/my-docker-repo/my-image@sha256:DIGEST
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `artifacts apt` | [`apt.md`](apt.md) | 2 | manage Artifact Registry Debian packages |
| `artifacts attachments` | [`attachments.md`](attachments.md) | 5 | manage Artifact Registry attachments |
| `artifacts docker` | [`docker.md`](docker.md) | 10 | manage Artifact Registry container images and tags |
| `artifacts files` | [`files.md`](files.md) | 5 | manage Artifact Registry files |
| `artifacts generic` | [`generic.md`](generic.md) | 2 | manage Artifact Registry generic artifacts |
| `artifacts go` | [`go.md`](go.md) | 2 | manage Artifact Registry Go modules |
| `artifacts locations` | [`locations.md`](locations.md) | 1 | manage Artifact Registry resource locations |
| `artifacts operations` | [`operations.md`](operations.md) | 1 | manage Artifact Registry long-running operations |
| `artifacts packages` | [`packages.md`](packages.md) | 4 | manage Artifact Registry packages |
| `artifacts print-settings` | [`print-settings.md`](print-settings.md) | 4 | print snippets to add to native tools settings files |
| `artifacts repositories` | [`repositories.md`](repositories.md) | 12 | manage Artifact Registry repositories |
| `artifacts rules` | [`rules.md`](rules.md) | 5 | manage Artifact Registry rules |
| `artifacts sbom` | [`sbom.md`](sbom.md) | 3 | manage Artifact SBOMs |
| `artifacts settings` | [`settings.md`](settings.md) | 3 | manage Artifact Registry project settings |
| `artifacts tags` | [`tags.md`](tags.md) | 5 | manage Artifact Registry tags |
| `artifacts versions` | [`versions.md`](versions.md) | 5 | manage Artifact Registry package versions |
| `artifacts vpcsc-config` | [`vpcsc-config.md`](vpcsc-config.md) | 3 | manage VPC Service Controls config for remote repositories |
| `artifacts vulnerabilities` | [`vulnerabilities.md`](vulnerabilities.md) | 2 | manage Artifact Vulnerabilities |
| `artifacts yum` | [`yum.md`](yum.md) | 2 | manage Artifact Registry RPM packages |

See [`index.md`](index.md) for a one-line index of all 76 GA commands.

## Common flags & tips

- **Set defaults to avoid repetition.** `gcloud config set artifacts/location us-central1` and `gcloud config set artifacts/repository my-repo` let you omit `--location` / `--repository` on most commands.
- **Repository format is required at creation.** `--repository-format` must be one of `apt`, `docker`, `go`, `kfp`, `maven`, `npm`, `python`, `yum`. Use `--mode` (`standard-repository`, `remote-repository`, `virtual-repository`) to choose the repository type; the default is `standard`.
- **Maven-only knobs:** `--version-policy` (`none|release|snapshot`) and `--allow-snapshot-overwrites`. **Docker-only:** `--immutable-tags`. **Virtual repos:** `--upstream-policy-file`. **Remote repos:** the `--remote-*-repo` family plus `--remote-username` / `--remote-password-secret-version`.
- **Image references** use `LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE`, addressable by `:tag` or `@sha256:digest`. Deleting by digest or tag when other tags exist requires `--delete-tags`.
- **`--show-*` describe flags** enrich `docker images describe` output: `--show-package-vulnerability`, `--show-build-details`, `--show-provenance`, `--show-sbom-references`, `--show-image-basis`, `--show-deployment`, `--show-all-metadata`.
- **Scanning location is a multi-region.** `docker images scan --location` accepts only `asia`, `europe`, or `us` (default `us`); `vulnerabilities list` takes the image URI as a positional argument.
- **`--format` / `--filter` examples:**
  - `gcloud artifacts repositories list --format="table(name, format, mode, createTime)"`
  - `gcloud artifacts repositories list --filter="format=DOCKER" --sort-by=~createTime`
  - `gcloud artifacts versions list --package=my-pkg --sort-by=~createTime --limit=10`
  - `gcloud artifacts vulnerabilities list IMAGE_URI --format=json` (full fields)
- **Long-running operations:** add `--async` to repository/package/version/image deletes (and other mutating commands) to return immediately; track with `gcloud artifacts operations describe`.

## beta / alpha

Both `gcloud beta artifacts` and `gcloud alpha artifacts` exist and mirror the GA command groups (apt, docker, files, generic, go, locations, operations, packages, print-settings, repositories, settings, tags, versions, vpcsc-config, yum). The `attachments`, `rules`, `sbom`, and `vulnerabilities` groups are GA in the documented surface and are not part of the documented beta tree. No capability is currently documented as exclusively beta/alpha — the GA surface (76 commands) is the primary reference. Check the beta/alpha reference pages for any in-flight features not yet graduated to GA.

## Official documentation

- [Artifact Registry documentation home](https://cloud.google.com/artifact-registry/docs) — product docs landing page (quickstarts, how-to, concepts).
- [Product overview](https://cloud.google.com/artifact-registry/docs/overview) — features, repository modes, supply-chain security, Container Registry comparison.
- [Store Docker container images](https://cloud.google.com/artifact-registry/docs/docker/store-docker-container-images) — Docker quickstart: create a repo, configure Docker auth, push/pull.
- [Store Java packages (Maven/Gradle)](https://cloud.google.com/artifact-registry/docs/java/store-java) — Maven/Gradle quickstart with pom.xml/build.gradle snippets.
- [Store Python packages](https://cloud.google.com/artifact-registry/docs/python/store-python) — Python quickstart: create a python repo, list packages and versions.
- [Repositories overview](https://cloud.google.com/artifact-registry/docs/repositories) — standard, remote, virtual, and gcr.io domain repositories.
- [Create repositories](https://cloud.google.com/artifact-registry/docs/repositories/create-repos) — create repos for every supported format with all relevant flags.
- [Cleanup policies](https://cloud.google.com/artifact-registry/docs/repositories/cleanup-policy) — delete/keep policy JSON format and dry-run testing.
- [Access control (IAM)](https://cloud.google.com/artifact-registry/docs/access-control) — IAM roles and access control for repositories and artifacts.
- [gcloud artifacts CLI reference](https://cloud.google.com/sdk/gcloud/reference/artifacts) — full command reference for all `gcloud artifacts` commands.
