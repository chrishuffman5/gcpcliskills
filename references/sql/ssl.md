# gcloud sql ssl

provide commands for managing SSL certificates of Cloud SQL instances


## `gcloud sql ssl client-certs` — provide commands for managing client certificates of Cloud SQL instances
### `gcloud sql ssl client-certs create`

Create a client certificate for a Cloud SQL instance

Create a client certificate for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql ssl client-certs create COMMON_NAME CERT_FILE
    --instance=INSTANCE, -i INSTANCE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
COMMON_NAME
   User supplied name. Constrained to [a-zA-Z.-_ ]+.

CERT_FILE
   Location of file which the private key of the created ssl-cert will be
   written to.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl/client-certs/create)

---
### `gcloud sql ssl client-certs delete`

Delete a client certificate for a Cloud SQL instance

Delete a client certificate for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql ssl client-certs delete COMMON_NAME --instance=INSTANCE, -i
    INSTANCE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
COMMON_NAME
   User supplied name. Constrained to [a-zA-Z.-_ ]+.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl/client-certs/delete)

---
### `gcloud sql ssl client-certs describe`

Retrieve information about a client cert for a Cloud SQL instance

Retrieve information about a client cert for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql ssl client-certs describe COMMON_NAME --instance=INSTANCE, -i
    INSTANCE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
COMMON_NAME
   User supplied name. Constrained to [a-zA-Z.-_ ]+.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl/client-certs/describe)

---
### `gcloud sql ssl client-certs list`

List all client certs for a Cloud SQL instance

List all client certs for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql ssl client-certs list --instance=INSTANCE, -i INSTANCE
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl/client-certs/list)

---

## `gcloud sql ssl server-ca-certs` — provide commands for managing server CA certs of Cloud SQL instances
### `gcloud sql ssl server-ca-certs create`

Create a server CA cert for a Cloud SQL instance

Create a server CA cert for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql ssl server-ca-certs create --instance=INSTANCE, -i INSTANCE
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl/server-ca-certs/create)

---
### `gcloud sql ssl server-ca-certs list`

List all server CA certs for a Cloud SQL instance

List all server CA certs for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql ssl server-ca-certs list --instance=INSTANCE, -i INSTANCE
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl/server-ca-certs/list)

---
### `gcloud sql ssl server-ca-certs rollback`

Roll back to the previous server CA cert for a Cloud SQL instance

Roll back to the previous server CA cert for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql ssl server-ca-certs rollback --instance=INSTANCE, -i INSTANCE
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl/server-ca-certs/rollback)

---
### `gcloud sql ssl server-ca-certs rotate`

Rotate in the upcoming server CA cert for a Cloud SQL instance

Rotate in the upcoming server CA cert for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql ssl server-ca-certs rotate --instance=INSTANCE, -i INSTANCE
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl/server-ca-certs/rotate)

---

## `gcloud sql ssl server-certs` — provide commands for managing server certificates of Cloud SQL instances
### `gcloud sql ssl server-certs create`

Create a server certificate for a Cloud SQL instance

Create a server certificate for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql ssl server-certs create --instance=INSTANCE, -i INSTANCE
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl/server-certs/create)

---
### `gcloud sql ssl server-certs list`

List all server certificates for a Cloud SQL instance

List all server certificates for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql ssl server-certs list --instance=INSTANCE, -i INSTANCE
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl/server-certs/list)

---
### `gcloud sql ssl server-certs rollback`

Roll back to the previous server certificate for a Cloud SQL instance

Roll back to the previous server certificate for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql ssl server-certs rollback --instance=INSTANCE, -i INSTANCE
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl/server-certs/rollback)

---
### `gcloud sql ssl server-certs rotate`

Rotate in the upcoming server certificate for a Cloud SQL instance

Rotate in the upcoming server certificate for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql ssl server-certs rotate --instance=INSTANCE, -i INSTANCE
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl/server-certs/rotate)

---