# gcloud privateca certificates

manage certificates

### `gcloud privateca certificates create`

Create a new certificate

**Synopsis:**
```
gcloud privateca certificates create
    [[CERTIFICATE]
      --issuer-location=ISSUER_LOCATION --issuer-pool=ISSUER_POOL]
    (--cert-output-file=CERT_OUTPUT_FILE | --validate-only)
    (--csr=CSR | [(--dns-san=[DNS_SAN,...] --email-san=[EMAIL_SAN,...]
      --ip-san=[IP_SAN,...] --subject=[SUBJECT,...]
      --uri-san=[URI_SAN,...])
      (--generate-key --key-output-file=KEY_OUTPUT_FILE
      | [--kms-key-version=KMS_KEY_VERSION : --kms-key=KMS_KEY
      --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT])
      : --use-preset-profile=USE_PRESET_PROFILE
      | --extended-key-usages=[EXTENDED_KEY_USAGES,...] --is-ca-cert
      --key-usages=[KEY_USAGES,...] --max-chain-length=MAX_CHAIN_LENGTH
      | --unconstrained-chain-length --no-name-constraints-critical
      --name-excluded-dns=[NAME_EXCLUDED_DNS,...]
      --name-excluded-email=[NAME_EXCLUDED_EMAIL,...]
      --name-excluded-ip=[NAME_EXCLUDED_IP,...]
      --name-excluded-uri=[NAME_EXCLUDED_URI,...]
      --name-permitted-dns=[NAME_PERMITTED_DNS,...]
      --name-permitted-email=[NAME_PERMITTED_EMAIL,...]
      --name-permitted-ip=[NAME_PERMITTED_IP,...]
      --name-permitted-uri=[NAME_PERMITTED_URI,...]]) [--ca=CA]
    [--labels=[KEY=VALUE,...]] [--subject-key-id=SUBJECT_KEY_ID]
    [--validity=VALIDITY; default="P30D"]
    [--template=TEMPLATE : --template-location=TEMPLATE_LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE resource - The name of the certificate to issue. If the
certificate ID is omitted, a random identifier will be generated according
to the following format: {YYYYMMDD}-{3 random alphanumeric characters}-{3
random alphanumeric characters}. The certificate ID is not required when
the issuing CA pool is in the DevOps tier. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument CERTIFICATE on the command line with a fully
   specified name;
 * certificate id will default to an automatically generated id with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [CERTIFICATE]
     ID of the CERTIFICATE or fully qualified identifier for the
     CERTIFICATE.

     To set the certificate attribute:
     + provide the argument CERTIFICATE on the command line;
     + certificate id will default to an automatically generated id.

  --issuer-location=ISSUER_LOCATION
     The location of the CERTIFICATE.

     To set the issuer-location attribute:
     + provide the argument CERTIFICATE on the command line with a fully
       specified name;
     + certificate id will default to an automatically generated id with
       a fully specified name;
     + provide the argument --issuer-location on the command line;
     + set the property privateca/location.

  --issuer-pool=ISSUER_POOL
     The parent CA Pool of the CERTIFICATE.

     To set the issuer-pool attribute:
     + provide the argument CERTIFICATE on the command line with a fully
       specified name;
     + certificate id will default to an automatically generated id with
       a fully specified name;
     + provide the argument --issuer-pool on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cert-output-file` | CERT_OUTPUT_FILE |  | _[Exactly one of these must be specified:]_ The path where the resulting PEM-encoded certificate chain file should be written (ordered from leaf to root). |
| `--validate-only` |  |  | _[Exactly one of these must be specified:]_ If this flag is set, the certificate resource will not be persisted and the returned certificate will not contain the pem_certificate field. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ca` | CA |  | The name of an existing certificate authority to use for issuing the certificate. If omitted, a certificate authority will be will be chosen from the CA pool by the service on your behalf. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--subject-key-id` | SUBJECT_KEY_ID |  | Optional field to specify subject key ID for certificate. DO NOT USE except to maintain a previously established identifier for a public key, whose SKI was not generated using method (1) described in RFC 5280 section 4.2.1.2. |
| `--validity` | VALIDITY | P30D | The validity of this certificate, as an ISO8601 duration. Defaults to 30 days. |


**Examples:**
```bash
To create a certificate using a CSR:

    $ gcloud privateca certificates create frontend-server-tls \
      --issuer-pool=my-pool --issuer-location=us-west1 \
      --csr=./csr.pem --cert-output-file=./cert.pem --validity=P30D

To create a certificate using a client-generated key:

    $ gcloud privateca certificates create frontend-server-tls \
      --issuer-pool=my-pool --issuer-location=us-west1 \
      --generate-key --key-output-file=./key \
      --cert-output-file=./cert.pem --dns-san=www.example.com \
      --use-preset-profile=leaf_server_tls
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/certificates/create)

---
### `gcloud privateca certificates describe`

Get metadata for a certificate

Returns metadata for the given certificate.

**Synopsis:**
```
gcloud privateca certificates describe
    (CERTIFICATE
      : --issuer-location=ISSUER_LOCATION --issuer-pool=ISSUER_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE resource - The certificate for which to obtain metadata. The
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
     ID of the CERTIFICATE or fully qualified identifier for the
     CERTIFICATE.

     To set the certificate attribute:
     + provide the argument certificate on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --issuer-location=ISSUER_LOCATION
     The location of the CERTIFICATE.

     To set the issuer-location attribute:
     + provide the argument certificate on the command line with a fully
       specified name;
     + provide the argument --issuer-location on the command line;
     + set the property privateca/location.

  --issuer-pool=ISSUER_POOL
     The ID of the issuing CA Pool.

     To set the issuer-pool attribute:
     + provide the argument certificate on the command line with a fully
       specified name;
     + provide the argument --issuer-pool on the command line.
```

**Examples:**
```bash
To get metadata for the 'frontend-server-tls' certificate:

    $ gcloud privateca certificates describe frontend-server-tls \
        --issuer-pool=my-pool --issuer-location=us-west1

To download the PEM-encoded certificate for the 'frontend-server-tls'
certificate to a file called 'frontend-server-tls.crt':

    $ gcloud privateca certificates describe frontend-server-tls \
        --issuer-pool=my-pool --issuer-location=us-west1 \
        --format="value(pemCertificate)" > ./frontend-server-tls.crt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/certificates/describe)

---
### `gcloud privateca certificates export`

Export a pem-encoded certificate to a file

**Synopsis:**
```
gcloud privateca certificates export
    (CERTIFICATE
      : --issuer-location=ISSUER_LOCATION --issuer-pool=ISSUER_POOL)
    --output-file=OUTPUT_FILE [--include-chain] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE resource - The certificate to export. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument CERTIFICATE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE
     ID of the CERTIFICATE or fully qualified identifier for the
     CERTIFICATE.

     To set the certificate attribute:
     + provide the argument CERTIFICATE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --issuer-location=ISSUER_LOCATION
     The location of the CERTIFICATE.

     To set the issuer-location attribute:
     + provide the argument CERTIFICATE on the command line with a fully
       specified name;
     + provide the argument --issuer-location on the command line;
     + set the property privateca/location.

  --issuer-pool=ISSUER_POOL
     The parent CA Pool of the CERTIFICATE.

     To set the issuer-pool attribute:
     + provide the argument CERTIFICATE on the command line with a fully
       specified name;
     + provide the argument --issuer-pool on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--output-file` | OUTPUT_FILE |  | The path where the resulting PEM-encoded certificate will be written. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--include-chain` |  |  | Whether to include the certificate's issuer chain in the exported file. If this is set, the resulting file will contain the pem-encoded certificate and its issuing chain, ordered from leaf to root. |


**Examples:**
```bash
    To export a single pem-encoded certificate to a file, run the following:

        $ gcloud privateca certificates export my-cert \
            --issuer-pool=my-pool --issuer-location=us-west1 \
            --output-file=cert.pem

    To export a pem-encoded certificate along with its issuing chain in the
    same file, run the following:

        $ gcloud privateca certificates export my-cert \
            --issuer-pool=my-pool --issuer-location=us-west1 \
            --include-chain --output-file=chain.pem

    You can omit the --issuer-location flag in both of the above examples if
    you've already set the privateca/location property. For example:

    $ gcloud config set privateca/location us-west1

The following is equivalent to the first example above.

        $ gcloud privateca certificates export my-cert \
            --issuer-pool=my-pool --output-file=cert.pem

The following is equivalent to the second example above.

        $ gcloud privateca certificates export my-cert \
            --issuer-pool=my-pool --include-chain --output-file=chain.pem
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/certificates/export)

---
### `gcloud privateca certificates list`

List certificates within a project

List certificates within a project. Note that listing certificates accross
locations is not supported.

**Synopsis:**
```
gcloud privateca certificates list
    [--issuer-pool=ISSUER_POOL --location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE; default=100]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--issuer-pool` | ISSUER_POOL |  | _[* set the property core/project.]_ ID of the CA_POOL or fully qualified identifier for the CA_POOL. To set the pool attribute: + provide the argument --issuer-pool on the command line; + defaults to all CA pools in the given location. |
| `--location` | LOCATION |  | _[* set the property core/project.]_ The location of the CA_POOL. To set the location attribute: + provide the argument --issuer-pool on the command line with a fully specified name; + defaults to all CA pools in the given location with a fully specified name; + provide the argument --location on the command line; + set the property privateca/location. |


**Examples:**
```bash
To list all Certificates issued by a given CA pool, run:

    $ gcloud privateca certificates list --issuer-pool=my-pool \
        --location=us-west1

To list all Certificates issued by all CA pools in a location, run:

    $ gcloud privateca certificates list --location=us-west1

To list all Certificates issued directly under a CA, run:

    $ gcloud privateca certificates list --issuer-pool=my-pool \
        --location=us-west1 \
        --filter="issuer_certificate_authority='projects/1234567890/loca\
    tions/us-west1/caPools/my-pool/certificateAuthorities/my-ca'"

You can omit the --location flag in both of the above examples if you've
already set the privateca/location property. For example:

    $ gcloud config set privateca/location us-west1

    # The following is equivalent to the first example above.
    $ gcloud privateca certificates list --issuer-pool=my-pool

    # The following is equivalent to the second example above.
    $ gcloud privateca certificates list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/certificates/list)

---
### `gcloud privateca certificates revoke`

Revoke a certificate

Revokes the given certificate for the given reason.

**Synopsis:**
```
gcloud privateca certificates revoke
    (--certificate=CERTIFICATE | --serial-number=SERIAL_NUMBER)
    [--reason=REASON; default="unspecified"]
    [--issuer-pool=ISSUER_POOL : --issuer-location=ISSUER_LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--certificate` | CERTIFICATE |  | _[specified name.]_ ID of the certificate or fully qualified identifier for the certificate. To set the certificate attribute: - provide the argument --certificate on the command line. |
| `--serial-number` | SERIAL_NUMBER |  | _[specified name.]_ The serial number of the certificate. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--reason` | one of: affiliation-changed, attribute-authority-compromise, certificate-authority-compromise, certificate-hold, cessation-of-operation, key-compromise, privilege-withdrawn, unspecified, superseded | unspecified | Revocation reason to include in the CRL. REASON must be one of: affiliation-changed, attribute-authority-compromise, certificate-authority-compromise, certificate-hold, cessation-of-operation, key-compromise, privilege-withdrawn, unspecified, superseded. |


**Examples:**
```bash
To revoke the 'frontend-server-tls' certificate due to key compromise:

    $ gcloud privateca certificates revoke \
        --certificate=frontend-server-tls --issuer-pool=my-pool \
        --issuer-location=us-west1 --reason=key_compromise

To revoke the a certificate with the serial number
'7dc1d9186372de2e1f4824abb1c4c9e5e43cbb40' due to a newer one being issued:

    $ gcloud privateca certificates revoke \
        --serial-number=7dc1d9186372de2e1f4824abb1c4c9e5e43cbb40 \
        --issuer-pool=my-pool --issuer-location=us-west1 \
        --reason=superseded
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/certificates/revoke)

---
### `gcloud privateca certificates update`

Update an existing certificate

**Synopsis:**
```
gcloud privateca certificates update
    (CERTIFICATE
      : --issuer-location=ISSUER_LOCATION --issuer-pool=ISSUER_POOL)
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE resource - The certificate to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument CERTIFICATE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE
     ID of the CERTIFICATE or fully qualified identifier for the
     CERTIFICATE.

     To set the certificate attribute:
     + provide the argument CERTIFICATE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --issuer-location=ISSUER_LOCATION
     The location of the CERTIFICATE.

     To set the issuer-location attribute:
     + provide the argument CERTIFICATE on the command line with a fully
       specified name;
     + provide the argument --issuer-location on the command line;
     + set the property privateca/location.

  --issuer-pool=ISSUER_POOL
     The parent CA Pool of the CERTIFICATE.

     To set the issuer-pool attribute:
     + provide the argument CERTIFICATE on the command line with a fully
       specified name;
     + provide the argument --issuer-pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels on a certificate:

    $ gcloud privateca certificates update frontend-server-tls \
       --issuer-pool=my-pool --issuer-location=us-west1 \
       --update-labels=in_use=true
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/certificates/update)

---