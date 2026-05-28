# gcloud sql (top-level commands)

### `gcloud sql connect`

Connects to a Cloud SQL instance

Connects to a Cloud SQL instance.

This command temporarily changes the authorized networks for this instance
to allow the connection from your IP address.

This command isn't supported for Cloud SQL instances with only private IP
addresses.

NOTE: If you're connecting from an IPv6 address, or are constrained by
certain organization policies (restrictPublicIP,
restrictAuthorizedNetworks), consider running the beta version of this
command to avoid error by connecting through the Cloud SQL proxy: gcloud
beta sql connect

**Synopsis:**
```
gcloud sql connect INSTANCE [--database=DATABASE, -d DATABASE]
    [--user=USER, -u USER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE, -d DATABASE |  | The SQL Server database to connect to. |
| `--user` | USER, -u USER |  | Cloud SQL instance user to connect as. |


**Examples:**
```bash
To connect to a Cloud SQL instance, run:

    $ gcloud sql connect my-instance --user=root
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/connect)

---
### `gcloud sql generate-login-token`

Generate an IAM login token for Cloud SQL

gcloud sql generate-login-token generates an IAM token to use for logging
in to Cloud SQL instances.

**Synopsis:**
```
gcloud sql generate-login-token [--application-default-credential]
    [--instance=INSTANCE, -i INSTANCE] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application-default-credential` |  |  | Use application default credentials to generate the login token. |
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Examples:**
```bash
To generate an IAM login token using gcloud credentials, run:

    $ gcloud sql generate-login-token

To generate an IAM login token using application default credentials, run:

    $ gcloud sql generate-login-token --application-default-credential

To generate an IAM login token using gcloud credentials for instance
my-instance, run:

    $ gcloud sql generate-login-token --instance=my-instance

To generate an IAM login token using application default credentials for
instance my-instance, run:

    $ gcloud sql generate-login-token --instance=my-instance \
        --application-default-credential
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/generate-login-token)

---
### `gcloud sql reschedule-maintenance`

Reschedule a Cloud SQL instance's maintenance

gcloud sql reschedule-maintenance reschedules a Cloud SQL instance's
maintenance.

**Synopsis:**
```
gcloud sql reschedule-maintenance INSTANCE
    --reschedule-type=RESCHEDULE_TYPE [--schedule-time=SCHEDULE_TIME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--reschedule-type` | one of: IMMEDIATE, NEXT_AVAILABLE_WINDOW, SPECIFIC_TIME |  | The type of reschedule operation to perform. RESCHEDULE_TYPE must be one of: IMMEDIATE, NEXT_AVAILABLE_WINDOW, SPECIFIC_TIME. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--schedule-time` | SCHEDULE_TIME |  | When specifying SPECIFIC_TIME, the date and time at which to schedule the maintenance in ISO 8601 format. |


**Examples:**
```bash
To run maintenance on instance my-instance immediately, run:

    $ gcloud sql reschedule-maintenance my-instance \
        --reschedule-type=IMMEDIATE

To reschedule maintenance on instance my-instance to the next available
window, run:

    $ gcloud sql reschedule-maintenance my-instance \
        --reschedule-type=NEXT_AVAILABLE_WINDOW

To reschedule maintenance on instance my-instance to 2019-11-07 at 4:00 am
UTC, run:

    $ gcloud sql reschedule-maintenance my-instance \
        --reschedule-type=SPECIFIC_TIME \
        --schedule-time=2019-11-07T04:00Z
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/reschedule-maintenance)

---