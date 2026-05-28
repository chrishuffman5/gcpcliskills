# gcloud auth enterprise-certificate-config

manage enterprise certificate configurations


## `gcloud auth enterprise-certificate-config create` — create enterprise certificate configurations
### `gcloud auth enterprise-certificate-config create linux`

Create an enterprise-certificate configuration file for Linux

This command creates a configuration file used by gcloud to use the
enterprise-certificate-proxy component for mTLS.

**Synopsis:**
```
gcloud auth enterprise-certificate-config create linux --label=LABEL
    --module=MODULE --slot=SLOT [--ecp=ECP] [--ecp-client=ECP_CLIENT]
    [--output-file=OUTPUT_FILE] [--tls-offload=TLS_OFFLOAD]
    [--user-pin=USER_PIN] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--label` | LABEL |  | The PKCS #11 label for the target credentials. The certificate, public key, and private key MUST have the same label. enterprise-certificate-proxy will use all three objects. |
| `--module` | MODULE |  | The full file path to the PKCS #11 module. |
| `--slot` | SLOT |  | The PKCS #11 slot containing the target credentials. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ecp` | ECP |  | Provide a custom path to the enterprise-certificate-proxy binary. This flag must be the full path to the binary. |
| `--ecp-client` | ECP_CLIENT |  | Provide a custom path to the enterprise-certificate-proxy shared client library. This flag must be the full path to the shared library. |
| `--output-file` | OUTPUT_FILE |  | Override the file path that the enterprise-certificate-proxy configuration is written to. |
| `--tls-offload` | TLS_OFFLOAD |  | Provide a custom path to the enterprise-certificate-proxy shared tls offload library. This flag must be the full path to the shared library. |
| `--user-pin` | USER_PIN |  | The user pin used to login to the PKCS #11 module. If there is no user pin leave this field empty. |


**Examples:**
```bash
To create a credential configuration run:

    $ gcloud auth enterprise-certificate-config create linux \
        --module=$PATH_TO_PKCS11_MODULE --slot=$PKCS11_SLOT_ID \
        --label=$PKCS11_OBJECT_LABEL --user-pin=$PKCS11_USER_PIN
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/auth/enterprise-certificate-config/create/linux)

---
### `gcloud auth enterprise-certificate-config create macos`

Create an enterprise-certificate configuration file for MacOS

This command creates a configuration file used by gcloud to use the
enterprise-certificate-proxy component for mTLS.

**Synopsis:**
```
gcloud auth enterprise-certificate-config create macos --issuer=ISSUER
    [--ecp=ECP] [--ecp-client=ECP_CLIENT]
    [--keychain-type=KEYCHAIN_TYPE; default="all"]
    [--output-file=OUTPUT_FILE] [--tls-offload=TLS_OFFLOAD]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--issuer` | ISSUER |  | The certificate issuer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ecp` | ECP |  | Provide a custom path to the enterprise-certificate-proxy binary. This flag must be the full path to the binary. |
| `--ecp-client` | ECP_CLIENT |  | Provide a custom path to the enterprise-certificate-proxy shared client library. This flag must be the full path to the shared library. |
| `--keychain-type` | KEYCHAIN_TYPE | all | Specify the target keychain(s) for certificate lookup.Accepted values are "login", "system", or "all". If omitted,defaults to "all". Use "all" to include custom keychains. |
| `--output-file` | OUTPUT_FILE |  | Override the file path that the enterprise-certificate-proxy configuration is written to. |
| `--tls-offload` | TLS_OFFLOAD |  | Provide a custom path to the enterprise-certificate-proxy shared tls offload library. This flag must be the full path to the shared library. |


**Examples:**
```bash
To create a credential configuration run:

    $ gcloud auth enterprise-certificate-config create macos \
        --issuer=$CERT_ISSUER
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/auth/enterprise-certificate-config/create/macos)

---
### `gcloud auth enterprise-certificate-config create windows`

Create an enterprise-certificate configuration file for Windows

This command creates a configuration file used by gcloud to use the
enterprise-certificate-proxy component for mTLS.

**Synopsis:**
```
gcloud auth enterprise-certificate-config create windows --issuer=ISSUER
    --provider=PROVIDER --store=STORE [--ecp=ECP] [--ecp-client=ECP_CLIENT]
    [--output-file=OUTPUT_FILE] [--tls-offload=TLS_OFFLOAD]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--issuer` | ISSUER |  | The certificate issuer. |
| `--provider` | PROVIDER |  | The Windows secure store provider. |
| `--store` | STORE |  | The Windows secure store. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ecp` | ECP |  | Provide a custom path to the enterprise-certificate-proxy binary. This flag must be the full path to the binary. |
| `--ecp-client` | ECP_CLIENT |  | Provide a custom path to the enterprise-certificate-proxy shared client library. This flag must be the full path to the shared library. |
| `--output-file` | OUTPUT_FILE |  | Override the file path that the enterprise-certificate-proxy configuration is written to. |
| `--tls-offload` | TLS_OFFLOAD |  | Provide a custom path to the enterprise-certificate-proxy shared tls offload library. This flag must be the full path to the shared library. |


**Examples:**
```bash
To create a credential configuration run:

    $ gcloud auth enterprise-certificate-config create windows \
        --issuer=$CERT_ISSUER --store=$STORE --provider=$PROVIDER
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/auth/enterprise-certificate-config/create/windows)

---