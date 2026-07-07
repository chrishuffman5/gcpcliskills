# gcloud sql users

provide commands for managing Cloud SQL users

### `gcloud sql users create`

Creates a user in a given instance

Creates a user in a given instance with specified username, host, type, and
password.

**Synopsis:**
```
gcloud sql users create USERNAME --instance=INSTANCE, -i INSTANCE [--async]
    [--host=HOST] [--password=PASSWORD]
    [--password-policy-allowed-failed-attempts=PASSWORD_POLICY_ALLOWED_FAILED_ATTEMPTS]
    [--[no-]password-policy-enable-failed-attempts-check]
    [--[no-]password-policy-enable-password-verification]
    [--password-policy-password-expiration-duration=PASSWORD_POLICY_PASSWORD_EXPIRATION_DURATION]
    [--type=TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USERNAME
   Cloud SQL username.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--host` | HOST |  | Cloud SQL user's hostname expressed as a specific IP address or address range. % denotes an unrestricted hostname. Applicable flag for MySQL instances; ignored for all other engines. Note, if you connect to your instance using IP addresses, you must add your client IP address as an authorized address, even if your hostname is unrestricted. For more information, see Configure IP (https://cloud.google.com/sql/docs/mysql/configure-ip). |
| `--password` | PASSWORD |  | Cloud SQL user's password. |
| `--password-policy-allowed-failed-attempts` | PASSWORD_POLICY_ALLOWED_FAILED_ATTEMPTS |  | Number of failed login attempts allowed before a user is locked out. |
| `--[no-]password-policy-enable-failed-attempts-check` |  |  | Enables the failed login attempts check if set to true. Use --password-policy-enable-failed-attempts-check to enable and --no-password-policy-enable-failed-attempts-check to disable. |
| `--[no-]password-policy-enable-password-verification` |  |  | The current password must be specified when altering the password. Use --password-policy-enable-password-verification to enable and --no-password-policy-enable-password-verification to disable. |
| `--password-policy-password-expiration-duration` | PASSWORD_POLICY_PASSWORD_EXPIRATION_DURATION |  | Expiration duration after a password is updated, for example, 2d for 2 days. See gcloud topic datetimes for information on duration formats. |
| `--type` | TYPE |  | Cloud SQL user's type. It determines the method to authenticate the user during login. See the list of user types at https://cloud.google.com/sql/docs/postgres/admin-api/rest/v1beta4/SqlUserType |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/users/create)

---
### `gcloud sql users delete`

Deletes a Cloud SQL user in a given instance

Deletes a Cloud SQL user in a given instance specified by username and
host.

**Synopsis:**
```
gcloud sql users delete USERNAME --instance=INSTANCE, -i INSTANCE [--async]
    [--host=HOST] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USERNAME
   Cloud SQL username.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--host` | HOST |  | Cloud SQL user's hostname expressed as a specific IP address or address range. % denotes an unrestricted hostname. Applicable flag for MySQL instances; ignored for all other engines. Note, if you connect to your instance using IP addresses, you must add your client IP address as an authorized address, even if your hostname is unrestricted. For more information, see Configure IP (https://cloud.google.com/sql/docs/mysql/configure-ip). |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/users/delete)

---
### `gcloud sql users describe`

Retrieves information about a Cloud SQL user in a given instance

Retrieves information about a Cloud SQL user in a given instance.

**Synopsis:**
```
gcloud sql users describe USERNAME --instance=INSTANCE, -i INSTANCE
    [--host=HOST] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USERNAME
   Cloud SQL username.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--host` | HOST |  | Cloud SQL user's hostname expressed as a specific IP address or address range. % denotes an unrestricted hostname. Applicable flag for MySQL instances; ignored for all other engines. Note, if you connect to your instance using IP addresses, you must add your client IP address as an authorized address, even if your hostname is unrestricted. For more information, see Configure IP (https://cloud.google.com/sql/docs/mysql/configure-ip). |


**Examples:**
```bash
To fetch a user with name 'my-user' and optional host '%' in instance
'my-instance', run:

    $ gcloud sql users describe my-user --host=% --instance=my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/users/describe)

---
### `gcloud sql users list`

Lists Cloud SQL users in a given instance

Lists Cloud SQL users in a given instance in the alphabetical order of the
user name.

**Synopsis:**
```
gcloud sql users list --instance=INSTANCE, -i INSTANCE
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/users/list)

---
### `gcloud sql users set-password`

Changes a user's password in a given instance

Changes a user's password in a given instance with specified username and
host.

**Synopsis:**
```
gcloud sql users set-password USERNAME --instance=INSTANCE, -i INSTANCE
    [--async] [--host=HOST] [--discard-dual-password | --retain-password]
    [--password=PASSWORD | --prompt-for-password] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USERNAME
   Cloud SQL username.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--host` | HOST |  | Cloud SQL user's hostname expressed as a specific IP address or address range. % denotes an unrestricted hostname. Applicable flag for MySQL instances; ignored for all other engines. Note, if you connect to your instance using IP addresses, you must add your client IP address as an authorized address, even if your hostname is unrestricted. For more information, see Configure IP (https://cloud.google.com/sql/docs/mysql/configure-ip). |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/users/set-password)

---
### `gcloud sql users set-password-policy`

Replaces a user's password policy in a given instance

Replaces a user's password policy in a given instance with a specified
username and host.

**Synopsis:**
```
gcloud sql users set-password-policy USERNAME --instance=INSTANCE, -i
    INSTANCE [--async] [--clear-password-policy] [--host=HOST]
    [--password-policy-allowed-failed-attempts=PASSWORD_POLICY_ALLOWED_FAILED_ATTEMPTS]
    [--[no-]password-policy-enable-failed-attempts-check]
    [--[no-]password-policy-enable-password-verification]
    [--password-policy-password-expiration-duration=PASSWORD_POLICY_PASSWORD_EXPIRATION_DURATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USERNAME
   Cloud SQL username.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--clear-password-policy` |  |  | Clear the existing password policy. This flag is only available for Postgres. |
| `--host` | HOST |  | Cloud SQL user's hostname expressed as a specific IP address or address range. % denotes an unrestricted hostname. Applicable flag for MySQL instances; ignored for all other engines. Note, if you connect to your instance using IP addresses, you must add your client IP address as an authorized address, even if your hostname is unrestricted. For more information, see Configure IP (https://cloud.google.com/sql/docs/mysql/configure-ip). |
| `--password-policy-allowed-failed-attempts` | PASSWORD_POLICY_ALLOWED_FAILED_ATTEMPTS |  | Number of failed login attempts allowed before a user is locked out. |
| `--[no-]password-policy-enable-failed-attempts-check` |  |  | Enables the failed login attempts check if set to true. Use --password-policy-enable-failed-attempts-check to enable and --no-password-policy-enable-failed-attempts-check to disable. |
| `--[no-]password-policy-enable-password-verification` |  |  | The current password must be specified when altering the password. Use --password-policy-enable-password-verification to enable and --no-password-policy-enable-password-verification to disable. |
| `--password-policy-password-expiration-duration` | PASSWORD_POLICY_PASSWORD_EXPIRATION_DURATION |  | Expiration duration after a password is updated, for example, 2d for 2 days. See gcloud topic datetimes for information on duration formats. |


**Examples:**
```bash
To replace the password policy with 2 minutes password expiration time for
my-user in instance prod-instance, run:

    $ gcloud sql users set-password-policy my-user \
        --instance=prod-instance \
        --password-policy-password-expiration-duration=2m

To clear the existing password policy of my-user in instance prod-instance,
run:

    $ gcloud sql users set-password-policy my-user \
        --instance=prod-instance --clear-password-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/users/set-password-policy)

---