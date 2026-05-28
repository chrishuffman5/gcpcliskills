# gcloud kms (top-level commands)

### `gcloud kms asymmetric-decrypt`

Decrypt an input file using an asymmetric-encryption key version

Decrypts the given ciphertext file using the provided asymmetric-encryption
key version and saves the decrypted data to the plaintext file.

By default, the command performs integrity verification on data sent to and
received from Cloud KMS. Use --skip-integrity-verification to disable
integrity verification.

**Synopsis:**
```
gcloud kms asymmetric-decrypt --ciphertext-file=CIPHERTEXT_FILE
    --plaintext-file=PLAINTEXT_FILE [--key=KEY] [--keyring=KEYRING]
    [--location=LOCATION] [--skip-integrity-verification]
    [--version=VERSION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ciphertext-file` | CIPHERTEXT_FILE |  | File path of the ciphertext file to decrypt. |
| `--plaintext-file` | PLAINTEXT_FILE |  | File path of the plaintext file to output. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | to use for asymmetric-decryption. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--skip-integrity-verification` |  |  | Skip integrity verification on request and response API fields. |
| `--version` | VERSION |  | Version to use for asymmetric-decryption. |


**Examples:**
```bash
The following command will read the file '/tmp/my/secret.file.enc', decrypt
it using the asymmetric CryptoKey dont-panic Version 3 and write the
plaintext to '/tmp/my/secret.file.dec'.

    $ gcloud kms asymmetric-decrypt --location=us-central1 \
        --keyring=hitchhiker --key=dont-panic --version=3 \
        --ciphertext-file=/tmp/my/secret.file.enc \
        --plaintext-file=/tmp/my/secret.file.dec
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/asymmetric-decrypt)

---
### `gcloud kms asymmetric-sign`

Sign a user input file using an asymmetric-signing key version

Creates a digital signature of the input file using the provided
asymmetric-signing key version and saves the base64 encoded signature.

The required flag signature-file indicates the path to store signature.

By default, the command performs integrity verification on data sent to and
received from Cloud KMS. Use --skip-integrity-verification to disable
integrity verification.

**Synopsis:**
```
gcloud kms asymmetric-sign --input-file=INPUT_FILE
    --signature-file=SIGNATURE_FILE [--digest-algorithm=DIGEST_ALGORITHM]
    [--key=KEY] [--keyring=KEYRING] [--location=LOCATION]
    [--skip-integrity-verification] [--version=VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--input-file` | INPUT_FILE |  | Path to the input file to sign. |
| `--signature-file` | SIGNATURE_FILE |  | Path to the signature file to output. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--digest-algorithm` | one of: sha256, sha384, sha512 |  | The algorithm to digest the input. DIGEST_ALGORITHM must be one of: sha256, sha384, sha512. |
| `--key` | KEY |  | to use for signing. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--skip-integrity-verification` |  |  | Skip integrity verification on request and response API fields. |
| `--version` | VERSION |  | Version to use for signing. |


**Examples:**
```bash
The following command will read the file '/tmp/my/file.to.sign', digest it
with the digest algorithm 'sha256' and sign it using the asymmetric
CryptoKey dont-panic Version 3, and save the signature in base64 format to
'/tmp/my/signature'.

    $ gcloud kms asymmetric-sign --location=us-central1 \
        --keyring=hitchhiker --key=dont-panic --version=3 \
        --digest-algorithm=sha256 --input-file=/tmp/my/file.to.sign \
        --signature-file=/tmp/my/signature
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/asymmetric-sign)

---
### `gcloud kms decapsulate`

Decapsulate an input file using a key-encapsulation key version

Decapsulates the given ciphertext file using the provided key-encapsulation
key version and saves the decapsulated shared secret to the shared secret
file.

By default, the command performs integrity verification on data sent to and
received from Cloud KMS. Use --skip-integrity-verification to disable
integrity verification.

**Synopsis:**
```
gcloud kms decapsulate --ciphertext-file=CIPHERTEXT_FILE
    --shared-secret-file=SHARED_SECRET_FILE [--key=KEY] [--keyring=KEYRING]
    [--location=LOCATION] [--skip-integrity-verification]
    [--version=VERSION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ciphertext-file` | CIPHERTEXT_FILE |  | File path of the ciphertext file to decapsulate. |
| `--shared-secret-file` | SHARED_SECRET_FILE |  | File path of the shared secret file to output. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | to use for decapsulation. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--skip-integrity-verification` |  |  | Skip integrity verification on request and response API fields. |
| `--version` | VERSION |  | Version to use for decapsulation. |


**Examples:**
```bash
The following command will read the file '/tmp/my/secret.file.enc',
decapsulate it using the key encapsulation CryptoKey my-key Version 3 and
write the shared secret to '/tmp/my/secret.file.dec'.

    $ gcloud kms decapsulate --location=us-central1 \
        --keyring=my-keyring --key=my-key --version=3 \
        --ciphertext-file=/tmp/my/secret.file.enc \
        --shared-secret-file=/tmp/my/secret.file.dec
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/decapsulate)

---
### `gcloud kms decrypt`

Decrypt a ciphertext file using a Cloud KMS key

gcloud kms decrypt decrypts the given ciphertext file using the given Cloud
KMS key and writes the result to the named plaintext file. Note that to
permit users to decrypt using a key, they must be have at least one of the
following IAM roles for that key: roles/cloudkms.cryptoKeyDecrypter,
roles/cloudkms.cryptoKeyEncrypterDecrypter.

Additional authenticated data (AAD) is used as an additional check by Cloud
KMS to authenticate a decryption request. If an additional authenticated
data file is provided, its contents must match the additional authenticated
data provided during encryption and must not be larger than 64KiB. If you
don't provide a value for --additional-authenticated-data-file, an empty
string is used. For a thorough explanation of AAD, refer to this guide:
https://cloud.google.com/kms/docs/additional-authenticated-data

If --ciphertext-file or --additional-authenticated-data-file is set to '-',
that file is read from stdin. Note that both files cannot be read from
stdin. Similarly, if --plaintext-file is set to '-', the decrypted
plaintext is written to stdout.

By default, the command performs integrity verification on data sent to and
received from Cloud KMS. Use --skip-integrity-verification to disable
integrity verification.

**Synopsis:**
```
gcloud kms decrypt --ciphertext-file=CIPHERTEXT_FILE
    --plaintext-file=PLAINTEXT_FILE
    [--additional-authenticated-data-file=ADDITIONAL_AUTHENTICATED_DATA_FILE]
    [--key=KEY] [--keyring=KEYRING] [--location=LOCATION]
    [--skip-integrity-verification] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ciphertext-file` | CIPHERTEXT_FILE |  | File path of the ciphertext file to decrypt. This file should contain the result of encrypting a file with gcloud kms encrypt. |
| `--plaintext-file` | PLAINTEXT_FILE |  | File path of the plaintext file to output. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-authenticated-data-file` | ADDITIONAL_AUTHENTICATED_DATA_FILE |  | File path to the optional file containing the additional authenticated data. |
| `--key` | KEY |  | Cloud KMS key to use for decryption. * For symmetric keys, Cloud KMS detects the decryption key version from the ciphertext. If you specify a key version as part of a symmetric decryption request, an error is logged and decryption fails. * For asymmetric keys, the encryption key version can't be detected automatically. You must keep track of this information and provide the key version in the decryption request. The key version itself is not sensitive data and does not need to be encrypted. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--skip-integrity-verification` |  |  | Skip integrity verification on request and response API fields. |


**Examples:**
```bash
To decrypt the file 'path/to/ciphertext' using the key frodo with key ring
fellowship and location global and write the plaintext to
'path/to/plaintext.dec', run:

    $ gcloud kms decrypt --key=frodo --keyring=fellowship \
        --location=global --ciphertext-file=path/to/input/ciphertext \
        --plaintext-file=path/to/output/plaintext.dec

To decrypt the file 'path/to/ciphertext' using the key frodo and the
additional authenticated data that was used to encrypt the ciphertext, and
write the decrypted plaintext to stdout, run:

    $ gcloud kms decrypt --key=frodo --keyring=fellowship \
        --location=global \
        --additional-authenticated-data-file=path/to/aad \
        --ciphertext-file=path/to/input/ciphertext --plaintext-file='-'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/decrypt)

---
### `gcloud kms encrypt`

Encrypt a plaintext file using a key

Encrypts the given plaintext file using the given CryptoKey and writes the
result to the named ciphertext file. The plaintext file must not be larger
than 64KiB.

If an additional authenticated data file is provided, its contents must
also be provided during decryption. The file must not be larger than 64KiB.

The flag --version indicates the version of the key to use for encryption.
By default, the primary version is used.

If --plaintext-file or --additional-authenticated-data-file is set to '-',
that file is read from stdin. Similarly, if --ciphertext-file is set to
'-', the ciphertext is written to stdout.

By default, the command performs integrity verification on data sent to and
received from Cloud KMS. Use --skip-integrity-verification to disable
integrity verification.

**Synopsis:**
```
gcloud kms encrypt --ciphertext-file=CIPHERTEXT_FILE
    --plaintext-file=PLAINTEXT_FILE
    [--additional-authenticated-data-file=ADDITIONAL_AUTHENTICATED_DATA_FILE]
    [--key=KEY] [--keyring=KEYRING] [--location=LOCATION]
    [--skip-integrity-verification] [--version=VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ciphertext-file` | CIPHERTEXT_FILE |  | File path of the ciphertext file to output. |
| `--plaintext-file` | PLAINTEXT_FILE |  | File path of the plaintext file to encrypt. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-authenticated-data-file` | ADDITIONAL_AUTHENTICATED_DATA_FILE |  | File path to the optional file containing the additional authenticated data. |
| `--key` | KEY |  | The key to use for encryption. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--skip-integrity-verification` |  |  | Skip integrity verification on request and response API fields. |
| `--version` | VERSION |  | Version to use for encryption. |


**Examples:**
```bash
The following command will read the file 'path/to/plaintext', encrypt it
using the CryptoKey frodo with the KeyRing fellowship and Location global,
and write the ciphertext to 'path/to/ciphertext'.

    $ gcloud kms encrypt --key=frodo --keyring=fellowship \
        --location=global --plaintext-file=path/to/input/plaintext \
        --ciphertext-file=path/to/output/ciphertext
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/encrypt)

---
### `gcloud kms mac-sign`

Sign a user input file using a MAC key version

Creates a digital signature of the input file using the provided MAC
signing key version and saves the base64 encoded signature.

The required flag signature-file indicates the path to store signature.

By default, the command performs integrity verification on data sent to and
received from Cloud KMS. Use --skip-integrity-verification to disable
integrity verification.

**Synopsis:**
```
gcloud kms mac-sign --input-file=INPUT_FILE --signature-file=SIGNATURE_FILE
    [--key=KEY] [--keyring=KEYRING] [--location=LOCATION]
    [--skip-integrity-verification] [--version=VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--input-file` | INPUT_FILE |  | Path to the input file to sign. |
| `--signature-file` | SIGNATURE_FILE |  | Path to the signature file to output. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | to use for signing. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--skip-integrity-verification` |  |  | Skip integrity verification on request and response API fields. |
| `--version` | VERSION |  | Version to use for signing. |


**Examples:**
```bash
The following command will read the file '/tmp/my/file.to.sign', and sign
it using the symmetric MAC CryptoKey dont-panic Version 3, and save the
signature in base64 format to '/tmp/my/signature'.

    $ gcloud kms mac-sign --location=us-central1 --keyring=hitchhiker \
        --key=dont-panic --version=3 --input-file=/tmp/my/file.to.sign \
        --signature-file=/tmp/my/signature
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/mac-sign)

---
### `gcloud kms mac-verify`

Verify a user signature file using a MAC key version

Verifies a digital signature using the provided MAC signing key version.

By default, the command performs integrity verification on data sent to and
received from Cloud KMS. Use --skip-integrity-verification to disable
integrity verification.

**Synopsis:**
```
gcloud kms mac-verify --input-file=INPUT_FILE
    --signature-file=SIGNATURE_FILE [--key=KEY] [--keyring=KEYRING]
    [--location=LOCATION] [--skip-integrity-verification]
    [--version=VERSION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--input-file` | INPUT_FILE |  | Path to the input file to use for verification. |
| `--signature-file` | SIGNATURE_FILE |  | Path to the signature file to be verified. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | to use for signing. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--skip-integrity-verification` |  |  | Skip integrity verification on request and response API fields. |
| `--version` | VERSION |  | Version to use for signing. |


**Examples:**
```bash
The following command will read the file '/tmp/my/file.to.verify', and
verify it using the symmetric MAC CryptoKey dont-panic Version 3 and the
file used previously to generate the MAC tag
('/tmp/my/original.data.file').

    $ gcloud kms mac-verify --location=us-central1 \
        --keyring=hitchhiker --key=dont-panic --version=3 \
        --input-file=/tmp/my/original.data.file \
        --signature-file=/tmp/my/file.to.verify
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/mac-verify)

---
### `gcloud kms raw-decrypt`

Decrypt a ciphertext file using a raw key

gcloud kms raw-decrypt decrypts the given ciphertext file using the given
CryptoKey containing a raw key and writes the result to the named plaintext
file. The ciphertext file must not be larger than 64KiB.

The supported algorithms are: AES-128-GCM, AES-256-GCM, AES-128-CBC,
AES-256-CBC, AES-128-CTR, and AES-256-CTR.

AES-GCM provides authentication which means that it accepts additional
authenticated data (AAD). So, the flag --additional-authenticated-data-file
is only valid with AES-128-GCM and AES-256-GCM algorithms. If AAD is
provided during encryption, it must be provided during decryption too. The
file must not be larger than 64KiB.

If --plaintext-file or --additional-authenticated-data-file or
--initialization-vector-file is set to '-', that file is read from stdin.
Similarly, if --ciphertext-file is set to '-', the ciphertext is written to
stdout.

By default, the command performs integrity verification on data sent to and
received from Cloud KMS. Use --skip-integrity-verification to disable
integrity verification.

**Synopsis:**
```
gcloud kms raw-decrypt --ciphertext-file=CIPHERTEXT_FILE
    --plaintext-file=PLAINTEXT_FILE --version=VERSION
    [--additional-authenticated-data-file=ADDITIONAL_AUTHENTICATED_DATA_FILE]
    [--initialization-vector-file=INITIALIZATION_VECTOR_FILE] [--key=KEY]
    [--keyring=KEYRING] [--location=LOCATION]
    [--skip-integrity-verification] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ciphertext-file` | CIPHERTEXT_FILE |  | File path of the ciphertext file to decrypt. |
| `--plaintext-file` | PLAINTEXT_FILE |  | File path of the plaintext file to store the decrypted data. |
| `--version` | VERSION |  | Version to use for decryption. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-authenticated-data-file` | ADDITIONAL_AUTHENTICATED_DATA_FILE |  | File path to the optional file containing the additional authenticated data. |
| `--initialization-vector-file` | INITIALIZATION_VECTOR_FILE |  | File path to the optional file containing the initialization vector for decryption. |
| `--key` | KEY |  | The (raw) key to use for decryption. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--skip-integrity-verification` |  |  | Skip integrity verification on request and response API fields. |


**Examples:**
```bash
The following command reads and decrypts the file path/to/input/ciphertext.
The file will be decrypted using the CryptoKey KEYNAME containing a raw
key, from the KeyRing KEYRING in the global location. It uses the
additional authenticated data file path/to/input/aad (only valid with the
AES-GCM algorithms) and the initialization vector file path/to/input/iv.
The resulting plaintext will be written to path/to/output/plaintext.

    $ gcloud kms raw-decrypt --key=KEYNAME --keyring=KEYRING \
        --location=global --ciphertext-file=path/to/input/ciphertext \
        --additional-authenticated-data-file=path/to/input/aad \
        --initialization-vector-file=path/to/input/iv \
        --plaintext-file=path/to/output/plaintext
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/raw-decrypt)

---
### `gcloud kms raw-encrypt`

Encrypt a plaintext file using a raw key

Encrypts the given plaintext file using the given CryptoKey containing a
raw key and writes the result to the named ciphertext file. The plaintext
file must not be larger than 64KiB. For the AES-CBC algorithms, no
server-side padding is being done, so the plaintext must be a multiple of
the block size.

The supported algorithms are: AES-128-GCM, AES-256-GCM, AES-128-CBC,
AES-256-CBC, AES-128-CTR, and AES-256-CTR.

AES-GCM provides authentication which means that it accepts additional
authenticated data (AAD). So, the flag --additional-authenticated-data-file
is only valid with AES-128-GCM and AES-256-GCM algorithms.

The initialization vector (flag --initialization-vector-file) is only
supported for AES-CBC and AES-CTR algorithms, and must be 16B in length.

Therefore, both additional authenticated data and initialization vector
can't be provided during encryption. If an additional authenticated data
file is provided, its contents must also be provided during decryption. The
file must not be larger than 64KiB.

The flag --version indicates the version of the key to use for encryption.

If --plaintext-file or --additional-authenticated-data-file or
--initialization-vector-file is set to '-', that file is read from stdin.
Similarly, if --ciphertext-file is set to '-', the ciphertext is written to
stdout.

By default, the command performs integrity verification on data sent to and
received from Cloud KMS. Use --skip-integrity-verification to disable
integrity verification.

**Synopsis:**
```
gcloud kms raw-encrypt --ciphertext-file=CIPHERTEXT_FILE
    --plaintext-file=PLAINTEXT_FILE --version=VERSION
    [--additional-authenticated-data-file=ADDITIONAL_AUTHENTICATED_DATA_FILE]
    [--initialization-vector-file=INITIALIZATION_VECTOR_FILE] [--key=KEY]
    [--keyring=KEYRING] [--location=LOCATION]
    [--skip-integrity-verification] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ciphertext-file` | CIPHERTEXT_FILE |  | File path of the ciphertext file to output. |
| `--plaintext-file` | PLAINTEXT_FILE |  | File path of the plaintext file to encrypt. |
| `--version` | VERSION |  | Version to use for encryption. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-authenticated-data-file` | ADDITIONAL_AUTHENTICATED_DATA_FILE |  | File path to the optional file containing the additional authenticated data. |
| `--initialization-vector-file` | INITIALIZATION_VECTOR_FILE |  | File path to the optional file containing the initialization vector for encryption. |
| `--key` | KEY |  | The key to use for encryption. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--skip-integrity-verification` |  |  | Skip integrity verification on request and response API fields. |


**Examples:**
```bash
The following command reads and encrypts the file path/to/input/plaintext.
The file will be encrypted using the AES-GCM CryptoKey KEYNAME from the
KeyRing KEYRING in the global location using the additional authenticated
data file path/to/input/aad. The resulting ciphertext will be written to
path/to/output/ciphertext.

    $ gcloud kms raw-encrypt --key=KEYNAME --keyring=KEYRING \
        --location=global --plaintext-file=path/to/input/plaintext \
        --additional-authenticated-data-file=path/to/input/aad \
        --ciphertext-file=path/to/output/ciphertext

The following command reads and encrypts the file path/to/input/plaintext.
The file will be encrypted using the AES-CBC CryptoKey KEYNAME from the
KeyRing KEYRING in the global location using the initialization vector
stored at path/to/input/aad. The resulting ciphertext will be written to
path/to/output/ciphertext.

    $ gcloud kms raw-encrypt --key=KEYNAME --keyring=KEYRING \
        --location=global --plaintext-file=path/to/input/plaintext \
        --initialization-vector-file=path/to/input/iv \
        --ciphertext-file=path/to/output/ciphertext
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/raw-encrypt)

---