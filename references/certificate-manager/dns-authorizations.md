# gcloud certificate-manager dns-authorizations

manage Certificate Manager DNS authorizations

### `gcloud certificate-manager dns-authorizations create`

Create a DNS Authorization

Create a new DNS Authorization.

**Synopsis:**
```
gcloud certificate-manager dns-authorizations create
    (DNS_AUTHORIZATION : --location=LOCATION) --domain=DOMAIN [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]] [--type=TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DnsAuthorization resource - The name of the DNS Authorization to create.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dns_authorization on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DNS_AUTHORIZATION
     ID of the dnsAuthorization or fully qualified identifier for the
     dnsAuthorization.

     To set the dns_authorization attribute:
     + provide the argument dns_authorization on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument dns_authorization on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--domain` | DOMAIN |  | Public domain name to create an authorization for. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Human-readable description of the resource. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--type` | one of: fixed-record, per-project-record, type-unspecified |  | Type of the DNS authorization. TYPE must be one of: fixed-record, per-project-record, type-unspecified. |


**Examples:**
```bash
To create a DNS authorization called my-authorization, run:

    $ gcloud certificate-manager dns-authorizations create \
        my-authorization --domain=host.example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/dns-authorizations/create)

---
### `gcloud certificate-manager dns-authorizations delete`

Delete a DNS Authorization

Delete a DNS Authorization.

**Synopsis:**
```
gcloud certificate-manager dns-authorizations delete
    (DNS_AUTHORIZATION : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DnsAuthorization resource - The name of the DNS Authorization to delete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dns_authorization on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DNS_AUTHORIZATION
     ID of the dnsAuthorization or fully qualified identifier for the
     dnsAuthorization.

     To set the dns_authorization attribute:
     + provide the argument dns_authorization on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument dns_authorization on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a DNS Authorization called my-authorization, run:

    $ gcloud certificate-manager dns-authorizations delete \
        my-authorization
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/dns-authorizations/delete)

---
### `gcloud certificate-manager dns-authorizations describe`

Show details about a DNS Authorization

Show details about a DNS Authorization.

**Synopsis:**
```
gcloud certificate-manager dns-authorizations describe
    (DNS_AUTHORIZATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DnsAuthorization resource - The DNS Authorization you want to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dns_authorization on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DNS_AUTHORIZATION
     ID of the dnsAuthorization or fully qualified identifier for the
     dnsAuthorization.

     To set the dns_authorization attribute:
     + provide the argument dns_authorization on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument dns_authorization on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Examples:**
```bash
To show details about an existing authorization, run:

    $ gcloud certificate-manager dns-authorizations describe \
        my-authorization
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/dns-authorizations/describe)

---
### `gcloud certificate-manager dns-authorizations list`

List all DNS Authorizations in a project

List existing DNS Authorizations.

**Synopsis:**
```
gcloud certificate-manager dns-authorizations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + if left empty, will use the wildcard '-' to list all locations. |


**Examples:**
```bash
To list existing DNS authorizations, run:

    $ gcloud certificate-manager dns-authorizations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/dns-authorizations/list)

---
### `gcloud certificate-manager dns-authorizations update`

Update a DNS Authorization

Update a DNS Authorization.

**Synopsis:**
```
gcloud certificate-manager dns-authorizations update
    (DNS_AUTHORIZATION : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DnsAuthorization resource - The name of the DNS Authorization to delete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dns_authorization on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DNS_AUTHORIZATION
     ID of the dnsAuthorization or fully qualified identifier for the
     dnsAuthorization.

     To set the dns_authorization attribute:
     + provide the argument dns_authorization on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument dns_authorization on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Human-readable description of the resource. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To Update a DNS Authorization called my-authorization, run:

    $ gcloud certificate-manager dns-authorizations update \
        my-authorization
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/dns-authorizations/update)

---