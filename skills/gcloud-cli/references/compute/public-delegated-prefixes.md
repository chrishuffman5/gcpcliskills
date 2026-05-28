# gcloud compute public-delegated-prefixes

manage public delegated prefix resources

### `gcloud compute public-delegated-prefixes create`

Creates a Compute Engine public delegated prefix

**Synopsis:**
```
gcloud compute public-delegated-prefixes create NAME --range=RANGE
    (--public-advertised-prefix=PUBLIC_ADVERTISED_PREFIX
      | --public-delegated-prefix=PUBLIC_DELEGATED_PREFIX)
    [--allocatable-prefix-length=ALLOCATABLE_PREFIX_LENGTH]
    [--description=DESCRIPTION] [--enable-live-migration] [--mode=MODE]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the public delegated prefix to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--range` | RANGE |  | IP range from this public delegated prefix that should be delegated, in CIDR format. It must be smaller than parent public advertised prefix range. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allocatable-prefix-length` | ALLOCATABLE_PREFIX_LENGTH |  | The allocatable prefix length supported by this PDP. |
| `--description` | DESCRIPTION |  | Description of this public delegated prefix. |
| `--enable-live-migration` |  |  | Specify if this public delegated prefix is meant to be live migrated. |
| `--mode` | one of: delegation, external-ipv6-forwarding-rule-creation, external-ipv6-subnetwork-creation, internal-ipv6-subnetwork-creation |  | Specifies the mode of this IPv6 PDP. MODE must be one of: delegation, external-ipv6-forwarding-rule-creation, external-ipv6-subnetwork-creation, internal-ipv6-subnetwork-creation. |


**Examples:**
```bash
To create a public delegated prefix:

    $ gcloud compute public-delegated-prefixes create \
        my-public-delegated-prefix --public-advertised-prefix=my-pap \
        --range=120.120.10.128/27 --global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/public-delegated-prefixes/create)

---
### `gcloud compute public-delegated-prefixes delete`

Deletes a Compute Engine public delegated prefix

**Synopsis:**
```
gcloud compute public-delegated-prefixes delete NAME
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the public delegated prefix to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the public delegated prefix is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the public delegated prefix to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To delete a public delegated prefix:

    $ gcloud compute public-delegated-prefixes delete \
        my-public-delegated-prefix --global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/public-delegated-prefixes/delete)

---
### `gcloud compute public-delegated-prefixes describe`

Describes a Compute Engine public delegated prefix

**Synopsis:**
```
gcloud compute public-delegated-prefixes describe NAME
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the public delegated prefix to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the public delegated prefix is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the public delegated prefix to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To describe a public delegated prefix:

    $ gcloud compute public-delegated-prefixes describe \
        my-public-delegated-prefix --global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/public-delegated-prefixes/describe)

---
### `gcloud compute public-delegated-prefixes list`

List Google Compute Engine public delegated prefixes

gcloud compute public-delegated-prefixes list displays all Google Compute
Engine public delegated prefixes in a project.

**Synopsis:**
```
gcloud compute public-delegated-prefixes list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all public delegated prefixes in a project in table form, run:

    $ gcloud compute public-delegated-prefixes list

To list the URIs of all public delegated prefixes in a project, run:

    $ gcloud compute public-delegated-prefixes list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/public-delegated-prefixes/list)

---
### `gcloud compute public-delegated-prefixes update`

Updates a Compute Engine public delegated prefix

**Synopsis:**
```
gcloud compute public-delegated-prefixes update NAME
    (--announce-prefix | --withdraw-prefix) [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the public delegated prefix to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--announce-prefix` |  |  | _[Exactly one of these must be specified:]_ Specify if the prefix will be announced. Default is false. |
| `--withdraw-prefix` |  |  | _[Exactly one of these must be specified:]_ Specify if the prefix will be withdrawn. Default is false. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the public delegated prefix to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To announce a regional v2 public delegated prefix:

    $ gcloud compute public-delegated-prefixes update my-pdp \
        --announce-prefix --region=us-central1

To withdraw a regional v2 public delegated prefix:

    $ gcloud compute public-delegated-prefixes update my-pdp \
        --withdraw-prefix --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/public-delegated-prefixes/update)

---

## `gcloud compute public-delegated-prefixes delegated-sub-prefixes` — manage delegated sub prefixes
### `gcloud compute public-delegated-prefixes delegated-sub-prefixes create`

Creates a Compute Engine delegated sub prefix

Creates a Compute Engine delegated sub prefix.

**Synopsis:**
```
gcloud compute public-delegated-prefixes delegated-sub-prefixes create NAME
    --public-delegated-prefix=PUBLIC_DELEGATED_PREFIX
    [--allocatable-prefix-length=ALLOCATABLE_PREFIX_LENGTH]
    [--create-addresses] [--delegatee-project=DELEGATEE_PROJECT]
    [--description=DESCRIPTION] [--mode=MODE] [--range=RANGE]
    [--global-public-delegated-prefix
      | --public-delegated-prefix-region=PUBLIC_DELEGATED_PREFIX_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the delegated sub prefix to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--public-delegated-prefix` | PUBLIC_DELEGATED_PREFIX |  | Name of the public delegated prefix to create the delegate sub prefix for. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allocatable-prefix-length` | ALLOCATABLE_PREFIX_LENGTH |  | Specify allocatable prefix length supported by this sub prefix. |
| `--create-addresses` |  |  | Specify if the sub prefix is delegated to create address resources in the delegatee project. Default is false. |
| `--delegatee-project` | DELEGATEE_PROJECT |  | Project to delegate the IPv4 range specified in --range to. If empty, the sub-range is delegated to the same/existing project. |
| `--description` | DESCRIPTION |  | Description of the delegated sub prefix to create. |
| `--mode` | one of: delegation, external-ipv6-forwarding-rule-creation, external-ipv6-subnetwork-creation, internal-ipv6-subnetwork-creation |  | Specifies the mode of this IPv6 PDP. MODE must be one of: delegation, external-ipv6-forwarding-rule-creation, external-ipv6-subnetwork-creation, internal-ipv6-subnetwork-creation. |
| `--range` | RANGE |  | IPv4 range from this public delegated prefix that should be delegated, in CIDR format. If not specified, the entire range ofthe public advertised prefix is delegated. |


**Examples:**
```bash
To create a delegated sub prefix for a global public delegated prefix:

    $ gcloud compute public-delegated-prefixes delegated-sub-prefixes \
        create my-sub-prefix --range=120.120.10.128/28 \
        --public-delegated-prefix=my-pdp \
        --global-public-delegated-prefix

To create a delegated sub prefix for a regional public delegated prefix:

    $ gcloud compute public-delegated-prefixes delegated-sub-prefixes \
        create my-sub-prefix --range=120.120.10.128/30 \
        --create-addresses --public-delegated-prefix=my-pdp \
        --public-delegated-prefix-region=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/public-delegated-prefixes/delegated-sub-prefixes/create)

---
### `gcloud compute public-delegated-prefixes delegated-sub-prefixes delete`

Deletes a Compute Engine delegated sub prefix

Deletes a Compute Engine delegated sub prefix.

**Synopsis:**
```
gcloud compute public-delegated-prefixes delegated-sub-prefixes delete NAME
    --public-delegated-prefix=PUBLIC_DELEGATED_PREFIX
    [--global-public-delegated-prefix
      | --public-delegated-prefix-region=PUBLIC_DELEGATED_PREFIX_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the delegated sub prefix to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--public-delegated-prefix` | PUBLIC_DELEGATED_PREFIX |  | Name of the public delegated prefix to delete the delegate sub prefix for. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global-public-delegated-prefix` |  |  | _[At most one of these can be specified:]_ If set, the public delegated prefix is global. |
| `--public-delegated-prefix-region` | PUBLIC_DELEGATED_PREFIX_REGION |  | _[At most one of these can be specified:]_ Region of the public delegated prefix to delete the delegate sub prefix for. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To delete a delegated sub prefix for a global public delegated prefix:

    $ gcloud compute public-delegated-prefixes delegated-sub-prefixes \
        delete my-sub-prefix --public-delegated-prefix=my-pdp \
        --global-public-delegated-prefix

To delete a delegated sub prefix for a regional public delegated prefix:

    $ gcloud compute public-delegated-prefixes delegated-sub-prefixes \
        delete my-sub-prefix --public-delegated-prefix=my-pdp \
        --public-delegated-prefix-region=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/public-delegated-prefixes/delegated-sub-prefixes/delete)

---