# gcloud privateca subordinates

manage subordinate certificate authorities

### `gcloud privateca subordinates activate`

Activate a subordinate certificate authority awaiting user activation

**Synopsis:**
```
gcloud privateca subordinates activate
    (CERTIFICATE_AUTHORITY : --location=LOCATION --pool=POOL)
    --pem-chain=PEM_CHAIN [--auto-enable] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE AUTHORITY resource - The certificate authority to activate.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument CERTIFICATE_AUTHORITY on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_AUTHORITY
     ID of the CERTIFICATE_AUTHORITY or fully qualified identifier for the
     CERTIFICATE_AUTHORITY.

     To set the certificate_authority attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CERTIFICATE_AUTHORITY.

     To set the location attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.

  --pool=POOL
     The parent CA Pool of the CERTIFICATE_AUTHORITY.

     To set the pool attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --pool on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--pem-chain` | PEM_CHAIN |  | A file containing a list of PEM-encoded certificates, starting with the current CA certificate and ending with the root CA certificate. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auto-enable` |  |  | If this flag is set, the Certificate Authority will be automatically enabled upon creation. |


**Examples:**
```bash
To activate a subordinate CA named 'server-tls-1' in the location
'us-west1'

and CA Pool 'server-tls-pool' using a PEM certificate chain in 'chain.crt':

    $ gcloud privateca subordinates activate server-tls-1 \
        --location=us-west1 --pool=server-tls-pool \
        --pem-chain=./chain.crt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/subordinates/activate)

---
### `gcloud privateca subordinates create`

Create a new subordinate certificate authority

**Synopsis:**
```
gcloud privateca subordinates create
    (CERTIFICATE_AUTHORITY : --location=LOCATION --pool=POOL)
    (--create-csr --csr-output-file=CSR_OUTPUT_FILE
      | [--issuer-pool=ISSUER_POOL : --issuer-location=ISSUER_LOCATION])
    [--auto-enable] [--bucket=BUCKET]
    [--custom-aia-urls=[CUSTOM_AIA_URLS,...]]
    [--custom-cdp-urls=[CUSTOM_CDP_URLS,...]] [--dns-san=[DNS_SAN,...]]
    [--email-san=[EMAIL_SAN,...]] [--from-ca=FROM_CA]
    [--ip-san=[IP_SAN,...]] [--issuer-ca=ISSUER_CA]
    [--labels=[KEY=VALUE,...]] [--subject=[SUBJECT,...]]
    [--subject-key-id=SUBJECT_KEY_ID] [--uri-san=[URI_SAN,...]]
    [--validity=VALIDITY; default="P3Y"]
    [--key-algorithm=KEY_ALGORITHM; default="rsa-pkcs1-2048-sha256"
      | [--kms-key-version=KMS_KEY_VERSION : --kms-key=KMS_KEY
      --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]]
    [--use-preset-profile=USE_PRESET_PROFILE
      | --extended-key-usages=[EXTENDED_KEY_USAGES,...]
      --key-usages=[KEY_USAGES,...] --max-chain-length=MAX_CHAIN_LENGTH
      | --unconstrained-chain-length --no-name-constraints-critical
      --name-excluded-dns=[NAME_EXCLUDED_DNS,...]
      --name-excluded-email=[NAME_EXCLUDED_EMAIL,...]
      --name-excluded-ip=[NAME_EXCLUDED_IP,...]
      --name-excluded-uri=[NAME_EXCLUDED_URI,...]
      --name-permitted-dns=[NAME_PERMITTED_DNS,...]
      --name-permitted-email=[NAME_PERMITTED_EMAIL,...]
      --name-permitted-ip=[NAME_PERMITTED_IP,...]
      --name-permitted-uri=[NAME_PERMITTED_URI,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate Authority resource - The name of the subordinate CA to create.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument CERTIFICATE_AUTHORITY on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_AUTHORITY
     ID of the Certificate Authority or fully qualified identifier for the
     Certificate Authority.

     To set the certificate_authority attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Certificate Authority.

     To set the location attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.

  --pool=POOL
     The parent CA Pool of the Certificate Authority.

     To set the pool attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --pool on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--create-csr` |  |  | _[settings:]_ Indicates that a CSR should be generated which can be signed by the issuing CA. This must be set if --issuer is not provided. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--csr-output-file` | CSR_OUTPUT_FILE |  | _[settings:]_ The path where the resulting PEM-encoded CSR file should be written. This flag argument must be specified if any of the other arguments in this group are specified. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auto-enable` |  |  | If this flag is set, the Certificate Authority will be automatically enabled upon creation. |
| `--bucket` | BUCKET |  | The name of an existing storage bucket to use for storing the CA certificates and CRLs for CAs in this pool. If omitted, a new bucket will be created and managed by the service on your behalf. |
| `--custom-aia-urls` | [CUSTOM_AIA_URLS,...] |  | One or more comma-separated URLs that will be added to the Authority Information Access extension in the issued certificate. These URLs are where the issuer CA certificate is located. |
| `--custom-cdp-urls` | [CUSTOM_CDP_URLS,...] |  | One or more comma-separated URLs that will be added to the CRL Distribution Points (CDP) extension in the issued certificate. These URLs are where CRL information is located. |
| `--dns-san` | [DNS_SAN,...] |  | One or more comma-separated DNS Subject Alternative Names. |
| `--email-san` | [EMAIL_SAN,...] |  | One or more comma-separated email Subject Alternative Names. |
| `--ip-san` | [IP_SAN,...] |  | _[+ provide the argument --from-ca on the command line.]_ One or more comma-separated IP Subject Alternative Names. |
| `--issuer-ca` | ISSUER_CA |  | _[+ provide the argument --from-ca on the command line.]_ The Certificate Authority ID of the CA to issue the subordinate CA certificate from. This ID is optional. If ommitted, any available ENABLED CA in the issuing CA pool will be chosen. |
| `--labels` | [KEY=VALUE,...] |  | _[+ provide the argument --from-ca on the command line.]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--subject` | [SUBJECT,...] |  | _[+ provide the argument --from-ca on the command line.]_ X.501 name of the certificate subject. Example: --subject "C=US,ST=California,L=Mountain View,O=Google LLC,CN=google.com" |
| `--subject-key-id` | SUBJECT_KEY_ID |  | _[+ provide the argument --from-ca on the command line.]_ Optional field to specify subject key ID for certificate. DO NOT USE except to maintain a previously established identifier for a public key, whose SKI was not generated using method (1) described in RFC 5280 section 4.2.1.2. |
| `--uri-san` | [URI_SAN,...] |  | _[+ provide the argument --from-ca on the command line.]_ One or more comma-separated URI Subject Alternative Names. |
| `--validity` | VALIDITY | P3Y | _[+ provide the argument --from-ca on the command line.]_ The validity of this CA, as an ISO8601 duration. Defaults to 3 years. |


**Examples:**
```bash
To create a subordinate CA named 'server-tls-1' whose issuer is on Private
CA:

    $ gcloud privateca subordinates create server-tls-1 \
        --location=us-west1 --pool=my-pool \
        --subject="CN=Example TLS CA, O=Google" \
        --issuer-pool=other-pool --issuer-location=us-west1 \
        --kms-key-version="projects/my-project-pki/locations/us-west1/ke\
    yRings/kr1/cryptoKeys/key2/cryptoKeyVersions/1"

To create a subordinate CA named 'server-tls-1' whose issuer is located
elsewhere:

    $ gcloud privateca subordinates create server-tls-1 \
        --location=us-west1 --pool=my-pool \
        --subject="CN=Example TLS CA, O=Google" --create-csr \
        --csr-output-file=./csr.pem \
        --kms-key-version="projects/my-project-pki/locations/us-west1/ke\
    yRings/kr1/cryptoKeys/key2/cryptoKeyVersions/1"

To create a subordinate CA named 'server-tls-1' chaining up to a root CA
named 'prod-root' based on an existing CA:

    $ gcloud privateca subordinates create server-tls-1 \
        --location=us-west1 --pool=my-pool --issuer-pool=other-pool \
        --issuer-location=us-west1 --from-ca=source-ca \
        --kms-key-version="projects/my-project-pki/locations/us-west1/ke\
    yRings/kr1/cryptoKeys/key2/cryptoKeyVersions/1"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/subordinates/create)

---
### `gcloud privateca subordinates delete`

Delete a subordinate certificate authority

Delete a Subordinate Certificate Authority. Deleted Subordinate Certificate
Authorities may be recovered with the gcloud privateca subordinates
undelete command within a grace period of 30 days.

Use the --skip-grace-period flag to delete as soon as possible without the
30-day grace period to undelete.

Note that any user-managed KMS keys or Google Cloud Storage buckets will
not be affected by this operation. You will need to delete the user-
managed resources separately once the CA is deleted. Any Google-managed
resources will be cleaned up.

The CA specified in this command MUST:

    1) be in the DISABLED or STAGED state.
    2) have no un-revoked or un-expired certificates. Use the revoke command
       to revoke any active certificates.

Use the --ignore-active-certificates flag to remove 2) as a requirement.

**Synopsis:**
```
gcloud privateca subordinates delete
    (CERTIFICATE_AUTHORITY : --location=LOCATION --pool=POOL)
    [--ignore-active-certificates] [--ignore-dependent-resources]
    [--skip-grace-period] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE AUTHORITY resource - The certificate authority to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument CERTIFICATE_AUTHORITY on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_AUTHORITY
     ID of the CERTIFICATE_AUTHORITY or fully qualified identifier for the
     CERTIFICATE_AUTHORITY.

     To set the certificate_authority attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CERTIFICATE_AUTHORITY.

     To set the location attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.

  --pool=POOL
     The parent CA Pool of the CERTIFICATE_AUTHORITY.

     To set the pool attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ignore-active-certificates` |  |  | If this flag is set, the Certificate Authority will be deleted even if the Certificate Authority has un-revoked or un-expired certificates after the grace period. |
| `--ignore-dependent-resources` |  |  | This field skips the integrity check that would normally prevent breaking a CA Pool if it is used by another cloud resource and allows the CA Pool to be in a state where it is not able to issue certificates. Doing so may result in unintended and unrecoverable effects on any dependent resource(s) since the CA Pool would not be able to issue certificates. |
| `--skip-grace-period` |  |  | If this flag is set, the Certificate Authority will be deleted as soon as possible without a 30-day grace period where undeletion would have been allowed. If you proceed, there will be no way to recover this CA. |


**Examples:**
```bash
To delete a subordinate CA:

    $ gcloud privateca subordinates delete server-tls-1 --pool=my-pool \
        --location=us-west1

To delete a CA while skipping the confirmation input:

    $ gcloud privateca subordinates delete server-tls-1s \
        --pool=my-pool --location=us-west1 --quiet

To undo the deletion for a subordinate CA:

    $ gcloud privateca subordinates undelete server-tls-1 \
        --pool=my-pool --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/subordinates/delete)

---
### `gcloud privateca subordinates describe`

Get metadata for a subordinate certificate authority

Returns metadata for the given certificate authority.

**Synopsis:**
```
gcloud privateca subordinates describe
    (CERTIFICATE_AUTHORITY : --location=LOCATION --pool=POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE AUTHORITY resource - The certificate authority for which to
obtain metadata. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument certificate_authority on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_AUTHORITY
     ID of the CERTIFICATE_AUTHORITY or fully qualified identifier for the
     CERTIFICATE_AUTHORITY.

     To set the certificate_authority attribute:
     + provide the argument certificate_authority on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CERTIFICATE_AUTHORITY.

     To set the location attribute:
     + provide the argument certificate_authority on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.

  --pool=POOL
     The ID of the CA Pool.

     To set the pool attribute:
     + provide the argument certificate_authority on the command line
       with a fully specified name;
     + provide the argument --pool on the command line.
```

**Examples:**
```bash
To get metadata for the subordinate CA 'server-tls-1' in CA Pool 'my-pool'
and location 'us-west1':

    $ gcloud privateca subordinates describe server-tls-1 \
        --location=us-west1 --pool=my-pool

To download the PEM-encoded CA certificate chain for the 'server-tls-1' CA
in location 'us-west1' to a file called 'server-tls-1.crt':

    $ gcloud privateca subordinates describe server-tls-1 \
        --location=us-west1 --pool=my-pool \
        --format="value(pemCaCertificates)" > ./server-tls-1.crt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/subordinates/describe)

---
### `gcloud privateca subordinates disable`

Disable a subordinate certificate authority

Disables a subordinate certificate authority. The subordinate certificate
authority will not be allowed to issue certificates once disabled. It may
still revoke certificates and/or generate CRLs.

**Synopsis:**
```
gcloud privateca subordinates disable
    (CERTIFICATE_AUTHORITY : --location=LOCATION --pool=POOL)
    [--ignore-dependent-resources] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE AUTHORITY resource - The certificate authority to disable. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument CERTIFICATE_AUTHORITY on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_AUTHORITY
     ID of the CERTIFICATE_AUTHORITY or fully qualified identifier for the
     CERTIFICATE_AUTHORITY.

     To set the certificate_authority attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CERTIFICATE_AUTHORITY.

     To set the location attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.

  --pool=POOL
     The parent CA Pool of the CERTIFICATE_AUTHORITY.

     To set the pool attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ignore-dependent-resources` |  |  | This field skips the integrity check that would normally prevent breaking a CA Pool if it is used by another cloud resource and allows the CA Pool to be in a state where it is not able to issue certificates. Doing so may result in unintended and unrecoverable effects on any dependent resource(s) since the CA Pool would not be able to issue certificates. |


**Examples:**
```bash
To disable a subordinate CA:

    $ gcloud privateca subordinates disable server-tls1 \
      --location=us-west1 --pool=my-pool
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/subordinates/disable)

---
### `gcloud privateca subordinates enable`

Enable a subordinate certificate authority

Enables a subordinate certificate authority. The subordinate certificate
authority will be allowed to issue certificates once enabled.

**Synopsis:**
```
gcloud privateca subordinates enable
    (CERTIFICATE_AUTHORITY : --location=LOCATION --pool=POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE AUTHORITY resource - The certificate authority to enable. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument CERTIFICATE_AUTHORITY on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_AUTHORITY
     ID of the CERTIFICATE_AUTHORITY or fully qualified identifier for the
     CERTIFICATE_AUTHORITY.

     To set the certificate_authority attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CERTIFICATE_AUTHORITY.

     To set the location attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.

  --pool=POOL
     The parent CA Pool of the CERTIFICATE_AUTHORITY.

     To set the pool attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --pool on the command line.
```

**Examples:**
```bash
To enable a subordinate CA:

    $ gcloud privateca subordinates enable server-tls1 --pool=my-pool \
      --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/subordinates/enable)

---
### `gcloud privateca subordinates get-csr`

Get the CSR for a subordinate certificate authority that has not yet been activated

Gets the PEM-encoded CSR for a subordinate certificate authority that is
awaiting user activation. The CSR should be signed by the issuing
Certificate Authority and uploaded back using the subordinates activate
command.

**Synopsis:**
```
gcloud privateca subordinates get-csr
    (CERTIFICATE_AUTHORITY : --location=LOCATION --pool=POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE AUTHORITY resource - The certificate authority for which to
get the CSR. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument CERTIFICATE_AUTHORITY on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_AUTHORITY
     ID of the CERTIFICATE_AUTHORITY or fully qualified identifier for the
     CERTIFICATE_AUTHORITY.

     To set the certificate_authority attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CERTIFICATE_AUTHORITY.

     To set the location attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.

  --pool=POOL
     The parent CA Pool of the CERTIFICATE_AUTHORITY.

     To set the pool attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --pool on the command line.
```

**Examples:**
```bash
To download the CSR for the 'server-tls-1' CA into a file called
'server-tls-1.csr':

    $ gcloud privateca subordinates get-csr server-tls-1 \
        --location=us-west1 --pool=my-pool > server-tls-1.csr
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/subordinates/get-csr)

---
### `gcloud privateca subordinates list`

List subordinate certificate authorities

List the subordinate certificate authorities within a project.

**Synopsis:**
```
gcloud privateca subordinates list [--location=LOCATION] [--pool=POOL]
    [--limit=LIMIT] [--page-size=PAGE_SIZE; default=100]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the certificate authorities. If omitted, subordinate CAs across all regions will be listed. Note that, if it is populated, the privateca/location property will be used if this flag is not specified. To ignore this property, specify "-" as the location. |
| `--pool` | POOL |  | ID of the CA Pool where the certificate authorities reside. If omitted, subordinate CAs across all CA pools will be listed. |


**Examples:**
```bash
To list all subordinate certificate authorities in a project:

    $ gcloud privateca subordinates list

To list all subordinate certificate authorities within a project and
location 'us-central1':

    $ gcloud privateca subordinates list --location=us-central1

To list all subordinate certificate authorities within a CA Pool in
location 'us-central1':

    $ gcloud privateca subordinates list --pool=my-pool \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/subordinates/list)

---
### `gcloud privateca subordinates undelete`

Undelete a subordinate certificate authority

Restores a subordinate Certificate Authority that has been deleted. A
Certificate Authority can be undeleted within 30 days of being deleted. Use
this command to halt the deletion process. An undeleted CA will move to
DISABLED state.

**Synopsis:**
```
gcloud privateca subordinates undelete
    (CERTIFICATE_AUTHORITY : --location=LOCATION --pool=POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE AUTHORITY resource - The certificate authority to undelete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument CERTIFICATE_AUTHORITY on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_AUTHORITY
     ID of the CERTIFICATE_AUTHORITY or fully qualified identifier for the
     CERTIFICATE_AUTHORITY.

     To set the certificate_authority attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CERTIFICATE_AUTHORITY.

     To set the location attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.

  --pool=POOL
     The parent CA Pool of the CERTIFICATE_AUTHORITY.

     To set the pool attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --pool on the command line.
```

**Examples:**
```bash
To undelete a subordinate CA:

    $ gcloud privateca subordinates undelete server-tls-1 \
      --location=us-west1 --pool=my-pool
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/subordinates/undelete)

---
### `gcloud privateca subordinates update`

Update an existing subordinate certificate authority

**Synopsis:**
```
gcloud privateca subordinates update
    (CERTIFICATE_AUTHORITY : --location=LOCATION --pool=POOL)
    [--pem-chain=PEM_CHAIN] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE AUTHORITY resource - The certificate authority to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument CERTIFICATE_AUTHORITY on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_AUTHORITY
     ID of the CERTIFICATE_AUTHORITY or fully qualified identifier for the
     CERTIFICATE_AUTHORITY.

     To set the certificate_authority attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CERTIFICATE_AUTHORITY.

     To set the location attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.

  --pool=POOL
     The parent CA Pool of the CERTIFICATE_AUTHORITY.

     To set the pool attribute:
     + provide the argument CERTIFICATE_AUTHORITY on the command line
       with a fully specified name;
     + provide the argument --pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--pem-chain` | PEM_CHAIN |  | A file containing a list of PEM-encoded certificates that represent the issuing chain of this CA. Please note that the certificate corresponding to this specific CA should be excluded. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels on a subordinate CA:

    $ gcloud privateca subordinates update server-tls-1 --pool=my-pool \
        --location=us-west1 --update-labels=foo=bar

To update the CA certificate chain for a subordinate CA:

    $ gcloud privateca subordinates update server-tls-1 --pool=my-pool \
        --location=us-west1 --pem-chain=pem_chain.txt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/subordinates/update)

---