# gcloud sql ssl-certs

provide commands for managing SSL certificates of Cloud SQL instances

### `gcloud sql ssl-certs create`

Creates an SSL certificate for a Cloud SQL instance

(DEPRECATED) Creates an SSL certificate for a Cloud SQL instance.

gcloud sql ssl-certs is deprecated. Use gcloud sql ssl client-certs
instead.

**Synopsis:**
```
gcloud sql ssl-certs create COMMON_NAME CERT_FILE --instance=INSTANCE, -i
    INSTANCE [GCLOUD_WIDE_FLAG ...]
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


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl-certs/create)

---
### `gcloud sql ssl-certs delete`

Deletes an SSL certificate for a Cloud SQL instance

(DEPRECATED) Deletes an SSL certificate for a Cloud SQL instance.

gcloud sql ssl-certs is deprecated. Use gcloud sql ssl client-certs
instead.

**Synopsis:**
```
gcloud sql ssl-certs delete COMMON_NAME --instance=INSTANCE, -i INSTANCE
    [--async] [GCLOUD_WIDE_FLAG ...]
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


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl-certs/delete)

---
### `gcloud sql ssl-certs describe`

Retrieves information about an SSL cert for a Cloud SQL instance

(DEPRECATED) Retrieves information about an SSL cert for a Cloud SQL
instance.

gcloud sql ssl-certs is deprecated. Use gcloud sql ssl client-certs
instead.

**Synopsis:**
```
gcloud sql ssl-certs describe COMMON_NAME --instance=INSTANCE, -i INSTANCE
    [GCLOUD_WIDE_FLAG ...]
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


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl-certs/describe)

---
### `gcloud sql ssl-certs list`

Lists all SSL certs for a Cloud SQL instance

(DEPRECATED) Lists all SSL certs for a Cloud SQL instance.

gcloud sql ssl-certs is deprecated. Use gcloud sql ssl client-certs
instead.

**Synopsis:**
```
gcloud sql ssl-certs list --instance=INSTANCE, -i INSTANCE
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/ssl-certs/list)

---