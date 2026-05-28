# gcloud app ssl-certificates

view and manage your App Engine SSL certificates

### `gcloud app ssl-certificates create`

Uploads a new SSL certificate

The user must be the verified owner of the certificate domain(s). Use the
gcloud domains command group to manage domain ownership and verification.

**Synopsis:**
```
gcloud app ssl-certificates create --certificate=LOCAL_FILE_PATH
    --display-name=DISPLAY_NAME --private-key=LOCAL_FILE_PATH
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--certificate` | LOCAL_FILE_PATH |  | The file path for the new certificate to upload. Must be in PEM x.509 format including the header and footer. |
| `--display-name` | DISPLAY_NAME |  | A display name for this certificate. |
| `--private-key` | LOCAL_FILE_PATH |  | The file path to a local RSA private key file. The private key must be PEM encoded with header and footer and must be 2048 bits or fewer. |


**Examples:**
```bash
To add a new SSL certificate to App Engine, run:

    $ gcloud app ssl-certificates create --display-name='example cert' \
      --certificate='/home/user/me/my_cert.cer' \
      --private-key='/home/user/me/my_key.pfx'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/ssl-certificates/create)

---
### `gcloud app ssl-certificates delete`

Deletes an SSL certificate

Deletes an SSL certificate.

**Synopsis:**
```
gcloud app ssl-certificates delete ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ID
   The id of the certificate. This identifier is printed upon creation of
   a new certificate. Run gcloud app ssl-certificates list to view
   existing certificates.
```

**Examples:**
```bash
To delete an App Engine SSL certificate, run:

    $ gcloud app ssl-certificates delete 1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/ssl-certificates/delete)

---
### `gcloud app ssl-certificates describe`

Describes a specified SSL certificate

Describes a specified SSL certificate.

**Synopsis:**
```
gcloud app ssl-certificates describe ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ID
   The id of the certificate. This identifier is printed upon creation of
   a new certificate. Run gcloud app ssl-certificates list to view
   existing certificates.
```

**Examples:**
```bash
To describe an App Engine SSL certificate, run:

    $ gcloud app ssl-certificates describe 1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/ssl-certificates/describe)

---
### `gcloud app ssl-certificates list`

Lists the SSL certificates

Lists the SSL certificates.

**Synopsis:**
```
gcloud app ssl-certificates list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all App Engine SSL certificates, run:

    $ gcloud app ssl-certificates list

This will return certificates mapped to domain-mappings for the current app
as well as all certificates that apply to domains which the current user
owns.

To view your owned domains, run gcloud domains list-user-verified.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/ssl-certificates/list)

---
### `gcloud app ssl-certificates update`

Updates an SSL certificate

Updates an SSL certificate.

**Synopsis:**
```
gcloud app ssl-certificates update ID [--certificate=LOCAL_FILE_PATH]
    [--display-name=DISPLAY_NAME] [--private-key=LOCAL_FILE_PATH]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ID
   The id of the certificate. This identifier is printed upon creation of
   a new certificate. Run gcloud app ssl-certificates list to view
   existing certificates.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--certificate` | LOCAL_FILE_PATH |  | The file path for the new certificate to upload. Must be in PEM x.509 format including the header and footer. |
| `--display-name` | DISPLAY_NAME |  | A display name for this certificate. |
| `--private-key` | LOCAL_FILE_PATH |  | The file path to a local RSA private key file. The private key must be PEM encoded with header and footer and must be 2048 bits or fewer. |


**Examples:**
```bash
To update an App Engine SSL certificate, run:

    $ gcloud app ssl-certificates update 1234 \
      --display-name='updated name' \
      --certificate='/home/user/me/new_cert.cer' \
      --private-key='/home/user/me/new_key.pfx'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/ssl-certificates/update)

---