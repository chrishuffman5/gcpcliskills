# gcloud certificate-manager certificates

manage Certificate Manager certificates

### `gcloud certificate-manager certificates create`

Create a certificate

Create a new certificate.

  o Managed certificates can be created by supplying one or more domain
    names and an (optional) list of DNS authorizations for those domain
    names.
  o Self-managed certificates can be created by uploading a certificate
    and its corresponding private key (both in PEM format).

**Synopsis:**
```
gcloud certificate-manager certificates create
    (CERTIFICATE : --location=LOCATION)
    (--certificate-file=PATH_TO_FILE --private-key-file=PATH_TO_FILE
      | [--domains=[DOMAINS,...]
      : --dns-authorizations=[DNS_AUTHORIZATIONS,...]
      | --issuance-config=ISSUANCE_CONFIG]) [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--scope=SCOPE; default="DEFAULT"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate resource - The name of the certificate to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument certificate on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE
     ID of the certificate or fully qualified identifier for the
     certificate.

     To set the certificate attribute:
     + provide the argument certificate on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument certificate on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--certificate-file` | PATH_TO_FILE |  | _[Configuration for uploading self-managed certificates and keys.]_ Certificate data in PEM-encoded form. Use a full or relative path to a local file containing the value of certificate_file. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--private-key-file` | PATH_TO_FILE |  | _[Configuration for uploading self-managed certificates and keys.]_ Private key data in PEM-encoded form. Use a full or relative path to a local file containing the value of private_key_file. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--domains` | [DOMAINS,...] |  | _[Configuration for creating new managed certificates.]_ Public domain name(s) to create a certificate for. - If a DNS authorization is provided for the domain, the certificate will be validated against the DNS record you added as part of the authorization flow. - If no DNS authorization is provided, Certificate Manager will attempt to validate the domain against the serving endpoint directly. You may list multiple, comma-separated domain names to include multiple names as Subject Alternative Names on the issued certificate. This flag argument must be specified if any of the other arguments in this group are specified. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Human-readable description of the resource. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--scope` | one of: all-regions Certificates with scope ALL_REGIONS are currently used for Cross-region Internal Application Load Balancer only | DEFAULT | Scope of the managed certificate. This determines which services the certificate can be attached to/associated with. Defaults to DEFAULT. SCOPE must be one of: all-regions Certificates with scope ALL_REGIONS are currently used for Cross-region Internal Application Load Balancer only. client-auth Certificates with scope CLIENT_AUTH are used for client authentication. default Certificates with DEFAULT scope are used for Load Balancing and Cloud CDN. If unsure, choose this option. edge-cache Certificates with scope EDGE_CACHE are special-purposed certificates, scoped for use with Media Edge services only. |


**Examples:**
```bash
To create (upload) a self-managed certificate called www-example-com, run:

    $ gcloud certificate-manager certificates create www-example-com \
        --private-key-file=key.pem --certificate-file=cert.pem

To create a certificate managed by Certificate Manager called
api-example-com, run:

    $ gcloud certificate-manager certificates create api-example-com \
        --domains="api.example.com"

To create a certificate managed by Certificate Manager called
api-example-com, using an existing DNS authorization, run:

    $ gcloud certificate-manager certificates create api-example-com \
        --dns-authorizations=api-example-com --domains="api.example.com"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/certificates/create)

---
### `gcloud certificate-manager certificates delete`

Delete a certificate

Delete a certificate resource.

**Synopsis:**
```
gcloud certificate-manager certificates delete
    (CERTIFICATE : --location=LOCATION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate resource - The certificate to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument certificate on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE
     ID of the certificate or fully qualified identifier for the
     certificate.

     To set the certificate attribute:
     + provide the argument certificate on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the certificate.

     To set the location attribute:
     + provide the argument certificate on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the certificate with name simple-cert, run:

    $ gcloud certificate-manager certificates delete simple-cert
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/certificates/delete)

---
### `gcloud certificate-manager certificates describe`

Describe an existing certificate

This command fetches and prints information about an existing certificate.

**Synopsis:**
```
gcloud certificate-manager certificates describe
    (CERTIFICATE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate resource - The certificate you want to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument certificate on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE
     ID of the certificate or fully qualified identifier for the
     certificate.

     To set the certificate attribute:
     + provide the argument certificate on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument certificate on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Examples:**
```bash
To describe a certificate with name my-cert, run:

    $ gcloud certificate-manager certificates describe my-cert
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/certificates/describe)

---
### `gcloud certificate-manager certificates list`

List certificates

List Certificate Manager certificates in the project.

**Synopsis:**
```
gcloud certificate-manager certificates list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + if left empty, will use the wildcard '-' to list all locations. |


**Examples:**
```bash
To list all certificates in the project, run:

    $ gcloud certificate-manager certificates list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/certificates/list)

---
### `gcloud certificate-manager certificates update`

Update a certificate

This command updates existing certificate.

**Synopsis:**
```
gcloud certificate-manager certificates update
    (CERTIFICATE : --location=LOCATION) [--description=DESCRIPTION]
    [--certificate-file=PATH_TO_FILE --private-key-file=PATH_TO_FILE]
    [--async] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate resource - The certificate to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument certificate on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE
     ID of the certificate or fully qualified identifier for the
     certificate.

     To set the certificate attribute:
     + provide the argument certificate on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the certificate.

     To set the location attribute:
     + provide the argument certificate on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Examples:**
```bash
To update a certificate with name simple-cert, run:

    $ gcloud certificate-manager certificates update simple-cert \
        --description="desc" --update-labels="key=value" \
        --certificate-file=cert.pem --private-key-file=key.pem
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/certificates/update)

---