# gcloud vmware dns-bind-permission

manage DNS binding permission in Google Cloud VMware Engine

### `gcloud vmware dns-bind-permission describe`

Get all users and service accounts having bind permission

Gets all the users and service accounts having bind permission on the
intranet VPC associated with the consumer project granted by the Grant API.

**Synopsis:**
```
gcloud vmware dns-bind-permission describe [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To get all the users and service accounts having bind permission on the
intranet VPC associated with the consumer project my-project, run:

    $ gcloud vmware dns-bind-permission describe --project=my-project

    Or:

    $ gcloud vmware dns-bind-permission describe

In the second example, the project is taken from gcloud properties
core/project.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/dns-bind-permission/describe)

---
### `gcloud vmware dns-bind-permission grant`

Grants a DNS Bind Permission

Grants the bind permission to the customer provided user/service account to
bind their DNS zone with the intranet VPC associated with the project.

**Synopsis:**
```
gcloud vmware dns-bind-permission grant
    (--service-account=SERVICE_ACCOUNT | --user=USER) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service-account` | SERVICE_ACCOUNT |  | _[Exactly one of these must be specified:]_ The consumer provided service account which needs to be granted permission to bind with the intranet VPC corresponding to the consumer project. If this field is not provided then the user should be provided. |
| `--user` | USER |  | _[Exactly one of these must be specified:]_ The consumer provided user which needs to be granted permission to bind with the intranet VPC corresponding to the consumer project. If this field is not provided then the service-account should be provided. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To grant the bind permission to the customer provided user user@abc.com to
bind their DNS zone with the intranet VPC associated with project
my-project, run:

    $ gcloud vmware dns-bind-permission grant --user=user@abc.com \
        --project=my-project

Or:

    $ gcloud vmware dns-bind-permission grant --user=user@abc.com

In the second example, the project is taken from gcloud properties
core/project.

To grant the bind permission to the customer provided service account
service-account@gserviceaccount.com to bind their DNS zone with the
intranet VPC associated with project my-project, run:

    $ gcloud vmware dns-bind-permission grant \
        --service-account=service-account@gserviceaccount.com \
        --project=my-project

Or:

    $ gcloud vmware dns-bind-permission grant \
        --service-account=service-account@gserviceaccount.com

In the second example, the project is taken from gcloud properties
core/project.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/dns-bind-permission/grant)

---
### `gcloud vmware dns-bind-permission revoke`

Revokes a DNS Bind Permission

Revokes the bind permission from the customer provided user/service account
on the intranet VPC associated with the consumer project.

**Synopsis:**
```
gcloud vmware dns-bind-permission revoke
    (--service-account=SERVICE_ACCOUNT | --user=USER) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service-account` | SERVICE_ACCOUNT |  | _[Exactly one of these must be specified:]_ The consumer provided service account whose permission needs to be revoked on the intranet VPC corresponding to the consumer project. If this field is not provided then the user should be provided. |
| `--user` | USER |  | _[Exactly one of these must be specified:]_ The consumer provided user whose permission needs to be revoked on the intranet VPC corresponding to the consumer project. If this field is not provided then the service-account should be provided. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To revoke the bind permission to the customer provided user user@abc.com on
the intranet VPC associated with the consumer project my-project, run:

    $ gcloud vmware dns-bind-permission revoke --user=user@abc.com \
        --project=my-project

Or:

    $ gcloud vmware dns-bind-permission revoke --user=user@abc.com

In the second example, the project is taken from gcloud properties
core/project.

To revoke the bind permission to the customer provided service account
service-account@gserviceaccount.com on the intranet VPC associated with the
consumer project my-project, run:

    $ gcloud vmware dns-bind-permission revoke \
        --service-account=service-account@gserviceaccount.com \
        --project=my-project

Or:

    $ gcloud vmware dns-bind-permission revoke \
        --service-account=service-account@gserviceaccount.com

In the second example, the project is taken from gcloud properties
core/project.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/dns-bind-permission/revoke)

---