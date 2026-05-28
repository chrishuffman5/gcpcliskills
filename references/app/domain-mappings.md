# gcloud app domain-mappings

view and manage your App Engine domain mappings

### `gcloud app domain-mappings create`

Creates a domain mapping

Creates a domain mapping.

**Synopsis:**
```
gcloud app domain-mappings create DOMAIN [--certificate-id=CERTIFICATE_ID]
    [--certificate-management=CERTIFICATE_MANAGEMENT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DOMAIN
   A valid domain which may begin with a wildcard, such as: example.com or
   *.example.com
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--certificate-id` | CERTIFICATE_ID |  | A certificate id to use for this domain. May not be used on a domain mapping with automatically managed certificates. Use the gcloud app ssl-certificates list to see available certificates for this app. |
| `--certificate-management` | one of: automatic, manual |  | Type of certificate management. 'automatic' will provision an SSL certificate automatically while 'manual' requires the user to provide a certificate id to provision. CERTIFICATE_MANAGEMENT must be one of: automatic, manual. |


**Examples:**
```bash
To create a new App Engine domain mapping with an automatically managed
certificate, run:

    $ gcloud app domain-mappings create 'example.com'

Note: managed certificates do not support wildcard domain mappings.

To create a domain with a manual certificate, run:

    $ gcloud app domain-mappings create '*.example.com' \
      --certificate-management=manual --certificate-id=1234

To create a domain with no associated certificate, run:

    $ gcloud app domain-mappings create '*.example.com' \
      --certificate-management=manual
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/domain-mappings/create)

---
### `gcloud app domain-mappings delete`

Deletes a specified domain mapping

Deletes a specified domain mapping.

**Synopsis:**
```
gcloud app domain-mappings delete DOMAIN [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DOMAIN
   A valid domain which may begin with a wildcard, such as: example.com or
   *.example.com
```

**Examples:**
```bash
To delete an App Engine domain mapping, run:

    $ gcloud app domain-mappings delete '*.example.com'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/domain-mappings/delete)

---
### `gcloud app domain-mappings describe`

Describes a specified domain mapping

Describes a specified domain mapping.

**Synopsis:**
```
gcloud app domain-mappings describe DOMAIN [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DOMAIN
   A valid domain which may begin with a wildcard, such as: example.com or
   *.example.com
```

**Examples:**
```bash
To describe an App Engine domain mapping, run:

    $ gcloud app domain-mappings describe '*.example.com'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/domain-mappings/describe)

---
### `gcloud app domain-mappings list`

Lists domain mappings

Lists domain mappings.

**Synopsis:**
```
gcloud app domain-mappings list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all App Engine domain mappings, run:

    $ gcloud app domain-mappings list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/domain-mappings/list)

---
### `gcloud app domain-mappings update`

Updates a domain mapping

Updates a domain mapping.

**Synopsis:**
```
gcloud app domain-mappings update DOMAIN
    [--certificate-management=CERTIFICATE_MANAGEMENT]
    [--certificate-id=CERTIFICATE_ID | --no-certificate-id]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DOMAIN
   A valid domain which may begin with a wildcard, such as: example.com or
   *.example.com
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--certificate-management` | one of: automatic, manual |  | Type of certificate management. 'automatic' will provision an SSL certificate automatically while 'manual' requires the user to provide a certificate id to provision. CERTIFICATE_MANAGEMENT must be one of: automatic, manual. |


**Examples:**
```bash
To update an App Engine domain mapping, run:

    $ gcloud app domain-mappings update '*.example.com' \
      --certificate-id=1234

To remove a certificate from a domain:

    $ gcloud app domain-mappings update '*.example.com' \
      --no-certificate-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/domain-mappings/update)

---