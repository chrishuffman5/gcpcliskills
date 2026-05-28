# gcloud storage hmac

manage Cloud Storage service account HMAC keys

### `gcloud storage hmac create`

Add a service account HMAC

gcloud storage hmac create command creates an HMAC key for the specified
service account. The secret key material is only available upon creation,
so be sure to store the returned secret along with the access_id.

**Synopsis:**
```
gcloud storage hmac create SERVICE_ACCOUNT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE_ACCOUNT
   The service account email.
```

**Examples:**
```bash
To create an HMAC key for
test.service.account@test_project.iam.gserviceaccount.com:

    $ gcloud storage hmac create \
        test.service.account@test_project.iam.gserviceaccount.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/hmac/create)

---
### `gcloud storage hmac delete`

Remove a service account HMAC

gcloud storage hmac delete permanently deletes the specified HMAC key. Note
that keys must be updated to be in the INACTIVE state before they can be
deleted.

**Synopsis:**
```
gcloud storage hmac delete ACCESS_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ACCESS_ID
   Access ID for HMAC key to delete.
```

**Examples:**
```bash
To delete a specific HMAC key:

    $ gcloud storage hmac delete GOOG56JBMFZX6PMPTQ62VD2

To be prompted for HMAC keys to delete:

    $ gcloud storage hmac delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/hmac/delete)

---
### `gcloud storage hmac describe`

Describes a service account HMAC key

gcloud storage hmac describe retrieves the specified HMAC key's metadata.
Note that there is no option to retrieve a key's secret material after it
has been created.

**Synopsis:**
```
gcloud storage hmac describe ACCESS_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ACCESS_ID
   The Access ID
   (https://cloud.google.com/storage/docs/authentication/hmackeys#overview)
   of the HMAC key
```

**Examples:**
```bash
The following command retrieves the HMAC key's metadata:

    $ gcloud storage hmac describe GOOG56JBMFZX6PMPTQ62VD2

Note GOOG56JBMFZX6PMPTQ62VD2 is the ACCESS_ID of the HMAC key.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/hmac/describe)

---
### `gcloud storage hmac list`

List service account HMAC keys

gcloud storage hmac list lists the HMAC key metadata for keys in the
current project.

**Synopsis:**
```
gcloud storage hmac list [--all, -a] [--long, -l]
    [--service-account=SERVICE_ACCOUNT, -u SERVICE_ACCOUNT]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all, -a` |  |  | Shows all keys, including recently deleted keys. |
| `--long, -l` |  |  | Use long listing format, showing the full metadata for each key excluding the secret. |
| `--service-account` | SERVICE_ACCOUNT, -u SERVICE_ACCOUNT |  | Filter keys for the provided service account email. |


**Examples:**
```bash
To show metadata for all keys, including recently deleted keys:

    $ gcloud storage hmac list --all --long

To list only HMAC keys belonging to the service account
test.sa@test.iam.gserviceaccount.com:

    $ gcloud storage hmac list \
        --service-account=test.sa@test.iam.gserviceaccount.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/hmac/list)

---
### `gcloud storage hmac update`

Change the status of a service account HMAC

gcloud storage hmac update sets the state of the specified key. Valid state
arguments are ACTIVE and INACTIVE. To set a key to state DELETED, use
gcloud storage hmac delete on an INACTIVE key. If an etag is set in the
command, it will only succeed if the provided etag matches the etag of the
stored key.

**Synopsis:**
```
gcloud storage hmac update ACCESS_ID (--activate | --deactivate)
    [--etag=ETAG, -e ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ACCESS_ID
   Access ID for HMAC key to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--activate` |  |  | _[Exactly one of these must be specified:]_ Sets the state of the specified key to ACTIVE. |
| `--deactivate` |  |  | _[Exactly one of these must be specified:]_ Sets the state of the specified key to INACTIVE. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG, -e ETAG |  | If provided, the update will only be performed if the specified etag matches the etag of the stored key. |


**Examples:**
```bash
To activate an HMAC key:

    $ gcloud storage hmac update GOOG56JBMFZX6PMPTQ62VD2 --activate

To set the state of an HMAC key to INACTIVE provided its etag is M42da=:

    $ gcloud storage hmac update GOOG56JBMFZX6PMPTQ62VD2 --deactivate \
        --etag=M42da=
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/hmac/update)

---