# gcloud secrets versions

manage secret versions

### `gcloud secrets versions access`

Access a secret version's data

Access the data for the specified secret version.

**Synopsis:**
```
gcloud secrets versions access (VERSION : --secret=SECRET)
    [--location=LOCATION] [--out-file=OUT-FILE-PATH] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - Numeric secret version to access or a configured alias
(including 'latest' to use the latest version). The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument VERSION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument VERSION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --secret=SECRET
     The secret of the version.

     To set the secret attribute:
     + provide the argument VERSION on the command line with a fully
       specified name;
     + provide the argument --secret on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--out-file` | OUT-FILE-PATH |  | _[* set the property core/project.]_ File path to which secret data is written. If this flag is not provided secret data will be written to stdout in UTF-8 format. |


**Examples:**
```bash
Access the data for version 123 of the secret 'my-secret':

    $ gcloud secrets versions access 123 --secret=my-secret

Note: The output will be formatted as UTF-8 which can corrupt binary
secrets.

To write raw bytes to a file use --out-file flag:

    $ gcloud secrets versions access 123 --secret=my-secret \
        --out-file=/tmp/secret

To get the raw bytes, have Google Cloud CLI print the response as
base64-encoded and decode:

    $ gcloud secrets versions access 123 --secret=my-secret \
        --format='get(payload.data)' | tr '_-' '/+' | base64 -d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/versions/access)

---
### `gcloud secrets versions add`

Create a new version of an existing secret

Create a new version of an existing secret with the provided data. The
command will return an error if no such secret exists.

**Synopsis:**
```
gcloud secrets versions add SECRET --data-file=PATH [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - The secret to create. This represents a Cloud resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-file` | PATH |  | File path from which to read secret data. Set this to "-" to read the secret data from stdin. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
Create a new version of an existing secret named 'my-secret' with secret
data "s3cr3t":

    $ printf "s3cr3t" | gcloud secrets versions add my-secret \
        --data-file=-

Create a new version of an existing secret named 'my-secret' with secret
data "s3cr3t" using PowerShell (Note: PowerShell will add a newline to the
resulting secret):

    $ Write-Output "s3cr3t" | gcloud secrets versions add my-secret \
        --data-file=-

Create a new version of an existing secret named 'my-secret' with secret
data from a file:

    $ gcloud secrets versions add my-secret --data-file=/tmp/secret
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/versions/add)

---
### `gcloud secrets versions describe`

Describe metadata about the secret version

Describe a secret version's metadata. This command does not include the
secret version's secret data.

**Synopsis:**
```
gcloud secrets versions describe (VERSION : --secret=SECRET)
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - Numeric secret version to describe or a configured
alias (including 'latest' to use the latest version). The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument VERSION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument VERSION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --secret=SECRET
     The secret of the version.

     To set the secret attribute:
     + provide the argument VERSION on the command line with a fully
       specified name;
     + provide the argument --secret on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
Describe version '123' of the secret named 'my-secret':

    $ gcloud secrets versions describe 123 --secret=my-secret
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/versions/describe)

---
### `gcloud secrets versions destroy`

Destroy a secret version's metadata and secret data

Destroy a secret version's metadata and secret data. This action is
irreversible.

**Synopsis:**
```
gcloud secrets versions destroy (VERSION : --secret=SECRET) [--etag=ETAG]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - Numeric secret version to destroy. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument VERSION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument VERSION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --secret=SECRET
     The secret of the version.

     To set the secret attribute:
     + provide the argument VERSION on the command line with a fully
       specified name;
     + provide the argument --secret on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Current entity tag (ETag) of the secret version. If specified, the version is destroyed only if the ETag provided matches the current version's ETag. |


**Examples:**
```bash
Destroy version 123 of the secret named my-secret:

    $ gcloud secrets versions destroy 123 --secret=my-secret

Destroy version 123 of the secret named my-secret using etag:

    $ gcloud secrets versions destroy 123 --secret=my-secret --etag=123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/versions/destroy)

---
### `gcloud secrets versions disable`

Disable the version of the provided secret

Disable the version of the provided secret. It can be re-enabled with
gcloud secrets versions enable.

**Synopsis:**
```
gcloud secrets versions disable (VERSION : --secret=SECRET) [--etag=ETAG]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - Numeric secret version to disable. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument VERSION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument VERSION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --secret=SECRET
     The secret of the version.

     To set the secret attribute:
     + provide the argument VERSION on the command line with a fully
       specified name;
     + provide the argument --secret on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Current entity tag (ETag) of the secret version. If specified, the version is disabled only if the ETag provided matches the current version's ETag. |


**Examples:**
```bash
Disable version 123 of the secret named my-secret:

    $ gcloud secrets versions disable 123 --secret=my-secret

Disable version 123 of the secret named my-secret using etag:

    $ gcloud secrets versions disable 123 --secret=my-secret --etag=123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/versions/disable)

---
### `gcloud secrets versions enable`

Enable the version of the provided secret

Enable the version of the provided secret. It can be disabled with gcloud
secrets versions disable.

**Synopsis:**
```
gcloud secrets versions enable (VERSION : --secret=SECRET) [--etag=ETAG]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - Numeric secret version to enable. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument VERSION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument VERSION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --secret=SECRET
     The secret of the version.

     To set the secret attribute:
     + provide the argument VERSION on the command line with a fully
       specified name;
     + provide the argument --secret on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Current entity tag (ETag) of the secret version. If specified, the version is enabled only if the ETag provided matches the current version's ETag. |


**Examples:**
```bash
Enable version 123 of the secret named my-secret:

    $ gcloud secrets versions enable 123 --secret=my-secret

Enable version 123 of the secret named my-secret using etag:

    $ gcloud secrets versions enable 123 --secret=my-secret --etag=123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/versions/enable)

---
### `gcloud secrets versions list`

List all versions for a secret

List all versions and their status (For example: active/disabled/destroyed)
for a secret.

**Synopsis:**
```
gcloud secrets versions list SECRET [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE; default=100] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - The secret from which to list versions. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
List all versions for the secret named 'my-secret':

    $ gcloud secrets versions list my-secret
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/versions/list)

---