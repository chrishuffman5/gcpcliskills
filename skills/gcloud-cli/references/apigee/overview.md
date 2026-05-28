# gcloud apigee — Apigee API Management

## Overview
`gcloud apigee` manages resources in Apigee, Google Cloud's full-lifecycle API management platform for designing, securing, deploying, monitoring, and monetizing APIs. The GA command surface covers the core publishing workflow: discovering organizations and environments, listing and deploying API proxies, and packaging proxies into API products consumed by registered developers and applications. Reach for it when you need to script proxy deployments or product/developer administration from the CLI rather than the Apigee UI.

Apigee organizations are distinct from Cloud Platform organizations and usually map one-to-one to a Cloud Platform project. Almost every command accepts `--organization`; if you omit it, the active project's associated Apigee organization is used.

## Quick reference — common workflows

### Enable the API (prerequisite)
```bash
gcloud services enable apigee.googleapis.com
# Provisioning a new Apigee org also typically needs:
gcloud services enable compute.googleapis.com
gcloud services enable servicenetworking.googleapis.com   # VPC peering
gcloud services enable cloudkms.googleapis.com             # data encryption
```

### 1. Discover organizations and environments
```bash
# All Apigee orgs your credentials can access (across projects)
gcloud apigee organizations list

# Environments in the active project's org
gcloud apigee environments list

# Environments in a named org
gcloud apigee environments list --organization=my-org
```

### 2. List and inspect API proxies
```bash
# All proxies in the active project
gcloud apigee apis list

# Proxies in a specific org as JSON
gcloud apigee apis list --organization=my-org --format=json

# Proxy metadata including its revisions
gcloud apigee apis describe my-proxy --verbose
```

### 3. Deploy an API proxy to an environment
```bash
# Deploy the latest revision of my-proxy to the test environment
gcloud apigee apis deploy --api=my-proxy --environment=test

# Deploy revision 3 to prod, overriding any conflicting deployment (zero downtime)
gcloud apigee apis deploy 3 --api=my-proxy --environment=prod \
    --organization=my-org --override

# Confirm deployment status
gcloud apigee deployments describe --api=my-proxy --environment=prod

# List every active deployment
gcloud apigee deployments list

# Filter deployments to one proxy in one environment
gcloud apigee deployments list --api=my-proxy --environment=prod \
    --organization=my-org
```

### 4. Undeploy an API proxy
```bash
# Undeploy whatever revision of my-proxy is currently in test
gcloud apigee apis undeploy --api=my-proxy --environment=test

# Undeploy a specific revision in a named org
gcloud apigee apis undeploy 3 --api=my-proxy --environment=prod \
    --organization=my-org
```

### 5. Create and publish an API product
```bash
# Public product exposing all proxies in prod
gcloud apigee products create my-product \
    --environments=prod --all-proxies --public-access \
    --display-name="My Product" \
    --description="Public API product for prod environment"

# Product with a quota (50 calls/minute) and manual key approval
gcloud apigee products create gated-product \
    --environments=prod --all-proxies --public-access \
    --quota=50 --quota-interval=1 --quota-unit=minute \
    --manual-approval

# Expose only specific proxies on specific resource paths
gcloud apigee products create consumer \
    --environments=prod --apis=menu,cart,delivery-tracker \
    --resources="/v1/**" --public-access

# List and inspect products
gcloud apigee products list
gcloud apigee products describe my-product --format=json
```

### 6. Update a product and review developers/apps
```bash
# Adjust quota and switch to automatic key approval
gcloud apigee products update my-product \
    --quota=45 --quota-interval=1 --quota-unit=minute \
    --automatic-approval --public-access

# Add a new proxy to the product and drop an old one
gcloud apigee products update my-product \
    --add-api=new-proxy --remove-api=old-proxy

# Registered developers and applications
gcloud apigee developers list
gcloud apigee developers describe developer@example.com
gcloud apigee applications list
gcloud apigee applications list --developer=developer@example.com
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `apigee apis` | [`apis.md`](apis.md) | 4 | manage Apigee API proxies (list, describe, deploy, undeploy) |
| `apigee applications` | [`applications.md`](applications.md) | 2 | manage third-party applications which call Apigee API proxies |
| `apigee deployments` | [`deployments.md`](deployments.md) | 2 | manage deployments of Apigee API proxies in runtime environments |
| `apigee developers` | [`developers.md`](developers.md) | 2 | manage Apigee developers |
| `apigee environments` | [`environments.md`](environments.md) | 1 | manage Apigee environments |
| `apigee organizations` | [`organizations.md`](organizations.md) | 1 | manage Apigee organizations |
| `apigee products` | [`products.md`](products.md) | 5 | manage Apigee API products |

See [`index.md`](index.md) for a one-line index of all 17 GA commands.

## Common flags & tips

- **`--organization`** — present on nearly every command. Omit it to use the Apigee org paired with the active project, or pass it explicitly to act across projects. `gcloud apigee organizations list` shows every org your credentials can reach.
- **Resource selection on `apis deploy`/`undeploy` and `deployments describe`** — the proxy revision is a positional argument. A bare number (e.g. `3`) targets that revision; on deploy, omitting it means `latest`; on undeploy/describe it means `auto` (the currently deployed revision). Pair with `--api` and `--environment`.
- **`--override` on deploy** — required for zero-downtime replacement when a conflicting revision is already deployed; without it, deploy fails until conflicts are undeployed.
- **Product access level** — exactly one of `--public-access`, `--private-access` (unlisted), or `--internal-access`. Approval mode is `--manual-approval` vs `--automatic-approval` (update only).
- **Product scope** — `--all-proxies` vs `--apis=API,...`, and `--all-environments` vs `--environments=ENV,...`. Narrow further with `--resources="/v1/**"` (use `#` to separate multiple resource paths, e.g. `--resources="/v0/**#/v1/**"`).
- **Quotas** — set all three together: `--quota`, `--quota-interval`, `--quota-unit` (e.g. `minute`). On update, clear with `--clear-quota`.
- **`--filter` / `--format`** — every `list` command supports them. Examples: `gcloud apigee organizations list --filter="project:(sandbox)"`, `--format=json` for machine-readable output, `gcloud apigee apis list --uri` for bare resource URIs.
- **Developers are keyed by email** — `gcloud apigee developers describe developer@example.com`. Applications are keyed by UUID; filter app listings by owner with `--developer`.

## beta / alpha

Both `gcloud beta apigee` and `gcloud alpha apigee` exist and include all GA groups plus two extra groups:

- **`apigee archives`** (beta + alpha) — manage Apigee archive deployments: deploy, list, describe, update, and delete local archive bundles to environments (used for Apigee hybrid / config-as-bundle workflows). E.g. `gcloud beta apigee archives deploy`.
- **`apigee operations`** (beta + alpha) — list and poll long-running asynchronous operations returned by other Apigee calls. E.g. `gcloud beta apigee operations list`.

## Official documentation

- [Apigee API Management docs home](https://cloud.google.com/apigee/docs) — guides, references, quickstarts, and tutorials for the full platform.
- [Get started overview](https://cloud.google.com/apigee/docs/api-platform/get-started/overview) — before-you-begin and provisioning paths by deployment model.
- [Provisioning introduction](https://cloud.google.com/apigee/docs/api-platform/get-started/provisioning-intro) — required API-enable steps and permissions for standing up an org.
- [What is an API product?](https://cloud.google.com/apigee/docs/api-platform/publish/what-api-product) — concepts behind the `apigee products` commands.
- [Apigee IAM roles](https://cloud.google.com/iam/docs/roles-permissions/apigee) — predefined `roles/apigee.*` roles (admin, deployer, apiAdminV2, developerAdmin, environmentAdmin, analyticsViewer, readOnlyAdmin, synchronizerManager).
- [gcloud apigee reference (GA)](https://cloud.google.com/sdk/gcloud/reference/apigee) — full CLI command reference.
- [gcloud beta apigee reference](https://cloud.google.com/sdk/gcloud/reference/beta/apigee) — adds the `archives` and `operations` groups.
