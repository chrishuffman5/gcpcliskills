# gcloud kms import-jobs

create and manage import jobs

### `gcloud kms import-jobs add-iam-policy-binding`

Add IAM policy binding to a KMS import job

Adds a policy binding to the IAM policy of a KMS import job. One binding
consists of a member and a role.

**Synopsis:**
```
gcloud kms import-jobs add-iam-policy-binding
    (IMPORT_JOB : --keyring=KEYRING --location=LOCATION) --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Import job resource - The import job to add the IAM policy binding to. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument import_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMPORT_JOB
     ID of the import job or fully qualified identifier for the import
     job.

     To set the import_job attribute:
     + provide the argument import_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The containing keyring.

     To set the keyring attribute:
     + provide the argument import_job on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The location of the resource.

     To set the location attribute:
     + provide the argument import_job on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/viewer' for the user
'test-user@gmail.com' on the import job frodo with the keyring fellowship
and location global, run:

    $ gcloud kms import-jobs add-iam-policy-binding frodo \
        --keyring='fellowship' --location='global' \
        --member='user:test-user@gmail.com' --role='roles/viewer'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/import-jobs/add-iam-policy-binding)

---
### `gcloud kms import-jobs create`

Create a new import job

Creates a new import job within the given keyring.

**Synopsis:**
```
gcloud kms import-jobs create IMPORT_JOB --import-method=IMPORT_METHOD
    --protection-level=PROTECTION_LEVEL [--keyring=KEYRING]
    [--location=LOCATION]
    [--single-tenant-hsm-instance=SINGLE_TENANT_HSM_INSTANCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMPORT_JOB
   Name of the import job to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--import-method` | one of: rsa-oaep-3072-sha1-aes-256, rsa-oaep-3072-sha256, rsa-oaep-3072-sha256-aes-256, rsa-oaep-4096-sha1-aes-256, rsa-oaep-4096-sha256, rsa-oaep-4096-sha256-aes-256 |  | The wrapping method to be used for incoming key material. For more information about choosing an import method, see https://cloud.google.com/kms/docs/key-wrapping. IMPORT_METHOD must be one of: rsa-oaep-3072-sha1-aes-256, rsa-oaep-3072-sha256, rsa-oaep-3072-sha256-aes-256, rsa-oaep-4096-sha1-aes-256, rsa-oaep-4096-sha256, rsa-oaep-4096-sha256-aes-256. |
| `--protection-level` | one of: software, hsm, hsm-single-tenant |  | Protection level of the import job. PROTECTION_LEVEL must be one of: software, hsm, hsm-single-tenant. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--keyring` | KEYRING |  | Key ring of the import job. |
| `--location` | LOCATION |  | Location of the import job. |
| `--single-tenant-hsm-instance` | SINGLE_TENANT_HSM_INSTANCE |  | The single tenant HSM instance to use for the import job. |


**Examples:**
```bash
The following command creates a new import job named strider within the
fellowship keyring, and us-central1 location:

    $ gcloud kms import-jobs create strider --location=us-central1 \
        --keyring=fellowship \
        --import-method=rsa-oaep-3072-sha256-aes-256 \
        --protection-level=hsm

The following command creates a new import job named strider within the
fellowship keyring, and us-central1 location:

    $ gcloud kms import-jobs create strider --location=us-central1 \
        --keyring=fellowship \
        --import-method=rsa-oaep-3072-sha256-aes-256 \
        --protection-level=hsm-single-tenant \
        --single-tenant-hsm-instance=my_sthi
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/import-jobs/create)

---
### `gcloud kms import-jobs describe`

Get metadata for a given import job

Returns metadata for the given import job.

The optional flag --attestation-file specifies file to write the
attestation into. The attestation enables the user to verify the integrity
and provenance of the key. See https://cloud.google.com/kms/docs/attest-key
for more information about attestations.

**Synopsis:**
```
gcloud kms import-jobs describe IMPORT_JOB
    [--attestation-file=ATTESTATION_FILE] [--keyring=KEYRING]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMPORT_JOB
   Name of the import job to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attestation-file` | ATTESTATION_FILE |  | Path to the output attestation file. |
| `--keyring` | KEYRING |  | Key ring of the import job. |
| `--location` | LOCATION |  | Location of the import job. |


**Examples:**
```bash
The following command returns metadata for import job 'strider' within the
keyring 'fellowship' in the location 'us-central1':

    $ gcloud kms import-jobs describe strider --keyring=fellowship \
        --location=us-central1

For import jobs with protection level HSM, use the --attestation-file flag
to save the attestation to a local file.

    $ gcloud kms import-jobs describe strider --keyring=fellowship \
        --location=us-central1 \
        --attestation-file=path/to/attestation.dat
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/import-jobs/describe)

---
### `gcloud kms import-jobs get-iam-policy`

Get the IAM policy for an import job

Displays the IAM policy associated with an import job. If formatted as
JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates; see $ gcloud
kms import-jobs set-iam-policy for additional details.

**Synopsis:**
```
gcloud kms import-jobs get-iam-policy
    (IMPORT_JOB : --keyring=KEYRING --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Import job resource - The import job for which to get the IAM policy
binding. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument import_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMPORT_JOB
     ID of the import job or fully qualified identifier for the import
     job.

     To set the import_job attribute:
     + provide the argument import_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The containing keyring.

     To set the keyring attribute:
     + provide the argument import_job on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The location of the resource.

     To set the location attribute:
     + provide the argument import_job on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given import job, run:

    $ gcloud kms import-jobs get-iam-policy --keyring=my-key-ring \
        --location=my-location my-importjob
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/import-jobs/get-iam-policy)

---
### `gcloud kms import-jobs list`

Lists import jobs within a keyring

Lists all import jobs within the given keyring.

**Synopsis:**
```
gcloud kms import-jobs list [--keyring=KEYRING] [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--keyring` | KEYRING |  | Key ring of the import job. |
| `--location` | LOCATION |  | Location of the import job. |


**Examples:**
```bash
The following command lists a maximum of five import jobs within the
keyring 'fellowship' and location 'global':

    $ gcloud kms import-jobs list --keyring=fellowship --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/import-jobs/list)

---
### `gcloud kms import-jobs remove-iam-policy-binding`

Remove IAM policy binding for a KMS import job

Removes a policy binding from the IAM policy of a KMS import job. One
binding consists of a member and a role.

**Synopsis:**
```
gcloud kms import-jobs remove-iam-policy-binding
    (IMPORT_JOB : --keyring=KEYRING --location=LOCATION) --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Import job resource - The import job from which to remove the IAM policy
binding. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument import_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMPORT_JOB
     ID of the import job or fully qualified identifier for the import
     job.

     To set the import_job attribute:
     + provide the argument import_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The containing keyring.

     To set the keyring attribute:
     + provide the argument import_job on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The location of the resource.

     To set the location attribute:
     + provide the argument import_job on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/viewer' for the user
'test-user@gmail.com' on the import job frodo with the keyring fellowship
and location global, run:

    $ gcloud kms import-jobs remove-iam-policy-binding frodo \
        --keyring='fellowship' --location='global' \
        --member='user:test-user@gmail.com' --role='roles/viewer'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/import-jobs/remove-iam-policy-binding)

---
### `gcloud kms import-jobs set-iam-policy`

Set the IAM policy binding for a KMS import job

Sets the IAM policy for the given import job as defined in a JSON or YAML
file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud kms import-jobs set-iam-policy
    (IMPORT_JOB : --keyring=KEYRING --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Import job resource - The import job for which to set the IAM policy
binding. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument import_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMPORT_JOB
     ID of the import job or fully qualified identifier for the import
     job.

     To set the import_job attribute:
     + provide the argument import_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The containing keyring.

     To set the keyring attribute:
     + provide the argument import_job on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The location of the resource.

     To set the location attribute:
     + provide the argument import_job on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the import job 'frodo' with the keyring
'fellowship' and location 'global':

    $ gcloud kms import-jobs set-iam-policy frodo policy.json \
        --keyring=fellowship --location=global

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/import-jobs/set-iam-policy)

---