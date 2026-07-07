# gcloud alloydb users

provide commands for managing AlloyDB users

### `gcloud alloydb users create`

Creates a user in a given cluster

Creates a user in a given cluster with specified username, cluster, region,
type, and password.

**Synopsis:**
```
gcloud alloydb users create USERNAME --cluster=CLUSTER --region=REGION
    [--db-roles=[ROLE,...]] [--keep-extra-roles=KEEP_EXTRA_ROLES]
    [--password=PASSWORD] [--superuser=SUPERUSER]
    [--type=TYPE; default="BUILT_IN"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USERNAME
   AlloyDB username
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | AlloyDB cluster ID |
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--db-roles` | [ROLE,...] |  | Comma separated list of database roles this new user will be granted upon creation. |
| `--keep-extra-roles` | KEEP_EXTRA_ROLES |  | If the user already exists and has extra roles, keep them. |
| `--password` | PASSWORD |  | Password for this database user. |
| `--superuser` | SUPERUSER |  | If true, new user will have AlloyDB superuser privileges. Default value is false. |
| `--type` | TYPE | BUILT_IN | Type corresponds to the user type. TYPE must be one of: BUILT_IN This database user can authenticate via password-based authentication IAM_BASED This database user can authenticate via IAM-based authentication |


**Examples:**
```bash
To create a new user, run:

    $ gcloud alloydb users create my-username --cluster=my-cluster \
        --region=us-central1 --password=postgres
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/users/create)

---
### `gcloud alloydb users delete`

Deletes an AlloyDB user in a given cluster

Deletes an AlloyDB user in a given cluster.

**Synopsis:**
```
gcloud alloydb users delete USERNAME --cluster=CLUSTER --region=REGION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USERNAME
   AlloyDB username
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | AlloyDB cluster ID |
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Examples:**
```bash
To delete an user, run:

    $ gcloud alloydb users delete my-username --cluster=my-cluster \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/users/delete)

---
### `gcloud alloydb users list`

Lists AlloyDB users in a given cluster

Lists AlloyDB users in a given cluster.

**Synopsis:**
```
gcloud alloydb users list --cluster=CLUSTER --region=REGION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | AlloyDB cluster ID |
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Examples:**
```bash
To list users, run:

    $ gcloud alloydb users list --cluster=my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/users/list)

---
### `gcloud alloydb users set-password`

Update an AlloyDB user's password within a given cluster and region

Update an AlloyDB user's password within a given cluster and region.

**Synopsis:**
```
gcloud alloydb users set-password USERNAME --cluster=CLUSTER
    --password=PASSWORD --region=REGION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USERNAME
   AlloyDB username
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | AlloyDB cluster ID |
| `--password` | PASSWORD |  | Password for this database user. |
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Examples:**
```bash
To update a user's password, run:

    $ gcloud alloydb users set-password my-username \
        --cluster=my-cluster --region=us-central1 --password=postgres
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/users/set-password)

---
### `gcloud alloydb users set-roles`

Update an AlloyDB user's database roles within a given cluster and region

Update an AlloyDB user's database roles within a given cluster and region.

**Synopsis:**
```
gcloud alloydb users set-roles USERNAME --cluster=CLUSTER
    --db-roles=[ROLE,...] --region=REGION
    [--keep-extra-roles=KEEP_EXTRA_ROLES] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USERNAME
   AlloyDB username
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | AlloyDB cluster ID |
| `--db-roles` | [ROLE,...] |  | Comma separated list of database roles this new user will be granted upon creation. |
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--keep-extra-roles` | KEEP_EXTRA_ROLES |  | If the user already exists and has extra roles, keep them. |


**Examples:**
```bash
To update a user's database roles, run:

    $ gcloud alloydb users set-roles my-username --cluster=my-cluster \
        --region=us-central1 --db-roles=role1,role2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/users/set-roles)

---
### `gcloud alloydb users set-superuser`

Update an AlloyDB user's superuser role within a given cluster and region

Update an AlloyDB user's superuser role within a given cluster and region.

**Synopsis:**
```
gcloud alloydb users set-superuser USERNAME --cluster=CLUSTER
    --region=REGION --superuser=SUPERUSER [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USERNAME
   AlloyDB username
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | AlloyDB cluster ID |
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |
| `--superuser` | SUPERUSER |  | If true, user will have AlloyDB superuser privileges |


**Examples:**
```bash
To update a user's superuser role, run:

    $ gcloud alloydb users set-superuser my-username \
        --cluster=my-cluster --region=us-central1 --superuser=true/false
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/users/set-superuser)

---