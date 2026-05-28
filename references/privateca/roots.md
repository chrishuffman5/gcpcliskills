# gcloud privateca roots

manage root certificate authorities

### `gcloud privateca roots create`

Create a new root certificate authority

TIP: Consider setting a project lien
(https://cloud.google.com/resource-manager/docs/project-liens) on the
project to prevent it from accidental deletion.

**Synopsis:**
```
gcloud privateca roots create
    (CERTIFICATE_AUTHORITY : --location=LOCATION --pool=POOL)
    [--auto-enable] [--bucket=BUCKET]
    [--custom-aia-urls=[CUSTOM_AIA_URLS,...]]
    [--custom-cdp-urls=[CUSTOM_CDP_URLS,...]] [--dns-san=[DNS_SAN,...]]
    [--email-san=[EMAIL_SAN,...]] [--from-ca=FROM_CA]
    [--ip-san=[IP_SAN,...]] [--labels=[KEY=VALUE,...]]
    [--subject=[SUBJECT,...]] [--subject-key-id=SUBJECT_KEY_ID]
    [--uri-san=[URI_SAN,...]] [--validity=VALIDITY; default="P10Y"]
    [--key-algorithm=KEY_ALGORITHM; default="rsa-pkcs1-4096-sha256"
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
Certificate Authority resource - The name of the root CA to create. The
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
| `--labels` | [KEY=VALUE,...] |  | _[+ provide the argument --from-ca on the command line.]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--subject` | [SUBJECT,...] |  | _[+ provide the argument --from-ca on the command line.]_ X.501 name of the certificate subject. Example: --subject "C=US,ST=California,L=Mountain View,O=Google LLC,CN=google.com" |
| `--subject-key-id` | SUBJECT_KEY_ID |  | _[+ provide the argument --from-ca on the command line.]_ Optional field to specify subject key ID for certificate. DO NOT USE except to maintain a previously established identifier for a public key, whose SKI was not generated using method (1) described in RFC 5280 section 4.2.1.2. |
| `--uri-san` | [URI_SAN,...] |  | _[+ provide the argument --from-ca on the command line.]_ One or more comma-separated URI Subject Alternative Names. |
| `--validity` | VALIDITY | P10Y | _[+ provide the argument --from-ca on the command line.]_ The validity of this CA, as an ISO8601 duration. Defaults to 10 years. |


**Examples:**
```bash
To create a root CA that supports one layer of subordinates:

    $ gcloud privateca roots create prod-root --location=us-west1 \
      --pool=my-pool \
      --kms-key-version="projects/my-project-pki/locations/us-west1/ke\
    yRings/kr1/cryptoKeys/k1/cryptoKeyVersions/1" \
        --subject="CN=Example Production Root CA, O=Google" \
        --max-chain-length=1

To create a root CA that is based on an existing CA:

    $ gcloud privateca roots create prod-root --location=us-west1 \
      --pool=my-pool \
      --kms-key-version="projects/my-project-pki/locations/us-west1/ke\
    yRings/kr1/cryptoKeys/k1/cryptoKeyVersions/1" --from-ca=source-root
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/roots/create)

---
### `gcloud privateca roots delete`

Delete a Root Certificate Authority

Delete a Root Certificate Authority. Deleted Root Certificate Authorities
may be recovered with the gcloud privateca roots undelete command within a
grace period of 30 days.

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
gcloud privateca roots delete
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
To delete a root CA:

    $ gcloud privateca roots delete prod-root --pool=my-pool \
        --location=us-west1

To delete a CA while skipping the confirmation input:

    $ gcloud privateca roots delete prod-root --pool=my-pool \
        --location=us-west1 --quiet

To undo the deletion for a root CA:

    $ gcloud privateca roots undelete prod-root --pool=my-pool \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/roots/delete)

---
### `gcloud privateca roots describe`

Get metadata for a root Certificate Authority

Returns metadata for the given Certificate Authority.

**Synopsis:**
```
gcloud privateca roots describe
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
To get metadata for the root CA 'prod-root' in location 'us-west1' and CA
Pool 'my-pool':

    $ gcloud privateca roots describe server-tls-1 --location=us-west1 \
        --pool=my-pool

To download the PEM-encoded CA certificate chain for the 'prod-root' CA in
location 'us-west1' and CA Pool 'my-pool' to a file called 'prod-root.crt':

    $ gcloud privateca roots describe prod-root --location=us-west1 \
        --pool=my-pool --format="value(pemCaCertificates)" > \
        ./prod-root.crt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/roots/describe)

---
### `gcloud privateca roots disable`

Disable a root certificate authority

Disables a root certificate authority. The root certificate authority will
not be allowed to issue certificates once disabled. It may still revoke
certificates and/or generate CRLs. The CA certfificate will still be
included in the FetchCaCertificates response for the parent CA Pool.

**Synopsis:**
```
gcloud privateca roots disable
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
To disable a root CA:

    $ gcloud privateca roots disable prod-root --pool=prod-root-pool \
      --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/roots/disable)

---
### `gcloud privateca roots enable`

Enable a root certificate authority

Enables a root certificate authority. The root certificate authority will
be allowed to issue certificates once enabled.

**Synopsis:**
```
gcloud privateca roots enable
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
To enable a root CA:

    $ gcloud privateca roots enable prod-root --location=us-west1 \
      --pool=my-pool
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/roots/enable)

---
### `gcloud privateca roots list`

List root certificate authorities

List the root certificate authorities within a project.

**Synopsis:**
```
gcloud privateca roots list [--location=LOCATION] [--pool=POOL]
    [--limit=LIMIT] [--page-size=PAGE_SIZE; default=100]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the certificate authorities. If ommitted, root CAs across all regions will be listed. |
| `--pool` | POOL |  | ID of the CA Pool where the certificate authorities reside. If ommitted, root CAs across all CA pools will be listed. |


**Examples:**
```bash
To list all root certificate authorities in a projects:

    $ gcloud privateca roots list

To list all root certificate authorities within a project and location
'us-central1':

    $ gcloud privateca roots list --location=us-central1

To list all root certificate authorities within a CA Pool in location
'us-central1':

    $ gcloud privateca roots list --pool=my-pool --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/roots/list)

---
### `gcloud privateca roots undelete`

Undelete a root Certificate Authority

Restores a root Certificate Authority that has been deleted. A Certificate
Authority can be undeleted within 30 days of being deleted. Use this
command to halt the deletion process. An undeleted CA will move to DISABLED
state.

**Synopsis:**
```
gcloud privateca roots undelete
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
To undelete a root CA:

    $ gcloud privateca roots undelete prod-root --location=us-west1 \
      --pool=my-pool
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/roots/undelete)

---
### `gcloud privateca roots update`

Update an existing root certificate authority

**Synopsis:**
```
gcloud privateca roots update
    (CERTIFICATE_AUTHORITY : --location=LOCATION --pool=POOL)
    [--update-labels=[KEY=VALUE,...]]
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
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels on a root CA:

    $ gcloud privateca roots update prod-root --location=us-west1 \
        --pool=my-pool --update-labels=foo=bar
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/roots/update)

---