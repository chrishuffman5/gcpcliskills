# gcloud source — Cloud Source Repositories

## Overview
`gcloud source` manages **Cloud Source Repositories (CSR)** — fully featured, private Git repositories hosted on Google Cloud. Use it to create and clone repos, manage per-repository IAM, wire repos to Cloud Pub/Sub for push notifications, and set project-wide policy such as PushBlock. **Deprecation notice:** as of **June 17, 2024**, CSR is no longer available to *new* customers; existing customers may continue to use it. For new workloads Google recommends **Secure Source Manager** (`gcloud source-manager`) or an external Git host (e.g. GitHub/GitLab) connected to your Google Cloud build and deploy pipelines.

## Quick reference — common workflows

### 1. Create and clone a new repository
```bash
# Enable the API (once per project)
gcloud services enable sourcerepo.googleapis.com

# Create the repository (name: 3-63 lowercase letters/digits/hyphens, starts with a letter)
gcloud source repos create my-repo

# Clone locally — configures the gcloud credential helper automatically
gcloud source repos clone my-repo ~/my-repo

# Work in the repo and push
cd ~/my-repo
git add . && git commit -m "initial commit"
git push origin main
```

### 2. List and inspect repositories
```bash
# List all repos in the current project
gcloud source repos list

# Describe one repo (full name projects/<id>/repos/<name>, size, URL)
gcloud source repos describe my-repo
```

### 3. Manage IAM access on a repository
```bash
# View the current IAM policy
gcloud source repos get-iam-policy my-repo

# Apply an updated policy from a JSON or YAML file
gcloud source repos set-iam-policy my-repo policy.json
```

### 4. Send repository push notifications to Pub/Sub
```bash
# Associate a Pub/Sub topic to receive repo update notifications
gcloud source repos update my-repo \
    --add-topic=my-topic \
    --service-account=my-sa@MY_PROJECT.iam.gserviceaccount.com \
    --message-format=json
```

### 5. Enable PushBlock project-wide (blocks pushes containing private keys)
```bash
# Enable PushBlock for all repos in the project
gcloud source project-configs update --enable-pushblock

# Verify project configuration
gcloud source project-configs describe

# Disable if needed
gcloud source project-configs update --disable-pushblock
```

### 6. Delete a repository
```bash
# --force is removed; use --quiet to suppress the confirmation prompt
gcloud source repos delete my-repo --quiet
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `source project-configs` | [`project-configs.md`](project-configs.md) | 2 | manage Cloud Source Repositories configuration of a project |
| `source repos` | [`repos.md`](repos.md) | 8 | manage cloud source repositories |

See [`index.md`](index.md) for a one-line index of all 10 commands.

## Common flags & tips
- **Repository names:** 3-63 characters, lowercase letters, digits, and hyphens; must start with a letter and may not end with a hyphen.
- **Project scoping:** commands operate on the active project. Override with the global `--project=PROJECT_ID` flag; `gcloud source repos list` without it lists the current project's repos.
- **Clone auth:** `gcloud source repos clone` configures the local clone to use your gcloud credentials for future Git operations — no separate credential helper setup is needed. It emits a warning if the repo is a mirror.
- **`--dry-run`:** on `clone`, prints the command that would run instead of executing it.
- **Pub/Sub notifications:** `--message-format` must be `json` or `protobuf`. `--service-account` must live in the same project as the repo (defaults to the Compute Engine default service account); the caller needs `iam.serviceAccounts.actAs` on it. Use `--add-topic` / `--remove-topic` / `--update-topic`, and `--topic-project` to point at a topic in another project.
- **Deleting:** the `--force` flag has been **removed**; suppress prompts with the global `--quiet`.
- **List/IAM output:** `repos list` and `repos get-iam-policy` support `--filter`, `--limit`, `--page-size`, and `--sort-by`. Example: `gcloud source repos list --filter="name:my-*" --format="value(name)"`.

## beta / alpha
- **`gcloud beta source`** mirrors the GA surface (`project-configs`, `repos`) with the same eight `repos` commands; no beta-exclusive commands are documented.
- **`gcloud alpha source`** adds a `repos config export` subcommand (export repository configuration) not present in GA or beta. The GA surface covers all production use cases; alpha is only needed for `repos config export`.

## Official documentation
- [Cloud Source Repositories docs home](https://cloud.google.com/source-repositories/docs) — product documentation; confirms the June 17, 2024 deprecation to new customers.
- [Quickstart](https://cloud.google.com/source-repositories/docs/quickstart) — enable the API, create a repo, then push code.
- [Create a repository](https://cloud.google.com/source-repositories/docs/create-code-repository) — create a new empty repo via console or gcloud.
- [Authentication setup](https://cloud.google.com/source-repositories/docs/authentication) — local auth via SSH keys, the gcloud credential helper, or generated credentials.
- [IAM roles for CSR](https://cloud.google.com/iam/docs/roles-permissions/source) — predefined `roles/source.*` roles (admin, writer, reader) and project-level Source editor/viewer.
- [gcloud source reference](https://cloud.google.com/sdk/gcloud/reference/source) — full CLI reference for the command group.
